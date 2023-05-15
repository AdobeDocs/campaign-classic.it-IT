---
product: campaign
title: Consegne
description: Ulteriori informazioni sui flussi di lavoro di consegna predefiniti
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 6%

---


# Consegne{#deliveries}



I flussi di lavoro descritti di seguito sono installati con **Consegne** modulo per impostazione predefinita.

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
   <td> Questo flusso di lavoro aggiorna gli aggregati utilizzati nei rapporti. Viene attivato ogni giorno alle 2 per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Billing</span> <br /> </td> 
   <td> <span class="uicontrol">billing</span> <br /> </td> 
   <td> Questo flusso di lavoro invia il rapporto sull’attività del sistema all’operatore di "fatturazione" tramite e-mail. Viene attivato il 25 di ogni mese per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia alias</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Questo flusso di lavoro standardizza i valori di enumerazione. Viene attivato ogni giorno alle 3 per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aggiornamento per il recapito messaggi</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Questo flusso di lavoro ti consente di creare l’elenco delle regole di qualificazione della posta non recapitata, nonché l’elenco dei domini e degli MX nella piattaforma. Questo flusso di lavoro funziona solo se la porta HTTPS è aperta. Questi elenchi non vengono aggiornati a meno che non sia installato il modulo Consegne.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro è il flusso di lavoro di manutenzione del database: effettua calcoli diversi dalle statistiche e dai processi ed elimina dati obsoleti dal database in base alla configurazione definita nell'assistente alla distribuzione. Viene attivato ogni giorno alle 4 per impostazione predefinita.</p> <p>Per ulteriori informazioni, consulta <a href="../../production/using/database-cleanup-workflow.md">page</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia dei flussi di lavoro in pausa</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro analizza i flussi di lavoro in pausa con la gravità impostata su normale e attiva avvisi e notifiche quando sono stati messi in pausa per troppo tempo. Dopo un mese, i flussi di lavoro tecnici in pausa vengono interrotti incondizionatamente. Per impostazione predefinita viene attivato ogni lunedì alle 5.</p> <p>Per ulteriori informazioni, consulta <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Gestione dei flussi di lavoro in pausa</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Notifica di offerta</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro distribuisce le offerte approvate nell’ambiente online, nonché in ogni categoria contenuta nel catalogo delle offerte.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Forecasting</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Questo flusso di lavoro analizza le consegne salvate nel calendario provvisorio (crea registri provvisori). Viene attivato ogni giorno all’1 per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracking</span> <br /> </td> 
   <td> <span class="uicontrol">tracking</span> <br /> </td> 
   <td> Questo flusso di lavoro esegue il ripristino e il consolidamento delle informazioni di tracciamento. Assicura inoltre il ricalcolo delle statistiche di tracciamento e consegna, in particolare quelle utilizzate dai flussi di lavoro di archiviazione Message Center. Per impostazione predefinita viene attivato una volta all’ora. <br /> </td> 
  </tr> 
 </tbody> 
</table>

