---
product: campaign
title: Implementazione mid-sourcing
description: Implementazione mid-sourcing
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 2%

---

# Implementazione mid-sourcing{#mid-sourcing-deployment}



Questa configurazione rappresenta una soluzione intermedia ottimale tra una configurazione ASP (Hosted Configuration) e l’internalizzazione. I componenti di esecuzione rivolti all’esterno vengono eseguiti su un server di &quot;mid-sourcing&quot; ospitato in Adobe Campaign.

>[!NOTE]
>
>Per impostare questo tipo di distribuzione, è necessario acquisire l’opzione appropriata. Verifica il contratto di licenza.

La comunicazione generale tra server e processi viene eseguita in base allo schema seguente:

![](assets/s_ncs_install_midsourcing.png)

* I moduli di esecuzione e gestione dei mancati recapiti sono disabilitati nell’istanza.
* L’applicazione è configurata per eseguire l’esecuzione dei messaggi su un server remoto di &quot;mid-sourcing&quot; guidato tramite chiamate SOAP (su HTTP o HTTPS).

## Funzioni {#features}

### Vantaggi {#advantages}

* Configurazione server semplificata: non è necessario che il cliente configuri moduli rivolti all’esterno (mta e inMail).
* Utilizzo limitato della larghezza di banda: poiché l’esecuzione viene eseguita dal server di mid-sourcing, è necessaria solo una larghezza di banda sufficiente per inviare i dati di personalizzazione al server di mid-sourcing.
* L’elevata disponibilità non è più un problema interno: il problema si sposta sul server di mid-sourcing (reindirizzamento, pagine mirror, server di esecuzione, ecc.).
* Il database non lascia la società: solo i dati necessari per assemblare i messaggi vengono inviati al server di mid-sourcing (per questo è possibile utilizzare HTTPS).
* Questo tipo di distribuzione può essere una soluzione per architetture con volumi elevati (molti destinatari nel database), con una velocità effettiva di consegna significativa.

### Svantaggi {#disadvantages}

* Leggero ritardo nella visualizzazione delle informazioni sull’esecuzione dei messaggi e nella funzionalità di reporting, dovuto al tempo necessario per recuperare le informazioni dal server di mid-sourcing.
* I sondaggi e i moduli web rimangono sulla piattaforma client.

### Attrezzature consigliate {#recommended-equipment}

* Server applicazioni: CPU quad-core da 2 Ghz, 4 GB di RAM, disco rigido SATA RAID 1 da 80 GB software.
* Server di database: CPU bi-quad-core a 3 GHz, almeno 4 GB di RAM, disco rigido SAS RAID 10 15000RPM hardware, numero che dipende dalle dimensioni e dalle prestazioni previste del database.

>[!NOTE]
>
>Il reindirizzamento e il mid-sourcing sono elementi separati, tuttavia il server di tracciamento sarà in generale condiviso con i server di mid-sourcing.

## Passaggi per l’installazione e la configurazione {#installation-and-configuration-steps-}

### Prerequisiti {#prerequisites}

* JDK sul server applicazioni.
* Accesso a un server di database nel server applicazioni.
* Firewall configurato per aprire le porte HTTP (80) o HTTPS (443) al server di mid-sourcing.

### Installazione e configurazione (distribuzione mid-sourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Fai riferimento a [Server di mid-sourcing](../../installation/using/mid-sourcing-server.md).
