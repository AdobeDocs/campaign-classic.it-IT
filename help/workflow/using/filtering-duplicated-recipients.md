---
product: campaign
title: Filtraggio dei destinatari duplicati
description: Scopri come filtrare i destinatari duplicati
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 7cbabbae-375f-4336-9afa-6356f37a79d0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 4%

---

# Filtraggio dei destinatari duplicati {#filtering-duplicated-recipients}

![](../../assets/common.svg)

In questo esempio, vogliamo filtrare i destinatari che vengono visualizzati due o più volte in una consegna per recuperare i profili duplicati.

Per creare questo esempio, esegui i seguenti passaggi:

1. Trascina e rilascia un’attività **[!UICONTROL Query]** in un flusso di lavoro e apri l’attività.
1. Fai clic su **[!UICONTROL Edit query]** e imposta le dimensioni di destinazione e filtro su **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Definisci la seguente condizione di filtro per indirizzare il destinatario che esiste nel registro di consegna. Scegli **Registro consegne destinatario (broadlog)** nella colonna **Espressione** , scegli **esiste come** nella colonna **Operatore** .

   ![](assets/query_recipients_2.png)

1. Definisci la seguente condizione di filtro per eseguire il targeting della consegna. Scegli **[!UICONTROL Internal name]** nella colonna Espressione e **[!UICONTROL equal to]** nella colonna Operatore .
1. Nella colonna del valore , aggiungi il nome interno della consegna di destinazione.

   ![](assets/query_recipients_3.png)

1. Con un operatore **[!UICONTROL AND]** , ripeti le stesse operazioni per eseguire il targeting di altre consegne.

   ![](assets/query_recipients_4.png)

La transizione in uscita contiene i destinatari duplicati interessati nelle consegne.
