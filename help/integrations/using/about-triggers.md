---
product: campaign
title: Informazioni su Adobe Experience Cloud Triggers
description: Introduzione all’implementazione dei trigger Adobe Experience Cloud
feature: Triggers
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 0e337620-a49f-4e14-8c67-9279d74736f1
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 7%

---

# Work with Campaign and Experience Cloud Triggers{#about-adobe-experience-triggers}

[!DNL Triggers] è un&#39;integrazione tra Adobe Campaign e Adobe Analytics che utilizza la pipeline. The pipeline retrieves users&#39; actions or triggers from your website. A cart abandonment is an example of trigger. Triggers are processed in Adobe Campaign to send emails in near real time.

>[!CAUTION]
>
>Questa funzionalità non è disponibile come funzione predefinita del prodotto. For this implementation, work with your Adobe representative / Customer Care. You will then be able to follow the steps detailed in this [page](../../integrations/using/configuring-pipeline.md#prerequisites).

[!DNL Triggers] run marketing actions within a short range of time following a user&#39;s action. The typical response time is less than one hour.

Consente integrazioni più agili, in quanto la configurazione è minima e non è coinvolta una terza parte.
Supporta inoltre elevati volumi di traffico senza influire sulle prestazioni delle attività di marketing. Ad esempio, l’integrazione può elaborare un milione di trigger all’ora.

![](assets/do-not-localize/book.png) Discover how to [create an Experience Cloud trigger](https://experienceleague.adobe.com/docs/experience-cloud/triggers/create.html) and identify, define, and monitor critical consumer behaviors.

## [!DNL Triggers] architecture {#triggers-architecture}

The [!DNL pipelined] process is always running on the Adobe Campaign marketing server. It connects to the pipeline, retrieves the events, and processes them immediately.

![](assets/triggers_2.png)

The [!DNL pipelined] process logs in to the Experience Cloud using an authentication service and sends a private key. Il servizio di autenticazione restituisce un token. The token is used to authenticate when retrieving the events.

## Prerequisiti {#adobe-io-prerequisites}

Before starting this implementation, please check you have:

* a valid **Organization identifier**: the Organization ID is the unique identifier within the Adobe Experience Cloud, used for example for the VisitorID service and the IMS Single-Sign On (SSO). [Ulteriori informazioni](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it)
* **Accesso per sviluppatori** all&#39;organizzazione. L&#39;amministratore di sistema dell&#39;organizzazione deve seguire la procedura **Aggiungi sviluppatori a un singolo profilo di prodotto** dettagliata [in questa pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html) per fornire agli sviluppatori l&#39;accesso al profilo di prodotto `Analytics - {tenantID}` del prodotto Adobe Analytics associato a Triggers.

## Passaggi di implementazione {#implement}

Per implementare Campaign e Experience Cloud Triggers, segui i passaggi seguenti:

1. Create an OAuth project. [Ulteriori informazioni](oauth-technical-account.md#oauth-service)

1. Add your OAuth project credentials in Adobe Campaign. [Ulteriori informazioni](oauth-technical-account.md#add-credentials)

1. Update the authentication type to the Developer console project in the configuration file **config-&lt; instance-name >.xml** as follows:

   ```
   <pipelined ... authType="imsJwtToken"  ... />
   ```

   Then, run a `config -reload` and a restart of the [!DNL pipelined] for the changes to be taken into account.

