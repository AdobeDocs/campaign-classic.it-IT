---
title: Ripristino v6.02
seo-title: Ripristino v6.02
description: Ripristino v6.02
seo-description: null
page-status-flag: never-activated
uuid: df21209b-4825-42fa-a303-f383f872abb5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: 4f65ba19-e9f0-4425-b640-f27c61394859
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9482a99c3be164651b3428179388cb0a8a75783f

---


# Ripristino v6.02{#restoring-v}

Procedura per ripristinare una v6.02 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperate la cartella **Neolane v6.back** (**nl6.back** in Linux), rinominatela in **Neolane v6** (**nl6** in Linux) e ripristinatela nella posizione originale.
1. Riconfigurare IIS riassegnando le porte di ascolto per ripristinare l&#39;integrazione di Adobe Campaign v6.02 a livello di sito Web IIS.
1. Arrestate il servizio Adobe Campaign v6.1.
1. Riavviate IIS.
1. Riavvia il servizio Adobe Campaign v6.02.

