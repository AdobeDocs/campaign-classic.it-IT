---
product: campaign
title: Esecuzione del calcolo aggregato
description: Scopri come eseguire il calcolo aggregato nelle query
feature: Workflows
hide: true
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
TQID: 'https://experienceleague.adobe.com/hr3jxs4JCrcPXdGBGN8I9edBG4FIg1AakOmWaN-Zplk'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%
---
# Esecuzione del calcolo aggregato {#performing-aggregate-computing}



In questo esempio, vogliamo contare il numero di destinatari che vivono a Londra, in base al genere.

* Quale tabella deve essere selezionata?

  Tabella dei destinatari (**nms:recipient**)

* Quali campi devono essere selezionati nella colonna di output?

  Chiave primaria (con conteggio) e genere

* Su quali condizioni vengono filtrate le informazioni?

  In base ai destinatari che vivono a Londra

Per creare questo esempio, attieniti alla seguente procedura:

1. In **[!UICONTROL Data to extract]**, definire un conteggio per la chiave primaria (come illustrato nell&#39;esempio precedente). Aggiungi il campo **[!UICONTROL Gender]** nella colonna di output. Selezionare l&#39;opzione **[!UICONTROL Group]** nella colonna **[!UICONTROL Gender]**. In questo modo i destinatari saranno raggruppati per genere.

   ![](assets/query_editor_nveau_27.png)

1. Nella finestra **[!UICONTROL Sorting]**, fare clic su **[!UICONTROL Next]**: non è necessario alcun ordinamento.
1. Configura il filtro dei dati. In questo caso, si desidera limitare la selezione ai contatti che risiedono a Londra.

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >I valori fanno distinzione tra maiuscole e minuscole. Se il valore &quot;Londra&quot; viene immesso nella condizione senza una lettera maiuscola e l’elenco dei destinatari contiene la parola &quot;Londra&quot; con una lettera maiuscola, la query avrà esito negativo.

1. Nella finestra **[!UICONTROL Data formatting]**, fare clic su **[!UICONTROL Next]**: nessuna formattazione richiesta per questo esempio.
1. Nella finestra di anteprima, fare clic su **[!UICONTROL Launch data preview]**.

   Esistono tre valori distinti per ogni ordinamento in base al sesso: **2** per la donna, **1** per il maschio e **0** quando il genere è sconosciuto. In questo esempio, l&#39;elenco contiene 10 donne, 16 uomini e 2 persone il cui genere non è noto.

   ![](assets/query_editor_agregat_04.png)
