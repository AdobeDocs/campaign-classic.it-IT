---
title: Esecuzione della consegna
seo-title: Esecuzione della consegna
description: Esecuzione della consegna
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 9%

---


# Esecuzione della consegna{#delivery-execution}

>[!NOTE]
>
>L&#39;MTA dà priorità all&#39;elaborazione dei messaggi transazionali rispetto a qualsiasi altra consegna.

Nell’istanza di esecuzione, una volta completata la fase di arricchimento e collegato un modello di consegna all’evento, la consegna viene inviata. Tutte le consegne sono raggruppate nella **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** cartella.

![](assets/messagecenter_deliveries_execinstances_001.png)

Per impostazione predefinita, sono ordinati in sottocartelle per mese di consegna.

Questo ordinamento può essere modificato nelle proprietà del modello di messaggio come mostrato di seguito.

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>Per le installazioni ospitate o ibride, se avete effettuato l&#39;aggiornamento all&#39;MTA avanzato, tutti i messaggi transazionali possono essere inviati anche con l&#39;MTA avanzata di Adobe Campaign  per migliorare la recapito, il throughput e la gestione dei bounce. Tutti gli impatti sono gli stessi dei messaggi di marketing standard e sono descritti nel documento MTA [avanzato di](https://helpx.adobe.com/it/campaign/kb/acc-campaign-enhanced-mta.html) Adobe Campaign.