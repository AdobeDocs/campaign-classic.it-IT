---
title: Consegne
seo-title: Consegne
description: Consegne
seo-description: null
page-status-flag: never-activated
uuid: d323eb4d-937b-4b37-8400-942336f0a1b4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: technical-workflows
discoiquuid: 37612f62-68c0-4f73-a9a1-6d017aab862f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 6%

---


# Consegne{#deliveries}

I flussi di lavoro descritti di seguito sono installati per impostazione predefinita.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta</strong><br /> </td> 
   <td> <strong>Nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Reporting aggregates</span> <br /> </td> 
   <td> <span class="uicontrol">reportingAggregates</span> <br /> </td> 
   <td> Questo flusso di lavoro aggiorna gli aggregati utilizzati nei report. Viene attivato ogni giorno alle 2 del mattino per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Billing</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Questo flusso di lavoro invia il rapporto sull'attività del sistema all'operatore di 'fatturazione' tramite e-mail. Viene attivato il 25 di ogni mese per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Numero di profili di fatturazione attivi</span> <br /> </td> 
   <td> <span class="uicontrol">InvoiceActiveContactCount</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro conta il numero di profili attivi. Viene attivato ogni notte all'una per impostazione predefinita.</p> <p>“<strong>Profile</strong>” means a record of information (e.g.: a record in the nmsRecipient table or an external table containing a cookie ID, Customer ID, mobile identifier or other information relevant to a particular channel) representing an end-customer, prospect, or lead. La fatturazione riguarda solo i profili che sono "attivi". Un profilo è considerato "attivo" se il profilo è stato preso di mira o comunicato negli ultimi 12 mesi tramite qualsiasi canale.</p> <p>I canali Facebook e Twitter non vengono presi in considerazione.</p> <p>Puoi avere una panoramica del <span class="uicontrol">numero di profili</span> attivi dal menu <span class="uicontrol">Amministrazione</span> &gt; Gestione <span class="uicontrol"></span> campagne &gt; Metriche <span class="uicontrol"></span> cliente.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia alias</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di standardizzare i valori di enumerazione. Viene attivato ogni giorno alle 3 del mattino per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update for deliverability</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di creare l'elenco delle regole per la qualifica della posta indesiderata, nonché l'elenco dei domini e dei file MX nella piattaforma. Questo flusso di lavoro funziona solo se la porta HTTPS è aperta. Questi elenchi non vengono aggiornati a meno che non sia installato il modulo Consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro è il flusso di lavoro di manutenzione del database: effettua diversi calcoli dalle statistiche e dai processi ed elimina i dati obsoleti dal database in base alla configurazione definita nell'Assistente distribuzione. Viene attivato ogni giorno alle 4 del mattino per impostazione predefinita.</p> <p>For more information, refer to this <a href="../../production/using/database-cleanup-workflow.md">page</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia dei flussi di lavoro in pausa</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro analizza i flussi di lavoro messi in pausa con gravità impostata su normale e attiva avvisi e notifiche quando sono stati messi in pausa per troppo tempo. Dopo un mese, i flussi di lavoro tecnici in pausa vengono interrotti senza condizioni. Per impostazione predefinita, viene attivato ogni lunedì alle 5 del mattino.</p> <p>Per ulteriori informazioni, vedere <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Gestione dei flussi di lavoro</a>in pausa.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Notifica offerta</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro distribuisce le offerte approvate nell’ambiente online, così come in ogni categoria contenuta nel catalogo delle offerte.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Anteprima</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Questo flusso di lavoro analizza le consegne salvate nel calendario provvisorio (crea i registri provvisori). Per impostazione predefinita, viene attivato ogni giorno all’1 del mattino.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Questo flusso di lavoro esegue il ripristino e il consolidamento delle informazioni di tracciamento. Garantisce inoltre il ricalcolo delle statistiche di monitoraggio e consegna, in particolare quelle utilizzate dai flussi di lavoro di archiviazione di Message Center. Per impostazione predefinita, viene attivato una volta all'ora. <br /> </td> 
  </tr> 
 </tbody> 
</table>

