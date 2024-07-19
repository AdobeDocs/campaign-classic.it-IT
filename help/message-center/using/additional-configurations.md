---
product: campaign
title: Configurazioni aggiuntive
description: Scopri come impostare configurazioni aggiuntive per la messaggistica transazionale in Adobe Campaign Classic
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 4%

---

# Configurazioni aggiuntive {#mc-additional-configurations}



## Monitorare le soglie {#monitoring-thresholds}

È possibile configurare le soglie di avviso (arancione) e le soglie di avviso (rosso) degli indicatori visualizzati nei report **Livello di servizio del Centro messaggi** e **Tempo di elaborazione del Centro messaggi** (fare riferimento a [Report di messaggistica transazionale di accesso](../../message-center/using/about-transactional-messaging-reports.md)).

A questo scopo, segui la procedura indicata di seguito:

1. Aprire la procedura guidata di distribuzione nell&#39;**istanza di esecuzione**.

1. Passare alla pagina **[!UICONTROL Message Center]**.

1. Utilizzare le frecce per modificare le soglie.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>Il numero di eventi in attesa nella coda viene visualizzato nella sezione [Indicatori di sistema](../../production/using/monitoring-processes.md#system-indicators) della pagina di monitoraggio dei processi di Adobe Campaign. Per ulteriori informazioni sulla procedura guidata di distribuzione, consultare [questa sezione](../../installation/using/deploying-an-instance.md#deployment-wizard).

## Eliminare gli eventi {#purging-events}

È possibile utilizzare la [procedura guidata di distribuzione](../../production/using/database-cleanup-workflow.md#deployment-wizard) per configurare la durata della memorizzazione dei dati nel database.

La rimozione degli eventi viene eseguita automaticamente dal [flusso di lavoro di pulizia del database](../../production/using/database-cleanup-workflow.md). Questo flusso di lavoro elimina gli eventi ricevuti e memorizzati nelle istanze di esecuzione e gli eventi archiviati in un&#39;istanza di controllo.

Utilizzare le frecce appropriate per modificare le impostazioni di rimozione.

Impostazioni di eliminazione degli eventi in un&#39;istanza di controllo:

![](assets/messagecenter_delete_events_001.png)

Impostazioni di eliminazione degli eventi in un&#39;istanza di esecuzione:

![](assets/messagecenter_delete_events_002.png)

Per ulteriori informazioni sul flusso di lavoro di pulizia del database, vedere [questa sezione](../../production/using/database-cleanup-workflow.md).


## Flussi di lavoro tecnici {#technical-workflows}

Prima di distribuire modelli di messaggi transazionali, è necessario assicurarsi che i flussi di lavoro tecnici sull’istanza di controllo e sulle diverse istanze di esecuzione siano stati effettivamente creati e avviati.

I vari flussi di lavoro tecnici relativi alla messaggistica transazionale (Centro messaggi) sono suddivisi tra l’istanza di controllo e le istanze di esecuzione.

### Controllare i flussi di lavoro delle istanze {#control-instance-workflows}

Nell&#39;istanza di controllo, indipendentemente dal fatto che siano registrate una o più istanze di esecuzione, è necessario creare un flusso di lavoro di archiviazione per ogni account esterno **[!UICONTROL Message Center execution instance]**. Fare clic sul pulsante **[!UICONTROL Create the archiving workflow]** per creare e avviare il flusso di lavoro.

![](assets/messagecenter_archiving_002.png)

È possibile accedere a questi flussi di lavoro dalla cartella **Amministrazione > Produzione > Centro messaggi**. Una volta creati, i flussi di lavoro di archiviazione vengono avviati automaticamente.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Flussi di lavoro dell’istanza di esecuzione {#execution-instance-workflows}

Nelle istanze di esecuzione, è possibile accedere ai flussi di lavoro tecnici per la messaggistica transazionale dalla cartella **Amministrazione > Produzione > Centro messaggi**. Devi solo avviarli. I flussi di lavoro nell’elenco sono:

* **[!UICONTROL Processing batch events]** (nome interno: **[!UICONTROL batchEventsProcessing]** ): questo flusso di lavoro consente di suddividere gli eventi batch in una coda prima che siano collegati a un modello di messaggio.
* **[!UICONTROL Processing real time events]** (nome interno: **[!UICONTROL rtEventsProcessing]** ): questo flusso di lavoro consente di suddividere gli eventi in tempo reale in una coda prima che vengano collegati a un modello di messaggio.
* **[!UICONTROL Update event status]** (nome interno: **[!UICONTROL updateEventStatus]** ): questo flusso di lavoro consente di attribuire uno stato all&#39;evento.

  Sono disponibili i seguenti stati dell’evento:

   * **[!UICONTROL Pending]** : l&#39;evento è in coda. Non è ancora stato assegnato alcun modello di messaggio.
   * **[!UICONTROL Pending delivery]** : l&#39;evento è in coda, gli è stato assegnato un modello di messaggio e viene elaborato dalla consegna.
   * **[!UICONTROL Sent]** : questo stato viene copiato dai registri di consegna. Significa che la consegna è stata inviata.
   * **[!UICONTROL Ignored by the delivery]** : questo stato viene copiato dai registri di consegna. Significa che la consegna è stata ignorata.
   * **[!UICONTROL Delivery failed]** : questo stato viene copiato dai registri di consegna. Significa che la consegna è non è andata a buon fine.
   * **[!UICONTROL Event not taken into account]** : impossibile collegare l&#39;evento a un modello di messaggio. L’evento non verrà elaborato.

### Pianificazione del flusso di lavoro di archiviazione

Evitare di modificare la pianificazione del flusso di lavoro di archiviazione **** eseguita sull&#39;istanza di controllo. In caso contrario, alcuni dati di tracciamento estratti dall’istanza di esecuzione potrebbero andare persi.

Se si modifica la pianificazione del flusso di lavoro di archiviazione, è necessario modificare anche la pianificazione del flusso di lavoro di **tracciamento** nell&#39;istanza di esecuzione in modo che corrisponda alla pianificazione del flusso di lavoro di archiviazione nell&#39;istanza di controllo.

## Configurare più brand {#configuring-multibranding}

Questa sezione descrive una soluzione per configurare il tracciamento e gli URL delle pagine mirror per marchio, per i messaggi transazionali in Adobe Campaign.

### Prerequisiti {#prerequisites}

* Tutti gli host devono essere aggiunti al file di configurazione dell&#39;istanza (`config-<instance>.xml`).
* A ogni marchio deve essere assegnato un sottodominio.
* Se il tracciamento web viene eseguito su pagine HTTPS, è necessario disporre di un certificato HTTPS per tutti i brand.

Per configurare il multibranding, è necessario configurare sia le istanze di esecuzione che l’istanza di controllo.

### Istanza di esecuzione {#execution-instance}

Nelle istanze di esecuzione, segui i passaggi seguenti:

1. Crea un account esterno per marchio.

   >[!NOTE]
   >
   >Scopri come creare un account esterno di tipo istanza di esecuzione in [questa sezione](../../message-center/using/configuring-instances.md#control-instance).

1. Estendere lo schema nms:extAccount per aggiungere l&#39;URL di tracciamento:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Scopri come estendere uno schema esistente nella sezione [Estensione di uno schema](../../configuration/using/extending-a-schema.md).

1. Modificare il modulo nms:extAccount:

   ```
   <container label="Message domain branding" type="frame">
        <static type="help"> These parameters are used to override the DNS alias and addresses used during message delivery. When not populated, the values of the 'NmsServer_MirrorPageUrl' and 'NmsEmail_DefaultErrorAddr' options are used.</static>
        <input xpath="@mirrorURL"/>
        <input xpath="@trackingURL"/>
        <input img="nms:sendemail.png" menuId="deliveryMenuBuilder" type="scriptEdit">
               xpath="errorAddress"/>
      </container>
   ```

1. Modificare le opzioni NmsTracking_OpenFormula e NmsTracking_ClickFormula per utilizzare il conto esterno anziché un&#39;opzione globale.

   Per eseguire questa operazione, sostituisci:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   con:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Queste modifiche potrebbero causare conflitti durante l&#39;aggiornamento. Potrebbe essere necessario unire manualmente queste formule con la nuova versione.

### Istanza di controllo {#control-instance}

Nell’istanza di controllo, devi collegare i modelli di consegna e gli account esterni.

A questo scopo, segui la procedura indicata di seguito:

1. Crea un account esterno per brand con lo stesso nome interno definito nell&#39;[istanza di esecuzione](#execution-instance) (passaggio 1).

1. Crea un modello di consegna predefinito per marchio.

   >[!NOTE]
   >
   >    Scopri come creare un modello di consegna in [questa sezione](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template).

1. In **[!UICONTROL Properties]** del modello di consegna, imposta il routing sull&#39;account esterno del brand.
