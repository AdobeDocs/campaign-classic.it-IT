---
product: campaign
title: Analisi web
description: Ulteriori informazioni sul pacchetto Web Analytics
hide: true
hidefromtoc: true
feature: Workflows, Analytics Integration
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 3%

---


# Analisi web{#web-analytics}



Per impostazione predefinita, i flussi di lavoro descritti di seguito vengono installati con il modulo **Connettori di analisi web**. Per ulteriori informazioni su questo modulo, consulta questa [sezione](../../integrations/using/gs-aa.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Invio di indicatori e attributi della campagna</span> <br /> </td> 
   <td> <span class="uicontrol">WebAnalyticsSendMetrics</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di inviare gli indicatori della campagna e-mail da Adobe Campaign a Adobe Experience Cloud Suite tramite il connettore Adobe® Analytics. Gli indicatori interessati sono i seguenti: <strong>Inviato</strong> (iSent), <strong>Numero totale di aperture</strong> (iTotalRecipientOpen), <strong>Numero totale di destinatari che hanno fatto clic</strong> (iTotalRecipientClick), <strong>Errori</strong> (iError), <strong>Rinuncia</strong> (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificazione dei contatti convertiti</span> <br /> </td> 
   <td> <span class="uicontrol">WebAnalyticsFindConvertito</span> <br /> </td> 
   <td> Questo flusso di lavoro indicizza i visitatori del sito che hanno completato l’acquisto dopo una campagna di remarketing. I dati recuperati da questo flusso di lavoro sono accessibili nel <span class="uicontrol">Rapporto sull'efficienza del remarketing</span>. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Eliminazione evento</span> <br /> </td> 
   <td> <span class="uicontrol">WebAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Questo flusso di lavoro ti consente di eliminare ogni evento dal campo del database in base al periodo configurato nel campo <span class="uicontrol">Durata</span>. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Ripristino di eventi Web</span> <br /> </td> 
   <td> <span class="uicontrol">WebAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Ogni ora, questo flusso di lavoro scarica segmenti sul comportamento degli utenti Internet su un determinato sito, li inserisce nel database di Adobe Campaign e avvia il flusso di lavoro di remarketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

