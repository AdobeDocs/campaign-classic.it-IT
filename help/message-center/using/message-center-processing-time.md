---
product: campaign
title: Tempo di elaborazione del Centro messaggi
description: Ulteriori informazioni sul report sull'ora di elaborazione del Centro messaggi.
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%

---

# Tempo di elaborazione del Centro messaggi {#message-center-processing-time}

![](../../assets/v7-only.svg)

Questo rapporto visualizza gli indicatori principali relativi alla coda in tempo reale.

Questo rapporto, rivolto agli amministratori tecnici, è accessibile anche tramite **[!UICONTROL Monitoring]** nell&#39;istanza di controllo.

![](assets/mc_reports_2.png)

Proprio come per la **[!UICONTROL Message Center service level]** puoi scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. Puoi anche filtrare i dati per canale e per un periodo di tempo specifico.

Gli indicatori visualizzati nel **[!UICONTROL Indicators over the period]** La sezione viene calcolata nel periodo selezionato:

* **[!UICONTROL Average queuing time]** : il tempo medio trascorso dall&#39;elaborazione degli eventi in Centro messaggi. Viene preso in considerazione solo il tempo di elaborazione.
* **[!UICONTROL Average message sending time (s)]** : il tempo medio trascorso dall&#39;elaborazione degli eventi in Centro messaggi. Viene preso in considerazione solo il tempo di consegna mta.
* **[!UICONTROL Average processing time (s)]** : il tempo medio trascorso dall&#39;elaborazione degli eventi in Centro messaggi. Il calcolo tiene conto del tempo di elaborazione e del tempo di invio mta.
* **[!UICONTROL Maximum number of queued events]** : numero massimo di eventi presenti nella coda del Centro messaggi in un dato momento.
* **[!UICONTROL Minimum number of queued events]** : numero minimo di eventi presenti nella coda del Centro messaggi in un dato momento.
* **[!UICONTROL Average number of queued events]** : numero medio di eventi presenti nella coda del Centro messaggi in un dato momento.

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e avviso (rosso) possono essere configurate nella procedura guidata di distribuzione di Adobe Campaign. Fai riferimento a [Monitorare le soglie](../../message-center/using/additional-configurations.md#monitoring-thresholds).
