---
product: campaign
title: Introduzione
description: Introduzione
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 1%

---

# Introduzione{#introduction}



Questa sezione descrive la procedura da applicare per aggiornare Adobe Campaign, lato client e lato server, e descrive il passaggio a Unicode di un’istanza esistente.

>[!NOTE]
>
>Per le istanze di servizi ospitati/gestiti, è necessario coordinarsi con l&#39;amministratore Adobe.\
>Per le istanze on-premise, puoi ottenere assistenza da Consulenti Adobe.

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
