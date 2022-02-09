---
product: campaign
title: Query tramite gestione dei raggruppamenti
description: Scopri come eseguire le query utilizzando la gestione dei raggruppamenti
feature: Query Editor
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# Eseguire query tramite gestione dei raggruppamenti {#querying-using-grouping-management}

![](../../assets/common.svg)

In questo esempio, vogliamo eseguire una query per trovare tutti i domini e-mail con targeting oltre 30 volte durante le consegne precedenti.

* Quale tabella deve essere selezionata?

   Tabella dei destinatari (nms:recipient)

* Campi da selezionare nelle colonne di output?

   Dominio e-mail e chiave primaria (con conteggio)

* Raggruppamento dati?

   Basato sul dominio e-mail con un conteggio di chiavi primarie superiore a 30. Questa operazione viene eseguita con **[!UICONTROL Group by + Having]** opzione . **[!UICONTROL Group by + Having]** consente di raggruppare i dati (&quot;raggruppare per&quot;) e di effettuare una selezione di ciò che è stato raggruppato (&quot;avere&quot;).

Per creare questo esempio, esegui i seguenti passaggi:

1. Apri **[!UICONTROL Generic query editor]** e scegli la tabella Destinatario (**nms:recipient**).

   ![](assets/query_editor_02.png)

1. In **[!UICONTROL Data to extract]** seleziona la finestra **[!UICONTROL Email domain]** e **[!UICONTROL Primary key]** campi. Esegui un conteggio sul **[!UICONTROL Primary key]** campo .

   Per ulteriori informazioni sui conteggi delle chiavi primarie, consulta [questa sezione](../../platform/using/defining-filter-conditions.md#building-expressions).

1. Controlla la **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** scatola.

   ![](assets/query_editor_nveau_29.png)

1. In **[!UICONTROL Sorting]** , ordina i domini e-mail in ordine decrescente. Per eseguire questa operazione, controlla **[!UICONTROL Yes]** in **[!UICONTROL Descending sort]** colonna. Fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_70.png)

1. In **[!UICONTROL Data filtering]**, seleziona **[!UICONTROL Filtering conditions]**. Vai a **[!UICONTROL Target elements]** finestra e fai clic su **[!UICONTROL Next]**.
1. In **[!UICONTROL Data grouping]** seleziona la finestra **[!UICONTROL Email domain]** facendo clic su **[!UICONTROL Add]**.

   Questa finestra di raggruppamento dati viene visualizzata solo se **[!UICONTROL Handle groupings (GROUP BY + HAVING]**).

   ![](assets/query_editor_blocklist_04.png)

1. In **[!UICONTROL Grouping condition]** window, indica un numero di chiavi primarie maggiore di 30, in quanto vogliamo che vengano restituiti come risultati solo i domini e-mail con targeting superiore a 30 volte.

   Questa finestra viene visualizzata quando **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** casella selezionata: in questo caso il risultato del raggruppamento viene filtrato (HAVING).

   ![](assets/query_editor_blocklist_05.png)

1. In **[!UICONTROL Data formatting]** finestra, fai clic su **[!UICONTROL Next]**: non è necessaria alcuna formattazione.
1. Nella finestra di anteprima dati, fai clic su **[!UICONTROL Launch data preview]**: in questo caso, vengono restituiti tre diversi domini e-mail con targeting per più di 30 volte.

   ![](assets/query_editor_blocklist_06.png)
