---
product: campaign
title: Profilo di consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro Struttura della consegna
feature: Workflows, Targeting Activity
hide: true
hidefromtoc: true
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Profilo di consegna{#delivery-outline}



La **struttura di consegna** ti consente di utilizzare una struttura in un flusso di lavoro della campagna. La struttura deve essere stata creata in precedenza nella campagna.

Per ulteriori informazioni sui profili di consegna in Adobe Campaign, consulta questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Per configurare l’attività, è sufficiente selezionare la struttura desiderata e la data di contatto pianificata. Puoi aggiungere regole di filtro aggiungendo tipologie o regole di tipologia.

## Esempio: inserimento di un’offerta tramite una struttura di consegna {#example--inserting-an-offer-via-a-delivery-outline}

L&#39;attività **struttura consegna**, disponibile nei flussi di lavoro della campagna, consente di presentare le offerte a cui si fa riferimento in una struttura di consegna della campagna corrente in corso.

>[!NOTE]
>
>È necessario installare il pacchetto **Interaction**.

1. In un flusso di lavoro, aggiungi un’attività di struttura della consegna prima di aggiungerla.
1. Nell’attività di struttura della consegna, specifica la struttura da utilizzare.

   Per ulteriori informazioni sulla specifica dei profili di consegna, consulta questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Completa i campi disponibili in base alla consegna.
1. Esistono due casi possibili:

   * Se desideri chiamare il motore di offerta, seleziona la casella **[!UICONTROL Restrict the number of propositions selected]**. Specifica lo spazio dell’offerta e il numero di proposte che verranno presentate nella consegna.

     Il motore di offerta terrà conto dei pesi delle offerte e delle regole di idoneità.

   * Se non selezioni la casella, tutte le offerte nella struttura della consegna verranno presentate senza effettuare una chiamata al motore di offerta.

   L’anteprima prende in considerazione il numero di offerte specificato nella consegna. Durante l’esecuzione di un flusso di lavoro, viene preso in considerazione il numero specificato nella struttura della consegna.

   ![](assets/int_compo_offre_wf1.png)
