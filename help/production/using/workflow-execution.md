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
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 2%

---

# Esecuzione di un flusso di lavoro{#workflow-execution}



La sezione seguente presenta informazioni sui problemi comuni relativi all’esecuzione dei flussi di lavoro e su come risolverli.

Per ulteriori informazioni sui flussi di lavoro, consulta le sezioni seguenti:

* [Informazioni sui flussi di lavoro](../../workflow/using/about-workflows.md)
* [Avvio di un flusso di lavoro](../../workflow/using/starting-a-workflow.md)
* [Ciclo di vita di un flusso di lavoro](../../workflow/using/workflow-life-cycle.md)
* [Best practice per l’utilizzo dei flussi di lavoro](../../workflow/using/workflow-best-practices.md)

## Inizia il prima possibile nelle campagne {#start-as-soon-as-possible-in-campaigns}

In alcuni casi, i flussi di lavoro eseguiti da una campagna non vengono avviati quando si fa clic su **[!UICONTROL Start]** pulsante. Invece di iniziare, si passa a uno stato &quot;Avvia il prima possibile&quot;.

Le cause di questo problema possono essere diverse. Per risolverlo, segui i passaggi seguenti:

1. Controlla la [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) stato del flusso di lavoro tecnico. Questo flusso di lavoro gestisce processi o flussi di lavoro all’interno di una campagna. In caso di errore, i flussi di lavoro non si avviano né si arrestano. Riavviala per riprendere l’esecuzione dei flussi di lavoro della campagna.

   Per ulteriori informazioni sul monitoraggio dei flussi di lavoro tecnici, consulta [questa pagina](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Una volta riavviato il flusso di lavoro, assicurati di eseguire le attività in sospeso (fai clic con il pulsante destro del mouse sul **[!UICONTROL Scheduler]** attività / **[!UICONTROL Execute pending task(s) now]**) per verificare se si verifica di nuovo un errore in una qualsiasi delle attività.

   Se il flusso di lavoro continua a non riuscire, controlla il registro di controllo per individuare un errore specifico, risolvi i problemi di conseguenza, quindi riavvia di nuovo il flusso di lavoro.

1. Controlla la **[!UICONTROL wfserver]** stato del modulo in **[!UICONTROL Monitoring]** , accessibile dalla home page di Campaign Classic (consulta [Monitoraggio dei processi](../../production/using/monitoring-processes.md)). Questo processo è responsabile dell’esecuzione di tutti i flussi di lavoro.

   Un utente amministratore può anche verificare che **wfserver@`<instance>`** viene avviato sul server applicazioni principale utilizzando il comando seguente.

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
   >Sostituisci **`<instance-name>`** con il nome dell’istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

1. Controlla se **numero di processi di campagna in esecuzione** sull’istanza è superiore alla soglia. Esiste un limite definito da [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) opzione sul numero di processi di campaign che possono essere eseguiti in parallelo sull’istanza. Al raggiungimento di questo limite, il flusso di lavoro rimane nello stato &quot;Avvia il prima possibile&quot; purché il numero di flussi di lavoro in esecuzione sia superiore al limite.

   Per risolvere questo problema, arresta i flussi di lavoro indesiderati ed elimina le consegne non riuscite. Se la soglia è stata raggiunta, sarà possibile eseguire nuovi processi.

   Per verificare il numero di flussi di lavoro in esecuzione nell’istanza, si consiglia di utilizzare le viste predefinite, accessibili per impostazione predefinita nella sezione **[!UICONTROL Administration]** / **[!UICONTROL Audit]** cartella. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Aumento della **[!UICONTROL NmsOperation_LimitConcurrency]** la soglia delle opzioni può causare problemi di prestazioni nell’istanza. In ogni caso, non eseguire questa operazione da solo e contatta il tuo contatto Adobe Campaign.

Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta [questa sezione](../../workflow/using/monitoring-workflow-execution.md).

## Avvio in corso {#start-in-progress}

Se i flussi di lavoro non sono in esecuzione e il loro stato è **Avvio in corso**, ciò potrebbe significare che il modulo del flusso di lavoro non viene avviato.

Per verificare e avviare il modulo, se necessario, attieniti alla seguente procedura:

1. Controlla la **[!UICONTROL wfserver]** stato del modulo in **[!UICONTROL Monitoring]** , accessibile dalla home page di Campaign Classic (consulta [Monitoraggio dei processi](../../production/using/monitoring-processes.md)).

   Un utente amministratore può anche verificare che **wfserver@`<instance>`** viene avviato sul server applicazioni principale utilizzando il comando seguente.

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
   >Sostituisci **`<instance-name>`** con il nome dell’istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instance-name>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

## Flusso di lavoro non riuscito {#failed-workflow}

Se un flusso di lavoro non riesce, effettua le seguenti operazioni:

1. Controlla il giornale di registrazione del flusso di lavoro. Per ulteriori informazioni, consulta [Monitoraggio dell’esecuzione dei flussi di lavoro](../../workflow/using/monitoring-workflow-execution.md) e [Visualizza registri](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) sezioni.
1. Monitorare i flussi di lavoro tecnici. Per ulteriori informazioni, consulta [questa sezione](../../workflow/using/monitoring-technical-workflows.md).
1. Cerca gli errori nelle singole attività del flusso di lavoro.
