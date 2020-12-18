---
solution: Campaign Classic
product: campaign
title: Caricamento dati (RDBMS)
description: Ulteriori informazioni sull'attività del flusso di lavoro di caricamento dati (RDBMS)
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---


# Caricamento dati (RDBMS){#data-loading-rdbms}

L&#39;attività **[!UICONTROL Data loading (RDBMS)]** consente di accedere direttamente a questo database esterno e di raccogliere solo i dati necessari per il targeting.

Per migliorare le prestazioni, si consiglia di utilizzare l&#39;attività di query (dove è possibile utilizzare i dati di un database esterno). Per ulteriori informazioni, vedere [Accesso a un database esterno (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

L&#39;operazione è la seguente:

1. Selezionare l&#39;origine dati dall&#39;elenco e immettere il nome della tabella che contiene i dati da estrarre.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Il nome della tabella immessa nel campo corrispondente viene utilizzato come modello per la raccolta dei dati nel database esterno. Il nome della tabella elaborata dal flusso di lavoro può essere calcolato o trasmesso dalla transizione in entrata dell&#39;attività di caricamento dei dati. Per selezionare la tabella da utilizzare, fare clic su **[!UICONTROL Advanced..]**. e selezionare l&#39;opzione **[!UICONTROL Specified in the transition]** o **[!UICONTROL Explicit]**.

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Fate clic sul collegamento **[!UICONTROL Select the columns to extract...]** per scegliere i dati da raccogliere nel database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. È possibile definire un filtro per questi dati. A tale scopo, fare clic sul collegamento **[!UICONTROL Edit query....]**.

   I dati raccolti in questo modo possono essere utilizzati per tutto il ciclo di vita del flusso di lavoro.

