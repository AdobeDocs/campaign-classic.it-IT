---
product: campaign
title: Introduzione
description: Introduzione
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
TQID: https://experienceleague.adobe.com/L6Ais2NSt-Z29b7Jgz25a6uYInel9V-Hb5kv0u6oSLo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 194
ht-degree: 1%

---

# Introduzione{#introduction}



Questa sezione descrive la procedura da applicare per aggiornare Adobe Campaign, lato client e lato server, e descrive il passaggio a Unicode di un’istanza esistente.

>[!NOTE]
>
>Per le istanze di servizi ospitati/gestiti, è necessario coordinarsi con l’amministratore Adobe.\
>Per le istanze on-premise, puoi ottenere assistenza dai consulenti Adobe.

L’aggiornamento deve essere applicato a tutti i server in cui è installato Adobe Campaign.

1. Esegui la migrazione dei server di reindirizzamento e tracciamento (Apache/IIS).
1. Eseguire la migrazione dei server Power Booster/Cluster.
1. Esegui la migrazione del server di marketing.

Adobe Campaign si basa su diversi processi eseguiti sul lato server che dovranno essere modificati durante gli aggiornamenti, in particolare:

* Server applicazioni (nlserver web)
* Server di consegna (mta nlserver)
* Server di reindirizzamento (webmdl)

>[!CAUTION]
>
>La console client deve trovarsi nella stessa build dell’istanza del server.

>[!NOTE]
>
>Per ulteriori informazioni sui vari processi di Adobe Campaign, consulta [questa sezione](../../installation/using/general-architecture.md#logical-application-layer).\
>Quando si utilizza l&#39;architettura di tipo Power Booster o Power Cluster, è necessario applicare questo processo a tutti i server Power Booster/Cluster.

Se la nuova versione comporta una modifica della struttura del database, si consiglia di riavviare i server nell&#39;ordine seguente:

1. Server applicazioni (nlserver web),
1. server di reindirizzamento (webmdl),
1. Server di consegna (mta nlserver).
