---
solution: Campaign Classic
product: campaign
title: Monitoraggio dei flussi di lavoro tecnici
description: Monitoraggio dei flussi di lavoro tecnici
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 8%

---


# Monitoraggio dei flussi di lavoro tecnici {#monitoring-technical-workflows}

I flussi di lavoro tecnici devono essere monitorati e devono essere intraprese azioni in caso di guasto.

In [questa pagina](../../production/using/monitoring-guidelines.md) sono descritti metodi aggiuntivi per monitorare i diversi processi di Campaign.

## Dashboard di monitoraggio delle istanze {#instance-monitoring-dashboard}

È possibile accedere al dashboard di monitoraggio delle istanze tramite la scheda **[!UICONTROL Monitoring]** .

![](assets/monitoring_technical_workflows1.png)

In Indicatori di sistema e file di base verificare che non siano evidenziati indicatori in rosso. Se questo è il caso e alcuni sono, dovresti:

* Verificare che i processi necessari siano sempre in esecuzione,
* Controlla che nessuno dei processi sia troppo vecchio,
* Controlla che i file di registro dei diversi processi non contengano errori allarmanti e ricorrenti.

## Flussi di lavoro tecnici {#technical-workflows}

I flussi di lavoro tecnici sono disponibili da **[!UICONTROL Administration]** > **[!UICONTROL Production]** > **[!UICONTROL Technical workflows]**.

A seconda del flusso di lavoro tecnico, segui i passaggi descritti di seguito per garantire che tutto funzioni come previsto.

Per comprendere meglio le operazioni che ogni flusso di lavoro tecnico deve eseguire, consulta questa [sezione](../../workflow/using/about-technical-workflows.md).

Per **[!UICONTROL Database Cleanup workflow (‘cleanup’)]**:

1. Verifica che il flusso di lavoro **[!UICONTROL Database Cleanup]** venga eseguito e terminato con successo ogni giorno. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/delivery.md).
1. Consultare il giornale di registrazione per verificare che il tempo trascorso sia relativamente costante nel tempo e non interferisca con altri flussi di lavoro.
1. Per ulteriori informazioni, controllare [page](../../production/using/database-cleanup-workflow.md).

Per **[!UICONTROL Tracking workflow (‘tracking’)]**:

Controlla che il flusso di lavoro di tracciamento venga eseguito come programmato (ogni ora per impostazione predefinita) e che il giornale di registrazione non evidenzi gli errori ricorrenti. Per ulteriori informazioni, consulta questa [sezione](../../workflow/using/delivery.md).

Per **[!UICONTROL Deliverability update (‘deliverabilityUpdate’)]**:

1. Verifica che il flusso di lavoro **[!UICONTROL Deliverability update]** venga eseguito e terminato con successo ogni giorno. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/delivery.md).
1. Verifica nel giornale di registrazione che le regole vengano aggiornate regolarmente.

Per **[!UICONTROL Campaign process ('operationMgt', 'deliveryMgt', ...)]**:

1. Osserva tutti i flussi di lavoro che si trovano sotto la cartella **[!UICONTROL Campaign process]** . Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/about-technical-workflows.md).
1. Verificare che i flussi di lavoro vengano eseguiti come programmato e che il giornale di registrazione non evidenzi gli errori ricorrenti.

## Sorveglianza del flusso di lavoro {#workflow-supervision}

Il gruppo **[!UICONTROL Workflow supervisors]** deve contenere operatori che devono essere informati degli errori e che possono intervenire in tempo.

![](assets/monitoring_technical_workflows3.png)

In caso di problemi, è necessario generare e inviare un avviso al gruppo corretto.

Assicurati che ogni operatore abbia un indirizzo e-mail valido.

Qualsiasi flusso di lavoro che deve essere in esecuzione per mantenere la piattaforma funzionante, ad esempio le importazioni giornaliere di dati, deve essere dichiarato come &quot;Produzione&quot; (casella di controllo) e visualizzato in grassetto.

## Elenco di manutenzione del flusso di lavoro {#workflow-maintenance-list}

Tutti i flussi di lavoro tecnici personalizzati devono essere documentati in un foglio di lavoro che contiene:

* Nome e posizione del flusso di lavoro.
* Scopo
* Pianificazione e dipendenze.
* Operatore incaricato del monitoraggio.
* Istruzioni su cosa fare in caso di errore.

![](assets/monitoring_technical_workflows4.png)

## Pianificazione e automazione del monitoraggio {#planning-and-automation-of-monitoring}

La pianificazione del monitoraggio del flusso di lavoro ne migliora l’efficienza. Alcune attività devono essere eseguite quotidianamente, mentre altre possono essere eseguite settimanalmente o mensilmente.

L’impostazione dei flussi di lavoro nelle cartelle denominate da ricorrenza e ordinate in base alla pianificazione dell’esecuzione migliora l’efficienza del monitoraggio.

L&#39;automazione del monitoraggio riduce il sovraccarico delle risorse e assicura che le attività siano pianificate con la frequenza appropriata.

È possibile creare un flusso di lavoro di monitoraggio per inviare un messaggio e-mail ogni volta che determinate attività non riescono o quando una tabella critica diventa troppo grande.

È possibile creare una visualizzazione che consenta di monitorare tutti i flussi di lavoro in un&#39;area funzionale o a livello di sistema.

Puoi anche utilizzare la funzionalità di processo o report di Adobe Campaign per creare la documentazione su richiesta, sempre aggiornata.
