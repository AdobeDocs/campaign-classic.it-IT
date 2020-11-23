---
solution: Campaign Classic
product: campaign
title: Tempo di elaborazione del Centro messaggi
description: Tempo di elaborazione del Centro messaggi
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---


# Tempo di elaborazione del Centro messaggi{#message-center-processing-time}

Questo rapporto mostra gli indicatori principali relativi alla coda in tempo reale. Questo rapporto, rivolto agli amministratori tecnici, è accessibile anche attraverso l&#39; **[!UICONTROL Monitoring]** universo nell&#39;istanza di controllo.

![](assets/mc_reports_2.png)

Come per il **[!UICONTROL Message Center service level]** rapporto, potete scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. È inoltre possibile filtrare i dati per canale e per un periodo specifico. Gli indicatori visualizzati nella **[!UICONTROL Indicators over the period]** sezione sono calcolati nel periodo selezionato:

* **[!UICONTROL Average queuing time]** : il tempo medio durante il quale gli eventi sono stati elaborati correttamente in Centro messaggi. Viene preso in considerazione solo il tempo di elaborazione.
* **[!UICONTROL Average message sending time (s)]** : il tempo medio durante il quale gli eventi sono stati elaborati correttamente in Centro messaggi. Si tiene conto solo dei tempi di consegna più lunghi.
* **[!UICONTROL Average processing time (s)]** : il tempo medio durante il quale gli eventi sono stati elaborati correttamente in Centro messaggi. Il calcolo prende in considerazione il tempo di elaborazione e il tempo di invio dei dati.
* **[!UICONTROL Maximum number of queued events]** : numero massimo di eventi presenti nella coda del Centro messaggi in un dato momento.
* **[!UICONTROL Minimum number of queued events]** : numero minimo di eventi presenti nella coda Centro messaggi in un dato momento.
* **[!UICONTROL Average number of queued events]** : numero medio di eventi presenti nella coda Centro messaggi in un dato momento.

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e avviso (rosso) possono essere configurate  distribuzione guidata Adobe Campaign. Fare riferimento alle soglie [di](../../message-center/using/monitoring-thresholds.md)monitoraggio.

