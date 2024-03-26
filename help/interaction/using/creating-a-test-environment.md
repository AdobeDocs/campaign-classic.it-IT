---
product: campaign
title: Creazione di un ambiente di test
description: Creazione di un ambiente di test
feature: Interaction, Offers
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 5%

---

# Creazione di un ambiente di test{#creating-a-test-environment}



Per creare un ambiente di test (modalità sandbox), effettua le seguenti operazioni:

>[!IMPORTANT]
>
>Utilizza questo metodo di creazione dell’ambiente solo per gli ambienti di test. In tutti gli altri casi, utilizza la procedura guidata di mappatura di destinazione. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Avvia Adobe Campaign Explorer e passa alla directory principale dell’istanza.
1. Fai clic con il pulsante destro del mouse e aggiungi un **[!UICONTROL Generic folder]** utilizzando i menu a discesa.

   ![](assets/offer_env_creation_001.png)

1. Quindi, vai alla cartella appena creata e aggiungi un **[!UICONTROL Offer environment]** utilizzando i menu di scelta rapida.

   ![](assets/offer_env_creation_001bis.png)

1. Applica lo stesso processo per creare sottocartelle ed elementi dell’ambiente.
1. Una volta completati i test e desideri utilizzare l’ambiente in produzione, duplica le offerte e gli spazi nell’ambiente di progettazione. (Clic con il pulsante destro del mouse > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)
