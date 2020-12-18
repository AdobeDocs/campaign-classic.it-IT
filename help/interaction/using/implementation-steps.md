---
solution: Campaign Classic
product: campaign
title: Passaggi di implementazione
description: Passaggi di implementazione
audience: interaction
content-type: reference
topic-tags: general-operation
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 3%

---


# Passaggi di implementazione{#implementation-steps}

## Configurazione dell&#39;interazione {#configuring-interaction}

>[!NOTE]
>
>I passaggi seguenti devono essere eseguiti da un profilo **Administrator** e solo in ambienti di progettazione.

1. Creazione di profili utente. Per ulteriori informazioni, fare riferimento a [Profili operatore](../../interaction/using/operator-profiles.md).
1. Creazione di un ambiente di offerte mediante il targeting della dimensione. Per ulteriori informazioni, vedere [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Creazione di regole di tipologia per ogni ambiente. Per ulteriori informazioni, consultate [Creazione e riferimento a una regola di presentazione delle offerte](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Creazione di spazi di offerta per ciascun ambiente e configurazione delle funzioni di rendering. Per ulteriori informazioni, vedere [Creazione di spazi di offerta](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Se lo spazio è definito da un canale unitario in modalità identificata, è necessario specificare i parametri avanzati per questo spazio.

1. Configurazione del motore di offerte per le interazioni in entrata per presentare e aggiornare una o più offerte.

   Le varie modalità di integrazione sono descritte in [Informazioni sui canali in ingresso](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Quando viene creato uno spazio sul canale Web in ingresso, è necessaria una configurazione anche sul sito in cui verrà visualizzata l&#39;offerta.

## Gestione del catalogo delle offerte {#managing-the-offer-catalog-}

>[!NOTE]
>
>I passaggi seguenti devono essere eseguiti da **Offer manager**.

1. Creazione di categorie di offerte in ambienti di progettazione. Per ulteriori informazioni, vedere [Creazione di categorie di offerte](../../interaction/using/creating-offer-categories.md).
1. Creazione di offerte in ambienti di progettazione. Per ulteriori informazioni, vedere [Creazione di un&#39;offerta](../../interaction/using/creating-an-offer.md).
1. Approvazione e pubblicazione di offerte su uno o più spazi per renderle disponibili in ambienti live per il gestore delle consegne. Per ulteriori informazioni, vedere [Approvazione e attivazione di un&#39;offerta](../../interaction/using/approving-and-activating-an-offer.md).

## Utilizzo del catalogo di offerte {#using-the-offer-catalog-}

>[!NOTE]
>
>I passaggi seguenti devono essere eseguiti da un profilo **Delivery manager**. Possono modificare le offerte solo in ambienti live.

1. Creazione di una campagna.
1. Riferimento a un&#39;offerta in una campagna o nella distribuzione di una campagna. Per ulteriori informazioni, vedere [Informazioni sui canali in uscita](../../interaction/using/about-outbound-channels.md).

