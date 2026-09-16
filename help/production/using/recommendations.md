---
product: campaign
title: Consigli
description: Consigli
feature: Monitoring
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
TQID: https://experienceleague.adobe.com/hz0wmjq8MEpmen-C30F0tHt5-sRXjQAJ6vaie3hjfAo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
    internal-label: Performance Monitoring
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '124'
ht-degree: 16%
---
# Consigli{#recommendations}



Adobe Campaign è un sistema a transazioni elevate (database OLTP). Ciò significa che il database sottostante verrà aggiornato di frequente, con conseguente deterioramento delle prestazioni nel tempo. Per evitare questo tipo di problemi, è necessaria una regolare manutenzione del database.

>[!IMPORTANT]
>
>Un database funziona in modo ottimale solo se viene gestito regolarmente. La manutenzione automatica offerta da alcuni RDBMS non è sufficiente e non sostituisce la manutenzione approfondita, come per tutti i sistemi di gestione transazionale di database relazionali.
>  
>Le procedure descritte nel presente documento sono raccomandazioni. I piani di manutenzione sono di responsabilità dell&#39;amministratore del database, che deve essere il primo contatto in caso di problemi.
