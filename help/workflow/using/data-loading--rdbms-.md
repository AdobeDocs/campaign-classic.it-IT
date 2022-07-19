---
product: campaign
title: Caricamento dati (RDBMS)
description: Ulteriori informazioni sull’attività del flusso di lavoro di caricamento dati (RDBMS)
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# Caricamento dati (RDBMS){#data-loading-rdbms}

![](../../assets/v7-only.svg)

La **[!UICONTROL Data loading (RDBMS)]** activity ti consente di accedere direttamente a questo database esterno e di raccogliere solo i dati necessari per il targeting.

Per migliorare le prestazioni, si consiglia di utilizzare l’attività query (in cui è possibile utilizzare i dati di un database esterno). Per ulteriori informazioni, consulta [Accesso a un database esterno (FDA)](accessing-an-external-database--fda-.md).

Operazione:

1. Selezionare l’origine dati dall’elenco e immettere il nome della tabella contenente i dati da estrarre.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Il nome della tabella immessa nel campo corrispondente viene utilizzato come modello per la raccolta dei dati nel database esterno. Il nome della tabella elaborata dal flusso di lavoro può essere calcolato o veicolato dalla transizione in entrata dell’attività di caricamento dei dati. Per selezionare la tabella da utilizzare, fai clic sul pulsante **[!UICONTROL Advanced..]**. e seleziona la **[!UICONTROL Specified in the transition]** o **[!UICONTROL Explicit]** opzione .

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Fai clic sul pulsante **[!UICONTROL Select the columns to extract...]** collegamento per scegliere i dati da raccogliere nel database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Puoi definire un filtro per questi dati. A questo scopo, fai clic sul pulsante **[!UICONTROL Edit query....]** link.

   I dati raccolti in questo modo possono essere utilizzati per tutto il ciclo di vita del flusso di lavoro.
