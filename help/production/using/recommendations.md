---
product: campaign
title: Consigli
description: Consigli
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: e458f6cb-f6d1-4688-9f6d-2a27a2f90829
TQID: https://experienceleague.adobe.com/hz0wmjq8MEpmen-C30F0tHt5-sRXjQAJ6vaie3hjfAo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 136
ht-degree: 15%

---

# Consigli{#recommendations}



Adobe Campaign è un sistema a transazioni elevate (database OLTP). Ciò significa che il database sottostante verrà aggiornato di frequente, con conseguente deterioramento delle prestazioni nel tempo. Per evitare questo tipo di problemi, è necessaria una regolare manutenzione del database.

>[!IMPORTANT]
>
>Un database funziona in modo ottimale solo se viene gestito regolarmente. La manutenzione automatica offerta da alcuni RDBMS non è sufficiente e non sostituisce la manutenzione approfondita, come per tutti i sistemi di gestione transazionale di database relazionali.
>  
>Le procedure descritte nel presente documento sono raccomandazioni. I piani di manutenzione sono di responsabilità dell&#39;amministratore del database, che deve essere il primo contatto in caso di problemi.
