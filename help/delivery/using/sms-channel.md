---
solution: Campaign Classic
product: campaign
title: Canale SMS
description: Canale SMS
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: f78fa94fb4fb9236222886a167a46d252497b2aa
workflow-type: tm+mt
source-wordcount: '3131'
ht-degree: 20%

---


# Canale SMS{#sms-channel}

Adobe Campaign ti consente di eseguire consegne personalizzate di massa di messaggi SMS. I profili dei destinatari devono contenere almeno un numero di telefono cellulare.

>[!NOTE]
>
>Adobe Campaign consente inoltre di inviare notifiche sui terminali mobili tramite l&#39;opzione **Adobe Campaign Mobile App Channel (NMAC)**.
> 
>Per ulteriori informazioni, consulta la sezione [Informazioni sul canale app mobile](../../delivery/using/about-mobile-app-channel.md) .

Le sezioni seguenti forniscono informazioni specifiche per il canale SMS. Per informazioni globali su come creare una consegna, consulta [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

## Configurazione del canale SMS {#setting-up-sms-channel}

Per inviare a un telefono cellulare, è necessario:

1. Un account esterno che specifica un connettore e il tipo di messaggio.

   A partire dalla versione 20.2, i seguenti connettori saranno obsoleti: SMPP generico (SMPP versione 3.4 che supporta la modalità binaria), Sybase365 (SAP SMS 365), CLX Communications, Tele2, O2 e iOS. Le funzionalità obsolete sono ancora disponibili, ma non saranno ulteriormente migliorate né supportate. Per ulteriori informazioni, consulta questa [pagina](https://helpx.adobe.com/it/campaign/kb/deprecated-and-removed-features.html).

1. Un modello di consegna in cui viene fatto riferimento a questo account esterno.

### Creazione di un account esterno SMPP {#creating-an-smpp-external-account}

Per inviare un SMS a un cellulare, devi innanzitutto creare il tuo account esterno SMPP.
Per ulteriori informazioni sul protocollo e le impostazioni SMS, consulta questa [pagina](../../delivery/using/sms-protocol.md).

Per farlo, segui la procedura indicata di seguito:

1. Nel nodo **[!UICONTROL Platform]** > **[!UICONTROL External accounts]** della struttura, fai clic sull&#39;icona **[!UICONTROL New]**.
1. Definisci il tipo di account come **Routing**, il canale come **Mobile (SMS)** e la modalità di consegna come **Consegna in blocco**.

   ![](assets/extended_smpp_create_account.png)

1. Seleziona la casella **[!UICONTROL Enabled]** .
1. Nella scheda **[!UICONTROL Mobile]** , seleziona **[!UICONTROL Extended generic SMPP]** dall’elenco a discesa **[!UICONTROL Connector]** .

   ![](assets/extended_smpp_connector.png)

   >[!CAUTION]
   >
   > A partire dalla versione 20.2, i connettori legacy sono obsoleti e non supportati. È consigliabile utilizzare il connettore **[!UICONTROL Extended generic SMPP]**. Per ulteriori informazioni sulla migrazione al connettore consigliato, consulta questa [pagina](../../delivery/using/unsupported-connector-migration.md).

1. L’opzione **[!UICONTROL Enable verbose SMPP traces in the log file]** ti consente di scaricare tutto il traffico SMPP nei file di registro. Devi abilitare questa opzione per risolvere i problemi del connettore e per confrontare il traffico rilevato dal provider.

1. Contatta il provider di servizi SMS per spiegarti come completare i diversi campi dell’account esterno dalla scheda **[!UICONTROL Connection settings]** .

   Quindi, contatta il tuo provider, a seconda di quello scelto, che ti darà il valore da inserire nel campo **[!UICONTROL SMSC implementation name]** .

   Puoi definire il numero di connessioni al provider per figlio MTA. Per impostazione predefinita, è impostato su 1.

1. Per impostazione predefinita, il numero di caratteri in un SMS soddisfa gli standard GSM.

   I messaggi SMS che utilizzano la codifica GSM sono limitati a 160 caratteri o 153 caratteri per SMS per messaggi inviati in più parti.

   >[!NOTE]
   >
   >Alcuni caratteri contano come due (parentesi graffe e quadre, il simbolo dell’euro, ecc.).
   >
   >L’elenco dei caratteri GSM disponibili è presentato di seguito.

   Se lo desideri, puoi autorizzare la traslitterazione di caratteri selezionando la casella corrispondente.

   ![](assets/extended_smpp_transliteration.png)

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#about-character-transliteration).

1. Nella scheda **[!UICONTROL Throughput and delays]** puoi specificare il throughput massimo dei messaggi in uscita (&quot;MT&quot;, Mobile Terminated) in MT al secondo. Se inserisci &quot;0&quot; nel campo corrispondente, il throughput effettivo sarà illimitato.

   È necessario completare in secondi i valori di tutti i campi corrispondenti alle durate.

1. Nella scheda **[!UICONTROL Mapping of encodings]** puoi definire le codifiche.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#about-text-encodings).

1. Nella scheda **[!UICONTROL SMSC specificities]** , l’opzione **[!UICONTROL Send full phone number]** è disabilitata per impostazione predefinita. Non attivarla se desideri rispettare il protocollo SMPP e trasferire solo le cifre al server del provider SMS (SMSC).

   Tuttavia, dato che alcuni provider richiedono l’uso del prefisso &quot;+&quot;, ti consigliamo di verificare con il provider se è necessario abilitare questa opzione.

   La casella di controllo **[!UICONTROL Enable TLS over SMPP]** ti consente di crittografare il traffico SMPP. Per ulteriori informazioni, consulta questa [pagina](../../delivery/using/sms-protocol.md).

1. Se stai configurando un connettore **[!UICONTROL Extended generic SMPP]**, puoi impostare le risposte automatiche.

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#automatic-reply).

### Informazioni sulla traslitterazione di caratteri {#about-character-transliteration}

La traslitterazione dei caratteri può essere impostata in un account esterno SMPP mobile delivery, nella scheda **[!UICONTROL Mobile]** .

La traslitterazione consiste nel sostituire un carattere di un SMS con un altro quando quel carattere non è preso in considerazione dallo standard GSM.

* Se la traslitterazione è **[!UICONTROL authorized]**, ogni carattere non preso in considerazione viene sostituito da un carattere GSM al momento dell’invio del messaggio. Ad esempio, la lettera &quot;ë&quot; è sostituita da &quot;e&quot;. Il messaggio viene quindi leggermente modificato, ma il limite di caratteri rimane lo stesso.
* Quando la traslitterazione è **[!UICONTROL not authorized]**, ogni messaggio che contiene caratteri non presi in considerazione viene inviato in formato binario (Unicode): tutti i caratteri vengono quindi inviati così come sono. Tuttavia, i messaggi SMS che utilizzano Unicode sono limitati a 70 caratteri (o 67 caratteri per SMS per messaggi inviati in più parti). Se viene superato il numero massimo di caratteri, vengono inviati diversi messaggi, il che potrebbe comportare costi aggiuntivi.

>[!IMPORTANT]
>
>L’inserimento di campi di personalizzazione nel contenuto del messaggio SMS può introdurre caratteri che non vengono presi in considerazione dalla codifica GSM.

Per impostazione predefinita, la traslitterazione di caratteri è disabilitata. Se desideri che tutti i caratteri nei messaggi SMS rimangano invariati, per non modificare ad esempio i nomi propri, ti consigliamo di non abilitare questa opzione.

Tuttavia, se i messaggi SMS contengono molti caratteri che generano messaggi Unicode, puoi abilitare questa opzione per limitare i costi di invio dei messaggi.

La tabella seguente presenta i caratteri presi in considerazione dallo standard GSM. Tutti i caratteri inseriti nel corpo del messaggio, diversi da quelli indicati di seguito, convertono l’intero messaggio in formato binario (Unicode) e quindi lo limitano a 70 caratteri.

**Caratteri base**

<table> 
 <tbody> 
  <tr> 
   <td> @ </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> SP </td> 
   <td> 0 </td> 
   <td> .4 </td> 
   <td> P </td> 
   <td> È </td> 
   <td> p </td> 
  </tr> 
  <tr> 
   <td> £ </td> 
   <td> _ </td> 
   <td> ! </td> 
   <td> 1 </td> 
   <td> A </td> 
   <td> Q </td> 
   <td> a </td> 
   <td> q </td> 
  </tr> 
  <tr> 
   <td> $ </td> 
   <td> <img height="21px" src="assets/phi.png" /> </td> 
   <td> " </td> 
   <td> 2 </td> 
   <td> B </td> 
   <td> R </td> 
   <td> b </td> 
   <td> r </td> 
  </tr> 
  <tr> 
   <td> ¥ </td> 
   <td> <img height="21px" src="assets/gamma.png" /> </td> 
   <td> # </td> 
   <td> 3 </td> 
   <td> C </td> 
   <td> S </td> 
   <td> c </td> 
   <td> s </td> 
  </tr> 
  <tr> 
   <td> è </td> 
   <td> <img height="21px" src="assets/delta.png" /> </td> 
   <td> m </td> 
   <td> 4 </td> 
   <td> D </td> 
   <td> T </td> 
   <td> d </td> 
   <td> t </td> 
  </tr> 
  <tr> 
   <td> é </td> 
   <td> <img height="21px" src="assets/omega.png" /> </td> 
   <td> % </td> 
   <td> 5 </td> 
   <td> E </td> 
   <td> U </td> 
   <td> e </td> 
   <td> u </td> 
  </tr> 
  <tr> 
   <td> ù </td> 
   <td> <img height="21px" src="assets/pi.png" /> </td> 
   <td> &amp; </td> 
   <td> 6 </td> 
   <td> F </td> 
   <td> V </td> 
   <td> f </td> 
   <td> v </td> 
  </tr> 
  <tr> 
   <td> ì </td> 
   <td> <img height="21px" src="assets/psi.png" /> </td> 
   <td> ' </td> 
   <td> 7 </td> 
   <td> G </td> 
   <td> W </td> 
   <td> g </td> 
   <td> w </td> 
  </tr> 
  <tr> 
   <td> ò </td> 
   <td> <img height="21px" src="assets/sigma.png" /> </td> 
   <td> ( </td> 
   <td> 8 </td> 
   <td> H </td> 
   <td> X </td> 
   <td> h </td> 
   <td> x </td> 
  </tr> 
  <tr> 
   <td> Ç </td> 
   <td> <img height="21px" src="assets/theta.png" /> </td> 
   <td> ) </td> 
   <td> 9 </td> 
   <td> I </td> 
   <td> Y </td> 
   <td> i </td> 
   <td> y </td> 
  </tr> 
  <tr> 
   <td> LF </td> 
   <td> <img height="21px" src="assets/xi.png" /> </td> 
   <td> * </td> 
   <td> : </td> 
   <td> J </td> 
   <td> Z </td> 
   <td> j </td> 
   <td> z </td> 
  </tr> 
  <tr> 
   <td> Ø </td> 
   <td> ESC </td> 
   <td> + </td> 
   <td> ; </td> 
   <td> K </td> 
   <td> Ä </td> 
   <td> k </td> 
   <td> ä </td> 
  </tr> 
  <tr> 
   <td> ø </td> 
   <td> Æ </td> 
   <td> , </td> 
   <td> &lt;&gt; </td> 
   <td> L </td> 
   <td> Ö </td> 
   <td> l </td> 
   <td> ö </td> 
  </tr> 
  <tr> 
   <td> CR </td> 
   <td> æ </td> 
   <td> - </td> 
   <td> = </td> 
   <td> M </td> 
   <td> Ñ </td> 
   <td> m </td> 
   <td> ñ </td> 
  </tr> 
  <tr> 
   <td> Å </td> 
   <td> ß </td> 
   <td> . </td> 
   <td> &gt; </td> 
   <td> N </td> 
   <td> Ü </td> 
   <td> n </td> 
   <td> ü </td> 
  </tr> 
  <tr> 
   <td> å </td> 
   <td> É </td> 
   <td> / </td> 
   <td> ? </td> 
   <td> O </td> 
   <td> § </td> 
   <td> o </td> 
   <td> à </td> 
  </tr> 
 </tbody> 
</table>

SP: Space

ESC: Escape

LF: Line Feed (avanzamento di riga)

CR: Carriage Return (ritorno a capo)

**Caratteri avanzati (contati due volte)**

^ { } `[ ~ ]` | €

### Informazioni sulle codifiche di testo {#about-text-encodings}

Al momento di inviare un messaggio SMS, Adobe Campaign può utilizzare una o più codifiche di testo. Ogni codifica ha un set di caratteri specifico e determina il numero di caratteri da includere in un messaggio SMS.

Durante la configurazione di un nuovo account esterno per la consegna mobile SMPP, puoi definire il percorso **[!UICONTROL Mapping of encodings]** nella scheda **[!UICONTROL Mobile]** : il campo **[!UICONTROL data_coding]** consente ad Adobe Campaign di comunicare quale codifica viene utilizzata per SMSC.

>[!NOTE]
>
>La mappatura tra il valore **data_coding** e la codifica effettivamente utilizzata è standardizzata. Tuttavia, alcuni SMSC hanno una propria mappatura specifica: in questo caso, l&#39;amministratore di **Adobe Campaign** deve dichiarare questa mappatura. Consulta il provider per saperne di più.

Puoi dichiarare **data_codings** e forzare la codifica, se necessario: a questo scopo, specifica una singola codifica nella tabella.

* Quando non viene definita alcuna mappatura delle codifiche, il connettore assume un comportamento generico:

   * Prova a utilizzare la codifica GSM a cui assegna il valore **data_coding = 0**.
   * Se non è possibile usare la codifica GSM, utilizza la codifica **UCS2** assegnandole il valore **data_coding = 8**.

* Quando definisci le codifiche desiderate e i valori dei campi **[!UICONTROL data_coding]** collegati, Adobe Campaign tenterà di utilizzare la prima codifica nell’elenco, quindi la seguente, se la prima codifica risulta impossibile.

>[!IMPORTANT]
>
>L’ordine di dichiarazione è importante: ti consigliamo di inserire l’elenco in ordine crescente **di costo** per favorire le codifiche che ti consentono di contenere il maggior numero possibile di caratteri in ogni messaggio SMS.
>
>Dichiara solo le codifiche che desideri utilizzare. Se alcune delle codifiche fornite dal SMSC non devono corrispondere al tuo scopo d&#39;uso, non dichiararle nell&#39;elenco.

### Risposta automatica {#automatic-reply}

Quando si imposta un connettore SMPP generico esteso, è possibile configurare le risposte automatiche.

Quando un utente con sottoscrizione risponde a un messaggio SMS inviato tramite Adobe Campaign e il relativo messaggio contiene una parola chiave come &quot;STOP&quot;, puoi configurare i messaggi che vengono automaticamente ritrasmessi nella sezione **[!UICONTROL Automatic reply sent to the MO]** .

>[!NOTE]
>
>Le parole chiave non sono sensibili all’uso di maiuscole e minuscole.

Per ogni parola chiave, specifica un codice breve, che è un numero generalmente utilizzato per inviare consegne e fungerà da nome mittente, quindi inserisci il messaggio che verrà inviato al sottoscrittore.

Puoi anche collegare un’azione alla risposta automatica: **[!UICONTROL Send to quarantine]** o **[!UICONTROL Remove from quarantine]**. Ad esempio, se un destinatario invia la parola chiave &quot;STOP&quot;, riceverà automaticamente una conferma dell’annullamento dell’abbonamento e verrà messo in quarantena.

![](assets/extended_smpp_reply.png)

Se colleghi l’azione **[!UICONTROL Remove from quarantine]** a una risposta automatica, i destinatari che inviano la parola chiave corrispondente vengono automaticamente rimossi dalla quarantena.

I destinatari sono elencati nella tabella **[!UICONTROL Non deliverables and addresses]** disponibile dal menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** .

* Per inviare la stessa risposta indipendentemente dal codice breve, lasciare vuota la colonna **[!UICONTROL Short code]**.
* Per inviare la stessa risposta indipendentemente dalla parola chiave, lasciare vuota la colonna **[!UICONTROL Keyword]**.
* Per eseguire un’azione senza inviare una risposta, lascia vuota la colonna **[!UICONTROL Response]** . Ad esempio, questo consente di rimuovere dalla quarantena un utente che risponde con un messaggio diverso da &quot;STOP&quot;.

Se si dispone di più account esterni utilizzando il connettore SMPP generico esteso con lo stesso account provider, potrebbe verificarsi il seguente problema: quando invii una risposta a un codice breve, potrebbe essere ricevuta su una qualsiasi delle tue connessioni account esterne. Di conseguenza, la risposta automatica inviata non poteva essere il messaggio previsto.
Per evitare questo problema, applica una delle soluzioni seguenti, a seconda del provider in uso:

* Crea un account provider per ogni account esterno.
* Utilizza il campo **[!UICONTROL System type]** della scheda **[!UICONTROL Mobile]** > **[!UICONTROL Connection settings]** per distinguere ogni codice breve. Chiedi al tuo provider un valore diverso per ogni account.

   ![](assets/extended_smpp_system-type.png)

I passaggi per la configurazione di un account esterno utilizzando il connettore SMPP generico esteso sono descritti in dettaglio nella sezione [Creazione di un account esterno SMPP](../../delivery/using/sms-channel.md#creating-an-smpp-external-account) .

### Modifica del modello di consegna {#changing-the-delivery-template}

Adobe Campaign fornisce un modello per la consegna a dispositivi mobili. Questo modello è disponibile nel nodo **[!UICONTROL Resources > Templates > Delivery templates]** . Per ulteriori informazioni, consulta la sezione [Informazioni sui modelli](../../delivery/using/about-templates.md) .

Per inviare tramite canale SMS, devi creare un modello in cui viene fatto riferimento al connettore del canale.

Per mantenere il modello di consegna nativo, ti consigliamo di duplicarlo e configurarlo.

Nell’esempio seguente, creiamo un modello per inviare messaggi tramite l’account SMPP abilitato in precedenza. Per eseguire questa operazione:

1. Passa al nodo **[!UICONTROL Delivery templates]** .
1. Fai clic con il pulsante destro del mouse sul modello **[!UICONTROL Send to mobiles]** e seleziona **[!UICONTROL Duplicate]**.

   ![](assets/s_user_mobile_template_change_01.png)

1. Modifica l’etichetta del modello, ad esempio **Inviato a dispositivi mobili (SMPP)**.

   ![](assets/s_user_mobile_template_change_02.png)

1. Fai clic su **[!UICONTROL Properties]**.
1. Nella scheda **[!UICONTROL General]** , seleziona una modalità di indirizzamento corrispondente all’account esterno creato nei passaggi precedenti.

   ![](assets/s_user_mobile_template_change_03.png)

1. Fai clic su **[!UICONTROL Save]** per creare il modello.

   ![](assets/s_user_mobile_template_list.png)

Ora disponi di un account esterno e di un modello di consegna che ti consente di inviare tramite SMS.

## Creazione di una consegna SMS {#creating-a-sms-delivery}

### Selezione del canale di consegna {#selecting-the-delivery-channel}

Per creare una nuova consegna SMS, segui i passaggi seguenti:

>[!NOTE]
>
>I concetti globali sulla creazione della consegna sono descritti in [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

1. Crea una nuova consegna, ad esempio dal dashboard Consegna .
1. Seleziona il modello di consegna **Inviato a dispositivi mobili (SMPP)** creato in precedenza. Per ulteriori informazioni, consulta la sezione [Modifica del modello di consegna](#changing-the-delivery-template) .

   ![](assets/s_user_mobile_wizard.png)

1. Identifica la consegna con un’etichetta, un codice e una descrizione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Fai clic su **[!UICONTROL Continue]** per confermare queste informazioni e visualizzare la finestra di configurazione del messaggio.

## Definizione del contenuto SMS {#defining-the-sms-content}

Per creare il contenuto dell’SMS, segui i passaggi seguenti:

1. Immetti il contenuto del messaggio nella sezione **[!UICONTROL Text content]** della procedura guidata. I pulsanti della barra degli strumenti consentono di importare, salvare o cercare contenuti. L’ultimo pulsante viene utilizzato per inserire campi di personalizzazione.

   ![](assets/s_ncs_user_wizard_sms01_138.png)

   L’utilizzo dei campi di personalizzazione è presentato nella sezione [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md) .

1. Fai clic su **[!UICONTROL Preview]** nella parte inferiore della pagina per visualizzare il rendering del messaggio con la relativa personalizzazione. Per avviare l’anteprima, seleziona un destinatario utilizzando il pulsante **[!UICONTROL Test personalization]** nella barra degli strumenti. Puoi selezionare un destinatario dalle destinazioni definite o scegliere un altro destinatario.

   ![](assets/s_ncs_user_wizard_sms01_139.png)

   Puoi approvare il messaggio SMS. Puoi anche visualizzare il contenuto dell’SMS sullo schermo del telefono cellulare visualizzato a destra dell’editor dei contenuti. Fai clic sulla schermata e utilizza il mouse per scorrere il contenuto.

   ![](assets/s_ncs_user_wizard_sms01_140.png)

1. Fai clic sul collegamento **[!UICONTROL Data loaded]** per visualizzare le informazioni relative al destinatario.

   ![](assets/s_user_mobile_wizard_sms_02.png)

   >[!NOTE]
   >
   >I messaggi SMS sono limitati a una lunghezza di 160 caratteri se si utilizza la tabella codici Latin-1 (ISO-8859-1). Se il messaggio è scritto in Unicode, non deve superare i 70 caratteri. Alcuni caratteri speciali possono influenzare la lunghezza del messaggio. Per ulteriori informazioni sulla lunghezza del messaggio, consulta la sezione [Informazioni sulla traslitterazione dei caratteri](#about-character-transliteration) .
   >
   >Quando sono presenti campi di personalizzazione o campi di contenuto condizionale, le dimensioni del messaggio variano da un destinatario all’altro. La lunghezza del messaggio deve essere valutata al momento dell’esecuzione della personalizzazione.
   >
   >Quando avvii l’analisi, viene controllata la lunghezza dei messaggi e viene visualizzato un avviso in caso di overflow.

1. Se utilizzi il connettore NetSize o un connettore SMPP, puoi personalizzare il nome del mittente della consegna. Per ulteriori informazioni, consulta la sezione [Parametri avanzati](#advanced-parameters) .

## Selezione della popolazione target {#selecting-the-target-population}

Il processo dettagliato durante la selezione della popolazione target di una consegna è presentato in [questa sezione](../../delivery/using/steps-defining-the-target-population.md).

Per ulteriori informazioni sull’utilizzo dei campi di personalizzazione, consulta [Informazioni sulla personalizzazione](../../delivery/using/about-personalization.md).

Per ulteriori informazioni sull&#39;inclusione di un elenco di seed, consulta [Informazioni sugli indirizzi di seed](../../delivery/using/about-seed-addresses.md).

## Invio di messaggi SMS {#sending-sms-messages}

Per approvare il messaggio e inviarlo ai destinatari della consegna da creare, fai clic su **[!UICONTROL Send]**.

Il processo dettagliato di convalida e invio di una consegna è presentato nelle sezioni seguenti:

* [Convalida della consegna](../../delivery/using/steps-validating-the-delivery.md)
* [Invio della consegna](../../delivery/using/steps-sending-the-delivery.md)

### Parametri avanzati {#advanced-parameters}

Il pulsante **[!UICONTROL Properties]** consente di accedere al parametro di consegna avanzato. I parametri specifici delle consegne SMS si trovano nella sezione **[!UICONTROL SMS parameters]** della scheda **[!UICONTROL Delivery]** .

Sono disponibili le seguenti opzioni:

* **Indirizzo** mittente: ti consente di personalizzare il nome del mittente della consegna utilizzando una stringa di caratteri alfanumerici limitati a undici caratteri. Il campo non deve essere costituito esclusivamente da cifre. È possibile definire una condizione per visualizzare, ad esempio, nomi diversi in base al codice dell’area del destinatario:

   ```
   <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
   ```

   >[!IMPORTANT]
   >
   >Controlla le leggi del tuo paese riguardo alla modifica dei nomi dei mittenti. È inoltre necessario verificare con l’operatore se offre questa funzionalità.

* **Modalità** di trasmissione: trasmissione di messaggi tramite SMS.
* **Priorità**: livello di importanza assegnato a un messaggio. **[!UICONTROL Normal]** la priorità è selezionata per impostazione predefinita. Chiedi al tuo provider di servizi il costo degli SMS inviati con priorità **[!UICONTROL High]** .
* **Tipo di applicazione**: scegli l’applicazione che desideri assegnare alla consegna SMS. L’opzione **[!UICONTROL Direct Marketing]** è selezionata per impostazione predefinita ed è la più comune utilizzata.

**Parametri specifici del connettore NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Utilizza diversi SMS per un singolo messaggio**: questo ti consente di inviare un messaggio lungo più di 160 caratteri tramite diversi messaggi SMS.

**Parametri specifici di un connettore SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Numero massimo di SMS per messaggio**: questa opzione ti consente di impostare il numero di SMS da utilizzare per inviare un messaggio. Se il numero è impostato su 0, puoi utilizzare un SMS per inviare il messaggio. Se il numero di SMS è impostato ad esempio su 1 o 2 e il messaggio supera questa soglia, non verrà inviato.

## Monitoraggio e tracciamento delle consegne SMS {#monitoring-and-tracking-sms-deliveries}

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [Monitoraggio di una consegna](../../delivery/using/about-delivery-monitoring.md)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Informazioni sul tracking dei messaggi](../../delivery/using/about-message-tracking.md)

## Elaborazione dei messaggi in entrata {#processing-inbound-messages}

Il modulo **nlserver sms** invia una query al router SMS a intervalli regolari. Questo consente ad Adobe Campaign di tenere traccia dell’avanzamento delle consegne e di gestire i rapporti sullo stato e le richieste di annullamento dell’abbonamento ai destinatari.

* **Rapporti** di stato: visualizza i registri di consegna per controllare lo stato dei messaggi.

   >[!NOTE]
   >
   >Ogni SMS inviato è collegato a un account esterno la sua chiave primaria. In questo modo:
   >
   > * I rapporti di stato da un account SMS esterno eliminato non vengono elaborati correttamente.
   > * Un account SMS può essere collegato solo a un singolo account esterno per garantire che i rapporti di stato siano attribuiti all’account corretto


* **Annullamento dell’abbonamento**: i destinatari che desiderano interrompere la ricezione delle consegne SMS possono restituire un messaggio contenente la parola STOP. Se il provider lo consente in base ai termini del contratto, puoi recuperare i messaggi tramite l’attività del flusso di lavoro **Inbound SMS** e quindi creare una query per abilitare l’opzione **No contact this recipient** per i destinatari interessati.

   Fai riferimento alla guida [Flussi di lavoro](../../workflow/using/architecture.md) .

## Schema InSMS {#insms-schema}

Lo schema InSMS contiene informazioni relative agli SMS in arrivo. Una descrizione di questi campi è disponibile tramite l’attributo desc .

* **messaggio**: contenuto dell’SMS ricevuto.
* **origine**: numero di cellulare all’origine del messaggio.
* **providerId**: identificatore del messaggio restituito da SMSC (message center).
* **creato**: il messaggio data in arrivo è stato inserito in Adobe Campaign.
* **extAccount**: Account esterno Adobe Campaign.

   >[!IMPORTANT]
   >
   >I campi seguenti sono specifici di NetSize.
   >
   >Se l&#39;operatore in uso non è NetSize, questi campi sono considerati vuoti.

* **alias**: alias del messaggio in arrivo.
* **separatore**: separatore tra l’alias e il corpo del messaggio.
* **messageDate**: data del messaggio fornita dall’operatore.
* **receivalDate**: messaggio data dall&#39;operatore ricevuto da SMSC (message center).
* **deliveryDate**: messaggio data inviato da SMSC (message center).
* **largeAccount**: codice dell’account cliente collegato all’SMS in entrata.
* **countryCode**: codice del paese dell&#39;operatore.
* **operatorCode**: codice di rete dell&#39;operatore.
* **linkedSmsId**: Identificatore Adobe Campaign (broadlogId) collegato all’SMS in uscita, dove questo SMS è la risposta.

## Gestione delle risposte automatiche (regolamento americano) {#managing-automatic-replies--american-regulation-}

Quando gli abbonati rispondono a un messaggio SMS loro inviato tramite Adobe Campaign e utilizzano una parola chiave come STOP, HELP o YES, è necessario, nel mercato statunitense, configurare messaggi che vengono restituiti automaticamente.

Ad esempio, se i destinatari inviano la parola chiave STOP, ricevono automaticamente un messaggio di conferma in cui si informa che l’iscrizione è stata annullata.

Il nome del mittente di questo tipo di messaggio è un codice breve solitamente utilizzato per inviare consegne.

>[!IMPORTANT]
>
>La seguente procedura dettagliata è valida solo per i connettori SMPP, ad eccezione del connettore SMPP generico esteso. Per ulteriori informazioni, consulta la sezione [Creazione di un account esterno SMPP](#creating-an-smpp-external-account) .
>
>Essa fa parte del processo di certificazione effettuato dagli operatori americani per le campagne di marketing negli Stati Uniti. Queste risposte ai messaggi SMS degli abbonati contenenti la parola chiave devono essere rimandate all’utente immediatamente dopo aver ricevuto un messaggio da loro.

1. Crea questo tipo di file XML:

   ```
   <autoreply>
     <shortcode name="12345">
       <reply keyword="STOP" text="You will not receive SMS anymore" />
       <reply keyword="HELP" text="Powered by Adobe Campaign" />
     </shortcode>
     <shortcode name="43115">
       <reply keyword="STOP" text="Vous ne recevrez plus de SMS" />
       <reply keyword="HELP" text="Service rendu par Adobe Campaign" />
     </shortcode>
     <shortcode name="*">
       <reply keyword="ADOBE" text="This text is replied when you send ADOBE to any short code" />
     </shortcode>
   </autoreply>
   ```

1. Per l’attributo **name** del tag **`<shortcode>`** , specifica il codice breve che verrà visualizzato al posto del nome del mittente del messaggio.

   In ciascun tag **`<reply>`**, inserisci l&#39;attributo **keyword** con una parola chiave e l&#39;attributo **text** con il messaggio che desideri inviare per questa parola chiave.

   >[!NOTE]
   >
   >Ogni parola chiave deve essere scritta in lettere maiuscole.

   Se desideri inviare lo stesso messaggio per più parole chiave, duplica la riga corrispondente.

   Ad esempio:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Una volta completato, salva questo file con il nome **smsAutoReply.xml**.

   Nota che il nome del file è sensibile a maiuscole e minuscole in Linux.

1. Copia questo file nella directory **conf** in Adobe Campaign, nella stessa posizione del server Web.

>[!IMPORTANT]
>
>Questo tipo di messaggi automatici non mantiene una cronologia. Pertanto non vengono visualizzate nel [dashboard di consegna](../../delivery/using/delivery-dashboard.md).
>
>Questi messaggi non sono considerati parte delle [regole di pressione commerciale](../../campaign/using/pressure-rules.md).
