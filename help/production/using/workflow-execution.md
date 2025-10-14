---
product: campaign
title: Esecuzione di un flusso di lavoro
description: Esecuzione di un flusso di lavoro
feature: Monitoring, Workflows
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 3%

---

# Esecuzione di un flusso di lavoro{#workflow-execution}



La sezione seguente presenta informazioni sui problemi comuni relativi all’esecuzione dei flussi di lavoro e su come risolverli.

Per ulteriori informazioni sui flussi di lavoro, consulta le sezioni seguenti:

* [Informazioni sui flussi di lavoro](../../workflow/using/about-workflows.md)
* [Avvio di un flusso di lavoro](https://experienceleague.adobe.com/docs/campaign/automation/workflows/executing-a-workflow/start-a-workflow.html?lang=it){target="_blank"}.
* [Ciclo di vita del flusso di lavoro](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=it){target="_blank"}.
* [Best practice per l&#39;utilizzo dei flussi di lavoro](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html){target="_blank"}.

## Inizia il prima possibile nelle campagne {#start-as-soon-as-possible-in-campaigns}

In alcuni casi, i flussi di lavoro eseguiti da una campagna non vengono avviati quando si fa clic sul pulsante **[!UICONTROL Start]**. Invece di iniziare, si passa a uno stato &quot;Avvia il prima possibile&quot;.

Le cause di questo problema possono essere diverse. Per risolverlo, segui i passaggi seguenti:

1. Verificare lo stato del flusso di lavoro tecnico [**[!UICONTROL operationMgt]**](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/technical-workflows.html){target="_blank"}. Questo flusso di lavoro gestisce processi o flussi di lavoro all’interno di una campagna. In caso di errore, i flussi di lavoro non si avviano né si arrestano. Riavviala per riprendere l’esecuzione dei flussi di lavoro della campagna.

   Per ulteriori informazioni sul monitoraggio dei flussi di lavoro tecnici, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=it){target="_blank"}.

   >[!NOTE]
   >
   >Dopo il riavvio del flusso di lavoro, assicurarsi di eseguire le attività in sospeso (fare clic con il pulsante destro del mouse sull&#39;attività **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) per verificare se si verificano nuovamente errori in una delle attività.

   Se il flusso di lavoro continua a non riuscire, controlla il registro di controllo per individuare un errore specifico, risolvi i problemi di conseguenza, quindi riavvia di nuovo il flusso di lavoro.

1. Controllare lo stato del modulo **[!UICONTROL wfserver]** nella scheda **[!UICONTROL Monitoring]**, accessibile dalla home page di Campaign Classic (vedere [Processi di monitoraggio](../../production/using/monitoring-processes.md)). Questo processo è responsabile dell’esecuzione di tutti i flussi di lavoro.

   Un utente amministratore può inoltre verificare che il modulo **wfserver@`<instance>`** sia stato avviato nel server applicazioni principale utilizzando il comando seguente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Se il modulo non è in esecuzione, contatta l’Assistenza clienti di Adobe. Se hai un’installazione on-premise, un utente amministratore deve riavviare il servizio utilizzando il comando seguente.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Sostituisci **`<instance-name>`** con il nome della tua istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

1. Verifica se il **numero di processi della campagna in esecuzione** nell&#39;istanza è superiore alla soglia. Esiste un limite definito dall&#39;opzione [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) sul numero di processi della campagna eseguibili in parallelo sull&#39;istanza. Al raggiungimento di questo limite, il flusso di lavoro rimane nello stato &quot;Avvia il prima possibile&quot; purché il numero di flussi di lavoro in esecuzione sia superiore al limite.

   Per risolvere questo problema, arresta i flussi di lavoro indesiderati ed elimina le consegne non riuscite. Se la soglia è stata raggiunta, sarà possibile eseguire nuovi processi.

   Per verificare il numero di flussi di lavoro in esecuzione nell&#39;istanza, si consiglia di utilizzare le viste predefinite, accessibili per impostazione predefinita nella cartella **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Per ulteriori informazioni, consulta la [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >L&#39;aumento della soglia dell&#39;opzione **[!UICONTROL NmsOperation_LimitConcurrency]** può causare problemi di prestazioni nell&#39;istanza. In ogni caso, non eseguire questa operazione da solo e contatta il tuo contatto Adobe Campaign.

Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}.

## Avvio in corso {#start-in-progress}

Se i flussi di lavoro non sono in esecuzione e il loro stato è **Avvio in corso**, il modulo del flusso di lavoro potrebbe non essere avviato.

Per verificare e avviare il modulo, se necessario, attieniti alla seguente procedura:

1. Controllare lo stato del modulo **[!UICONTROL wfserver]** nella scheda **[!UICONTROL Monitoring]**, accessibile dalla home page di Campaign Classic (vedere [Processi di monitoraggio](../../production/using/monitoring-processes.md)).

   Un utente amministratore può inoltre verificare che il modulo **wfserver@`<instance>`** sia stato avviato nel server applicazioni principale utilizzando il comando seguente.

   ```sql
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<instance-name> (9340) - 11.3 Mb
   [...]
   ```

   Per ulteriori informazioni su come monitorare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#monitoring-commands-).

1. Se il modulo non è in esecuzione, contatta l’Assistenza clienti di Adobe. Se hai un’installazione on-premise, un amministratore deve riavviarla utilizzando il comando seguente.

   ```
   nlserver start wfserver@<instance-name>
   ```

   >[!NOTE]
   >
   >Sostituisci **`<instance-name>`** con il nome della tua istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

## Flusso di lavoro non riuscito {#failed-workflow}

Se un flusso di lavoro non riesce, effettua le seguenti operazioni:

1. Controlla il giornale di registrazione del flusso di lavoro. Per ulteriori informazioni, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html){target="_blank"}.
1. Monitorare i flussi di lavoro tecnici. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-technical-workflows.html?lang=it){target="_blank"}.
1. Cerca gli errori nelle singole attività del flusso di lavoro.
