---
product: campaign
title: Aggiornamento dell’elenco trimestrale tramite una query incrementale
description: In questo caso d’uso, viene utilizzata una query incrementale per aggiornare automaticamente un elenco di destinatari.
feature: Workflows
exl-id: 0d3e7046-313a-42a6-9155-3365e8d60bac
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 5%

---

# Aggiornamento dell’elenco trimestrale tramite una query incrementale {#quarterly-list-update}

![](../../assets/v7-only.svg)

Nell&#39;esempio seguente, un [query incrementale](incremental-query.md) viene utilizzato per aggiornare automaticamente un elenco di destinatari. Questi destinatari vengono targetizzati come parte di campagne di marketing stagionali.

Poiché queste campagne vengono lanciate all&#39;inizio di ogni stagione per offrire attività sportive rilevanti, queste liste vengono aggiornate ogni trimestre. Tuttavia, un destinatario qui deve essere oggetto di targeting solo una volta ogni 9 mesi da questa campagna. Questo ti consente di definire la frequenza di idoneità del destinatario e di offrire attività per diverse stagioni nel corso degli anni.

![](assets/incremental_query_example.png)

1. Aggiungi una query incrementale e un’attività di aggiornamento elenco in un nuovo flusso di lavoro.
1. Configura le **[!UICONTROL Incremental query]** scheda dell’attività come specificato in [Creare una query](query.md#creating-a-query).
1. Seleziona la **[!UICONTROL Scheduling & History]** e specificare una cronologia di 270 giorni. Un destinatario che è già stato oggetto di targeting non sarà più oggetto di targeting per un periodo di 270 giorni o circa 9 mesi.

   Quindi fai clic sul pulsante **[!UICONTROL Change...]** pulsante .

1. Per verificare che l’elenco venga aggiornato prima dell’inizio di ogni stagione, seleziona **[!UICONTROL Monthly]**.
1. Nella schermata successiva, seleziona Marzo, Giugno, Settembre e Dicembre. Scegli il 20 del mese e l’ora in cui desideri avviare il flusso di lavoro.
1. Selezionare quindi il periodo di validità della query. Ad esempio, se desideri che questa attività sia attiva in modo permanente, seleziona **[!UICONTROL Permanent validity]**.

   ![](assets/incremental_query_example_2.png)

1. Dopo aver approvato la query incrementale, configura l’attività di aggiornamento elenco come spiegato in [Aggiornamento elenco](list-update.md).

Il flusso di lavoro verrà quindi avviato automaticamente immediatamente prima dell’inizio di ogni stagione. L’elenco verrà aggiornato con nuovi destinatari idonei per ricevere le offerte.
