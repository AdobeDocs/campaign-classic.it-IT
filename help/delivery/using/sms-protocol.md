---
product: campaign
title: Protocollo e impostazioni del connettore SMS
description: Ulteriori informazioni sul connettore SMS e su come configurarlo
feature: SMS
role: Developer
exl-id: fded088a-11a2-4b87-a368-7b197334aca4
TQID: 'https://experienceleague.adobe.com/-e39I2kK3veYtZTufN0ZZrnZPAAco47dU8HFlCtlIxY'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b1bd1421-1927-4c59-9bc6-ce292360e43b
    internal-label: SMS Messaging
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
    internal-label: Troubleshooting
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '4785'
ht-degree: 1%
---
# Protocollo e impostazioni del connettore SMS {#sms-connector-protocol}

>[!NOTE]
>
>In questo documento, tutti i riferimenti ai dettagli del protocollo, dei nomi dei campi e dei valori fanno riferimento alla [specifica SMPP 3.4](https://smpp.org/SMPP_v3_4_Issue1_2.pdf).
>

Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8. Per ulteriori informazioni sulle impostazioni del connettore SMS, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}.

[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account){target=_blank}

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

Il protocollo non è crittografato. La maggior parte dei provider implementa una variante di IP su un elenco Consentiti di in modo che gli indirizzi IP del server Adobe Campaign debbano essere dichiarati al provider.

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

* **data_coding**: indica la codifica utilizzata nel campo di testo. Per ulteriori informazioni, consulta la sezione [Codifica testo SMS](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/sms/sms-channel#sms-text-encoding){target="_blank"} (documentazione di Campaign v8).

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

### Limitazione velocità effettiva e finestra {#throughput-capping}

La maggior parte dei provider richiede un limite di velocità effettiva per ogni connessione SMPP. Ciò può essere ottenuto impostando una serie di SMS nell’account esterno. Si noti che la limitazione della velocità effettiva avviene per connessione, la velocità effettiva totale è il limite per connessione moltiplicato per il numero totale di connessioni. Questo è descritto nella sezione [Connessioni simultanee](sms-protocol.md#connection-settings).

Per raggiungere il massimo throughput possibile, è necessario regolare con precisione la finestra di invio massima. La finestra di invio è il numero di `SUBMIT_SM PDU` che possono essere inviati senza attendere un `SUBMIT_SM_RESP`. Per ulteriori dettagli, consulta la sezione [Impostazione della finestra di invio](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/sms/config-sms/smpp-external-account#smpp-delays){target="_blank"} (documentazione di Campaign v8).

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

## Parametri dell’account esterno SMPP {#SMPP-parameters-external}

Ogni implementazione del protocollo SMPP presenta diverse varianti. Per migliorare la compatibilità e l’adattabilità, sono disponibili molte impostazioni che consentono di modificare il comportamento del connettore SMPP. In questa sezione vengono descritti tutti i parametri e i relativi effetti sul connettore.

### Parametri generali e percorso {#general-parameters-routing}

**Limita istanze MTA per questo account**

È possibile impostare un limite al numero di istanze MTA consentite per la connessione al provider SMPP. Se questa opzione è selezionata, puoi specificare quanti MTA possono essere utilizzati al massimo.

Questa opzione consente un controllo più preciso sul numero di connessioni. Vedere [Connessioni simultanee](sms-protocol.md#connection-settings).

Se imposti un valore superiore al numero di MTA in esecuzione, tutti gli MTA verranno eseguiti come normale: questa opzione è solo un limite e non può generare MTA aggiuntivi.

Se devi controllare con precisione il numero di connessioni, ad esempio il requisito del provider, è consigliabile impostare sempre questa opzione anche se la distribuzione corrente dispone del numero corretto di MTA in esecuzione. Se in seguito vengono aggiunti altri MTA, il limite di connessione verrà comunque rispettato.

### Impostazioni della connessione {#connection-settings}

#### Nome dell’implementazione SMSC {#smsc-implementation-name}

Imposta il nome dell’implementazione SMSC. Deve essere impostato sul nome del provider. Contatta l’amministratore o il team di recapito messaggi per sapere cosa aggiungere in questo campo. Il ruolo di questo campo è descritto nella sezione [Gestione errori SR](sms-protocol.md#sr-error-management).

>[!NOTE]
>
>Il team di recapito messaggi si basa sul contratto e i clienti devono contattare il proprio rappresentante Adobe per informazioni relative al recapito messaggi.

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

### Impostazioni canale SMPP {#smpp-channel-settings}

#### Memorizza MO in ingresso nel database {#incoming-mo-storing}

Quando questa opzione è attivata, il MO in ingresso verrà memorizzato nella tabella inSMS del database. È possibile eseguire query su questa tabella utilizzando l&#39;attività di query di qualsiasi flusso di lavoro.

Adobe Campaign Classic memorizza sempre tutti i messaggi MO nel database inSMS, pertanto questa opzione non è disponibile.

#### Abilita aggiornamenti dei KPI in tempo reale durante l’elaborazione SR {#real-time-kpi}

Quando questa opzione è abilitata, i KPI vengono aggiornati in tempo reale sulla pagina di consegna principale quando si riceve l’errore SR.

L&#39;inconveniente può essere rappresentato da prestazioni insufficienti a causa del conflitto di database generato. Se disabilitata, le statistiche vengono aggiornate dal flusso di lavoro **syncfromexec**, in esecuzione ogni 20 minuti.

Adobe Campaign Classic dispone di un meccanismo completamente diverso per i KPI, pertanto questa opzione non è disponibile.

#### Codice breve {#short-code}

Indica il codice breve principale dell’account. Se per questo account vengono utilizzati più codici brevi o se il codice breve è sconosciuto, lascia vuoto questo campo.

La specifica di un codice breve è utile per due funzioni:

* Se non viene fornito alcun numero di origine, nell’anteprima viene visualizzato il codice breve. Rifletterà il comportamento reale sul telefono cellulare.

* L’impostazione di inserisce nell&#39;elenco Bloccati del codice di risposta automatica dell’di mette in quarantena l’utente solo per un codice breve specifico.

### Specifiche di SMSC {#SMSC-specifics}

Si tratta di impostazioni avanzate che adattano il connettore Adobe Campaign alla maggior parte delle peculiarità dell’implementazione SMPP.

#### Ignora controllo certificato TLS {#skip-tls}

Quando TLS è abilitato, ignora tutti i controlli dei certificati.

Se questa opzione è selezionata, la connessione non è più sicura e non deve essere abilitata in produzione.

Può essere utile a scopo di debug o test.

È possibile scegliere tra tre valori diversi per la convalida del certificato:

* Verifica della certificazione completa (incluso il nome host), impostazione predefinita.
* Ignora la verifica del nome host.
* Ignora la verifica del certificato.

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

### Parametri di consegna {#delivery-parameters}

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
