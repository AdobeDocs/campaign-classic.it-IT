---
product: campaign
title: Caricamento dati (RDBMS)
description: Ulteriori informazioni sull’attività del flusso di lavoro Caricamento dati (RDBMS)
feature: Workflows, Data Management Activity
hide: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
TQID: https://experienceleague.adobe.com/w7MFQZpUw-a0SIp634sptKz2VKm2MTZisjmN3VLDt2g
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
topic_v2:
  - id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 187
ht-degree: 3%

---

# Caricamento dati (RDBMS){#data-loading-rdbms}



L&#39;attività **[!UICONTROL Data loading (RDBMS)]** ti consente di accedere direttamente a questo database esterno e di raccogliere solo i dati necessari per il targeting.

Per migliorare le prestazioni, è consigliabile utilizzare l’attività di query, in cui è possibile utilizzare i dati di un database esterno. Per ulteriori informazioni, vedere [Accesso a un database esterno (FDA)](accessing-an-external-database-fda.md).

Il funzionamento è il seguente:

1. Selezionare l&#39;origine dati dall&#39;elenco e immettere il nome della tabella contenente i dati da estrarre.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Il nome della tabella immesso nel campo corrispondente viene utilizzato come modello per la raccolta dei dati nel database esterno. Il nome della tabella elaborata dal flusso di lavoro può essere calcolato o trasmesso dalla transizione in entrata dell’attività di caricamento dei dati. Per selezionare la tabella da utilizzare, fare clic su **[!UICONTROL Advanced..]**. collegare e selezionare l&#39;opzione **[!UICONTROL Specified in the transition]** o **[!UICONTROL Explicit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Fare clic sul collegamento **[!UICONTROL Select the columns to extract...]** per scegliere i dati da raccogliere nel database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. Puoi definire un filtro per questi dati. A tale scopo, fare clic sul collegamento **[!UICONTROL Edit query....]**.

   I dati raccolti in questo modo possono essere utilizzati in tutto il ciclo di vita del flusso di lavoro.
