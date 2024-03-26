---
product: campaign
title: Power Booster e Power Cluster
description: Power Booster e Power Cluster
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 7%

---

# Power Booster e Power Cluster{#power-booster-and-power-cluster}



## Panoramica {#overview}

Adobe Campaign offre due set di opzioni architetturali preconfigurate per la quotatura della distribuzione:

* **Power Booster**

  Questa opzione fornisce il supporto per una singola istanza di esecuzione aggiuntiva separata dall’istanza dell’applicazione Adobe Campaign principale. Le istanze di esecuzione dedicate possono essere ospitate in remoto o da una terza parte. Quando implementati, l’esecuzione e-mail, il tracciamento, le pagine mirror e i messaggi non recapitati vengono gestiti indipendentemente dalle funzioni centrali dell’applicazione.

* **Power Cluster**

  Questa opzione fornisce il supporto per 2 a N istanze di esecuzione in cluster disaccoppiate dall’istanza dell’applicazione Adobe Campaign principale in relazione a una determinata applicazione. I cluster possono essere ospitati in remoto, in implementazioni distribuite e da terze parti. Oltre ai vantaggi dell&#39;isolamento dei processi, l&#39;opzione Adobe Campaign Power Cluster consente la ridondanza e l&#39;espansione delle strategie utilizzando hardware di base per una più semplice evoluzione degli SLA o delle prestazioni.

![](assets/architectural_options_diagram.png)

## Domande ammissibili {#eligible-applications}

Le opzioni Power Booster e Power Cluster possono essere utilizzate dalle seguenti applicazioni:

* Campaign
* Consegna
* Centro messaggi

## Matrice di consigli per l&#39;architettura {#matrix-of-architectural-recommendations}

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td> <strong>Architettura standard</strong><br /> </td> 
   <td> <strong>Power Booster</strong><br /> </td> 
   <td> <strong>Power Cluster</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Campagne e interazioni in uscita<br /> </td> 
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
   <td> Quello del database primario<br /> </td> 
   <td> 24 ore su 24, 7 giorni su 7, ad eccezione delle finestre di manutenzione e dei tempi di inattività per l’istanza di esecuzione<br /> </td> 
   <td> 24/7/365 servizio possibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicurezza<br /> </td> 
   <td> Data mart è potenzialmente accessibile da Internet pubblico<br /> </td> 
   <td> Data mart è isolato da componenti frontali, rivolti a Internet<br /> </td> 
   <td> Data mart è isolato da componenti frontali, rivolti a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modello di distribuzione<br /> </td> 
   <td> Tutto su un sito (può essere on-premise o nel cloud)<br /> </td> 
   <td> Marketing on premise con esecuzione nel cloud possibile<br /> </td> 
   <td> Marketing on-premise con esecuzione nel cloud; esecuzione in aree geografiche diverse possibile<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Raccomandazioni {#recommendations}

* Un’istanza di esecuzione deve essere dedicata a un servizio. Non puoi installare un pacchetto per un servizio al quale non ti sei iscritto. Ad esempio, se ti abboni a **Power Booster** opzione per **Centro messaggi** , è possibile installare solo il **[!UICONTROL Execution of transactional messages]** sull’istanza di esecuzione dedicata. Controlla il contratto di licenza.
* Poiché le istanze dedicate (o cluster) sono istanze di Adobe Campaign, i consigli sono gli stessi di un’istanza principale. Per ulteriori informazioni, consulta [questo documento](../../production/using/foreword.md).
* Per configurare correttamente l’istanza dal punto di vista di un database o di componenti hardware, contatta Adobe Campaign Professional Services.
