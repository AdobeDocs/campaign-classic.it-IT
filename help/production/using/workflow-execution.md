---
solution: Campaign Classic
product: campaign
title: Esecuzione di un flusso di lavoro
description: Esecuzione di un flusso di lavoro
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 3%

---


# Esecuzione di un flusso di lavoro{#workflow-execution}

La sezione seguente contiene informazioni su problemi comuni relativi all’esecuzione dei flussi di lavoro e su come risolverli.

Per ulteriori informazioni sui flussi di lavoro, consulta le sezioni seguenti:

* [Informazioni sui flussi di lavoro](../../workflow/using/about-workflows.md)
* [Avvio di un flusso di lavoro](../../workflow/using/starting-a-workflow.md)
* [Ciclo di vita di un flusso di lavoro](../../workflow/using/workflow-life-cycle.md)
* [Best practice per l&#39;utilizzo dei flussi di lavoro](../../workflow/using/workflow-best-practices.md)

## Inizia il prima possibile nelle campagne {#start-as-soon-as-possible-in-campaigns}

In alcuni casi, i flussi di lavoro eseguiti da una campagna non iniziano quando si fa clic sul pulsante **[!UICONTROL Start]**. Anziché iniziare, lo stato diventa &quot;Inizia il prima possibile&quot;.

Il problema può essere dovuto a diverse cause, seguite i passaggi indicati di seguito per risolverlo:

1. Controllare lo stato del [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) flusso di lavoro tecnico. Questo flusso di lavoro consente di gestire i processi o i flussi di lavoro all’interno di una campagna. In caso di errore, i flussi di lavoro non verranno avviati/interrotti. Riavviatelo per riprendere i flussi di lavoro delle campagne.

   Per ulteriori informazioni sul monitoraggio dei flussi di lavoro tecnici, consultare [questa pagina](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Una volta riavviato il flusso di lavoro, assicurarsi di eseguire le attività in sospeso (fare clic con il pulsante destro del mouse sull&#39;attività **[!UICONTROL Scheduler]** / **[!UICONTROL Execute pending task(s) now]**) per verificare se ha nuovamente esito negativo su una delle attività.

   Se il flusso di lavoro continua a non riuscire, controllare il registro di controllo per verificare la presenza di errori specifici, risolvere i problemi di conseguenza, quindi riavviare il flusso di lavoro.

1. Controllare lo stato del modulo **[!UICONTROL wfserver]** nella scheda **[!UICONTROL Monitoring]**, accessibile dalla home page Campaign Classic (vedere [Processi di monitoraggio](../../production/using/monitoring-processes.md)). Questo processo è responsabile dell&#39;esecuzione di tutti i flussi di lavoro.

   Un utente amministratore può anche verificare che il modulo **wfserver@`<instance>`** sia avviato sul server applicazione principale utilizzando il comando seguente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Version X.Y (build XXXX) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Se il modulo non è in esecuzione, contatta  Assistenza clienti di Adobe. Se disponete di un&#39;installazione locale, un utente amministratore deve riavviare il servizio utilizzando il comando seguente.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sostituire **`<instancename>`** con il nome dell&#39;istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consultare [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

1. Verificare che il numero **di processi di campagna in esecuzione** nell&#39;istanza sia superiore alla soglia. Esiste un limite definito dall&#39;opzione [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) per il numero di processi di campagna che possono essere eseguiti parallelamente sull&#39;istanza. Una volta raggiunto questo limite, il flusso di lavoro rimane nello stato &quot;Avvia il prima possibile&quot;, a condizione che il numero di flussi di lavoro in esecuzione sia superiore al limite.

   Per risolvere questo problema, interrompere i flussi di lavoro indesiderati ed eliminare le consegne non riuscite. Se la soglia è stata raggiunta, ciò consentirà l&#39;esecuzione di nuovi processi.

   Per verificare il numero di flussi di lavoro in esecuzione dell&#39;istanza, si consiglia di utilizzare le viste predefinite, accessibili per impostazione predefinita nella cartella **[!UICONTROL Administration]** / **[!UICONTROL Audit]**. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!IMPORTANT]
   >
   >Aumentare la soglia di opzione **[!UICONTROL NmsOperation_LimitConcurrency]** potrebbe causare problemi di prestazioni nell&#39;istanza. In ogni caso, non eseguire questa operazione autonomamente e contattare il vostro contatto Adobe Campaign .

Per ulteriori informazioni su come monitorare i flussi di lavoro, consultare [questa sezione](../../workflow/using/monitoring-workflow-execution.md).

## Inizio in corso {#start-in-progress}

Se i flussi di lavoro non sono in esecuzione e il loro stato è **Inizia in corso**, ciò potrebbe significare che il modulo del flusso di lavoro non è avviato.

Per controllare questo e avviare il modulo, se necessario, eseguire i seguenti passaggi:

1. Controllare lo stato del modulo **[!UICONTROL wfserver]** nella scheda **[!UICONTROL Monitoring]**, accessibile dalla home page Campaign Classic (vedere [Processi di monitoraggio](../../production/using/monitoring-processes.md)).

   Un utente amministratore può anche verificare che il modulo **wfserver@`<instance>`** sia avviato sul server applicazione principale utilizzando il comando seguente.

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   [...]
   wfserver@<INSTANCENAME> (9340) - 11.3 Mb
   [...]
   ```

   Per ulteriori informazioni su come monitorare i moduli, consultare [questa sezione](../../production/using/usual-commands.md#monitoring-commands-).

1. Se il modulo non è in esecuzione, contatta  Assistenza clienti di Adobe. Se disponete di un&#39;installazione locale, un amministratore deve riavviarla utilizzando il comando seguente.

   ```
   nlserver start wfserver@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >Sostituire **`<instancename>`** con il nome dell&#39;istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Per ulteriori informazioni su come riavviare i moduli, consultare [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

## Flusso di lavoro non riuscito {#failed-workflow}

Se un flusso di lavoro ha esito negativo, effettuate le seguenti operazioni:

1. Controllare il giornale di registrazione del flusso di lavoro. Per ulteriori informazioni, consultare le sezioni [Esecuzione del flusso di lavoro di monitoraggio](../../workflow/using/monitoring-workflow-execution.md) e [Visualizza registri](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).
1. Monitorare i flussi di lavoro tecnici. Per ulteriori informazioni, fare riferimento alla sezione [presente](../../workflow/using/monitoring-technical-workflows.md).
1. Individuare eventuali errori nelle singole attività del flusso di lavoro.
