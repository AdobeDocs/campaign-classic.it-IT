---
product: campaign
title: Raccomandazioni
description: Raccomandazioni
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 9%

---

# Raccomandazioni{#recommendations}



Adobe Campaign è un sistema a transazioni elevate (database OLTP). Ciò significa che il database sottostante verrà aggiornato di frequente, con conseguente deterioramento delle prestazioni nel tempo. Per evitare questo tipo di problemi, è necessaria una regolare manutenzione del database.

>[!IMPORTANT]
>
>Un database funziona in modo ottimale solo se viene gestito regolarmente. La manutenzione automatica offerta da alcuni RDBMS non è sufficiente e non sostituisce la manutenzione approfondita, come per tutti i sistemi di gestione transazionale di database relazionali.
>  
>Le procedure descritte nel presente documento sono raccomandazioni. I piani di manutenzione sono di responsabilità dell&#39;amministratore del database, che deve essere il primo contatto in caso di problemi.
