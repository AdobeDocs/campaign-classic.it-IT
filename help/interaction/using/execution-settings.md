---
product: campaign
title: Impostazioni di esecuzione
description: Impostazioni di esecuzione
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# Impostazioni di esecuzione{#execution-settings}



Quando crei una simulazione, puoi specificare le impostazioni di esecuzione, se necessario. Queste impostazioni consentono di eseguire la simulazione durante un periodo di attività bassa a seconda della sua priorità o di registrare le query SQL nel registro. Questa fase è facoltativa.

Queste impostazioni possono essere modificate successivamente nella sezione **[!UICONTROL General]** scheda della finestra di simulazione.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : ti consente di pianificare la simulazione in base alla priorità scelta (Bassa, Media o Alta) per ottimizzare le prestazioni di Adobe Campaign.
* **[!UICONTROL Priority]** : questo è il livello applicato alla simulazione per pianificarla. Quando il **[!UICONTROL Schedule execution for a time of low activity]** è selezionata, il flusso di lavoro di elaborazione della campagna seleziona un periodo di tempo di attività insufficiente per avviare la campagna.
* **[!UICONTROL Log SQL queries in the journal]** : questa funzionalità è riservata solo agli utenti esperti. Consente di aggiungere una scheda al registro che visualizza le query SQL per rilevare eventuali malfunzionamenti se la simulazione termina con errori.
