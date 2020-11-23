---
solution: Campaign Classic
product: campaign
title: Analisi web
description: Ulteriori informazioni sul pacchetto Web Analytics
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 3%

---


# Analisi web{#web-analytics}

I flussi di lavoro descritti di seguito sono installati con il modulo di connettori **di** Web Analytics per impostazione predefinita. For more on this module, refer to this [section](../../platform/using/adobe-analytics-data-connector.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Invio di indicatori e attributi della campagna</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsSendMetrics</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di inviare gli indicatori delle campagne e-mail da  Adobe Campaign ad Adobe Experience Cloud Suite tramite il connettore  Adobe Genesis®. Gli indicatori interessati sono i seguenti: <strong>Inviato</strong> (inviato), conteggio <strong>totale delle aperture</strong> (iTotalRecipientOpen), numero <strong>totale dei destinatari che hanno fatto clic</strong> (iTotalRecipientClick), <strong>Errori</strong> (iError), <strong>Rinuncia</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificazione dei contatti convertiti</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Questo flusso di lavoro indicizza i visitatori del sito che hanno completato l’acquisto dopo una campagna di remarketing. I dati recuperati da questo flusso di lavoro sono accessibili nel rapporto <span class="uicontrol">di efficienza di</span> ricommercializzazione (fare riferimento a questa <a href="../../platform/using/adobe-analytics-data-connector.md#creating-a-re-marketing-campaign"> pagina</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Rimozione eventi</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di eliminare ogni evento dal campo del database in base al periodo configurato nel campo <span class="uicontrol">Durata</span> . <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recupero di eventi Web</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Ogni ora, questo flusso di lavoro scarica i segmenti sul comportamento degli utenti Internet in un dato sito, li inserisce nel database Adobe Campaign  e avvia il flusso di lavoro di remarketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

