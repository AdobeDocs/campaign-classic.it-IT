---
product: campaign
title: Creazione di un ambiente di test
description: Creazione di un ambiente di test
audience: interaction
content-type: reference
topic-tags: advanced-parameters
exl-id: 49ac279b-bc67-4311-b0a4-0e23f2a99c52
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 10%

---

# Creazione di un ambiente di test{#creating-a-test-environment}

![](../../assets/v7-only.svg)

Per creare un ambiente di test (modalità sandbox), effettua le seguenti operazioni:

>[!IMPORTANT]
>
>Utilizza questo metodo di creazione dell’ambiente solo per gli ambienti di test. In tutti gli altri casi, utilizza la procedura guidata di mappatura di destinazione. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).

1. Avvia Adobe Campaign Explorer e passa alla directory principale dell&#39;istanza.
1. Fai clic con il pulsante destro del mouse e aggiungi un **[!UICONTROL Generic folder]** utilizzando i menu a discesa.

   ![](assets/offer_env_creation_001.png)

1. Quindi, vai alla cartella appena creata e aggiungi un **[!UICONTROL Offer environment]** utilizzando i menu di scelta rapida.

   ![](assets/offer_env_creation_001bis.png)

1. Applica lo stesso processo per creare le sottocartelle ed elementi dell’ambiente.
1. Al termine dei test e quando desideri utilizzare l’ambiente di produzione, duplica le offerte e gli spazi nell’ambiente di progettazione. (Clic con il pulsante destro del mouse > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)
