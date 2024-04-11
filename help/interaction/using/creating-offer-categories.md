---
product: campaign
title: Creazione di categorie di offerta
description: Creazione di categorie di offerta
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
exl-id: ed97a1b5-c870-4b67-98b6-16adc316fd46
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 0%

---

# Creazione di categorie di offerta{#creating-offer-categories}



La creazione di categorie di offerta può avvenire solo nel **[!UICONTROL Design]** ambiente. Vengono distribuiti automaticamente in **[!UICONTROL Live]** ambiente (ovvero reso disponibile) quando le offerte create/modificate che contengono vengono approvate. Per impostazione predefinita, il **[!UICONTROL Design]** L’ambiente contiene una categoria per ricevere tutte le offerte. È possibile creare sottocategorie per aggiungere una gerarchia alle offerte di catalogo.

Per ogni categoria, puoi definire le date di idoneità, ovvero un periodo oltre il quale le offerte contenute nella categoria non possono più essere presentate al relativo target. Se desideri che le offerte di una categoria specifica vengano selezionate come priorità dal motore delle offerte, ad esempio per esporre meglio un prodotto, puoi aumentarne il peso per un determinato periodo aggiungendo un peso moltiplicatore alla categoria.

Per creare una categoria aggiuntiva, attieniti alla seguente procedura:

1. Vai a **[!UICONTROL Offer catalog]** cartella.

   ![](assets/offer_cat_create_001.png)

1. Fai clic con il pulsante destro del mouse e seleziona (Copia negli Appunti) **[!UICONTROL Create a new "Offer category" folder]** dall’elenco a discesa.

   ![](assets/offer_cat_create_002.png)

1. Rinomina la categoria. Puoi modificare l’etichetta in un secondo momento utilizzando **[!UICONTROL General]** scheda.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Ripeti questi passaggi per creare tutte le categorie necessarie.

   In seguito, se necessario, è possibile:

   * Assegna date di idoneità da **[!UICONTROL Eligibility]** scheda.

     ![](assets/offer_cat_create_004.png)

   * Immetti le parole chiave da utilizzare per selezionare le offerte all’interno di questa categoria, utilizzando **[!UICONTROL Themes]** campo.

     ![](assets/offer_cat_create_005.png)

     >[!NOTE]
     >
     >Quando si richiama il motore di offerta, viene selezionata solo la parte del catalogo in cui i temi o le categorie corrispondono ai parametri.

   * &quot;aumentare&quot; temporaneamente il peso dell’offerta di una categoria per un determinato periodo tramite **[!UICONTROL Multiplier weight]** campo.

     ![](assets/offer_cat_create_006.png)

Nel dashboard delle offerte incluse nella categoria è disponibile un riepilogo delle regole di idoneità. Per visualizzarli, fai clic su **[!UICONTROL Schedule and eligibility rules of the offer]** collegamento.

![](assets/offer_create_006.png)
