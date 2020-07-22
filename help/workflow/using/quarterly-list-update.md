---
title: Aggiornamento dell'elenco trimestrale tramite una query incrementale
description: In questo caso d'uso, viene utilizzata una query incrementale per aggiornare automaticamente un elenco di destinatari.
page-status-flag: never-activated
uuid: 24d322e8-172c-4faa-8a1f-59085b390a76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 31071cd2-7d97-4a4f-a6cc-5ac5b6178be5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aa192d975a08246ba684940fff3d33853d7d9345
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# Aggiornamento dell&#39;elenco trimestrale tramite una query incrementale {#quarterly-list-update}

Nell&#39;esempio seguente, una query [](../../workflow/using/incremental-query.md) incrementale viene utilizzata per aggiornare automaticamente un elenco di destinatari. Questi destinatari vengono indirizzati come parte di campagne di marketing stagionali.

Poiché queste campagne vengono lanciate all&#39;inizio di ogni stagione per offrire attività sportive rilevanti, queste liste vengono aggiornate ogni trimestre. Tuttavia, un destinatario deve essere selezionato solo una volta ogni 9 mesi da questa campagna. Questo consente di definire la frequenza di ammissibilità del destinatario e di offrire attività per diverse stagioni nel corso degli anni.

![](assets/incremental_query_example.png)

1. Aggiungi una query incrementale e un&#39;attività di aggiornamento elenco in un nuovo flusso di lavoro.
1. Configurate la **[!UICONTROL Incremental query]** scheda dell&#39;attività come specificato in [Creazione di una query](../../workflow/using/query.md#creating-a-query).
1. Selezionate la **[!UICONTROL Scheduling & History]** scheda e specificate una cronologia di 270 giorni. Un destinatario che è già stato preso di mira non sarà più destinato per un periodo di 270 giorni, o circa 9 mesi.

   Then click the **[!UICONTROL Change...]** button.

1. Per fare in modo che l&#39;elenco venga aggiornato prima dell&#39;inizio di ogni stagione, selezionare **[!UICONTROL Monthly]**.
1. Nella schermata successiva, selezionate Marzo, Giugno, Settembre e Dicembre. Scegliete il 20 del mese e l’ora di avvio del flusso di lavoro.
1. Selezionare quindi il periodo di validità della query. Ad esempio, se desiderate che l&#39;attività sia attiva in modo permanente, selezionate **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Dopo aver approvato la query incrementale, configurate l&#39;attività di aggiornamento dell&#39;elenco come descritto in Aggiornamento [](../../workflow/using/list-update.md)elenco.

Il flusso di lavoro verrà quindi avviato automaticamente subito prima dell&#39;inizio di ogni stagione. L&#39;elenco verrà aggiornato con nuovi destinatari idonei che riceveranno le offerte.
