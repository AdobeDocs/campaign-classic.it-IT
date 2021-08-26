---
product: campaign
title: Modelli di hosting
description: Scopri i modelli di hosting di Campaign
feature: Overview
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 2%

---

# Modelli di hosting{#hosting-models}

![](../../assets/v7-only.svg)

Adobe Campaign offre una scelta di tre modelli di hosting, che offrono flessibilità e libertà nella scelta del modello migliore, o modelli adatti alle esigenze aziendali.

>[!NOTE]
>
>Ad Adobe, gli ambienti ospitati, i passaggi principali di installazione e configurazione possono essere eseguiti solo per Adobe, ad esempio per configurare il server e personalizzare i file di configurazione dell’istanza. Per ulteriori informazioni sulle principali differenze tra le modalità di distribuzione, consulta [questa pagina](../../installation/using/capability-matrix.md).

## Managed Services / In hosting

Adobe Campaign può essere implementato come servizio gestito: tutti i componenti di Adobe Campaign, inclusa l’interfaccia utente, il motore di gestione dell’esecuzione e il database Campaign del cliente, sono interamente ospitati per Adobe, inclusi l’esecuzione di e-mail, le pagine mirror, il server di tracciamento e i componenti web rivolti all’esterno, come l’annullamento della sottoscrizione a un centro pagine/preferenze e le pagine di destinazione.

![](assets/deployment_hosted.png)

In qualità di cliente in hosting, la maggior parte dei passaggi di installazione e configurazione viene eseguita per Adobe. Puoi accedere alle seguenti sezioni per personalizzare la tua implementazione:

* Configura il tracciamento e gli URL della pagina speculare per marchio. Per i messaggi transazionali, consulta [questa sezione](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installa la console client: fare riferimento a [a questa sezione](../../installation/using/installing-the-client-console.md).
* Ulteriori informazioni sugli strumenti di recapito messaggi e sulle best practice leggendo la [documentazione dettagliata](../../delivery/using/about-deliverability.md).
* Configura le opzioni di Campaign: fare riferimento a [a questa sezione](../../installation/using/configuring-campaign-options.md).
* Configurare i connettori di gestione delle relazioni con i clienti: fare riferimento a [a questa sezione](../../platform/using/crm-connectors.md).

## On-Premise

Adobe Campaign può essere implementato on-premise: tutti i componenti di Adobe Campaign, inclusa l’interfaccia utente, il motore di gestione dell’esecuzione e il database, risiedono sul sito nel data center del cliente. In questo modello di implementazione, il cliente gestisce tutti gli aggiornamenti e gli aggiornamenti software e hardware e un amministratore di database dedicato deve eseguire attività di manutenzione e ottimizzazione per garantire la gestione delle istanze di Campaign.

![](assets/deployment_onpremise.png)

In qualità di cliente on-premise, prima di iniziare la distribuzione di Campaign Classic, è necessario soddisfare i seguenti prerequisiti e consigli:

* Consulta la [Matrice di compatibilità](../../rn/using/compatibility-matrix.md) che elenca tutte le versioni dei sistemi e dei componenti supportati per Adobe Campaign.
* A seconda dell&#39;ambiente, leggi i [prerequisiti per Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) e [prerequisiti per Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Scopri i consigli relativi ai motori di database [in questa sezione](../../installation/using/database.md).
* Controlla che i livelli di accesso al database richiesti siano installati sul server e accessibili dall&#39;account Adobe Campaign. [Ulteriori informazioni](../../installation/using/application-server.md).
* Configura le reti come alcuni processi devono comunicare con altri o per accedere alla LAN e a Internet. Ciò significa che alcune porte TCP devono essere aperte per questi processi. [Ulteriori ](../../installation/using/network-configuration.md) informazioni sui requisiti di configurazione della rete.
* Consulta la [Lista di controllo protezione e privacy delle campagne](https://helpx.adobe.com/it/campaign/kb/acc-security.html).
* Controlla le linee guida generali per la stima dei requisiti hardware per la distribuzione on-premise [in questo articolo](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html).

## Ibrido

Quando viene implementato come modello ibrido, il software della soluzione Adobe Campaign risiede on-premise sul sito del cliente e la gestione dell’esecuzione viene fornita come servizio cloud per Adobe. L’istanza di marketing Adobe Campaign è installata all’interno del firewall di un cliente, pertanto le informazioni personali identificabili (PII) rimangono interne e solo i dati necessari per personalizzare le e-mail vengono inviati al Cloud per l’esecuzione delle e-mail. L’istanza di esecuzione, ospitata nel cloud, riceve le richieste dall’istanza On-Premise di inviare e-mail. Questa istanza personalizza tutte le e-mail e le distribuisce. Nessun dato di alcun tipo viene memorizzato in modo permanente nel cloud.

![](assets/deployment_hybrid.png)

In qualità di cliente ibrido, la maggior parte dei passaggi di installazione e configurazione viene eseguita per Adobe. Puoi accedere alle seguenti sezioni per personalizzare la tua implementazione:

* Configurare i messaggi transazionali: fare riferimento a [a questa sezione](../../message-center/using/transactional-messaging-architecture.md).
* Configura il tracciamento e gli URL della pagina speculare per marchio. Per i messaggi transazionali, consulta [questa sezione](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installa la console client: fare riferimento a [a questa sezione](../../installation/using/installing-the-client-console.md).
* Installa pacchetti incorporati: fare riferimento a [a questa sezione](../../installation/using/installing-campaign-standard-packages.md).
* Consegna: configura [regole MX](../../installation/using/email-deliverability.md#mx-configuration) e [formati e-mail](../../installation/using/email-deliverability.md#managing-email-formats). Ulteriori informazioni sugli strumenti di recapito messaggi e sulle best practice leggendo la [documentazione dettagliata](../../delivery/using/about-deliverability.md).
* Configura le opzioni di Campaign: fare riferimento a [a questa sezione](../../installation/using/configuring-campaign-options.md).
* Configurare un database esterno (Federated Data Access): fare riferimento a [a questa sezione](../../installation/using/about-fda.md).
* Configurazione dei connettori di gestione delle relazioni con i clienti: fare riferimento a [a questa sezione](../../platform/using/crm-connectors.md).
* Per ulteriori informazioni sui principi di distribuzione di mid-sourcing, consulta [questa sezione](../../installation/using/mid-sourcing-deployment.md).
