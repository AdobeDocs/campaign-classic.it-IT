---
title: Filtrare i destinatari duplicati
description: Scopri come filtrare i destinatari duplicati
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# Filtrare i destinatari duplicati {#filtering-duplicated-recipients}

In questo esempio, vogliamo filtrare i destinatari che appaiono due o più volte in una consegna per recuperare i profili duplicati.

Per creare questo esempio, procedere come segue:

1. Trascinate e rilasciate un&#39; **[!UICONTROL Query]** attività in un flusso di lavoro e aprite l&#39;attività.
1. Fate clic **[!UICONTROL Edit query]** e impostate le dimensioni di destinazione e di filtro su **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definite la seguente condizione di filtro per il destinatario presente nel registro di consegna. Scegliete il registro di consegna **del destinatario (log di trasmissione)** nella colonna **Espressione** , scegliete **esistente, ad esempio** nella colonna **Operatore** .

   ![](assets/query_recipients_2.png)

1. Definite la seguente condizione di filtro per eseguire il targeting della consegna. Scegliete **[!UICONTROL Internal name]** nella colonna Espressione e **[!UICONTROL equal to]** nella colonna Operatore.
1. Nella colonna Valore, aggiungete il nome interno della consegna di destinazione.

   ![](assets/query_recipients_3.png)

1. Con un **[!UICONTROL AND]** operatore, ripetere le stesse operazioni per altre consegne.

   ![](assets/query_recipients_4.png)

La transizione in uscita contiene i destinatari duplicati assegnati alle consegne.
