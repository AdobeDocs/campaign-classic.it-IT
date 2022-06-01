---
product: campaign
title: Protocollo e impostazioni del connettore SMS
description: Ulteriori informazioni sul connettore SMS e su come configurarlo
feature: SMS
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
source-git-commit: 2c145829517a6961d502cc3e7b904547f8c71602
workflow-type: tm+mt
source-wordcount: '8460'
ht-degree: 0%

---

# Protocollo e impostazioni del connettore SMS {#sms-connector-protocol}

![](../../assets/common.svg)

>[!NOTE]
>
>In questo documento, tutti i riferimenti ai dettagli relativi al protocollo, ai nomi e ai valori dei campi fanno riferimento al [Specifiche di SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

## Panoramica {#overview}

L’SMS potrebbe essere limitato all’invio di messaggi di testo brevi senza formattazione, ma la sua semplicità lo rende un valido canale di comunicazione.

Esistono due modi principali per inviare un SMS:

* Mandalo manualmente da un telefono, il modo abituale per comunicare direttamente tra le persone.
* Invialo da Internet, il modo in cui Adobe Campaign invia i messaggi. Per questo, è necessario un provider di servizi SMS che connetta Internet alla rete mobile.
Adobe Campaign utilizza il protocollo SMPP per inviare SMS a un provider di servizi.

Questo documento illustra la connessione impostata tra Adobe Campaign e un provider SMPP.

I provider SMPP a volte possono derogare alle specifiche ufficiali, ma il connettore SMS in Adobe Campaign offre molte opzioni per adattare il proprio comportamento in modo che sia compatibile con la maggior parte dei provider.

>[!IMPORTANT]
>
>L&#39;impostazione di una connessione a un nuovo provider potrebbe richiedere alcune competenze tecniche, conoscenza di TCP, binario, rappresentazione esadecimale e codifiche di testo. Sarà inoltre necessaria una collaborazione attiva con il fornitore.

### Tipi di SMS {#sms-types}

Quando invii SMS di massa tramite un provider di SMS, incontrerai tre diversi tipi di SMS:

* **SMS MT (Mobile Terminated)**: un SMS inviato da Adobe Campaign ai telefoni cellulari tramite il provider SMPP.

* **SMS MO (origine mobile)**: un SMS inviato da un dispositivo mobile ad Adobe Campaign tramite il provider SMPP.

* **SMS SR (Status Report) o DR o DLR (Delivery Receipt)**: una ricevuta di ritorno inviata dal dispositivo mobile ad Adobe Campaign tramite il provider SMPP che indica che l’SMS è stato ricevuto correttamente. Adobe Campaign può anche ricevere SR che indica che il messaggio non può essere consegnato, spesso con una descrizione dell’errore.

È necessario distinguere tra riconoscimenti (PDU RESP, parte del protocollo SMPP) e SR: SR è una sorta di SMS che viene inviato attraverso la rete end-to-end, mentre un riconoscimento è solo una conferma del successo di un singolo trasferimento.

Sia le riconoscenze che l&#39;SR possono attivare gli errori, distinguendo tra i due aiuterà la risoluzione dei problemi.

### Informazioni trasportate da un SMS {#information-sms}

Un SMS trasporta più informazioni del testo. Ecco un elenco di ciò che ci si aspetta di trovare in un SMS:

* Il testo, che è limitato a 140 byte, ovvero tra 70 e 160 caratteri a seconda della codifica. Vedi [Codifica testo SMS](sms-protocol.md#sms-text-encoding) qui di seguito per dettagli e limitazioni.

* Un indirizzo destinatario, talvolta chiamato `ADC` o `MSISDN`. È il numero del cellulare che riceverà l&#39;SMS.

* Indirizzo mittente, che può essere chiamato `oADC` o a volte `sender id`. Può trattarsi di un numero di telefono utilizzato giorno per giorno, un codice breve inviato tramite un provider o un nome. Il nome è una funzione facoltativa, in tal caso non è possibile rispondere all’SMS.

* Flag che indica se il messaggio è un messaggio Flash. Un messaggio flash è un pop-up che non viene memorizzato in memoria.

* Flag che indica se un SR è previsto o meno.

* Una data di validità, dopo la quale non è consentito riprovare alcun dispositivo di rete.

* A `data_coding` , che indica la codifica del testo.

## Protocollo SMPP {#smpp-protocol}

Adobe Campaign Classic supporta la versione 3.4 del protocollo SMPP. Si tratta di un protocollo diffuso che consente l’invio di SMS a un provider (SMSC) e la ricezione di SMS e ricevute. Per ulteriori informazioni, consulta la sezione [Documentazione SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Le apparecchiature di rete sul lato del provider di servizi SMS sono spesso chiamate SMSC.

### Connessioni SMPP {#smpp-connections}

Adobe Campaign si connette all’apparecchiatura di rete del provider di servizi SMS tramite TCP. Il protocollo SMPP imposta le connessioni TCP permanenti da Adobe Campaign al provider. Le connessioni TCP sono sempre iniziate da Adobe Campaign, anche per ricevere messaggi.
SMPP apre 1 o 2 connessioni TCP, a seconda della sua modalità. Tutte le connessioni sono sempre avviate da Adobe Campaign.

Il protocollo SMPP può funzionare in due modalità:

* **Trasmettitore+ricevitore (o TX+RX)**: per la trasmissione e la ricezione dei messaggi vengono utilizzate due connessioni TCP separate.
* **Transceiver (o TRX)**: viene utilizzata una singola connessione TCP per la trasmissione e la ricezione dei messaggi.

>[!NOTE]
>
> Adobe Campaign Classic supporta solo la modalità TX+RX. Questa limitazione è dovuta alla sua architettura tecnica.

### PDU SMPP {#smpp-pdu}

Le unità di trasmissione SMPP (&quot;pacchetti&quot;) sono denominate PDU. A **PDU** contiene un comando, uno stato, un numero di sequenza e dati.

Ogni PDU deve essere riconosciuta da un `SMPP RESP PDU` (risposta sincrona). Le richieste possono essere inoltrate: il mittente può inviare molti comandi senza attendere `RESP`, il numero di richieste che possono essere eseguite in qualsiasi momento è denominato finestra . `RESP PDU` possono arrivare in qualsiasi ordine, non collegato all&#39;ordine della rispettiva PDU iniziatrice.

Nei separati **Trasmettitore+ricevitore** la connessione utilizzata dipende dal tipo di messaggio trasmesso. Il collegamento del trasmettitore viene utilizzato per MT e il collegamento del ricevitore viene utilizzato per MO e SR. Le richieste e le risposte per ogni tipo di messaggio vengono inviate tramite la stessa connessione TCP.

Ad esempio, quando si invia un MT, viene utilizzata la connessione del trasmettitore e il `RESP` che riconosce che il MT viene inviato anche attraverso il canale del trasmettitore. Quando si riceve un MO (o un SR), la connessione del ricevitore viene utilizzata per ricevere il MO e inviare il `RESP` che riconosce il MO.

![](assets/do-not-localize/sms_protocol_1.png)

In Adobe Campaign Classic, per collegare SR con i corrispondenti MT, viene restituito un ID da SMSC con il `SUBMIT_SM_RESP` e `DELIVER_SM` passaggi. L&#39;identificatore è memorizzato in `providerId` campo `nms::providerMsgId` e è collegato a `broadLogId` e `deliveryId`. Questa operazione di corrispondenza viene eseguita dal processo SMS durante la scrittura nel database.

Un successo `SUBMIT_SM_RESP PDU` attiva lo stato del messaggio &quot;inviato&quot; nel registro di invio mentre un esito positivo `DELIVER_SM (SR) PDU` attiva lo stato del messaggio &quot;ricevuto&quot;.

### Aspetti di sicurezza {#security-aspects}

Il protocollo stesso non è crittografato. La maggior parte dei provider implementa una variante di IP inserire nell&#39;elenco Consentiti, quindi gli indirizzi IP del server Adobe Campaign devono essere dichiarati al provider.

Adobe Campaign supporta il passaggio di un accesso e una password durante la fase di binding. Inoltre supporta SMPP rispetto a TLS. Va notato che i certificati sono necessari per garantire la sicurezza necessaria. Anche se il connettore SMPP consente di bypassare i controlli sui certificati, dovrebbe essere utilizzato solo per i test, perché TLS senza certificati fornisce un livello di sicurezza significativamente inferiore.

Il connettore utilizza i certificati predefiniti forniti dal sistema `openssl` libreria. Di solito è fornito dal `/etc/ssl/certs` directory su Debian. Questa directory è fornita dal pacchetto &quot;ca-certificates&quot; per impostazione predefinita, ma può essere personalizzata.

### Informazioni in ciascun tipo di PDU {#information-pdu}

Ogni tipo di PDU ha campi distinti che contengono diverse informazioni. Queste PDU sono descritte in dettaglio nella sezione [Specifiche di SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).

Ogni sezione seguente descrive sia la PDU che la relativa risposta sincrona (`*_RESP PDU`). Tutte le PDU devono essere riconosciute con un `RESP`, questa è una parte obbligatoria della specifica.

Le PDU possono disporre di campi facoltativi. Qui sono descritti solo i campi più comuni. Fai riferimento a [Specifiche di SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) per ulteriori informazioni.

**BIND_TRANSMITTER / BIND_RECEIVER / BIND_TRANSCEIVER**

Questa PDU viene utilizzata per avviare una connessione a SMSC. **Trasmettitore**, **Ricevitore** e **Ricetrasmettitore** le modalità cambiano solo il tipo di SMS consentito per essere trasferito su questa connessione, in particolare:

| Modalità | Tipi di SMS consentiti |
|:-:|:-:|
| Trasmettitore | MT |
| Ricevitore | MO + SR |
| Ricetrasmettitore | MT + MO + SR |

Campi di rilievo in un `BIND_* PDU`:

* **system_id**: Accesso utilizzato per l’autenticazione. Impostato nell’account esterno.

* **password**: Password utilizzata per l&#39;autenticazione. Impostato nell’account esterno.

* **system_type**: È necessario impostare un valore specifico per alcuni provider. Impostato nell’account esterno, disponibile in tutte le versioni. Spesso distingue tra diversi tipi di contratti, canali, paesi, ecc.

* **addr_ton** e **addr_npi**: Richiesto da alcuni provider. Impostato da `Bind TON` e `Bind NPI` nell’account esterno.

* **indirizzo_intervallo**: Richiesto da alcuni provider. Nella maggior parte dei casi, questo è un elenco di codici di scelta rapida consentiti in questa connessione. Impostato nell’account esterno.

`BIND_*_RESP` non dispone di un campo specifico e conferma se la connessione è riuscita o meno.

#### SBARCO {#unbind}

Questa PDU deve essere inviata dal sistema prima della disconnessione. Deve attendere la corrispondenza `UNBIND_RESP` PDU prima di chiudere la connessione.

La conformità a SMSC non deve chiudere la connessione. La connessione TCP è controllata dal connettore Adobe Campaign.

#### SUBMIT_SM {#submit-sm}

Questa PDU invia un MT al SMSC. La sua PDU di risposta dà l&#39;ID del MT.

Campi di rilievo in un `SUBMIT_SM` PDU:

* **service_type**: richiesto da alcuni provider. Imposta nelle proprietà di consegna.

* **source_addr_ton** e **source_addr_npi**: indica il tipo di indirizzo di origine trasmesso. Il significato di questi campi è standardizzato, ma poiché alcuni provider lo utilizzano in modo diverso, è necessario chiedere al provider il valore corretto. Impostato nell’account esterno.

* **source_addr**: l&#39;indirizzo di origine / oADC del MT. Sarà visualizzato sul cellulare. Impostato nell’account esterno e nella consegna, il valore nella consegna ha la precedenza sul valore dell’account esterno.

* **dest_addr_ton** e **dest_addr_npi**: indica il tipo di indirizzo di destinazione trasmesso (ad esempio, formato locale o internazionale). Il significato di questi campi è standardizzato, ma poiché alcuni provider lo utilizzano in modo diverso, è necessario chiedere al provider il valore corretto. Impostato nell’account esterno.

* **destination_addr**: indirizzo del destinatario, numero di telefono o MSISDN.

* **esm_class**: utilizzato per indicare se l’UDH è utilizzato o meno nel campo di testo. Abilitato automaticamente dal connettore per SMS suddivisi se il valore `message_payload` modalità non utilizzata.

* **priority_flag**: priorità del messaggio rispetto agli altri. Ciò è legato alla priorità della consegna stessa.

* **valid_period**: marca temporale dopo la quale non è necessario riprovare. Impostato nella consegna stessa.

* **registrato_delivery**: indica se una SR è richiesta o meno. Adobe Campaign imposta sempre questo flag ad eccezione delle risposte automatiche. Per i messaggi multiparte, il flag viene impostato solo per la prima parte. Tutte le versioni hanno lo stesso comportamento.

* **data_coding**: indica la codifica utilizzata nel campo di testo. Consulta la sezione [Codifica testo SMS](sms-protocol.md#sms-text-encoding) per ulteriori informazioni.

* **short_message**: il testo del messaggio. Se viene utilizzato UDH, contiene anche l’intestazione UHD.

Adobe Campaign supporta questi campi facoltativi:

* **dest_addr_subunit**: utilizzato per specificare il target dell’SMS: scheda flash, mobile o SIM. Imposta nelle proprietà di consegna.

* **message_payload**: se attivato nell’account esterno, i messaggi lunghi saranno inviati in un’unica PDU e il testo sarà trasmesso in questo campo anziché nella `short_message` campo .

#### SUBMIT_SM_RESP {#submit-sm-resp}

Questa PDU conterrà l&#39;ID del MT. Questo è utile per abbinarlo all&#39;SR in ingresso.

>[!IMPORTANT]
>
>Molti provider trasmettono l&#39;ID MT in esadecimale. Assicurati di impostare la **Formato ID nella convalida MT** impostazione corretta nell’account esterno.

Alcuni provider inviano `SUBMIT_SM_RESP` dopo l&#39;invio dell&#39;SR. Per tenere conto di tale comportamento, Adobe Campaign attende 30 secondi prima di rispondere **ID messaggio non valido** a un SR con un ID sconosciuto.

#### DELIVER_SM {#delivery-sm}

Questa PDU viene inviata da SMSC ad Adobe Campaign. Contiene un MO o un SR.

La maggior parte dei campi hanno lo stesso significato dei loro `SUBMIT_SM` controparte. Elenco di campi utili:

* **source_addr**: indirizzo di origine del MO/SR. Di solito questo è un numero di telefono.

* **destination_addr**: codice breve che ha ricevuto il MO o l&#39;SR.

* **esm_class**: utilizzato per indicare se la PDU è un MO o un SR.

* **short_message**: testo del messaggio. Per SR, questo contiene i dati descritti nell&#39;appendice B della specifica del protocollo SMPP. Vedi [Gestione degli errori SR](sms-protocol.md#sr-error-management) per ulteriori dettagli.

Adobe Campaign è in grado di leggere l&#39;ID del messaggio nel `receipted_message_id` campo facoltativo con alcune configurazioni.

#### DELIVER_SM_RESP {#deliver-sm-resp}

Questa PDU viene inviata da Adobe Campaign per confermare SR e MO.

Adobe Campaign Classic riconosce SR e MO una volta inseriti nel database. Alcuni errori di elaborazione possono verificarsi anche in caso di esito positivo `DELIVER_SM_RESP` La PDU è stata inviata. Questa limitazione è causata dall&#39;architettura software di Adobe Campaign Classic.

#### INQUIRE_LINK {#enquire-links}

Questa PDU viene utilizzata solo per verificare che la connessione sia attiva. La sua frequenza deve essere stabilita in base alle esigenze del fornitore.

I 60 secondi predefiniti devono corrispondere alla maggior parte delle configurazioni impostate nell’account esterno.

#### INQUIRE_LINK_RESP {#enquire-links-resp}

Questa PDU riconosce che la connessione è attiva.

### SMS multiparte (SMS lungo) {#multipart}

>[!IMPORTANT]
>
> Adobe Campaign supporta solo SMS multiparte o SMS lunghi per l’invio. UDH e `message_payload` non sono supportati per gli SMS in entrata (MO), il che significa che l’opzione MO è limitata a 160 caratteri.

Gli SMS multiparte, o SMS lunghi, sono SMS inviati in più parti. A causa di limitazioni tecniche nel protocollo di rete mobile, un SMS non può essere più grande di 140 byte o dovrà essere diviso. Consulta la sezione [Codifica testo SMS](sms-protocol.md#sms-text-encoding) per ulteriori informazioni sul numero di caratteri che possono essere inclusi in un SMS.

Ogni parte di un messaggio lungo è un singolo SMS. Queste parti viaggiano in modo indipendente sulla rete e sono assemblate dal telefono cellulare ricevente. Per gestire i nuovi tentativi e i problemi di connettività, Adobe Campaign invia queste parti in ordine inverso e richiede un SR solo nella prima parte del messaggio, l’ultima inviata. Poiché il telefono cellulare visualizza un messaggio solo quando viene ricevuta la sua prima parte, i nuovi tentativi su parti aggiuntive non produrranno duplicati sul telefono cellulare.

Il numero massimo di SMS per messaggio può essere impostato per consegna utilizzando il **Numero massimo di SMS per messaggio** nella **Modello di consegna**. I messaggi che superano questo limite avranno esito negativo durante l’invio con un motivo di errore SMS troppo lungo.

Ci sono 2 modi per inviare SMS lunghi:

* **UDH**: il modo predefinito e consigliato per inviare messaggi lunghi. In questa modalità, il connettore divide il messaggio in più `SUBMIT_SM PDU`è con informazioni UDH in loro. Questo protocollo è quello utilizzato dagli stessi telefoni cellulari. Questo significa che Adobe Campaign ha il maggior controllo sulla generazione dei messaggi, consentendogli di calcolare esattamente quante parti sono state inviate e come sono state suddivise.

* **message_payload**: il modo in cui inviare l&#39;intero messaggio lungo in un unico `SUBMIT_SM PDU`. Il provider dovrà dividerlo, il che significa che è impossibile per Adobe Campaign sapere esattamente quante parti sono state inviate. Alcuni fornitori richiedono questa modalità, ma consigliamo di utilizzarla solo se non supportano UDH.

Vedi la descrizione del `esm_class`, `short_message` e `message_payload` campi [PDU SUBMIT_SM](sms-protocol.md#information-pdu) per ulteriori dettagli sul protocollo e i formati.

### Limitazione del carico e finestre {#throughput-capping}

La maggior parte dei provider richiede un limite di throughput per ogni connessione SMPP. Questo può essere ottenuto impostando un numero di SMS nell’account esterno. Tieni presente che la limitazione della velocità effettiva avviene per connessione, il throughput effettivo totale corrisponde al limite per connessione moltiplicato per il numero totale di connessioni. Questo è descritto in [Connessioni simultanee](sms-protocol.md#connection-settings) sezione .

Per raggiungere il massimo throughput possibile, è necessario ottimizzare la finestra di invio massima. La finestra di invio è il numero di `SUBMIT_SM PDU`che può essere inviato senza attendere un `SUBMIT_SM_RESP`. Consulta la sezione [Impostazione della finestra di invio](sms-protocol.md#throughput-timeouts) per ulteriori dettagli.

### SR e gestione degli errori (&quot;Appendice B&quot;) {#sr-error-management}

Il protocollo SMPP definisce gli errori sincroni standard in `RESP PDU`s, ma non definisce i codici di errore per SR. Ogni provider utilizza i propri codici di errore con il proprio significato.

Una raccomandazione è formulata nella sezione dell&#39;appendice B del [Specifiche del protocollo SMPP](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pag. 167), ma questo non elenca i codici di errore effettivi né il loro significato.

Per adattarsi alla gestione degli errori, il sistema dei messaggi di broadlog di Adobe Campaign è stato sfruttato per fornire correttamente gli errori e la loro gravità (rigido, morbido, ecc.).

Come accennato in precedenza, esistono due tipi diversi di errori:

* risposte sincrone nel `SUBMIT_SM_RESP` che si verifica immediatamente dopo l’invio del messaggio a SMSC
* le ricevute che possono essere ricevute molto più tardi quando il dispositivo mobile ha ricevuto il messaggio o quando il messaggio è scaduto. In tal caso l&#39;errore si trova in un SR.

Quando viene ricevuta una SR, lo stato e l&#39;errore si trovano nella `short_message` campo (esempio per le implementazioni conformi all&#39;appendice B). La `short_message` Il campo della PDU è spesso denominato **campo di testo** poiché contiene testo in MT. In caso di SR, contiene informazioni tecniche più un sottocampo denominato **Testo**. Questi 2 campi sono diversi e `short_message` contiene effettivamente **Testo** e altre informazioni.

I connettori Adobe Campaign Classic (eccetto Extended SMPP) utilizzano un comportamento codificato che dipende dal provider selezionato. SMPP generico distingue solo tra successo ed errore, senza dettagli. Il registro di consegna può contenere alcune informazioni non garantite.

#### Formato del campo di testo SR {#sr-text-field-format}

La specifica consiglia di utilizzare questo formato per il campo di testo SR. Si tratta di un elenco di campi secondari, separati da uno spazio con due punti per separare il nome del campo e il relativo valore. I nomi dei campi non fanno distinzione tra maiuscole e minuscole.

Esempio di un campo di testo SR corrispondente alla raccomandazione dell&#39;appendice B:

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Il campo id è l&#39;ID ricevuto nel `SUBMIT_SM_RESP PDU`, il riconoscimento del MT.

`sub` e `dlvrd` devono contare la quantità di parti consegnate e di messaggi consegnati, ma questo non viene utilizzato da Adobe Campaign in quanto il sistema di log di trasmissione fornisce informazioni migliori e più integrate.

`submit date` e `done date` I campi sono marche temporali indicative di quando l’unità MT è stata inviata e quando l’unità SR è stata inviata dal dispositivo mobile. Ci si aspettano alcuni problemi con i fusi orari o anche marche temporali errate date da dispositivi mobili con data impostata non corretta.

Il campo stat è importante in quanto indica lo stato del messaggio. L&#39;unico status importante è `DELIVRD`, `UNDELIV` e `REJECTD`. La `DELIVRD` lo stato indica un successo, gli altri due indicano un errore. Altri valori sono possibili, ma sono solitamente notifiche intermedie, ad esempio il MT ha raggiunto il gestore di telefonia mobile, ma non il telefono cellulare. Queste notifiche intermedie vengono ignorate da Adobe Campaign.

Il campo error contiene il codice di errore specifico del provider. Il provider deve fornire una tabella dei possibili codici di errore insieme al loro significato per essere in grado di interpretare questo valore.

Infine, il campo di testo in genere contiene l&#39;inizio del testo del MT. Questo viene ignorato da Adobe Campaign e alcuni provider non lo trasmettono per evitare perdite di PII e il consumo di larghezza di banda della rete. Può essere utilizzato durante la risoluzione dei problemi per individuare più facilmente l&#39;SR che corrisponde a un MT di test leggendo questo campo.

### Esempio di elaborazione SR in Adobe Campaign Classic Extended generico SMPP {#sr-processing}

In questo esempio viene visualizzato il caso di un’implementazione successiva alla raccomandazione Appendice B, i valori predefiniti nell’account esterno e un SMS MT riuscito.

```
id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Primo, la `id extraction` regex viene applicato per estrarre l&#39;ID e riconciliarlo con il MT corrispondente.

Quindi, il `status extraction` regex e `error code extraction` regex viene applicato per estrarre questi campi e viene aggiunto alla stringa.

Il messaggio del registro di trasmissione viene costruito con queste informazioni e la stringa originale non modificata viene aggiunta come riferimento:

```
SR ExampleProvider DELIVRD 000|MESSAGE=id:1234567890 sub:001 dlvrd:001 submit date:1608011415 done date:1608011417 stat:DELIVRD err:000 Text:Hello Adobe world
```

Il messaggio viene quindi normalizzato, rimuovendo la parte MESSAGE per essere in grado di abbinare più messaggi con gli stessi codici stat e error.

```
SR ExampleProvider DELIVRD 000|#MESSAGE#
```

Se non è già stato eseguito il provisioning del messaggio nella tabella dei messaggi del registro di trasmissione, verrà creata una nuova voce utilizzando l’intero messaggio come **firstText** e il messaggio normalizzato. Quindi, il connettore utilizza il successo e `error` regex per determinare se si è trattato di un successo o di un errore:

* Se corrisponde al `success` regex, sarà considerato un successo.

* Se corrisponde al `error` regex, il messaggio è qualificato come errore.

* Se nessuno di questi due regex corrisponde, l&#39;SR viene ignorato. Potrebbe trattarsi di una notifica intermedia, che non viene gestita da Adobe Campaign.

Per impostazione predefinita, tutti gli errori vengono forniti come errori soft. Ciò significa che gli errori rigidi devono essere forniti a mano.

### Codifica testo SMS {#sms-text-encoding}

Dovrebbe **contatta sempre il provider SMSC in caso di problemi di codifica**. Solo i provider SMSC sono a conoscenza della codifica che supportano e delle regole speciali che possono essere applicate a causa di limitazioni nella loro piattaforma tecnica.

I messaggi SMS utilizzano una speciale codifica a 7 bit, spesso denominata codifica GSM7.

Nel protocollo SMPP, il testo GSM7 verrà espanso a 8 bit per carattere per facilitare la risoluzione dei problemi. SMSC lo impacchetterà in 7 bit per carattere prima di essere inviato al dispositivo mobile. Ciò significa che `short_message` Il campo dell’SMS può essere lungo fino a 160 byte nel frame SMPP, mentre è limitato a 140 byte quando viene inviato sulla rete mobile.

In caso di problemi di codifica, ecco alcuni aspetti importanti da verificare:

* Assicurati di sapere quali caratteri appartengono a quale codifica. GSM7 non supporta completamente i segni diacritici o gli accenti. Specialmente in francese, dove é ed è fanno parte del GSM7, ma ê, o ï no. Lo stesso vale per lo spagnolo.

* Il C con cedilla (ç) è presente solo in maiuscolo nell&#39;alfabeto GSM7, ma alcuni telefoni lo rendono in minuscolo o in caso &quot;intelligente&quot;. La raccomandazione generale è di evitarlo completamente e rimuovere il cedilla o passare a UCS-2.

* **Non utilizzare ASCII in SMS** a meno che non sia esplicitamente richiesto dal provider SMSC. Questa codifica spreca spazio perché ha caratteri a 8 bit e una copertura inferiore rispetto a GSM7. Questa codifica può essere necessaria per le reti CDMA utilizzate in Nord America.

* Latin-1 non è sempre supportato. Verificare la compatibilità con il provider SMSC prima di tentare di utilizzare Latin-1.

* Le tabelle di spostamento della lingua nazionale non sono supportate dal connettore Adobe Campaign. È necessario utilizzare UCS-2 o altro `data_coding` invece.

* UCS-2 e UTF-16 sono spesso mescolati da telefoni. Questo è un problema quando si utilizzano emoji e altri caratteri non presenti in UCS-2.

* La maggior parte dei telefoni non ha glifi di font per tutti i caratteri UCS-2. Gli smartphone tendono ad essere in grado di visualizzare caratteri rari piuttosto facilmente, ma i telefoni a funzionalità generalmente hanno un supporto limitato a ciò che è utile nella lingua madre del paese in cui sono stati acquistati. Se si desidera utilizzare emoji o ASCII-art, testarlo su un&#39;ampia varietà di telefoni prima di inviare. L’anteprima di Adobe Campaign non simula i glifi mancanti e visualizzerà i simboli disponibili nel browser web.

La `data_coding` indica la codifica utilizzata. Un problema importante è che il valore 0 indica la codifica SMSC predefinita nella specifica, che in genere si riferisce a GSM7. Controlla con il partner SMSC a quale codifica è associata `data_coding` = 0 che supporta solo Adobe Campaign. Altro `data_coding` i valori tendono a seguire le specifiche, ma l&#39;unico modo per essere sicuri è quello di controllare con il provider SMSC.

La dimensione massima di un messaggio dipende dalla relativa codifica. Questa tabella riassume tutte le informazioni pertinenti:

| Codifica | Codifica_dati normale | Dimensioni del messaggio (caratteri) | Dimensione della parte per SMS multiparte | Caratteri disponibili |
|:-:|:-:|:-:|:-:|:-:|
| GSM7 | 0 | 160 | 152 | Set di caratteri di base GSM7 + estensione (i caratteri estesi richiedono 2 caratteri) |
| Latino-1 | 3 | 140 | 134 | ISO-8859-1 |
| UCS-2 <br>UTF-16 | 8 | 70 | 67 | Unicode (varia da telefono a telefono) |

## Parametri dell’account esterno SMPP {#SMPP-parameters-external}

Ogni implementazione del protocollo SMPP ha molte varianti. Per migliorare la compatibilità e l&#39;adattabilità, sono disponibili molte impostazioni per modificare il comportamento del connettore SMPP. Questa sezione descrive ogni parametro e i relativi effetti sul connettore.

### Parametri generali e ciclo di produzione {#general-parameters-routing}

**Limita le istanze MTA per questo account**

È possibile impostare un limite al numero di istanze MTA consentite per la connessione al provider SMPP. Se questa opzione è selezionata, è possibile specificare il numero massimo di MTA utilizzabili.

Questa opzione consente un controllo più preciso del numero di connessioni, vedi [Connessioni simultanee](sms-protocol.md#connection-settings).

Se imposti un valore maggiore del numero di MTA in esecuzione, tutti gli MTA verranno eseguiti normalmente: questa opzione è solo un limite e non può generare ulteriori MTA.

Se è necessario controllare con precisione il numero di connessioni, ad esempio il requisito del provider, si consiglia di impostare sempre questa opzione anche se la distribuzione corrente ha il numero corretto di MTA in esecuzione. Se successivamente verranno aggiunti ulteriori MTA, il limite di connessione sarà comunque rispettato.

### Impostazioni di connessione {#connection-settings}

#### Nome implementazione SMSC {#smsc-implementation-name}

Imposta il nome dell’implementazione SMSC. Deve essere impostato sul nome del provider. Contatta l’amministratore o il team di recapito per sapere cosa aggiungere in questo campo. Il ruolo di questo campo è descritto in [Gestione degli errori SR](sms-protocol.md#sr-error-management) sezione .

#### Server {#server}

Nome DNS o indirizzo IP del server a cui connettersi.

#### Porta {#port}

Porta TCP a cui connettersi.

#### Account {#account}

Accesso della connessione. Trasmesso in `system_id` campo della PDU BIND.

#### Password {#password}

Password della connessione SMPP. Passato nel campo password della PDU BIND.

#### Tipo di sistema {#system-type}

Valore passato nel `system_id` campo della PDU BIND. Alcuni provider hanno bisogno di un valore specifico qui.

#### Numero di connessioni figlio MTA {#number-mta-child}

In Adobe Campaign Classic, definisce il numero di connessioni per figlio MTA.

Il connettore SMPP esteso Adobe Campaign Classic può controllare il numero di connessioni per figlio MTA. Per controllare il limite globale di connessioni, dovrai limitare il numero di processi figlio MTA, il che spesso significa avere una piattaforma di mid-sourcing dedicata per SMS.

Per Adobe Campaign Classic, può esserci un numero diverso di connessioni al ricevitore e al trasmettitore:

* **Connessioni del trasmettitore = Numero di connessioni figlio MTA * numero di processi figlio MTA * numero di MTA </br> (se è impostata la risposta automatica) + Numero di connessioni figlio MTA**

Come suggerito in precedenza, il processo SMS di Adobe Campaign Classic apre più connessioni al trasmettitore se la risposta automatica è abilitata. Queste connessioni aggiuntive vengono utilizzate per inviare le risposte automatiche.

* **Connessioni ricevitore = Numero di connessioni figlio MTA**

Se si impostano le risposte automatiche, il processo SMS aprirà coppie trasmettitore/ricevitore, aumentando il numero di connessioni del trasmettitore. Se non hai impostato alcuna risposta automatica, aprirà solo le connessioni del ricevitore.

#### Abilitare TLS su SMPP {#enable-TLS}

Utilizza TLS per connetterti al provider. La connessione verrà crittografata. La connessione TLS è gestita dalla libreria OpenSSL : tutto ciò che è applicabile a OpenSSL è vero per questa connessione.

#### Abilita tracce SMPP dettagliate nel file di registro {#enable-verbose-log-file}

Questa impostazione esegue il dump di tutto il traffico SMPP nei file di registro. Spesso è necessario regolare i parametri durante la configurazione iniziale. Questa opzione deve essere abilitata per la risoluzione dei problemi relativi al connettore e confrontata con il traffico rilevato dal provider.

In Adobe Campaign Classic, l’output di registro si trova nel registro MTA per il traffico correlato all’MT e nel registro SMS per il traffico correlato all’MO e all’SR.

### Impostazione di connessione del ricevitore {#receiver-connection}

Questa sezione è visibile solo in separata **trasmettitore+ricevitore** modalità.

#### Utilizzare parametri diversi per il ricevitore {#receiver-parameters}

Quando la casella è deselezionata, le stesse impostazioni vengono utilizzate per il trasmettitore e il ricevitore.

Quando la casella è selezionata, le impostazioni nella **Impostazioni di connessione** la sezione si applica al trasmettitore e alle impostazioni nella **Connessione ricevitore** le impostazioni verranno applicate al ricevitore.

**Server ricevitore, porta, account, password, tipo di sistema**

Queste impostazioni si applicano al ricevitore in modalità trasmettitore+ricevitore. Funzionano come la parte del trasmettitore, vedi sopra per maggiori dettagli.

### Impostazioni dei canali SMPP {#smpp-channel-settings}

#### Consenti traslitterazione caratteri {#allow-character-transliteration}

La traslitterazione è il processo di ricerca di caratteri equivalenti a quelli mancanti. Ad esempio, il carattere francese &quot;ê&quot; (con accento circonflesso) non è presente nella codifica GSM, ma può essere sostituito da &quot;e&quot; senza compromettere la leggibilità.

Se questa casella è deselezionata, la codifica del testo avrà esito negativo se non è in grado di codificare la stringa esattamente come è.

Quando questa casella è selezionata, la codifica del testo tenterà di convertire la stringa in una versione approssimativa, anziché generare un errore. Se alcuni caratteri non hanno un equivalente nella codifica di destinazione, la codifica del testo non riuscirà.

Consulta la sezione [Definire una mappatura specifica delle impostazioni di codifica](sms-protocol.md#SMSC-specifics) per una spiegazione più generale del processo di codifica.

#### Archiviare MO in ingresso nel database {#incoming-mo-storing}

Quando abilitato, l’MO in entrata viene memorizzato nella tabella inSMS del database. Puoi eseguire una query su questa tabella utilizzando l’attività query di qualsiasi flusso di lavoro.

Adobe Campaign Classic memorizza sempre tutti i MOs nel database inSMS, quindi questa opzione non è disponibile.

#### Abilitare gli aggiornamenti dei KPI in tempo reale durante l&#39;elaborazione SR {#real-time-kpi}

Quando è abilitata, i KPI vengono aggiornati in tempo reale nella pagina di consegna principale al momento della ricezione dell’SR dell’errore.

L&#39;inconveniente può essere a basse prestazioni a causa del contenzioso del database generato. Se disabilitata, le statistiche vengono aggiornate dal **syncfromexec** flusso di lavoro, in esecuzione ogni 20 minuti.

Adobe Campaign Classic dispone di un meccanismo completamente diverso per i KPI, pertanto questa opzione non è disponibile.

#### Numero di origine {#source-number}

Definisce l&#39;indirizzo di origine predefinito per i messaggi. Questa impostazione si applica solo se il numero di origine è stato lasciato vuoto nella consegna.

Per impostazione predefinita, il campo del numero di origine non viene passato, pertanto il provider lo sostituirà al codice breve.

Questo abilita la funzione di sostituzione dell’indirizzo del mittente/oADC.

#### Codice breve {#short-code}

Indica il codice breve principale dell&#39;account. Se per questo account vengono utilizzati più codici brevi o se il codice breve è sconosciuto, lasciare vuoto questo campo.

È utile specificare un codice breve per due funzioni:

* L&#39;anteprima mostrerà il codice breve se non viene fornito alcun numero di origine. Rifletterà il comportamento reale sul cellulare.

* L&#39;impostazione di elenco Bloccati della funzione di risposta automatica invia solo all&#39;utente la quarantena per un codice breve specifico.

#### Origine TON/NPI, destinazione TON/NPI {#ton-npi}

TON (Tipo di numero) e NPI (Indicatore del piano di numerazione) sono descritti nella sezione 5.2.5 del [Specifiche di SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pagina 117). Questi valori devono essere impostati sulle esigenze del provider.

Sono trasmessi così come sono `source_addr_ton`, `source_addr_npi`, `dest_addr_ton` e `dest_addr_npi` campi `SUBMIT_SM PDU`.

#### Tipo di servizio {#service-type}

Questo campo viene trasmesso così come è nella `service_type` campo `SUBMIT_SM PDU`. Imposta questo valore in base alle esigenze del provider.

### Throughput e timeout {#throughput-timeouts}

Queste impostazioni controllano tutti gli aspetti temporali del canale SMPP. Alcuni provider richiedono un controllo molto preciso della frequenza dei messaggi, degli intervalli delle finestre e dei tentativi. Queste impostazioni devono essere impostate su valori che corrispondano alla capacità del fornitore e alle condizioni indicate nel contratto.

#### Finestra di invio {#sending-window}

La finestra è il numero di `SUBMIT_SM PDU`che può essere inviato senza attendere una corrispondenza `SUBMIT_SM_RESP`.

Esempio di trasmissione con finestra massima 4:

![](assets/do-not-localize/sms_protocol_2.png)

La finestra consente di aumentare la velocità effettiva quando il collegamento di rete ha una latenza elevata.  Il valore della finestra deve essere almeno il numero di SMS/s moltiplicato per la latenza del collegamento in secondi, in modo che il connettore non sia in attesa di un `SUBMIT_SM_RESP` prima di inviare il messaggio successivo.
Se la finestra è troppo grande, puoi inviare più messaggi duplicati in caso di problemi di connessione. Inoltre, la maggior parte dei provider hanno un limite molto rigoroso per la finestra e rifiutano i messaggi che superano il limite.

Come calcolare la formula ottimale della finestra di invio:

* Misura la latenza massima tra `SUBMIT_SM` e `SUBMIT_SM_RESP`.

* Moltiplica questo valore in secondi al throughput MT massimo. Questo darà il valore ottimale della finestra di invio.

Esempio: Se hai 300 SMS/s impostato nel throughput massimo di MT e c&#39;è una latenza di 100 ms tra `SUBMIT_SM` e `SUBMIT_SM_RESP` in media, il valore ottimale sarebbe `300×0.1 = 30`.

#### Velocità effettiva max MT {#max-mt-throughput}

Numero massimo di MT al secondo e per connessione. Questa impostazione è rigorosamente applicata e l’MTA non invierà mai i messaggi push più velocemente di questo limite. È utile per i provider che richiedono una limitazione precisa.

Per conoscere il limite di throughput totale, moltiplica questo numero per il numero totale di connessioni come descritto nella formula precedente.

0 significa nessun limite, l&#39;MTA invierà MT il più rapidamente possibile.

Si raccomanda generalmente di mantenere questa impostazione al di sotto di 1000, poiché è impossibile garantire un throughput preciso al di sopra di questo numero, a meno che non sia adeguatamente valutato sull&#39;architettura finale e il provider SMPP specificamente richiesto. Potrebbe essere meglio aumentare il numero di connessioni da superare 1000 MT/s.

#### Tempo prima della riconnessione {#time-reconnection}

Quando la connessione TCP viene persa, il connettore attenderà questo numero di secondi prima di provare a effettuare una connessione.

#### Periodo di scadenza del MT {#expiration-period}

Timeout tra `SUBMIT_SM` e la sua corrispondenza `SUBMIT_SM_RESP`. Se la `RESP` non viene ricevuto in tempo, il messaggio verrà considerato come non riuscito e verranno applicati i criteri di esecuzione di nuovi tentativi globali dell’MTA.

#### Timeout del binding {#bind-timeout}

Timeout tra il tentativo di connessione TCP e il `BIND_*_RESP` rispondi. Quando si verifica un timeout, la connessione viene chiusa dal connettore Adobe Campaign e attenderà Tempo prima di riconnettersi prima di riprovare.

#### periodo inquire_link {#enquire-link-period}

`enquire_link` è un tipo speciale di PDU inviato per mantenere la connessione in vita. Questo periodo è in secondi. Il connettore della campagna invia solo `enquire_link` quando la connessione è inattiva per risparmiare larghezza di banda. Se non viene ricevuto alcun RESP dopo due volte questo periodo, la connessione verrà considerata morta e verrà attivato un processo di riconnessione.

### Specifiche di SMSC {#SMSC-specifics}

Queste impostazioni sono impostazioni avanzate che adattano il connettore Adobe Campaign alla maggior parte delle peculiarità di implementazione SMPP.

**Definire una mappatura specifica delle codifiche**

Consulta la sezione [Codifica testo SMS](sms-protocol.md#sms-text-encoding) per informazioni sulla codifica del testo.

Questa impostazione consente di definire una mappatura di codifica personalizzata, diversa dalla specifica. Sarà in grado di dichiarare un elenco di codifiche, insieme alle loro `data_coding` valore.

L’MTA tenterà di codificare utilizzando la prima codifica nell’elenco. In caso di errore, tenterà di utilizzare la codifica successiva nell’elenco, ecc. Se non è possibile utilizzare alcuna codifica per codificare il messaggio, si verifica un errore. Una volta trovata la codifica, l’MTA creerà l’ `SUBMIT_SM PDU` con il testo codificato e `data_coding` campo impostato con il valore specificato nella tabella.

L’ordine degli elementi nella tabella è importante: le codifiche sono tentativi dall&#39;alto verso il basso. Inserite la codifica più economica o consigliata in cima all’elenco, seguita da codifiche sempre più costose.

Tieni presente che UCS-2 non avrà mai esito negativo in quanto può codificare tutti i caratteri supportati in Adobe Campaign e che la lunghezza massima di un SMS UCS-2 è molto inferiore: Solo 70 caratteri.

È inoltre possibile utilizzare questa impostazione per forzare l’utilizzo di una codifica specifica dichiarando una sola riga nella tabella di mappatura.

La mappatura predefinita utilizzata quando la casella di controllo non è selezionata equivale alla tabella seguente:

| data_coding | Codifica |
|---|---|
| 0 | GSM |
| 9 | UCS-2 |

Questo significa che l’MTA cercherà di codificare il messaggio in GSM. Se ha successo, lo invierà con `data_coding` impostato su 0.

Se il messaggio non può essere codificato in GSM, verrà codificato in UCS-2 e verrà impostato `data_coding` 8.

#### Abilita message_payload {#enable-message-payload}

Se questa opzione è deselezionata, l’SMS lungo viene suddiviso dall’MTA e inviato in più `SUBMIT_SM PDU`s con UDH. Il messaggio sarà ricomposto dal cellulare in base ai dati UDH.

Se questa opzione è selezionata, l’SMS lungo verrà inviato in una delle PDU SUBMIT_SM, inserendo il testo nel campo opzionale message_payload . Consulta la sezione [Specifiche SMPP](sms-protocol.md#ACS-SMPP-connector) per ulteriori dettagli.

Se questa funzione è abilitata, Adobe Campaign non sarà in grado di contare le parti SMS singolarmente: tutti i messaggi saranno conteggiati come inviati in una parte.

#### Invia il numero di telefono completo {#send-full-phone-number}

Quando questa casella di controllo non è selezionata, vengono inviate al provider solo le cifre del numero di telefono (`destination_addr` campo `SUBMIT_SM` (campo). Questo è il comportamento predefinito, in quanto l’indicatore del numero internazionale, solitamente un prefisso +, viene sostituito dai campi TON e NPI in SMPP.

Quando la casella di controllo è selezionata, il numero di telefono viene inviato così com&#39;è, senza pre-elaborazione e spazi potenziali, + prefisso o cancelletto/hash/stella segni.

Questa funzione ha anche un effetto sul comportamento della funzione di elenco Bloccati di risposta automatica: se la casella di controllo non è selezionata, ai numeri di telefono inseriti nella tabella di quarantena verrà aggiunto un prefisso + per compensare la rimozione del prefisso + dal numero di telefono da parte del protocollo SMPP stesso.

#### Ignora controllo certificato TLS {#skip-tls}

Quando TLS è abilitato, salta tutti i controlli sui certificati.

Quando questa opzione è selezionata, la connessione non è più sicura e non deve essere abilitata in produzione.

Può essere utile a scopo di debug o test.

Per la convalida del certificato è possibile scegliere tra tre valori diversi:

* Verifica completa della certificazione (incluso il nome host), impostazione predefinita.
* Ignora la verifica del nome host.
* Ignora la verifica del certificato.

#### Bind TON/NPI {#bind-ton-npi}

TON (Tipo di numero) e NPI (Indicatore del piano di numerazione) descritti al punto 5.2.5 del [Specifiche di SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf) (pagina 117). Questi valori devono essere impostati in base alle esigenze del provider.

Sono trasmessi così come sono `addr_ton` e `addr_npi` campi della PDU BIND.

#### Intervallo indirizzi {#address-range}

Inviato come nel campo address_range della PDU BIND. Questo valore deve essere impostato su qualsiasi esigenza del provider.

#### Numero di riconoscimenti ID non valido {#invalid-id}

Limita il numero di **ID messaggio non valido** `DELIVER_SM_RESP` che può essere inviato per un singolo SR.

**Deve essere utilizzato solo per la risoluzione dei problemi come soluzione alternativa** e impostato su 0 in condizioni normali.

Esempio Fox, quando si imposta su 2:

* Il provider invia un SR (`DELIVER_SM`) con ID &quot;1234&quot;.

* Impossibile trovare l&#39;ID &quot;1234&quot; nel database.

* Il connettore conta 1 **ID non valido** errore per l&#39;ID, quindi invia `DELIVER_SM_RESP` con il codice di errore &quot;ID messaggio non valido&quot; (comportamento normale).

* Il provider prova lo stesso SR con ID &quot;1234&quot;.

* Impossibile trovare l&#39;ID &quot;1234&quot; nel database.

* Il connettore conta 2 **ID non valido** errore per l&#39;ID, quindi invia `DELIVER_SM_RESP` &quot;OK&quot;, anche se non è stato elaborato correttamente.

* Questa funzione è destinata a svuotare i buffer SR sul lato del provider quando un blocco SR non valido è legittimo che i messaggi non possano essere elaborati.

L&#39;impostazione di questo campo su 0 disattiva il meccanismo in cui **ID messaggio non valido** viene sempre restituito, si tratta di un comportamento normale.

Impostando questo campo su 1, il connettore risponde sempre &quot;OK&quot; anche se l’ID non è valido. Questo valore deve essere impostato su 1 solo sotto controllo, per la risoluzione dei problemi e per il periodo minimo di tempo, ad esempio per recuperare da un problema sul lato del fornitore.

#### Regex di estrazione dell’ID nell’SR {#regex-extraction}

Il formato SR non è rigorosamente applicato dalla specifica del protocollo SMPP. Si tratta solo di una raccomandazione descritta in [Appendice B](sms-protocol.md#sr-error-management) (pagina 167) del disciplinare. Alcuni implementatori SMPP formattano questo campo in modo diverso, pertanto Adobe Campaign ha bisogno di un modo per estrarre il campo corretto.

Per impostazione predefinita, acquisisce fino a 10 caratteri alfanumerici dopo `id:`.

Il regex deve avere esattamente un gruppo di cattura con una parte contenuta tra parentesi. Le parentesi devono circondare la parte ID. Il formato regex è PCRE.

Quando regoli questa impostazione, accertati di includere il maggior numero possibile di contesti per evitare falsi attivatori. In presenza di prefissi specifici, ad esempio `id:` nello standard, includerli nel regex. Utilizza anche il più possibile i delimitatori di parole (\b) per evitare di acquisire testo al centro di una parola.

L&#39;assenza di un contesto sufficiente nel regex può introdurre un piccolo difetto di sicurezza: il contenuto effettivo del messaggio può essere incluso nell&#39;SR. Se incontri solo un formato ID specifico senza contesto, ad esempio un UUID, potrebbe essere l’analisi del contenuto di testo effettivo, ad esempio un UUID incorporato nel campo di testo, invece dell’ID.

#### Regex applicato per determinare lo stato riuscito/errore {#regex-applied}

Quando si incontrano messaggi con una combinazione di campi stat/err sconosciuta, questi regex vengono applicati sul campo stat per determinare se l’SR è stato un successo o un errore. L’SR con valori stat che non corrispondono a nessuno di questi regex viene ignorato.

Per impostazione predefinita, i valori stat che iniziano con `DELIV`ad esempio `DELIVRD` in [Appendice B](sms-protocol.md#sr-error-management), verrà considerato come consegnato con successo e tutti i valori stat che corrispondono a errori, ad esempio `REJECTED`, `UNDELIV`, sono considerati errori.

#### Formato ID nella convalida MT {#id-format-mt}

Indica il formato dell&#39;ID restituito nella `message_id` campo `SUBMIT_SM_RESP PDU`.

* **Non modificare**: L’ID viene memorizzato come testo con codifica ASCII nel database. Non si verifica alcuna pre-elaborazione o filtraggio.

* **Numero decimale**: L&#39;ID deve essere un numero decimale in formato ASCII. Gli spazi iniziali e finali e gli zeri iniziali vengono rimossi quando si utilizza questa impostazione.

* **Numero esadecimale**: L&#39;ID deve essere un numero esadecimale in formato ASCII, senza l&#39;iniziale 0x o h finale. L&#39;ID viene quindi convertito in un numero decimale prima di essere memorizzato nel database.

* **Stringa esadecimale**: L’ID deve essere un testo con codifica ASCII che è a sua volta una stringa di byte codificati come esadecimale. Ad esempio, nella PDU troverai `0x34 0x31 0x34 0x32 0x34 0x33`, che si traduce in ASCII &quot;414243&quot;. Questa stringa viene quindi decodificata come stringa esadecimale di byte e si ottiene &quot;ABC&quot; come risultato: memorizzerai l&#39;ID &quot;ABC&quot; nel database.

#### Formato ID in SR {#id-format-sr}

Indica il formato dell&#39;ID acquisito dal `Extraction` regex dell&#39;ID nell&#39;SR. I valori hanno lo stesso significato e lo stesso comportamento del formato in MT sopra.

**ID SR o codice di errore nel campo opzionale**

>[!NOTE]
>
>Disponibile solo nel connettore SMPP esteso Adobe Campaign Classic.

Se questa opzione è selezionata, il contenuto dei campi facoltativi verrà aggiunto al testo elaborato dalle regex sopra riportate. Il testo avrà il formato `0xTAG:VALUE`, `0xTAG` il valore esadecimale a 4 cifre del tag in maiuscolo, ad esempio `0x002E`.

Ad esempio, puoi acquisire l’ID in `receipted_message_id` campo . A questo scopo, abilita questa casella di controllo e il seguente testo verrà aggiunto allo stato :

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

Se selezionato, il **Testo** Il campo viene mantenuto durante l&#39;elaborazione del testo dello stato dell&#39;SR.

Questa opzione è utile se il provider inserisce dati importanti in questo campo, come l’ID o lo stato . Di solito questo campo può essere ignorato in modo sicuro, poiché potrebbe contenere testo con una codifica non ASCII e interrompere l’elaborazione regex.

L’abilitazione di questa opzione può presentare un difetto di sicurezza molto piccolo se la `Extraction` L&#39;espressione regex dell&#39;ID nel campo SR non è sufficientemente specifica. Il contenuto del **Testo** Il campo può essere analizzato come ID e un autore dell’attacco può usarlo per inserire ID falsi, il che può causare una parziale negazione della situazione del servizio.

**ID servizio**

Consente di aggiungere un TLV personalizzato. Questo campo imposta la porzione di tag. Il valore può essere personalizzato per consegna nel **ID servizio o programma** nei parametri avanzati della consegna.

Questa impostazione consente di aggiungere solo un’opzione TLV per messaggio.

### Risposta automatica inviata al MO {#automatic-reply}

>[!IMPORTANT]
>
>In Adobe Campaign Classic e in un&#39;architettura ibrida, l&#39;applicazione della risposta automatica per il connettore SMPP esteso richiede di aggiungere l&#39;accesso in scrittura per l&#39;operatore mid sul **Account esterno** cartella.

Questa funzione consente di rispondere rapidamente al testo su MO e di gestire l’invio di codice per breve tempo al elenco Bloccati.

La **Parola chiave** e **Codice breve** Le colonne definiscono le condizioni per attivare la risposta automatica. Se entrambi i campi corrispondono, viene inviato l’MO e viene attivata l’azione aggiuntiva. Per specificare un carattere jolly, lasciare vuoto il campo . Parola chiave corrisponde alla prima parola alfanumerica nel testo M, ignorando la punteggiatura e gli spazi iniziali. Significa che **Parola chiave** Il campo non può contenere spazi e deve essere una sola parola.

La **Parola chiave** è un prefisso. Ad esempio, se specifichi &quot;AD&quot;, corrisponderà a &quot;AD&quot;, &quot;ADAPT&quot; e &quot;ADOBE&quot;. Se si dispone di più parole chiave con un prefisso comune, è necessario prestare attenzione all&#39;ordine in quanto le parole chiave vengono elaborate dall&#39;alto verso il basso.

La **Rispondi** Il testo da rispondere è column . In questo campo non è disponibile alcuna personalizzazione. Se lasci vuoto questo campo, non verrà risposto alcun messaggio, ma verrà comunque attivata l’azione aggiuntiva.

La **Azione aggiuntiva** La colonna fornisce un’azione aggiuntiva quando entrambe **Parola chiave** e **Codice breve** Il codice breve vuoto corrisponde a tutti i codici brevi. È possibile mettere in quarantena o rimuovere dalla quarantena, il valore nessuna risponde al testo. Se specifichi un **Azione aggiuntiva** ma lascia la **Rispondi** campo vuoto, l’azione verrà eseguita ma non verrà inviata alcuna risposta. La quarantena viene applicata solo al codice breve specificato o a tutti i codici brevi se il campo viene lasciato vuoto.

>[!IMPORTANT]
>
>L&#39;impostazione di invio del numero di telefono completo ha un impatto sul comportamento del meccanismo di quarantena di risposta automatica: se l&#39;invio del numero di telefono completo non è controllato, il numero di telefono messo in quarantena sarà preceduto da un segno più (&quot;+&quot;) per renderlo compatibile con il formato del numero di telefono internazionale.

Tutte le voci nella tabella vengono elaborate nell’ordine specificato, fino a quando non corrisponde una regola. Se più regole corrispondono a un MO, verrà applicata solo la regola più in alto.

## Parametri del modello di consegna SMS {#sms-delivery-template-parameters}

Alcuni parametri possono essere impostati per modello di consegna.

### Campo Da {#from-field}

Questo campo è facoltativo. Consente di ignorare l’indirizzo del mittente (oADC). Il contenuto di questo campo viene inserito nella `source_addr` campo `SUBMIT_SM PDU`.

Il campo è limitato a 21 caratteri dalla specifica SMPP, ma alcuni provider potrebbero consentire valori più lunghi. Tieni presente che in alcuni paesi possono essere applicate restrizioni molto rigorose, ad esempio lunghezza, contenuto e caratteri consentiti.

### Parametri di consegna {#delivery-parameters}

#### Numero massimo di SMS per messaggio {#maximum-sms}

Questa impostazione funziona solo se **Payload messaggio** è disabilitata. Se il messaggio richiede più SMS di questo valore, viene attivato un errore.

Il protocollo SMS limita gli SMS a 255 parti, ma alcuni telefoni cellulari hanno problemi a mettere insieme messaggi lunghi con più di 10 parti o giù di lì, il limite dipende dal modello esatto. Ti consigliamo di non passare oltre 5 parti per messaggio.

A causa del funzionamento dei messaggi personalizzati in Adobe Campaign, le dimensioni dei messaggi possono variare. Avere una grande quantità di messaggi lunghi potrebbe aumentare i costi di invio.

#### Modalità di trasmissione {#transmission-mode}

Questo campo indica il tipo di SMS che desideri trasferire: messaggi normali o flash, memorizzati sul cellulare o sulla scheda SIM.

Questa impostazione viene trasmessa nella `dest_addr_subunit` campo opzionale nel `SUBMIT_SM PDU`.

* **Non specificato** non invia alcun campo facoltativo nella PDU.

* **Flash** imposta il valore su 1. Invia un messaggio Flash che compare sul dispositivo mobile e non viene memorizzato in memoria.

* **Normale** imposta il valore su 0. Invia un messaggio normale.

* **Salva su dispositivi mobili** imposta il valore su 2. Indica al telefono di memorizzare l’SMS nella memoria interna.

* **Salva sul terminale** imposta il valore su 3. Dice al telefono di memorizzare l&#39;SMS nella scheda SIM.

#### Periodo di validità {#validity-period}

Il periodo di validità è trasmesso nel `validity_period` campo `SUBMIT_SM PDU`. La data viene sempre formattata come formato di ora UTC assoluto; il campo data termina con &quot;00+&quot;.

## Connettore SMPP generico esteso {#acc-extended-connector}

![](assets/do-not-localize/sms_protocol_4.png)

Le frecce rappresentano i flussi di dati.

Quando si inviano parti di consegna, l’MTA genera elementi secondari MTA. Il numero di processi figlio MTA è dinamico e dipende da una configurazione in serverConf.xml. Ogni elemento figlio MTA crea un&#39;istanza del connettore `CSmppConnectorWorker` che si connette al provider SMPP. Le connessioni vengono mantenute in vita finché il figlio MTA viene mantenuto in vita, configurabile anche in serverConf.xml.

Il processo SMS elabora solo l’SR, si connette al provider e lascia aperta la connessione. Il processo si riconnette ogni 10 minuti per ricaricare nuove impostazioni, operazione normale.

### Voci MT, SR e broadlog corrispondenti {#matching-mt}

Tabella intermedia `nmsProviderMsgId` viene utilizzato per memorizzare temporaneamente i dati MT e SR prima di essere impegnati in modo asincrono nel registro di trasmissione.

`nmsProviderMsgId` La tabella ha 3 gruppi di colonne:

* Colonne aggiornate quando un MT viene inviato e riconosciuto: `iBroadLogId`, `iDeliveryId`

* Colonne aggiornate quando viene ricevuto un SR: `iMsgId`, `iStatus`

* Colonne sempre aggiornate: `tsCreated`, `sProviderId`

Al termine dell&#39;elaborazione MT e SR, è necessario disporre di linee complete, sia con le informazioni del registro di trasmissione che con le informazioni sullo stato.

Qui, `iMsgId` è collegato a `nmsBroadLogMsg` tabella, che indica il messaggio di stato/errore completo.

Il processo SMS verifica la presenza di righe complete ogni minuto, quindi le elabora in modo asincrono:

* Viene letta la riga completa.
* Il processo SMS calcola il nome della tabella del registro di trasmissione in base alla mappatura della consegna.
* Il processo SMS aggiorna la tabella del registro di trasmissione con l’ID del messaggio e lo stato .

**Connessioni Throughput e parallele**

Ogni elemento figlio MTA crea una quantità configurabile di connessioni, pertanto limitare il numero di elementi figlio MTA limiterà il numero di connessioni. Poiché la correlazione tra i processi secondari MTA e il traffico è correlata, questo può essere in qualche modo controllato ma ancora un po&#39; imprevedibile.

## Prima di andare in diretta {#checklist}

Questa lista di controllo fornisce un elenco degli elementi da controllare prima di essere live. Una configurazione incompleta può causare molti problemi.

### Verifica conflitti di account esterni {#external-account-conflict}

Verifica di non disporre di vecchi account esterni SMS. Se l&#39;account di test viene disattivato, correte il rischio che venga riabilitato nel sistema di produzione e generato potenziali conflitti.

Se disponi di più account sulla stessa istanza di Adobe Campaign che si connettono allo stesso provider, contatta il provider per assicurarti che distinguano effettivamente le connessioni tra questi account. Disporre di più account con lo stesso accesso richiede una configurazione aggiuntiva.

### Abilita tracce SMPP dettagliate durante i controlli {#enable-verbose}

È sempre necessario abilitare tracce SMPP dettagliate durante i controlli.
Anche se non puoi controllare i log da solo, sarà più facile per [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per aiutarti.

### Test dell’SMS {#test}

* **Invia SMS con tutti i tipi di caratteri**
Se devi inviare SMS con caratteri non GSM o non ASCII, prova a inviare alcuni messaggi con il maggior numero possibile di caratteri diversi. Se imposti una tabella di mappatura dei caratteri personalizzata, invia almeno un SMS per tutti i possibili 
`data_coding` values.

* **Verificare che SR sia elaborato correttamente**
L’SMS deve essere contrassegnato come ricevuto nel registro di consegna. Il registro di consegna deve avere esito positivo ed essere simile al seguente: Verifica di aver modificato il nome del provider di consegna. Il registro di consegna non deve mai contenere    `SR yourProvider stat=DELIVRD err=000|#MESSAGE`
Verifica di aver modificato il nome del provider di consegna. Il registro di consegna non deve mai contenere **Generico SR** in ambienti di produzione.

* **Verificare che la funzione MO sia elaborata**
Se è necessario elaborare MO (risposte automatiche, archiviazione MO nel database, ecc.) prova a fare alcuni test. Invia qualche SMS per tutte le parole chiave di risposta automatica e controlla se la risposta è abbastanza veloce, non più di pochi secondi.
Controlla nel registro che Adobe Campaign risponda con successo 
`DELIVER_SM_RESP` (command_status=0).

### Controllare le PDU {#check-pdus}

Anche se i messaggi sembrano di successo, è importante verificare che le PDU siano formattate correttamente.

Questo passaggio è necessario quando ci si connette a un provider che non era collegato ad Adobe Campaign in precedenza.

#### DIETRO {#bind}

Controlla che `BIND_* PDUs` sono inviate correttamente. La cosa più importante da verificare è che il provider restituisce sempre successo `BIND_*_RESP PDUs` (command_status = 0).

Controlla che non ci siano troppi `BIND_* PDU`s. Se ce ne sono troppi, potrebbe indicare che la connessione è instabile. Consulta la sezione [Problemi con connessioni instabili](sms-protocol.md#issues-unstable-connection) per ulteriori informazioni.

#### INQUIRE_LINK {#enquire-link-pdus}

Controlla che `ENQUIRE_LINK PDU`s sono scambiati regolarmente quando la connessione è inattiva.

**SUBMIT_SM / DELIVER_SM**

Invia un messaggio, quindi cerca nei registri il relativo `SUBMIT_SM`, `SUBMIT_SM_RESP`, `DELIVER_SM` e `DELIVER_SM_RESP PDU`s.

Con la `SUBMIT_SM PDU`:

* Controlla che `data_coding` è corretto, 0 per impostazione predefinita.
* Controlla che `short_message` è codificato correttamente. Prova a decodificarlo utilizzando un convertitore esadecimale che supporta più codifiche.

Con la `SUBMIT_SM_RESP PDU`:

* Verificare che sia stato eseguito correttamente, command_status = 0.
* Verificare che il corpo contenga un ID formattato correttamente seguito da un byte &#39;0&#39;.

Con la `DELIVER_SM PDU`:

* Decodificare l&#39;esadecimale `short_message` campo .
* Controlla con uno strumento di controllo regex che il regex definito in `Extraction` L&#39;espressione regex dell&#39;ID nell&#39;SR restituisce esattamente un gruppo di acquisizione e acquisisce l&#39;intero ID nel messaggio.
* Verifica che l&#39;ID estratto corrisponda a quello in `SUBMIT_SM_RESP`.
* Controlla che il regex sia definito in `Extraction` regex dello stato nell&#39;SR restituisce il contenuto del campo stat.
* Controlla che il regex sia definito in `Extraction` Il regex dell&#39;errore nell&#39;SR restituisce il contenuto del campo err.

Con la `DELIVER_SM_RESP PDU`:

* Verifica che sia stato inviato rapidamente dopo la ricezione del `DELIVER_SM PDU`, generalmente inferiore a 1 secondo.
* Verificare che sia stato eseguito correttamente, command_status = 0.

### Controlla con il tuo provider {#provider}

Anche se l’SMS ha esito positivo, contatta il provider per vedere se tutto è in ordine.

### Disattiva tracce SMPP dettagliate {#disable-verbose}

Una volta completati tutti i controlli, l&#39;ultima cosa è **Disattiva tracce SMPP dettagliate** per non generare troppi registri. Puoi riabilitarli per la risoluzione dei problemi anche sui sistemi di produzione.
