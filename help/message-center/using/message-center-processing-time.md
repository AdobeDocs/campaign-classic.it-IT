---
product: campaign
title: Tempo di elaborazione del Centro messaggi
description: Ulteriori informazioni sul report del tempo di elaborazione del Centro messaggi
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: c797fd94-0c8d-480b-b22a-1489ac331e77
TQID: 'https://experienceleague.adobe.com/nESBoEHC7YU0SO4yJ0rscDa3E-ePk6yNbPKzusER7C4'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 3%
---
# Tempo di elaborazione del Centro messaggi {#message-center-processing-time}



Questo rapporto visualizza gli indicatori principali relativi alla coda in tempo reale.

È inoltre possibile accedere a questo report, destinato agli amministratori tecnici, tramite la scheda **[!UICONTROL Monitoring]** nell&#39;istanza di controllo.

![](assets/mc_reports_2.png)

Proprio come per il report **[!UICONTROL Message Center service level]**, è possibile scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. Puoi anche filtrare i dati per canale e in un periodo specifico.

Gli indicatori visualizzati nella sezione **[!UICONTROL Indicators over the period]** vengono calcolati per il periodo selezionato:

* **[!UICONTROL Average queuing time]**: tempo medio trascorso nel Centro messaggi durante l&#39;elaborazione degli eventi. Viene preso in considerazione solo il tempo di elaborazione.
* **[!UICONTROL Average message sending time (s)]**: tempo medio trascorso nel Centro messaggi durante l&#39;elaborazione degli eventi. Viene preso in considerazione solo il tempo di consegna dell’MTA.
* **[!UICONTROL Average processing time (s)]**: tempo medio trascorso nel Centro messaggi durante l&#39;elaborazione degli eventi. Il calcolo tiene conto del tempo di elaborazione e del tempo di invio dell’MTA.
* **[!UICONTROL Maximum number of queued events]**: numero massimo di eventi presenti nella coda del Centro messaggi in un determinato momento.
* **[!UICONTROL Minimum number of queued events]**: numero minimo di eventi presenti nella coda del Centro messaggi in un determinato momento.
* **[!UICONTROL Average number of queued events]**: numero medio di eventi presenti nella coda del Centro messaggi in un determinato momento.

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e di avviso (rosso) possono essere configurate nella procedura guidata di distribuzione di Adobe Campaign. Consulta [Monitorare le soglie](../../message-center/using/additional-configurations.md#monitoring-thresholds).
