---
product: campaign
title: Implementazione mid-sourcing
description: Implementazione mid-sourcing
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---

# Implementazione mid-sourcing{#mid-sourcing-deployment}

Questa configurazione è una soluzione intermedia ottimale tra una configurazione in hosting (ASP) e l’internalizzazione. I componenti di esecuzione rivolti all’esterno vengono eseguiti su un server &quot;mid-sourcing&quot; ospitato in Adobe Campaign.

>[!NOTE]
>
>Per impostare questo tipo di distribuzione, devi acquisire l’opzione appropriata. Controlla il tuo contratto di licenza.

La comunicazione generale tra server e processi viene eseguita secondo il seguente schema:

![](assets/s_ncs_install_midsourcing.png)

* I moduli di esecuzione e gestione dei messaggi non recapitati sono disabilitati nell’istanza.
* L’applicazione è configurata per eseguire l’esecuzione dei messaggi su un server remoto &quot;mid-sourced&quot;, gestito utilizzando chiamate SOAP (su HTTP o HTTPS).

## Funzioni {#features}

### Vantaggi {#advantages}

* Configurazione del server semplificata: Non è necessario che il cliente configuri moduli rivolti all&#39;esterno (mta e inMail).
* Utilizzo limitato della larghezza di banda: Poiché l’esecuzione viene eseguita dal server di mid-sourcing, è necessaria solo una larghezza di banda sufficiente per inviare i dati di personalizzazione al server di mid-sourcing.
* L&#39;elevata disponibilità non è più un problema interno: Il problema viene spostato sul server di mid-sourcing (reindirizzamento, pagine mirror, server di esecuzione, ecc.).
* Il database non lascia l&#39;azienda: Solo i dati necessari per assemblare i messaggi vengono inviati al server di mid-sourcing (per questo è possibile utilizzare HTTPS).
* Questo tipo di implementazione può essere una soluzione per architetture di grandi volumi (molti destinatari nel database), con un throughput di consegna significativo.

### Svantaggi {#disadvantages}

* Leggermente ritardato nella visualizzazione delle informazioni di esecuzione dei messaggi e per la funzionalità di reporting a causa del tempo necessario per recuperare le informazioni dal server di mid-sourcing.
* I sondaggi e i moduli web rimangono sulla piattaforma client.

### Attrezzature consigliate {#recommended-equipment}

* Server applicazioni: 2 Ghz CPU quad-core, 4 GB di RAM, software RAID 1 disco rigido SATA da 80 GB.
* Server di database: CPU biquadrupla da 3 GHz, almeno 4 GB di RAM, disco rigido SAS hardware RAID 10 15000 rpm, il numero a seconda delle dimensioni e delle prestazioni previste del database.

>[!NOTE]
>
>Il reindirizzamento e il mid-sourcing sono elementi separati, tuttavia il server di tracciamento sarà, in generale, condiviso con i server di mid-sourcing.

## Passaggi di installazione e configurazione {#installation-and-configuration-steps-}

### Prerequisiti {#prerequisites}

* JDK sul server dell&#39;applicazione.
* Accesso a un server di database sul server dell&#39;applicazione.
* Firewall configurato per aprire le porte HTTP (80) o HTTPS (443) al server di mid-sourcing.

### Installazione e configurazione (distribuzione di mid-sourcing) {#installing-and-configuring--mid-sourcing-deployment-}

Fare riferimento a [Server di mid-sourcing](../../installation/using/mid-sourcing-server.md).
