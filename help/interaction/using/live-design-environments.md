---
product: campaign
title: Ambienti di progettazione e Live
description: Ambienti di progettazione e Live
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: interaction
content-type: reference
topic-tags: managing-environments
exl-id: 965c4a6a-6535-454d-bd37-e9c8312b4d13
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
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

Ogni **[!UICONTROL Design]** l&#39;ambiente è collegato a un **[!UICONTROL Live]** ambiente. Quando un&#39;offerta è completa, il suo contenuto e le sue regole di idoneità sono soggette a un ciclo di approvazione. Una volta completato questo ciclo, l&#39;offerta in questione viene automaticamente distribuita nel **[!UICONTROL Live]** ambiente. Da questo momento in poi sarà disponibile per la consegna.

Per impostazione predefinita, l’interazione viene fornita con un **[!UICONTROL Design]** ambiente e **[!UICONTROL Live]** ambiente ad esso collegato. Entrambi gli ambienti sono preconfigurati per eseguire il targeting della tabella dei destinatari incorporata.

>[!NOTE]
>
>Per eseguire il targeting di un’altra tabella (tabella dei visitatori per offerte anonime o tabella dei destinatari specifica), è necessario utilizzare la procedura guidata di mappatura di destinazione per creare gli ambienti. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](#creating-an-offer-environment).

![](assets/offer_environments_overview_002.png)

I responsabili delle offerte e i responsabili della consegna possono accedere a diverse viste dell’ambiente. I gestori di consegne possono visualizzare solo **[!UICONTROL Live]** l’ambiente delle offerte e le offerte di utilizzo per consegnarle. I gestori di offerte possono visualizzare e modificare **[!UICONTROL Design]** ambiente e visualizza **[!UICONTROL Live]** ambiente. Per ulteriori informazioni, consulta [Profili operatore](../../interaction/using/operator-profiles.md).

## Creazione di un ambiente di offerta {#creating-an-offer-environment}

Per impostazione predefinita, l’interazione viene fornita con un ambiente preconfigurato per eseguire il targeting della tabella dei destinatari (offerte identificate). Se desideri eseguire il targeting di un’altra tabella (tabella visitatore per offerte anonime o tabella dei destinatari specifica), devi applicare le seguenti configurazioni:

1. Posizionare il cursore sul **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Delivery mappings]** nodo. Fai clic con il pulsante destro del mouse sulla mappatura della consegna che desideri utilizzare (**[!UICONTROL Visitors]** se desideri utilizzare offerte anonime) e seleziona **[!UICONTROL Actions]** > **[!UICONTROL Modify the options of the targeting dimension]**.

   ![](assets/offer_env_anonymous_001.png)

1. Fai clic su **[!UICONTROL Next]** per passare alla schermata successiva della procedura guidata, controlla **[!UICONTROL Generate a storage schema for propositions]** e fai clic su **[!UICONTROL Save]**.

   ![](assets/offer_env_anonymous_002.png)

   >[!NOTE]
   >
   >Se la casella è già selezionata, deselezionala e ricontrolla.

1. Adobe Campaign crea due ambienti (**[!UICONTROL Design]** e **[!UICONTROL Live]** ) con informazioni di targeting dalla mappatura di destinazione precedentemente abilitata. L’ambiente è preconfigurato con le informazioni di targeting.

   Se hai attivato **[!UICONTROL Visitor]** mappatura, **[!UICONTROL Environment dedicated to incoming anonymous interactions]** viene selezionato automaticamente nel **[!UICONTROL General]** scheda .

   Questa opzione consente di attivare funzioni specifiche per l’interazione anonima, in particolare durante la configurazione degli spazi di offerta dell’ambiente. Puoi anche configurare le opzioni che ti consentono di passare da un ambiente &quot;identificato&quot; a un ambiente &quot;anonimo&quot;.

   Ad esempio, puoi collegare uno spazio di offerta nell’ambiente destinatario (contatto identificato) con uno spazio di offerta corrispondente a un ambiente visitatore (contatto non identificato). In questo modo, il contatto potrà ricevere diverse offerte a seconda che il contatto sia identificato o meno. Per ulteriori informazioni, consulta [Creazione di spazi di offerta](../../interaction/using/creating-offer-spaces.md).

   ![](assets/offer_env_anonymous_003.png)

>[!NOTE]
>
>Per ulteriori informazioni sulle interazioni anonime su un canale in entrata, consulta [Interazioni anonime](../../interaction/using/anonymous-interactions.md).
