---
product: campaign
title: Ripristino della versione precedente
description: Scopri come ripristinare la versione precedente
audience: migration
content-type: reference
topic-tags: rollback
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# Ripristino della versione precedente{#about-rollback}

![](../../assets/v7-only.svg)

Dopo una migrazione, in caso di problemi, potrebbe essere necessario eseguire il rollback alla versione precedente di Campaign.

La procedura di rollback dipende dalla versione iniziale di Campaign.

Questa è la procedura per ripristinare una v6.1 da una v7.

1. Recuperare il backup del database e ripristinarlo.
1. Recuperare **Adobe Campaign v6.back** cartella (**nl6.back** in Linux), rinominalo in **Adobe Campaign v6** (**nl6** in Linux) e ripristinarlo nella sua posizione originale.
1. Riconfigura IIS riassegnando le porte di ascolto per ristabilire l&#39;integrazione di Adobe Campaign v6.1 a livello di sito Web IIS.
1. Arresta il servizio Adobe Campaign v7.
1. Riavvia IIS.
1. Riavvia il servizio Adobe Campaign v6.1.

<!--
	
## Restore to Campaign v6.02

Here is the procedure to restore a v6.02 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v6.back** folder (**nl6.back** in Linux), rename it to **Neolane v6** (**nl6** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Adobe Campaign v6.02 at IIS Website level.
1. Stop the Adobe Campaign v6.1 service.
1. Re-start IIS.
1. Restart the Adobe Campaign v6.02 service.

## Restore to Campaign v5.11

Here is the procedure to restore a v5.11 from a v7.

1. Recover the backup of the database and restore it.
1. Recover the **Neolane v5.back** folder (**nl5.back** in Linux), rename it to **Neolane v5** (**nl5** in Linux) and restore it to its original location.
1. Re-configure IIS by re-assigning the listen ports to re-establish the integration of Neolane v5 at IIS Website level.
1. Stop the Adobe Campaign v7 service.
1. Re-start IIS.
1. Re-start the Adobe Campaign v5 service.

-->