---
product: campaign
title: Caricamento dati (RDBMS)
description: Ulteriori informazioni sull’attività del flusso di lavoro Caricamento dati (RDBMS)
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 6%

---

# Caricamento dati (RDBMS){#data-loading-rdbms}



Il **[!UICONTROL Data loading (RDBMS)]** attività consente di accedere direttamente a questo database esterno e di raccogliere solo i dati necessari per il targeting.

Per migliorare le prestazioni, è consigliabile utilizzare l’attività di query, in cui è possibile utilizzare i dati di un database esterno. Per ulteriori informazioni, consulta [Accesso a un database esterno (FDA)](accessing-an-external-database-fda.md).

Il funzionamento è il seguente:

1. Selezionare l&#39;origine dati dall&#39;elenco e immettere il nome della tabella contenente i dati da estrarre.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Il nome della tabella immesso nel campo corrispondente viene utilizzato come modello per la raccolta dei dati nel database esterno. Il nome della tabella elaborata dal flusso di lavoro può essere calcolato o trasmesso dalla transizione in entrata dell’attività di caricamento dei dati. Per selezionare la tabella da utilizzare, fare clic su **[!UICONTROL Advanced..]**. collega e seleziona la **[!UICONTROL Specified in the transition]** o **[!UICONTROL Explicit]** opzione.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Fai clic su **[!UICONTROL Select the columns to extract...]** per scegliere i dati da raccogliere nel database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Puoi definire un filtro per questi dati. A questo scopo, fai clic su **[!UICONTROL Edit query....]** collegamento.

   I dati raccolti in questo modo possono essere utilizzati in tutto il ciclo di vita del flusso di lavoro.
