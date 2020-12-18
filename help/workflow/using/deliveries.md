---
solution: Campaign Classic
product: campaign
title: Consegne
description: Ulteriori informazioni sui flussi di lavoro di distribuzione predefiniti
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '436'
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
   <td> <p>Questo flusso di lavoro conta il numero di profili attivi. Viene attivato ogni notte all'una per impostazione predefinita.</p> <p>"<strong>Profilo</strong>" indica un record di informazioni (ad esempio: un record nella tabella nmsRecipient o una tabella esterna contenente un ID cookie, un ID cliente, un identificatore mobile o altre informazioni pertinenti a un canale specifico) che rappresenta un cliente finale, un potenziale o un lead. La fatturazione riguarda solo i profili che sono "attivi". Un profilo è considerato "attivo" se il profilo è stato preso di mira o comunicato negli ultimi 12 mesi tramite qualsiasi canale.</p> <p>I canali Facebook e Twitter non vengono presi in considerazione.</p> <p>È possibile ottenere una panoramica del <span class="uicontrol">numero di profili attivi</span> dal menu <span class="uicontrol">Amministrazione</span> &gt; <span class="uicontrol">Gestione campagna</span> &gt; <span class="uicontrol">Metriche cliente</span>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia alias</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di standardizzare i valori di enumerazione. Viene attivato ogni giorno alle 3 del mattino per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Update for deliverability</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Questo flusso di lavoro consente di creare l'elenco delle regole per la qualifica della posta indesiderata, nonché l'elenco dei domini e dei file MX nella piattaforma. Questo flusso di lavoro funziona solo se la porta HTTPS è aperta. Questi elenchi non vengono aggiornati a meno che non sia installato il modulo di recapito.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro è il flusso di lavoro di manutenzione del database: effettua diversi calcoli dalle statistiche e dai processi ed elimina i dati obsoleti dal database in base alla configurazione definita nell'Assistente distribuzione. Viene attivato ogni giorno alle 4 del mattino per impostazione predefinita.</p> <p>Per ulteriori informazioni, fare riferimento a questa <a href="../../production/using/database-cleanup-workflow.md">pagina</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia dei flussi di lavoro in pausa</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro analizza i flussi di lavoro messi in pausa con gravità impostata su normale e attiva avvisi e notifiche quando sono stati messi in pausa per troppo tempo. Dopo un mese, i flussi di lavoro tecnici in pausa vengono interrotti senza condizioni. Per impostazione predefinita, viene attivato ogni lunedì alle 5 del mattino.</p> <p>Per ulteriori informazioni, consultare <a href="../../workflow/using/monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Gestione dei flussi di lavoro in pausa</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Notifica offerta</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro distribuisce le offerte approvate nell'ambiente online, così come ogni categoria contenuta nel catalogo delle offerte.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Anteprima</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Questo flusso di lavoro analizza le consegne salvate nel calendario provvisorio (crea i registri provvisori). Viene attivato ogni giorno alle 1 del mattino per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Questo flusso di lavoro esegue il ripristino e il consolidamento delle informazioni di tracciamento. Garantisce inoltre il ricalcolo delle statistiche di monitoraggio e consegna, in particolare quelle utilizzate dai flussi di lavoro di archiviazione di Message Center. Per impostazione predefinita, viene attivato una volta all'ora. <br /> </td> 
  </tr> 
 </tbody> 
</table>

