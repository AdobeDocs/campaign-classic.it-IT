---
title: Flussi di lavoro tecnici
seo-title: Flussi di lavoro tecnici
description: Flussi di lavoro tecnici
seo-description: null
page-status-flag: never-activated
uuid: dfd1b180-86b5-4740-9bad-a0e210f433c5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: instance-configuration
discoiquuid: 2e648e63-06d2-4e8f-9934-066a41d18eac
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 10%

---


# Flussi di lavoro tecnici{#technical-workflows}

Devi accertarti che i flussi di lavoro tecnici sull&#39;istanza di controllo e sulle diverse istanze di esecuzione siano effettivamente stati creati e avviati prima di distribuire qualsiasi modello di messaggio transazionale.

I vari flussi di lavoro tecnici relativi ai messaggi transazionali (Centro messaggi) sono suddivisi tra l&#39;istanza di controllo e le istanze di esecuzione.

## Flussi di lavoro delle istanze di controllo {#control-instance-workflows}

Nell&#39;istanza di controllo è necessario creare un flusso di lavoro di archiviazione per istanza di esecuzione. I flussi di lavoro di archiviazione sono quindi accessibili dalla cartella **Amministrazione > Produzione > Centro** messaggi. Una volta creati, i flussi di lavoro di archiviazione vengono avviati automaticamente.

**Architettura distribuita**

Se si dispone di una o più istanze di esecuzione registrate, nell&#39;istanza di controllo è necessario creare un flusso di lavoro di archiviazione per ciascun account **[!UICONTROL Message Center execution instance]** esterno. Fate clic sul **[!UICONTROL Create the archiving workflow]** pulsante per creare e avviare il flusso di lavoro.

![](assets/messagecenter_archiving_002.png)

**Architettura minima**

Una volta che i moduli di controllo e di esecuzione sono installati nella stessa istanza, è necessario creare il flusso di lavoro di archiviazione utilizzando la procedura guidata di distribuzione. Fate clic sul **[!UICONTROL Create the archiving workflow]** pulsante per creare e avviare il flusso di lavoro.

![](assets/messagecenter_archiving_001.png)

## Flussi di lavoro per le istanze di esecuzione {#execution-instance-workflows}

Nelle istanze di esecuzione, è possibile accedere ai flussi di lavoro tecnici per i messaggi transazionali dalla cartella **Amministrazione > Produzione > Centro** messaggi. Dovete solo iniziare a farlo. I flussi di lavoro elencati sono:

* **[!UICONTROL Processing batch events]** (nome interno: **[!UICONTROL batchEventsProcessing]** ): questo flusso di lavoro consente di suddividere gli eventi batch in una coda prima che siano collegati a un modello di messaggio.
* **[!UICONTROL Processing real time events]** (nome interno: **[!UICONTROL rtEventsProcessing]** ): questo flusso di lavoro consente di suddividere gli eventi in tempo reale in una coda prima che siano collegati a un modello di messaggio.
* **[!UICONTROL Update event status]** (nome interno: **[!UICONTROL updateEventStatus]** ): questo flusso di lavoro consente di attribuire uno stato all’evento.

   Sono disponibili i seguenti stati dell&#39;evento:

   * **[!UICONTROL Pending]** : l&#39;evento è nella coda. Non è ancora stato assegnato alcun modello di messaggio.
   * **[!UICONTROL Pending delivery]** : l&#39;evento è nella coda, gli è stato assegnato un modello di messaggio e viene elaborato dal recapito.
   * **[!UICONTROL Sent]** : questo stato viene copiato dai registri di consegna. Significa che la consegna è stata inviata.
   * **[!UICONTROL Ignored by the delivery]** : questo stato viene copiato dai registri di consegna. Significa che la consegna è stata ignorata.
   * **[!UICONTROL Delivery failed]** : questo stato viene copiato dai registri di consegna. Significa che la consegna è non è andata a buon fine.
   * **[!UICONTROL Event not taken into account]** : impossibile collegare l&#39;evento a un modello di messaggio. L’evento non viene elaborato.

