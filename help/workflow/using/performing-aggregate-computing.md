---
title: Esecuzione del calcolo aggregato
description: Scopri come eseguire il calcolo aggregato nelle query
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---


# Esecuzione del calcolo aggregato {#performing-aggregate-computing}

In questo esempio, vogliamo contare il numero di destinatari che vivono a Londra, in base al sesso.

* Quale tabella deve essere selezionata?

   Tabella destinatari (**nms:destinatario**)

* Quali campi devono essere selezionati nella colonna di output?

   Chiave primaria (con conteggio) e Sesso

* A quali condizioni vengono filtrate le informazioni?

   Basato sui destinatari che vivono a Londra

Per creare questo esempio, procedere come segue:

1. In **[!UICONTROL Data to extract]**, definite un conteggio per la chiave primaria (come mostrato nell&#39;esempio precedente). Aggiungere il **[!UICONTROL Gender]** campo nella colonna di output. Selezionate l’ **[!UICONTROL Group]** opzione nella **[!UICONTROL Gender]** colonna. In questo modo i destinatari verranno raggruppati per genere.

   ![](assets/query_editor_nveau_27.png)

1. Nella **[!UICONTROL Sorting]** finestra, fate clic su **[!UICONTROL Next]**: qui non è necessario effettuare alcuna selezione.
1. Configurare il filtraggio dei dati. Qui si desidera limitare la selezione ai contatti che vivono a Londra.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >I valori seguono la distinzione tra maiuscole e minuscole. Se il valore &quot;London&quot; viene immesso nella condizione senza lettera maiuscola e l&#39;elenco dei destinatari contiene la parola &quot;London&quot; con una lettera maiuscola, la query non riuscirà.

1. Nella **[!UICONTROL Data formatting]** finestra, fate clic su **[!UICONTROL Next]**: per questo esempio non è richiesta alcuna formattazione.
1. Nella finestra di anteprima, fate clic su **[!UICONTROL Launch data preview]**.

   Esistono tre valori distinti per ciascun ordinamento per genere: **2** per le donne, **1** per i maschi e **0** quando il genere è sconosciuto. In questo esempio, l&#39;elenco contiene 10 donne, 16 uomini e 2 persone il cui sesso non è noto.

   ![](assets/query_editor_agregat_04.png)
