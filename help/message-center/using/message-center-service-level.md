---
title: Livello di servizio del Centro messaggi
seo-title: Livello di servizio del Centro messaggi
description: Livello di servizio del Centro messaggi
seo-description: null
page-status-flag: never-activated
uuid: 8e363706-292b-40db-97bc-d41b41910556
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: reports
discoiquuid: e46a4e87-6c02-4b9c-bf6d-bb4e785e78fa
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 6%

---


# Livello di servizio del Centro messaggi{#message-center-service-level}

Questo rapporto mostra le statistiche di consegna relative ai messaggi transazionali e la suddivisione degli errori. È possibile fare clic su un tipo di errore per visualizzarne i dettagli. Questo rapporto, rivolto agli amministratori tecnici, è accessibile anche attraverso l&#39; **[!UICONTROL Monitoring]** universo nell&#39;istanza di controllo.

![](assets/mc_reports_1.png)

In questo rapporto potete scegliere di visualizzare le statistiche generali o quelle relative a una particolare istanza di esecuzione. È inoltre possibile filtrare i dati per canale e per un periodo specifico. Gli indicatori visualizzati nella **[!UICONTROL Indicators over the period]** sezione sono calcolati nel periodo selezionato:

* **[!UICONTROL Incoming (throughput event/h)]** : numero medio orario di eventi immessi nella coda Centro messaggi.
* **[!UICONTROL Incoming (event vol)]** : numero di eventi immessi nella coda Centro messaggi.
* **[!UICONTROL Outgoing (throughput msg/h)]** : numero medio orario di eventi del Centro messaggi in uscita riusciti (inviati da una consegna).
* **[!UICONTROL Outgoing (msg vol)]** : numero di eventi del Centro messaggi in uscita (inviati da un destinatario).
* **[!UICONTROL Average sending time (seconds)]** : tempo medio trascorso in Centro messaggi per gli eventi elaborati correttamente. Il calcolo prende in considerazione il tempo di elaborazione e il tempo di invio dei dati.
* **[!UICONTROL Error rate]** : numero di eventi con errori rispetto al numero di eventi entrati nella coda del Centro messaggi. Vengono presi in considerazione i seguenti errori: errore di routing, evento scaduto (evento che è stato nella coda troppo lungo), errore di consegna, ignorato dalla consegna (quarantena, ecc.).

>[!NOTE]
>
>Le soglie degli indicatori di avviso (arancione) e avviso (rosso) possono essere configurate nella procedura guidata di distribuzione. Fare riferimento alle soglie [di](../../message-center/using/monitoring-thresholds.md)monitoraggio.

