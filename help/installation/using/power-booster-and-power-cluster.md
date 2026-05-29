---
product: campaign
title: Power Booster e Power Cluster
description: Power Booster e Power Cluster
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 59364cfc-9917-4057-ad5f-fbca7e261b07
TQID: https://experienceleague.adobe.com/lcr5Xfipd9cDuglWBqBsiVXJUUZqQxLEmzzZPrAEhHU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
subfeature_v2:
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
  - id: fb2a841f-c522-491f-9901-a1b939d252df
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 412
ht-degree: 6%

---

# Power Booster e Power Cluster{#power-booster-and-power-cluster}



## Panoramica {#overview}

Adobe Campaign offre due set di opzioni architetturali preconfigurate per la quotatura della distribuzione:

* **Power Booster**

  Questa opzione fornisce il supporto per una singola istanza di esecuzione aggiuntiva separata dall’istanza dell’applicazione Adobe Campaign principale. Le istanze di esecuzione dedicate possono essere ospitate in remoto o da una terza parte. Quando implementati, l’esecuzione e-mail, il tracciamento, le pagine mirror e i messaggi non recapitati vengono gestiti indipendentemente dalle funzioni centrali dell’applicazione.

* **Power Cluster**

  Questa opzione fornisce il supporto per 2 a N istanze di esecuzione in cluster disaccoppiate dall’istanza dell’applicazione Adobe Campaign principale in relazione a una determinata applicazione. I cluster possono essere ospitati in remoto, in implementazioni distribuite e da terze parti. Oltre ai vantaggi dell&#39;isolamento dei processi, l&#39;opzione Adobe Campaign Power Cluster consente la ridondanza e l&#39;espansione delle strategie utilizzando componenti hardware di base per semplificare l&#39;evoluzione di SLA o delle prestazioni.

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
   <td> 24 ore su 24, 7 giorni su 7, ad eccezione delle finestre di manutenzione e dei tempi di inattività per l'istanza di esecuzione<br /> </td> 
   <td> Servizio 24/7/365 possibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Sicurezza<br /> </td> 
   <td> Data mart è potenzialmente accessibile da Internet pubblico<br /> </td> 
   <td> Data mart è isolato da componenti frontali rivolti a Internet<br /> </td> 
   <td> Data mart è isolato da componenti frontali rivolti a Internet<br /> </td> 
  </tr> 
  <tr> 
   <td> Modello di distribuzione<br /> </td> 
   <td> Tutto in un sito (può essere locale o nel cloud)<br /> </td> 
   <td> Marketing on-premise con esecuzione nel cloud possibile<br /> </td> 
   <td> Marketing on-premise con esecuzione nel cloud; esecuzione in aree geografiche diverse possibile<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Consigli {#recommendations}

* Un’istanza di esecuzione deve essere dedicata a un servizio. Non puoi installare un pacchetto per un servizio al quale non ti sei iscritto. Ad esempio, se si sottoscrive l&#39;opzione **Power Booster** per il servizio **Message Center**, è possibile installare il pacchetto **[!UICONTROL Execution of transactional messages]** solo nell&#39;istanza di esecuzione dedicata. Controlla il contratto di licenza.
* Poiché le istanze dedicate (o cluster) sono istanze di Adobe Campaign, i consigli sono gli stessi di un’istanza principale. Per ulteriori informazioni, consulta [questo documento](../../production/using/foreword.md).
* Per configurare correttamente l’istanza dal punto di vista di un database o di componenti hardware, contatta Adobe Campaign Professional Services.
