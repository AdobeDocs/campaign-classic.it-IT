---
title: Distribuzione mid-sourcing
seo-title: Distribuzione mid-sourcing
description: Distribuzione mid-sourcing
seo-description: null
page-status-flag: never-activated
uuid: e359c486-7ee6-4295-80fc-4c371a0ef068
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 19220d8e-9494-46b4-9aa0-4c4a729aea96
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 2%

---


# Distribuzione mid-sourcing{#mid-sourcing-deployment}

Questa configurazione è una soluzione intermedia ottimale tra una configurazione in hosting (ASP) e l&#39;internalizzazione. I componenti di esecuzione rivolti all’esterno vengono eseguiti su un server di &quot;mid-sourcing&quot; ospitato  Adobe Campaign.

>[!NOTE]
>
>Per impostare questo tipo di distribuzione, è necessario acquisire l&#39;opzione appropriata. Controlla il contratto di licenza.

La comunicazione generale tra server e processi viene eseguita secondo il seguente schema:

![](assets/s_ncs_install_midsourcing.png)

* I moduli di esecuzione e gestione dei rimbalzi sono disattivati nell&#39;istanza.
* L&#39;applicazione è configurata per eseguire l&#39;esecuzione dei messaggi su un server remoto &quot;mid-sourced&quot;, guidato tramite chiamate SOAP (su HTTP o HTTPS).

## Caratteristiche {#features}

### Vantaggi {#advantages}

* Configurazione server semplificata: Non è necessario che il cliente configuri moduli rivolti verso l&#39;esterno (mta e inMail).
* Uso limitato della larghezza di banda: Poiché l&#39;esecuzione è eseguita dal server di mid-sourcing, è necessaria solo una larghezza di banda sufficiente per inviare i dati di personalizzazione al server di mid-sourcing.
* L&#39;elevata disponibilità non è più un problema interno: Il problema viene spostato sul server di mid-sourcing (reindirizzamento, pagine mirror, server di esecuzione, ecc.).
* Il database non lascia la società: Solo i dati necessari per assemblare i messaggi vengono inviati al server di mid-sourcing (per questo può essere utilizzato HTTPS).
* Questo tipo di implementazione può essere una soluzione per architetture di grandi volumi (molti destinatari nel database), con un significativo throughput di distribuzione.

### Svantaggi {#disadvantages}

* Leggero ritardo nella visualizzazione delle informazioni di esecuzione dei messaggi e della funzionalità di reporting, a causa del tempo necessario per recuperare le informazioni dal server mid-sourcing.
* I sondaggi e i moduli Web restano sulla piattaforma client.

### Apparecchiature consigliate {#recommended-equipment}

* Server applicazioni: 2 Ghz quad-core CPU, 4 GB di RAM, software RAID 1 disco rigido SATA da 80 GB.
* Server di database: CPU biquadruple a 3 GHz, almeno 4 GB di RAM, disco rigido SAS RAID 10 15000 rpm hardware, il numero a seconda delle dimensioni e delle prestazioni previste del database.

>[!NOTE]
>
>Reindirizzamento e mid-sourcing sono elementi separati, ma il server di tracciamento sarà, in generale, condiviso con i server di mid-sourcing.

## Procedura di installazione e configurazione {#installation-and-configuration-steps-}

### Prerequisiti {#prerequisites}

* JDK sul server dell’applicazione.
* Accesso a un server di database sul server dell’applicazione.
* Firewall configurato per aprire le porte HTTP (80) o HTTPS (443) al server di mid-sourcing.

### Installazione e configurazione (distribuzione mid-sourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Fare riferimento al server [](../../installation/using/mid-sourcing-server.md)mid-sourcing.
