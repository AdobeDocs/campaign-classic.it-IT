---
solution: Campaign Classic
product: campaign
title: Monitoraggio dei flussi di lavoro tecnici
description: Monitoraggio dei flussi di lavoro tecnici
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: a9d58e25ab17baaabf4ff8c109b53e83c7d93218
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 8%

---


# Monitoraggio dei flussi di lavoro tecnici {#monitoring-technical-workflows}

I flussi di lavoro tecnici devono essere monitorati e le azioni devono essere intraprese in caso di guasto.

In [questa pagina](../../production/using/monitoring-guidelines.md) sono disponibili metodi aggiuntivi per monitorare i diversi processi di Campaign.

## Pannello di controllo per istanza {#instance-monitoring-dashboard}

È possibile accedere al dashboard di monitoraggio delle istanze tramite l&#39;universo **[!UICONTROL Monitoring]**.

![](assets/monitoring_technical_workflows1.png)

In Indicatori di sistema e file di base, verificare che nessun indicatore sia evidenziato in rosso. Se questo è il caso e alcuni sono, è necessario:

* Verificare che i processi necessari siano sempre in esecuzione,
* Verificate che nessuno dei processi sia troppo vecchio,
* Verificate che i file di registro dei diversi processi non contengano errori allarmanti e ricorrenti.

## Flussi di lavoro tecnici {#technical-workflows}

I flussi di lavoro tecnici sono disponibili da **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

A seconda del flusso di lavoro tecnico, seguite i passaggi descritti di seguito per assicurarvi che tutto funzioni come previsto.

Per comprendere meglio le operazioni che ogni flusso di lavoro tecnico dovrebbe eseguire, fare riferimento a questa sezione [](../../workflow/using/about-technical-workflows.md).

Per **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. Verificare che il flusso di lavoro **[!UICONTROL Database Cleanup]** venga eseguito e terminato correttamente ogni giorno. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/delivery.md).
1. Esaminare il giornale di registrazione per verificare che il tempo trascorso sia relativamente costante nel tempo e non interferisca con altri flussi di lavoro.
1. Per ulteriori informazioni, controllare la [pagina](../../production/using/database-cleanup-workflow.md).

Per **[!UICONTROL Tracking workflow (‘tracking’)]**:

Verificare che il flusso di lavoro di tracciamento venga eseguito come pianificato (ogni ora per impostazione predefinita) e che il giornale di registrazione non evidenzi gli errori ricorrenti. Per ulteriori informazioni, consulta questa [sezione](../../workflow/using/delivery.md).

Per **[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. Verificare che il flusso di lavoro **[!UICONTROL Deliverability update]** venga eseguito e terminato correttamente ogni giorno. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/delivery.md).
1. Verificare nel giornale di registrazione che le regole siano aggiornate regolarmente.

Per **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. Esaminate tutti i flussi di lavoro che si trovano nella cartella **[!UICONTROL Campaign process]**. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/about-technical-workflows.md).
1. Verificare che i flussi di lavoro vengano eseguiti come pianificato e che il giornale di registrazione non evidenzi gli errori ricorrenti.

## Controllo del flusso di lavoro {#workflow-supervision}

Il gruppo **[!UICONTROL Workflow supervisors]** deve contenere operatori che devono essere informati dei guasti e che possono intervenire in tempo.

![](assets/monitoring_technical_workflows3.png)

In caso di problemi, è necessario generare un avviso e inviarlo al gruppo corretto.

Accertatevi che ciascun operatore disponga di un indirizzo e-mail valido.

Qualsiasi flusso di lavoro da eseguire per mantenere la piattaforma attiva, ad esempio le importazioni giornaliere di dati, deve essere dichiarato &quot;Produzione&quot; (casella di controllo) e visualizzato in grassetto.

## Elenco di manutenzione del flusso di lavoro {#workflow-maintenance-list}

Tutti i flussi di lavoro tecnici personalizzati devono essere documentati in un foglio di lavoro contenente:

* Nome e posizione del flusso di lavoro.
* Finalità.
* Pianificazione e dipendenze.
* Operatore incaricato del monitoraggio.
* Istruzioni su cosa fare in caso di errore.

![](assets/monitoring_technical_workflows4.png)

## Pianificazione e automazione del monitoraggio {#planning-and-automation-of-monitoring}

Il monitoraggio del flusso di lavoro di pianificazione ne migliora l&#39;efficienza. Alcune attività devono essere eseguite quotidianamente mentre altre possono essere eseguite settimanalmente o mensilmente.

L&#39;impostazione dei flussi di lavoro in cartelle denominate per ricorrenza e ordinate per pianificazione dell&#39;esecuzione migliora l&#39;efficienza del monitoraggio.

L&#39;automazione del monitoraggio riduce il sovraccarico delle risorse e assicura che le attività siano pianificate alla frequenza appropriata.

Potete creare un flusso di lavoro di monitoraggio per inviare un messaggio e-mail ogni volta che determinate attività non vanno a buon fine o quando una tabella critica diventa troppo grande.

È possibile creare una visualizzazione che consenta di monitorare tutti i flussi di lavoro in un&#39;area funzionale o a livello di sistema.

Potete inoltre utilizzare la funzionalità di  processo Adobe Campaign o di report per creare la documentazione su richiesta, sempre aggiornata.
