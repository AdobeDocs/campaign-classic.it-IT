---
product: campaign
title: Informazioni sulla configurazione iniziale
description: Informazioni sulla configurazione iniziale
feature: Installation, Configuration
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f77ba178-0dfb-4a2e-b33b-971765d42298
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 5%

---

# Passaggi chiave per configurare e distribuire l’istanza{#about-initial-configuration}



Una volta completata l’installazione di Adobe Campaign, devi configurarla per assicurarti che funzioni in modo efficiente in base ai vincoli e all’architettura tecnica. I passaggi per configurare un’istanza di Adobe Campaign sono descritti in questo capitolo, nella sequenza seguente:

1. Crea l’istanza e la connessione correlata; consulta [Creazione di un’istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
1. Creare e configurare il database, fare riferimento a [Creazione e configurazione del database](../../installation/using/creating-and-configuring-the-database.md).
1. Configurare il server Adobe Campaign, fare riferimento a [Configurazione del server Campaign](../../installation/using/configuring-campaign-server.md).
1. Distribuire l’istanza, fare riferimento a [Distribuzione di un’istanza](../../installation/using/deploying-an-instance.md).

La configurazione dell’istanza implica l’abilitazione di processi (web, mta, wfserver, ecc.) da avviare sul server e configurare moduli per l’invio di e-mail, per il tracciamento, ecc. Per ogni istanza, i processi di Adobe Campaign vengono attivati sul server. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#enabling-processes).

Per ottimizzare il funzionamento di Adobe Campaign possono essere necessarie configurazioni aggiuntive per ogni istanza (a seconda dei moduli utilizzati, dell’architettura e delle esigenze).
