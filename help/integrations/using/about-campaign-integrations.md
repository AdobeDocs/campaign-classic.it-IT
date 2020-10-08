---
title: Informazioni sulle integrazioni di Campaign
description: Usa altre soluzioni  Adobe e unisci le loro diverse funzionalità con Campaign.
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 10%

---


# Informazioni sulle integrazioni di Campaign {#about-campaign-integrations}

Adobe Experience Cloud è un set completo di soluzioni integrate all&#39;avanguardia, basate su una piattaforma dati comune con un set comune di potenti servizi di base.

Informazioni sulle integrazioni funzionali disponibili tra  soluzioni [Adobe Campaign e](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) Adobe Experience Cloud e i servizi [](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)core. Potete quindi modernizzare le implementazioni della soluzione e implementare il Experience Cloud  in modo da poter utilizzare funzioni come gli attributi del cliente e le audience.

L&#39;elenco completo delle soluzioni e dei servizi di base  Adobe che possono essere integrati con  Adobe Campaign, così come la documentazione associata, è disponibile in [questa sezione](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>La maggior parte di queste integrazioni richiede l&#39;accesso tramite un Adobe ID  (IMS). For more on this implementation, refer to [this page](../../integrations/using/about-adobe-id.md).
>
>L&#39;implementazione IMS è un processo complesso, che può essere lungo. È strettamente riservato agli amministratori tecnici del Adobe .

## Collegamento delle soluzioni {#working-with-experience-cloud-solutions}

A seconda dell&#39;ambiente, diverse soluzioni possono essere collegate ad Adobe Experience Cloud. Sono collegate come organizzazioni. An **organization** is the entity that enables an administrator to configure groups and users, and to control single sign-on in the Experience Cloud. L’organizzazione funziona come una log-in company che abbraccia tutti i prodotti e le soluzioni di Experience Cloud. Nella maggior parte dei casi l’organizzazione corrisponde al nome aziendale, ma una stessa azienda può avere molte organizzazioni.

La gestione dell&#39;organizzazione e il collegamento degli account Adobe Experience Cloud sono descritti dettagliatamente nel portale [della guida di](https://docs.adobe.com/content/help/it-IT/core-services/interface/manage-users-and-products/organizations.html)Adobe Experience Cloud.

>[!CAUTION]
>
>Durante la nuova installazione  Adobe Campaign o l’integrazione di un’installazione esistente con Adobe Experience Cloud, il servizio [ID di](https://docs.adobe.com/content/help/en/id-service/using/home.html) Experience Cloud è attivato. Questo servizio sostituisce il cookie permanente utilizzato innanzitutto da  Adobe Campaign per le sue funzionalità di monitoraggio.
>
>Un ID visitatore univoco verrà quindi assegnato ai destinatari che generano registri di tracciamento. Questo ID verrà salvato nel **[!UICONTROL Requester UUID (@sourceID)]** campo della **[!UICONTROL nms:trackingLogRcp]** tabella. I dati di tracciamento dei destinatari che esistevano prima dell’implementazione del servizio ID visitatore non saranno più utilizzabili.
>
>L’ID verrà quindi riconosciuto dalle altre soluzioni Adobe Experience Cloud con lo stesso [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

## Integrazioni Experience Cloud {#experience-cloud-integrations}

La tabella seguente fornisce l&#39;accesso alla documentazione di integrazione  Experience Cloud disponibile.

<table> 
 <thead> 
  <tr> 
   <th> Soluzioni e servizi di base<br /> </th> 
   <th> Casi d’uso<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform</strong><br /> </td> 
   <td> L'integrazione tra  Adobe Campaign e  Adobe Real-time Customer Data Platform consente di condividere i dati dei segmenti e importare i tipi di pubblico  Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Ulteriori</a> informazioni sull'integrazione della piattaforma dati cliente in tempo reale  Adobe con Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS -  Adobe ID</strong><br /> </td> 
   <td> Consente di connettersi a  Adobe Campaign con lo stesso Adobe ID  delle altre soluzioni Adobe Experience Cloud.<br /> Per accedere a un Adobe ID  è necessario utilizzare alcune funzionalità collegate alle integrazioni Adobe Experience Cloud, in particolare i servizi di base.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Ulteriori</a> informazioni sull'implementazione  Adobe ID con  Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Allows you to create email contents or forms mapped to the Adobe Campaign database directly in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Ulteriori</a> informazioni sull'integrazione  Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Allows you to insert images that are dynamically computed by <strong>Adobe Target</strong> when the email created and sent by Adobe Campaign is opened.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Ulteriori</a> informazioni sull'integrazione  Adobe Campaign -  Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servizio</strong><br /> di base Persone <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Consente di condividere i tipi di pubblico tra le soluzioni Adobe Experience Cloud e i core utilizzati.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Scopri di più</a> su  servizi di base Persone e integrazioni Adobe Audience Manager per Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servizio di base risorse</strong><br /> </td> 
   <td> Consente di inserire gli assets dalla libreria di Adobe Experience Cloud nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Scopri di più</a> su  Adobe Campaign - Integrazione dei servizi di base di Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Allows you to insert assets from your <strong>AEM Assets</strong> library into emails and landing pages created in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Ulteriori</a> informazioni sull'integrazione  Adobe Campaign -  AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trigger di Experience Cloud</strong><br /> </td> 
   <td> Integration between <strong>Triggers core service</strong> and Adobe Campaign allows you to send personalized emails to your customers as a reaction to specific behaviors that are tracked on your website by Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/it/campaign/kb/triggers-and-campaign.html">Scopri di più</a> su  Adobe Campaign -  Experience Cloud attiva l'integrazione.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Connettori dati</strong><br /> </td> 
   <td> <strong>I connettori</strong> dati (precedentemente noti come  Adobe Genesis) consentono  Adobe Campaign e  Adobe Analytics di interagire attraverso segmenti relativi al comportamento degli utenti in seguito a una campagna e-mail. Al contrario, invia indicatori e attributi delle campagne e-mail distribuite da  Adobe Campaign a  Adobe Analytics - Connettore dati.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Ulteriori</a> informazioni sull'integrazione Campaign - Connettori dati.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

