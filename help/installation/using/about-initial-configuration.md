---
product: campaign
title: Informazioni sulla configurazione iniziale
description: Informazioni sulla configurazione iniziale
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 8%

---

# Passaggi chiave per configurare e distribuire l’istanza{#about-initial-configuration}



Una volta completata l’installazione di Adobe Campaign, devi configurarla per assicurarti che funzioni in modo efficiente con i tuoi vincoli e l’architettura tecnica. I passaggi per la configurazione di un’istanza di Adobe Campaign sono descritti in questo capitolo, nella sequenza seguente:

1. Crea l&#39;istanza e la relativa connessione, fai riferimento a [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
1. Crea e configura il database, consulta [Creazione e configurazione del database](../../installation/using/creating-and-configuring-the-database.md).
1. Configura il server Adobe Campaign, fai riferimento a [Configurazione del server Campaign](../../installation/using/configuring-campaign-server.md).
1. Distribuisci l’istanza, fai riferimento a [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md).

La configurazione dell’istanza implica l’abilitazione dei processi (web, mta, wfserver, ecc.) da avviare sul server e configurare moduli per l’invio di e-mail, per il tracciamento, ecc. Per ogni istanza, i processi Adobe Campaign vengono attivati sul server. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

Per ottimizzare il funzionamento di Adobe Campaign, possono essere necessarie configurazioni aggiuntive per ogni istanza (a seconda dei moduli utilizzati, dell’architettura e delle esigenze).
