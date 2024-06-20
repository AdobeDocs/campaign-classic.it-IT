---
product: campaign
title: Configurazione di Developer Console per Adobe Experience Cloud Triggers
description: Scopri come configurare Developer Console Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---

# Configurazione di Developer Console per Adobe Experience Cloud Triggers {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## Prerequisiti {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

Prima di iniziare questa implementazione, verifica di disporre di:

* un valore valido **Identificatore organizzazione**: l’ID organizzazione è l’identificatore univoco all’interno di Adobe Experience Cloud, utilizzato ad esempio per il servizio VisitorID e l’accesso Single Sign-On (SSO) di IMS. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it)
* a **Accesso per sviluppatori** alla tua organizzazione. L’amministratore di sistema dell’organizzazione deve seguire la procedura **Aggiungere sviluppatori a un singolo profilo di prodotto** procedura dettagliata [in questa pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html) per fornire agli sviluppatori l&#39;accesso per `Analytics - {tenantID}` Profilo prodotto del prodotto Adobe Analytics associato a Triggers.

## Passaggio 1: creare/aggiornare il progetto OAuth {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> Le credenziali dell’account di servizio (JWT) sono state dichiarate obsolete da Adobe. Le integrazioni di Campaign con le soluzioni e le app Adobe ora devono basarsi sulle credenziali server-to-server OAuth. </br>
>
> * Se hai implementato le integrazioni in entrata con Campaign, devi migrare l’account tecnico come descritto in [questa documentazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Le credenziali dell’account di servizio (JWT) esistenti continueranno a funzionare fino al 27 gennaio 2025.</br>
>
> * Se hai implementato integrazioni in uscita, ad esempio l’integrazione Campaign-Analytics o l’integrazione Experience Cloud Triggers, queste continueranno a funzionare fino al 27 gennaio 2025. Tuttavia, prima di tale data, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a oAuth.

Per procedere con la configurazione del connettore Adobe Analytics, accedi alla console Adobe Developer e crea il progetto server-to-server OAuth.

Fai riferimento a [questa pagina](oauth-technical-account.md#oauth-service) per la documentazione dettagliata.

## Passaggio 2: aggiungere le credenziali del progetto in Adobe Campaign {#add-credentials-campaign}

Segui i passaggi descritti in [questa pagina](oauth-technical-account.md#add-credentials) per aggiungere le credenziali del progetto OAuth in Adobe Campaign.

## Passaggio 3: aggiornare il tag pipeline {#update-pipelined-tag}

Da aggiornare [!DNL pipelined] , è necessario aggiornare il tipo di autenticazione al progetto Console sviluppatori nel file di configurazione **config-&lt; nome-istanza >.xml** come segue:

```
<pipelined ... authType="imsJwtToken"  ... />
```

Quindi, esegui una `config -reload` e il riavvio del [!DNL pipelined] affinché le modifiche siano prese in considerazione.
