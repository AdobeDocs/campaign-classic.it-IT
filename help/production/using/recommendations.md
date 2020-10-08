---
title: Raccomandazioni
seo-title: Raccomandazioni
description: Raccomandazioni
seo-description: null
page-status-flag: never-activated
uuid: d898fe6d-7627-405f-b2bc-b17bf1dc9e96
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: a31c5c9f-503f-4b55-8409-34d4addbd581
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 3%

---


# Raccomandazioni{#recommendations}

 Adobe Campaign è un sistema altamente transazionale (database OLTP). Ciò significa che il database sottostante verrà aggiornato frequentemente, con conseguente peggioramento delle prestazioni nel tempo. Per evitare questo tipo di problema, è necessaria una manutenzione regolare del database.

>[!CAUTION]
>
>Un database funziona in modo ottimale solo se viene mantenuto su base regolare. La manutenzione automatica offerta da alcuni RDBMS non è sufficiente e non sostituisce la manutenzione approfondita, come per qualsiasi sistema di gestione delle transazioni di database relazionale.
>  
>Le procedure descritte nel presente documento sono raccomandazioni. I piani di manutenzione sono responsabilità dell&#39;amministratore del database, che deve essere il primo contatto in caso di problemi.

