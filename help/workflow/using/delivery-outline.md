---
product: campaign
title: Profilo di consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro del profilo di consegna
feature: Workflows, Targeting Activity
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# Profilo di consegna{#delivery-outline}

![](../../assets/v7-only.svg)

La **profilo di consegna** consente di utilizzare una struttura in un flusso di lavoro della campagna. La struttura deve essere stata creata in precedenza nella campagna.

Per ulteriori informazioni sui profili di consegna in Adobe Campaign, consulta questo [sezione](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

Per configurare l’attività, è sufficiente selezionare il profilo desiderato e la data di contatto pianificata. Puoi aggiungere regole di filtro aggiungendo tipologie o regole di tipologia.

## Esempio: Inserimento di un’offerta tramite un profilo di consegna {#example--inserting-an-offer-via-a-delivery-outline}

La **profilo di consegna** L’attività , disponibile nei flussi di lavoro delle campagne, ti consente di presentare offerte a cui si fa riferimento in una struttura di consegna dalla campagna corrente in corso.

>[!NOTE]
>
>La **Interazione** il pacchetto deve essere installato.

1. In un flusso di lavoro, aggiungi un’attività di profilo della consegna prima di aggiungere un’attività di consegna.
1. Nell’attività di struttura della consegna, specifica il profilo da utilizzare.

   Per ulteriori informazioni sulla specifica dei profili di consegna, consulta questo [sezione](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Completa i campi disponibili in base alla consegna.
1. Esistono due casi possibili:

   * Se desideri chiamare il motore di offerta, controlla la **[!UICONTROL Restrict the number of propositions selected]** scatola. Specifica lo spazio di offerta e il numero di proposte da presentare nella consegna.

      Il motore di offerta terrà conto dei fattori di ponderazione e delle regole di idoneità dell’offerta.

   * Se non selezioni la casella , tutte le offerte nel profilo di consegna verranno presentate senza effettuare una chiamata al motore di offerta.

   L’anteprima tiene conto del numero di offerte specificate nella consegna. Quando esegui un flusso di lavoro, viene preso in considerazione il numero specificato nel profilo di consegna.

   ![](assets/int_compo_offre_wf1.png)
