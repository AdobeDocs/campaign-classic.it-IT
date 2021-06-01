---
solution: Campaign Classic
product: campaign
title: Livello di servizio del Centro messaggi
description: Ulteriori informazioni sul report a livello di servizio del Centro messaggi.
audience: message-center
content-type: reference
topic-tags: reports
exl-id: b8dc9891-84c8-445d-ad6a-d06048c8faaf
source-git-commit: d39b15b0efc6cbd6ab24e074713be6f8fc90e5fc
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 3%

---

# Livello di servizio del Centro messaggi {#message-center-service-level}

Questo rapporto visualizza le statistiche di consegna relative ai messaggi transazionali e la suddivisione degli errori. Puoi fare clic su un tipo di errore per visualizzarne i dettagli.

Questo rapporto, destinato agli amministratori tecnici, è accessibile anche tramite la scheda **[!UICONTROL Monitoring]** nell’istanza di controllo .

![](assets/mc_reports_1.png)

In questo rapporto puoi scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. Puoi anche filtrare i dati per canale e per un periodo di tempo specifico.

Gli indicatori visualizzati nella sezione **[!UICONTROL Indicators over the period]** vengono calcolati nel periodo selezionato:

* **[!UICONTROL Incoming (throughput event/h)]** : numero medio orario di eventi immessi nella coda del Centro messaggi.
* **[!UICONTROL Incoming (event vol)]** : numero di eventi immessi nella coda del Centro messaggi.
* **[!UICONTROL Outgoing (throughput msg/h)]** : numero medio orario di eventi del Centro messaggi in uscita riusciti (inviati da una consegna).
* **[!UICONTROL Outgoing (msg vol)]** : numero di eventi del Centro messaggi in uscita riusciti (inviati da una consegna).
* **[!UICONTROL Average sending time (seconds)]** : tempo medio trascorso in Centro messaggi per gli eventi elaborati correttamente. Il calcolo tiene conto del tempo di elaborazione e del tempo di invio mta.
* **[!UICONTROL Error rate]** : numero di eventi con errori rispetto al numero di eventi che sono entrati nella coda del Centro messaggi. Vengono presi in considerazione i seguenti errori: errore di routing, evento scaduto (evento che è stato in coda troppo a lungo), errore di consegna, ignorato dalla consegna (quarantena, ecc.).

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e avviso (rosso) possono essere configurate nella procedura guidata di distribuzione. Fare riferimento a [Soglie di monitoraggio](../../message-center/using/additional-configurations.md#monitoring-thresholds).
