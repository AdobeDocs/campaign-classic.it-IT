---
product: campaign
title: Informazioni sulle integrazioni di Campaign
description: Usa altre soluzioni Adobe e combina le loro diverse funzionalità con Campaign
feature: Overview
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
topic-tags: campaign-integrations
exl-id: ceb584da-bc97-4b71-9499-59df5e6d10c3
source-git-commit: 597d24fa780a324507c56c55a5309b6ee1cf46eb
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 4%

---

# Guida introduttiva alle integrazioni Adobe Campaign {#about-campaign-integrations}

Adobe Experience Cloud è un set completo di soluzioni integrate all’avanguardia, basate su una piattaforma di dati comune e con un set comune di potenti soluzioni e app.

Ulteriori informazioni sulle integrazioni funzionali disponibili tra le soluzioni Adobe Campaign e Adobe Experience Cloud in [questa pagina](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/integrations){_blank}.

L’elenco completo dei servizi di app e soluzioni di Adobe che possono essere integrati con Adobe Campaign, e la relativa documentazione, sono disponibili in [questa sezione](#experience-cloud-integrations).

>[!CAUTION]
>
>Queste integrazioni richiedono l’implementazione di Adobe Identity Management System (IMS), per accedere tramite un Adobe ID. [Per ulteriori informazioni, consulta questa pagina](../../integrations/using/about-adobe-id.md).
>

## Collegamento delle soluzioni {#working-with-experience-cloud-solutions}

È possibile collegare più soluzioni a Adobe Experience Cloud. Il **organizzazione** è l&#39;entità cliente che consente all&#39;amministratore di configurare gruppi e utenti e di controllare il single sign-on (SSO) in Adobe Experience Cloud. L’organizzazione si comporta come un’azienda di accesso che abbraccia tutti i prodotti e le soluzioni di Experience Cloud. Nella maggior parte dei casi l’organizzazione corrisponde al nome aziendale, Tuttavia, un’azienda può avere molte organizzazioni.

La gestione dell&#39;organizzazione e il collegamento degli account Adobe Experience Cloud sono descritti in dettaglio nella [Portale della guida di Adobe Experience Cloud](https://experienceleague.adobe.com/en/docs/core-services/interface/administration/organizations){_blank}.

## Gestione di identità e cookie {#id-and-cookies}

Durante l’installazione di Adobe Campaign o l’integrazione di un’installazione esistente con Adobe Experience Cloud, il [Servizio Adobe Experience Cloud Identity](https://experienceleague.adobe.com/en/docs/id-service/using/home){_blank} è abilitato. Questo servizio sostituisce il cookie permanente utilizzato in primo luogo da Adobe Campaign per le sue funzionalità di tracciamento.

Il servizio Adobe Experience Cloud Identity (servizio ID) fornisce un ID universale e costante che identifica i visitatori in tutte le soluzioni dell’Experience Cloud.

Ai destinatari che generano i registri di tracciamento verrà assegnato un ID visitatore univoco. Questo ID verrà salvato in **[!UICONTROL Requester UUID (@sourceID)]** campo del **[!UICONTROL nms:trackingLogRcp]** tabella. **I dati di tracciamento dei destinatari che esistevano prima dell’implementazione del servizio ID visitatore non saranno più utilizzabili**.

L’ID verrà quindi riconosciuto dalle altre soluzioni Adobe Experience Cloud con lo stesso CNAME. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/id-service/using/reference/analytics-reference/cname){_blank}.

## Integrazioni di Experience Cloud {#experience-cloud-integrations}

La tabella seguente fornisce l’accesso alla documentazione disponibile sull’integrazione di Experience Cloud.

<table> 
 <thead> 
  <tr> 
   <th> Soluzioni e app<br /> </th> 
   <th> Casi d’uso<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Real-time Customer Data Platform (RTCDP)</strong><br /> </td> 
   <td> Configura l’integrazione tra Adobe Campaign e Adobe Real-time Customer Data Platform (RTCDP) per condividere i dati dei segmenti e importare i tipi di pubblico in Adobe Campaign.<br /> <p><a href="../../integrations/using/get-started-sources-destinations.md">Ulteriori informazioni</a> informazioni sull’integrazione di Campaign - Adobe Real-time Customer Data Platform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Identity Management System (IMS) - Adobe ID</strong><br /> </td> 
   <td> Configura Adobe IMS per connettersi ad Adobe Campaign con lo stesso Adobe ID utilizzato per le altre soluzioni Adobe Experience Cloud.<br /> Per utilizzare alcune funzionalità collegate alle integrazioni Adobe Experience Cloud, è necessario utilizzare un’Adobe ID per effettuare l’accesso.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Ulteriori informazioni</a> informazioni sull’implementazione di Adobe ID con Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Configura questa integrazione per creare contenuti e-mail o moduli mappati al database di Adobe Campaign direttamente in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Ulteriori informazioni</a> informazioni sull’integrazione Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Configura questa integrazione per inserire immagini calcolate dinamicamente da <strong>Adobe Target</strong> all’apertura dell’e-mail creata e inviata da Adobe Campaign.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Ulteriori informazioni</a> informazioni sull’integrazione Adobe Campaign - Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td><strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Configura questa integrazione per condividere i tipi di pubblico tra le soluzioni e le app Adobe Experience Cloud che utilizzi.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Ulteriori informazioni</a> informazioni sulle integrazioni Adobe Campaign - Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Risorse</strong><br /> </td> 
   <td> Configura questa integrazione per inserire le risorse dalla libreria Adobe Experience Cloud nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Ulteriori informazioni</a> informazioni sull’integrazione di Adobe Campaign con Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Configura questa integrazione per inserire risorse dal tuo <strong>AEM Assets</strong> nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Ulteriori informazioni</a> informazioni sull’integrazione Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Trigger Experience Cloud</strong><br /> </td> 
   <td> Configurare l’integrazione tra <strong>Adobe Experience Cloud Triggers</strong> e Adobe Campaign per inviare e-mail personalizzate ai clienti come reazione a comportamenti specifici tracciati sul sito web da Adobe Analytics.<br /> <p><a href="about-triggers.md">Ulteriori informazioni</a> informazioni su Adobe Campaign: integrazione Experience Cloud triggers.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Connettore Adobe Analytics</strong><br /> </td> 
   <td> Configura questa integrazione per consentire ad Adobe Campaign e Adobe Analytics di interagire attraverso i segmenti relativi al comportamento degli utenti a seguito di una campagna e-mail. Al contrario, invia ad Adobe Analytics indicatori e attributi delle campagne e-mail consegnate da Adobe Campaign.<br /> <p><a href="../../integrations/using/gs-aa.md">Ulteriori informazioni</a> informazioni sull’integrazione Campaign - Analytics Connectors.</p><br /> </td> 
  </tr> 
 </tbody> 
</table>
