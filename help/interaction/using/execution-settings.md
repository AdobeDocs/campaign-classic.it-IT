---
solution: Campaign Classic
product: campaign
title: Impostazioni di esecuzione
description: Impostazioni di esecuzione
audience: interaction
content-type: reference
topic-tags: simulating-offers
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# Impostazioni di esecuzione{#execution-settings}

Quando create una simulazione, potete specificare le impostazioni di esecuzione, se necessario. Queste impostazioni consentono di eseguire la simulazione durante un periodo di attività bassa a seconda della priorità o di registrare le query SQL nel registro. Questa fase è facoltativa.

Queste impostazioni possono essere modificate successivamente nella scheda **[!UICONTROL General]** della finestra di simulazione.

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** : consente di pianificare la simulazione in base alla priorità scelta (Basso, Media o Alta) per ottimizzare  prestazioni Adobe Campaign.
* **[!UICONTROL Priority]** : questo è il livello applicato alla simulazione per programmarla. Quando l&#39;opzione **[!UICONTROL Schedule execution for a time of low activity]** è selezionata, il flusso di lavoro di elaborazione della campagna seleziona un periodo di tempo limitato per avviare la campagna.
* **[!UICONTROL Log SQL queries in the journal]** : questa funzionalità è riservata solo agli utenti esperti. Consente di aggiungere una scheda al registro che visualizza query SQL per rilevare eventuali malfunzionamenti se la simulazione termina con errori.

