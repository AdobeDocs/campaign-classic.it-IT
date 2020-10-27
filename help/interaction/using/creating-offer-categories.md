---
title: Creazione di categorie di offerta
seo-title: Creazione di categorie di offerta
description: Creazione di categorie di offerta
seo-description: null
page-status-flag: never-activated
uuid: 5ac0ae5e-1731-4699-b4ef-f3867ad0ab58
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: managing-an-offer-catalog
discoiquuid: a9fad813-3256-4a00-ba74-7dbaba9e8e23
translation-type: tm+mt
source-git-commit: 8fc3e793ec544948049fc122b44b6bffdebecba0
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 4%

---


# Creazione di categorie di offerta{#creating-offer-categories}

La creazione di categorie di offerte può avvenire solo nell&#39; **[!UICONTROL Design]** ambiente. Vengono distribuiti automaticamente nell&#39; **[!UICONTROL Live]** ambiente (ovvero resi disponibili) quando vengono approvate le offerte create/modificate che contengono. Per impostazione predefinita, l&#39; **[!UICONTROL Design]** ambiente contiene una categoria in cui ricevere tutte le offerte. È possibile creare sottocategorie per aggiungere una gerarchia alle offerte del catalogo.

Per ciascuna categoria, è possibile definire le date di idoneità, ossia un periodo oltre il quale le offerte contenute nella categoria non possono più essere presentate al relativo target. Se desiderate che le offerte di una categoria specifica siano selezionate come priorità dal motore delle offerte, per esporre meglio un prodotto, ad esempio, potete aumentare il loro peso per un dato periodo aggiungendo un peso moltiplicatore alla categoria.

Per creare una categoria aggiuntiva, attenetevi alla seguente procedura:

1. Go to the **[!UICONTROL Offer catalog]** folder.

   ![](assets/offer_cat_create_001.png)

1. Fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL Create a new "Offer category" folder]** dall&#39;elenco a discesa.

   ![](assets/offer_cat_create_002.png)

1. Rinominare la categoria. È possibile modificare l&#39;etichetta in un secondo momento utilizzando la **[!UICONTROL General]** scheda.

   ![](assets/offer_cat_create_003.png)

   >[!NOTE]
   >
   >Ripetete questi passaggi per creare tutte le categorie necessarie.

   Quindi, in base alle esigenze, potete:

   * Assegnare le date di idoneità dalla **[!UICONTROL Eligibility]** scheda.

      ![](assets/offer_cat_create_004.png)

   * Inserite le parole chiave che possono essere utilizzate per selezionare offerte dall&#39;interno di questa categoria, utilizzando il **[!UICONTROL Themes]** campo.

      ![](assets/offer_cat_create_005.png)

      >[!NOTE]
      >
      >Quando si richiama il motore delle offerte, viene selezionata solo la parte del catalogo in cui i temi o le categorie corrispondono ai parametri.

   * &quot;aumentare&quot; temporaneamente il peso dell&#39;offerta di una categoria per un dato periodo attraverso il **[!UICONTROL Multiplier weight]** campo.

      ![](assets/offer_cat_create_006.png)

Nel dashboard delle offerte incluse nella categoria è disponibile un ricap delle regole di idoneità. Per visualizzarli, fate clic sul **[!UICONTROL Schedule and eligibility rules of the offer]** collegamento.

![](assets/offer_create_006.png)

