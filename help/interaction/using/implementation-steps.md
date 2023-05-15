---
product: campaign
title: Passaggi di implementazione
description: Passaggi di implementazione per il modulo di interazione di Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Interaction, Offers
exl-id: 82b88ab7-6a95-4bb3-b8b3-abea0fdd4ca0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# Passaggi di implementazione{#implementation-steps}



## Configurazione dell’interazione {#configuring-interaction}

>[!NOTE]
>
>I seguenti passaggi devono essere eseguiti da un **Amministratore** e solo in ambienti di progettazione.

1. Creazione di profili utente. Per ulteriori informazioni, consulta [Profili operatore](../../interaction/using/operator-profiles.md).
1. Creazione di un ambiente di offerta tramite la dimensione di targeting. Per ulteriori informazioni, consulta [Creazione di un ambiente di offerta](../../interaction/using/live-design-environments.md#creating-an-offer-environment).
1. Creazione di regole di tipologia per ogni ambiente. Per ulteriori informazioni, consulta [Creazione e riferimento a una regola di presentazione dell’offerta](../../interaction/using/managing-offer-presentation.md#creating-and-referencing-an-offer-presentation-rule).
1. Creazione di spazi di offerta per ciascun ambiente e configurazione delle funzioni di rendering. Per ulteriori informazioni, consulta [Creazione di spazi di offerta](../../interaction/using/creating-offer-spaces.md).

   >[!NOTE]
   >
   >Se lo spazio è definito da un canale unitario in modalità identificata, è necessario specificare i parametri avanzati per questo spazio.

1. Configurazione del motore di offerta per le interazioni in entrata al fine di presentare e aggiornare una o più offerte.

   Le varie modalità di integrazione sono descritte in [Informazioni sui canali in entrata](../../interaction/using/about-inbound-channels.md).

   >[!NOTE]
   >
   >Quando viene creato uno spazio sul canale Web in entrata, è necessaria una configurazione anche sul sito in cui verrà visualizzata l’offerta.

## Gestione del catalogo delle offerte {#managing-the-offer-catalog-}

>[!NOTE]
>
>Le seguenti fasi devono essere eseguite da un **Gestione delle offerte**.

1. Creazione di categorie di offerte in ambienti di progettazione. Per ulteriori informazioni, consulta [Creazione di categorie di offerta](../../interaction/using/creating-offer-categories.md).
1. Creazione di offerte in ambienti di progettazione. Per ulteriori informazioni, consulta [Creazione di un’offerta](../../interaction/using/creating-an-offer.md).
1. Approvazione e pubblicazione di offerte su uno o più spazi per renderli disponibili in ambienti live per il gestore consegne. Per ulteriori informazioni, consulta [Approvazione e attivazione di un’offerta](../../interaction/using/approving-and-activating-an-offer.md).

## Utilizzo del catalogo delle offerte {#using-the-offer-catalog-}

>[!NOTE]
>
>I seguenti passaggi devono essere eseguiti da un **Responsabile della consegna** profilo. Possono modificare solo le offerte in ambienti live.

1. Creazione di una campagna.
1. Riferimento a un’offerta in una campagna o una consegna di una campagna. Per ulteriori informazioni, consulta [Informazioni sui canali in uscita](../../interaction/using/about-outbound-channels.md).
