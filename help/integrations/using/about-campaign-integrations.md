---
solution: Campaign Classic
product: campaign
title: Informazioni sulle integrazioni di Campaign
description: Usa altre soluzioni Adobe e combina le loro diverse funzionalità con Campaign.
audience: integrations
content-type: reference
topic-tags: campaign-integrations
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 9%

---


# Introduzione alle  integrazioni Adobe Campaign {#about-campaign-integrations}

Adobe Experience Cloud è un set completo di soluzioni integrate all&#39;avanguardia, basate su una piattaforma dati comune con un set comune di potenti servizi di base.

Informazioni sulle integrazioni funzionali disponibili tra  soluzioni Adobe Campaign e [Adobe Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) e [servizi di base](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html). Potete quindi modernizzare le implementazioni della soluzione e implementare il Experience Cloud  in modo da poter utilizzare funzioni come gli attributi del cliente e le audience.

![](assets/ExCloud-solutions.png)

L&#39;elenco completo delle soluzioni e dei servizi di base  Adobe che possono essere integrati con  Adobe Campaign, così come la documentazione associata, è disponibile in [questa sezione](#experience-cloud-integrations).

>[!CAUTION]
>
>La maggior parte di queste integrazioni richiede l&#39;implementazione  Adobe  Identity Management System (IMS) per l&#39;accesso tramite un Adobe ID . [Ulteriori informazioni in questa pagina](../../integrations/using/about-adobe-id.md).


## Collegamento delle soluzioni {#working-with-experience-cloud-solutions}

È possibile collegare più soluzioni ad Adobe Experience Cloud. L&#39; **organizzazione** è l&#39;entità cliente che consente all&#39;amministratore di configurare gruppi e utenti e di controllare SSO (Single Sign-On) in Adobe Experience Cloud. L&#39;organizzazione si comporta come un&#39;azienda che abbraccia tutti i prodotti e le soluzioni  Experienci Cloud. Nella maggior parte dei casi l’organizzazione corrisponde al nome aziendale, ma una stessa azienda può avere molte organizzazioni.

La gestione dell&#39;organizzazione e il collegamento degli account Adobe Experience Cloud sono descritti nel [portale della guida Adobe Experience Cloud](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/organizations.html).

## Gestione identità e cookie {#id-and-cookies}

Durante l&#39;installazione  Adobe Campaign o l&#39;integrazione di un&#39;installazione esistente con Adobe Experience Cloud, [Adobe Experience Cloud Identity Service](https://docs.adobe.com/content/help/en/id-service/using/home.html) è attivato. Questo servizio sostituisce il cookie permanente utilizzato innanzitutto da  Adobe Campaign per le sue funzionalità di monitoraggio.

Il servizio Adobe Experience Cloud Identity Service (ID) fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni del Experience Cloud .

Un ID visitatore univoco verrà assegnato ai destinatari che generano registri di tracciamento. Questo ID verrà salvato nel campo **[!UICONTROL Requester UUID (@sourceID)]** della tabella **[!UICONTROL nms:trackingLogRcp]**. **I dati di tracciamento dei destinatari che esistevano prima dell’implementazione del servizio ID visitatore non saranno più utilizzabili**.

L&#39;ID verrà quindi riconosciuto dalle altre soluzioni Adobe Experience Cloud con lo stesso [CNAME](https://docs.adobe.com/content/help/en/id-service/using/reference/analytics-reference/cname.html).

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
   <td> <strong> Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> L'integrazione tra  Adobe Campaign e  Adobe Real-time Customer Data Platform (RTCDP) consente di condividere i dati dei segmenti e importare i tipi di pubblico  Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Scopri </a> di più sull'integrazione di Campaign -  Adobe Real-time Customer Data Platform (Piattaforma dati cliente in tempo reale).</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> Adobe  Identity Management System (IMS) -  Adobe ID</strong><br /> </td> 
   <td> Consente di connettersi a  Adobe Campaign con lo stesso Adobe ID  delle altre soluzioni Adobe Experience Cloud.<br /> Per accedere a un Adobe ID  è necessario utilizzare alcune funzionalità collegate alle integrazioni Adobe Experience Cloud, in particolare i servizi di base.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Scopri </a> di più sull'implementazione  Adobe ID con  Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Consente di creare contenuti e-mail o moduli mappati al database Adobe Campaign  direttamente in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Scopri </a> di più sull'integrazione  Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Consente di inserire immagini che vengono calcolate dinamicamente da <strong> Adobe Target</strong> all'apertura dell'e-mail creata e inviata da  Adobe Campaign.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Scoprite </a> di più 'integrazione Adobe Campaign -  Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>People core </strong><br /> <strong>serviceAudience Manager  Adobe</strong><br /> </td> 
   <td> Consente di condividere i tipi di pubblico tra le soluzioni Adobe Experience Cloud e i core utilizzati.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Scopri </a> di più  Adobe Campaign - Servizio di base Persone e integrazioni Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servizio di base risorse</strong><br /> </td> 
   <td> Consente di inserire gli assets dalla libreria di Adobe Experience Cloud nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Scopri </a> di più su  Adobe Campaign - Integrazione dei servizi di base di Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> AEM Assets</strong><br /> </td> 
   <td> Consente di inserire risorse dalla <strong> libreria AEM Assets</strong> nelle e-mail e nelle pagine di destinazione create in  Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Scoprite </a> di più 'integrazione Adobe Campaign -  AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trigger di Experience Cloud</strong><br /> </td> 
   <td> L'integrazione tra <strong>Triggers core service</strong> e  Adobe Campaign consente di inviare e-mail personalizzate ai clienti come reazione a comportamenti specifici seguiti sul sito Web da  Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/it/campaign/kb/triggers-and-campaign.html">Ulteriori </a> informazioni  Adobe Campaign -  Experience Cloud attiva l'integrazione.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong> Adobe Analytics - Connettori dati</strong><br /> </td> 
   <td> <strong>I connettori</strong>  dati (precedentemente noti come  Adobe Genesis) consentono  Adobe Campaign e  Adobe Analytics di interagire attraverso segmenti relativi al comportamento degli utenti in seguito a una campagna e-mail. Al contrario, invia indicatori e attributi delle campagne e-mail distribuite da  Adobe Campaign a  Adobe Analytics - Connettore dati.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Scopri </a> di più sull'integrazione Campaign - Connettori dati.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>

