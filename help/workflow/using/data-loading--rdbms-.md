---
title: Caricamento dati (RDBMS)
seo-title: Caricamento dati (RDBMS)
description: Caricamento dati (RDBMS)
seo-description: null
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 6%

---


# Caricamento dati (RDBMS){#data-loading-rdbms}

L&#39; **[!UICONTROL Data loading (RDBMS)]** attività consente di accedere direttamente a questo database esterno e di raccogliere solo i dati necessari per il targeting.

Per migliorare le prestazioni, si consiglia di utilizzare l&#39;attività di query (dove è possibile utilizzare i dati di un database esterno). Per ulteriori informazioni, vedere [Accesso a un database esterno (FDA)](../../workflow/using/accessing-an-external-database--fda-.md).

L&#39;operazione è la seguente:

1. Selezionare l&#39;origine dati dall&#39;elenco e immettere il nome della tabella che contiene i dati da estrarre.

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   Il nome della tabella immessa nel campo corrispondente viene utilizzato come modello per la raccolta dei dati nel database esterno. Il nome della tabella elaborata dal flusso di lavoro può essere calcolato o trasmesso dalla transizione in entrata dell&#39;attività di caricamento dei dati. Per selezionare la tabella da utilizzare, fare clic su **[!UICONTROL Advanced..]**. e selezionate l&#39; **[!UICONTROL Specified in the transition]** opzione o **[!UICONTROL Explicit]** .

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. Fate clic sul **[!UICONTROL Select the columns to extract...]** collegamento per scegliere i dati da raccogliere nel database.

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. È possibile definire un filtro per questi dati. A tale scopo, fare clic sul **[!UICONTROL Edit query....]** collegamento.

   I dati raccolti in questo modo possono essere utilizzati per tutto il ciclo di vita del flusso di lavoro.

