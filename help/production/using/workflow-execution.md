---
product: campaign
title: Esecuzione di un flusso di lavoro
description: Esecuzione di un flusso di lavoro
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: b5aa5663-1902-4f50-9202-783e73a28838
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---

# Esecuzione di un flusso di lavoro{#workflow-execution}

![](../../assets/v7-only.svg)

La sezione seguente presenta informazioni sui problemi comuni relativi all’esecuzione dei flussi di lavoro e su come risolverli.

Per ulteriori informazioni sui flussi di lavoro, consulta queste sezioni:

* [Informazioni sui flussi di lavoro](../../workflow/using/about-workflows.md)
* [Avvio di un flusso di lavoro](../../workflow/using/starting-a-workflow.md)
* [Ciclo di vita di un flusso di lavoro](../../workflow/using/workflow-life-cycle.md)
* [Best practice per l’utilizzo dei flussi di lavoro](../../workflow/using/workflow-best-practices.md)

## Inizia il prima possibile nelle campagne {#start-as-soon-as-possible-in-campaigns}

In alcuni casi, i flussi di lavoro eseguiti da una campagna non si avviano facendo clic sul pulsante **[!UICONTROL Start]** . Invece di iniziare, passa a uno stato &quot;Avvia il prima possibile&quot;.

Ci possono essere diverse cause per questo problema, segui i passaggi seguenti per risolverlo:

1. Controlla lo stato del flusso di lavoro tecnico [**[!UICONTROL operationMgt]**](../../workflow/using/about-technical-workflows.md) . Questo flusso di lavoro gestisce processi o flussi di lavoro all’interno di una campagna. In caso di errore, i flussi di lavoro non verranno avviati/interrotti. Riavvialo per riprendere l’esecuzione dei flussi di lavoro della campagna.

   Per ulteriori informazioni sul monitoraggio dei flussi di lavoro tecnici, consulta [questa pagina](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Una volta riavviato il flusso di lavoro, assicurati di eseguire le attività in sospeso (fai clic con il pulsante destro del mouse sull’ **[!UICONTROL Scheduler]** attività / **[!UICONTROL Execute pending task(s) now]**) per verificare se non riesce di nuovo su una qualsiasi delle attività.

   Se il flusso di lavoro continua a non riuscire, controlla il registro di controllo per individuare un errore specifico, risolvi di conseguenza, quindi riavvia il flusso di lavoro.

1. Controlla lo stato del modulo **[!UICONTROL wfserver]** nella scheda **[!UICONTROL Monitoring]**, accessibile dalla home page di Campaign Classic (consulta [Processi di monitoraggio](../../production/using/monitoring-processes.md)). Questo processo è responsabile dell&#39;esecuzione di tutti i flussi di lavoro.

   Un utente amministratore può anche verificare che il modulo **wfserver@`<instance>`** sia avviato sul server dell&#39;applicazione principale utilizzando il comando seguente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Se il modulo non è in esecuzione, contatta l’Assistenza clienti Adobe. Se disponi di un’installazione on-premise, un utente amministratore deve riavviare il servizio utilizzando il comando seguente.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sostituisci **`<instancename>`** con il nome della tua istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

1. Controlla se il **numero di processi della campagna che eseguono** sull&#39;istanza è superiore alla soglia. Esiste un limite definito dall’opzione [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) per il numero di processi di campagna che possono essere eseguiti in parallelo sull’istanza. Al raggiungimento di questo limite, il flusso di lavoro rimane nello stato &quot;Avvia il prima possibile&quot; purché il numero di flussi di lavoro in esecuzione sia superiore al limite.

   Per risolvere questo problema, interrompi i flussi di lavoro indesiderati ed elimina le consegne non riuscite. Se la soglia è stata raggiunta, questo consentirà l&#39;esecuzione di nuovi processi.

   Per controllare il numero di flussi di lavoro in esecuzione nell’istanza, si consiglia di utilizzare le viste predefinite, accessibili per impostazione predefinita nella cartella **[!UICONTROL Administration]** / **[!UICONTROL Audit]** . Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >L’aumento della soglia di opzione **[!UICONTROL NmsOperation_LimitConcurrency]** può causare problemi di prestazioni nell’istanza. In ogni caso, non eseguire questa operazione da solo e contatta il tuo contatto Adobe Campaign.

Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta [questa sezione](../../workflow/using/monitoring-workflow-execution.md).

## Inizia in corso {#start-in-progress}

Se i flussi di lavoro non sono in esecuzione e il loro stato è **Start in progress**, ciò potrebbe significare che il modulo del flusso di lavoro non viene avviato.

Per verificare questo e per avviare il modulo, se necessario, esegui i seguenti passaggi:

1. Controlla lo stato del modulo **[!UICONTROL wfserver]** nella scheda **[!UICONTROL Monitoring]**, accessibile dalla home page di Campaign Classic (consulta [Processi di monitoraggio](../../production/using/monitoring-processes.md)).

   Un utente amministratore può anche verificare che il modulo **wfserver@`<instance>`** sia avviato sul server dell&#39;applicazione principale utilizzando il comando seguente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Per ulteriori informazioni su come monitorare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#monitoring-commands-).

1. Se il modulo non è in esecuzione, contatta l’Assistenza clienti Adobe. Se disponi di un’installazione on-premise, un amministratore deve riavviarla utilizzando il comando seguente.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sostituisci **`<instancename>`** con il nome della tua istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consulta [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

## Flusso di lavoro non riuscito {#failed-workflow}

Se un flusso di lavoro non riesce, procedi come segue:

1. Controlla il giornale di registrazione del flusso di lavoro. Per ulteriori informazioni, consulta le sezioni [Esecuzione del flusso di lavoro di monitoraggio](../../workflow/using/monitoring-workflow-execution.md) e [Visualizza registri](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) .
1. Monitorare i flussi di lavoro tecnici. Per ulteriori informazioni, consulta [questa sezione](../../workflow/using/monitoring-technical-workflows.md).
1. Cerca gli errori nelle singole attività del flusso di lavoro.
