---
product: campaign
title: Modelli di hosting
description: Scopri i modelli di hosting di Campaign
feature: Installation, Architecture, Deployment
role: Architect
level: Beginner
exl-id: a06b1365-d487-4df1-8f4a-7268b871a427
source-git-commit: a38d53f4b37aadbc53446b5e399af2eae56c12af
workflow-type: tm+mt
source-wordcount: '615'
ht-degree: 0%

---

# Modelli di hosting{#hosting-models}



Adobe Campaign offre una scelta di tre modelli di hosting, che offrono flessibilità e libertà per scegliere il modello o i modelli migliori per soddisfare le esigenze aziendali.

>[!NOTE]
>
>Ad Adobe, negli ambienti in hosting, i passaggi principali di installazione e configurazione possono essere eseguiti solo per Adobe, come la configurazione del server e la personalizzazione dei file di configurazione delle istanze. Per ulteriori informazioni sulle principali differenze tra le modalità di distribuzione, consultare [questa pagina](../../installation/using/capability-matrix.md).

## Managed Services / In hosting

Adobe Campaign può essere implementato in modo as a Managed Service: tutti i componenti di Adobe Campaign, inclusa l’interfaccia utente, il motore di gestione dell’esecuzione e il database Campaign del cliente, sono completamente ospitati in Adobe, tra cui l’esecuzione e-mail, le pagine mirror, il server di tracciamento e i componenti web rivolti verso l’esterno quali la pagina di annullamento dell’abbonamento/il centro preferenze e le pagine di destinazione.

![](assets/deployment_hosted.png)

In qualità di cliente in hosting, la maggior parte dei passaggi di installazione e configurazione viene eseguita da Adobe. Per personalizzare l’implementazione, puoi accedere alle sezioni seguenti:

* Configura il tracciamento e gli URL delle pagine mirror per marchio. Per i messaggi transazionali, fai riferimento a [questa sezione](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installa la console client: fai riferimento a [questa sezione](../../installation/using/installing-the-client-console.md).
* Per ulteriori informazioni sugli strumenti di recapito messaggi e sulle best practice, consulta la [documentazione dettagliata](../../delivery/using/about-deliverability.md).
* Configurare le opzioni di Campaign: fai riferimento a [questa sezione](../../installation/using/configuring-campaign-options.md).
* Configurare i connettori di gestione delle relazioni con i clienti: fai riferimento a [questa sezione](../../platform/using/crm-connectors.md).

## On-premise

Adobe Campaign può essere implementato on-premise: tutti i componenti di Adobe Campaign, inclusi l’interfaccia utente, il motore di gestione dell’esecuzione e il database, risiedono on-site nel data center del cliente. In questo modello di implementazione, il cliente gestisce tutti gli aggiornamenti e le operazioni di aggiornamento di software e hardware; un amministratore di database dedicato deve eseguire attività di manutenzione e ottimizzazione per garantire la gestione delle istanze di Campaign.

![](assets/deployment_onpremise.png)

In qualità di cliente on-premise, prima di iniziare a distribuire Campaign Classic, considera i seguenti prerequisiti e consigli:

* Consulta la [Matrice di compatibilità](../../rn/using/compatibility-matrix.md) in cui sono elencate tutte le versioni dei sistemi e dei componenti supportati per Adobe Campaign.
* A seconda dell&#39;ambiente, leggere i [prerequisiti per Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) e [prerequisiti per Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md).
* Scopri i consigli relativi ai motori di database [in questa sezione](../../installation/using/database.md).
* Verificare che i livelli di accesso al database richiesti siano installati nel server e accessibili dall&#39;account Adobe Campaign. [Ulteriori informazioni](../../installation/using/application-server.md).
* Configurare le reti in base alle esigenze di comunicazione di alcuni processi o di accesso alla rete LAN e a Internet. Ciò significa che alcune porte TCP devono essere aperte per questi processi. [Ulteriori informazioni](../../installation/using/network-configuration.md) sui requisiti di configurazione della rete.
* Consulta la [lista di controllo per la sicurezza e la privacy di Campaign](https://helpx.adobe.com/it/campaign/kb/acc-security.html).
* Consultare le linee guida generali per la stima dei requisiti hardware per la distribuzione locale [ in questo articolo](https://helpx.adobe.com/it/campaign/kb/hardware-sizing-guide.html).

## Ibrido

Quando viene distribuito come modello ibrido, il software della soluzione Adobe Campaign risiede on-premise presso la sede del cliente e la gestione dell’esecuzione viene fornita come servizio cloud da Adobe. L’istanza di marketing Adobe Campaign è installata all’interno del firewall di un cliente, pertanto i dati personali (PII, personally identifiable information) rimangono interni e solo i dati necessari per personalizzare le e-mail vengono inviati al Cloud per l’esecuzione delle e-mail. L’istanza di esecuzione, ospitata nel cloud, riceve dall’istanza on-premise le richieste di consegna delle e-mail. Questa istanza personalizza tutte le e-mail e le consegna. Nessun dato di alcun tipo viene memorizzato in modo permanente nel cloud.

![](assets/deployment_hybrid.png)

In qualità di cliente ibrido, la maggior parte dei passaggi di installazione e configurazione viene eseguita per Adobe. Per personalizzare l’implementazione, puoi accedere alle sezioni seguenti:

* Configurare i messaggi transazionali: fai riferimento a [questa sezione](../../message-center/using/transactional-messaging-architecture.md).
* Configura il tracciamento e gli URL delle pagine mirror per marchio. Per i messaggi transazionali, fai riferimento a [questa sezione](../../message-center/using/additional-configurations.md#configuring-multibranding).
* Installa la console client: fai riferimento a [questa sezione](../../installation/using/installing-the-client-console.md).
* Installa pacchetti incorporati: fai riferimento a [questa sezione](../../installation/using/installing-campaign-standard-packages.md).
* Recapito messaggi: configura [regole MX](../../installation/using/email-deliverability.md#mx-configuration) e [formati e-mail](../../installation/using/email-deliverability.md#managing-email-formats). Per ulteriori informazioni sugli strumenti di recapito messaggi e sulle best practice, consulta la [documentazione dettagliata](../../delivery/using/about-deliverability.md).
* Configurare le opzioni di Campaign: fai riferimento a [questa sezione](../../installation/using/configuring-campaign-options.md).
* Configurare un database esterno (Federated Data Access): fare riferimento a [questa sezione](../../installation/using/about-fda.md).
* Configurazione dei connettori di gestione delle relazioni con i clienti: fai riferimento a [questa sezione](../../platform/using/crm-connectors.md).
* Per ulteriori informazioni sui principi di distribuzione di mid-sourcing, consulta [questa sezione](../../installation/using/mid-sourcing-deployment.md).
