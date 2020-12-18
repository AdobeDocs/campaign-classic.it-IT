---
solution: Campaign Classic
product: campaign
title: Query tramite gestione dei raggruppamenti
description: Scopri come eseguire query utilizzando la gestione dei gruppi
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---


# Query tramite gestione dei raggruppamenti {#querying-using-grouping-management}

In questo esempio, vogliamo eseguire una query per trovare tutti i domini e-mail con targeting più di 30 volte durante le consegne precedenti.

* Quale tabella deve essere selezionata?

   Tabella destinatari (nms:destinatario)

* Campi da selezionare nelle colonne di output?

   Dominio e chiave primaria e di posta elettronica (con conteggio)

* Raggruppamento dati?

   Basato sul dominio e-mail con un numero di chiavi primarie superiore a 30. Questa operazione viene eseguita con l&#39;opzione **[!UICONTROL Group by + Having]**. **[!UICONTROL Group by + Having]** consente di raggruppare i dati (&quot;raggruppare per&quot;) e di selezionare il gruppo (&quot;avere&quot;).

Per creare questo esempio, procedere come segue:

1. Aprite la **[!UICONTROL Generic query editor]** e scegliete la tabella Destinatario (**nms:destinatario**).

   ![](assets/query_editor_02.png)

1. Nella finestra **[!UICONTROL Data to extract]**, selezionare i campi **[!UICONTROL Email domain]** e **[!UICONTROL Primary key]**. Eseguire un conteggio sul campo **[!UICONTROL Primary key]**.

   Per ulteriori informazioni sui conteggi delle chiavi primarie, consultare [questa sezione](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Selezionare la casella **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**.

   ![](assets/query_editor_nveau_29.png)

1. Nella finestra **[!UICONTROL Sorting]**, ordinate i domini e-mail in ordine decrescente. A questo scopo, selezionare **[!UICONTROL Yes]** nella colonna **[!UICONTROL Descending sort]**. Fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. In **[!UICONTROL Data filtering]**, seleziona **[!UICONTROL Filtering conditions]**. Passare alla finestra **[!UICONTROL Target elements]** e fare clic su **[!UICONTROL Next]**.
1. Nella finestra **[!UICONTROL Data grouping]**, selezionare **[!UICONTROL Email domain]** facendo clic su **[!UICONTROL Add]**.

   Questa finestra di raggruppamento dei dati viene visualizzata solo se la casella **[!UICONTROL Handle groupings (GROUP BY + HAVING]**) è stata selezionata.

   ![](assets/query_editor_blocklist_04.png)

1. Nella finestra **[!UICONTROL Grouping condition]**, indicate un numero di chiavi primarie superiore a 30, in quanto desideriamo che vengano restituiti come risultati solo i domini e-mail con targeting superiore a 30 volte.

   Questa finestra viene visualizzata quando la casella **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** è stata selezionata: in questo caso il risultato del raggruppamento viene filtrato (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. Nella finestra **[!UICONTROL Data formatting]**, fare clic su **[!UICONTROL Next]**: qui non è necessaria alcuna formattazione.
1. Nella finestra di anteprima dei dati, fare clic su **[!UICONTROL Launch data preview]**: qui vengono restituiti tre diversi domini e-mail con targeting superiore a 30 volte.

   ![](assets/query_editor_blocklist_06.png)
