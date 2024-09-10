---
product: campaign
title: Consegne
description: Ulteriori informazioni sui flussi di lavoro predefiniti per le consegne
feature: Workflows
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 4%

---


# Consegne{#deliveries}



Per impostazione predefinita, i flussi di lavoro descritti di seguito sono installati con il modulo **Consegne**.

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
   <td> Questo flusso di lavoro invia il rapporto sull’attività del sistema all’operatore di "fatturazione" tramite e-mail. Per impostazione predefinita viene attivato il 25 di ogni mese.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia alias</span> <br /> </td> 
   <td> <span class="uicontrol">aliasCleansing</span> <br /> </td> 
   <td> Questo flusso di lavoro standardizza i valori di enumerazione. Viene attivato ogni giorno alle 3 per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Aggiorna per il recapito messaggi</span> <br /> </td> 
   <td> <span class="uicontrol">deliverabilityUpdate</span> <br /> </td> 
   <td> Questo flusso di lavoro ti consente di creare l’elenco delle regole di qualifica della posta non recapitata, nonché l’elenco di domini e MX nella piattaforma. Questo flusso di lavoro funziona solo se la porta HTTPS è aperta. Questi elenchi non vengono aggiornati a meno che non sia installato il modulo Deliverability.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Database cleanup</span> <br /> </td> 
   <td> <span class="uicontrol">cleanup</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro è il flusso di lavoro di manutenzione del database: esegue calcoli diversi dalle statistiche e dai processi ed elimina i dati obsoleti dal database in base alla configurazione definita nella procedura guidata di distribuzione. Viene attivato ogni giorno alle 4 per impostazione predefinita.</p> <p>Per ulteriori informazioni, consulta questa <a href="../../production/using/database-cleanup-workflow.md">pagina</a>.</p> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Pulizia flussi di lavoro sospesi</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPausedWorkflows</span> <br /> </td> 
   <td> <p>Questo flusso di lavoro analizza i flussi di lavoro in pausa la cui gravità è impostata su Normal e attiva avvisi e notifiche se sono stati messi in pausa troppo a lungo. Dopo un mese, i flussi di lavoro tecnici in pausa vengono interrotti incondizionatamente. Per impostazione predefinita viene attivato ogni lunedì alle 5.</p> <p>Per ulteriori informazioni, consultare <a href="monitoring-workflow-execution.md#handling-of-paused-workflows" target="_blank">Gestione dei flussi di lavoro in pausa</a>.</p></td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Notifica offerta</span> <br /> </td> 
   <td> <span class="uicontrol">offerMgt</span> <br /> </td> 
   <td> Questo flusso di lavoro distribuisce le offerte approvate nell'ambiente online, nonché in ogni categoria contenuta nel catalogo delle offerte.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Forecasting</span> <br /> </td> 
   <td> <span class="uicontrol">forecasting</span> <br /> </td> 
   <td> Questo flusso di lavoro analizza le consegne salvate nel calendario provvisorio (crea registri provvisori). Viene attivato ogni giorno all'1 per impostazione predefinita.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Tracciamento</span> <br /> </td> 
   <td> <span class="uicontrol">tracciamento</span> <br /> </td> 
   <td> Questo flusso di lavoro esegue il ripristino e il consolidamento delle informazioni di tracciamento. Assicura inoltre il ricalcolo delle statistiche di tracciamento e consegna, in particolare quelle utilizzate dai flussi di lavoro di archiviazione del Centro messaggi. Per impostazione predefinita viene attivato una volta all’ora. <br /> </td> 
  </tr> 
 </tbody> 
</table>

