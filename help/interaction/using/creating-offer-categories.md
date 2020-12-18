---
solution: Campaign Classic
product: campaign
title: Creazione di categorie di offerta
description: Creazione di categorie di offerta
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Creazione di categorie di offerta{#creating-offer-categories}

La creazione di categorie di offerte può avvenire solo nell&#39;ambiente **[!UICONTROL Design]**. Vengono distribuiti automaticamente nell&#39;ambiente **[!UICONTROL Live]** (ovvero resi disponibili) quando vengono approvate le offerte create/modificate che contengono. Per impostazione predefinita, l&#39;ambiente **[!UICONTROL Design]** contiene una categoria in cui ricevere tutte le offerte. È possibile creare sottocategorie per aggiungere una gerarchia alle offerte del catalogo.

Per ciascuna categoria, è possibile definire le date di idoneità, ossia un periodo oltre il quale le offerte contenute nella categoria non possono più essere presentate al relativo target. Se desiderate che le offerte di una categoria specifica siano selezionate come priorità dal motore delle offerte, per esporre meglio un prodotto, ad esempio, potete aumentare il loro peso per un dato periodo aggiungendo un peso moltiplicatore alla categoria.

Per creare una categoria aggiuntiva, attenetevi alla seguente procedura:

1. Andate alla cartella **[!UICONTROL Offer catalog]**.

   ![](assets/offer_cat_create_001.png)

1. Fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL Create a new "Offer category" folder]** dall&#39;elenco a discesa.

   ![](assets/offer_cat_create_002.png)

1. Rinominare la categoria. È possibile modificare l&#39;etichetta in un secondo momento utilizzando la scheda **[!UICONTROL General]**.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Ripetete questi passaggi per creare tutte le categorie necessarie.

   Quindi, in base alle esigenze, potete:

   * Assegnare le date di idoneità dalla scheda **[!UICONTROL Eligibility]**.

      ![](assets/offer_cat_create_004.png)

   * Immettete le parole chiave che possono essere utilizzate per selezionare le offerte dall&#39;interno di questa categoria, utilizzando il campo **[!UICONTROL Themes]**.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Quando si richiama il motore delle offerte, viene selezionata solo la parte del catalogo in cui i temi o le categorie corrispondono ai parametri.

   * &quot;Aumenta&quot; temporaneamente il peso dell&#39;offerta di una categoria per un dato periodo tramite il campo **[!UICONTROL Multiplier weight]**.

      ![](assets/offer_cat_create_006.png)

Nel dashboard delle offerte incluse nella categoria è disponibile un ricap delle regole di idoneità. Per visualizzarli, fate clic sul collegamento **[!UICONTROL Schedule and eligibility rules of the offer]**.

![](assets/offer_create_006.png)

