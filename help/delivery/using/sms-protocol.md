---
product: campaign
title: Protocollo e impostazioni del connettore SMS
description: Ulteriori informazioni sul connettore SMS e su come configurarlo
feature: SMS
role: Developer, Data Engineer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
source-git-commit: 41296a0acaee93d31874bf58287e51085c6c1261
workflow-type: tm+mt
source-wordcount: '8457'
ht-degree: 1%

---

# Protocollo e impostazioni del connettore SMS {#sms-connector-protocol}

>[!NOTE]
>
>In questo documento, tutti i riferimenti ai dettagli del protocollo, dei nomi dei campi e dei valori fanno riferimento alla [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

## Panoramica {#overview}

Gli SMS possono essere limitati all’invio di brevi messaggi di testo senza formattazione, ma la loro semplicità lo rende un canale di comunicazione prezioso.

Esistono due modi principali per inviare un SMS:

* Invialo manualmente da un telefono, il solito modo per comunicare direttamente tra le persone.
* Invialo da Internet, nello stesso modo in cui Adobe Campaign invia i messaggi. A tal fine, è necessario un provider di servizi SMS che colleghi Internet alla rete mobile.
Adobe Campaign utilizza il protocollo SMPP per inviare SMS a un provider di servizi.

Questo documento illustra la connessione impostata tra Adobe Campaign e un provider SMPP.

I provider SMPP possono a volte deviare dalle specifiche ufficiali, ma il connettore SMS in Adobe Campaign offre molte opzioni per adattarne il comportamento e renderlo compatibile con la maggior parte dei provider.

>[!IMPORTANT]
>
>L&#39;impostazione di una connessione a un nuovo provider può richiedere alcune competenze tecniche, la conoscenza di TCP, binarie, rappresentazioni esadecimali e codifiche di testo. Sarà inoltre necessaria una cooperazione attiva con il fornitore.

### Tipi di SMS {#sms-types}

Quando invii SMS di massa tramite un provider SMS, incontrerai tre diversi tipi di SMS:

* **SMS MT (Mobile Terminated)**: SMS emesso da Adobe Campaign nei confronti di telefoni cellulari tramite il provider SMPP.

* **SMS MO (originato da dispositivo mobile)**: SMS inviato da dispositivo mobile ad Adobe Campaign tramite il provider SMPP.

* **SMS SR (Status Report) o DR o DLR (Delivery Receipt)**: una ricevuta di ritorno inviata dal dispositivo mobile ad Adobe Campaign tramite il provider SMPP che indica che l&#39;SMS è stato ricevuto correttamente. Adobe Campaign può anche ricevere messaggi SR che indicano che il messaggio non può essere consegnato, spesso con una descrizione dell’errore.

È necessario distinguere tra conferme (RESP PDU, parte del protocollo SMPP) e SR: SR è un tipo di SMS inviato tramite la rete end-to-end, mentre una conferma è solo una conferma del successo di un trasferimento.

Sia le conferme che l’SR possono attivare gli errori, distinguendo tra i due sarà utile per la risoluzione dei problemi.

### Informazioni trasmesse da un SMS {#information-sms}

Un SMS trasporta più informazioni che testo. Di seguito un elenco di ciò che puoi aspettarti di trovare in un SMS:

* Il testo, che è limitato a 140 byte, che significa tra 70 e 160 caratteri a seconda della codifica. Consulta [Codifica testo SMS](sms-protocol.md#sms-text-encoding) di seguito per dettagli e limitazioni.

* Un indirizzo del destinatario, a volte denominato `ADC` o `MSISDN`. Questo è il numero del cellulare che riceverà l&#39;SMS.

* Un indirizzo del mittente, che può essere chiamato `oADC` o talvolta `sender id`. Può essere un numero di telefono nell’uso quotidiano, un codice breve quando inviato tramite un provider o un nome. Il nome è una funzione facoltativa, in tal caso non puoi rispondere all’SMS.

* Un flag per indicare se il messaggio è un messaggio flash. Un messaggio flash è un pop-up non memorizzato.

* Un flag per indicare se è previsto o meno un messaggio SR.

* Una data di validità, dopo la quale non è consentito ritentare l&#39;esecuzione di apparecchiature di rete.

* Un campo `data_coding`, che indica la codifica del testo.

## Protocollo SMPP {#smpp-protocol}

Adobe Campaign Classic supporta la versione 3.4 del protocollo SMPP. Si tratta di un protocollo molto diffuso che consente di inviare SMS a un provider (SMSC) e di ricevere SMS e ricevute. Per ulteriori informazioni, consulta la [documentazione SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

L’apparecchiatura di rete sul lato del fornitore di servizi SMS è spesso denominata SMSC.

### Connessioni SMPP {#smpp-connections}

Adobe Campaign si connette all’apparecchiatura di rete del provider di servizi SMS tramite TCP. Il protocollo SMPP imposta le connessioni TCP permanenti da Adobe Campaign al provider. Le connessioni TCP vengono sempre avviate da Adobe Campaign, anche per la ricezione di messaggi.
SMPP apre 1 o 2 connessioni TCP, a seconda della modalità. Tutte le connessioni vengono sempre avviate da Adobe Campaign.

Il protocollo SMPP può funzionare in due modalità:

* **Trasmettitore+ricevitore (o TX+RX)**: per la trasmissione e la ricezione dei messaggi vengono utilizzate due connessioni TCP separate.
* **Ricetrasmettitore (o TRX)**: viene utilizzata una singola connessione TCP per la trasmissione e la ricezione dei messaggi.

>[!NOTE]
>
> Adobe Campaign Classic supporta solo la modalità TX+RX. Questa limitazione è dovuta alla sua architettura tecnica.

### PDU SMPP {#smpp-pdu}

Le unità di trasmissione SMPP (&quot;pacchetti&quot;) sono denominate PDU. Una **PDU** contiene un comando, uno stato, un numero di sequenza e dati.

Ogni PDU deve essere confermata da una `SMPP RESP PDU` (risposta sincrona). Le richieste possono essere reindirizzate: il mittente può inviare molti comandi senza attendere `RESP`; il numero di richieste che possono essere reindirizzate in qualsiasi momento è denominato finestra. `RESP PDU` può arrivare in qualsiasi ordine, non correlato all&#39;ordine della PDU dell&#39;iniziatore corrispondente.

Nella modalità separata **Trasmettitore+ricevitore**, la connessione utilizzata dipende dal tipo di messaggio trasmesso. La connessione del trasmettitore viene utilizzata per il segnale MT e la connessione del ricevitore per il segnale MO e SR. Le richieste e le risposte per ogni tipo di messaggio vengono inviate tramite la stessa connessione TCP.

Ad esempio, quando si invia un messaggio MT, viene utilizzata la connessione del trasmettitore e `RESP` che riconosce il messaggio MT viene inviato anche tramite il canale del trasmettitore. Quando si riceve un MO (o un SR), la connessione del ricevitore viene utilizzata per ricevere il MO e per inviare il `RESP` che riconosce il MO.

![](assets/do-not-localize/sms_protocol_1.png)

In Adobe Campaign Classic, per collegare SR con il corrispondente MT, SMSC restituisce un ID con i passaggi `SUBMIT_SM_RESP` e `DELIVER_SM`. L&#39;identificatore è archiviato nel campo `providerId` della tabella `nms::providerMsgId` ed è collegato a `broadLogId` e `deliveryId`. Questa operazione di corrispondenza viene eseguita dal processo SMS durante la scrittura nel database.

Se `SUBMIT_SM_RESP PDU` ha esito positivo, lo stato del messaggio &quot;inviato&quot; viene attivato nel registro di invio, mentre se `DELIVER_SM (SR) PDU` ha esito positivo viene attivato lo stato del messaggio &quot;ricevuto&quot;.

### Aspetti relativi alla sicurezza {#security-aspects}

Il protocollo non è crittografato. La maggior parte dei provider implementa una variante di IP su un elenco Consentiti di, pertanto gli indirizzi IP del server Adobe Campaign devono essere dichiarati al provider.

Adobe Campaign supporta il passaggio di un login e di una password durante la fase di binding. Supporta anche SMPP su TLS. Si noti che i certificati sono necessari per una sicurezza adeguata. Anche se il connettore SMPP consente di evitare i controlli dei certificati, deve essere utilizzato solo per il test, in quanto TLS senza certificati offre un livello di sicurezza notevolmente inferiore.

Il connettore utilizza i certificati predefiniti forniti dalla libreria `openssl` di sistema. Di solito viene fornito dalla directory `/etc/ssl/certs` su Debian. Questa directory viene fornita dal pacchetto &quot;ca-certificates&quot; per impostazione predefinita, ma può essere personalizzata.

### Informazioni in ogni tipo di PDU {#information-pdu}

Ogni tipo di PDU dispone di campi distinti che contengono informazioni diverse. Queste PDU sono descritte in dettaglio nella specifica [SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Ogni sezione seguente descrive sia la PDU che la relativa risposta sincrona (`*_RESP PDU`). Tutte le PDU devono essere confermate da un `RESP` corrispondente. Questa è una parte obbligatoria della specifica.

Le PDU possono avere campi opzionali. Qui vengono descritti solo i campi più comuni. Per ulteriori informazioni, consulta la [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Questa PDU viene utilizzata per avviare una connessione a SMSC. Le modalità **Trasmettitore**, **Ricevitore** e **Ricetrasmettitore** modificano solo il tipo di SMS consentito per il trasferimento tramite questa connessione, in particolare:

| Modalità | Tipi di SMS consentiti |
|:-:|:-:|
| Trasmettitore | MT |
| Ricevitore | MO + SR |
| Ricetrasmettitore | MT + MO + SR |

Campi rilevanti in un `BIND_* PDU`:

* **system_id**: accesso utilizzato per l&#39;autenticazione. Impostato nell’account esterno.

* **password**: password utilizzata per l&#39;autenticazione. Impostato nell’account esterno.

* **system_type**: necessario impostare un valore specifico per alcuni provider. Impostato nell’account esterno, disponibile in tutte le versioni. Spesso distingue tra diversi tipi di contratti, canali, paesi, ecc.

* **addr_ton** e **addr_npi**: richiesto da alcuni provider. Impostato dalle impostazioni `Bind TON` e `Bind NPI` nell&#39;account esterno.

* **address_range**: richiesto da alcuni provider. Nella maggior parte dei casi, si tratta di un elenco di codici brevi consentiti per questa connessione. Impostato nell’account esterno.

`BIND_*_RESP` non dispone di un campo specifico, che conferma se la connessione è riuscita o meno.

#### RIMUOVI ASSOCIAZIONE {#unbind}

Questa PDU deve essere inviata dal sistema prima della disconnessione. Prima di chiudere la connessione, è necessario attendere la PDU `UNBIND_RESP` corrispondente.

SMSC conforme non deve chiudere la connessione, la connessione TCP è controllata dal connettore Adobe Campaign.

#### SUBMIT_SM {#submit-sm}

Questa PDU invia un messaggio MT a SMSC. La PDU di risposta fornisce l’ID del messaggio MT.

Campi rilevanti in una PDU `SUBMIT_SM`:

* **service_type**: richiesto da alcuni provider. Impostato nelle proprietà di consegna.

* **source_addr_ton** e **source_addr_npi**: indica il tipo di indirizzo di origine trasmesso. Il significato di questi campi è standardizzato, ma poiché alcuni provider lo utilizzano in modo diverso, è necessario chiedere al provider il valore corretto. Impostato nell’account esterno.

* **source_addr**: indirizzo/oADC di origine del messaggio MT. Verrà visualizzato sul telefono cellulare. Impostato nell’account esterno e nella consegna, il valore nella consegna ha la precedenza sul valore dell’account esterno.

* **dest_addr_ton** e **dest_addr_npi**: indica il tipo di indirizzo di destinazione trasmesso (ad esempio, formato locale o internazionale). Il significato di questi campi è standardizzato, ma poiché alcuni provider lo utilizzano in modo diverso, è necessario chiedere al provider il valore corretto. Impostato nell’account esterno.

* **destination_addr**: indirizzo destinatario, numero di telefono o MSISDN.

* **esm_class**: utilizzato per indicare se l&#39;UDH è utilizzato o meno nel campo di testo. Attivato automaticamente dal connettore per gli SMS suddivisi se non viene utilizzata la modalità `message_payload`.

* **priority_flag**: priorità di questo messaggio rispetto ad altri. Questo è legato alla priorità della consegna stessa.

* **validation_period**: timestamp dopo il quale non deve essere effettuato alcun nuovo tentativo. Impostato nella consegna stessa.

* **registered_delivery**: indica se un messaggio SR è richiesto o meno. Adobe Campaign imposta sempre questo flag, ad eccezione delle risposte automatiche. Per i messaggi in più parti, il flag viene impostato solo per la prima parte. Tutte le versioni hanno lo stesso comportamento.

* **data_coding**: indica la codifica utilizzata nel campo di testo. Per ulteriori informazioni, consulta la sezione [Codifica testo SMS](sms-protocol.md#sms-text-encoding).

* **short_message**: testo del messaggio. Se si utilizza UDH, questo conterrà anche l’intestazione UHD.

Adobe Campaign supporta i seguenti campi facoltativi:

* **dest_addr_subunit**: utilizzato per specificare la destinazione dell&#39;SMS: flash, mobile o scheda SIM. Impostato nelle proprietà di consegna.

* **message_payload**: se abilitata nell&#39;account esterno, i messaggi lunghi verranno inviati in una singola PDU e il testo verrà trasmesso in questo campo anziché nel campo `short_message`.

#### SUBMIT_SM_RESP {#submit-sm-resp}

Questa PDU conterrà l’ID del messaggio MT. Questo è utile per farla corrispondere al messaggio SR in arrivo.

>[!IMPORTANT]
>
>Molti provider trasmettono l’ID MT in formato esadecimale. Assicurarsi di impostare correttamente il formato **ID nella conferma MT** nell&#39;account esterno.

Alcuni provider inviano `SUBMIT_SM_RESP` dopo l&#39;invio dell&#39;SR. Per tenere conto di questo comportamento, Adobe Campaign attende 30 secondi prima di rispondere con **ID messaggio non valido** a un messaggio SR con un ID sconosciuto.

#### DELIVER_SM {#delivery-sm}

Questa PDU viene inviata da SMSC ad Adobe Campaign. Contiene un MO o un SR.

La maggior parte dei campi ha lo stesso significato della controparte `SUBMIT_SM`. Di seguito è riportato l’elenco dei campi utili:

* **source_addr**: indirizzo di origine del MO/SR. Di solito questo è un numero di telefono.

* **destination_addr**: codice breve che ha ricevuto il MO o il SR.

* **esm_class**: utilizzato per stabilire se la PDU è un MO o un SR.

* **short_message**: testo del messaggio. Per SR, contiene i dati descritti nell’appendice B delle specifiche del protocollo SMPP. Per ulteriori dettagli, consulta [Gestione errori SR](sms-protocol.md#sr-error-management).

Adobe Campaign è in grado di leggere l&#39;ID del messaggio nel campo facoltativo `receipted_message_id` con una configurazione.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Questa PDU viene inviata da Adobe Campaign per riconoscere SR e MO.

Adobe Campaign Classic riconosce i messaggi SR e MO una volta inseriti nel database. Alcuni errori di elaborazione possono verificarsi anche se è stata inviata una PDU `DELIVER_SM_RESP` riuscita. Questa limitazione è causata dall&#39;architettura software di Adobe Campaign Classic.

#### INQUIRE_LINK {#enquire-links}

Questa PDU viene utilizzata solo per verificare che la connessione sia attiva. La frequenza dovrebbe essere stabilita in base alle esigenze del fornitore.

I 60 secondi predefiniti devono corrispondere alla maggior parte delle configurazioni impostate nell’account esterno.

#### INQUIRE_LINK_RESP {#enquire-links-resp}

Questa PDU riconosce che la connessione è attiva.

### SMS multipart (SMS lunghi) {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign supporta solo SMS in più parti o SMS lunghi per l’invio. UDH e `message_payload` non sono supportati per gli SMS in arrivo (MO), il che significa che MO sono limitati a 160 caratteri.

Gli SMS multipart, o SMS lunghi, sono SMS inviati in più parti. A causa di limitazioni tecniche nel protocollo di rete mobile, un SMS non può superare i 140 byte o dovrà essere suddiviso. Per ulteriori informazioni sul numero di caratteri che possono essere contenuti in un SMS, consulta la sezione [Codifica testo SMS](sms-protocol.md#sms-text-encoding).

Ogni parte di un messaggio lungo è un singolo SMS. Questi componenti viaggiano in modo indipendente sulla rete e sono assemblati dal telefono cellulare ricevente. Per gestire nuovi tentativi e problemi di connettività, Adobe Campaign invia queste parti in ordine inverso e richiede un SR solo sulla prima parte del messaggio, l’ultima inviata. Poiché il telefono cellulare visualizza un messaggio solo quando viene ricevuta la prima parte, i nuovi tentativi su parti aggiuntive non produrranno duplicati sul telefono cellulare.

È possibile impostare il numero massimo di SMS per messaggio per ogni consegna utilizzando l&#39;impostazione **Numero massimo di SMS per messaggio** nel **Modello di consegna**. I messaggi che superano questo limite non riusciranno durante l’invio con un SMS che presenta un motivo di errore troppo lungo.

Sono disponibili 2 modi per inviare SMS lunghi:

* **UDH**: metodo predefinito e consigliato per l&#39;invio di messaggi lunghi. In questa modalità, il connettore divide il messaggio in più `SUBMIT_SM PDU` con le informazioni UDH al suo interno. Questo protocollo è quello utilizzato dagli stessi cellulari. Ciò significa che Adobe Campaign ha il maggior controllo sulla generazione dei messaggi, rendendola in grado di calcolare esattamente quante parti sono state inviate e come sono state divise.

* **message_payload**: il modo in cui inviare l&#39;intero messaggio lungo in un singolo `SUBMIT_SM PDU`. Il provider dovrà suddividerlo, il che significa che per Adobe Campaign è impossibile sapere esattamente quante parti sono state inviate. Alcuni provider richiedono questa modalità, ma si consiglia di utilizzarla solo se non supportano UDH.

Per ulteriori dettagli sul protocollo e i formati, vedere la descrizione dei campi `esm_class`, `short_message` e `message_payload` della PDU [SUBMIT_SM](sms-protocol.md#information-pdu).

### Limitazione velocità effettiva e finestra {#throughput-capping}

La maggior parte dei provider richiede un limite di velocità effettiva per ogni connessione SMPP. Ciò può essere ottenuto impostando una serie di SMS nell’account esterno. Si noti che la limitazione della velocità effettiva avviene per connessione, la velocità effettiva totale è il limite per connessione moltiplicato per il numero totale di connessioni. Questo è descritto nella sezione [Connessioni simultanee](sms-protocol.md#connection-settings).

Per raggiungere il massimo throughput possibile, è necessario regolare con precisione la finestra di invio massima. La finestra di invio è il numero di `SUBMIT_SM PDU` che possono essere inviati senza attendere un `SUBMIT_SM_RESP`. Per ulteriori dettagli, consulta la sezione [Impostazione della finestra di invio](sms-protocol.md#throughput-timeouts).

### Gestione degli SR e degli errori (Appendice B) {#sr-error-management}

Il protocollo SMPP definisce gli errori sincroni standard in `RESP PDU` secondi, ma non definisce i codici di errore per SR. Ogni provider utilizza i propri codici di errore con il proprio significato.

Nella sezione dell&#39;Appendice B della [Specifica del protocollo SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) viene fatta una raccomandazione, ma questa non elenca i codici di errore effettivi né il loro significato.

Per adattarsi alla gestione degli errori, il sistema di messaggi broadlog di Adobe Campaign è stato utilizzato per eseguire correttamente il provisioning degli errori e della loro gravità (hard, soft, ecc.).

Come accennato in precedenza, esistono due diversi tipi di errori:

* risposte sincrone in `SUBMIT_SM_RESP` che si verificano immediatamente dopo l&#39;invio del messaggio a SMSC
* ricevute che potrebbero arrivare molto più tardi quando il cellulare ha ricevuto il messaggio o quando il messaggio è scaduto. In tal caso, l’errore si trova in un messaggio SR.

Quando viene ricevuto un messaggio SR, lo stato e l&#39;errore si trovano nel relativo campo `short_message` (ad esempio, per le implementazioni conformi all&#39;Appendice B). Il campo `short_message` della PDU è spesso denominato **campo di testo** poiché contiene testo in MT. Nel caso di SR, contiene informazioni tecniche e un sottocampo denominato **Testo**. Questi due campi sono diversi e `short_message` contiene effettivamente il campo **Testo** e altre informazioni.

I connettori Adobe Campaign Classic (ad eccezione di SMPP esteso) utilizzano un comportamento hardcoded che dipende dal provider selezionato. Il protocollo SMPP generico distingue solo tra successo ed errore, senza dettagli. Il registro di consegna può contenere alcune informazioni che non sono garantite.

#### Formato campo testo SR {#sr-text-field-format}

La specifica consiglia di utilizzare questo formato per il campo di testo SR. Si tratta di un elenco di sottocampi, separati da spazi e da due punti, per separare il nome del campo e il relativo valore. I nomi dei campi non fanno distinzione tra maiuscole e minuscole.

Esempio di un campo di testo SR corrispondente alla raccomandazione dell’appendice B:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Il campo ID è l&#39;ID ricevuto in `SUBMIT_SM_RESP PDU`, la conferma del messaggio MT.

`sub` e `dlvrd` devono contare la quantità di parti consegnate e messaggi consegnati, ma questo valore non viene utilizzato da Adobe Campaign in quanto il sistema broadlog fornisce informazioni migliori e più integrate.

I campi `submit date` e `done date` sono marche temporali indicative di quando il messaggio MT è stato inviato e quando il messaggio SR è stato inviato dal dispositivo mobile. Potrebbero verificarsi alcuni problemi con i fusi orari o persino marche temporali errate date da dispositivi mobili con date non corrette.

Il campo stat è importante in quanto indica lo stato del messaggio. Gli unici stati importanti sono `DELIVRD`, `UNDELIV` e `REJECTD`. Lo stato `DELIVRD` indica un successo, gli altri due indicano un errore. Altri valori sono possibili, ma in genere si tratta di notifiche intermedie, ad esempio il messaggio MT ha raggiunto il gestore di telefonia mobile, ma non il telefono cellulare. Adobe Campaign ignora queste notifiche intermedie.

Il campo err contiene il codice di errore specifico del provider. Per poter interpretare questo valore, il fornitore deve fornire una tabella dei possibili codici di errore e del relativo significato.

Infine, il campo di testo contiene in genere l’inizio del testo del messaggio MT. Questo viene ignorato da Adobe Campaign e alcuni provider non lo trasmettono per evitare la perdita di dati PII e il consumo di larghezza di banda della rete. Può essere utilizzato durante la risoluzione dei problemi per individuare più facilmente l’SR che corrisponde a un test MT leggendo questo campo.

### Esempio di elaborazione SR in SMPP generico esteso di Adobe Campaign Classic {#sr-processing}

In questo esempio viene visualizzato il caso di un’implementazione che segue il consiglio dell’Appendice B, i valori predefiniti nell’account esterno e un messaggio SMS MT riuscito.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Innanzitutto, viene applicato il regex `id extraction` per estrarre l&#39;ID e riconciliarlo con il MT corrispondente.

Quindi, `status extraction` regex e `error code extraction` regex vengono applicati per estrarre questi campi e vengono aggiunti alla stringa.

Il messaggio broadlog è costruito con queste informazioni e la stringa originale non modificata viene aggiunta come riferimento:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Il messaggio viene quindi normalizzato, rimuovendo la parte MESSAGE in modo da poter far corrispondere più messaggi con gli stessi codici stat ed err.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Se il provisioning del messaggio non è già stato eseguito nella tabella dei messaggi del registro di trasmissione, verrà creata una nuova voce utilizzando l&#39;intero messaggio come **firstText** e il messaggio normalizzato. Quindi, il connettore utilizza i valori regex `error` e success per determinare se si è trattato di un success o di un failure:

* Se corrisponde al regex `success`, verrà considerato un successo.

* Se corrisponde al regex `error`, il messaggio viene qualificato come errore.

* Se nessuno di questi due regex corrisponde, l’SR viene ignorato. Potrebbe essere una notifica intermedia, che non viene gestita da Adobe Campaign.

Per impostazione predefinita, tutti gli errori vengono configurati come errori soft. Ciò significa che gli errori rigidi devono essere predisposti manualmente.

### Codifica testo SMS {#sms-text-encoding}

È necessario **contattare sempre il provider SMSC in caso di problemi di codifica**. Solo i provider SMSC hanno conoscenza della codifica supportata e delle regole speciali che possono essere applicate a causa delle limitazioni della piattaforma tecnica.

I messaggi SMS utilizzano una speciale codifica a 7 bit, spesso denominata codifica GSM7.

Nel protocollo SMPP, il testo GSM7 verrà espanso a 8 bit per carattere per facilitare la risoluzione dei problemi. SMSC lo impacchetterà in 7 bit per carattere prima di inviarlo al dispositivo mobile. Ciò significa che il campo `short_message` dell’SMS può avere una lunghezza massima di 160 byte nel frame SMPP, mentre è limitato a 140 byte quando viene inviato sulla rete mobile.

In caso di problemi di codifica, ecco alcuni aspetti importanti da verificare:

* Assicurati di sapere quali caratteri appartengono a quale codifica. GSM7 non supporta completamente segni o accenti diacritici. Soprattutto in francese, dove è ed è fanno parte del GSM7, ma ê, â o ï non lo sono. Lo stesso vale per lo spagnolo.

* La C con cediglia (ç) è presente solo in maiuscolo nell’alfabeto GSM7, ma alcuni telefoni la rendono in minuscolo o con caratteri &quot;intelligenti&quot;. La raccomandazione generale è di evitarla completamente e rimuovere la cediglia o passare a UCS-2.

* **Non utilizzare ASCII in SMS** a meno che non sia esplicitamente richiesto dal provider SMSC. Questa codifica occupa spazio perché contiene caratteri a 8 bit e una copertura inferiore rispetto a GSM7. Questa codifica può essere richiesta per le reti CDMA, utilizzate in Nord America.

* Latin-1 non è sempre supportato. Verifica la compatibilità con il provider SMSC prima di tentare di utilizzare Latin-1.

* Le tabelle di cambio della lingua nazionale non sono supportate dal connettore Adobe Campaign. Al suo posto, devi utilizzare UCS-2 o un altro `data_coding`.

* Le unità UCS-2 e UTF-16 sono spesso combinate dai telefoni. Questo è un problema quando si utilizzano emoji e altri caratteri non presenti in UCS-2.

* La maggior parte dei telefoni non dispone di glifi font per tutti i caratteri UCS-2. Gli smartphone tendono ad essere in grado di mostrare caratteri rari piuttosto facilmente, ma i telefoni di caratteristiche generalmente hanno un supporto limitato a ciò che è utile nella lingua nativa del paese in cui sono stati acquistati. Se desideri utilizzare emoji o ASCII-art, esegui il test su un’ampia gamma di telefoni prima dell’invio. L’anteprima di Adobe Campaign non simula i glifi mancanti e visualizza i simboli disponibili sul browser web.

Il campo `data_coding` indica la codifica utilizzata. Un problema importante è che il valore 0 indica la codifica SMSC predefinita nelle specifiche, che in genere si riferisce a GSM7. Verifica con il partner SMSC quale codifica è associata a `data_coding` = 0 che Adobe Campaign supporta solo. Altri valori `data_coding` tendono a seguire la specifica, ma l&#39;unico modo per essere sicuri è quello di verificare con il provider SMSC.

La dimensione massima di un messaggio dipende dalla relativa codifica. Questa tabella riassume tutte le informazioni pertinenti:

| Codifica | Data_coding abituale | Dimensione del messaggio (caratteri) | Dimensione parte per SMS in più parti | Caratteri disponibili |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | Set di caratteri di base GSM7 + estensione (i caratteri estesi contengono 2 caratteri) |
| Latin-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (varia da telefono a telefono) |

## Parametri dell’account esterno SMPP {#SMPP-parameters-external}

Ogni implementazione del protocollo SMPP presenta diverse varianti. Per migliorare la compatibilità e l’adattabilità, sono disponibili molte impostazioni che consentono di modificare il comportamento del connettore SMPP. In questa sezione vengono descritti tutti i parametri e i relativi effetti sul connettore.

### Parametri generali e percorso {#general-parameters-routing}

**Limita istanze MTA per questo account**

È possibile impostare un limite al numero di istanze MTA consentite per la connessione al provider SMPP. Se questa opzione è selezionata, puoi specificare quanti MTA possono essere utilizzati al massimo.

Questa opzione consente un controllo più preciso sul numero di connessioni. Vedere [Connessioni simultanee](sms-protocol.md#connection-settings).

Se imposti un valore superiore al numero di MTA in esecuzione, tutti gli MTA verranno eseguiti come normale: questa opzione è solo un limite e non può generare MTA aggiuntivi.

Se devi controllare con precisione il numero di connessioni, ad esempio il requisito del provider, è consigliabile impostare sempre questa opzione anche se la distribuzione corrente dispone del numero corretto di MTA in esecuzione. Se in seguito vengono aggiunti altri MTA, il limite di connessione verrà comunque rispettato.

### Impostazioni di connessione {#connection-settings}

#### Nome dell’implementazione SMSC {#smsc-implementation-name}

Imposta il nome dell’implementazione SMSC. Deve essere impostato sul nome del provider. Contatta l’amministratore o il team di recapito messaggi per sapere cosa aggiungere in questo campo. Il ruolo di questo campo è descritto nella sezione [Gestione errori SR](sms-protocol.md#sr-error-management).

>[!NOTE]
>
>Il team di recapito messaggi si basa sul contratto e i clienti devono contattare il proprio rappresentante Adobe per informazioni relative al recapito messaggi.

#### Server {#server}

Nome DNS o indirizzo IP del server a cui connettersi.

#### Porta {#port}

Porta TCP a cui connettersi.

#### Account {#account}

Accesso della connessione. Passato nel campo `system_id` della PDU BIND.

#### Password {#password}

Password della connessione SMPP. Passato nel campo password della PDU BIND.

#### Tipo di sistema {#system-type}

Valore passato nel campo `system_id` della PDU BIND. Alcuni provider necessitano di un valore specifico.

#### Numero di connessioni MTA secondarie {#number-mta-child}

In Adobe Campaign Classic, definisce il numero di connessioni per elemento secondario MTA.

Il connettore SMPP esteso di Adobe Campaign Classic può controllare il numero di connessioni per elemento secondario MTA. Per controllare il limite globale delle connessioni, dovrai limitare il numero di processi secondari MTA, il che spesso significa disporre di una piattaforma di mid-sourcing dedicata per gli SMS.

Per Adobe Campaign Classic, può esistere un diverso numero di connessioni ricevitore e trasmettitore:

* **Connessioni del trasmettitore = Numero di connessioni MTA secondarie * Numero di processi MTA secondari * Numero di MTA (se è impostata la risposta automatica) * Numero di connessioni MTA secondarie**

Come suggerito in precedenza, il processo SMS di Adobe Campaign Classic apre più connessioni trasmettitore se è abilitata la risposta automatica. Queste connessioni aggiuntive vengono utilizzate per inviare le risposte automatiche.

* **Connessioni del ricevitore = numero di connessioni secondarie MTA**

Se imposti le risposte automatiche, il processo SMS aprirà coppie trasmettitore/ricevitore, aumentando il numero di connessioni trasmettitore. Se non è stata impostata alcuna risposta automatica, verranno aperte solo le connessioni del ricevitore.

#### Abilita TLS su SMPP {#enable-TLS}

Utilizza TLS per connettersi al provider. La connessione verrà crittografata. La connessione TLS è gestita dalla libreria OpenSSL. Qualsiasi elemento applicabile a OpenSSL sarà true per questa connessione.

#### Abilita tracce SMPP verbose nel file di registro {#enable-verbose-log-file}

Questa impostazione esegue il dump di tutto il traffico SMPP nei file di registro. Spesso è necessario regolare i parametri durante la configurazione iniziale. Questa opzione deve essere abilitata durante la risoluzione dei problemi del connettore e confrontata con il traffico visualizzato dal provider.

In Adobe Campaign Classic, l’output del registro si trova nel registro MTA per il traffico relativo a MT e nel registro SMS per il traffico relativo a MO e SR.

### Impostazione della connessione del ricevitore {#receiver-connection}

Questa sezione è visibile solo in modalità **trasmettitore+ricevitore** separata.

#### Utilizza parametri diversi per il ricevente {#receiver-parameters}

Se la casella non è selezionata, le stesse impostazioni vengono utilizzate per il trasmettitore e il ricevitore.

Quando la casella è selezionata, le impostazioni della sezione **Impostazioni di connessione** verranno applicate al trasmettitore e le impostazioni della **Connessione ricevente** verranno applicate al ricevitore.

**Server di ricezione, porta, account, password, tipo di sistema**

Queste impostazioni si applicano al ricevitore in modalità trasmettitore+ricevitore. Funzionano come la parte del trasmettitore, vedi sopra per maggiori dettagli.

### Impostazioni del canale SMPP {#smpp-channel-settings}

#### Consenti traslitterazione caratteri {#allow-character-transliteration}

La traslitterazione è il processo di ricerca di caratteri equivalenti a quelli mancanti. Ad esempio, il carattere francese &quot;ê&quot; (con accento circonflesso) non è presente nella codifica GSM, ma può essere sostituito da &quot;e&quot; senza compromettere la leggibilità.

Se questa casella non è selezionata, la codifica del testo avrà esito negativo se non è in grado di codificare la stringa esattamente come è.

Se questa casella è selezionata, la codifica del testo tenterà di convertire la stringa in una versione approssimativa anziché non riuscire. Se alcuni caratteri non hanno un equivalente nella codifica di destinazione, la codifica del testo avrà esito negativo.

Per una spiegazione più generale del processo di codifica, vedere [Definire una mappatura specifica delle impostazioni di codifica](sms-protocol.md#SMSC-specifics).

#### Memorizza MO in ingresso nel database {#incoming-mo-storing}

Quando questa opzione è attivata, il MO in ingresso verrà memorizzato nella tabella inSMS del database. È possibile eseguire query su questa tabella utilizzando l&#39;attività di query di qualsiasi flusso di lavoro.

Adobe Campaign Classic memorizza sempre tutti i messaggi MO nel database inSMS, pertanto questa opzione non è disponibile.

#### Abilita aggiornamenti dei KPI in tempo reale durante l’elaborazione SR {#real-time-kpi}

Quando questa opzione è abilitata, i KPI vengono aggiornati in tempo reale sulla pagina di consegna principale quando si riceve l’errore SR.

L&#39;inconveniente può essere rappresentato da prestazioni insufficienti a causa del conflitto di database generato. Se disabilitata, le statistiche vengono aggiornate dal flusso di lavoro **syncfromexec**, in esecuzione ogni 20 minuti.

Adobe Campaign Classic dispone di un meccanismo completamente diverso per i KPI, pertanto questa opzione non è disponibile.

#### Numero sorgente {#source-number}

Definisce l&#39;indirizzo di origine predefinito per i messaggi. Questa impostazione si applica solo se il numero di origine è stato lasciato vuoto nella consegna.

Per impostazione predefinita, il campo del numero di origine non viene passato, pertanto il provider lo sostituirà con il codice breve.

In questo modo viene attivata la funzione di sostituzione indirizzo mittente/ADC.

#### Codice breve {#short-code}

Indica il codice breve principale dell’account. Se per questo account vengono utilizzati più codici brevi o se il codice breve è sconosciuto, lascia vuoto questo campo.

La specifica di un codice breve è utile per due funzioni:

* Se non viene fornito alcun numero di origine, nell’anteprima viene visualizzato il codice breve. Rifletterà il comportamento reale sul telefono cellulare.

* L’impostazione di inserisce nell&#39;elenco Bloccati del codice di risposta automatica dell’di mette in quarantena l’utente solo per un codice breve specifico.

#### Source TON/NPI, TON di destinazione/NPI {#ton-npi}

TON (Type Of Number) e NPI (Numbering Plan Indicator) sono descritti nella sezione 5.2.5 della [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pagina 117). Questi valori devono essere impostati in base alle esigenze del provider.

Vengono trasmessi così come sono nei campi `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` e `dest_addr_npi` di `SUBMIT_SM PDU`.

#### Tipo di servizio {#service-type}

Questo campo viene trasmesso così com&#39;è nel campo `service_type` di `SUBMIT_SM PDU`. Imposta in base alle esigenze del provider.

### Throughput e timeout {#throughput-timeouts}

Queste impostazioni controllano tutti gli aspetti relativi alla temporizzazione del canale SMPP. Alcuni provider richiedono un controllo molto preciso della frequenza dei messaggi, della finestra e degli intervalli dei nuovi tentativi. Queste impostazioni devono essere impostate su valori che corrispondano alla capacità del fornitore e alle condizioni indicate nel contratto.

#### Finestra di invio {#sending-window}

La finestra è il numero di `SUBMIT_SM PDU` che possono essere inviati senza attendere un `SUBMIT_SM_RESP` corrispondente.

Esempio di trasmissione con una finestra massima di 4:

![](assets/do-not-localize/sms_protocol_2.png)

La finestra consente di aumentare il throughput quando il collegamento di rete ha una latenza elevata.  Il valore della finestra deve essere almeno il numero di SMS/s moltiplicato per la latenza del collegamento
in secondi, pertanto il connettore non attende mai `SUBMIT_SM_RESP` prima di inviare il messaggio successivo.
Se la finestra è troppo grande, puoi inviare altri messaggi duplicati in caso di problemi di connessione. Inoltre, la maggior parte dei provider ha un limite molto rigoroso per la finestra e rifiuta i messaggi che superano tale limite.

Come calcolare la formula ottimale della finestra di invio:

* Misurare la latenza massima tra `SUBMIT_SM` e `SUBMIT_SM_RESP`.

* Moltiplica questo valore in secondi per il throughput MT massimo. Questo fornirà il valore ottimale della finestra di invio.

Esempio: se hai impostato 300 SMS/s nella velocità effettiva massima MT ed è presente in media una latenza di 100 ms tra `SUBMIT_SM` e `SUBMIT_SM_RESP`, il valore ottimale è `300×0.1 = 30`.

#### Velocità effettiva MT massima {#max-mt-throughput}

Numero massimo di MT al secondo e per connessione. Questa impostazione è rigorosamente applicata, l’MTA non invierà mai i messaggi più rapidamente di questo limite. È utile per i provider che richiedono una limitazione precisa.

Per conoscere il limite di velocità effettiva totale, moltiplica questo numero per il numero totale di connessioni come descritto nella formula precedente.

0 significa nessun limite, l’MTA invierà MT il più rapidamente possibile.

In genere si raccomanda di mantenere questa impostazione al di sotto di 1000, poiché è impossibile garantire un throughput preciso superiore a tale numero a meno che non sia opportunamente analizzata l’architettura finale e non sia stato specificamente richiesto al fornitore di SMPP. Potrebbe essere meglio aumentare il numero di connessioni per superare i 1000 MT/s.

#### Tempo prima della riconnessione {#time-reconnection}

Quando la connessione TCP viene persa, il connettore attenderà questo numero di secondi prima di tentare di stabilire una connessione.

#### Periodo di scadenza del MT {#expiration-period}

Timeout tra `SUBMIT_SM` e `SUBMIT_SM_RESP` corrispondente. Se `RESP` non viene ricevuto in tempo, il messaggio verrà considerato come non riuscito e verranno applicati i criteri globali per i nuovi tentativi dell&#39;MTA.

#### Associa timeout {#bind-timeout}

Timeout tra il tentativo di connessione TCP e la risposta `BIND_*_RESP`. Quando si verifica un timeout, la connessione viene chiusa dal connettore Adobe Campaign e si attende il tempo necessario per riconnettersi prima di riprovare.

#### Periodo enquire_link {#enquire-link-period}

`enquire_link` è un tipo speciale di PDU inviata per mantenere attiva la connessione. Questo periodo è in secondi. Il connettore campaign invia solo `enquire_link` quando la connessione è inattiva per risparmiare larghezza di banda. Se non viene ricevuto alcun RESP dopo il doppio di questo periodo, la connessione verrà considerata inattiva e verrà attivato un processo di riconnessione.

### Specifiche di SMSC {#SMSC-specifics}

Si tratta di impostazioni avanzate che adattano il connettore Adobe Campaign alla maggior parte delle peculiarità dell’implementazione SMPP.

**Definire una mappatura specifica delle codifiche**

Per informazioni dettagliate sulla codifica del testo, consulta la sezione [Codifica del testo SMS](sms-protocol.md#sms-text-encoding).

Questa impostazione consente di definire una mappatura di codifica personalizzata, diversa dalle specifiche. Potrai dichiarare un elenco di codifiche e il relativo valore `data_coding`.

L’MTA tenterà di codificare utilizzando la prima codifica dell’elenco. In caso contrario, tenterà di utilizzare la codifica successiva nell’elenco, ecc. Se non è possibile utilizzare alcuna codifica per codificare il messaggio, si verifica un errore. Una volta trovata la codifica, l&#39;MTA creerà `SUBMIT_SM PDU` con il testo codificato e il campo `data_coding` impostato con il valore specificato nella tabella.

L’ordine degli elementi nella tabella è importante: le codifiche sono tentativi dall’alto verso il basso. La codifica più economica o quella più consigliata si trova in cima all&#39;elenco, seguita da codifiche sempre più costose.

Tieni presente che UCS-2 non avrà mai esito negativo in quanto può codificare tutti i caratteri supportati in Adobe Campaign e che la lunghezza massima di un SMS UCS-2 è molto inferiore: solo 70 caratteri.

Puoi inoltre utilizzare questa impostazione per forzare l’utilizzo di una codifica specifica dichiarando solo 1 riga nella tabella di mappatura.

La mappatura predefinita utilizzata quando la casella di controllo non è selezionata equivale alla tabella seguente:

| data_coding | Codifica |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

Ciò significa che l’MTA tenterà di codificare il messaggio in GSM. In caso di esito positivo, verrà inviato con `data_coding` impostato su 0.

Se il messaggio non può essere codificato in GSM, verrà codificato in UCS-2 e verrà impostato `data_coding` su 8.

#### Abilita message_payload {#enable-message-payload}

Se questa opzione è deselezionata, gli SMS lunghi verranno suddivisi dall’MTA e inviati in più `SUBMIT_SM PDU` secondi con UDH. Il messaggio verrà ricomposto dal telefono cellulare dopo i dati UDH.

Se questa opzione è selezionata, gli SMS lunghi vengono inviati in una PDU SUBMIT_SM, inserendo il testo nel campo facoltativo message_payload. Per informazioni dettagliate, consulta la [specifica SMPP](sms-protocol.md#ACS-SMPP-connector).

Se questa funzione è abilitata, Adobe Campaign non sarà in grado di contare le parti SMS singolarmente: tutti i messaggi verranno conteggiati come inviati in una sola parte.

#### Invia il numero di telefono completo {#send-full-phone-number}

Se questa casella di controllo non è selezionata, solo le cifre del numero di telefono vengono inviate al provider (campo `destination_addr` del campo `SUBMIT_SM`). Questo è il comportamento predefinito poiché l’indicatore del numero internazionale, in genere un prefisso +, viene sostituito dai campi TON e NPI in SMPP.

Quando la casella di controllo è selezionata, il numero di telefono viene inviato così com’è, senza preelaborazione e spazi potenziali, + prefisso o cancelletto/hash/asterisco.

Questa funzione ha anche un effetto sul comportamento della funzione di inserisce nell&#39;elenco Bloccati automatica di risposta di un’: quando la casella di controllo non è selezionata, ai numeri di telefono inseriti nella tabella di quarantena viene aggiunto un prefisso + per compensare la rimozione del prefisso + dal numero di telefono da parte del protocollo SMPP stesso.

#### Ignora controllo certificato TLS {#skip-tls}

Quando TLS è abilitato, ignora tutti i controlli dei certificati.

Se questa opzione è selezionata, la connessione non è più sicura e non deve essere abilitata in produzione.

Può essere utile a scopo di debug o test.

È possibile scegliere tra tre valori diversi per la convalida del certificato:

* Verifica della certificazione completa (incluso il nome host), impostazione predefinita.
* Ignora la verifica del nome host.
* Ignora la verifica del certificato.

#### Associa TON/NPI {#bind-ton-npi}

TON (tipo di numero) e NPI (indicatore del piano di numerazione) descritti nella sezione 5.2.5 della specifica [SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pagina 117). Questi valori devono essere impostati in base alle esigenze del provider.

Vengono trasmessi così come sono nei campi `addr_ton` e `addr_npi` della PDU BIND.

#### Intervallo di indirizzi {#address-range}

Inviato così com’è nel campo address_range della PDU BIND. Questo valore deve essere impostato in base alle esigenze del provider.

#### Conteggio ID conferma non valido {#invalid-id}

Limita il numero di **ID messaggio non valido** `DELIVER_SM_RESP` che può essere inviato per un singolo messaggio SR.

**Utilizzare questa opzione solo per la risoluzione dei problemi come soluzione alternativa** e impostarla su 0 in condizioni normali.

Esempio Fox, quando si imposta su 2:

* Il provider invia un messaggio SR (`DELIVER_SM`) con ID &quot;1234&quot;.

* Impossibile trovare l&#39;ID &quot;1234&quot; nel database.

* Il connettore conta 1 **Errore ID** non valido per tale ID, pertanto invia `DELIVER_SM_RESP` con il codice di errore &quot;ID messaggio non valido&quot; (comportamento normale).

* Il provider ritenta lo stesso messaggio SR con ID &quot;1234&quot;.

* Impossibile trovare l&#39;ID &quot;1234&quot; nel database.

* Il connettore conta 2 **Errore ID** non valido per tale ID, pertanto invia `DELIVER_SM_RESP` &quot;OK&quot;, anche se non è stato elaborato correttamente.

* Questa funzione ha lo scopo di effettuare il flushing dei buffer SR sul lato provider quando un blocco SR non valido è legittimo e i messaggi non possono essere elaborati.

Impostando questo campo su 0 si disabilita il meccanismo in cui viene sempre restituito **ID messaggio non valido**. Si tratta di un comportamento normale.

Impostando questo campo su 1, il connettore risponde sempre &quot;OK&quot;, anche se l’ID non è valido. Questo valore deve essere impostato su 1 solo sotto supervisione, per la risoluzione dei problemi e per il tempo minimo, ad esempio per il ripristino da un problema lato provider.

#### Regex di estrazione dell’ID nell’SR {#regex-extraction}

Il formato SR non è strettamente imposto dalla specifica del protocollo SMPP. Si tratta solo di una raccomandazione descritta nell&#39;[Appendice B](sms-protocol.md#sr-error-management) (pagina 167) del disciplinare. Alcuni implementatori SMPP formattano questo campo in modo diverso, pertanto Adobe Campaign ha bisogno di un modo per estrarre il campo corretto.

Per impostazione predefinita, acquisisce fino a 10 caratteri alfanumerici dopo `id:`.

Il regex deve avere esattamente un gruppo di acquisizione con una parte racchiusa tra parentesi. Le parentesi devono circondare la parte ID. Il formato regex è PCRE.

Quando regoli questa impostazione, accertati di includere il maggior contesto possibile per evitare falsi attivatori. Se sono presenti prefissi specifici, ad esempio `id:` nello standard, includili nel regex. Utilizzare inoltre i delimitatori di parola (\b) il più possibile per evitare di acquisire il testo al centro di una parola.

L’inclusione di un numero insufficiente di contenuti nel codice regex può introdurre un piccolo difetto di sicurezza: il contenuto effettivo del messaggio può essere incluso nell’SR. Se abbini solo un formato ID specifico senza contesto, ad esempio un UUID, potrebbe essere l’analisi del contenuto di testo effettivo, ad esempio un UUID incorporato nel campo di testo, invece dell’ID.

#### Regex applicato per determinare lo stato di esito positivo/errore {#regex-applied}

Quando si verificano messaggi con una combinazione di campi stat/err sconosciuta, questi regex vengono applicati al campo stat per determinare se l’SR è stato un successo o un errore. I SR con valori stat che non corrispondono a nessuno di questi regex vengono ignorati.

Per impostazione predefinita, i valori stat che iniziano con `DELIV`, ad esempio `DELIVRD` nell&#39;[Appendice B](sms-protocol.md#sr-error-management), verranno considerati consegnati correttamente e tutti i valori stat che corrispondono agli errori, ad esempio `REJECTED`, `UNDELIV`, vengono considerati errori.

#### Formato ID nella conferma MT {#id-format-mt}

Indica il formato dell&#39;ID restituito nel campo `message_id` di `SUBMIT_SM_RESP PDU`.

* **Non modificare**: l&#39;ID viene archiviato così com&#39;è nel database, come testo con codifica ASCII. Non si verificano pre-elaborazione né filtri.

* **Numero decimale**: l&#39;ID deve essere un numero decimale in formato ASCII. Gli spazi iniziali e finali e gli zeri iniziali vengono rimossi quando si utilizza questa impostazione.

* **Numero esadecimale**: l&#39;ID deve essere un numero esadecimale in formato ASCII, senza 0x iniziale né h finale. L’ID viene quindi convertito in un numero decimale prima di essere memorizzato nel database.

* **Stringa esadecimale**: l&#39;ID deve essere un testo con codifica ASCII, a sua volta una stringa di byte con codifica esadecimale. Ad esempio, nella PDU troverai `0x34 0x31 0x34 0x32 0x34 0x33`, che si traduce in ASCII &quot;414243&quot;. Questa stringa viene quindi decodificata come stringa esadecimale di byte e si ottiene &quot;ABC&quot; come risultato: si memorizzerà l&#39;ID &quot;ABC&quot; nel database.

#### Formato ID in SR {#id-format-sr}

Indica il formato dell&#39;ID acquisito dal regex `Extraction` dell&#39;ID nell&#39;SR. I valori hanno lo stesso significato e lo stesso comportamento del formato in MT qui sopra.

**ID SR o codice di errore nel campo facoltativo**

>[!NOTE]
>
>Disponibile solo nel connettore SMPP esteso di Adobe Campaign Classic.

Se questa opzione è selezionata, il contenuto dei campi facoltativi verrà aggiunto al testo elaborato dai regex di cui sopra. Il formato del testo sarà `0xTAG:VALUE`, dove `0xTAG` è il valore esadecimale a 4 cifre del tag in lettere maiuscole, ad esempio `0x002E`.

Ad esempio, potrebbe essere utile acquisire l&#39;ID nel campo `receipted_message_id`. Per questo, abilita questa casella di controllo e il seguente testo verrà aggiunto allo stato:

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

In questo esempio, 0x001E è il tag del campo facoltativo e l’UUID è il valore del campo.

Per acquisire questo valore, ora puoi impostare il seguente regex nel regex di estrazione dell’ID nel campo SR:

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>È possibile acquisire solo campi facoltativi con valori di testo (ASCII/UTF-8). In particolare, i campi binari non possono essere acquisiti in modo affidabile con il sistema regex corrente.

**ID SR o codice di errore nel campo di testo**

Se questa opzione è selezionata, il campo **Testo** verrà mantenuto durante l&#39;elaborazione del testo dello stato dell&#39;SR.

Questa opzione è utile se il provider inserisce dati importanti in questo campo, ad esempio l’ID o lo stato. Di solito questo campo può essere eliminato in modo sicuro perché può contenere testo con una codifica non ASCII e interrompere l’elaborazione regex.

L&#39;abilitazione di questa opzione può introdurre un errore di sicurezza molto piccolo se il regex `Extraction` dell&#39;ID nel campo SR non è abbastanza specifico. Il contenuto del campo **Testo** può essere analizzato come ID e un utente non autorizzato può utilizzarlo per inserire ID contraffatti, il che può portare a una situazione di rifiuto parziale del servizio.

**Tag ID servizio**

Consente di aggiungere un valore TLV personalizzato. Questo campo imposta la porzione di tag. Il valore può essere personalizzato per consegna nel valore **ID servizio o programma** nei parametri avanzati della consegna.

Questa impostazione consente di aggiungere solo un’opzione TLV per messaggio.

### Risposta automatica inviata al MO {#automatic-reply}

>[!IMPORTANT]
>
>In Adobe Campaign Classic e in un&#39;architettura ibrida, l&#39;applicazione della risposta automatica per il connettore SMPP esteso richiede di aggiungere l&#39;accesso in scrittura per l&#39;operatore mid nella cartella **External account**.

Questa funzione consente di rispondere rapidamente al testo in formato MO e gestire l’invio di codice per short a un inserisco nell&#39;elenco Bloccati di tipo.

Le colonne **Parola chiave** e **Codice breve** definiscono le condizioni per attivare la risposta automatica. Se entrambi i campi corrispondono, viene inviato il messaggio MO e viene attivata l’azione aggiuntiva. Per specificare un carattere jolly, lasciare vuoto il campo. La parola chiave corrisponde alla prima parola alfanumerica nel testo MO, ignorando la punteggiatura e gli spazi iniziali. Ciò significa che il campo **Parola chiave** non può contenere spazi e deve essere una singola parola.

L&#39;impostazione **Parola chiave** è un prefisso. Ad esempio, se specifichi &quot;AD&quot;, corrisponderà a &quot;AD&quot;, &quot;ADAPT&quot; e &quot;ADOBE&quot;. Se disponi di più parole chiave con un prefisso comune, è necessario prestare attenzione all’ordine, poiché le parole chiave vengono elaborate dall’alto verso il basso.

La colonna **Rispondi** è il testo da rispondere. Non è disponibile alcuna personalizzazione in questo campo. Se lasci questo campo vuoto, non verrà risposto alcun messaggio, ma l’azione aggiuntiva verrà attivata comunque.

La colonna **Azione aggiuntiva** fornisce un&#39;azione aggiuntiva quando **Parola chiave** e **Codice breve** corrispondono, il codice breve vuoto corrisponde a tutti i codici brevi. Puoi mettere in quarantena o rimuoverlo dalla quarantena; valore nessuno risponde al testo. Se si specifica una **Azione aggiuntiva** ma si lascia vuoto il campo **Rispondi**, l&#39;azione verrà eseguita ma non verrà inviata alcuna risposta. La quarantena viene applicata solo per il codice breve specificato o per tutti i codici brevi se il campo viene lasciato vuoto.

>[!IMPORTANT]
>
>L’impostazione Invia numero di telefono completo ha un impatto sul comportamento del meccanismo di quarantena automatica delle risposte: se l’opzione Invia numero di telefono completo non è selezionata, il numero di telefono messo in quarantena sarà preceduto da un segno più (&quot;+&quot;) per renderlo compatibile con il formato del numero di telefono internazionale.

Tutte le voci della tabella vengono elaborate nell&#39;ordine specificato, fino a quando non viene trovata una corrispondenza per una regola. Se più regole corrispondono a un MO, verrà applicata solo la regola più in alto.

## Parametri del modello di consegna SMS {#sms-delivery-template-parameters}

Alcuni parametri possono essere impostati per modello di consegna.

### Campo Da {#from-field}

Questo campo è facoltativo. Consente di ignorare l’indirizzo del mittente (oADC). Il contenuto di questo campo viene inserito nel campo `source_addr` di `SUBMIT_SM PDU`.

La specifica SMPP limita il campo a 21 caratteri, ma alcuni provider possono consentire valori più lunghi. Tieni presente che in alcuni paesi possono essere applicate restrizioni molto rigide, ad esempio lunghezza, contenuto e caratteri consentiti.

### Parametri di consegna {#delivery-parameters}

#### Numero massimo di SMS per messaggio {#maximum-sms}

Questa impostazione funziona solo se l&#39;impostazione **Payload messaggio** è disabilitata. Se il messaggio richiede più SMS di questo valore, viene attivato un errore.

Il protocollo SMS limita gli SMS a 255 parti, ma alcuni telefoni cellulari hanno problemi a mettere insieme messaggi lunghi con più di 10 parti o giù di lì, il limite dipende dal modello esatto. Ti consigliamo di non superare le 5 parti per messaggio.

A causa del funzionamento dei messaggi personalizzati in Adobe Campaign, le dimensioni dei messaggi possono variare. La disponibilità di una grande quantità di messaggi lunghi potrebbe aumentare i costi di invio.

#### Modalità di trasmissione {#transmission-mode}

Questo campo indica il tipo di SMS che desideri trasferire: messaggi normali o flash, memorizzati sul cellulare o sulla scheda SIM.

Questa impostazione viene trasmessa nel campo facoltativo `dest_addr_subunit` in `SUBMIT_SM PDU`.

* **Non specificato** non invia alcun campo facoltativo nella PDU.

* **Flash** imposta il valore su 1. Invia un messaggio flash che viene visualizzato sul dispositivo mobile e non viene memorizzato.

* **Normal** imposta il valore su 0. Invia un messaggio normale.

* **Salva su dispositivo mobile** imposta il valore su 2. Indica al telefono di memorizzare l’SMS nella memoria interna.

* **Salva nel terminale** imposta il valore su 3. Indica al telefono di memorizzare l’SMS nella scheda SIM.

#### Periodo di validità {#validity-period}

Il periodo di validità viene trasmesso nel campo `validity_period` di `SUBMIT_SM PDU`. La data viene sempre formattata come formato ora UTC assoluto; il campo data termina con &quot;00+&quot;.

## Connettore SMPP generico esteso {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

Le frecce rappresentano i flussi di dati.

Quando si inviano parti di consegna, l’MTA genera elementi secondari dell’MTA. Il numero di processi secondari MTA è dinamico e dipende da una configurazione in serverConf.xml. Ogni elemento secondario MTA crea un’istanza del connettore `CSmppConnectorWorker` che si connette al provider SMPP. Le connessioni restano attive finché l’elemento secondario MTA rimane attivo, anche configurabile in serverConf.xml.

Il processo SMS elabora solo SR, si connette al provider e lascia aperta la connessione. Il processo si riconnette ogni 10 minuti per ricaricare le nuove impostazioni, operazione normale.

### Voci MT, SR e broadlog corrispondenti {#matching-mt}

Una tabella intermedia `nmsProviderMsgId` viene utilizzata per memorizzare temporaneamente i dati MT e SR prima di essere salvati in modo asincrono nel broadlog.

La tabella `nmsProviderMsgId` contiene 3 gruppi di colonne:

* Colonne aggiornate quando un messaggio MT viene inviato e riconosciuto: `iBroadLogId`, `iDeliveryId`

* Colonne aggiornate alla ricezione di un messaggio SR: `iMsgId`, `iStatus`

* Colonne sempre aggiornate: `tsCreated`, `sProviderId`

Al termine dell’elaborazione di MT e SR, è necessario disporre di linee complete, contenenti sia informazioni sul broadlog che informazioni sullo stato.

In questo caso, `iMsgId` è collegato alla tabella `nmsBroadLogMsg`, che indica il messaggio di stato/errore completo.

Il processo SMS verifica la presenza di righe complete ogni minuto, quindi le elabora in modo asincrono:

* Viene letta la riga completa.
* Il processo SMS calcola il nome della tabella broadlog in base alla mappatura della consegna.
* Il processo SMS aggiorna la tabella broadlog con l’ID del messaggio e lo stato.

**Velocità effettiva e connessioni parallele**

Ogni elemento secondario MTA crea una quantità configurabile di connessioni, pertanto la limitazione del numero di elementi secondari MTA limiterà il numero di connessioni. Poiché la correlazione tra i processi secondari MTA e il traffico è correlata, questo può essere in qualche modo controllato, ma ancora un po’ imprevedibile.

## Prima di andare in diretta {#checklist}

Questo elenco di controllo fornisce un elenco di elementi da controllare prima della pubblicazione. Una configurazione incompleta può causare molti problemi.

### Verifica la presenza di conflitti di account esterni {#external-account-conflict}

Verifica di non disporre di account SMS esterni precedenti. Se si lascia disabilitato l&#39;account di test, si corre il rischio che venga riabilitato nel sistema di produzione e che vengano generati potenziali conflitti.

Se sulla stessa istanza di Adobe Campaign sono presenti più account che si connettono allo stesso provider, contatta il provider per assicurarti che distinguano effettivamente le connessioni tra tali account. Avere più account con lo stesso accesso richiede una configurazione aggiuntiva.

### Abilita tracce SMPP dettagliate durante i controlli {#enable-verbose}

Durante i controlli è sempre necessario abilitare tracce SMPP dettagliate.
Anche se non riesci a controllare i registri da solo, [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) potrà aiutarti più facilmente.

### Verifica l’SMS {#test}

* **Invia SMS con tutti i tipi di caratteri**
Se devi inviare un SMS con caratteri non GSM o non ASCII, prova a inviare alcuni messaggi con il maggior numero possibile di caratteri diversi. Se imposti una tabella di mappatura caratteri personalizzata, invia almeno un SMS per tutti i possibili valori `data_coding`.

* **Verifica che i messaggi SR siano elaborati correttamente**
L’SMS deve essere contrassegnato come ricevuto nel registro di consegna. Il registro di consegna deve avere esito positivo e avere un aspetto simile al seguente:
  `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Verifica di aver modificato il nome del provider di consegna. Il registro di consegna non deve mai contenere **SR Generic** negli ambienti di produzione.

* **Verifica che MO siano elaborati**
Se hai bisogno di elaborare il MO (risposte automatiche, memorizzazione del MO nel database, ecc.) prova a fare alcuni test. Invia alcuni SMS per tutte le parole chiave di risposta automatica e controlla se la risposta è abbastanza veloce, non più di qualche secondo.
Archivia il registro che Adobe Campaign risponde con un `DELIVER_SM_RESP` (command_status=0) riuscito.

### Controllare le PDU {#check-pdus}

Anche se i messaggi hanno un aspetto positivo, è importante verificare che le PDU siano formattate correttamente.

Questo passaggio è necessario per la connessione a un provider che in precedenza non era connesso ad Adobe Campaign.

#### BINDING {#bind}

Verificare che `BIND_* PDUs` siano inviati correttamente. La cosa più importante da verificare è che il provider restituisca sempre `BIND_*_RESP PDUs` (command_status = 0).

Verifica che non siano presenti troppi `BIND_* PDU`. Se ne sono presenti troppi, potrebbe indicare che la connessione è instabile. Per ulteriori informazioni, vedere la sezione [Problemi relativi alle connessioni instabili](sms-protocol.md#issues-unstable-connection).

#### INQUIRE_LINK {#enquire-link-pdus}

Controlla che `ENQUIRE_LINK PDU` vengano scambiati regolarmente quando la connessione è inattiva.

**SUBMIT_SM / DELIVER_SM**

Invia un messaggio, quindi cerca nei registri i corrispondenti `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` e `DELIVER_SM_RESP PDU`.

Con `SUBMIT_SM PDU`:

* Verificare che `data_coding` sia corretto, 0 per impostazione predefinita.
* Verificare che `short_message` sia codificato correttamente. Prova a decodificarlo utilizzando un convertitore esadecimale che supporta più codifiche.

Con `SUBMIT_SM_RESP PDU`:

* Verifica che sia stato eseguito correttamente, command_status = 0.
* Verifica che il corpo della stringa contenga un ID formattato correttamente seguito da un byte &quot;0&quot;.

Con `DELIVER_SM PDU`:

* Decodificare il campo esadecimale `short_message`.
* Verificare con uno strumento di controllo regex che il regex definito in `Extraction` regex dell&#39;ID nell&#39;SR restituisca esattamente un gruppo di acquisizione e che acquisisca l&#39;intero ID nel messaggio.
* Verificare che l&#39;ID estratto corrisponda a quello in `SUBMIT_SM_RESP`.
* Verificare che il regex definito in `Extraction` regex dello stato nell&#39;SR restituisca il contenuto del campo stat.
* Verificare che il regex definito in `Extraction` regex dell&#39;errore nell&#39;SR restituisca il contenuto del campo err.

Con `DELIVER_SM_RESP PDU`:

* Verificare che sia stato inviato rapidamente dopo aver ricevuto `DELIVER_SM PDU`, in genere meno di 1 secondo.
* Verifica che sia stato eseguito correttamente, command_status = 0.

### Verifica con il provider {#provider}

Anche se l’SMS ha esito positivo, contatta il provider per verificare se è tutto in ordine.

### Disattiva tracce SMPP dettagliate {#disable-verbose}

Una volta completati tutti i controlli, l&#39;ultima cosa è **Disabilitare le tracce SMPP verbose** per non generare troppi registri. Puoi abilitarli di nuovo per la risoluzione dei problemi anche sui sistemi di produzione.
