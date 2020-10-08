---
title: Impostazioni di esecuzione
seo-title: Impostazioni di esecuzione
description: Impostazioni di esecuzione
seo-description: null
page-status-flag: never-activated
uuid: a6549091-0c33-4fe1-adde-de3b285dd456
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: interaction
content-type: reference
topic-tags: simulating-offers
discoiquuid: 52b5d5a9-10dc-4601-8fe4-962a2334322b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 5%

---


# Impostazioni di esecuzione{#execution-settings}

Quando create una simulazione, potete specificare le impostazioni di esecuzione, se necessario. Queste impostazioni consentono di eseguire la simulazione durante un periodo di attività bassa a seconda della priorità o di registrare le query SQL nel registro. Questa fase è facoltativa.

Queste impostazioni possono essere modificate successivamente nella **[!UICONTROL General]** scheda della finestra di simulazione.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : consente di pianificare la simulazione in base alla priorità scelta (Basso, Media o Alta) per ottimizzare  prestazioni Adobe Campaign.
* **[!UICONTROL Priority]** : questo è il livello applicato alla simulazione per programmarla. Quando l&#39; **[!UICONTROL Schedule execution for a time of low activity]** opzione è selezionata, il flusso di lavoro di elaborazione della campagna seleziona un&#39;ora di attività bassa per avviare la campagna.
* **[!UICONTROL Log SQL queries in the journal]** : questa funzionalità è riservata solo agli utenti esperti. Consente di aggiungere una scheda al registro che visualizza query SQL per rilevare eventuali malfunzionamenti se la simulazione termina con errori.

