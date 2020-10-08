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
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 5%

---


# AND-join{#and-join}

Un join attiva la propria transizione in uscita solo quando vengono attivate tutte le transizioni in entrata, ossia quando tutte le attività precedenti sono terminate. Questo consente di verificare che alcune attività siano state completate prima di continuare a eseguire il flusso di lavoro.

Ad esempio, potete utilizzare un&#39;attività AND-join nel contesto della creazione di contenuto e dell&#39;automazione dell&#39;invio di contenuti, per fare in modo che una consegna venga avviata solo una volta completate le fasi di query di destinazione e di aggiornamento dei contenuti. In [questa sezione è disponibile un caso di utilizzo dedicato](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

La popolazione inviata in uscita dell&#39;attività è determinata scegliendo un set principale tra le transizioni in entrata nell&#39;attività.

La transizione in uscita può contenere solo una delle popolazioni di transizione in entrata. Se l&#39;attività non è configurata, la transizione in uscita selezionerà in modo casuale una delle popolazioni in entrata.

>[!CAUTION]
>
>Nel caso di attività di tipo **AND-join** , le variabili dell&#39;evento vengono unite, ma se una stessa variabile viene definita due volte, si verifica un conflitto e il valore rimane indeterminato. Per ulteriori informazioni, fai riferimento a [](../../workflow/using/javascript-scripts-and-templates.md#event-variables).
