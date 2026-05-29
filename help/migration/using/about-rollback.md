---
product: campaign
title: Ripristino della versione precedente
description: Scopri come ripristinare la versione precedente
feature: Upgrade
audience: migration
content-type: reference
topic-tags: rollback
hide: true
exl-id: 5120a7c4-3760-48d9-94da-d587d333e8d8
TQID: https://experienceleague.adobe.com/THilp-bTvgoG7Sot0dc-2f07Ff-kpkNUFYAdUMAQbv4
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
subfeature_v2: id: eff19c99-440a-4318-b319-444edc4d8d8f
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 130
ht-degree: 0%

---

# Ripristino della versione precedente{#about-rollback}



Dopo una migrazione, in caso di problemi, potrebbe essere necessario eseguire il rollback alla versione precedente di Campaign.

La procedura di ripristino dipende dalla versione iniziale di Campaign.

Di seguito è illustrata la procedura per ripristinare una versione v6.1 da una v7.

1. Ripristinare il backup del database e ripristinarlo.
1. Recupera la cartella **Adobe Campaign v6.back** (**nl6.back** in Linux), rinominala in **Adobe Campaign v6** (**nl6** in Linux) e ripristina il percorso originale.
1. Riconfigura IIS riassegnando le porte di ascolto per ristabilire l’integrazione di Adobe Campaign v6.1 a livello di sito web IIS.
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