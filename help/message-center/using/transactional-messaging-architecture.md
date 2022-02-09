---
product: campaign
title: Architettura della messaggistica transazionale
description: Questa sezione descrive l’architettura dei messaggi transazionali di Adobe Campaign Classic e i canali disponibili per la distribuzione dei messaggi transazionali
exl-id: 0a059397-b037-405b-b9c1-94a4a072674d
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 1%

---

# Architettura della messaggistica transazionale {#transactional-messaging-architecture}

![](../../assets/v7-only.svg)

La messaggistica transazionale si basa su un’architettura specifica, costituita da diverse istanze:

* A **istanza di controllo**, in cui vengono creati i modelli di messaggio.

* Uno o più **istanze di esecuzione**, che ricevono eventi e inviano messaggi.

![](assets/messagecenter_diagram.png)

| Istanza di controllo | Istanza di esecuzione |
|--- |--- |
| Gli utenti di Adobe Campaign accedono all’istanza di controllo per: <ul><li>Creare modelli di messaggi transazionali</li><li>Genera l’anteprima del messaggio utilizzando un elenco di seed</li><li>Visualizzare i rapporti</li><li>Monitorare le istanze di esecuzione</li></ul> | Le istanze di esecuzione sono disponibili qui per: <ul><li>Ricevi eventi</li><li>Collegali a modelli di messaggi transazionali</li><li>Invia un messaggio personalizzato a ciascun destinatario</li></ul> |

## Installare le istanze {#installing-instances}

Ci sono diverse precauzioni da prendere quando installi i pacchetti di messaggi transazionali. Adobe consiglia di lavorare in un ambiente di test prima di passare alla produzione. È inoltre necessario disporre di una licenza Adobe Campaign compatibile. Per ulteriori informazioni, contatta il tuo responsabile dell&#39;account di Adobe.

>[!IMPORTANT]
>
>L&#39;istanza di controllo e le istanze di esecuzione devono essere installate su computer diversi. Non possono condividere la stessa istanza Campaign.

Se devi utilizzare più canali, devi installare e configurare i pacchetti correlati prima di installare i pacchetti di messaggi transazionali. Per ulteriori informazioni, consulta [Aggiungere un canale di consegna](#adding-a-delivery-channel).

## Istanza di controllo {#control-instance}

Per installare l&#39;istanza di controllo sul computer, selezionare la **[!UICONTROL Transactional message control]** tramite **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Per ulteriori informazioni, consulta [Installazione dei pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_controlinstance_001.png)

I passaggi dettagliati per la configurazione dell’istanza di controllo sono descritti in [questa sezione](../../message-center/using/configuring-instances.md#control-instance).

### Supporto di più istanze di controllo {#supporting-several-control-instances}

>[!IMPORTANT]
>
>La condivisione di un cluster di esecuzione con diverse istanze di controllo è supportata solo per gli ambienti on-premise.

È possibile condividere un cluster di esecuzione tra diverse istanze di controllo. Ad esempio, se gestisci diversi archivi specializzati, puoi configurare un’istanza di controllo per marchio e collegarli tutti allo stesso cluster di esecuzione.

![](assets/messagecenter_diagram_2.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione necessaria, consulta [Utilizzare diverse istanze di controllo](../../message-center/using/configuring-instances.md#using-several-control-instances).

## Istanza di esecuzione {#execution-instance}

Per installare un&#39;istanza di esecuzione sul computer, seleziona la **[!UICONTROL Transactional message execution]** tramite **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Per ulteriori informazioni, consulta [Installazione dei pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).

![](assets/messagecenter_install_executioninstance_001.png)

I passaggi dettagliati per la configurazione di un’istanza di esecuzione sono descritti in [questa sezione](../../message-center/using/configuring-instances.md#execution-instance).

## Canali di consegna disponibili

Il canale e-mail è disponibile per impostazione predefinita. Per inviare messaggi transazionali su più canali, puoi aggiungere altri canali (canale mobile, canale app mobile, ecc.).

>[!IMPORTANT]
>
>Aggiunta di un canale di consegna (canale mobile, canale app mobile, ecc.) deve essere eseguito prima di installare il pacchetto di messaggi transazionali.

### Aggiungere un canale di consegna {#adding-a-delivery-channel}

Adobe consiglia di **aggiungi sempre il pacchetto del canale di consegna prima di installare il pacchetto del messaggio transazionale**.

Tuttavia, se hai avviato un progetto di messaggistica transazionale sul canale e-mail e poi decidi durante il progetto di aggiungere un nuovo canale, puoi seguire i passaggi seguenti.

>[!NOTE]
>
>Questa procedura si applica solo ai clienti che utilizzano un server Windows NLS installato sullo stesso computer in cui lavorano.

1. Installa il canale necessario, ad esempio il **Canale mobile**, utilizzando la procedura guidata di importazione del pacchetto (**[!UICONTROL Tools > Advanced > Import package... > Adobe Campaign Package]**).
1. Esegui un&#39;importazione di file (**[!UICONTROL Tools > Advanced > Import package... > File]**) e seleziona la **datakitnms **`[Your language]`**packagemessageCenter.xml** file.
1. In **[!UICONTROL XML content of the data to import]**, mantieni solo il modello di consegna che corrisponde al canale aggiunto. Ad esempio, se hai aggiunto il **Canale mobile**, mantieni solo **entità** che corrisponde a **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Se hai aggiunto il **Canale app mobile**, mantieni solo **Messaggio sulle transazioni iOS** (iosTriggerMessage) e **Messaggio sulle transazioni Android** (androidTriggerMessage).

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

### Notifiche push transazionali {#transactional-messaging-and-push-notifications}

Se combinato con il modulo del canale dell’app mobile, la messaggistica transazionale consente di inviare messaggi transazionali tramite notifiche su dispositivi mobili.

>[!NOTE]
>
>Il canale app mobile è descritto in [questa sezione](../../delivery/using/about-mobile-app-channel.md).

Per utilizzare moduli di messaggi transazionali con Mobile App Channel, devi applicare le seguenti configurazioni:

1. Installa il **Canale app mobile** creare pacchetti nelle istanze di controllo ed esecuzione.
1. Replicare il **App mobile** digita il servizio Adobe Campaign e le applicazioni mobili in esso contenute nelle istanze di esecuzione.

L&#39;evento deve contenere i seguenti elementi:

* L&#39;ID del dispositivo mobile (**registrationId** per Android e **deviceToken** per iOS). Questo ID rappresenta l&#39;&quot;indirizzo&quot; a cui verrà inviata la notifica.
* Il collegamento all’app mobile o alla chiave di integrazione (**uuid**) che consente di recuperare le informazioni di connessione specifiche dell’applicazione.
* Il canale a cui verrà inviata la notifica (**wishChannel**): 41 per iOS e 42 per Android
* Tutti i dati utili per la personalizzazione

Di seguito è riportato un esempio di evento contenente queste informazioni:

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
>La creazione dei modelli di messaggio rimane la stessa.

### Messaggistica transazionale e LINE {#transactional-messaging-and-line}

Insieme al canale LINE, i messaggi transazionali ti consentono di inviare messaggi in tempo reale sull’app LINE installata su dispositivi mobili consumer. Viene utilizzato per inviare il messaggio di benvenuto quando un utente LINE aggiunge la pagina del brand.

Per utilizzare il modulo di messaggio transazionale con LINE, sono necessari i seguenti elementi per la configurazione sul **marketing** istanza e **esecuzione** istanza:

* Installa il **[!UICONTROL LINE Connect]** su entrambe le istanze.
* Installa il **[!UICONTROL Transactional message control]** pacchetto sulla tua istanza di marketing e **[!UICONTROL Transactional message execution]** pacchetto sull&#39;istanza di esecuzione.
* Creare una riga **account esterno** e **servizio** su entrambe le istanze con denominazione identica per le quali devono essere sincronizzate. Per ulteriori informazioni su come creare un account e un servizio esterni LINE, consulta [questa sezione](../../delivery/using/line-channel.md#setting-up-line-channel).

Quindi, dal **[!UICONTROL Explorer]** , in **[!UICONTROL Platform]** > **[!UICONTROL External account]** , è necessario configurare account esterni diversi per entrambe le istanze:

1. Crea un **[!UICONTROL External database]** account esterno nel tuo **esecuzione** istanza con la seguente configurazione:

   ![](assets/line_config_mc.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : denomina il tuo account esterno come necessario.
   * **[!UICONTROL Type]** : select **[!UICONTROL External database]** .
   * **[!UICONTROL Enabled]** deve essere selezionata.

   Da **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL Type]** : selezionare il server di database, ad esempio PostgresSQL.
   * **[!UICONTROL Server]** : immetti l&#39;URL del server di database.
   * **[!UICONTROL Account]** : immettere l&#39;account del database.

      >[!NOTE]
      >
      >L&#39;utente del database deve disporre di diritti di lettura sulle tabelle seguenti per la connessione FDA: XtkOption, NmsVisitor, NmsVisitorSub, NmsService, NmsBroadLogRtEvent, NmsBroadLogBatchEvent, NmsTrackingLogRtEvent, NmsTrackingLogBatchEvent, NmsRtEvent, NmsBatchEvent, NmsBroadLogMsg, NmsTrackingUrl, NmsDelivery, NmsWebTrackingLogXtkFolder.

   * **[!UICONTROL Password]** : immetti la password dell&#39;account del database.
   * **[!UICONTROL Database]** : immettere il nome del database dell&#39;istanza di esecuzione.
   * **[!UICONTROL Target of an HTTP relay to remote database's account]** deve essere selezionata.


1. Crea un **[!UICONTROL External Database]** nel tuo account **marketing** con la seguente configurazione.

   ![](assets/line_config_mc_1.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : denomina il tuo account esterno come necessario.
   * **[!UICONTROL Type]** : select **[!UICONTROL External database]** .
   * La casella attivata deve essere selezionata.

   Da **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL Type]** : select **[!UICONTROL HTTP relay to remote Database]** .
   * **[!UICONTROL Server]** : immetti l’URL del server della campagna dell’istanza di esecuzione.
   * **[!UICONTROL Account]** : immetti l’account utilizzato per accedere all’istanza di esecuzione.
   * **[!UICONTROL Password]** : immetti la password dell’account utilizzato per accedere all’istanza di esecuzione.
   * **[!UICONTROL Data Source]** : immettere la sintassi seguente **[!UICONTROL nms:extAccount:ID of your external database account in the execution instance]** .


1. Crea un **[!UICONTROL Execution instance]** account esterno nel tuo **marketing** istanza che utilizza la seguente configurazione per creare il flusso di lavoro di sincronizzazione dati:

   ![](assets/line_config_mc_2.png)

   * **[!UICONTROL Label]** e **[!UICONTROL Internal name]** : denomina il tuo account esterno come necessario.
   * **[!UICONTROL Type]** : select **[!UICONTROL Execution instance]** .
   * La casella attivata deve essere selezionata.

   Da **[!UICONTROL Connection]** categoria:

   * **[!UICONTROL URL]** : immetti l’URL dell’istanza di esecuzione.
   * **[!UICONTROL Account]** : immetti l’account utilizzato per accedere all’istanza di esecuzione.
   * **[!UICONTROL Password]** : immetti la password dell’account utilizzato per accedere all’istanza di esecuzione.

   Da **[!UICONTROL Account connection method]** categoria:

   * **[!UICONTROL Method]** : select **[!UICONTROL Federated Data Access (FDA)]** .
   * **[!UICONTROL FDA account]** : seleziona il tuo account FDA dal menu a discesa.
   * Fai clic sul pulsante **[!UICONTROL Create the archiving workflow]**.
   * Fai clic sul pulsante **[!UICONTROL Create data synchronization workflow]** per creare il flusso di lavoro di sincronizzazione dati LINE.



1. Ora puoi iniziare [creazione di messaggi transazionali](../../message-center/using/creating-the-message-template.md).
