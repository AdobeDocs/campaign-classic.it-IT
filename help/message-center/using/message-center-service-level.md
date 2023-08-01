---
product: campaign
title: Livello di servizio del Centro messaggi
description: Ulteriori informazioni sul report del livello di servizio del Centro messaggi
feature: Transactional Messaging, Message Center
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 3%

---

# Livello di servizio del Centro messaggi {#message-center-service-level}



Questo rapporto visualizza le statistiche di consegna relative ai messaggi transazionali e il raggruppamento degli errori. Puoi fare clic su un tipo di errore per visualizzarne i dettagli.

Il report, destinato agli amministratori tecnici, è accessibile anche tramite il **[!UICONTROL Monitoring]** sull&#39;istanza di controllo.

![](assets/mc_reports_1.png)

In questo rapporto puoi scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. Puoi anche filtrare i dati per canale e in un periodo specifico.

Gli indicatori visualizzati nella **[!UICONTROL Indicators over the period]** vengono calcolate nel periodo selezionato:

* **[!UICONTROL Incoming (throughput event/h)]** : numero medio orario di eventi immessi nella coda del Centro messaggi.
* **[!UICONTROL Incoming (event vol)]** : numero di eventi immessi nella coda del Centro messaggi.
* **[!UICONTROL Outgoing (throughput msg/h)]** : numero medio orario di eventi del Centro messaggi in uscita riusciti (inviati da una consegna).
* **[!UICONTROL Outgoing (msg vol)]** : numero di eventi del Centro messaggi in uscita completati (inviati da una consegna).
* **[!UICONTROL Average sending time (seconds)]** : tempo medio trascorso nel Centro messaggi per gli eventi elaborati correttamente. Il calcolo tiene conto del tempo di elaborazione e del tempo di invio dell’MTA.
* **[!UICONTROL Error rate]** : numero di eventi con errori rispetto al numero di eventi che sono entrati nella coda del Centro messaggi. Vengono presi in considerazione i seguenti errori: errore di routing, evento scaduto (evento che è stato nella coda troppo lungo), errore di consegna, ignorato dalla consegna (quarantena, ecc.).

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e di avviso (rosso) possono essere configurate nella procedura guidata di distribuzione. Fai riferimento a [Monitorare le soglie](../../message-center/using/additional-configurations.md#monitoring-thresholds).
