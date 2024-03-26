---
product: campaign
title: Impostazioni di esecuzione
description: Impostazioni di esecuzione
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Impostazioni di esecuzione{#execution-settings}



Quando crei una simulazione, puoi specificare le impostazioni di esecuzione, se necessario. Queste impostazioni consentono di eseguire la simulazione in un periodo di bassa attività a seconda della priorità o di registrare le query SQL nel registro. Questa fase è facoltativa.

Queste impostazioni possono essere modificate in un secondo momento nel **[!UICONTROL General]** della finestra di simulazione.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : consente di pianificare la simulazione in base alla priorità scelta (Bassa, Media o Alta) per ottimizzare le prestazioni di Adobe Campaign.
* **[!UICONTROL Priority]** : questo è il livello applicato alla simulazione per pianificarla. Quando **[!UICONTROL Schedule execution for a time of low activity]** se questa opzione è selezionata, il flusso di lavoro di elaborazione della campagna seleziona un periodo di bassa attività per avviare la campagna.
* **[!UICONTROL Log SQL queries in the journal]** : questa funzionalità è riservata agli utenti esperti. Consente di aggiungere una scheda al registro che visualizza le query SQL per rilevare possibili malfunzionamenti se la simulazione termina con errori.
