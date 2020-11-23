---
solution: Campaign Classic
product: campaign
title: Ripristino della versione precedente
description: Scopri come ripristinare la versione precedente
audience: migration
content-type: reference
topic-tags: rollback
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# Ripristino della versione precedente{#about-rollback}

Dopo una migrazione, in caso di problemi, potrebbe essere necessario ripristinare la versione precedente di Campaign.

La procedura di rollback dipende dalla versione iniziale di Campaign.

## Ripristino della versione v6.1

Procedura per ripristinare una v6.1 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperate la cartella **Adobe Campaign v6.back** (**nl6.back** in Linux), rinominatela in **Adobe Campaign v6** (**nl6** in Linux) e ripristinatela nella posizione originale.
1. Riconfigurare IIS riassegnando le porte di ascolto per ripristinare l&#39;integrazione di  Adobe Campaign v6.1 a livello di sito Web IIS.
1. Arrestate il servizio  Adobe Campaign v7.
1. Riavviate IIS.
1. Riavviate il servizio  Adobe Campaign v6.1.

## Ripristino della campagna v6.02

Procedura per ripristinare una v6.02 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperate la cartella **Neolane v6.back** (**nl6.back** in Linux), rinominatela in **Neolane v6** (**nl6** in Linux) e ripristinatela nella posizione originale.
1. Riconfigurare IIS riassegnando le porte di ascolto per ripristinare l&#39;integrazione di  Adobe Campaign v6.02 a livello di sito Web IIS.
1. Arrestate il servizio  Adobe Campaign v6.1.
1. Riavviate IIS.
1. Riavviate il servizio  Adobe Campaign v6.02.

## Ripristino della campagna v5.11

Di seguito viene illustrata la procedura per ripristinare una v5.11 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperate la cartella **Neolane v5.back** (**nl5.back** in Linux), rinominatela in **Neolane v5** (**nl5** in Linux) e ripristinatela nella posizione originale.
1. Riconfigurare IIS riassegnando le porte di ascolto per ripristinare l&#39;integrazione di Neolane v5 a livello di sito Web IIS.
1. Arrestate il servizio  Adobe Campaign v7.
1. Riavviate IIS.
1. Riavviate il servizio  Adobe Campaign v5.
