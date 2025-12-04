---
product: campaign
title: Inviare, monitorare e tenere traccia degli SMS
description: Scopri come inviare, monitorare e tenere traccia degli SMS in Campaign
feature: SMS
role: User
exl-id: 442672ee-5037-49b7-a06f-3a99920ce2b6
source-git-commit: 62ab16b206563aa25b8943e606d03a3184eb00db
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 1%

---

# Configurazione aggiuntiva{#sms-properties}

<!--
## Send SMS messages {#sending-sms-messages}

To approve your message and send it to the recipients of the delivery being created, click **[!UICONTROL Send]**.

The detailed process when validating and sending a delivery is presented in the sections below:

* [Validate the delivery](steps-validating-the-delivery.md)
* [Send the delivery](steps-sending-the-delivery.md)
-->

## Parametri avanzati {#advanced-parameters}

Il pulsante **[!UICONTROL Properties]** consente di accedere al parametro di consegna avanzata. I parametri specifici per le consegne SMS si trovano nella sezione **[!UICONTROL SMS parameters]** della scheda **[!UICONTROL Delivery]**.

Sono disponibili le seguenti opzioni:

* **Indirizzo mittente**: consente di personalizzare il nome del mittente della consegna utilizzando una stringa di caratteri alfanumerici limitata a undici caratteri. Il campo non deve essere costituito esclusivamente da cifre. È possibile definire una condizione da visualizzare, ad esempio nomi diversi in base all’indicativo di località del destinatario:

  ```
  <% if( String(recipient.mobilePhone).indexOf("+1") == 0){ %>NeoShopUS<%} else {%>NeoShopWorld<%}%>
  ```

  >[!IMPORTANT]
  >
  >Controlla la legge del tuo paese relativa alla modifica dei nomi dei mittenti. Dovresti anche verificare con l’operatore se offre questa funzionalità.

* **Modalità di trasmissione**: trasmissione di messaggi tramite SMS.
* **Priorità**: livello di importanza assegnato a un messaggio. Priorità **[!UICONTROL Normal]** selezionata per impostazione predefinita. Chiedere al provider di servizi informazioni sul costo degli SMS inviati con priorità **[!UICONTROL High]**.
* **Tipo di applicazione**: scegli l&#39;applicazione da assegnare alla consegna SMS. L&#39;opzione **[!UICONTROL Direct Marketing]** è selezionata per impostazione predefinita ed è la più comune utilizzata.

**Parametri specifici del connettore NetSize**

![](assets/s_user_mobile_sms_adv_netsize.png)

* **Utilizza diversi SMS per un singolo messaggio**: questo ti consente di inviare un messaggio lungo più di 160 caratteri tramite diversi messaggi SMS.

**Parametri specifici di un connettore SMPP**

![](assets/s_user_mobile_sms_adv_smpp.png)

* **Numero massimo di SMS per messaggio**: questa opzione consente di impostare il numero di SMS da utilizzare per inviare un messaggio. Se il numero è impostato su 0, puoi utilizzare un SMS per recapitare il messaggio. Se ad esempio il numero di SMS è impostato su 1 o 2 e il messaggio supera questa soglia, non verrà inviato.

<!--
## Monitor and track SMS {#monitoring-and-tracking-sms-deliveries}

After sending messages, you can monitor and track your deliveries. For more on this, refer to these sections:

* [Monitor a delivery](about-delivery-monitoring.md)
* [Understand delivery failures](delivery-failures-quarantine.md)
* [About message tracking](about-message-tracking.md)
-->

## Elabora messaggi in entrata {#processing-inbound-messages}

Il modulo **nlserver sms** esegue query sul router SMS a intervalli regolari. Questo consente ad Adobe Campaign di tenere traccia dell’avanzamento delle consegne e di gestire le relazioni sullo stato e le richieste di annullamento dell’abbonamento dei destinatari.

* **Relazioni sullo stato**: visualizza i registri di consegna per controllare lo stato dei messaggi.

  >[!NOTE]
  >
  >Ogni SMS inviato è collegato a un account esterno che ne rappresenta la chiave primaria. In questo modo:
  >
  > * Le relazioni sullo stato da un account SMS esterno eliminato non vengono elaborate correttamente.
  > * Un account SMS può essere collegato solo a un singolo account esterno per garantire che le relazioni sullo stato siano attribuite all’account corretto

* **Annullamento dell&#39;abbonamento**: i destinatari che desiderano interrompere la ricezione delle consegne SMS possono restituire un messaggio contenente la parola STOP. Se il provider lo consente in base ai termini del contratto, è possibile recuperare messaggi tramite l&#39;attività del flusso di lavoro **SMS in entrata** e quindi creare una query per abilitare l&#39;opzione **Non contattare più questo destinatario** per i destinatari interessati.

## Schema InSMS {#insms-schema}

Lo schema InSMS contiene informazioni relative agli SMS in arrivo. Una descrizione di questi campi è disponibile tramite l&#39;attributo desc.

* **messaggio**: contenuto dell&#39;SMS ricevuto.
* **origine**: numero di cellulare all&#39;origine del messaggio.
* **providerId**: identificatore del messaggio restituito da SMSC (centro messaggi).
* **created**: data di inserimento del messaggio in arrivo in Adobe Campaign.
* **extAccount**: account esterno Adobe Campaign.

  >[!IMPORTANT]
  >
  >I campi seguenti sono specifici di NetSize.
  >
  >Se l&#39;operatore in uso non è NetSize, questi campi vengono considerati vuoti.

* **alias**: alias del messaggio in arrivo.
* **separatore**: separatore tra l&#39;alias e il corpo del messaggio.
* **messageDate**: data del messaggio fornita dall&#39;operatore.
* **receivalDate**: il messaggio della data dall&#39;operatore è stato ricevuto da SMSC (centro messaggi).
* **deliveryDate**: messaggio di data inviato da SMSC (centro messaggi).
* **largeAccount**: codice account cliente collegato agli SMS in arrivo.
* **countryCode**: codice paese operatore.
* **operatorCode**: codice di rete operatore.
* **linkedSmsId**: identificatore Adobe Campaign (broadlogId) collegato all&#39;SMS in uscita, dove questo SMS è la risposta.

## Gestisci risposte automatiche (regolamento americano) {#managing-automatic-replies--american-regulation-}

Quando gli abbonati rispondono a un messaggio SMS che è stato loro inviato tramite Adobe Campaign e utilizzano una parola chiave come STOP, HELP o YES, è necessario, nel mercato statunitense, configurare i messaggi che vengono restituiti automaticamente.

Ad esempio, se i destinatari inviano la parola chiave STOP, ricevono automaticamente un messaggio di conferma che informa che l’iscrizione è stata annullata.

Il nome del mittente per questo tipo di messaggio è un codice breve utilizzato in genere per inviare consegne.

>[!IMPORTANT]
>
>La procedura dettagliata seguente è valida solo per i connettori SMPP, ad eccezione del connettore SMPP generico esteso. Per ulteriori informazioni, consulta la sezione [Creare un account esterno SMPP](sms-set-up.md#creating-an-smpp-external-account).
>
>Esso fa parte del processo di certificazione svolto dagli operatori americani per campagne di marketing negli Stati Uniti. Queste risposte ai messaggi SMS dell’abbonato contenenti la parola chiave devono essere rimandate all’abbonato immediatamente dopo aver ricevuto un messaggio da parte loro.

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

1. Per l&#39;attributo **name** del tag **`<shortcode>`**, specificare il codice breve che verrà visualizzato al posto del nome del mittente del messaggio.

   In ogni tag **`<reply>`** immettere l&#39;attributo **keyword** con una parola chiave e l&#39;attributo **text** con il messaggio che si desidera inviare per questa parola chiave.

   >[!NOTE]
   >
   >Ogni parola chiave deve essere scritta in lettere maiuscole.

   Se desideri inviare lo stesso messaggio per più parole chiave, duplica la riga corrispondente.

   Ad esempio:

   ```
   <reply keyword="STOP" text="You will not receive SMS anymore" />
   <reply keyword="QUIT" text="You will not receive SMS anymore" />
   ```

1. Al termine, salvare il file con il nome **smsAutoReply.xml**.

   In Linux, il nome del file distingue tra maiuscole e minuscole.

1. Copiare il file nella directory **conf** di Adobe Campaign, nello stesso punto del server Web.

>[!IMPORTANT]
>
>Questi tipi di messaggi automatici non conservano una cronologia. Pertanto, non vengono visualizzati nel dashboard di consegna. [Ulteriori informazioni](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.
>
>Tali messaggi non sono presi in considerazione nelle norme sulla pressione commerciale. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/pressure-rules.html?lang=it){target="_blank"}.
