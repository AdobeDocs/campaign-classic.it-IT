---
product: campaign
title: Informazioni sui tipi di implementazione
description: Informazioni sui tipi di implementazione
feature: Installation, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 08628efb-9186-4b67-9431-310d4bc276b4
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 11%

---

# Informazioni sui tipi di implementazione{#about-deployment-types}



La progettazione modulare di Adobe Campaign consente un&#39;ampia gamma di configurazioni di distribuzione, dalle configurazioni autonome (tutti i componenti di un unico computer) alle implementazioni aziendali con architettura completamente ridondante e distribuita che utilizzano più server. Tutto dipende dal livello richiesto di prestazioni e sicurezza.

In caso di configurazione su più computer, non è necessario utilizzare lo stesso sistema operativo in: ad esempio, è possibile utilizzare un server di reindirizzamento su Linux + Apache con server di consegna su Windows.

>[!NOTE]
>
>I passaggi di configurazione dell’installazione principale possono essere eseguiti solo da Adobe per le distribuzioni in hosting da Adobe, ad esempio per configurare i file di configurazione del server e dell’istanza.
>
>Per ulteriori informazioni sulle principali differenze tra le distribuzioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o al [Differenze tra le funzioni per le distribuzioni in hosting e on-premise](../../installation/using/capability-matrix.md).
