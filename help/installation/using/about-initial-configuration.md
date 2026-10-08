---
product: campaign
title: Informazioni sulla configurazione iniziale
description: Informazioni sulla configurazione iniziale
feature: Installation, Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
TQID: 'https://experienceleague.adobe.com/rQT-wcpjGzyYfEV3thGlY0WD7Po-A08yD0pGMr13p7s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 14%
---
# Passaggi chiave per configurare e distribuire l’istanza{#about-initial-configuration}



Una volta completata l’installazione di Adobe Campaign, devi configurarla per assicurarti che funzioni in modo efficiente in base ai vincoli e all’architettura tecnica. I passaggi per configurare un’istanza di Adobe Campaign sono descritti in questo capitolo, nella sequenza seguente:

1. Creare l&#39;istanza e la connessione correlata. Fare riferimento a [Creazione di un&#39;istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
1. Creare e configurare il database. Fare riferimento a [Creazione e configurazione del database](../../installation/using/creating-and-configuring-the-database.md).
1. Configura il server Adobe Campaign. Fai riferimento a [Configurazione del server Campaign](../../installation/using/configuring-campaign-server.md).
1. Distribuire l&#39;istanza, fare riferimento a [Distribuzione di un&#39;istanza](../../installation/using/deploying-an-instance.md).

La configurazione dell’istanza implica l’abilitazione di processi (web, mta, wfserver, ecc.) da avviare sul server e configurare moduli per l’invio di e-mail, per il tracciamento, ecc. Per ogni istanza, i processi di Adobe Campaign vengono attivati sul server. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

Per ottimizzare il funzionamento di Adobe Campaign possono essere necessarie configurazioni aggiuntive per ogni istanza (a seconda dei moduli utilizzati, dell’architettura e delle esigenze).
