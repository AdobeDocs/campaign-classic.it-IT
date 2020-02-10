---
title: Utilizzo della tabella Destinatari classici di Adobe Campaign
description: Scopri come utilizzare la tabella dei destinatari out-of-the-box in Adobe Campaign Classic durante la progettazione del modello dati.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 620724e283215df1fb3f10bd0211652b36284b57

---


# Best practice per i modelli di dati{#data-model-best-practices}

Di seguito sono riportate alcune best practice da seguire per la progettazione del modello dati utilizzando tabelle di grandi dimensioni e join complessi.

* Quando utilizzi tabelle di destinatari personalizzate aggiuntive, accertati di disporre di una tabella di registro dedicata per ogni mapping di consegna.
* Ridurre il numero di colonne, in particolare identificando quelle non utilizzate.
* Ottimizzate le relazioni del modello dati evitando join complessi, ad esempio join su più condizioni e/o più colonne.
* Per le chiavi di join, utilizzare sempre dati numerici anziché stringhe di caratteri.
* Ridurre al massimo la profondità di conservazione del registro. Se si desidera una cronologia più approfondita, è possibile aggregare il calcolo e/o gestire tabelle di registro personalizzate per memorizzare una cronologia più grande.

Per best practice dettagliate su come ottimizzare la progettazione del database per volumi più grandi, consulta [Campaign Classic Data Model Best practice](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).
