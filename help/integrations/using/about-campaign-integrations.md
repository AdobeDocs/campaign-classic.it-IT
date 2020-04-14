---
title: Informazioni sulle integrazioni di Campaign
description: Informazioni sulle integrazioni funzionali disponibili tra la versione corrente di Adobe Campaign e [soluzioni Adobe Experience Cloud]
page-status-flag: never-activated
uuid: 087abdf0-b4b2-45e6-be21-b03bf85ddf83
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: campaign-integrations
discoiquuid: 0af1fd96-48ef-43c9-a03b-0f9a6e0e02fe
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0a4272ae13b469c7c17b8c3afa9748cbfbcf07ff

---


# Informazioni sulle integrazioni di Campaign {#about-campaign-integrations}

Adobe Experience Cloud è un set completo di soluzioni integrate all&#39;avanguardia, basate su una piattaforma dati comune con un set comune di potenti servizi di base.

Informazioni sulle integrazioni funzionali disponibili tra le soluzioni [e i servizi](https://docs.adobe.com/content/help/en/core-services/interface/marketing-cloud-integrations.html) di [base di Adobe Campaign e](https://docs.adobe.com/content/help/en/core-services/interface/about-core-services/core-services.html)Adobe Experience Cloud. Puoi quindi modernizzare le implementazioni della soluzione e implementare Experience Cloud in modo da poter utilizzare funzioni come gli attributi del cliente e i tipi di pubblico.

L&#39;elenco completo delle soluzioni e dei servizi di base Adobe che possono essere integrati con Adobe Campaign, nonché la documentazione associata, è disponibile in [questa sezione](#experience-cloud-integrations).

![](assets/ExCloud-solutions.png)


>[!CAUTION]
>
>La maggior parte di queste integrazioni richiede l&#39;accesso tramite un Adobe ID (IMS). Per ulteriori informazioni su questa implementazione, consulta [questa pagina](../../integrations/using/about-adobe-id.md).
>
>L&#39;implementazione IMS è un processo complesso, che può essere lungo. È strettamente riservato agli amministratori tecnici Adobe.

## Collegamento delle soluzioni {#working-with-experience-cloud-solutions}

A seconda dell&#39;ambiente, diverse soluzioni possono essere collegate ad Adobe Experience Cloud. Sono collegate come organizzazioni. Un&#39; **organizzazione** è l&#39;entità che consente all&#39;amministratore di configurare gruppi e utenti e di controllare il single sign-on in Experience Cloud. L&#39;organizzazione funziona come un&#39;azienda che abbraccia tutti i prodotti e le soluzioni Experience Cloud. Nella maggior parte dei casi, un&#39;organizzazione è il vostro nome aziendale. Tuttavia, un&#39;azienda può avere molte organizzazioni.

La gestione dell&#39;organizzazione e il collegamento degli account Adobe Experience Cloud sono descritti dettagliatamente nel portale [dell&#39;Aiuto di](https://marketing.adobe.com/resources/help/it_IT/mcloud/organizations.html)Adobe Experience Cloud.

>[!CAUTION]
>
>Durante la nuova installazione di Adobe Campaign o l&#39;integrazione di un&#39;installazione esistente con Adobe Experience Cloud, il servizio [](https://marketing.adobe.com/resources/help/en_US/mcvid/) Experience Cloud ID è abilitato. Questo servizio sostituisce il cookie permanente utilizzato innanzitutto da Adobe Campaign per le sue funzionalità di tracciamento.
>
>Un ID visitatore univoco verrà quindi assegnato ai destinatari che generano registri di tracciamento. Questo ID verrà salvato nel **[!UICONTROL Requester UUID (@sourceID)]** campo della **[!UICONTROL nms:trackingLogRcp]** tabella. I dati di tracciamento dei destinatari che esistevano prima dell’implementazione del servizio ID visitatore non saranno più utilizzabili.
>
>L’ID verrà quindi riconosciuto dalle altre soluzioni Adobe Experience Cloud con lo stesso [CNAME](https://marketing.adobe.com/resources/help/en_US/mcvid/mcvid_cname.html).

## Integrazioni Experience Cloud {#experience-cloud-integrations}

La seguente tabella consente di accedere alla documentazione di integrazione di Experience Cloud disponibile.

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
   <td> L'integrazione tra Adobe Campaign e Adobe Real-time Customer Data Platform consente di condividere i dati dei segmenti e importare audience in Adobe Campaign.<br /> <p><a href="https://docs.adobe.com/content/help/en/experience-platform/rtcdp/destinations/destinations-cat/adobe-destinations/adobe-campaign-destination.html">Ulteriori</a> informazioni sull'integrazione di Campaign - Adobe Real-time Customer Data Platform.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>IMS - Adobe ID</strong><br /> </td> 
   <td> Consente di connettersi ad Adobe Campaign con lo stesso Adobe ID delle altre soluzioni Adobe Experience Cloud.<br /> È necessario utilizzare un Adobe ID per effettuare l'accesso al fine di utilizzare alcune funzionalità collegate alle integrazioni Adobe Experience Cloud, in particolare i servizi di base.<br /> <p><a href="../../integrations/using/about-adobe-id.md">Ulteriori</a> informazioni sull'implementazione di Adobe ID con Adobe Campaign.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Experience Manager</strong><br /> </td> 
   <td> Consente di creare contenuti e-mail o moduli mappati al database Adobe Campaign direttamente in <strong>Adobe Experience Manager</strong>.<br /> <p><a href="../../integrations/using/about-adobe-experience-manager.md">Ulteriori</a> informazioni sull'integrazione di Adobe Campaign - Adobe Experience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Target</strong><br /> </td> 
   <td> Consente di inserire immagini calcolate in modo dinamico da <strong>Adobe Target</strong> all'apertura dell'e-mail creata e inviata da Adobe Campaign.<br /> <p><a href="../../integrations/using/integrating-with-adobe-target.md">Ulteriori</a> informazioni sull'integrazione di Adobe Campaign - Adobe Target.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servizio</strong><br /> di base Persone di <strong>Adobe Audience Manager</strong><br /> </td> 
   <td> Consente di condividere i tipi di pubblico tra le soluzioni e i core Adobe Experience Cloud che utilizzi.<br /> <p><a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Scopri di più</a> su Adobe Campaign - Servizio di base Persone e sulle integrazioni Adobe Audience Manager.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Servizio di base risorse</strong><br /> </td> 
   <td> Consente di inserire le risorse dalla libreria Adobe Experience Cloud nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-experience-cloud-assets">Ulteriori</a> informazioni su Adobe Campaign - Integrazione dei servizi di base Assets</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AEM Assets</strong><br /> </td> 
   <td> Consente di inserire le risorse dalla libreria Risorse <strong></strong> AEM nelle e-mail e nelle pagine di destinazione create in Adobe Campaign.<br /> <p><a href="../../integrations/using/configuring-access-to-assets.md#integrating-with-aem-assets">Ulteriori</a> informazioni sull'integrazione di Adobe Campaign - AEM Assets.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Experience Cloud Triggers</strong><br /> </td> 
   <td> L'integrazione tra il servizio <strong>di base</strong> Triggers e Adobe Campaign consente di inviare e-mail personalizzate ai clienti come reazione a comportamenti specifici seguiti sul sito Web da Adobe Analytics.<br /> <p><a href="https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html">Ulteriori</a> informazioni su Adobe Campaign - Integrazione degli attivatori Experience Cloud.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Analytics - Connettori dati</strong><br /> </td> 
   <td> <strong>I connettori</strong> dati (precedentemente noti come Adobe Genesis) consentono ad Adobe Campaign e Adobe Analytics di interagire attraverso i segmenti relativi al comportamento degli utenti in seguito a una campagna e-mail. Al contrario, invia indicatori e attributi delle campagne e-mail distribuite da Adobe Campaign ad Adobe Analytics - Connettore dati.<br /> <p><a href="../../platform/using/adobe-analytics-data-connector.md">Ulteriori</a> informazioni sull'integrazione Campaign - Connettori dati.</p><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Adobe Campaign Standard</strong> (offerta Prime)<br /> </td> 
   <td> Consente di replicare i dati su <strong>Campaign Standard</strong>, unendo il meglio di entrambe le applicazioni. Campaign Classic v7 dispone di strumenti avanzati per gestire il database di marketing principale. La replica dei dati di Campaign Classic v7 consente a Campaign Standard di sfruttare i dati avanzati in un ambiente semplice da utilizzare.<br /><p> <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Ulteriori</a> informazioni sull'integrazione di Adobe Campaign Classic - Adobe Campaign Standard.</p><br /></td> 
  </tr> 
 </tbody> 
</table>

