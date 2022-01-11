---
product: campaign
title: Ripristino della versione precedente
description: Scopri come ripristinare la versione precedente
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Ripristino della versione precedente{#about-rollback}

![](../../assets/v7-only.svg)

Dopo una migrazione, in caso di problemi, potrebbe essere necessario eseguire il rollback alla versione precedente di Campaign.

La procedura di rollback dipende dalla versione iniziale di Campaign.

## Ripristino di Campaign v6.1

Questa è la procedura per ripristinare una v6.1 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperare **Adobe Campaign v6.back** cartella (**nl6.back** in Linux), rinominalo in **Adobe Campaign v6** (**nl6** in Linux) e ripristinarlo nella sua posizione originale.
1. Riconfigura IIS riassegnando le porte di ascolto per ristabilire l&#39;integrazione di Adobe Campaign v6.1 a livello di sito Web IIS.
1. Arresta il servizio Adobe Campaign v7.
1. Riavvia IIS.
1. Riavvia il servizio Adobe Campaign v6.1.

## Ripristino della versione v6.02 di Campaign

Questa è la procedura per ripristinare una v6.02 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperare **Neolane v6.back** cartella (**nl6.back** in Linux), rinominalo in **Neolane v6** (**nl6** in Linux) e ripristinarlo nella sua posizione originale.
1. Riconfigura IIS riassegnando le porte di ascolto per ristabilire l&#39;integrazione di Adobe Campaign v6.02 a livello di sito Web IIS.
1. Arresta il servizio Adobe Campaign v6.1.
1. Riavvia IIS.
1. Riavvia il servizio Adobe Campaign v6.02.

## Ripristina Campaign v5.11

Questa è la procedura per ripristinare una v5.11 da a v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperare **Neolane v5.back** cartella (**nl5.back** in Linux), rinominalo in **Neolane v5** (**nl5** in Linux) e ripristinarlo nella sua posizione originale.
1. Riconfigura IIS riassegnando le porte di ascolto per ristabilire l&#39;integrazione di Neolane v5 a livello di sito Web IIS.
1. Arresta il servizio Adobe Campaign v7.
1. Riavvia IIS.
1. Riavvia il servizio Adobe Campaign v5.
