---
solution: Campaign Classic
product: campaign
title: Elenco dei report
description: Elenco dei report
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 1%

---


# Elenco dei report{#list-of-reports}

## Report sulle consegne {#reports-on-deliveries}

I report incorporati forniti da  Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta [questa sezione](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Attività utente (attività destinatario)<br /> </td> 
   <td> Suddivisione di aperture, clic e transazioni per periodo di tempo.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Velocità di consegna (throughput)<br /> </td> 
   <td> Diffusione di grafici throughput, in messaggi/ora e Mbit/s.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori e rimbalzi (errori)<br /> </td> 
   <td> Bounces e non deliverable per causa e dominio.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (deliveryFeedback)<br /> </td> 
   <td> Riepilogo degli indicatori chiave per tenere traccia del comportamento del destinatario.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Indicatori di tracciamento di una distribuzione a un’applicazione mobile.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Browser (browserStatistics)<br /> </td> 
   <td> Statistiche sui browser utilizzati dai destinatari che hanno fatto clic nei messaggi.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione su social network (deliveryForward)<br /> </td> 
   <td> Condivisione dell'attività e pubblicazione di statistiche aperte.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Clic a caldo (a sinistra)<br /> </td> 
   <td> Visualizza il messaggio e le percentuali di clic sovrapposte.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Rapporto ipotesi (deliveryHypoeses)<br /> </td> 
   <td> Visualizza il riepilogo delle misure in base alle ipotesi di consegna.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di consegna (statisticsPerDelivery)<br /> </td> 
   <td> Statistiche (messaggi elaborati, messaggi consegnati, rimbalzi netti, rimbalzi morbidi, clic, sottoscrizioni) per dominio e-mail.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione delle statistiche sulle attività (forwardActivities)<br /> </td> 
   <td> Analisi delle attività di condivisione, aperture e iscrizioni per periodo di tempo.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di tracciamento (trackingStatistics)<br /> </td> 
   <td> Apri, fai clic su e crea un rapporto sui tassi di transazione.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo consegna (deliverySending)<br /> </td> 
   <td> Riepilogo degli indicatori di consegna: target, esclusione e messaggi inviati.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo consegna (deliveryStatistics)<br /> </td> 
   <td> Tabella di riepilogo per le consegne selezionate: Destinazioni, Esclusioni e Messaggi Inviati.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Sistemi operativi (osStatistics)<br /> </td> 
   <td> Statistiche sui sistemi operativi utilizzati dai destinatari che hanno fatto clic in un messaggio.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (deliveryFeedbackSocial)<br /> </td> 
   <td> Tasso di reattività di distribuzione e disaggregazione della reazione.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> URL e fate clic su throughput (topUrlDelivery)<br /> </td> 
   <td> La maggior parte degli URL reattivi e dei flussi di clic associati.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle campagne {#reports-on-campaigns}

I report sulle campagne riguardano i dati nella tabella **nms:operation** .

I report incorporati forniti da  Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta [questa sezione](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Attività utente (operationRecipientActivity)<br /> </td> 
   <td> La suddivisione di aperture, clic e transazioni per periodo di tempo dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Velocità di consegna (operationThroughput)<br /> </td> 
   <td> I grafici della velocità effettiva di distribuzione, nei messaggi e-mail/ora e Mbit/s, dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Spese campagna (budgetOperationExpenses)<br /> </td> 
   <td> Visualizza in dettaglio le righe della campagna, a seconda di Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori e rimbalzi (operationErrors)<br /> </td> 
   <td> I fatturati e i non consegnabili per causa e dominio dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle righe dei costi (budgetExplorerOperation)<br /> </td> 
   <td> L'analisi descrittiva delle linee di costo, dipende da MRM.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (operationFeedback)<br /> </td> 
   <td> Panoramica degli indicatori di tracciamento chiave: Le aperture, i clic e le transazioni dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione su social network (operationForward)<br /> </td> 
   <td> La condivisione di attività e la pubblicazione di statistiche aperte dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rapporto di ipotesi (operationHypoeses)<br /> </td> 
   <td> Visualizza il riepilogo delle misure di ipotesi per le consegne della campagna, a seconda di Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione delle statistiche sulle attività (forwardActivityOpt)<br /> </td> 
   <td> L'analisi delle attività di condivisione, delle aperture e delle sottoscrizioni per periodo di tempo dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo consegna (operationStatistics)<br /> </td> 
   <td> Grafico di riepilogo delle consegne della campagna: Destinazioni, Esclusioni e Messaggi Inviati.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL e fate clic su throughput (operationTopUrlDelivery)<br /> </td> 
   <td> La maggior parte degli URL reattivi e dei flussi di clic associati dipendono da Campaign.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sui servizi {#reports-on-services}

I rapporti sui servizi riguardano i dati nella tabella **nms:service** .

I report incorporati forniti da  Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta le relative guide.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Acquisizioni di ventole (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Quali applicazioni Web hanno permesso le acquisizioni potenziali? Dipende dal componente aggiuntivo Social marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione delle sottoscrizioni (mobileAppDistribution)<br /> </td> 
   <td> La suddivisione delle iscrizioni attive per applicazione mobile dipende dal componente aggiuntivo per canale app mobile.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tracciamento iscrizione (subscriptionsProgress)<br /> </td> 
   <td> Evoluzione delle sottoscrizioni ai servizi di informazione<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (socialReactionRate)<br /> </td> 
   <td> Quali sono i tassi di reattività per le ultime consegne? Dipende dal componente aggiuntivo Social marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Velocità di reattività (mobileAppReactivityRate)<br /> </td> 
   <td> Il tasso di reattività per le ultime consegne dipende dal componente aggiuntivo per canale app mobile.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Report budget {#budget-reports}

I report incorporati forniti da  Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta [questa sezione](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Costi collegati al programma o ai programmi (budgetProgramCost)<br /> </td> 
   <td> Ripartizione dei costi del programma.<br /> </td> 
   <td> nms:programma<br /> </td> 
  </tr> 
  <tr> 
   <td> Andamento del budget (budgetEvolution)<br /> </td> 
   <td> Evoluzione dei costi di bilancio per livello di impegno.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione cumulativa del bilancio (budgetEvolutionCumulative)<br /> </td> 
   <td> Evoluzione dei costi di bilancio cumulati, ripartiti per livello di spesa comunitaria<br /> . </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle linee dei costi (budgetExplorerBudget)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle righe dei costi (budgetExplorer)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle righe dei costi (budgetExplorerPlan)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:piano<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle righe dei costi (budgetExplorerProgram)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:programma<br /> </td> 
  </tr> 
  <tr> 
   <td> Sintesi del bilancio (bilancio)<br /> </td> 
   <td> Istantanea dei principali costi, categorie di spesa e budget.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle simulazioni {#reports-on-simulations}

I rapporti sulle simulazioni riguardano i dati nella tabella **nms:simulation** .

I report incorporati forniti da  Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta le relative guide.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dettagli delle esclusioni di simulazione (dlvSimuLossesDetail)<br /> </td> 
   <td> Tabella dettagliata di tutte le cause di esclusione.<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione delle offerte per classificazione (offerSimulationRanking)<br /> </td> 
   <td> Suddivisione delle offerte nella simulazione, per classificazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo simulazione (dlvSimuLossesSummary)<br /> </td> 
   <td> Riepilogo dei volumi di simulazione ed esclusioni.<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di sovrapposizione (dlvSimuOverlapping)<br /> </td> 
   <td> Volume di sovrapposizione target di consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo delle esclusioni dovute alla simulazione (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabella delle esclusioni dovute alla simulazione.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle applicazioni Web {#reports-on-web-applications}

I report sulle applicazioni Web riguardano i dati nella tabella **nms:WebApp** .

I report incorporati forniti da  Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta [questa sezione](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Documentazione (surveyDictionary)<br /> </td> 
   <td> Descrizione della struttura del sondaggio, dipende dal componente aggiuntivo di Survey Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> Main (surveyProperties)<br /> </td> 
   <td> Proprietà sondaggio<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione delle risposte (surveyDistribution)<br /> </td> 
   <td> Suddivisione delle risposte alle domande.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Altri rapporti ootb {#other-ootb-reports}

Vengono forniti anche i seguenti rapporti incorporati. Per ulteriori informazioni, consultare il documento sulle funzionalità che interessano.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Analisi delle offerte (offerAnalysis)<br /> </td> 
   <td> L'analisi delle offerte per data e canale dipende dal componente aggiuntivo Interaction.<br /> </td> 
   <td> nms:offerta<br /> </td> 
  </tr> 
  <tr> 
   <td> Efficienza di ricommercializzazione (remarketingEffect)<br /> </td> 
   <td> Misurazione dell'efficienza del remarketing<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Storia delle acquisizioni di prospettiva sociale (socialVisitorStatistics)<br /> </td> 
   <td> La storia delle acquisizioni potenziali di Twitter e Facebook dipende dal componente aggiuntivo Social marketing.<br /> </td> 
   <td> nms:visitatore<br /> </td> 
  </tr> 
  <tr> 
   <td> Tracciamento delle proposte recenti (RecentProposition)<br /> </td> 
   <td> Tracciamento delle proposte in tempo reale<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>

