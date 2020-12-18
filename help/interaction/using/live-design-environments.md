---
solution: Campaign Classic
product: campaign
title: Ambienti di progettazione/in tempo reale
description: Ambienti di progettazione/in tempo reale
audience: interaction
content-type: reference
topic-tags: managing-environments
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 2%

---


# Ambienti di progettazione/in tempo reale{#live-design-environments}

## Principio di funzionamento {#operating-principle}

L&#39;interazione funziona con due tipi di ambienti di offerta:

* **[!UICONTROL Design]** gli ambienti di offerte che includono offerte in fase di modifica e che possono essere modificate. Queste offerte non sono state sottoposte al ciclo di approvazione e non vengono consegnate ai contatti.
* **[!UICONTROL Live]** ambienti di offerte che includono offerte approvate mentre vengono presentate ai contatti. Le offerte in questo ambiente sono di sola lettura.

![](assets/offer_environments_overview_001.png)

Ogni ambiente **[!UICONTROL Design]** è collegato a un ambiente **[!UICONTROL Live]**. Quando un&#39;offerta è completa, il suo contenuto e le regole di ammissibilità sono soggetti a un ciclo di approvazione. Una volta completato il ciclo, l&#39;offerta interessata viene automaticamente distribuita nell&#39;ambiente **[!UICONTROL Live]**. Da questo momento in poi, sarà disponibile per la consegna.

Per impostazione predefinita, l&#39;interazione viene fornita con un ambiente **[!UICONTROL Design]** e un ambiente **[!UICONTROL Live]** ad esso collegato. Entrambi gli ambienti sono preconfigurati per il targeting della tabella dei destinatari out-of-the-box.

>[!NOTE]
>
>Per eseguire il targeting di un&#39;altra tabella (tabella visitatore per le offerte anonime o una tabella di destinazione specifica), è necessario utilizzare la procedura guidata di mappatura della destinazione per creare gli ambienti. Per ulteriori informazioni, vedere [Creazione di un ambiente di offerta](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

I responsabili dell&#39;offerta e i responsabili della distribuzione hanno accesso a diverse viste dell&#39;ambiente. I manager della distribuzione possono visualizzare solo l&#39;ambiente di offerta **[!UICONTROL Live]** e utilizzare le offerte per distribuirli. I gestori delle offerte possono visualizzare e modificare l&#39;ambiente **[!UICONTROL Design]** e visualizzare l&#39;ambiente **[!UICONTROL Live]**. Per ulteriori informazioni, fare riferimento a [Profili operatore](../../interaction/using/operator-profiles.md).

## Creazione di un ambiente di offerta {#creating-an-offer-environment}

Per impostazione predefinita, Interaction viene fornito con un ambiente preconfigurato per il targeting della tabella dei destinatari (offerte identificate). Se desiderate eseguire il targeting di un&#39;altra tabella (tabella visitatore per offerte anonime o tabella di destinatari specifica), dovete applicare le seguenti configurazioni:

1. Posizionare il cursore sul nodo **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]**. Fare clic con il pulsante destro del mouse sulla mappatura della consegna che si desidera utilizzare (**[!UICONTROL Visitors]** se si desidera utilizzare offerte anonime), quindi selezionare **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Fare clic su **[!UICONTROL Next]** per passare alla schermata successiva della procedura guidata, selezionare la casella **[!UICONTROL Generate a storage schema for propositions]** e fare clic su **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Se la casella è già selezionata, deselezionarla e quindi ricontrollarla.

1.  Adobe Campaign crea due ambienti (**[!UICONTROL Design]** e **[!UICONTROL Live]**) con informazioni di targeting provenienti dalla mappatura di destinazione precedentemente abilitata. L&#39;ambiente è preconfigurato con le informazioni di targeting.

   Se è stata attivata la mappatura **[!UICONTROL Visitor]**, la casella **[!UICONTROL Environment dedicated to incoming anonymous interactions]** viene selezionata automaticamente nella scheda **[!UICONTROL General]** dell&#39;ambiente.

   Questa opzione consente di attivare funzioni specifiche per l&#39;interazione anonima, in particolare quando si configurano gli spazi di offerta per l&#39;ambiente. Potete inoltre configurare le opzioni che consentono di passare da un ambiente &quot;identificato&quot; a un ambiente &quot;anonimo&quot;.

   Ad esempio, puoi collegare un ambiente destinatario a uno spazio di offerta (contatto identificato) con uno spazio di offerta che corrisponda a un ambiente visitatore (contatto non identificato). In questo modo, verranno messe a disposizione del contatto diverse offerte a seconda che s/he sia identificato o meno. Per ulteriori informazioni, vedere [Creazione di spazi di offerta](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Per ulteriori informazioni sulle interazioni anonime su un canale in ingresso, fare riferimento a [Interazioni anonime](../../interaction/using/anonymous-interactions.md).

