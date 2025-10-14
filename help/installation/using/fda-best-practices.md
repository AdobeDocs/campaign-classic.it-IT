---
product: campaign
title: Best practice e limitazioni dell’FDA per Campaign
description: Scopri le best practice e le limitazioni nell’utilizzo di un database esterno (FDA)
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 1%

---

# Best practice e limitazioni



## Ottimizzare la personalizzazione delle e-mail con dati esterni {#optimizing-email-personalization-with-external-data}

Puoi pre-elaborare la personalizzazione dei messaggi in un flusso di lavoro dedicato. Per eseguire questa operazione, utilizza l&#39;opzione **[!UICONTROL Prepare the personalization data with a workflow]**, disponibile nella scheda **[!UICONTROL Analysis]** delle proprietà di consegna.

Durante l’analisi della consegna, questa opzione crea ed esegue automaticamente un flusso di lavoro che memorizza tutti i dati collegati alla destinazione in una tabella temporanea, inclusi i dati di tabelle collegate in un database esterno.

Questa opzione migliora notevolmente le prestazioni durante l’esecuzione del passaggio di personalizzazione.

## Utilizzare dati da un database esterno in un flusso di lavoro {#using-data-from-an-external-database-in-a-workflow}

In più attività del flusso di lavoro di Adobe Campaign, puoi utilizzare i dati memorizzati in un database esterno.

* **Filtro su dati esterni** - L&#39;attività Query ti consente di aggiungere dati esterni e di utilizzarli nelle configurazioni di filtro definite. Per ulteriori informazioni, consulta la [documentazione di Campaign v8]https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/wf-type/targeting-workflows.html){target="_blank"}.

* **Crea sottoinsiemi** - L&#39;attività di suddivisione consente di creare sottoinsiemi. Puoi utilizzare dati esterni per definire i criteri di filtro da utilizzare. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/split.html){target="_blank"}.

* **Carica database esterno** - Puoi utilizzare i dati esterni nell&#39;attività di caricamento dati (RDBMS). Ulteriori informazioni sono disponibili nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/action-activities/data-loading-rdbms.html){target="_blank"}.

* **Aggiunta di informazioni e collegamenti** - L&#39;attività Enrichment consente di aggiungere dati aggiuntivi alla tabella di lavoro del flusso di lavoro e collegamenti a una tabella esterna. In questo contesto, può utilizzare dati provenienti da un database esterno. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/enrichment.html){target="_blank"}.

## Guardrail e limitazioni {#fda-limitations}

L’opzione FDA è progettata per manipolare i dati nei database esterni in modalità batch nei flussi di lavoro. Per evitare problemi di prestazioni, si sconsiglia di utilizzare il modulo FDA nel contesto di operazioni unitarie, come: personalizzazione, interazione, messaggistica in tempo reale, ecc.

Il targeting dei dati da un database e il filtraggio dei risultati tramite una dimensione di filtro che appartiene a un altro database non è supportato. Non è possibile eseguire il join di tabelle che si trovano su origini dati diverse in una query. Puoi superare questo limite utilizzando altre attività del flusso di lavoro, ad esempio Modifica dimensione.

Evita le operazioni che devono utilizzare il più possibile sia Adobe Campaign che il database esterno. Si consiglia di:

* Esporta il database di Adobe Campaign nel database esterno ed esegui le operazioni solo dal database esterno prima di reimportare i risultati in Adobe Campaign.

* Raccogli i dati dal database esterno di Adobe Campaign ed esegui le operazioni localmente.

Se desideri eseguire la personalizzazione nelle consegne utilizzando i dati del database esterno, raccogli i dati da utilizzare in un flusso di lavoro per renderli disponibili in una tabella temporanea. Quindi utilizza i dati della tabella temporanea per personalizzare la consegna.

L’opzione FDA è soggetta alle limitazioni del sistema di database esterno utilizzato.
