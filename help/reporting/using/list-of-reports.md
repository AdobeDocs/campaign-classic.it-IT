---
product: campaign
title: Elenco dei rapporti
description: Elenco dei rapporti
feature: Reporting
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 2%

---

# Elenco dei rapporti{#list-of-reports}

![](../../assets/common.svg)

## Report sulle consegne {#reports-on-deliveries}

I rapporti incorporati forniti da Adobe Campaign si trovano nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta [questa sezione](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Attività utente (recipientActivity)<br /> </td> 
   <td> Suddivisione di aperture, clic e transazioni per periodo di tempo.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Velocità effettiva di consegna (throughput)<br /> </td> 
   <td> Grafici a velocità effettiva di consegna, in messaggi/ora e Mbit/s.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori e mancati recapiti (errori)<br /> </td> 
   <td> Rimbalzi e non risultati finali per causa e dominio.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (deliveryFeedback)<br /> </td> 
   <td> Riepilogo degli indicatori chiave per il tracciamento del comportamento dei destinatari.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Indicatori di tracciamento di una consegna a un’app mobile.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Browser (browserStatistics)<br /> </td> 
   <td> Statistiche sui browser utilizzati dai destinatari che hanno fatto clic sui messaggi.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione sui social network (deliveryForward)<br /> </td> 
   <td> Condivisione di statistiche di apertura di attività e posta elettronica.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Hot click (foto)<br /> </td> 
   <td> Visualizza il messaggio e le percentuali di clic sovrapposte.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Rapporto di ipotesi (deliveryHypothetic)<br /> </td> 
   <td> Visualizza il riepilogo delle misure in base alle ipotesi di consegna.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di consegna (statisticsPerDelivery)<br /> </td> 
   <td> Statistiche (messaggi elaborati, messaggi consegnati, mancati recapiti, non recapitati, clic, annullamenti di abbonamenti) per dominio e-mail.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione di statistiche sulle attività (forwardActivities)<br /> </td> 
   <td> Analisi delle attività di condivisione, delle aperture e degli abbonamenti per periodo di tempo.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di tracciamento (trackingStatistics)<br /> </td> 
   <td> Apri, fai clic su e rapporto tassi di transazione.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo consegna (deliverySending)<br /> </td> 
   <td> Sintesi degli indicatori di consegna: target, esclusione e messaggi inviati.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo della consegna (deliveryStatistics)<br /> </td> 
   <td> Tabella di riepilogo per le consegne selezionate: Target, esclusioni e messaggi inviati.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> Sistemi operativi (osStatistics)<br /> </td> 
   <td> Statistiche sui sistemi operativi utilizzati dai destinatari che hanno fatto clic su in un messaggio.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (deliveryFeedbackSocial)<br /> </td> 
   <td> Tasso di reattività della consegna e disaggregazione della reazione.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
  <tr> 
   <td> URL e throughput di clic (topUrlDelivery)<br /> </td> 
   <td> La maggior parte degli URL reattivi e dei flussi di clic associati.<br /> </td> 
   <td> nms:consegna<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Report sulle campagne {#reports-on-campaigns}

I rapporti sulle campagne riguardano i dati nel **nms:operazione** tabella.

I rapporti incorporati forniti da Adobe Campaign si trovano nella tabella seguente.

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
   <td> Velocità effettiva di consegna (operationThroughput)<br /> </td> 
   <td> I grafici della velocità effettiva di consegna, in e-mail/ora e Mbit/s, dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Spese campagna (budgetOperationExpenses)<br /> </td> 
   <td> Visualizza in dettaglio le voci della campagna, a seconda di Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori e mancati recapiti (operationErrors)<br /> </td> 
   <td> I rimbalzi e i non consegnabili per causa e dominio dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle linee dei costi (budgetExplorerOperation)<br /> </td> 
   <td> L'analisi descrittiva delle linee di costo dipende dal MRM.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (operationFeedback)<br /> </td> 
   <td> Panoramica degli indicatori di tracciamento chiave: Le aperture, i clic e le transazioni dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione sui social network (operationForward)<br /> </td> 
   <td> La condivisione di statistiche di apertura di attività e posta dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rapporto di ipotesi (operationHypothetic)<br /> </td> 
   <td> Visualizza il riepilogo delle misurazioni delle ipotesi per le consegne della campagna, a seconda di Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione di statistiche sulle attività (forwardActivityOpt)<br /> </td> 
   <td> L’analisi delle attività di condivisione, delle aperture e degli abbonamenti per periodo di tempo dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo della consegna (operationStatistics)<br /> </td> 
   <td> Grafico di riepilogo delle consegne della campagna: Target, esclusioni e messaggi inviati.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL e throughput di clic (operationTopUrlDelivery)<br /> </td> 
   <td> La maggior parte degli URL reattivi e dei flussi di clic associati dipendono da Campaign.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sui servizi {#reports-on-services}

Le relazioni sui servizi riguardano i dati **nms:servizio** tabella.

I rapporti incorporati forniti da Adobe Campaign si trovano nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta le relative guide.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Acquisizioni di ventole (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Quali applicazioni web hanno permesso le acquisizioni potenziali? Dipende dal componente aggiuntivo Social marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Disaggregazione degli abbonamenti (mobileAppDistribution)<br /> </td> 
   <td> La suddivisione degli abbonamenti attivi per app mobile dipende dal componente aggiuntivo per canale app mobile.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tracciamento sottoscrizione (subscriptionsProgress)<br /> </td> 
   <td> Evoluzione degli abbonamenti ai servizi di informazione<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (socialReactionRate)<br /> </td> 
   <td> Quali sono i tassi di reattività per le ultime consegne? Dipende dal componente aggiuntivo Social marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (mobileAppReactivityRate)<br /> </td> 
   <td> Il tasso di reattività per le consegne più recenti dipende dal componente aggiuntivo per canale app mobile.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Relazioni di bilancio {#budget-reports}

I rapporti incorporati forniti da Adobe Campaign si trovano nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta [questa sezione](../../campaign/using/designing-marketing-campaigns.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Costi legati al programma o ai programmi (budgetProgramCost)<br /> </td> 
   <td> Ripartizione dei costi dei programmi.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione del bilancio (evoluzione del bilancio)<br /> </td> 
   <td> Evoluzione dei costi di bilancio per livello di impegno.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione cumulativa del budget (budgetCumulativeEvolution)<br /> </td> 
   <td> Evoluzione dei costi di bilancio cumulati ripartiti per commi<br /> livello del trattamento. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle linee di costo (budgetExplorerBudget)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle linee di costo (budgetExplorer)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle linee di costo (budgetExplorerPlan)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:plan<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione delle linee di costo (budgetExplorerProgram)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo.<br /> </td> 
   <td> nms:program<br /> </td> 
  </tr> 
  <tr> 
   <td> Sintesi del bilancio (bilancio)<br /> </td> 
   <td> Istantanea dei principali costi, categorie di spesa e budget.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle simulazioni {#reports-on-simulations}

Le relazioni sulle simulazioni riguardano i dati **nms:simulazione** tabella.

I rapporti incorporati forniti da Adobe Campaign si trovano nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta le relative guide.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dettaglio delle esclusioni di simulazione (dlvSimuLossesDetail)<br /> </td> 
   <td> Tabella dettagliata di tutte le cause di esclusione.<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione delle offerte per classificazione (offerSimulationRanking)<br /> </td> 
   <td> Suddivisione delle offerte nella simulazione, per classificazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo della simulazione (dlvSimuLossesSummary)<br /> </td> 
   <td> Riepilogo dei volumi di simulazione ed esclusioni.<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di sovrapposizione (dlvSimuOverlapping)<br /> </td> 
   <td> Volumi di sovrapposizione target di consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo delle esclusioni dovute alla simulazione (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabella delle esclusioni dovute alla simulazione.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle applicazioni web {#reports-on-web-applications}

I rapporti sulle applicazioni web riguardano i dati **nms:WebApp** tabella.

I rapporti incorporati forniti da Adobe Campaign si trovano nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta [questa sezione](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Documentazione (surveyDictionary)<br /> </td> 
   <td> Descrizione della struttura del sondaggio, dipende dal componente aggiuntivo Survey Manager.<br /> </td> 
  </tr> 
  <tr> 
   <td> Principale (surveyProperties)<br /> </td> 
   <td> Proprietà del sondaggio<br /> </td> 
  </tr> 
  <tr> 
   <td> Suddivisione delle risposte (surveyDistribution)<br /> </td> 
   <td> Scomposizione delle risposte alle domande.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Altri rapporti ootb {#other-ootb-reports}

Vengono inoltre forniti i seguenti rapporti incorporati. Per ulteriori informazioni, consulta il documento sulle funzionalità che riguardano.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Analisi delle offerte (offerAnalysis)<br /> </td> 
   <td> L’analisi dell’offerta per data e canale dipende dal componente aggiuntivo Interaction .<br /> </td> 
   <td> nms:offerta<br /> </td> 
  </tr> 
  <tr> 
   <td> Efficienza di remarketing (remarketingEffect)<br /> </td> 
   <td> Misurazione dell’efficienza del remarketing<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Storia delle acquisizioni di prospettiva sociale (socialVisitorStatistics)<br /> </td> 
   <td> La storia delle acquisizioni potenziali di Twitter e Facebook dipende dal componente aggiuntivo Social marketing.<br /> </td> 
   <td> nms:visitatore<br /> </td> 
  </tr> 
  <tr> 
   <td> Tracking delle proposte recenti (RecentProposition)<br /> </td> 
   <td> Tracciamento delle proposte in tempo reale<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
