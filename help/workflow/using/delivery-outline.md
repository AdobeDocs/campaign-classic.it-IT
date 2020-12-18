---
solution: Campaign Classic
product: campaign
title: Profilo di consegna
description: Ulteriori informazioni sull'attività del flusso di lavoro del profilo di distribuzione
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---


# Profilo di consegna{#delivery-outline}

Il **profilo di consegna** consente di utilizzare un profilo in un flusso di lavoro della campagna. Il profilo deve essere stato creato in precedenza nella campagna.

Per ulteriori informazioni sui contorni di consegna in  Adobe Campaign, fare riferimento a questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Per configurare l&#39;attività, è sufficiente selezionare il profilo desiderato e la data di contatto prevista. Potete aggiungere regole di filtro aggiungendo tipologie o regole di tipologia.

## Esempio: Inserimento di un&#39;offerta tramite un profilo di consegna {#example--inserting-an-offer-via-a-delivery-outline}

L&#39;attività **consegna struttura**, disponibile nei flussi di lavoro della campagna, consente di presentare offerte alle quali viene fatto riferimento in una struttura di consegna dalla campagna corrente in corso.

>[!NOTE]
>
>È necessario installare il pacchetto **Interaction**.

1. In un flusso di lavoro, aggiungete un&#39;attività di struttura della consegna prima di aggiungere un&#39;attività di consegna.
1. Nell&#39;attività del profilo di consegna, specificate il profilo da utilizzare.

   Per ulteriori informazioni sulla specifica dei contorni di consegna, fare riferimento a questa sezione [](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Completa i campi disponibili in base alla consegna.
1. Esistono due casi possibili:

   * Se desiderate chiamare il motore delle offerte, selezionate la casella **[!UICONTROL Restrict the number of propositions selected]**. Specificate lo spazio dell&#39;offerta e il numero di proposte che verranno presentate nella consegna.

      I pesi delle offerte e le regole di ammissibilità saranno prese in considerazione dal motore delle offerte.

   * Se non selezionate la casella, tutte le offerte nel profilo di consegna verranno presentate senza effettuare una chiamata al motore delle offerte.

   L&#39;anteprima tiene conto del numero di offerte specificate nella consegna. Quando si esegue un flusso di lavoro, viene preso in considerazione il numero specificato nel profilo di consegna.

   ![](assets/int_compo_offre_wf1.png)

