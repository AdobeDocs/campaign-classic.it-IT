---
product: campaign
title: Passaggi di implementazione
description: Passaggi per l’implementazione del modulo di interazione di Campaign
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 1%

---

# Passaggi di implementazione{#implementation-steps}



## Configurazione dell’interazione {#configuring-interaction}

>[!NOTE]
>
>I seguenti passaggi devono essere eseguiti da un **Amministratore** profilo e solo in ambienti di progettazione.

1. Creazione di profili utente. Per ulteriori informazioni, consulta [Profili operatore](../../interaction/using/operator-profiles.md).
1. Creazione di un ambiente di offerta tramite la dimensione di targeting. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Creazione di regole di tipologia per ogni ambiente. Per ulteriori informazioni, consulta [Creazione e riferimento a una regola di presentazione dell’offerta](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Creazione di spazi di offerta per ogni ambiente e configurazione delle funzioni di rendering. Per ulteriori informazioni, consulta [Creazione di spazi dell’offerta](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Se lo spazio è definito da un canale unitario in modalità identificata, è necessario specificare i parametri avanzati per questo spazio.

1. Configurazione del motore di offerta per le interazioni in entrata al fine di presentare e aggiornare una o più offerte.

   Le varie modalità di integrazione sono descritte in [Informazioni sui canali in entrata](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Quando viene creato uno spazio sul canale web in entrata, è necessaria anche una configurazione sul sito in cui verrà visualizzata l’offerta.

## Gestione del catalogo delle offerte {#managing-the-offer-catalog-}

>[!NOTE]
>
>Le seguenti fasi devono essere eseguite da un **Gestione offerte**.

1. Creazione di categorie di offerta in ambienti di progettazione. Per ulteriori informazioni, consulta [Creazione di categorie di offerta](../../interaction/using/creating-offer-categories.md).
1. Creazione di offerte in ambienti di progettazione. Per ulteriori informazioni, consulta [Creazione di un’offerta](../../interaction/using/creating-an-offer.md).
1. Approvazione e pubblicazione di offerte su uno o più spazi per renderle disponibili negli ambienti live per il gestore della consegna. Per ulteriori informazioni, consulta [Approvazione e attivazione di un’offerta](../../interaction/using/approving-and-activating-an-offer.md).

## Utilizzo del catalogo delle offerte {#using-the-offer-catalog-}

>[!NOTE]
>
>I seguenti passaggi devono essere eseguiti da un **Responsabile della consegna** profilo. Possono modificare le offerte solo in ambienti live.

1. Creazione di una campagna.
1. Riferimento a un’offerta in una campagna o in una consegna di campagne. Per ulteriori informazioni, consulta [Informazioni sui canali in uscita](../../interaction/using/about-outbound-channels.md).
