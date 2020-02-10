---
title: Analisi Web
seo-title: Analisi Web
description: Analisi Web
seo-description: null
page-status-flag: never-activated
uuid: 63742453-16d9-48c2-9a3d-d96f5b131fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: cc2d4741-2b26-4933-a28d-5dd7b5f436be
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# Analisi Web{#web-analytics}

I flussi di lavoro descritti di seguito sono installati con il modulo di connettori **di** Web Analytics per impostazione predefinita. Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Invio di indicatori e attributi</span> della campagna <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span><br /> </td> 
   <td> Questo flusso di lavoro consente di inviare indicatori di campagna e-mail da Adobe Campaign ad Adobe Experience Cloud Suite tramite il connettore Adobe® Genesis. Gli indicatori interessati sono i seguenti: <strong>Inviato</strong> (iSent), conteggio <strong>totale delle aperture</strong> (iTotalRecipientOpen), numero <strong>totale dei destinatari che hanno fatto clic</strong> (iTotalRecipientClick), <strong>Errori</strong> (iError), <strong>Rifiuto</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificazione dei contatti</span> convertiti <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span><br /> </td> 
   <td> Questo flusso di lavoro indicizza i visitatori del sito che hanno completato l’acquisto dopo una campagna di remarketing. I dati recuperati da questo flusso di lavoro sono accessibili nel rapporto <span class="uicontrol">di efficienza di</span> ricommercializzazione (fare riferimento a questa <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> pagina</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Eliminazione</span> eventi <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span><br /> </td> 
   <td> Questo flusso di lavoro consente di eliminare ogni evento dal campo del database in base al periodo configurato nel campo <span class="uicontrol">Durata</span> . <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recupero di eventi</span> Web <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span><br /> </td> 
   <td> Ogni ora, questo flusso di lavoro scarica i segmenti sul comportamento degli utenti Internet in un dato sito, li inserisce nel database Adobe Campaign e avvia il flusso di lavoro di remarketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

