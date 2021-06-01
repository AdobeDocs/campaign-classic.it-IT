---
product: campaign
title: Ambienti di progettazione e Live
description: Ambienti di progettazione e Live
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---

# Ambienti di progettazione e Live{#live-design-environments}

## Principio di funzionamento {#operating-principle}

L’interazione funziona con due tipi di ambienti di offerta:

* **[!UICONTROL Design]** ambienti di offerte che includono offerte in fase di modifica e che possono essere modificate. Queste offerte non hanno superato il ciclo di approvazione e non vengono consegnate ai contatti.
* **[!UICONTROL Live]** gli ambienti di offerte che includono offerte approvate mentre vengono presentate ai contatti. Le offerte in questo ambiente sono di sola lettura.

![](assets/offer_environments_overview_001.png)

Ogni ambiente **[!UICONTROL Design]** è collegato a un ambiente **[!UICONTROL Live]**. Quando un&#39;offerta è completa, il suo contenuto e le sue regole di idoneità sono soggette a un ciclo di approvazione. Una volta completato questo ciclo, l&#39;offerta interessata viene distribuita automaticamente nell&#39;ambiente **[!UICONTROL Live]**. Da questo momento in poi sarà disponibile per la consegna.

Per impostazione predefinita, l’interazione viene fornita con un ambiente **[!UICONTROL Design]** e un ambiente **[!UICONTROL Live]** ad esso collegato. Entrambi gli ambienti sono preconfigurati per eseguire il targeting della tabella dei destinatari predefinita.

>[!NOTE]
>
>Per eseguire il targeting di un’altra tabella (tabella dei visitatori per offerte anonime o tabella dei destinatari specifica), è necessario utilizzare la procedura guidata di mappatura di destinazione per creare gli ambienti. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

I responsabili delle offerte e i responsabili della consegna possono accedere a diverse viste dell’ambiente. I responsabili della consegna possono visualizzare solo l’ ambiente delle offerte **[!UICONTROL Live]** e utilizzare le offerte per consegnarle. I gestori di offerte possono visualizzare e modificare l’ambiente **[!UICONTROL Design]** e visualizzare l’ambiente **[!UICONTROL Live]**. Per ulteriori informazioni, consulta [Profili operatore](../../interaction/using/operator-profiles.md).

## Creazione di un ambiente di offerta {#creating-an-offer-environment}

Per impostazione predefinita, l’interazione viene fornita con un ambiente preconfigurato per eseguire il targeting della tabella dei destinatari (offerte identificate). Se desideri eseguire il targeting di un’altra tabella (tabella visitatore per offerte anonime o tabella dei destinatari specifica), devi applicare le seguenti configurazioni:

1. Posiziona il cursore sul nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** . Fai clic con il pulsante destro del mouse sulla mappatura della consegna che desideri utilizzare (**[!UICONTROL Visitors]** se desideri utilizzare offerte anonime) e seleziona **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Fai clic su **[!UICONTROL Next]** per passare alla schermata successiva nella procedura guidata, seleziona la casella **[!UICONTROL Generate a storage schema for propositions]** e fai clic su **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Se la casella è già selezionata, deselezionala e ricontrolla.

1. Adobe Campaign crea due ambienti (**[!UICONTROL Design]** e **[!UICONTROL Live]** ) con informazioni di targeting dalla mappatura di destinazione precedentemente abilitata. L’ambiente è preconfigurato con le informazioni di targeting.

   Se hai attivato la mappatura **[!UICONTROL Visitor]**, la casella **[!UICONTROL Environment dedicated to incoming anonymous interactions]** viene selezionata automaticamente nella scheda **[!UICONTROL General]** dell’ambiente.

   Questa opzione consente di attivare funzioni specifiche per l’interazione anonima, in particolare durante la configurazione degli spazi di offerta dell’ambiente. Puoi anche configurare le opzioni che ti consentono di passare da un ambiente &quot;identificato&quot; a un ambiente &quot;anonimo&quot;.

   Ad esempio, puoi collegare uno spazio di offerta nell’ambiente destinatario (contatto identificato) con uno spazio di offerta corrispondente a un ambiente visitatore (contatto non identificato). In questo modo, verranno messe a disposizione del contatto diverse offerte a seconda che s/he sia identificato o meno. Per ulteriori informazioni, consulta [Creazione di spazi di offerta](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Per ulteriori informazioni sulle interazioni anonime su un canale in entrata, consulta [Interazioni anonime](../../interaction/using/anonymous-interactions.md).
