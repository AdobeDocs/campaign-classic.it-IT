---
product: campaign
title: Ambienti di progettazione e Live
description: Ambienti di progettazione e Live
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# Ambienti di progettazione e Live{#live-design-environments}



## Principio di funzionamento {#operating-principle}

L’interazione funziona con due tipi di ambienti di offerta:

* **[!UICONTROL Design]** ambienti di offerta che includono offerte in fase di modifica che possono essere modificate. Queste offerte non sono state sottoposte al ciclo di approvazione e non vengono consegnate ai contatti.
* **[!UICONTROL Live]** ambienti di offerta che includono le offerte approvate quando vengono presentate ai contatti. Le offerte in questo ambiente sono di sola lettura.

![](assets/offer_environments_overview_001.png)

Ogni **[!UICONTROL Design]** l’ambiente è collegato a un **[!UICONTROL Live]** ambiente. Quando un’offerta è completa, il suo contenuto e le relative regole di idoneità sono soggetti a un ciclo di approvazione. Una volta completato il ciclo, l’offerta in questione viene distribuita automaticamente nel **[!UICONTROL Live]** ambiente. Da questo momento, sarà disponibile per la consegna.

Per impostazione predefinita, l’interazione viene fornita con una **[!UICONTROL Design]** ambiente e **[!UICONTROL Live]** ambiente ad esso collegato. Entrambi gli ambienti sono preconfigurati per la destinazione della tabella dei destinatari incorporata.

>[!NOTE]
>
>Per eseguire il targeting di un’altra tabella (tabella dei visitatori per le offerte anonime o una tabella dei destinatari specifica), è necessario utilizzare la procedura guidata di mappatura di destinazione per creare gli ambienti. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

I responsabili delle offerte e i responsabili della consegna hanno accesso a diverse viste dell’ambiente. I responsabili delle consegne possono solo visualizzare **[!UICONTROL Live]** offre un ambiente e utilizza le offerte per distribuirle. I responsabili delle offerte possono visualizzare e modificare **[!UICONTROL Design]** e visualizzare **[!UICONTROL Live]** ambiente. Per ulteriori informazioni, consulta [Profili operatore](../../interaction/using/operator-profiles.md).

## Creazione di un ambiente di offerta {#creating-an-offer-environment}

Per impostazione predefinita, Interaction viene fornito con un ambiente preconfigurato per eseguire il targeting della tabella dei destinatari (offerte identificate). Se desideri eseguire il targeting di un’altra tabella (tabella dei visitatori per le offerte anonime o una tabella dei destinatari specifica), devi applicare le seguenti configurazioni:

1. Posizionare il cursore sul **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** nodo. Fai clic con il pulsante destro del mouse sulla mappatura di consegna che desideri utilizzare (**[!UICONTROL Visitors]** se desideri utilizzare le offerte anonime) e seleziona **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Clic **[!UICONTROL Next]** per passare alla schermata successiva della procedura guidata, selezionare **[!UICONTROL Generate a storage schema for propositions]** e fai clic su **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Se la casella è già selezionata, deselezionarla e ricontrollarla.

1. Adobe Campaign crea due ambienti (**[!UICONTROL Design]** e **[!UICONTROL Live]** ) con informazioni di targeting dalla mappatura target precedentemente abilitata. L’ambiente è preconfigurato con le informazioni di targeting.

   Se ha attivato **[!UICONTROL Visitor]** mappatura, **[!UICONTROL Environment dedicated to incoming anonymous interactions]** viene selezionata automaticamente nel file **[!UICONTROL General]** scheda.

   Questa opzione consente di attivare funzioni specifiche di interazione anonima, in particolare durante la configurazione degli spazi dell’offerta dell’ambiente. Puoi anche configurare le opzioni che ti consentono di passare da un ambiente &quot;identificato&quot; a un ambiente &quot;anonimo&quot;.

   Ad esempio, puoi collegare uno spazio dell’offerta in un ambiente destinatario (contatto identificato) con uno spazio dell’offerta che corrisponda a un ambiente visitatore (contatto non identificato). In questo modo, al contatto saranno rese disponibili offerte diverse a seconda che il contatto sia stato identificato o meno. Per ulteriori informazioni, consulta [Creazione di spazi dell’offerta](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Per ulteriori informazioni sulle interazioni anonime su un canale in entrata, consulta [Interazioni anonime](../../interaction/using/anonymous-interactions.md).
