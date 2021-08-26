---
product: campaign
title: Power Booster e Power Cluster
description: Power Booster e Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---

# Power Booster e Power Cluster{#power-booster-and-power-cluster}

![](../../assets/v7-only.svg)

## Panoramica {#overview}

Adobe Campaign offre due set di opzioni architettoniche preconfigurate per la quotatura della distribuzione:

* **Alimentazione**

   Questa opzione fornisce il supporto per una singola istanza di esecuzione aggiuntiva disaccoppiata dall’istanza principale dell’applicazione Adobe Campaign. Le istanze di esecuzione dedicate possono essere ospitate in remoto o da terze parti. Quando implementato, l’esecuzione delle e-mail, il tracciamento, le pagine mirror e i messaggi non recapitati vengono gestiti indipendentemente dalle funzioni dell’applicazione centrale.

* **Cluster di alimentazione**

   Questa opzione fornisce il supporto per le istanze di esecuzione in cluster da 2 a N disaccoppiate dall&#39;istanza primaria dell&#39;applicazione Adobe Campaign in relazione a una determinata applicazione. I cluster possono essere ospitati in remoto, in implementazioni distribuite e da terze parti. Oltre ai vantaggi dell&#39;isolamento del processo, l&#39;opzione Adobe Campaign Power Cluster consente la ridondanza e l&#39;ottimizzazione delle strategie utilizzando l&#39;hardware di base per un&#39;evoluzione semplificata dello SLA o delle prestazioni.

![](assets/architectural_options_diagram.png)

## Domande ammissibili {#eligible-applications}

Le opzioni Power Booster e Power Cluster possono essere utilizzate dalle seguenti applicazioni:

* Campaign
* Consegna
* Centro messaggi

## Matrice di raccomandazioni architettoniche {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Architettura standard</strong><br /> </td> 
   <td> <strong>Alimentazione</strong><br /> </td> 
   <td> <strong>Cluster di alimentazione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campagne e-mail e interazioni in uscita<br /> </td> 
   <td> Fino a circa 30 milioni di e-mail al mese<br /> </td> 
   <td> Da 30 a 100 milioni di e-mail al mese<br /> </td> 
   <td> Oltre 100 milioni di e-mail al mese<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi transazionali<br /> </td> 
   <td> 50.000 all'ora per server di esecuzione<br /> </td> 
   <td> 50.000 all'ora per server di esecuzione<br /> </td> 
   <td> 50.000 all'ora per server di esecuzione<br /> </td> 
  </tr> 
  <tr> 
   <td> Disponibilità<br /> </td> 
   <td> Quello del database principale<br /> </td> 
   <td> 24/7 tranne le finestre di manutenzione e i tempi di inattività per l'istanza di esecuzione<br /> </td> 
   <td> 24/7/365 servizio possibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicurezza<br /> </td> 
   <td> Data mart è potenzialmente accessibile da Internet pubblico<br /> </td> 
   <td> Data mart è isolato dai componenti frontali rivolti a Internet<br /> </td> 
   <td> Data mart è isolato dai componenti frontali rivolti a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modello di distribuzione<br /> </td> 
   <td> Tutti su un sito (può essere on-premise o nel cloud)<br /> </td> 
   <td> Possibilità di effettuare il marketing on-premise con l’esecuzione nel cloud<br /> </td> 
   <td> marketing on-premise con esecuzione nel cloud; esecuzione in diversi geos possibili<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Raccomandazioni {#recommendations}

* Un&#39;istanza di esecuzione deve essere dedicata a un servizio. Non è possibile installare un pacchetto per un servizio a cui non si è iscritti. Ad esempio, se ti abboni all&#39;opzione **Power Booster** per il servizio **Message Center**, puoi installare il pacchetto **[!UICONTROL Execution of transactional messages]** solo sull&#39;istanza di esecuzione dedicata. Controlla il contratto di licenza.
* Poiché le istanze dedicate (o cluster) sono istanze Adobe Campaign, le raccomandazioni sono le stesse di un&#39;istanza principale. Per ulteriori informazioni, consulta [questo documento](../../production/using/foreword.md).
* Per configurare correttamente l&#39;istanza dal punto di vista di un database/componenti hardware, contatta Adobe Campaign Professional Services.
