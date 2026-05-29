---
product: campaign
title: Livello di servizio del Centro messaggi
description: Ulteriori informazioni sul report del livello di servizio del Centro messaggi
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
TQID: https://experienceleague.adobe.com/v9s-xydUk-4cNxNYSAj1HLCOOscZhpQDP-bSJt9mUzg
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 237
ht-degree: 3%

---

# Livello di servizio del Centro messaggi {#message-center-service-level}



Questo rapporto visualizza le statistiche di consegna relative ai messaggi transazionali e il raggruppamento degli errori. Puoi fare clic su un tipo di errore per visualizzarne i dettagli.

È inoltre possibile accedere a questo report, destinato agli amministratori tecnici, tramite la scheda **[!UICONTROL Monitoring]** nell&#39;istanza di controllo.

![](assets/mc_reports_1.png)

In questo rapporto puoi scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. Puoi anche filtrare i dati per canale e in un periodo specifico.

Gli indicatori visualizzati nella sezione **[!UICONTROL Indicators over the period]** vengono calcolati per il periodo selezionato:

* **[!UICONTROL Incoming (throughput event/h)]**: numero medio orario di eventi immessi nella coda del Centro messaggi.
* **[!UICONTROL Incoming (event vol)]**: numero di eventi immessi nella coda del Centro messaggi.
* **[!UICONTROL Outgoing (throughput msg/h)]**: numero medio orario di eventi del Centro messaggi in uscita completati (inviati da una consegna).
* **[!UICONTROL Outgoing (msg vol)]**: numero di eventi del Centro messaggi in uscita completati (inviati da una consegna).
* **[!UICONTROL Average sending time (seconds)]**: tempo medio trascorso nel Centro messaggi per gli eventi elaborati correttamente. Il calcolo tiene conto del tempo di elaborazione e del tempo di invio dell’MTA.
* **[!UICONTROL Error rate]** : numero di eventi con errori rispetto al numero di eventi che sono entrati nella coda del Centro messaggi. Vengono presi in considerazione i seguenti errori: errore di routing, evento scaduto (evento che è stato nella coda troppo lungo), errore di consegna, ignorato dalla consegna (quarantena, ecc.).

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e di avviso (rosso) possono essere configurate nella procedura guidata di distribuzione. Consulta [Monitorare le soglie](../../message-center/using/additional-configurations.md#monitoring-thresholds).
