---
product: campaign
title: Informazioni sulle integrazioni di Campaign
description: Usa altre soluzioni Adobe e combina le loro diverse funzionalità con Campaign
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 12%

---

# Guida introduttiva alle integrazioni Adobe Campaign {#about-campaign-integrations}



Adobe Experience Cloud è un set completo di soluzioni integrate di altissimo livello, costruito su una piattaforma dati comune con un set comune di potenti servizi di base.

Scopri le integrazioni funzionali disponibili tra Adobe Campaign e [Soluzioni Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/marketing-cloud-integrations.html) e [servizi principali](https://experienceleague.adobe.com/docs/core-services/interface/about-core-services/core-services.html). Puoi quindi modernizzare le implementazioni della soluzione e implementarlo in modo da poter utilizzare funzioni quali gli attributi del cliente e i tipi di pubblico.

![](assets/ExCloud-solutions.png)

L’elenco completo delle soluzioni e dei servizi di base di Adobe che possono essere integrati con Adobe Campaign e la relativa documentazione sono disponibili in [questa sezione](#experience-cloud-integrations).

>[!CAUTION]
>
>La maggior parte di queste integrazioni richiede l’implementazione di Adobe Identity Management System (IMS) per accedere tramite un Adobe ID. [Per ulteriori informazioni, consulta questa pagina](../../integrations/using/about-adobe-id.md).

## Collegamento delle soluzioni {#working-with-experience-cloud-solutions}

È possibile collegare più soluzioni a Adobe Experience Cloud. La **organizzazione** è l’entità cliente che consente all’amministratore di configurare gruppi e utenti e di controllare il single sign-on (SSO) in Adobe Experience Cloud. L’organizzazione agisce come un’azienda che abbraccia tutti i prodotti e le soluzioni Experience Cloud. Nella maggior parte dei casi l’organizzazione corrisponde al nome aziendale, ma una stessa azienda può avere molte organizzazioni.

La gestione dell&#39;organizzazione e il collegamento degli account Adobe Experience Cloud sono descritti nel [Portale guida di Adobe Experience Cloud](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html).

## Gestione di identità e cookie {#id-and-cookies}

Quando installi Adobe Campaign o integri un&#39;installazione esistente con Adobe Experience Cloud, la [Servizio Adobe Experience Cloud Identity](https://experienceleague.adobe.com/docs/id-service/using/home.html) è abilitato. Questo servizio sostituisce il cookie permanente utilizzato principalmente da Adobe Campaign per le sue funzionalità di tracciamento.

Il servizio Adobe Experience Cloud Identity (servizio ID) fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni dell’Experience Cloud.

Ai destinatari che generano registri di tracciamento verrà assegnato un ID visitatore univoco. Questo ID verrà salvato nella **[!UICONTROL Requester UUID (@sourceID)]** campo **[!UICONTROL nms:trackingLogRcp]** tabella. **I dati di tracciamento dei destinatari che esistevano prima dell’implementazione del servizio ID visitatore non saranno più utilizzabili**.

L&#39;ID verrà quindi riconosciuto dalle altre soluzioni Adobe Experience Cloud con lo stesso CNAME. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/id-service/using/reference/analytics-reference/cname.html)

## Integrazioni Experience Cloud {#experience-cloud-integrations}

La tabella seguente fornisce l’accesso alla documentazione di integrazione di Experience Cloud disponibile.

<table> 
 <thead> 
  <tr> 
   <th> Soluzione e servizi di base<br /> </th> 
   <th> Casi d’uso<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> L’integrazione tra Adobe Campaign e Adobe Real-time Customer Data Platform (RTCDP) consente di condividere i dati dei segmenti e importare i tipi di pubblico in Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Ulteriori informazioni</a> informazioni sull’integrazione Campaign - Adobe Real-time Customer Data Platform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Consente di connettersi ad Adobe Campaign con lo stesso Adobe ID delle altre soluzioni Adobe Experience Cloud.<br /> Per accedere è necessario utilizzare un Adobe ID per utilizzare alcune funzionalità collegate alle integrazioni Adobe Experience Cloud, in particolare i servizi core.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Ulteriori informazioni</a> informazioni sull’implementazione di Adobe ID con Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Consente di creare contenuti e-mail o moduli mappati al database Adobe Campaign direttamente in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Ulteriori informazioni</a> informazioni sull’integrazione Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Consente di inserire immagini calcolate dinamicamente da <strong>Adobe Target</strong> all’apertura dell’e-mail creata e inviata da Adobe Campaign.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Ulteriori informazioni</a> informazioni sull’integrazione Adobe Campaign - Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servizio core persone</strong><br /> <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Consente di condividere i tipi di pubblico tra le soluzioni Adobe Experience Cloud e il nucleo utilizzato.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Ulteriori informazioni</a> informazioni su Adobe Campaign - Servizio core People e integrazioni Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servizio core Assets</strong><br /> </td> 
   <td> Consente di inserire gli assets dalla libreria di Adobe Experience Cloud nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Ulteriori informazioni</a> informazioni su Adobe Campaign - Integrazione del servizio core Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Consente di inserire risorse dal <strong>AEM Assets</strong> nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Ulteriori informazioni</a> informazioni sull’integrazione Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trigger di Experience Cloud</strong><br /> </td> 
   <td> Integrazione tra <strong>Triggers servizio principale</strong> e Adobe Campaign consente di inviare e-mail personalizzate ai clienti come reazione a comportamenti specifici tracciati sul sito web da Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/it/campaign/kb/triggers-and-campaign.html">Ulteriori informazioni</a> informazioni su Adobe Campaign - Integrazione dei trigger Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Connettore Adobe Analytics</strong><br /> </td> 
   <td> <strong>Connettore Adobe Analytics</strong> consente ad Adobe Campaign e Adobe Analytics di interagire attraverso i segmenti relativi al comportamento degli utenti dopo una campagna e-mail. Al contrario, invia ad Adobe Analytics gli indicatori e gli attributi delle campagne e-mail inviate da Adobe Campaign.<br /> <p><a href="../../platform/using/adobe-analytics-connector.md">Ulteriori informazioni</a> informazioni sull’integrazione di Campaign - Connettori di Analytics.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
