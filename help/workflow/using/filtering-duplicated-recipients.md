---
solution: Campaign Classic
product: campaign
title: Filtraggio dei destinatari duplicati
description: Scopri come filtrare i destinatari duplicati
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---


# Filtraggio dei destinatari duplicati {#filtering-duplicated-recipients}

In questo esempio, vogliamo filtrare i destinatari che appaiono due o più volte in una consegna per recuperare i profili duplicati.

Per creare questo esempio, procedere come segue:

1. Trascinate e rilasciate un&#39;attività **[!UICONTROL Query]** in un flusso di lavoro e aprite l&#39;attività.
1. Fare clic su **[!UICONTROL Edit query]** e impostare le dimensioni di destinazione e filtro su **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definite la seguente condizione di filtro per il destinatario presente nel registro di consegna. Scegliete **Registro consegna destinatari (log di trasmissione)** nella colonna **Espressione**, scegliete **esiste come** nella colonna **Operatore**.

   ![](assets/query_recipients_2.png)

1. Definite la seguente condizione di filtro per eseguire il targeting della consegna. Scegliete **[!UICONTROL Internal name]** nella colonna Espressione e **[!UICONTROL equal to]** nella colonna Operatore.
1. Nella colonna Valore, aggiungete il nome interno della consegna di destinazione.

   ![](assets/query_recipients_3.png)

1. Con un operatore **[!UICONTROL AND]**, ripetere le stesse operazioni per altre consegne.

   ![](assets/query_recipients_4.png)

La transizione in uscita contiene i destinatari duplicati assegnati alle consegne.
