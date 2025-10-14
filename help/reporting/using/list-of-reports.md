---
product: campaign
title: Elenco dei rapporti
description: Elenco dei rapporti
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Reporting, Monitoring
exl-id: c01f4850-ab17-44ac-a5e0-ff082ec206b3
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1020'
ht-degree: 2%

---

# Elenco dei rapporti{#list-of-reports}



## Rapporti sulle consegne {#reports-on-deliveries}

I rapporti incorporati forniti da Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi report, consulta [questa sezione](../../reporting/using/delivery-reports.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Attività utente (recipientActivity)<br /> </td> 
   <td> Raggruppamento di aperture, clic e transazioni per periodo di tempo.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Velocità effettiva di consegna (velocità effettiva)<br /> </td> 
   <td> Grafici della velocità effettiva di consegna, in messaggi/ora e Mbit/s.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori e mancati recapiti (errori)<br /> </td> 
   <td> Mancati recapiti e non recapiti per causa e dominio.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (deliveryFeedback)<br /> </td> 
   <td> Riepilogo degli indicatori chiave per tenere traccia del comportamento del destinatario.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (mobileAppDeliveryFeedback)<br /> </td> 
   <td> Indicatori di tracciamento di una consegna a un'app mobile.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Browser (browserStatistics)<br /> </td> 
   <td> Statistiche sui browser utilizzati dai destinatari che hanno fatto clic nei messaggi.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione sui social network (deliveryForward)<br /> </td> 
   <td> Condivisione delle statistiche relative all'attività e all'apertura dei messaggi di posta elettronica.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Hot click (hoturl)<br /> </td> 
   <td> Visualizza il messaggio e le percentuali di clic sovrapposte.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Rapporto ipotesi (deliveryHypothesis)<br /> </td> 
   <td> Visualizza il riepilogo delle misure sulle ipotesi di consegna.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di consegna (statisticsPerDelivery)<br /> </td> 
   <td> Statistiche (messaggi elaborati, messaggi consegnati, mancati recapiti permanenti, mancati recapiti non permanenti, clic, annullamenti di abbonamenti) per dominio e-mail.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione delle statistiche delle attività (forwardActivities)<br /> </td> 
   <td> Analisi delle attività di condivisione, delle aperture e delle sottoscrizioni per periodo di tempo.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di tracciamento (trackingStatistics)<br /> </td> 
   <td> Apri, rapporto sulle tariffe di clic e transazione.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo delle consegne (deliverySending)<br /> </td> 
   <td> Riepilogo degli indicatori di consegna: destinazione, esclusione e messaggi inviati.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo delle consegne (deliveryStatistics)<br /> </td> 
   <td> Tabella di riepilogo per le consegne selezionate: destinazioni, esclusioni e messaggi inviati.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> Sistemi operativi (osStatistics)<br /> </td> 
   <td> Statistiche sui sistemi operativi utilizzati dai destinatari che hanno fatto clic in un messaggio.<br /> </td> 
   <td> xtk:none<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (deliveryFeedbackSocial)<br /> </td> 
   <td> Frequenza di reattività della consegna e raggruppamento della reazione.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
  <tr> 
   <td> URL e velocità effettiva di clic (topUrlDelivery)<br /> </td> 
   <td> URL più reattivi e flussi di clic associati.<br /> </td> 
   <td> nms:delivery<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle campagne {#reports-on-campaigns}

I report sulle campagne riguardano i dati nella tabella **nms:operation**.

I rapporti incorporati forniti da Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi report, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=it){target=_blank}.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Attività utente (operationRecipientActivity)<br /> </td> 
   <td> Raggruppamento di aperture, clic e transazioni per periodo di tempo, in base a Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Velocità effettiva di consegna (operationThroughput)<br /> </td> 
   <td> I grafici della velocità effettiva di consegna, in mail/ora e Mbit/s, dipendono da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Spese campagna (budgetOperationExpenses)<br /> </td> 
   <td> Visualizza gli elementi riga campagna in dettaglio, a seconda di Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Errori e mancati recapiti (operationErrors)<br /> </td> 
   <td> Mancati recapiti e non recapitabili per causa e dominio, dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione righe costi (budgetExplorerOperation)<br /> </td> 
   <td> Analisi descrittiva delle linee di costo, dipende da MRM.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indicatori di tracciamento (operationFeedback)<br /> </td> 
   <td> Panoramica degli indicatori chiave di tracciamento: aperture, clic e transazioni, dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione sui social network (operationForward)<br /> </td> 
   <td> La condivisione delle statistiche di attività e apertura della posta dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Report ipotesi (operationHypothesis)<br /> </td> 
   <td> Visualizza il riepilogo delle misurazioni delle ipotesi per le consegne della campagna, in base a Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Condivisione delle statistiche delle attività (forwardActivityOpt)<br /> </td> 
   <td> L'analisi delle attività di condivisione, delle aperture e delle sottoscrizioni per periodo di tempo dipende da Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo consegne (operationStatistics)<br /> </td> 
   <td> Grafico di riepilogo delle consegne della campagna: destinazioni, esclusioni e messaggi inviati.<br /> </td> 
  </tr> 
  <tr> 
   <td> URL e velocità effettiva di clic (operationTopUrlDelivery)<br /> </td> 
   <td> La maggior parte degli URL reattivi e dei flussi di clic associati dipende da Campaign.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sui servizi {#reports-on-services}

I report sui servizi riguardano i dati nella tabella **nms:service**.

I rapporti incorporati forniti da Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi rapporti, consulta le relative guide.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Acquisizioni di ventole (socialAcquisitionsByWebapp)<br /> </td> 
   <td> Quali applicazioni web hanno consentito le acquisizioni dei potenziali clienti? Dipende dal componente aggiuntivo Social marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Raggruppamento delle sottoscrizioni (mobileAppDistribution)<br /> </td> 
   <td> Raggruppamento degli abbonamenti attivi per app mobile, in base al componente aggiuntivo Canale app mobile.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tracciamento abbonamento (subscriptionsProgress)<br /> </td> 
   <td> Evoluzione degli abbonamenti a servizi di informazione<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (socialReactionRate)<br /> </td> 
   <td> Quali sono i tassi di reattività per le ultime consegne? Dipende dal componente aggiuntivo Social marketing.<br /> </td> 
  </tr> 
  <tr> 
   <td> Tasso di reattività (mobileAppReactivityRate)<br /> </td> 
   <td> Il tasso di reattività per le ultime consegne dipende dal componente aggiuntivo Canale app mobile.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Report budget {#budget-reports}

I rapporti incorporati forniti da Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi report, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html?lang=it){target=_blank}.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Costi collegati ai programmi (budgetProgramCost)<br /> </td> 
   <td> Raggruppamento dei costi del programma.<br /> </td> 
   <td> nms:programma<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione budget (budgetEvolution)<br /> </td> 
   <td> Evoluzione dei costi budget per livello di impegno.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Evoluzione cumulativa del budget (budgetCumulativeEvolution)<br /> </td> 
   <td> Evoluzione dei costi preventivati cumulativi suddivisi per livello di frammento Commi<br />. </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione righe costi (budgetExplorerBudget)<br /> </td> 
   <td> Analisi descrittiva delle righe costi.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione righe costi (budgetExplorer)<br /> </td> 
   <td> Analisi descrittiva delle righe costi.<br /> </td> 
   <td> nms:costLine<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione righe costi (budgetExplorerPlan)<br /> </td> 
   <td> Analisi descrittiva delle righe costi.<br /> </td> 
   <td> nms:piano<br /> </td> 
  </tr> 
  <tr> 
   <td> Esplorazione righe costi (budgetExplorerProgram)<br /> </td> 
   <td> Analisi descrittiva delle righe costi.<br /> </td> 
   <td> nms:programma<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo budget (budget)<br /> </td> 
   <td> Snapshot dei costi principali, delle categorie di spesa e dei budget.<br /> </td> 
   <td> nms:budget<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle simulazioni {#reports-on-simulations}

I report sulle simulazioni riguardano i dati nella tabella **nms:simulation**.

I rapporti incorporati forniti da Adobe Campaign sono disponibili nella tabella seguente.

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
   <td> Raggruppamento delle offerte per rango (offerSimulationRanking)<br /> </td> 
   <td> Raggruppamento delle offerte nella simulazione, per rango.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo simulazione (dlvSimuLossesSummary)<br /> </td> 
   <td> Riepilogo di volumi ed esclusioni di simulazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> Statistiche di sovrapposizione (dlvSimuOverlapping)<br /> </td> 
   <td> Volumi di sovrapposizione di destinazione della consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Riepilogo delle esclusioni dovute alla simulazione (dlvSimuLossesSimu)<br /> </td> 
   <td> Tabella di esclusioni dovute alla simulazione.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Rapporti sulle applicazioni web {#reports-on-web-applications}

I report sulle applicazioni Web riguardano i dati nella tabella **nms:WebApp**.

I rapporti incorporati forniti da Adobe Campaign sono disponibili nella tabella seguente.

Per ulteriori informazioni sul contenuto di questi report, consulta [questa sezione](../../web/using/about-web-applications.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Documentazione (surveyDictionary)<br /> </td> 
   <td> Descrizione della struttura del sondaggio, in base al componente aggiuntivo Gestione sondaggi.<br /> </td> 
  </tr> 
  <tr> 
   <td> Principale (surveyProperties)<br /> </td> 
   <td> Proprietà sondaggio<br /> </td> 
  </tr> 
  <tr> 
   <td> Raggruppamento delle risposte (surveyDistribution)<br /> </td> 
   <td> Raggruppamento delle risposte alle domande.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Altri rapporti ootb {#other-ootb-reports}

Sono inoltre forniti i seguenti rapporti incorporati. Per ulteriori informazioni, consulta il documento sulle funzionalità a cui si riferiscono.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Etichetta e nome interno</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Schema</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Analisi delle offerte (offerAnalysis)<br /> </td> 
   <td> L'analisi delle offerte per data e canale dipende dal componente aggiuntivo di interazione.<br /> </td> 
   <td> nms:offer<br /> </td> 
  </tr> 
  <tr> 
   <td> Efficienza remarketing (remarketingEffect)<br /> </td> 
   <td> Misurazione dell'efficienza di remarketing<br /> </td> 
   <td> nms:webEvent<br /> </td> 
  </tr> 
  <tr> 
   <td> Cronologia acquisizioni di potenziali clienti social (socialVisitorStatistics)<br /> </td> 
   <td> La cronologia delle acquisizioni di X (precedentemente noto come Twitter) e Facebook prospect dipende dal componente aggiuntivo Social marketing.<br /> </td> 
   <td> nms:visitor<br /> </td> 
  </tr> 
  <tr> 
   <td> Tracciamento delle proposte recenti (recentiPropositions)<br /> </td> 
   <td> Tracciamento delle proposte in tempo reale<br /> </td> 
   <td> nms:propositionRcp<br /> </td> 
  </tr> 
 </tbody> 
</table>
