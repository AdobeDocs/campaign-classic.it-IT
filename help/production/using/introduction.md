---
title: Introduzione
seo-title: Introduzione
description: Introduzione
seo-description: null
page-status-flag: never-activated
uuid: 4192a74e-1d4f-4784-80e3-53aaefa9141e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 772992bf-588f-42bd-a72a-986a88815264
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Introduzione{#introduction}

Questa sezione illustra la procedura da applicare per aggiornare Adobe Campaign, lato client e lato server e descrive il passaggio a Unicode di un&#39;istanza esistente.

>[!NOTE]
>
>Per le istanze ospitate, dovete coordinarvi con l&#39;amministratore Adobe.\
>Per le istanze locali, potete ottenere assistenza dai consulenti Adobe.

L&#39;aggiornamento deve essere applicato a tutti i server in cui è installato Adobe Campaign.

1. Migrare i server di reindirizzamento e tracciamento (Apache/IIS).
1. Migrare i server Power Booster/Cluster.
1. Migra il server di marketing.

Adobe Campaign è basato su diversi processi eseguiti sul lato server che dovranno essere modificati durante gli aggiornamenti, in particolare:

* Server applicazioni (web nlserver)
* Server di consegna (mta nlserver)
* Server di reindirizzamento (webmdl)

>[!NOTE]
>
>Per ulteriori informazioni sui vari processi di Adobe Campaign, consulta [questa sezione](../../installation/using/general-architecture.md#logical-application-layer).\
>Quando si utilizza l&#39;architettura Power Booster o Power Cluster, è necessario applicare questo processo a tutti i server Power Booster/Cluster.

Se la nuova versione comporta una modifica della struttura del database, si consiglia di riavviare i server nell&#39;ordine seguente:

1. Application server (web nlserver),
1. server di reindirizzamento (webmdl),
1. Server di consegna (nlserver mta).

