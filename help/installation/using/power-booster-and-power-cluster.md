---
solution: Campaign Classic
product: campaign
title: Power Booster e Power Cluster
description: Power Booster e Power Cluster
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 6%

---


# Power Booster e Power Cluster{#power-booster-and-power-cluster}

## Panoramica {#overview}

 Adobe Campaign offre due serie di opzioni di architettura precompilate per la quotatura dell’implementazione:

* **Alimentatore**

   Questa opzione fornisce il supporto per una singola istanza di esecuzione aggiuntiva disaccoppiata dall&#39;istanza dell&#39;applicazione Adobe Campaign  principale. Le istanze di esecuzione dedicate possono essere ospitate in remoto o da terzi. Quando implementata, l&#39;esecuzione delle e-mail, il tracciamento, le pagine mirror e i messaggi di rimbalzo vengono gestiti indipendentemente dalle funzioni dell&#39;applicazione centrale.

* **Cluster di alimentazione**

   Questa opzione supporta da 2 a N istanze di esecuzione in cluster disaccoppiate dall&#39;istanza dell&#39;applicazione Adobe Campaign  principale in relazione a una determinata applicazione. I cluster possono essere ospitati in remoto, in distribuzioni distribuite e da terze parti. Oltre ai vantaggi dell&#39;isolamento del processo, l&#39;opzione  Adobe Campaign Power Cluster consente la ridondanza e l&#39;implementazione di strategie tramite hardware di base per un&#39;evoluzione semplificata dello SLA o delle prestazioni.

![](assets/architectural_options_diagram.png)

## Domande ammissibili {#eligible-applications}

Le opzioni Power Booster e Power Cluster possono essere utilizzate dalle seguenti applicazioni:

* Campagna
* Consegna
* Centro messaggi

## Matrice di raccomandazioni architettoniche {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Architettura standard</strong><br /> </td> 
   <td> <strong>Alimentatore</strong><br /> </td> 
   <td> <strong>Cluster di alimentazione</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campagne e interazioni via e-mail<br /> </td> 
   <td> Fino a circa 30 milioni di email al mese<br /> </td> 
   <td> Da 30 a 100 milioni di email al mese<br /> </td> 
   <td> Oltre 100 milioni di email al mese<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggi transazionali<br /> </td> 
   <td> 50.000 all'ora per server di esecuzione<br /> </td> 
   <td> 50.000 all'ora per server di esecuzione<br /> </td> 
   <td> 50.000 all'ora per server di esecuzione<br /> </td> 
  </tr> 
  <tr> 
   <td> Disponibilità<br /> </td> 
   <td> Quello del database primario<br /> </td> 
   <td> 24/7 tranne finestre di manutenzione e tempi di inattività per l'istanza di esecuzione<br /> </td> 
   <td> 24/7/365 possibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicurezza<br /> </td> 
   <td> Data mart è potenzialmente accessibile da Internet pubblico<br /> </td> 
   <td> Data mart è isolato dai componenti frontali rivolti a Internet<br /> </td> 
   <td> Data mart è isolato dai componenti frontali rivolti a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modello di distribuzione<br /> </td> 
   <td> Tutti su un sito (può essere in sede o nel cloud)<br /> </td> 
   <td> Marketing locale con esecuzione nel cloud possibile<br /> </td> 
   <td> Marketing locale con esecuzione nel cloud; esecuzione in diverse aree geografiche possibili<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Raccomandazioni {#recommendations}

* Un&#39;istanza di esecuzione deve essere dedicata a un servizio. Non potete installare un pacchetto per un servizio a cui non avete effettuato la sottoscrizione. Se, ad esempio, vi iscrivete all&#39;opzione **Power Booster** per il servizio **Message Center** , potete installare il **[!UICONTROL Execution of transactional messages]** pacchetto solo nell&#39;istanza di esecuzione dedicata. Controlla il contratto di licenza.
* Poiché le istanze dedicate (o cluster) sono  istanze Adobe Campaign, le raccomandazioni sono le stesse di un&#39;istanza principale. For more on this, refer to [this document](../../production/using/foreword.md).
* Per configurare correttamente l&#39;istanza dal punto di vista di un database o componenti hardware, contattare  Adobe Campaign Professional Services.

