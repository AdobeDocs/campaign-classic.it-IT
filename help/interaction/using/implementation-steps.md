---
title: Passaggi di implementazione
seo-title: Passaggi di implementazione
description: Passaggi di implementazione
seo-description: null
page-status-flag: never-activated
uuid: 11582071-00a2-4245-af3e-bc81174ce223
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: general-operation
discoiquuid: 7f79c0d8-77b0-4cc6-a888-7dbd32d2f3b6
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 3%

---


# Passaggi di implementazione{#implementation-steps}

## Configurazione dell&#39;interazione {#configuring-interaction}

>[!NOTE]
>
>I passaggi seguenti devono essere eseguiti da un profilo **Amministratore** e solo in ambienti di progettazione.

1. Creazione di profili utente. For more on this, refer to [Operator profiles](../../interaction/using/operator-profiles.md).
1. Creazione di un ambiente di offerte mediante il targeting della dimensione. Per ulteriori informazioni, consultate [Creazione di un ambiente](../../interaction/using/live-design-environments.md#creating-an-offer-environment)di offerte.
1. Creazione di regole di tipologia per ogni ambiente. Per ulteriori informazioni, consultate [Creazione e riferimento a una regola](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule)di presentazione delle offerte.
1. Creazione di spazi di offerta per ciascun ambiente e configurazione delle funzioni di rendering. Per ulteriori informazioni, consultate [Creazione di spazi](../../interaction/using/creating-offer-spaces.md)per le offerte.

   >[!NOTE]
   >
   >Se lo spazio è definito da un canale unitario in modalità identificata, è necessario specificare i parametri avanzati per questo spazio.

1. Configurazione del motore di offerte per le interazioni in entrata per presentare e aggiornare una o più offerte.

   Le varie modalità di integrazione sono descritte in [Informazioni sui canali](../../interaction/using/about-inbound-channels.md)in ingresso.

   >[!NOTE]
   >
   >Quando viene creato uno spazio sul canale Web in ingresso, è necessaria una configurazione anche sul sito in cui verrà visualizzata l&#39;offerta.

## Managing the offer catalog {#managing-the-offer-catalog-}

>[!NOTE]
>
>I seguenti passaggi devono essere eseguiti da un gestore **** dell&#39;offerta.

1. Creazione di categorie di offerte in ambienti di progettazione. Per ulteriori informazioni, consultate [Creazione di categorie](../../interaction/using/creating-offer-categories.md)di offerte.
1. Creazione di offerte in ambienti di progettazione. Per ulteriori informazioni, consultate [Creazione di un&#39;offerta](../../interaction/using/creating-an-offer.md).
1. Approvazione e pubblicazione di offerte su uno o più spazi per renderle disponibili in ambienti live per il gestore delle consegne. Per ulteriori informazioni, consultate [Approvazione e attivazione di un&#39;offerta](../../interaction/using/approving-and-activating-an-offer.md).

## Utilizzo del catalogo delle offerte {#using-the-offer-catalog-}

>[!NOTE]
>
>I passaggi seguenti devono essere eseguiti da un profilo di **Delivery Manager** . Possono modificare le offerte solo in ambienti live.

1. Creazione di una campagna.
1. Riferimento a un&#39;offerta in una campagna o nella distribuzione di una campagna. Per ulteriori informazioni, vedere [Informazioni sui canali](../../interaction/using/about-outbound-channels.md)in uscita.

