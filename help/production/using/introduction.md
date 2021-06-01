---
product: campaign
title: Introduzione
description: Introduzione
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 3e39a0d2-ff7e-4233-82bb-2b360f696a33
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 1%

---

# Introduzione{#introduction}

Questa sezione presenta la procedura da applicare per l’aggiornamento di Adobe Campaign, lato client e lato server e descrive il passaggio a Unicode di un’istanza esistente.

>[!NOTE]
>
>Per le istanze ospitate, devi coordinarti con il tuo amministratore di Adobe.\
>Per le istanze on-premise, puoi ottenere assistenza dai Consulenti Adobe.

L&#39;aggiornamento deve essere applicato a tutti i server in cui è installato Adobe Campaign.

1. Esegui la migrazione dei server di reindirizzamento e tracking (Apache/IIS).
1. Eseguire la migrazione dei server Power Booster/Cluster.
1. Esegui la migrazione del server di marketing.

Adobe Campaign si basa su diversi processi eseguiti sul lato server che sarà necessario manipolare durante gli aggiornamenti, in particolare:

* Server applicazioni (web nlserver)
* Server di consegna (mta nlserver)
* Server di reindirizzamento (webmdl)

>[!CAUTION]
>
>La console client deve trovarsi nella stessa build dell’istanza server.

>[!NOTE]
>
>Per ulteriori informazioni sui vari processi Adobe Campaign, consulta [questa sezione](../../installation/using/general-architecture.md#logical-application-layer).\
>Quando si utilizza l&#39;architettura di tipo Power Booster o Power Cluster, è necessario applicare questo processo a tutti i server Power Booster/Cluster.

Se la nuova versione comporta una modifica della struttura del database, si consiglia di riavviare i server nel seguente ordine:

1. server applicazioni (web nlserver),
1. server di reindirizzamento (webmdl),
1. Server di consegna (nlserver mta).
