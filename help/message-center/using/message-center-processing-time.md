---
solution: Campaign Classic
product: campaign
title: Tempo di elaborazione del Centro messaggi
description: Tempo di elaborazione del Centro messaggi
audience: message-center
content-type: reference
topic-tags: reports
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 5%

---


# Tempo di elaborazione del Centro messaggi{#message-center-processing-time}

Questo rapporto visualizza gli indicatori principali relativi alla coda in tempo reale. Questo rapporto, destinato agli amministratori tecnici, è accessibile anche tramite la scheda **[!UICONTROL Monitoring]** nell’istanza di controllo .

![](assets/mc_reports_2.png)

Come per il rapporto **[!UICONTROL Message Center service level]**, puoi scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. Puoi anche filtrare i dati per canale e per un periodo di tempo specifico. Gli indicatori visualizzati nella sezione **[!UICONTROL Indicators over the period]** vengono calcolati nel periodo selezionato:

* **[!UICONTROL Average queuing time]** : il tempo medio trascorso dall&#39;elaborazione degli eventi in Centro messaggi. Viene preso in considerazione solo il tempo di elaborazione.
* **[!UICONTROL Average message sending time (s)]** : il tempo medio trascorso dall&#39;elaborazione degli eventi in Centro messaggi. Viene preso in considerazione solo il tempo di consegna mta.
* **[!UICONTROL Average processing time (s)]** : il tempo medio trascorso dall&#39;elaborazione degli eventi in Centro messaggi. Il calcolo tiene conto del tempo di elaborazione e del tempo di invio mta.
* **[!UICONTROL Maximum number of queued events]** : numero massimo di eventi presenti nella coda del Centro messaggi in un dato momento.
* **[!UICONTROL Minimum number of queued events]** : numero minimo di eventi presenti nella coda del Centro messaggi in un dato momento.
* **[!UICONTROL Average number of queued events]** : numero medio di eventi presenti nella coda del Centro messaggi in un dato momento.

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e avviso (rosso) possono essere configurate nella procedura guidata di distribuzione di Adobe Campaign. Fare riferimento a [Soglie di monitoraggio](../../message-center/using/monitoring-thresholds.md).

