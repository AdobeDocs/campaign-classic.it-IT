---
solution: Campaign Classic
product: campaign
title: Architettura dei messaggi transazionali Adobe Campaign Classic
description: Questa sezione descrive l'architettura dei messaggi transazionali Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 1%

---


# Architettura della messaggistica transazionale{#transactional-messaging-architecture}

## Informazioni sulle istanze di esecuzione e controllo {#about-execution-and-control-instances}

In  Adobe Campaign, le funzionalità di messaggistica transazionali (note anche come Message Center) sono state progettate per supportare la scalabilità e fornire un servizio 24/7. Si compone di diversi casi:

* un&#39;istanza di controllo in cui vengono creati i modelli di messaggio,
* una o più istanze di esecuzione che ricevono eventi e inviano messaggi.

Per utilizzare queste funzionalità,  gli utenti Adobe Campaign accedono all&#39;istanza di controllo per creare modelli di messaggi transazionali, generare l&#39;anteprima dei messaggi utilizzando un elenco di elementi iniziali, visualizzare i rapporti e monitorare le istanze di esecuzione.

Le istanze di esecuzione ricevono gli eventi, li collegano a modelli di messaggi transazionali e inviano un messaggio personalizzato a ciascun destinatario.

![](assets/messagecenter_diagram.png)

## Supporto di più istanze di controllo {#supporting-several-control-instances}

>[!IMPORTANT]
>
>La condivisione di un cluster di esecuzione con più istanze di controllo è supportata solo per gli ambienti locali.

È possibile condividere un cluster di esecuzione tra diverse istanze di controllo. Ad esempio, se gestisci diversi store specializzati, puoi configurare un’istanza di controllo per marchio e collegarli tutti allo stesso cluster di esecuzione.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione necessaria, vedere [Uso di più istanze](../../message-center/using/creating-a-shared-connection.md#using-several-control-instances)di controllo.

## Installazione delle istanze {#installing-instances}

Durante l&#39;installazione dei pacchetti di messaggi transazionali è necessario prendere diverse precauzioni.  Adobe consiglia di lavorare in un ambiente di test prima di entrare in produzione. È inoltre necessario disporre di una licenza Adobe Campaign  compatibile. Per ulteriori informazioni, contattate il vostro responsabile commerciale  Adobe.

>[!IMPORTANT]
>
>L&#39;istanza di controllo e le istanze di esecuzione devono essere installate su computer diversi. Non possono condividere la stessa istanza Campaign.

Se devi usare più canali, devi installare e configurare i pacchetti correlati prima di installare i pacchetti di messaggi transazionali. Fare riferimento a [Aggiunta di un canale](#adding-a-delivery-channel)di consegna.

* Per installare l&#39;istanza di controllo sul computer, selezionare il **[!UICONTROL Transactional message control]** modulo.

   ![](assets/messagecenter_install_controlinstance_001.png)

* Per installare l&#39;istanza di esecuzione sul computer, selezionare il **[!UICONTROL Transactional message execution]** modulo.

   ![](assets/messagecenter_install_executioninstance_001.png)

## Aggiunta di un canale di consegna {#adding-a-delivery-channel}

Aggiunta di un canale di consegna (canale mobile, canale app mobile, ecc.) deve essere eseguito prima di installare il pacchetto di messaggi transazionali. Se hai avviato un progetto di messaggistica transazionale sul canale e-mail e poi hai deciso durante il progetto di aggiungere un nuovo canale, devi seguire la procedura seguente:

1. Installa il canale necessario, ad esempio il canale **** Mobile, utilizzando la procedura guidata di importazione dei pacchetti ( **[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]** ).
1. Effettuate un&#39;importazione di file ( **[!UICONTROL Tools > Advanced > Import package... > File]** ) e selezionate il file ****`[Your language]`**datakitnmspackagemessageCenter.xml** .
1. In **[!UICONTROL XML content of the data to import]** , mantenere solo il modello di consegna che corrisponde al canale aggiunto. Ad esempio, se hai aggiunto il canale **** Mobile, tieni solo l&#39;elemento **entities** che corrisponde al **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Se hai aggiunto **Mobile App Channel**, mantieni solo il messaggio **transazionale** iOS (iosTriggerMessage) e il messaggio **transazionale** Android (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

<!--## Transactional messages and inbound Interaction {#transactional-messages-and-inbound-interaction}

When combined with the Inbound Interaction module, transactional messaging enables you to insert a marketing offer dedicated to the recipient into the message.

>[!NOTE]
>
>The Interaction module is detailed in [Interaction](../../interaction/using/interaction-and-offer-management.md).

To use transactional messaging with Interaction, you need to apply the following configurations:

* Install the **Interaction** package onto the control instance and configure your offer catalog.

  >[!IMPORTANT]
  >
  >Do not replicate the offers onto the execution instances.

* The event must include an identifier linked to the recipients, for personalizing offers. The **@externalId** attribute must contain the value of this identifier. **Interaction** is configured by default to identify the recipient of the primary key:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="1242"> 
  ```

  You can configure **Interaction** so that identification takes place in the field of your choice, for example on the email address:

  ```
  <rtEvent type="order_confirmation" email="john.doe@adobe.com" externalId="john.doe@yahoo.com"> 
  ```

Create your delivery templates the way you would for an email campaign:

* Add the offer to your transactional message template.
* Check the preview, send a proof and publish the template.

You also have to enable the unitary mode on your offer spaces. For more on this, refer to [this section](../../interaction/using/creating-offer-spaces.md).-->

## Messaggi transazionali e notifiche push {#transactional-messaging-and-push-notifications}

Se combinato con il modulo del canale delle app mobili, i messaggi transazionali consentono di inviare messaggi transazionali tramite notifiche su dispositivi mobili.

>[!NOTE]
>
>Il canale dell&#39;app mobile è dettagliato in [questa sezione](../../delivery/using/about-mobile-app-channel.md).

Per utilizzare i moduli di messaggi transazionali con Mobile App Channel, è necessario applicare le seguenti configurazioni:

1. Installa il pacchetto **Mobile App Channel** nelle istanze di controllo ed esecuzione.
1. Replicare il tipo di applicazione **** Mobile  servizio Adobe Campaign e le applicazioni mobili che contiene sulle istanze di esecuzione.

L&#39;evento deve contenere i seguenti elementi:

* L’ID del dispositivo mobile (**registrationId** per Android e **deviceToken** per iOS). Questo ID rappresenta l&#39;&quot;indirizzo&quot; a cui verrà inviata la notifica.
* Il collegamento all&#39;applicazione mobile o alla chiave di integrazione (**uuid**) che consente di recuperare le informazioni di connessione specifiche per l&#39;applicazione.
* Canale a cui verrà inviata la notifica (**DesiderateChannel**): 41 per iOS e 42 per Android
* Tutti i dati utili per la personalizzazione

Di seguito è riportato un esempio di evento che contiene le informazioni seguenti:

```
<SOAP-ENV:Envelope xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
   <SOAP-ENV:Body>
     <urn:PushEvent>
         <urn:sessiontoken>mc/</urn:sessiontoken>
         <urn:domEvent>

              <rtEvent wishedChannel="41" type="DELIVERY" registrationToken="2cefnefzef758398493srefzefkzq483974">
                <mobileApp _operation=”none” uuid="com.adobe.NeoMiles"/>
                <ctx>
                    <deliveryTime>1:30 PM</deliveryTime>
                    <url>http://www.adobe.com</url>
                </ctx>
              </rtEvent>

         </urn:domEvent>
     </urn:PushEvent>           
   </SOAP-ENV:Body>
</SOAP-ENV:Envelope>
```

>[!NOTE]
>
>La creazione di modelli di messaggio rimane la stessa.

## Messaggi transazionali e LINE {#transactional-messaging-and-line}

Insieme al canale LINE, i messaggi transazionali consentono di inviare messaggi in tempo reale sull&#39;app LINE installata nei dispositivi mobili consumer. Viene utilizzato per inviare il messaggio di benvenuto quando un utente LINE aggiunge la pagina del marchio.

Per utilizzare il modulo di messaggi transazionali con LINE, sono necessari i seguenti elementi per la configurazione nell&#39;istanza di **marketing** e nell&#39;istanza di **esecuzione** :

* Installate il **[!UICONTROL LINE Connect]** pacchetto su entrambe le istanze.
* Installate il **[!UICONTROL Transactional message control]** pacchetto nell&#39;istanza di marketing e il **[!UICONTROL Transactional message execution]** pacchetto nell&#39;istanza di esecuzione.
* Creare un account **e un** servizio **** esterni LINE su entrambe le istanze con nomi identici per la sincronizzazione. Per ulteriori informazioni su come creare un account e un servizio LINE esterno, fare riferimento a questa [pagina](../../delivery/using/line-channel.md#creating-a-line-account-and-an-external-account-).

Quindi, da **[!UICONTROL Explorer]** , in **[!UICONTROL Platform]** > **[!UICONTROL External account]** , è necessario configurare account esterni diversi per entrambe le istanze:

1. Create un account **[!UICONTROL External database]** esterno nell’istanza di **esecuzione** con la seguente configurazione:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : assegnate un nome all’account esterno come necessario.
   * **[!UICONTROL Type]** : selezionate **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]** deve essere selezionata.

   Dalla **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL Type]** : selezionate il server del database, ad esempio PostgresSQL.
   * **[!UICONTROL Server]** : immettete l’URL del server del database.
   * **[!UICONTROL Account]** : inserite l&#39;account del database.

      >[!NOTE]
      >
      >L&#39;utente del database deve disporre dei diritti di lettura sulle tabelle seguenti per la connessione FDA: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRtEvent, NmsBatchEvent, NmsBroadLogMsg NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Password]** : immettete la password per l&#39;account del database.
   * **[!UICONTROL Database]** : immettere il nome del database dell&#39;istanza di esecuzione.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** deve essere selezionata.


1. Crea un **[!UICONTROL External Database]** account nella tua istanza **di marketing** con la seguente configurazione.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : assegnate un nome all’account esterno come necessario.
   * **[!UICONTROL Type]** : selezionate **[!UICONTROL External database]** .
   * La casella attivata deve essere selezionata.

   Dalla **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL Type]** : selezionate **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : immettete l&#39;URL del server della campagna per l&#39;istanza di esecuzione.
   * **[!UICONTROL Account]** : immettete l&#39;account utilizzato per accedere all&#39;istanza di esecuzione.
   * **[!UICONTROL Password]** : immettete la password per l&#39;account utilizzato per accedere all&#39;istanza di esecuzione.
   * **[!UICONTROL Data Source]** : immettete la sintassi seguente **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** .


1. Crea un account **[!UICONTROL Execution instance]** esterno nell’istanza di **marketing** utilizzando la seguente configurazione per creare il flusso di lavoro di sincronizzazione dei dati:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : assegnate un nome all’account esterno come necessario.
   * **[!UICONTROL Type]** : selezionate **[!UICONTROL Execution instance]** .
   * La casella attivata deve essere selezionata.

   Dalla **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL URL]** : immettete l&#39;URL dell&#39;istanza di esecuzione.
   * **[!UICONTROL Account]** : immettete l&#39;account utilizzato per accedere all&#39;istanza di esecuzione.
   * **[!UICONTROL Password]** : immettete la password per l&#39;account utilizzato per accedere all&#39;istanza di esecuzione.

   Dalla **[!UICONTROL Account connection method]** categoria:

   * **[!UICONTROL Method]** : selezionate **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : selezionate il vostro account FDA dall&#39;elenco a discesa.
   * Fai clic sul pulsante **[!UICONTROL Create the archiving workflow]**.
   * Fare clic sul **[!UICONTROL Create data synchronization workflow]** pulsante per creare il flusso di lavoro di sincronizzazione dei dati LINE.



1. Ora puoi iniziare a creare messaggi transazionali. Per ulteriori informazioni, consulta questa [pagina](../../message-center/using/introduction.md).
