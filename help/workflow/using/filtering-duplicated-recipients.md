---
product: campaign
title: Filtrare i destinatari duplicati
description: Scopri come filtrare i destinatari duplicati
feature: Workflows
hide: true
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
TQID: https://experienceleague.adobe.com/qsfiVfgYUq38VWmh5QEq87-WBwFGrc2iCSeAhjaKXbg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 147
ht-degree: 4%

---

# Filtrare i destinatari duplicati {#filtering-duplicated-recipients}



In questo esempio, vogliamo filtrare i destinatari che compaiono due o più volte in una consegna per recuperare i profili duplicati.

Per creare questo esempio, attieniti alla seguente procedura:

1. Trascinare e rilasciare un&#39;attività **[!UICONTROL Query]** in un flusso di lavoro e aprire l&#39;attività.
1. Fare clic su **[!UICONTROL Edit query]** e impostare la destinazione e le dimensioni filtro su **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definisci la seguente condizione di filtro per eseguire il targeting dei destinatari esistenti nel registro di consegna. Scegliere **Registro recapito destinatari (broadlog)** nella colonna **Espressione**, scegliere **esiste come** nella colonna **Operatore**.

   ![](assets/query_recipients_2.png)

1. Definisci la seguente condizione di filtro per eseguire il targeting della consegna. Scegliere **[!UICONTROL Internal name]** nella colonna Espressione e **[!UICONTROL equal to]** nella colonna Operatore.
1. Nella colonna Valore aggiungi il nome interno della consegna di destinazione.

   ![](assets/query_recipients_3.png)

1. Con un operatore **[!UICONTROL AND]**, ripeti le stesse operazioni per eseguire il targeting di altre consegne.

   ![](assets/query_recipients_4.png)

La transizione in uscita contiene i destinatari duplicati target delle consegne.
