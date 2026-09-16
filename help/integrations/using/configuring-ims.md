---
product: campaign
title: Configurazione di IMS
description: Scopri come connettersi tramite un Adobe ID
feature: Configuration
badge-v7-prem: label="On-premise/hybrid only" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applies to on-premise and hybrid deployments only"
audience: integrations
content-type: reference
topic-tags: connecting-via-an-adobe-id
exl-id: b70ca220-1c81-4b23-b07a-a2cd694877fe
feature_v2: []
subfeature_v2:
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Adobe Analytics integration
  - id: df0d6518-6f49-46e2-b46e-3bcc513f553f
    internal-label: Adobe Experience Manager integration
  - id: eb007b6d-6e57-46ab-9485-3f24d6102304
    internal-label: Adobe Experience Platform integration
  - id: b1fd1501-3105-4d6b-b4d4-9af53126df75
    internal-label: Adobe Target integration
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 12%
---
# Configurazione di IMS{#configuring-ims}

>[!IMPORTANT]
>
>In qualità di utente di Campaign hosted o managed services, l’implementazione Adobe IMS è di proprietà di Adobe. I passaggi descritti di seguito si applicano solo ai clienti on-premise e ibridi.
> L’implementazione di Adobe IMS deve essere eseguita solo da amministratori tecnici Adobe. Contatta il rappresentante Adobe per avviare il processo di implementazione.

## Prerequisiti {#prerequisites}

* È necessario disporre di un nome e di un ID organizzazione Adobe Experience Cloud. Per trovare il tuo ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}.
* Devi aggiungere degli utenti in Experience Cloud. Per ulteriori informazioni, consulta [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/admin-getting-started.html){_blank}.

>[!NOTE]
>
>Assicurati che gli utenti siano collegati ai gruppi Adobe Experience Cloud che verranno sincronizzati con Adobe Campaign. [Ulteriori informazioni](#configuring-the-external-account).

## Aggiornamento della console {#updating-the-console}

Per utilizzare questa funzionalità, è fondamentale installare la versione più recente della console client.

## Installazione del pacchetto {#installing-the-package}

È necessario installare il pacchetto predefinito **[!UICONTROL Integration with the Adobe Experience Cloud]**. L&#39;installazione di un pacchetto di integrazione equivale all&#39;installazione di un pacchetto standard, descritto in [questa pagina](../../installation/using/installing-campaign-standard-packages.md).

![](assets/ims_6.png)

## Configurazione dell’account esterno {#configuring-the-external-account}

Configura l&#39;account esterno **Adobe Experience Cloud** in **[!UICONTROL Administration > Platform > External accounts]**.

![](assets/ims_5.png)

Immettere le seguenti informazioni:

* Informazioni di connessione per il server IMS utilizzato (ID e segreto). Queste informazioni sono fornite dal team di Assistenza clienti di Adobe. Per ulteriori informazioni, consulta le [Domande frequenti per gli amministratori di Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html).

  L&#39;indirizzo **[!UICONTROL Callback server]** deve essere specificato in **https**. Questo campo corrisponde all’URL di accesso dell’istanza di Adobe Campaign.

* ID organizzazione: per trovare il tuo ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}.

* Maschera di associazione: questo campo ti consente di definire la sintassi che consentirà la sincronizzazione dei nomi delle configurazioni nel dashboard di Enterprise con i gruppi in Adobe Campaign. Se utilizzi la sintassi &quot;Campaign - tenant_id - (.&#42;)&quot;, il gruppo di sicurezza creato in Adobe Campaign verrà collegato al nome della configurazione &quot;Campaign - tenant_id - internal_name&quot; nel dashboard di Enterprise.

* Informazioni sulla connessione di Adobe Experience Cloud, che è il nome del tenant di Adobe Experience Cloud.
