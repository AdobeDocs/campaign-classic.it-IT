---
title: Modelli di hosting
seo-title: Modelli di hosting
description: Modelli di hosting
seo-description: null
page-status-flag: never-activated
uuid: a9e035d9-326b-4e14-8f05-a22fe38d172b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 3175b9ab-e305-4f19-8267-d6172fa07a2a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 3%

---


# Modelli di hosting{#hosting-models}

 Adobe Campaign offre tre modelli di hosting, che offrono flessibilità e libertà di scegliere il modello migliore o modelli adatti alle esigenze aziendali.

>[!NOTE]
>
>I passaggi di installazione e configurazione principali possono essere eseguiti solo da  Adobe per le distribuzioni ospitate da  Adobe. Ad esempio, per configurare i file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle principali differenze tra le modalità di distribuzione, consultate [questo articolo](https://helpx.adobe.com/it/campaign/kb/acc-on-prem-vs-hosted.html). Se disponete di un modello ospitato o ibrido, fate riferimento a questa [sezione](../../installation/using/about-hybrid-and-hosted-models.md).

* **Managed Services (ospitato)**

    Adobe Campaign può essere distribuito come servizio gestito: tutti i componenti di  Adobe Campaign, inclusa l&#39;interfaccia utente, il motore di gestione dell&#39;esecuzione e il database Campaign del cliente, sono ospitati completamente da  Adobe, tra cui l&#39;esecuzione dell&#39;e-mail, le pagine mirror, il server di tracciamento e componenti Web esterni come l&#39;annullamento dell&#39;iscrizione al centro pagina/preferenze e le pagine di destinazione.  Adobe alloca fino a tre istanze nel cloud: Sviluppo, Test/Stage e Produzione. I passaggi di installazione e configurazione per questo modello di hosting sono descritti in questa [sezione](../../installation/using/hosted-model.md).

   ![](assets/deployment_hosted.png)

* **In sede**

    Adobe Campaign può essere implementato in sede: tutti i componenti di  Adobe Campaign, inclusa l&#39;interfaccia utente, il motore di gestione dell&#39;esecuzione e il database, risiedono sul sito nel centro dati del cliente. In questo modello di distribuzione, il cliente gestisce tutti gli aggiornamenti e gli aggiornamenti software e hardware e un amministratore di database dedicato deve eseguire attività di manutenzione e ottimizzazione per garantire la gestione delle istanze di Campaign.

   ![](assets/deployment_onpremise.png)

* **Ibrido**

   Se implementato come modello ibrido, il software della soluzione Adobe Campaign  risiede in sede presso il sito del cliente, e la gestione dell&#39;esecuzione viene fornita come servizio cloud da  Adobe. &#39;istanza di marketing di Adobe Campaign è installata all&#39;interno del firewall del cliente, pertanto le informazioni personali (PII) rimangono interne e solo i dati richiesti per personalizzare le e-mail vengono inviati al Cloud per l&#39;esecuzione delle e-mail. L&#39;istanza di esecuzione, ospitata in Cloud, riceve le richieste dall&#39;istanza locale per inviare e-mail. Questa istanza personalizza tutte le e-mail e le distribuisce. Nessun dato di alcun tipo viene memorizzato in modo permanente nel cloud. I passaggi di installazione e configurazione per questo modello di hosting sono descritti in questa [sezione](../../installation/using/hybrid-model.md).

   ![](assets/deployment_hybrid.png)

