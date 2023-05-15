---
product: campaign
title: Configurazioni aggiuntive
description: Scopri come configurare configurazioni aggiuntive per i messaggi transazionali in Adobe Campaign Classic
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 4d25d740-db57-4d18-8cae-2dd49c4a786e
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 7%

---

# Configurazioni aggiuntive {#mc-additional-configurations}



## Monitorare le soglie {#monitoring-thresholds}

Puoi configurare le soglie di avviso (arancione) e le soglie di avviso (rosso) degli indicatori visualizzati nella **Livello di servizio del Centro messaggi** e **Tempo di elaborazione del Centro messaggi** rapporti (fare riferimento a [Accedere ai rapporti di messaggistica transazionale](../../message-center/using/about-transactional-messaging-reports.md)).

A tale scopo, segui la procedura indicata di seguito:

1. Apri la procedura guidata di distribuzione in **istanza di esecuzione**.

1. Vai a **[!UICONTROL Message Center]** pagina.

1. Utilizzare le frecce per modificare le soglie.

   ![](assets/messagecenter_monitor_events_001.png)

>[!NOTE]
>
>Il numero di eventi in sospeso nella coda viene visualizzato nella [Indicatori di sistema](../../production/using/monitoring-processes.md#system-indicators) della pagina di monitoraggio del processo di Adobe Campaign. Per ulteriori informazioni sulla procedura guidata di distribuzione, consulta [questa sezione](../../installation/using/deploying-an-instance.md#deployment-wizard).

## Eliminare gli eventi {#purging-events}

È possibile utilizzare [procedura guidata di distribuzione](../../production/using/database-cleanup-workflow.md#deployment-wizard) per configurare per quanto tempo i dati devono essere memorizzati nel database.

L&#39;eliminazione degli eventi viene eseguita automaticamente dal [Flusso di lavoro di pulizia del database](../../production/using/database-cleanup-workflow.md). Questo flusso di lavoro elimina gli eventi ricevuti e memorizzati nelle istanze di esecuzione e gli eventi archiviati in un’istanza di controllo.

Utilizzare le frecce appropriate per modificare le impostazioni di eliminazione.

Impostazioni di eliminazione degli eventi in un&#39;istanza di controllo:

![](assets/messagecenter_delete_events_001.png)

Impostazioni di eliminazione degli eventi in un&#39;istanza di esecuzione:

![](assets/messagecenter_delete_events_002.png)

Per ulteriori informazioni sul flusso di lavoro di pulizia del database, consulta [questa sezione](../../production/using/database-cleanup-workflow.md).


## Flussi di lavoro tecnici {#technical-workflows}

Devi accertarti che i flussi di lavoro tecnici sull’istanza di controllo e sulle diverse istanze di esecuzione siano stati effettivamente creati e avviati prima di distribuire qualsiasi modello di messaggio transazionale.

I vari flussi di lavoro tecnici relativi alla messaggistica transazionale (Message Center, Centro messaggi) sono suddivisi tra l’istanza di controllo e le istanze di esecuzione.

### Controllare i flussi di lavoro delle istanze {#control-instance-workflows}

Nell’istanza di controllo, indipendentemente dalla registrazione di una o più istanze di esecuzione, è necessario creare un flusso di lavoro di archiviazione per ogni **[!UICONTROL Message Center execution instance]** conto esterno. Fai clic sul pulsante **[!UICONTROL Create the archiving workflow]** per creare e avviare il flusso di lavoro.

![](assets/messagecenter_archiving_002.png)

Questi flussi di lavoro sono quindi accessibili dal **Amministrazione > Produzione > Centro messaggi** cartella. Una volta creati, i flussi di lavoro di archiviazione vengono avviati automaticamente.

<!--**Minimal architecture**

Once the control and execution modules are installed on the same instance, you must create the archiving workflow using the deployment wizard. Click the **[!UICONTROL Create the archiving workflow]** button to create and start the workflow.

![](assets/messagecenter_archiving_001.png)-->

### Flussi di lavoro dell’istanza di esecuzione {#execution-instance-workflows}

Nelle istanze di esecuzione, è possibile accedere ai flussi di lavoro tecnici per la messaggistica transazionale da **Amministrazione > Produzione > Centro messaggi** cartella. Dovete solo cominciare a farlo. I flussi di lavoro nell’elenco sono:

* **[!UICONTROL Processing batch events]** (nome interno: **[!UICONTROL batchEventsProcessing]** ): questo flusso di lavoro ti consente di suddividere gli eventi batch in una coda prima che siano collegati a un modello di messaggio.
* **[!UICONTROL Processing real time events]** (nome interno: **[!UICONTROL rtEventsProcessing]** ): questo flusso di lavoro ti consente di suddividere gli eventi in tempo reale in una coda prima che siano collegati a un modello di messaggio.
* **[!UICONTROL Update event status]** (nome interno: **[!UICONTROL updateEventStatus]** ): questo flusso di lavoro ti consente di attribuire uno stato all’evento.

   Sono disponibili i seguenti stati dell’evento:

   * **[!UICONTROL Pending]** : l’evento è in coda. Non è ancora stato assegnato alcun modello di messaggio.
   * **[!UICONTROL Pending delivery]** : l’evento è in coda, gli è stato assegnato un modello di messaggio e viene elaborato dalla consegna.
   * **[!UICONTROL Sent]** : questo stato viene copiato dai log di consegna. Significa che la consegna è stata inviata.
   * **[!UICONTROL Ignored by the delivery]** : questo stato viene copiato dai log di consegna. Significa che la consegna è stata ignorata.
   * **[!UICONTROL Delivery failed]** : questo stato viene copiato dai log di consegna. Significa che la consegna è non è andata a buon fine.
   * **[!UICONTROL Event not taken into account]** : impossibile collegare l&#39;evento a un modello di messaggio. L’evento non viene elaborato.

## Configurare più brand {#configuring-multibranding}

Questa sezione descrive una soluzione per configurare il tracciamento e gli URL di pagina speculare per marchio, per i messaggi transazionali in Adobe Campaign.

### Prerequisiti {#prerequisites}

* Tutti gli host devono essere aggiunti al file di configurazione dell&#39;istanza (`config-<instance>.xml`).
* A ogni marchio deve essere assegnato un sottodominio.
* Se il monitoraggio web viene eseguito su pagine HTTPS, è necessario disporre di un certificato HTTPS per tutti i marchi.

Per configurare più brand, è necessario configurare sia le istanze di esecuzione che l’istanza di controllo.

### Istanza di esecuzione {#execution-instance}

Sulle istanze di esecuzione, segui i passaggi seguenti:

1. Crea un account esterno per marchio.

   >[!NOTE]
   >
   >Scopri come creare un account esterno di tipo istanza di esecuzione in [questa sezione](../../message-center/using/configuring-instances.md#control-instance).

1. Estendi lo schema nms:extAccount per aggiungere l&#39;URL di tracciamento:

   ```
   <attribute advanced="true" desc="URL of the tracking servers" label="Tracking server URL"
   length="100" name="trackingURL" type="string"/>
   ```

   >[!NOTE]
   >
   >Scopri come estendere uno schema esistente nel [Estensione di uno schema](../../configuration/using/extending-a-schema.md) sezione .

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

1. Modifica le opzioni NmsTracking_OpenFormula e NmsTracking_ClickFormula per utilizzare l&#39;account esterno invece di un&#39;opzione globale.

   A questo scopo, sostituisci:

   ```
   <%@ include option='NmsTracking_ServerUrl' %>
   ```

   con:

   ```
   <%@ value object="provider" xpath="@trackingURL" %>
   ```

   >[!IMPORTANT]
   >
   >Queste modifiche potrebbero causare conflitti durante l&#39;aggiornamento. Potrebbe essere necessario unire manualmente queste formule con la loro nuova versione.

### Istanza di controllo {#control-instance}

Nell’istanza di controllo è necessario collegare modelli di consegna e account esterni.

A tale scopo, segui la procedura indicata di seguito:

1. Crea un account esterno per marchio con lo stesso nome interno definito nella [istanza di esecuzione](#execution-instance) (passaggio 1).

1. Crea un modello di consegna predefinito per marchio.

   >[!NOTE]
   >
   >    Scopri come creare un modello di consegna in [questa sezione](../../delivery/using/creating-a-delivery-template.md#creating-a-new-template).

1. Nel modello di consegna **[!UICONTROL Properties]**, imposta il routing sull’account esterno del brand.
