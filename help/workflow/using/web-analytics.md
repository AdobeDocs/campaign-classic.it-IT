---
product: campaign
title: Analisi web
description: Ulteriori informazioni sul pacchetto Web Analytics
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Analytics Integration
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 4%

---


# Analisi web{#web-analytics}



I flussi di lavoro descritti di seguito sono installati con **Connettori di Web Analytics** modulo per impostazione predefinita. Per ulteriori informazioni su questo modulo, consulta questo [sezione](../../platform/using/adobe-analytics-connector.md).

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
   <td> Questo flusso di lavoro consente di inviare gli indicatori delle campagne e-mail da Adobe Campaign a Adobe Experience Cloud Suite tramite il connettore Adobe® Analytics. Gli indicatori interessati sono i seguenti: <strong>Inviato</strong> (Inviato), <strong>Numero totale di aperture</strong> (iTotalRecipientOpen), <strong>Numero totale di destinatari che hanno fatto clic su</strong> (iTotalRecipientClick), <strong>Errori</strong> (iError), <strong>Rinuncia</strong> (opt-out) (iOptOut).<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Identificazione dei contatti convertiti</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsFindConverted</span> <br /> </td> 
   <td> Questo flusso di lavoro indicizza i visitatori del sito che hanno completato l’acquisto dopo una campagna di remarketing. I dati recuperati da questo flusso di lavoro sono accessibili nel <span class="uicontrol">Rapporto sull’efficienza di remarketing</span> (Fai riferimento a questo <a href="../../platform/using/adobe-analytics-connector.md#creating-a-re-marketing-campaign"> page</a>). <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Eliminazione eventi</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsPurgeWebEvents</span> <br /> </td> 
   <td> Questo flusso di lavoro ti consente di eliminare ogni evento dal campo del database in base al periodo configurato nel <span class="uicontrol">Durata</span> campo . <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Recupero di eventi web</span> <br /> </td> 
   <td> <span class="uicontrol">webAnalyticsGetWebEvents</span> <br /> </td> 
   <td> Ogni ora, questo flusso di lavoro scarica i segmenti sul comportamento degli utenti Internet su un dato sito, li inserisce nel database Adobe Campaign e avvia il flusso di lavoro di remarketing. <br /> </td> 
  </tr> 
 </tbody> 
</table>

