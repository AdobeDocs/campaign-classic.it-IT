---
title: Esecuzione di un flusso di lavoro
seo-title: Esecuzione di un flusso di lavoro
description: Esecuzione di un flusso di lavoro
seo-description: null
page-status-flag: never-activated
uuid: 115256f6-bdf2-4594-885c-e90d02a25b80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 7d8828c5-5776-49ca-b4f7-a4a6aaaa9db1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5a4ee9b14d4c77f74ff73209d4323bf4f1347155
workflow-type: tm+mt
source-wordcount: '635'
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

In alcuni casi, i flussi di lavoro eseguiti da una campagna non iniziano quando si fa clic sul **[!UICONTROL Start]** pulsante. Anziché iniziare, lo stato diventa &quot;Inizia il prima possibile&quot;.

Il problema può essere dovuto a diverse cause, seguite i passaggi indicati di seguito per risolverlo:

1. Controllare lo stato del flusso di lavoro [**[!UICONTROL operationMgt]**](../../workflow/using/campaign.md) tecnico. Questo flusso di lavoro consente di gestire i processi o i flussi di lavoro all’interno di una campagna. In caso di errore, i flussi di lavoro non verranno avviati/interrotti. Riavviatelo per riprendere i flussi di lavoro delle campagne.

   Per ulteriori informazioni sul monitoraggio dei flussi di lavoro tecnici, consulta [questa pagina](../../workflow/using/monitoring-technical-workflows.md).

   >[!NOTE]
   >
   >Una volta riavviato il flusso di lavoro, accertatevi di eseguire le attività in sospeso (fate clic con il pulsante destro del mouse sull&#39; **[!UICONTROL Scheduler]** attività / **[!UICONTROL Execute pending task(s) now]**) per verificare se il flusso di lavoro ha nuovamente esito negativo su una qualsiasi delle attività.

   Se il flusso di lavoro continua a non riuscire, controllare il registro di controllo per verificare la presenza di errori specifici, risolvere i problemi di conseguenza, quindi riavviare il flusso di lavoro.

1. Controllare lo stato del **[!UICONTROL wfserver]** modulo nella **[!UICONTROL Monitoring]** scheda, accessibile dalla homepage del Campaign Classic (vedere Processi [di](../../production/using/monitoring-processes.md)monitoraggio). Questo processo è responsabile dell&#39;esecuzione di tutti i flussi di lavoro.

   Un utente amministratore può anche verificare che il modulo **wfserver@`<instance>`** venga avviato sul server applicazione principale utilizzando il comando seguente.

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
   >Sostituire **`<instancename>`** con il nome dell’istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Per ulteriori informazioni sul riavvio dei moduli, consultare [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

1. Verificare se il **numero di processi della campagna in esecuzione** sull&#39;istanza è superiore alla soglia. Esiste un limite definito dall&#39; [**[!UICONTROL NmsOperation_LimitConcurrency]**](../../installation/using/configuring-campaign-options.md#campaign-e-workflow-management) opzione per il numero di processi di campagna che possono essere eseguiti in parallelo sull&#39;istanza. Una volta raggiunto questo limite, il flusso di lavoro rimane nello stato &quot;Avvia il prima possibile&quot;, a condizione che il numero di flussi di lavoro in esecuzione sia superiore al limite.

   Per risolvere questo problema, interrompere i flussi di lavoro indesiderati ed eliminare le consegne non riuscite. Se la soglia è stata raggiunta, ciò consentirà l&#39;esecuzione di nuovi processi.

   Per verificare il numero di flussi di lavoro in esecuzione dell&#39;istanza, si consiglia di utilizzare le viste predefinite, accessibili per impostazione predefinita nella cartella **[!UICONTROL Administration]** / **[!UICONTROL Audit]** . Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status).

   >[!CAUTION]
   >
   >L&#39;aumento della soglia di **[!UICONTROL NmsOperation_LimitConcurrency]** opzione potrebbe causare problemi di prestazioni nell&#39;istanza. In ogni caso, non eseguire questa operazione autonomamente e contattare il vostro contatto Adobe Campaign .

Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta [questa sezione](../../workflow/using/monitoring-workflow-execution.md).

## Inizio in corso {#start-in-progress}

Se i flussi di lavoro non sono in esecuzione e il loro stato è **Inizia in corso**, ciò potrebbe significare che il modulo del flusso di lavoro non è avviato.

Per controllare questo e avviare il modulo, se necessario, eseguire i seguenti passaggi:

1. Controllare lo stato del **[!UICONTROL wfserver]** modulo nella **[!UICONTROL Monitoring]** scheda, accessibile dalla homepage del Campaign Classic (vedere Processi [di](../../production/using/monitoring-processes.md)monitoraggio).

   Un utente amministratore può anche verificare che il modulo **wfserver@`<instance>`** venga avviato sul server applicazione principale utilizzando il comando seguente.

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
   >Sostituire **`<instancename>`** con il nome dell’istanza (produzione, sviluppo, ecc.). Il nome dell’istanza viene identificato tramite i file di configurazione:
   >`[path of application]nl6/conf/config-<instancename>.xml`

   Per ulteriori informazioni sul riavvio dei moduli, consultare [questa sezione](../../production/using/usual-commands.md#module-launch-commands).

## Flusso di lavoro non riuscito {#failed-workflow}

Se un flusso di lavoro ha esito negativo, effettuate le seguenti operazioni:

1. Controllare il giornale di registrazione del flusso di lavoro. Per ulteriori informazioni, consulta le sezioni Esecuzione [del flusso di lavoro di](../../workflow/using/monitoring-workflow-execution.md) monitoraggio e [Visualizza registri](../../workflow/using/monitoring-workflow-execution.md#displaying-logs) .
1. Monitorare i flussi di lavoro tecnici. For more on this refer to the [this section](../../workflow/using/monitoring-technical-workflows.md).
1. Individuare eventuali errori nelle singole attività del flusso di lavoro.
