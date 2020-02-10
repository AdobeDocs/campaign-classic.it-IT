---
title: AND-join
seo-title: AND-join
description: AND-join
seo-description: null
page-status-flag: never-activated
uuid: 8234d6cd-0e9b-4187-9ddf-9e1f86aa1b9a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 075206aa-ff7b-4fa8-a05d-14a29fb119ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# AND-join{#and-join}

Un join attiva la propria transizione in uscita solo quando vengono attivate tutte le transizioni in entrata, ossia quando tutte le attività precedenti sono terminate. Questo consente di verificare che alcune attività siano state completate prima di continuare a eseguire il flusso di lavoro.

La popolazione inviata in uscita dell&#39;attività è determinata scegliendo un set principale tra le transizioni in entrata nell&#39;attività.

La transizione in uscita può contenere solo una delle popolazioni in entrata. Se l&#39;attività non è configurata, la transizione in uscita selezionerà in modo casuale una delle popolazioni in entrata.
