---
product: campaign
title: Best practice e limitazioni dell’FDA di Campaign
description: Scopri le best practice e le limitazioni quando lavori con un database esterno (FDA)
audience: platform
content-type: reference
topic-tags: connectors
exl-id: f3980859-2837-416b-a0ef-2b369d2d50bd
source-git-commit: 1312f7c319c96851bc83ae21501164e2688d0dff
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 7%

---

# Best practice e limitazioni

## Ottimizzazione della personalizzazione delle e-mail con dati esterni {#optimizing-email-personalization-with-external-data}

Puoi preelaborare la personalizzazione dei messaggi in un flusso di lavoro dedicato. Per eseguire questa operazione, utilizza l’opzione **[!UICONTROL Prepare the personalization data with a workflow]** , disponibile nella scheda **[!UICONTROL Analysis]** delle proprietà di consegna.

Durante l’analisi della consegna, questa opzione crea ed esegue automaticamente un flusso di lavoro che memorizza in una tabella temporanea tutti i dati collegati alla destinazione, inclusi i dati provenienti da tabelle collegate in un database esterno.

Questa opzione migliora notevolmente le prestazioni durante l’esecuzione del passaggio di personalizzazione.

## Utilizzare i dati di un database esterno in un flusso di lavoro {#using-data-from-an-external-database-in-a-workflow}

In più attività del flusso di lavoro Adobe Campaign, puoi utilizzare i dati memorizzati in un database esterno.

* **Filtrare i dati esterni**  - La  [](../../workflow/using/targeting-data.md#selecting-data) Queryactivity ti consente di aggiungere dati esterni e di utilizzarli nelle configurazioni di filtro definite. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/targeting-data.md#selecting-data).

* **Crea sottoinsiemi** : consente di creare sottoinsiemi  [](../../workflow/using/split.md) Splitactivity. Puoi utilizzare dati esterni per definire i criteri di filtro da utilizzare. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/split.md).

* **Carica database esterno** : è possibile utilizzare i dati esterni nell&#39;attività di caricamento  [dati](../../workflow/using/data-loading--rdbms-.md)  (RDBMS). Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/data-loading--rdbms-.md).

* **Aggiunta di informazioni e collegamenti**  - L’attività  [](../../workflow/using/enrichment.md) Enrichmentactivity ti consente di aggiungere dati aggiuntivi alla tabella di lavoro del flusso di lavoro e collegamenti a una tabella esterna. In questo contesto, può utilizzare dati provenienti da un database esterno. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/enrichment.md).

## Limiti FDA {#limitations}

L’opzione FDA viene eseguita per manipolare i dati in database esterni in modalità batch nei flussi di lavoro. Per evitare problemi di prestazioni, si sconsiglia di utilizzare il modulo FDA nel contesto di operazioni unitarie, ad esempio: personalizzazione, interazione, messaggistica in tempo reale, ecc.

Evita le operazioni che devono utilizzare il più possibile sia Adobe Campaign che il database esterno. A questo scopo, puoi:

* Esporta il database Adobe Campaign nel database esterno ed esegui le operazioni solo dal database esterno prima di reimportare i risultati in Adobe Campaign.

* Raccogli i dati dal database Adobe Campaign esterno ed esegui le operazioni localmente.

Se desideri eseguire la personalizzazione nelle consegne utilizzando i dati del database esterno, raccogli i dati da utilizzare in un flusso di lavoro per renderli disponibili in una tabella temporanea. Quindi utilizza i dati della tabella temporanea per personalizzare la consegna.

L’opzione FDA è soggetta alle limitazioni del sistema di database esterno utilizzato.
