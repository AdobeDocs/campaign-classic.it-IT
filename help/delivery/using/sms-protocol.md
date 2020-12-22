---
solution: Campaign Classic
product: campaign
title: Protocollo e impostazioni del connettore SMS
description: Ulteriori informazioni sul connettore SMS e come configurarlo.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 8f45fcc57062e6f13bc674c72f53788483de93fb
workflow-type: tm+mt
source-wordcount: '8399'
ht-degree: 0%

---

# Protocollo e impostazioni del connettore SMS {#sms-connector-protocol}

>[!NOTE]
>
>In questo documento, tutti i riferimenti a dettagli sul protocollo, nomi e valori dei campi fanno riferimento alla [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

## Panoramica {#overview}

SMS potrebbe essere limitato all&#39;invio di messaggi di testo brevi senza formattazione, ma la sua semplicità lo rende un canale di comunicazione prezioso.

Esistono due modi principali per inviare un SMS:

* Inviatelo manualmente da un telefono, il modo usuale per comunicare direttamente tra le persone.
* Inviatelo da Internet, come  Adobe Campaign invia messaggi. Per questo, è necessario un provider di servizi SMS che connetta Internet alla rete mobile.
 Adobe Campaign utilizza il protocollo SMPP per inviare SMS a un provider di servizi.

Questo documento illustra la connessione impostata tra  Adobe Campaign e un provider SMPP.

I fornitori SMPP a volte possono deviare dalle specifiche ufficiali, ma il connettore SMS in  Adobe Campaign offre molte opzioni per adattare il suo comportamento affinché sia compatibile con la maggior parte dei fornitori.

>[!IMPORTANT]
>
>La configurazione di una connessione a un nuovo provider potrebbe richiedere alcune competenze tecniche, conoscenza di TCP, binario, rappresentazione esadecimale e codifiche di testo. Sarà inoltre necessaria una collaborazione attiva con il fornitore.

### Tipi di SMS {#sms-types}

Quando si invia SMS di massa attraverso un fornitore di SMS, si incontreranno tre diversi tipi di SMS:

* **SMS MT (Mobile Terminated)**: un SMS emesso da  Adobe Campaign verso i telefoni cellulari tramite il provider SMPP.

* **SMS MO (Mobile Originato)**: un SMS inviato da un dispositivo mobile a  Adobe Campaign tramite il provider SMPP.

* **SMS SR (Stato Report), DR o DLR (Consegna consegna)**: una ricevuta di ritorno inviata dal dispositivo mobile a  Adobe Campaign tramite il provider SMPP per indicare che l&#39;SMS è stato ricevuto correttamente.  Adobe Campaign potrebbe inoltre ricevere SR che indica che il messaggio non è stato recapitato, spesso con una descrizione dell&#39;errore.

È necessario distinguere tra riconoscimenti (RESP PDU, parte del protocollo SMPP) e SR: SR è un tipo di SMS che viene inviato attraverso la rete end-to-end, mentre un riconoscimento è solo una conferma che un trasferimento ha avuto successo.

Entrambi i riconoscimenti e i SR possono causare errori, distinguendo tra i due aiuterà a risolvere i problemi.

### Informazioni trasportate da un SMS {#information-sms}

Un SMS contiene più informazioni che testo. Di seguito è riportato un elenco di ciò che ci si può aspettare in un SMS:

* Il testo, che è limitato a 140 byte, ovvero tra 70 e 160 caratteri a seconda della codifica. Per informazioni dettagliate e limitazioni, vedere [Codifica di testo SMS](../../delivery/using/sms-protocol.md#sms-text-encoding) di seguito.

* Un indirizzo destinatario, a volte denominato `ADC` o `MSISDN`. Questo è il numero del cellulare che riceverà l&#39;SMS.

* Un indirizzo del mittente, che può essere chiamato `oADC` o a volte `sender id`. Può trattarsi di un numero di telefono utilizzato giorno per giorno, di un codice breve inviato tramite un provider o un nome. Nome è una funzione opzionale, in tal caso non è possibile rispondere all&#39;SMS.

* Flag che indica se il messaggio è un messaggio Flash. Un messaggio Flash è un messaggio pop-up che non è memorizzato nella memoria.

* Flag che indica se un SR è previsto o meno.

* Una data di validità, dopo la quale non è consentito riprovare alcuna attrezzatura di rete.

* Un campo `data_coding` che indica la codifica del testo.

## Protocollo SMPP {#smpp-protocol}

Adobe Campaign Classic supporta il protocollo SMPP versione 3.4. Si tratta di un protocollo diffuso che consente l&#39;invio di SMS a un provider (SMSC), la ricezione di SMS e ricevute. Per ulteriori informazioni, consultare la [documentazione SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Le apparecchiature di rete sul lato del fornitore di servizi di SMS sono spesso chiamate SMSC.

### Connessioni SMPP {#smpp-connections}

 Adobe Campaign si collega alle apparecchiature di rete del provider di servizi SMS tramite TCP. Il protocollo SMPP imposta connessioni TCP permanenti da  Adobe Campaign al provider. Le connessioni TCP vengono sempre avviate da  Adobe Campaign, anche per ricevere messaggi.
SMPP apre 1 o 2 connessioni TCP, a seconda della modalità. Tutte le connessioni sono sempre avviate da  Adobe Campaign.

Il protocollo SMPP può funzionare in due modalità:

* **Trasmettitore+ricevitore (o TX+RX)**: per la trasmissione e la ricezione dei messaggi vengono utilizzate due diverse connessioni TCP.
* **Transciver (o TRX)**: per la trasmissione e la ricezione dei messaggi viene utilizzata una singola connessione TCP.

>[!NOTE]
>
> Adobe Campaign Classic supporta solo la modalità TX+RX. Questa limitazione è dovuta alla sua architettura tecnica.

### PDU SMPP {#smpp-pdu}

Le unità di trasmissione SMPP (&quot;pacchetti&quot;) sono denominate PDU. Un **PDU** contiene un comando, uno stato, un numero di sequenza e dati.

Ciascuna PDU deve essere riconosciuta da un `SMPP RESP PDU` (risposta sincrona). Le richieste possono essere inoltrate: il mittente può inviare molti comandi senza attendere `RESP`, il numero di richieste che possono essere inoltrate in qualsiasi momento è chiamato finestra. `RESP PDU` possono arrivare in qualsiasi ordine, non collegato all&#39;ordine della corrispondente PDU iniziatore.

Nella modalità **Trasmettitore+ricevitore** separata, la connessione utilizzata dipende dal tipo di messaggio trasmesso. La connessione del trasmettitore viene utilizzata per MT e la connessione del ricevitore viene utilizzata per MO e SR. Richieste e risposte per ogni tipo di messaggio vengono inviate attraverso la stessa connessione TCP.

Ad esempio, quando si invia un MT, viene utilizzata la connessione del trasmettitore e la `RESP` che riconosce che il MT viene inviato anche attraverso il canale del trasmettitore. Quando si riceve un MO (o un SR), la connessione del ricevitore viene utilizzata per ricevere il MO e inviare il `RESP` che riconosce il MO.

![](assets/sms_protocol_1.png)

In Adobe Campaign Classic, per collegare SR con il corrispondente MT, l&#39;SMSC restituisce un ID con i passaggi `SUBMIT_SM_RESP` e `DELIVER_SM`. L&#39;identificatore è memorizzato nel campo `providerId` della tabella `nms::providerMsgId` ed è collegato a `broadLogId` e `deliveryId`. Questa operazione di corrispondenza viene eseguita dal processo SMS durante la scrittura nel database.

Un `SUBMIT_SM_RESP PDU` riuscito attiva lo stato del messaggio &quot;inviato&quot; nel registro di invio mentre un `DELIVER_SM (SR) PDU` riuscito attiva lo stato del messaggio &quot;ricevuto&quot;.

### Aspetti di sicurezza {#security-aspects}

Il protocollo stesso non è crittografato. La maggior parte dei provider implementa una variante di IP  inserire nell&#39;elenco Consentiti, pertanto  gli indirizzi IP del server Adobe Campaign devono essere dichiarati al provider.

 Adobe Campaign supporta il passaggio di un login e una password durante la fase di binding. Supporta inoltre SMPP su TLS. Va notato che i certificati sono richiesti per una sicurezza adeguata. Anche se il connettore SMPP consente di bypassare i controlli dei certificati, dovrebbe essere utilizzato solo per il test, dal momento che TLS senza certificati fornisce un livello di protezione significativamente inferiore.

Il connettore utilizza i certificati predefiniti forniti dalla libreria di sistema `openssl`. Di solito è fornito dalla directory `/etc/ssl/certs` su Debian. Questa directory è fornita per impostazione predefinita dal pacchetto &quot;ca-certificates&quot;, ma può essere personalizzata.

### Informazioni in ogni tipo di PDU {#information-pdu}

Ogni tipo di PDU ha campi distinti che contengono informazioni diverse. Queste PDU sono descritte dettagliatamente nella [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Ogni sezione seguente descrive sia la PDU che la risposta sincrona (`*_RESP PDU`). Tutte le PDU devono essere riconosciute da una `RESP` corrispondente, che è una parte obbligatoria della specifica.

Le PDU possono avere campi facoltativi. Qui sono descritti solo i campi più comuni. Per ulteriori informazioni, fare riferimento alla [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Questa PDU viene utilizzata per avviare una connessione con SMSC. **Trasmettitore**,  **** Ricezione e  **** Trasmettitori cambia solo il tipo di SMS consentito per il trasferimento su questa connessione, in particolare:

| Modalità | Tipi di SMS consentiti |
|:-:|:-:|
| Trasmettitore | MT |
| Ricevitore | MO + SR |
| Ricetrasmettitore | MT + MO + SR |

Campi di rilievo in `BIND_* PDU`:

* **system_id**: Login utilizzato per l&#39;autenticazione. Impostato nell’account esterno.

* **password**: Password utilizzata per l&#39;autenticazione. Impostato nell’account esterno.

* **system_type**: Obbligatorio per essere impostato su un valore specifico per alcuni provider. Impostato nell&#39;account esterno, disponibile in tutte le versioni. Spesso distingue tra diversi tipi di contratti, canali, paesi, ecc.

* **addr_** tonand  **addr_npi**: Richiesto da alcuni provider. Impostato dalle impostazioni `Bind TON` e `Bind NPI` nell&#39;account esterno.

* **address_range**: Richiesto da alcuni provider. Nella maggior parte dei casi, si tratta di un elenco di codici di scelta rapida consentiti in questa connessione. Impostato nell’account esterno.

`BIND_*_RESP` non ha un campo specifico, conferma se la connessione è stata eseguita correttamente o meno.

#### UNBIND {#unbind}

La PDU deve essere inviata dal sistema prima della disconnessione. Deve attendere la `UNBIND_RESP` PDU corrispondente prima di chiudere la connessione.

La connessione SMSC conforme non deve essere chiusa. La connessione TCP è controllata dal connettore Adobe Campaign .

#### SUBMIT_SM {#submit-sm}

Questa PDU invia un MT al SMSC. La sua PDU di risposta fornisce l&#39;ID del MT.

Campi principali in una `SUBMIT_SM` PDU:

* **service_type**: richiesto da alcuni fornitori. Impostate le proprietà di consegna.

* **source_addr_** tonand  **source_addr_npi**: indica il tipo di indirizzo di origine trasmesso. Il significato di questi campi è standardizzato, ma poiché alcuni fornitori li utilizzano in modo diverso, è necessario chiedere al provider il valore corretto. Impostato nell’account esterno.

* **source_addr**: l&#39;indirizzo di origine / oADC del MT. Verrà visualizzato sul cellulare. Impostato nel conto esterno e nella consegna, il valore nella consegna ha la precedenza sul valore del conto esterno.

* **dest_addr_** tonand  **dest_addr_npi**: indica quale tipo di indirizzo di destinazione viene trasmesso (ad esempio, formato locale o internazionale). Il significato di questi campi è standardizzato, ma poiché alcuni fornitori li utilizzano in modo diverso, è necessario chiedere al provider il valore corretto. Impostato nell’account esterno.

* **Destination_addr**: indirizzo del destinatario, numero di telefono o MSISDN.

* **esm_class**: utilizzato per indicare se l&#39;UDH è utilizzato o meno nel campo di testo. Abilitato automaticamente dal connettore per SMS diviso se la modalità `message_payload` non è utilizzata.

* **priority_flag**: priorità di questo messaggio rispetto agli altri. Ciò è legato alla priorità della consegna stessa.

* **validation_period**: marca temporale dopo la quale non è necessario tentare alcun tentativo. Impostato nella consegna stessa.

* **registrato_delivery**: indica se una SR è richiesta o meno.  Adobe Campaign imposta sempre questo flag, ad eccezione delle risposte automatiche. Per i messaggi multiparte, il flag è impostato solo per la prima parte. Tutte le versioni hanno lo stesso comportamento.

* **data_coding**: indica la codifica utilizzata nel campo di testo. Per ulteriori informazioni, vedere la sezione [Codifica di testo SMS](../../delivery/using/sms-protocol.md#sms-text-encoding).

* **short_message**: il testo del messaggio. Se viene utilizzato UDH, questo contiene anche l’intestazione UHD.

 Adobe Campaign supporta i seguenti campi facoltativi:

* **dest_addr_subunit**: utilizzato per specificare il target dell&#39;SMS: scheda flash, mobile o SIM. Impostate le proprietà di consegna.

* **message_payload**: se attivato nell&#39;account esterno, i messaggi lunghi saranno inviati in un&#39;unica PDU e il testo verrà trasmesso in questo campo anziché nel  `short_message` campo.

#### SUBMIT_SM_RESP {#submit-sm-resp}

La PDU conterrà l&#39;ID del MT. Questo è utile per abbinarlo con SR in ingresso.

>[!IMPORTANT]
>
>Molti provider trasmettono l’ID MT in formato esadecimale. Accertatevi di impostare correttamente il formato **ID in corrispondenza MT** nell&#39;account esterno.

Alcuni fornitori inviano `SUBMIT_SM_RESP` dopo l&#39;invio dell&#39;SR. Per tenere conto di tale comportamento,  Adobe Campaign attende 30 secondi prima di rispondere a **ID messaggio** non valido a un SR con un ID sconosciuto.

#### DELIVER_SM {#delivery-sm}

Il PDU viene inviato da SMSC a  Adobe Campaign. Contiene un MO o una SR.

La maggior parte dei campi ha lo stesso significato della controparte `SUBMIT_SM`. Elenco di campi utili:

* **source_addr**: indirizzo di origine del MO/SR. Di solito questo è un numero di telefono.

* **Destination_addr**: codice breve che ha ricevuto il MO o la SR.

* **esm_class**: utilizzato per indicare se la PDU è un MO o un SR.

* **short_message**: testo del messaggio. Per SR, questo contiene i dati descritti nell&#39;appendice B della specifica del protocollo SMPP. Per ulteriori informazioni, vedere [Gestione errori SR](../../delivery/using/sms-protocol.md#sr-error-management).

 Adobe Campaign è in grado di leggere l&#39;ID del messaggio nel campo opzionale `receipted_message_id` con alcune configurazioni.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Questa PDU viene inviata da  Adobe Campaign per confermare SR e MO.

Adobe Campaign Classic riconosce SR e MO una volta inseriti nel database. Alcuni errori di elaborazione possono verificarsi anche se è stata inviata correttamente una `DELIVER_SM_RESP` PDU. Questa limitazione è causata dall&#39;architettura software di Adobe Campaign Classic.

#### INQUIRE_LINK {#enquire-links}

Questa PDU viene utilizzata solo per verificare che la connessione sia attiva. La sua frequenza deve essere fissata in base alle esigenze del fornitore.

I 60 secondi predefiniti devono corrispondere alla maggior parte delle configurazioni impostate nell&#39;account esterno.

#### INQUIRE_LINK_RESP {#enquire-links-resp}

Questa PDU riconosce che la connessione è attiva.

### SMS multiparte (SMS esteso) {#multipart}

Gli SMS multiparte, o gli SMS lunghi, sono SMS inviati in più parti. A causa di limiti tecnici nel protocollo di rete mobile, un SMS non può essere maggiore di 140 byte o dovrà essere suddiviso. Per ulteriori informazioni sul numero di caratteri che possono essere inclusi in un SMS, vedere la sezione [Codifica di testo SMS](../../delivery/using/sms-protocol.md#sms-text-encoding).

Ogni parte di un lungo messaggio è un singolo SMS. Queste parti viaggiano in modo indipendente sulla rete e sono assemblate dal telefono cellulare ricevente. Per gestire i tentativi e i problemi di connettività,  Adobe Campaign invia queste parti in ordine inverso e richiede un SR solo per la prima parte del messaggio, l&#39;ultimo inviato. Poiché il telefono cellulare visualizza un messaggio solo quando viene ricevuta la prima parte, i tentativi su parti aggiuntive non generano duplicati sul telefono cellulare.

Il numero massimo di SMS per messaggio può essere impostato per consegna utilizzando l&#39;impostazione **Numero massimo di SMS per messaggio** nel **modello di consegna**. I messaggi che superano questo limite non riusciranno durante l&#39;invio con un SMS per un motivo di errore troppo lungo.

Ci sono 2 modi per inviare SMS lunghi:

* **UDH**: il modo predefinito e consigliato per inviare messaggi lunghi. In questa modalità, il connettore divide il messaggio in più `SUBMIT_SM PDU`s con le informazioni UDH al loro interno. Questo protocollo è quello utilizzato dagli stessi telefoni cellulari. Ciò significa che  Adobe Campaign ha il maggior controllo sulla generazione dei messaggi, rendendola in grado di calcolare esattamente quante parti sono state inviate e come sono state divise.

* **message_payload**: il modo di inviare l&#39;intero lungo messaggio in un solo  `SUBMIT_SM PDU`. Il fornitore dovrà dividerlo, il che significa che è impossibile per  Adobe Campaign sapere esattamente quante parti sono state inviate. Alcuni fornitori richiedono questa modalità, ma consigliamo di utilizzarla solo se non supportano UDH.

Per ulteriori informazioni sul protocollo e i formati, vedere la descrizione dei campi `esm_class`, `short_message` e `message_payload` della [SUBMIT_SM PDU](../../delivery/using/sms-protocol.md#information-pdu).

### Limite di carico e finestra {#throughput-capping}

La maggior parte dei fornitori richiede un limite di throughput per ogni connessione SMPP. Questo può essere ottenuto impostando un numero di SMS nell&#39;account esterno. Si noti che la velocità di trasmissione avviene per connessione, la velocità effettiva totale è il limite per connessione moltiplicato per il numero totale di connessioni. Questo è illustrato nella sezione [Connessioni simultanee](../../delivery/using/sms-protocol.md#connection-settings).

Per raggiungere la massima velocità possibile, dovrete regolare la finestra massima di invio. La finestra di invio è il numero di `SUBMIT_SM PDU`s che possono essere inviati senza aspettare un `SUBMIT_SM_RESP`. Per ulteriori informazioni, vedere la sezione [Impostazione della finestra di invio](../../delivery/using/sms-protocol.md#throughput-timeouts).

### SR e gestione degli errori (&quot;Appendice B&quot;) {#sr-error-management}

Il protocollo SMPP definisce gli errori sincroni standard in `RESP PDU`s, ma non definisce i codici di errore per SR. Ogni provider utilizza i propri codici di errore con il proprio significato.

Una raccomandazione è fatta nella sezione Appendice B della specifica del protocollo [SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pagina 167), ma non elenca i codici di errore effettivi né il loro significato.

Per adattarsi alla gestione degli errori, il sistema di trasmissione dei messaggi di  Adobe Campaign è stato sfruttato per fornire correttamente gli errori e la loro gravità (duro, morbido, ecc.).

Come già detto, vi sono due tipi diversi di errori:

* risposte sincrone nella `SUBMIT_SM_RESP` che si verificano immediatamente dopo l&#39;invio del messaggio all&#39;SMSC
* le ricevute che potrebbero essere visualizzate più tardi quando il dispositivo mobile ha ricevuto il messaggio o quando il messaggio è scaduto. In tal caso l&#39;errore si trova in un SR.

Quando viene ricevuta una SR, lo stato e l&#39;errore si trovano nel relativo campo `short_message` (ad esempio per le implementazioni conformi all&#39;appendice B). Il campo `short_message` della PDU è spesso denominato **campo di testo** poiché contiene testo in MT. In caso di SR, contiene informazioni tecniche più un sottocampo denominato **Text**. Questi due campi sono diversi e `short_message` contiene effettivamente il campo **Text** e altre informazioni.

I connettori Adobe Campaign Classic (eccetto Extended SMPP) utilizzano un comportamento hardcoded che dipende dal provider selezionato. SMPP generico distingue solo tra successo ed errore, senza alcun dettaglio. Il registro di consegna può contenere alcune informazioni non garantite.

#### Formato del campo di testo SR {#sr-text-field-format}

Si consiglia di utilizzare questo formato per il campo di testo SR. Si tratta di un elenco di campi secondari, separati da spazi con due punti per separare il nome del campo e il relativo valore. I nomi dei campi non fanno distinzione tra maiuscole e minuscole.

Esempio di un campo di testo SR che corrisponde alla raccomandazione dell&#39;appendice B:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Il campo id è l&#39;ID ricevuto nella `SUBMIT_SM_RESP PDU`, la conferma dell&#39;MT.

`sub` e  `dlvrd` devono contare la quantità di parti consegnate e di messaggi consegnati, ma questo non viene utilizzato da  Adobe Campaign, dal momento che il sistema di trasmissione offre informazioni migliori e più integrate.

`submit date` e  `done date` i campi sono marche temporali indicative di quando il MT è stato inviato e quando l&#39;SR è stato inviato dal cellulare. Ci si aspetta qualche problema con i fusi orari o anche con marche temporali errate date da cellulari con data non corretta.

Il campo stat è importante perché indica lo stato del messaggio. L&#39;unico stato importante sono `DELIVRD`, `UNDELIV` e `REJECTD`. Lo stato `DELIVRD` indica un esito positivo, mentre gli altri due indicano un errore. Altri valori sono possibili, ma di solito sono notifiche intermedie, ad esempio il MT ha raggiunto il vettore mobile, ma non il cellulare. Queste notifiche intermedie vengono ignorate da  Adobe Campaign.

Il campo err contiene il codice di errore specifico del provider. Il provider deve fornire una tabella di possibili codici di errore con il relativo significato per essere in grado di interpretare questo valore.

Infine, il campo di testo in genere contiene l&#39;inizio del testo del MT. Questo viene ignorato da  Adobe Campaign e alcuni fornitori non lo trasmettono per evitare perdite di PII e il consumo di larghezza di banda della rete. Può essere utilizzato durante la risoluzione dei problemi per individuare più facilmente la SR che corrisponde a un MT di prova leggendo questo campo.

### Esempio di elaborazione SR in Adobe Campaign Classic Extended SMPP generico {#sr-processing}

In questo esempio viene visualizzato il caso di un&#39;implementazione successiva alla raccomandazione Appendice B, i valori predefiniti nell&#39;account esterno e un SMS MT con esito positivo.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Innanzitutto, il regex `id extraction` viene applicato per estrarre l&#39;ID e riconciliarlo con il MT corrispondente.

Quindi, i campi `status extraction` regex e `error code extraction` regex vengono applicati per estrarre questi campi e aggiunti alla stringa.

Il messaggio di broadcast viene creato con queste informazioni e la stringa originale non modificata viene aggiunta come riferimento:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Il messaggio viene quindi normalizzato, rimuovendo la parte MESSAGE per essere in grado di far corrispondere più messaggi con gli stessi codici di stato e di errore.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Se il messaggio non è già stato fornito nella tabella dei messaggi di trasmissione, verrà creata una nuova voce utilizzando l&#39;intero messaggio come **firstText** e il messaggio normalizzato. Quindi, il connettore utilizza il formato success e `error` regex per determinare se si è trattato di un esito positivo o negativo:

* Se corrisponde al regex `success`, verrà considerato un successo.

* Se corrisponde al regex `error`, il messaggio viene qualificato come errore.

* Se nessuno di questi due regex corrisponde, l&#39;SR viene ignorato. Potrebbe trattarsi di una notifica intermedia, che non viene gestita da  Adobe Campaign.

Per impostazione predefinita, tutti gli errori vengono forniti come errori software. Ciò significa che gli errori gravi devono essere forniti a mano.

### Codifica di testo SMS {#sms-text-encoding}

È necessario **contattare sempre il provider SMSC in caso di problemi di codifica**. Solo i fornitori SMSC sono a conoscenza della codifica che supportano e delle regole speciali che possono essere applicate a causa di limitazioni nella loro piattaforma tecnica.

I messaggi SMS utilizzano una codifica speciale a 7 bit, spesso denominata codifica GSM7.

Nel protocollo SMPP, il testo GSM7 verrà espanso a 8 bit per carattere per facilitare la risoluzione dei problemi. SMSC lo impacchetterà in 7 bit per carattere prima di inviarlo al dispositivo mobile. Ciò significa che il campo `short_message` dell&#39;SMS può avere una lunghezza massima di 160 byte nel frame SMPP, mentre è limitato a 140 byte quando viene inviato sulla rete mobile.

In caso di problemi di codifica, è necessario verificare alcuni aspetti importanti:

* Accertatevi di sapere quali caratteri appartengono a quale codifica. GSM7 non supporta completamente i segni diacritici o gli accenti. Specialmente in francese, dove é ed è fanno parte del GSM7, ma ê, o ï no. Lo stesso vale per lo spagnolo.

* Il C con cedilla (ç) è presente solo in lettere maiuscole nell’alfabeto GSM7, ma alcuni telefoni lo rendono in lettere minuscole o &quot;smart&quot;. La raccomandazione generale è di evitarlo completamente e rimuovere il cedilla o passare a UCS-2.

* **Non utilizzare ASCII in** SMS, a meno che non sia espressamente richiesto dal provider SMSC. Questa codifica consente di sprecare spazio perché contiene caratteri a 8 bit e una copertura inferiore rispetto a GSM7. Questa codifica può essere necessaria per le reti CDMA, utilizzate in America del Nord.

* Latin-1 non è sempre supportato. Verificare la compatibilità con il provider SMSC prima di tentare di utilizzare Latin-1.

* Le tabelle di spostamento della lingua nazionale non sono supportate dal connettore Adobe Campaign . È necessario utilizzare UCS-2 o altro `data_coding`.

* UCS-2 e UTF-16 sono spesso mescolati dai telefoni. Questo è un problema quando si utilizzano emoji e altri caratteri non presenti nell&#39;UCS-2.

* La maggior parte dei telefoni non dispone di glifi di font per tutti i caratteri UCS-2. Gli smartphone tendono ad essere in grado di visualizzare caratteri rari piuttosto facilmente, ma i cellulari con caratteristiche generalmente hanno un supporto limitato a ciò che è utile nella lingua nativa del paese in cui sono stati acquistati. Se desiderate utilizzare emoji o ASCII-art, testatela su un&#39;ampia varietà di telefoni prima di inviarla.  anteprima Adobe Campaign non simula i glifi mancanti e visualizzerà i simboli disponibili nel browser Web.

Il campo `data_coding` indica la codifica utilizzata. Un problema importante è che il valore 0 indica la codifica SMSC predefinita nella specifica, che in genere si riferisce a GSM7. Verificare con il partner SMSC quale codifica è associata a `data_coding` = 0 che  solo Adobe Campaign supporta. Altri valori `data_coding` tendono a seguire la specifica, ma l&#39;unico modo per essere certi è di controllare con il provider SMSC.

La dimensione massima di un messaggio dipende dalla codifica. Questa tabella riassume tutte le informazioni pertinenti:

| Codifica | Solito data_coding | Dimensione del messaggio (caratteri) | Dimensioni parte per SMS multiparte | Caratteri disponibili |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | GSM7 set di caratteri di base + estensione (i caratteri estesi prendono 2 caratteri) |
| Latin-1 | 1 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (varia da telefono a telefono) |

## Parametri del conto esterno SMPP {#SMPP-parameters-external}

Ogni implementazione del protocollo SMPP presenta numerose variazioni. Per migliorare la compatibilità e l&#39;adattabilità, sono disponibili diverse impostazioni per modificare il comportamento del connettore SMPP. Questa sezione descrive ogni parametro e i relativi effetti sul connettore.

### Parametri generali e routing {#general-parameters-routing}

**Limita le istanze MTA per l&#39;account**

È possibile impostare un limite al numero di istanze MTA consentite per connettersi al provider SMPP. Se questa opzione è selezionata, potete specificare il numero massimo di MTA utilizzabili.

Questa opzione consente un controllo più preciso del numero di connessioni, vedere [Connessioni simultanee](../../delivery/using/sms-protocol.md#connection-settings).

Se imposti un valore maggiore del numero di MTA in esecuzione, tutti i MTA verranno eseguiti normalmente: questa opzione è solo un limite e non può generare ulteriori MTA.

Se è necessario controllare con precisione il numero di connessioni, ad esempio il requisito del fornitore, si consiglia di impostare sempre questa opzione anche se la distribuzione corrente ha il numero corretto di MTA in esecuzione. Se successivamente verranno aggiunte ulteriori MTA, il limite di connessione sarà comunque rispettato.

### Impostazioni di connessione {#connection-settings}

#### Nome implementazione SMSC {#smsc-implementation-name}

Definisce il nome dell&#39;implementazione SMSC. Deve essere impostato sul nome del provider. Contatta l’amministratore o il team di recapito per sapere cosa aggiungere in questo campo. Il ruolo di questo campo è descritto nella sezione [Gestione errori SR](../../delivery/using/sms-protocol.md#sr-error-management).

#### Server {#server}

Nome DNS o indirizzo IP del server a cui connettersi.

#### Porta {#port}

La porta TCP a cui connettersi.

#### Account {#account}

Login della connessione. Trasmesso nel campo `system_id` della PDU BIND.

#### Password {#password}

Password della connessione SMPP. Trasmesso nel campo password della BIND PDU.

#### Tipo di sistema {#system-type}

Valore passato nel campo `system_id` della PDU BIND. Alcuni fornitori necessitano di un valore specifico.

#### Numero di connessioni figlio MTA {#number-mta-child}

In Adobe Campaign Classic, definisce il numero di connessioni per figlio MTA.

Il connettore SMPP esteso Adobe Campaign Classic può controllare il numero di connessioni per figlio MTA. Per controllare il limite globale di connessioni, dovrete limitare il numero di processi figlio MTA, che spesso significa avere una piattaforma mid-sourcing dedicata per SMS.

Per Adobe Campaign Classic, può essere presente un numero diverso di connessioni di ricevitore e trasmettitore:

* **Connessioni del trasmettitore = numero di connessioni figlio MTA * numero di processi figlio MTA * numero di MTA (se è impostata la risposta automatica) + numero di connessioni figlio MTA**

Come suggerito in precedenza, il processo Adobe Campaign Classic SMS apre più connessioni di trasmettitore se la risposta automatica è abilitata. Queste connessioni aggiuntive vengono utilizzate per inviare le risposte automatiche.

* **Connessioni ricevitore = numero di connessioni figlio MTA**

Se si impostano le risposte automatiche, il processo SMS aprirà coppie trasmettitore/ricevitore, aumentando il numero di connessioni del trasmettitore. Se non hai impostato alcuna risposta automatica, aprirà solo le connessioni del ricevitore.

#### Abilita TLS su SMPP {#enable-TLS}

Utilizzate TLS per la connessione al provider. La connessione sarà crittografata. La connessione TLS è gestita dalla libreria OpenSSL, tutto ciò che è applicabile a OpenSSL è vero per questa connessione.

#### Abilitare tracce SMPP dettagliate nel file di registro {#enable-verbose-log-file}

Questa impostazione scarica tutto il traffico SMPP nei file di registro. Spesso è necessario regolare i parametri durante la configurazione iniziale. Questa opzione deve essere abilitata per la risoluzione dei problemi relativi al connettore e confrontata con il traffico visualizzato dal provider.

In Adobe Campaign Classic, l&#39;output di registro è nel registro MTA per il traffico correlato a MT e nel registro SMS per il traffico correlato a MO e SR.

### Impostazione connessione ricevitore {#receiver-connection}

Questa sezione è visibile solo in modalità **trasmettitore+ricevitore** separata.

#### Utilizzare parametri diversi per il ricevitore {#receiver-parameters}

Quando la casella è deselezionata, le stesse impostazioni vengono utilizzate per il trasmettitore e il ricevitore.

Quando la casella è selezionata, le impostazioni della sezione **Impostazioni di connessione** si applicano al trasmettitore e le impostazioni della **Connessione ricevitore** si applicano al ricevitore.

**Server di ricezione, porta, account, password, tipo di sistema**

Queste impostazioni si applicano al ricevitore in modalità trasmettitore+ricevitore. Funzionano come la parte del trasmettitore, vedi sopra per maggiori dettagli.

### Impostazioni canale SMPP {#smpp-channel-settings}

#### Consenti traslitterazione caratteri {#allow-character-transliteration}

Transliteration è il processo di ricerca di caratteri equivalenti a quelli mancanti. Ad esempio, il carattere francese &quot;ê&quot; (con accento circonflesso) non è presente nella codifica GSM, ma può essere sostituito da &quot;e&quot; senza compromettere la leggibilità.

Se questa casella è deselezionata, la codifica del testo non riuscirà se non sarà in grado di codificare la stringa esattamente come è.

Quando questa casella è selezionata, la codifica del testo tenterà di convertire la stringa in una versione approssimativa anziché in errore. Se alcuni caratteri non hanno un equivalente nella codifica di destinazione, la codifica del testo non riuscirà.

Per una spiegazione più generale del processo di codifica, vedere [Definire una mappatura specifica delle impostazioni di codifica](../../delivery/using/sms-protocol.md#SMSC-specifics).

#### Archiviare l&#39;MO in entrata nel database {#incoming-mo-storing}

Se abilitata, la MO in entrata verrà memorizzata nella tabella inSMS del database. Questa tabella può essere interrogata utilizzando l&#39;attività di query di qualsiasi flusso di lavoro.

Adobe Campaign Classic memorizza sempre tutte le MOs nel database inSMS, quindi questa opzione non è disponibile.

#### Abilitare gli aggiornamenti KPI in tempo reale durante l&#39;elaborazione SR {#real-time-kpi}

Se attivato, i KPI verranno aggiornati in tempo reale sulla pagina di consegna principale quando viene visualizzato un SR di errore.

L&#39;inconveniente può essere a basse prestazioni a causa del contenzioso del database generato. Se disabilitata, le statistiche vengono aggiornate dal flusso di lavoro **syncfromexec**, che viene eseguito ogni 20 minuti.

Adobe Campaign Classic dispone di un meccanismo completamente diverso per i KPI, pertanto questa opzione non è disponibile.

#### Numero di origine {#source-number}

Definisce l&#39;indirizzo di origine predefinito per i messaggi. Questa impostazione è valida solo se il numero di origine è rimasto vuoto nella consegna.

Per impostazione predefinita, il campo relativo al numero di origine non viene passato, pertanto il provider lo sostituirà al codice breve.

Questo abilita la funzione di sostituzione indirizzo del mittente/oADC.

#### Codice breve {#short-code}

Indica il codice breve principale del conto. Se per questo account sono utilizzati più codici brevi o se il codice breve è sconosciuto, lasciare vuoto questo campo.

La specifica del codice breve è utile per due funzioni:

* Nell&#39;anteprima viene visualizzato il codice breve se non viene fornito alcun numero di origine. Rifletterà il comportamento reale sul cellulare.

* L&#39;impostazione di inserire nell&#39;elenco Bloccati  della funzione di risposta automatica invia solo all&#39;utente la quarantena per un codice breve specifico.

#### TON/NPI di origine, TON/NPI di destinazione {#ton-npi}

TON (Tipo di numero) e NPI (Indicatore del piano di numerazione) sono descritti nella sezione 5.2.5 della [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pagina 117). Questi valori devono essere impostati in base alle esigenze del provider.

Vengono trasmesse così come sono nei campi `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` e `dest_addr_npi` di `SUBMIT_SM PDU`.

#### Tipo di servizio {#service-type}

Questo campo viene trasmesso così come si trova nel campo `service_type` della `SUBMIT_SM PDU`. Impostate questo valore in base alle esigenze del provider.

### Throughput e timeout {#throughput-timeouts}

Queste impostazioni controllano tutti gli aspetti temporali del canale SMPP. Alcuni fornitori richiedono un controllo molto preciso della frequenza dei messaggi, degli orari delle finestre e dei tentativi. Tali impostazioni devono essere impostate su valori che corrispondano alla capacità del fornitore e alle condizioni indicate nel contratto.

#### Finestra di invio {#sending-window}

La finestra è il numero di `SUBMIT_SM PDU`s che possono essere inviati senza aspettare un `SUBMIT_SM_RESP` corrispondente.

Esempio di trasmissione con una finestra massima di 4:

![](assets/sms_protocol_2.png)

La finestra consente di aumentare il throughput quando il collegamento di rete ha una latenza elevata.  Il valore della finestra deve essere almeno il numero di SMS/s moltiplicato per la latenza del collegamento
in secondi, in modo che il connettore non sia mai in attesa di un `SUBMIT_SM_RESP` prima di inviare il messaggio successivo.
Se la finestra è troppo grande, è possibile inviare altri messaggi duplicati in caso di problemi di connessione. Inoltre, la maggior parte dei fornitori hanno un limite molto stretto per la finestra e rifiutano i messaggi che oltrepassano il limite.

Come calcolare la formula ottimale della finestra di invio:

* Misurare la latenza massima tra `SUBMIT_SM` e `SUBMIT_SM_RESP`.

* Moltiplica questo valore in secondi fino al throughput MT massimo. Questo darà il valore ottimale della finestra di invio.

Esempio: Se hai 300 SMS/s impostato in velocità di trasmissione max MT e c&#39;è una latenza di 100 ms tra `SUBMIT_SM` e `SUBMIT_SM_RESP` in media, il valore ottimale sarebbe `300×0.1 = 30`.

#### Velocità max MT {#max-mt-throughput}

Numero massimo di MT al secondo e per connessione. Questa impostazione è rigorosamente applicata, l&#39;MTA non invierà mai i messaggi push più velocemente di questo limite. È utile per i fornitori che richiedono una limitazione precisa.

Per conoscere il limite di throughput totale, moltiplicate questo numero per il numero totale di connessioni come descritto nella formula precedente.

0 significa nessun limite, l&#39;MTA invierà MT il più velocemente possibile.

Si raccomanda in genere di mantenere questa impostazione al di sotto di 1000, poiché è impossibile garantire una velocità di trasmissione precisa al di sopra di questo numero, a meno che non venga adeguatamente valutata sull&#39;architettura finale e su richiesta specifica del fornitore SMPP. Potrebbe essere meglio aumentare il numero di connessioni per superare i 1000 MT/s.

#### Tempo prima della riconnessione {#time-reconnection}

Se la connessione TCP viene persa, il connettore attenderà questo numero di secondi prima di provare a creare una connessione.

#### Periodo di scadenza del MT {#expiration-period}

Timeout tra `SUBMIT_SM` e la `SUBMIT_SM_RESP` corrispondente. Se la `RESP` non viene ricevuta in tempo, il messaggio verrà considerato come non riuscito e verrà applicato il criterio globale dei tentativi dell&#39;MTA.

#### Timeout associazione {#bind-timeout}

Timeout tra il tentativo di connessione TCP e la risposta `BIND_*_RESP`. In caso di timeout, la connessione viene chiusa dal connettore Adobe Campaign  e prima di riprovare, si attende Tempo.

#### periodo di collegamento inquire_link {#enquire-link-period}

`enquire_link` è un tipo speciale di PDU inviato per mantenere la connessione in vita. Questo periodo è in secondi. Il connettore della campagna invia solo `enquire_link` quando la connessione è inattiva per conservare la larghezza di banda. Se non viene ricevuto alcun RESP dopo il doppio di questo periodo, la connessione verrà considerata morta e verrà attivato un processo di riconnessione.

### Specifiche di SMSC {#SMSC-specifics}

Queste impostazioni sono impostazioni avanzate che adattano il connettore Adobe Campaign  alla maggior parte delle peculiarità di implementazione SMPP.

**Definire una mappatura specifica delle codifiche**

Per informazioni dettagliate sulla codifica del testo, vedere la sezione [Codifica testo SMS](../../delivery/using/sms-protocol.md#sms-text-encoding).

Questa impostazione consente di definire una mappatura di codifica personalizzata, diversa dalla specifica. Sarà possibile dichiarare un elenco di codifiche, insieme al relativo valore `data_coding`.

L&#39;MTA tenterà di codificare utilizzando la prima codifica nell&#39;elenco. Se non riesce, proverà a utilizzare la codifica successiva nell&#39;elenco, ecc. Se non è possibile utilizzare alcuna codifica per codificare il messaggio, si verificherà un errore. Una volta trovata la codifica, l&#39;MTA creerà il `SUBMIT_SM PDU` con il testo codificato e il campo `data_coding` impostato con il valore specificato nella tabella.

L&#39;ordine degli elementi nella tabella è importante: le codifiche sono tentativi dall&#39;alto verso il basso. Si dovrebbe mettere la codifica più economica o quella più consigliata in cima all&#39;elenco, seguita da codifiche sempre più costose.

Tenere presente che UCS-2 non fallirà mai in quanto può codificare tutti i caratteri supportati in  Adobe Campaign e che la lunghezza massima di un SMS UCS-2 è molto inferiore: Solo 70 caratteri.

È inoltre possibile utilizzare questa impostazione per applicare a una codifica specifica un utilizzo sempre dichiarando solo 1 riga nella tabella di mappatura.

La mappatura predefinita utilizzata quando la casella di controllo non è selezionata equivale alla tabella seguente:

| data_coding | Codifica |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

Questo significa che l&#39;MTA cercherà di codificare il messaggio in GSM. Se riesce, lo invierà con `data_coding` impostato su 0.

Se il messaggio non può essere codificato in GSM, verrà codificato in UCS-2 e verrà impostato su 8 da `data_coding`.

#### Abilita message_payload {#enable-message-payload}

Se questa opzione è deselezionata, gli SMS lunghi verranno suddivisi dalla MTA e inviati in più `SUBMIT_SM PDU`s con UDH. Il messaggio sarà ricomposto dal cellulare dopo i dati UDH.

Se questa opzione è attivata, gli SMS lunghi verranno inviati in una delle PDU SUBMIT_SM, inserendo il testo nel campo facoltativo message_payload. Per ulteriori informazioni, vedere la [specifica SMPP](../../delivery/using/sms-protocol.md#ACS-SMPP-connector).

Se questa funzione è attivata,  Adobe Campaign non sarà in grado di contare le parti SMS singolarmente: tutti i messaggi saranno conteggiati come inviati in una parte.

#### Invia il numero di telefono completo {#send-full-phone-number}

Se questa casella di controllo non è selezionata, vengono inviate al provider solo le cifre del numero di telefono (`destination_addr` campo del campo `SUBMIT_SM`). Questo è il comportamento predefinito, in quanto l’indicatore internazionale del numero, in genere il prefisso +, viene sostituito dai campi TON e NPI in SMPP.

Quando la casella di controllo è selezionata, il numero di telefono viene inviato così come è, senza pre-elaborazione e spazi potenziali, + prefisso o cancelletto/hash/stelle segni.

Questa funzione ha anche un effetto sul comportamento della funzione di elenco Bloccati di risposta automatica: se la casella di controllo non è selezionata, ai numeri di telefono inseriti nella tabella di quarantena verrà aggiunto un prefisso + per compensare la rimozione del prefisso + dal numero di telefono da parte del protocollo SMPP stesso.

#### Ignora controllo certificato TLS {#skip-tls}

Quando TLS è abilitato, ignora tutti i controlli dei certificati.

Se questa opzione è selezionata, la connessione non è più sicura e non deve essere abilitata in produzione.

Può essere utile a scopo di debug o test.

#### Associazione TON/NPI {#bind-ton-npi}

TON (tipo di numero) e NPI (indicatore del piano di numerazione) descritti al punto 5.2.5 della [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pagina 117). Questi valori devono essere impostati in base alle esigenze del provider.

Vengono trasmesse così come sono nei campi `addr_ton` e `addr_npi` della PDU BIND.

#### Intervallo di indirizzi {#address-range}

Inviato come nel campo address_range della PDU BIND. Questo valore deve essere impostato a prescindere dalle esigenze del provider.

#### Numero di riconoscimenti ID non valido {#invalid-id}

Limita il numero di **ID messaggio non valido** `DELIVER_SM_RESP` che possono essere inviati per un singolo SR.

**Deve essere utilizzato solo per la risoluzione dei problemi come** soluzione alternativa e impostato su 0 in condizioni normali.

Esempio Fox, quando si imposta su 2:

* Il provider invia un SR (`DELIVER_SM`) con ID &quot;1234&quot;.

* Impossibile trovare l&#39;ID &quot;1234&quot; nel database.

* Il connettore conteggia 1 **ID** non valido per tale ID, quindi invia `DELIVER_SM_RESP` con il codice di errore &quot;ID messaggio non valido&quot; (comportamento normale).

* Il provider tenta lo stesso SR con ID &quot;1234&quot;.

* Impossibile trovare l&#39;ID &quot;1234&quot; nel database.

* Il connettore conteggia 2 **ID** non valido per tale ID, quindi invia `DELIVER_SM_RESP` &quot;OK&quot;, anche se non è stato elaborato correttamente.

* Questa funzione consente di cancellare i buffer SR dal lato del provider quando il blocco SR non valido è legittimo che i messaggi non possano essere elaborati.

Se si imposta questo campo su 0, viene disattivato il meccanismo in cui viene sempre restituito **ID messaggio non valido**, si tratta di un comportamento normale.

Impostando questo campo su 1, il connettore risponde sempre &quot;OK&quot; anche se l&#39;ID non è valido. Questo valore deve essere impostato su 1 solo sotto supervisione, per la risoluzione dei problemi e per il periodo minimo di tempo, ad esempio per recuperare da un problema sul lato del fornitore.

#### Area di estrazione dell&#39;ID nell&#39;SR {#regex-extraction}

Il formato SR non è applicato in modo rigoroso dalla specifica del protocollo SMPP. Si tratta solo di una raccomandazione descritta nell&#39; [Appendice B](../../delivery/using/sms-protocol.md#sr-error-management) (pagina 167) della specifica. Alcuni implementatori SMPP formattano questo campo in modo diverso, quindi  Adobe Campaign ha bisogno di un modo per estrarre il campo corretto.

Per impostazione predefinita, dopo `id:` vengono acquisiti fino a 10 caratteri alfanumerici.

Il regex deve avere esattamente un gruppo di cattura con una parte contenuta tra parentesi. Le parentesi devono racchiudere la parte ID. Il formato regex è PCRE.

Quando regolate questa impostazione, accertatevi di includere il maggior numero possibile di contesti per evitare falsi attivatori. Se nello standard sono presenti prefissi specifici, ad esempio `id:`, includerli nel regex. Usate anche i delimitatori di parole (\b) il più possibile per evitare di acquisire testo al centro di una parola.

Non includendo abbastanza contesto nel regex può introdurre un piccolo difetto di sicurezza: il contenuto effettivo del messaggio può essere incluso nella SR. Se confrontate solo un formato ID specifico senza contesto, ad esempio un UUID, potrebbe essere l’analisi del contenuto di testo effettivo, ad esempio un UUID incorporato nel campo di testo invece dell’ID.

#### Regex applicato per determinare lo stato di riuscita/errore {#regex-applied}

Quando si incontrano messaggi con una combinazione di campi di stato/errore sconosciuta, questi regex vengono applicati al campo di stato per determinare se l&#39;SR è stato un successo o un errore. L&#39;SR con valori di stato che non corrispondono a nessuno di questi regessi viene ignorato.

Per impostazione predefinita, i valori stat iniziano con `DELIV`, ad esempio `DELIVRD` nell&#39; [Appendice B](../../delivery/using/sms-protocol.md#sr-error-management), sarà considerato come consegnato con successo e tutti i valori di stato che corrispondono a errori, ad esempio `REJECTED`, `UNDELIV` sono considerati errori.

#### Formato ID nella conferma MT {#id-format-mt}

Indica il formato dell&#39;ID restituito nel campo `message_id` di `SUBMIT_SM_RESP PDU`.

* **Non modificare**: L’ID viene memorizzato così come è nel database, come testo con codifica ASCII. Non si verifica alcuna pre-elaborazione né filtraggio.

* **Numero** decimale: L’ID deve essere un numero decimale in formato ASCII. Gli spazi iniziali e finali e gli zero iniziali vengono rimossi quando questa impostazione viene utilizzata.

* **Numero** esadecimale: L’ID deve essere un numero esadecimale in formato ASCII, senza l’iniziale 0x o h finale. L&#39;ID viene quindi convertito in un numero decimale prima di essere memorizzato nel database.

* **Stringa** esadecimale: L’ID deve essere un testo con codifica ASCII che a sua volta è una stringa di byte codificati come esadecimali. Ad esempio, nella PDU si trova `0x34 0x31 0x34 0x32 0x34 0x33`, che si traduce in ASCII &quot;414243&quot;. Questa stringa viene quindi decodificata come una stringa esadecimale di byte ed è quindi possibile ottenere &quot;ABC&quot;: nel database verrà memorizzato l&#39;ID &quot;ABC&quot;.

#### Formato ID in SR {#id-format-sr}

Indica il formato dell&#39;ID acquisito dal regex `Extraction` dell&#39;ID nell&#39;SR. I valori hanno lo stesso significato e lo stesso comportamento del formato indicato in MT sopra.

**ID SR o codice di errore nel campo facoltativo**

>[!NOTE]
>
>Disponibile solo nel connettore Adobe Campaign Classic Extended SMPP.

Se questa opzione è attivata, il contenuto dei campi facoltativi verrà aggiunto al testo elaborato dai regex sopra. Il testo avrà il formato `0xTAG:VALUE`, `0xTAG` che corrisponde al valore esadecimale di 4 cifre del tag in lettere maiuscole, ad esempio `0x002E`.

Ad esempio, potresti voler acquisire l&#39;ID nel campo `receipted_message_id`. Per questo, abilita questa casella di controllo e il testo seguente verrà aggiunto allo stato:

```
0x001E:05e3299e-8d37-49d0-97c6-8e4fe60c7739
```

In questo esempio, 0x001E è il tag del campo facoltativo e UUID è il valore del campo.

Per acquisire questo valore, ora puoi impostare il seguente regex nel regex di estrazione dell’ID nel campo SR:

```
\b0x001E:([0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12})\b
```

>[!IMPORTANT]
>
>È possibile acquisire solo i campi facoltativi con valori di testo (ASCII/UTF-8). In particolare, i campi binari non possono essere acquisiti in modo affidabile con il sistema regex corrente.

**ID SR o codice di errore nel campo di testo**

Se selezionato, il campo **Testo** verrà mantenuto durante l&#39;elaborazione del testo dello stato dell&#39;SR.

Questo è utile se il provider inserisce dati importanti in questo campo come l&#39;ID o lo stato. In genere questo campo può essere eliminato in modo sicuro, poiché può contenere testo con una codifica non ASCII e interrompere l’elaborazione regolare.

Abilitando questa opzione è possibile che si verifichi un difetto di sicurezza molto piccolo se il regex `Extraction` dell&#39;ID nel campo SR non è sufficientemente specifico. Il contenuto del campo **Testo** può essere analizzato come ID e un utente malintenzionato può utilizzarlo per iniettare ID falsi, il che può portare a una situazione di rifiuto parziale del servizio.

**ID servizio**

Consente di aggiungere un TLV personalizzato. Questo campo imposta la porzione del tag. Il valore può essere personalizzato per consegna nel valore **Service o program ID** nei parametri avanzati della consegna.

Questa impostazione consente solo di aggiungere un’opzione TLV per messaggio.

### Risposta automatica inviata al MO {#automatic-reply}

>[!IMPORTANT]
>
>In Adobe Campaign Classic e in un&#39;architettura ibrida, l&#39;applicazione della risposta automatica per il connettore SMPP esteso richiede l&#39;accesso in scrittura per l&#39;operatore mid nella cartella **Account esterno**.

Questa funzione consente di rispondere rapidamente al testo su MO e di gestire per codice breve l&#39;invio al elenco Bloccati .

Le colonne **Parola chiave** e **Codice breve** definiscono le condizioni per attivare la risposta automatica. Se entrambi i campi corrispondono, l&#39;MO viene inviato e l&#39;azione aggiuntiva viene attivata. Per specificare un carattere jolly, lasciare vuoto il campo. La parola chiave corrisponde alla prima parola alfanumerica nel testo MO, ignorando la punteggiatura e gli spazi iniziali. Significa che il campo **Parola chiave** non può contenere spazi e deve essere una sola parola.

L&#39;impostazione **Parola chiave** è un prefisso. Ad esempio, se specificate &quot;AD&quot;, i valori corrispondenti saranno &quot;AD&quot;, &quot;ADAPT&quot; e &quot; ADOBE&quot;. Se si dispone di più parole chiave con un prefisso comune, è necessario prestare attenzione all&#39;ordine in quanto le parole chiave vengono elaborate dall&#39;alto verso il basso.

La colonna **Rispondi** è il testo da rispondere. In questo campo non è disponibile alcuna personalizzazione. Se lasciate vuoto questo campo, non verrà risposto alcun messaggio, ma verrà comunque attivata l&#39;azione aggiuntiva.

La colonna **Azioni aggiuntive** fornisce un&#39;azione aggiuntiva quando **Parola chiave** e **Codice breve** corrispondono, il codice breve vuoto corrisponde a tutti i codici brevi. È possibile inviare alla quarantena o rimuovere dalla quarantena, con valore none risponde al testo. Se si specifica un&#39;azione **aggiuntiva** ma si lascia vuoto il campo **Rispondi**, l&#39;azione verrà eseguita ma non verrà inviata alcuna risposta. La quarantena viene applicata solo per il codice breve specificato, oppure per tutti i codici brevi se il campo viene lasciato vuoto.

>[!IMPORTANT]
>
>L&#39;impostazione Invia numero di telefono completo ha un impatto sul comportamento del meccanismo di quarantena automatica delle risposte: se l&#39;opzione Invia numero di telefono completo non è selezionata, il numero di telefono messo in quarantena sarà preceduto dal segno più (&quot;+&quot;) per renderlo compatibile con il formato del numero di telefono internazionale.

Tutte le voci della tabella vengono elaborate nell&#39;ordine specificato, fino a quando una regola non corrisponde. Se più regole corrispondono a una regola MO, verrà applicata solo la regola superiore.

## Parametri modello di consegna SMS {#sms-delivery-template-parameters}

Alcuni parametri possono essere impostati per modello di consegna.

### Da campo {#from-field}

Questo campo è facoltativo. Consente di sovrascrivere l&#39;indirizzo del mittente (oADC). Il contenuto di questo campo viene inserito nel campo `source_addr` della `SUBMIT_SM PDU`.

Il campo è limitato a 21 caratteri dalla specifica SMPP, ma alcuni fornitori possono consentire valori più lunghi. È inoltre possibile applicare restrizioni molto rigorose in alcuni paesi, ad esempio lunghezza, contenuto e caratteri consentiti.

### Parametri di consegna {#delivery-parameters}

#### Numero massimo di SMS per messaggio {#maximum-sms}

Questa impostazione funziona solo se l&#39;impostazione **Messaggio payload** è disabilitata. Se il messaggio richiede più SMS di questo valore, verrà attivato un errore.

Il protocollo SMS limita gli SMS a 255 parti, ma alcuni telefoni cellulari hanno problemi a mettere insieme lunghi messaggi con più di 10 parti circa, il limite dipende dal modello esatto. Ti consigliamo di non superare 5 parti per messaggio.

A causa del funzionamento dei messaggi personalizzati in  Adobe Campaign, i messaggi possono avere dimensioni diverse. Avere una grande quantità di messaggi lunghi potrebbe aumentare i costi di invio.

#### Modalità di trasmissione {#transmission-mode}

Questo campo indica il tipo di SMS che si desidera trasferire: messaggi normali o flash, memorizzati sulla scheda mobile o SIM.

Questa impostazione viene trasmessa nel campo `dest_addr_subunit` facoltativo della `SUBMIT_SM PDU`.

* **Nessun campo** facoltativo nella PDU.

* **Imposta** il valore su 1. Invia un messaggio Flash che viene visualizzato sul dispositivo mobile e non viene memorizzato nella memoria.

* **In** genere il valore viene impostato su 0. Invia un messaggio normale.

* **Salva su** mobilesimposta il valore su 2. Indica al telefono di memorizzare l&#39;SMS nella memoria interna.

* **Salva su** terminali imposta il valore su 3. Indica al telefono di memorizzare l&#39;SMS nella scheda SIM.

#### Periodo di validità {#validity-period}

Il periodo di validità viene trasmesso nel campo `validity_period` della `SUBMIT_SM PDU`. La data è sempre formattata come formato di ora UTC assoluto, il campo data termina con &quot;00+&quot;.

## Connettore SMPP generico esteso {#acc-extended-connector}

![](assets/sms_protocol_4.png)

Le frecce rappresentano i flussi di dati.

Quando si inviano parti di consegna, l&#39;MTA genera elementi figlio MTA. Il numero di processi secondari MTA è dinamico e dipende da una configurazione in serverConf.xml. Ogni elemento secondario MTA crea un&#39;istanza del connettore `CSmppConnectorWorker` che si collega al provider SMPP. Le connessioni vengono mantenute in vita finché il figlio MTA viene mantenuto in vita, anch&#39;esso configurabile in serverConf.xml.

Il processo SMS elabora solo SR, si collega al provider e lascia la connessione aperta. Il processo si riconnette ogni 10 minuti per ricaricare le nuove impostazioni, operazione normale.

### Voci MT, SR e broadcast corrispondenti {#matching-mt}

Una tabella intermedia `nmsProviderMsgId` viene utilizzata per memorizzare temporaneamente i dati MT e SR prima di eseguirne il commit asincrono nel registro di trasmissione.

`nmsProviderMsgId` la tabella ha 3 gruppi di colonne:

* Colonne aggiornate quando un MT viene inviato e riconosciuto: `iBroadLogId`, `iDeliveryId`

* Colonne aggiornate al ricevimento di un SR: `iMsgId`, `iStatus`

* Colonne sempre aggiornate: `tsCreated`, `sProviderId`

Al termine dell&#39;elaborazione MT e SR, è necessario disporre di linee complete, con informazioni di trasmissione e stato.

Qui, `iMsgId` è collegato alla tabella `nmsBroadLogMsg`, indicando lo stato/il messaggio di errore completo.

Il processo SMS verifica la presenza di linee complete ogni minuto, quindi le elabora in modo asincrono:

* La riga completa viene letta.
* Il processo SMS calcola il nome della tabella del registro di trasmissione in base alla mappatura della consegna.
* Il processo SMS aggiorna la tabella del registro di trasmissione con l&#39;ID del messaggio e lo stato.

**Percorsi e connessioni parallele**

Ogni elemento secondario MTA crea una quantità configurabile di connessioni, pertanto limitare il numero di elementi secondari MTA limiterà il numero di connessioni. Poiché la correlazione tra i processi figlio MTA e il traffico è correlata, questo può essere in qualche modo controllato ma ancora un po&#39; imprevedibile.

## Prima di andare in diretta {#checklist}

Questa lista di controllo contiene un elenco di elementi da verificare prima di iniziare a vivere. Una configurazione incompleta può causare molti problemi.

### Verificare i conflitti di account esterni {#external-account-conflict}

Controlla di non avere vecchi account esterni SMS. Se l&#39;account di test viene disattivato, si corre il rischio che venga riattivato nel sistema di produzione e si generino potenziali conflitti.

Se avete più account sulla stessa istanza di Adobe Campaign  che si connettono allo stesso provider, contattate il provider per essere sicuri che distinguano effettivamente le connessioni tra questi account. La presenza di più account con lo stesso accesso richiede una configurazione aggiuntiva.

### Abilitare tracce SMPP dettagliate durante i controlli {#enable-verbose}

È sempre necessario abilitare le tracce SMPP dettagliate durante i controlli.
Anche se non è possibile controllare personalmente i file di registro, sarà più semplice per il supporto di aiutarvi.

### Test dell&#39;SMS {#test}

* **Invia SMS con tutti i tipi di**
caratteriSe devi inviare SMS con caratteri non GSM o non ASCII, prova a inviare alcuni messaggi con il maggior numero possibile di caratteri diversi. Se imposti una tabella di mappatura caratteri personalizzata, invia almeno un SMS per tutti i possibili 
`data_coding` values.

* **Verificare che SR siano**
elaborati correttamenteL&#39;SMS deve essere contrassegnato come ricevuto nel registro di consegna. Il registro di consegna deve avere esito positivo ed essere simile al seguente:

Verificate di aver modificato il nome del provider di consegna. Il registro di consegna non deve mai contenere    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Verificate di aver modificato il nome del provider di consegna. Il registro di distribuzione non deve mai contenere **SR Generic** negli ambienti di produzione.

* **Verificare che MO siano**
elaboratiSe è necessario elaborare MO (risposte automatiche, memorizzazione MO nel database, ecc.) prova a fare qualche test. Inviate qualche SMS per tutte le parole chiave di risposta automatica e controllate se la risposta è abbastanza veloce, non più di pochi secondi.
Archiviare il registro che  Adobe Campaign risponde con un esito positivo 
`DELIVER_SM_RESP` (command_status=0).

### Controllare le PDU {#check-pdus}

Anche se i messaggi hanno un aspetto positivo, è importante verificare che le PDU siano formattate correttamente.

Questo passaggio è necessario quando ci si connette a un provider che non era già connesso a  Adobe Campaign.

#### BIND {#bind}

Verificate che `BIND_* PDUs` venga inviato correttamente. La cosa più importante da verificare è che il provider restituisca sempre correttamente `BIND_*_RESP PDUs` (command_status = 0).

Verificare che non siano presenti troppi `BIND_* PDU`s. Se ce ne sono troppi, potrebbe indicare che la connessione è instabile. Per ulteriori informazioni, vedere la sezione [Problemi con connessioni instabili](../../delivery/using/sms-protocol.md#issues-unstable-connection).

#### INQUIRE_LINK {#enquire-link-pdus}

Verificare che `ENQUIRE_LINK PDU`s siano scambiati regolarmente quando la connessione è inattiva.

**SUBMIT_SM / DELIVER_SM**

Inviate un messaggio, quindi cercate nei registri le `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` e `DELIVER_SM_RESP PDU`s corrispondenti.

Con la `SUBMIT_SM PDU`:

* Verificare che `data_coding` sia corretto, 0 per impostazione predefinita.
* Verificare che `short_message` sia codificato correttamente. Provate a decodificarlo utilizzando un convertitore esadecimale che supporta più codifiche.

Con la `SUBMIT_SM_RESP PDU`:

* Verificare che sia stato eseguito correttamente, command_status = 0.
* Verificate che il relativo corpo contenga un ID formattato correttamente seguito da un byte &#39;0&#39;.

Con la `DELIVER_SM PDU`:

* Decodificare il campo esadecimale `short_message`.
* Verificare con uno strumento di controllo del regex che il regex definito in `Extraction` regex dell&#39;ID nell&#39;SR restituisca esattamente un gruppo di acquisizione e che acquisisca l&#39;intero ID nel messaggio.
* Verificare che l&#39;ID estratto corrisponda a quello in `SUBMIT_SM_RESP`.
* Verificare che il regex definito in `Extraction` regex dello stato nell&#39;SR restituisca il contenuto del campo stat.
* Verificate che il regex definito in `Extraction` regex dell&#39;errore nell&#39;SR restituisca il contenuto del campo err.

Con la `DELIVER_SM_RESP PDU`:

* Verificate che sia stato inviato rapidamente dopo la ricezione del `DELIVER_SM PDU`, in genere meno di 1 secondo.
* Verificare che sia stato eseguito correttamente, command_status = 0.

### Verificare con il provider {#provider}

Anche se il tuo SMS ha successo, contatta il provider per vedere se tutto è in ordine.

### Disattivazione di tracce SMPP dettagliate {#disable-verbose}

Una volta completati tutti i controlli, l&#39;ultima cosa è **Disabilita tracce SMPP dettagliate** per non generare troppi log. Potete riattivarli per la risoluzione dei problemi anche sui sistemi di produzione.
