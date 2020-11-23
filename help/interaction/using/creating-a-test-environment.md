---
solution: Campaign Classic
product: campaign
title: Creazione di un ambiente di test
description: Creazione di un ambiente di test
audience: interaction
content-type: reference
topic-tags: advanced-parameters
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 10%

---


# Creazione di un ambiente di test{#creating-a-test-environment}

Per creare un ambiente di test (modalità sandbox), effettuate le seguenti operazioni:

>[!IMPORTANT]
>
>Utilizzare questo metodo di creazione dell&#39;ambiente solo per gli ambienti di test. In tutti gli altri casi, utilizzate la procedura guidata di mappatura della destinazione. Per ulteriori informazioni, consultate [Creazione di un ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment)di offerte.

1. Avviate  Adobe Campaign Explorer e passate alla directory principale dell&#39;istanza.
1. Fate clic con il pulsante destro del mouse e aggiungete un **[!UICONTROL Generic folder]** oggetto utilizzando i menu a discesa.

   ![](assets/offer_env_creation_001.png)

1. Quindi, passate alla cartella appena creata e aggiungete un **[!UICONTROL Offer environment]** mediante i menu di scelta rapida.

   ![](assets/offer_env_creation_001bis.png)

1. Applicate lo stesso processo per creare sottocartelle ed elementi dell’ambiente.
1. Una volta completati i test e desiderate utilizzare l&#39;ambiente in fase di produzione, duplicate le offerte e gli spazi nell&#39;ambiente di progettazione. (Fare clic con il pulsante destro del mouse > **[!UICONTROL Actions]** > **[!UICONTROL Deploy]** ).

   ![](assets/migration_interaction_5.png)

