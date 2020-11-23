---
solution: Campaign Classic
product: campaign
title: Introduzione
description: Introduzione
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 1%

---


# Introduzione{#introduction}

Questa sezione illustra la procedura da applicare per l&#39;aggiornamento  lato Adobe Campaign, lato client e lato server e descrive il passaggio a Unicode di un&#39;istanza esistente.

>[!NOTE]
>
>Per le istanze ospitate, dovete coordinarvi con l&#39;amministratore di Adobe .\
>Per le istanze locali, potete ottenere assistenza dai Consulenti  Adobe.

L&#39;aggiornamento deve essere applicato a tutti i server in cui è installato  Adobe Campaign.

1. Migrare i server di reindirizzamento e tracciamento (Apache/IIS).
1. Migrare i server Power Booster/Cluster.
1. Esegui la migrazione del server di marketing.

 Adobe Campaign si basa su diversi processi eseguiti sul lato server che sarà necessario manipolare durante gli aggiornamenti, in particolare:

* Server applicazioni (web nlserver)
* Server di consegna (mta nlserver)
* Server di reindirizzamento (webmdl)

>[!NOTE]
>
>Per ulteriori informazioni sui vari processi  Adobe Campaign, consulta [questa sezione](../../installation/using/general-architecture.md#logical-application-layer).\
>Quando si utilizza l&#39;architettura Power Booster o Power Cluster, è necessario applicare questo processo a tutti i server Power Booster/Cluster.

Se la nuova versione comporta una modifica della struttura del database, si consiglia di riavviare i server nell&#39;ordine seguente:

1. Application server (web nlserver),
1. server di reindirizzamento (webmdl),
1. Server di consegna (nlserver mta).

