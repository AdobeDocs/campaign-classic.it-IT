---
product: campaign
title: Tempo di elaborazione del Centro messaggi
description: Ulteriori informazioni sul report del tempo di elaborazione del Centro messaggi
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 6%

---

# Tempo di elaborazione del Centro messaggi {#message-center-processing-time}



Questo rapporto visualizza gli indicatori principali relativi alla coda in tempo reale.

Il report, destinato agli amministratori tecnici, è accessibile anche tramite il **[!UICONTROL Monitoring]** sull&#39;istanza di controllo.

![](assets/mc_reports_2.png)

Proprio come per il **[!UICONTROL Message Center service level]** rapporto, puoi scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. Puoi anche filtrare i dati per canale e in un periodo specifico.

Gli indicatori visualizzati nella **[!UICONTROL Indicators over the period]** vengono calcolate nel periodo selezionato:

* **[!UICONTROL Average queuing time]** : tempo medio trascorso nel Centro messaggi durante l’elaborazione degli eventi. Viene preso in considerazione solo il tempo di elaborazione.
* **[!UICONTROL Average message sending time (s)]** : tempo medio trascorso nel Centro messaggi durante l’elaborazione degli eventi. Viene preso in considerazione solo il tempo di consegna dell’MTA.
* **[!UICONTROL Average processing time (s)]** : tempo medio trascorso nel Centro messaggi durante l’elaborazione degli eventi. Il calcolo tiene conto del tempo di elaborazione e del tempo di invio dell’MTA.
* **[!UICONTROL Maximum number of queued events]** : numero massimo di eventi presenti nella coda del Centro messaggi in un determinato momento.
* **[!UICONTROL Minimum number of queued events]** : numero minimo di eventi presenti nella coda del Centro messaggi in un determinato momento.
* **[!UICONTROL Average number of queued events]** : numero medio di eventi presenti nella coda del Centro messaggi in un determinato momento.

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e di avviso (rosso) possono essere configurate nella procedura guidata di distribuzione di Adobe Campaign. Fai riferimento a [Monitorare le soglie](../../message-center/using/additional-configurations.md#monitoring-thresholds).
