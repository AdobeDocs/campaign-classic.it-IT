---
title: Ripristino della versione v5.11
seo-title: Ripristino della versione v5.11
description: Ripristino della versione v5.11
seo-description: null
page-status-flag: never-activated
uuid: 4480c97c-5845-483c-a17b-644f05783b4e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: rollback
discoiquuid: ef778333-8e50-402b-9a69-78ac94497c67
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 9%

---


# Ripristino della versione v5.11{#restoring-v}

Di seguito viene illustrata la procedura per ripristinare una v5.11 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperate la cartella **Neolane v5.back** (**nl5.back** in Linux), rinominatela in **Neolane v5** (**nl5** in Linux) e ripristinatela nella posizione originale.
1. Riconfigurare IIS riassegnando le porte di ascolto per ripristinare l&#39;integrazione di Neolane v5 a livello di sito Web IIS.
1. Arrestate il servizio  Adobe Campaign v7.
1. Riavviate IIS.
1. Riavviate il servizio  Adobe Campaign v5.

