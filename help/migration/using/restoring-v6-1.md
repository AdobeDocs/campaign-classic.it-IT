---
title: Ripristino della versione 6.1
seo-title: Ripristino della versione 6.1
description: Ripristino della versione 6.1
seo-description: null
page-status-flag: never-activated
uuid: 3fb71b6f-4d70-4814-a885-4d414a542eca
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: e510482c-a56d-4254-90f8-19bd5c545e30
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Ripristino della versione 6.1{#restoring-v}

Procedura per ripristinare una v6.1 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperate la cartella **Adobe Campaign v6.back** (**nl6.back** in Linux), rinominatela in **Adobe Campaign v6** (**nl6** in Linux) e ripristinatela nella posizione originale.
1. Riconfigurare IIS riassegnando le porte di ascolto per ripristinare l&#39;integrazione di Adobe Campaign v6.1 a livello di sito Web IIS.
1. Arrestate il servizio Adobe Campaign v7.
1. Riavviate IIS.
1. Riavvia il servizio Adobe Campaign v6.1.

