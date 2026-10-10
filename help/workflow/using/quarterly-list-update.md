---
product: campaign
title: Aggiornamento dell’elenco trimestrale tramite una query incrementale
description: In questo caso d’uso, viene utilizzata una query incrementale per aggiornare automaticamente un elenco di destinatari
feature: Workflows
hide: true
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
TQID: 'https://experienceleague.adobe.com/BH9Rd9DTl5ZnTIo17AS6FKEYio-DjbXiOf0Nn1GLXWI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 5%
---
# Aggiornamento dell’elenco trimestrale tramite una query incrementale {#quarterly-list-update}



Nell&#39;esempio seguente viene utilizzata una [query incrementale](incremental-query.md) per aggiornare automaticamente un elenco di destinatari. Questi destinatari sono destinatari delle campagne di marketing stagionali.

Poiché tali campagne sono lanciate all’inizio di ogni stagione per offrire attività sportive pertinenti, tali elenchi sono aggiornati ogni trimestre. Tuttavia, un destinatario in questo caso deve essere oggetto di targeting solo una volta ogni 9 mesi per questa campagna. Questo ti consente di intervallare la frequenza di idoneità del destinatario e di offrire attività per diverse stagioni nel corso degli anni.

![](assets/incremental_query_example.png)

1. Aggiungi una query incrementale e un’attività di aggiornamento elenco in un nuovo flusso di lavoro.
1. Configura la scheda **[!UICONTROL Incremental query]** dell&#39;attività come specificato in [Crea una query](query.md#creating-a-query).
1. Selezionare la scheda **[!UICONTROL Scheduling & History]** e quindi specificare una cronologia di 270 giorni. Un destinatario che è già stato oggetto di targeting non sarà più oggetto di targeting per un periodo di 270 giorni, o circa 9 mesi.

   Quindi fare clic sul pulsante **[!UICONTROL Change...]**.

1. Per assicurarsi che l&#39;elenco venga aggiornato prima dell&#39;inizio di ogni stagione, selezionare **[!UICONTROL Monthly]**.
1. Nella schermata successiva, selezionare Marzo, Giugno, Settembre e Dicembre. Scegli il 20 del mese e scegli l’ora in cui desideri avviare il flusso di lavoro.
1. Quindi, seleziona il periodo di validità per la query. Ad esempio, se desideri che questa attività sia attiva in modo permanente, seleziona **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Dopo aver approvato la query incrementale, configura l&#39;attività di aggiornamento dell&#39;elenco come descritto in [Aggiornamento elenco](list-update.md).

Il flusso di lavoro verrà quindi avviato automaticamente poco prima dell&#39;inizio di ogni stagione. L’elenco verrà aggiornato con i nuovi destinatari idonei a ricevere le offerte.
