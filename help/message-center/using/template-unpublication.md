---
title: Pubblicazione modelli
seo-title: Pubblicazione modelli
description: Pubblicazione modelli
seo-description: null
page-status-flag: never-activated
uuid: f83dbe5f-762c-4c58-aeed-6ec289eb522f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: message-templates
discoiquuid: 43908738-a71a-49be-ac00-175f57a0555c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 71aeeda3edafc64dbe696ce6f344b8b0ccdc43d1
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---


# Annullamento pubblicazione modello{#template-unpublication}

Una volta pubblicato il modello di messaggio sulle istanze di esecuzione, è possibile annullarne la pubblicazione.

In effetti, è ancora possibile chiamare un modello pubblicato. Pertanto, se non utilizzate più un modello di messaggio, è consigliabile annullarne la pubblicazione. In questo modo si evita di inviare per errore un messaggio transazionale indesiderato. Ad esempio, hai pubblicato un modello di messaggio che utilizzavi solo per le campagne natalizie. Potrebbe essere utile annullarla la pubblicazione al termine del periodo natalizio e pubblicarla nuovamente l&#39;anno successivo.

Inoltre, non puoi eliminare un modello di messaggio transazionale con lo **[!UICONTROL Published]** stato. È necessario prima annullare la pubblicazione.

Per annullare la pubblicazione di un modello di messaggio transazionale, effettua le operazioni riportate di seguito.

1. Nell&#39;istanza di controllo, passare alla **[!UICONTROL Message Center > Transactional message templates]** cartella della struttura.
1. Selezionate il modello da annullare la pubblicazione.
1. Clic **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Clic **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Lo stato del modello di messaggio transazionale cambia di nuovo da **[!UICONTROL Published]** a **[!UICONTROL Being edited]**.

Al termine dell&#39;annullamento della pubblicazione:

* Entrambi i modelli di messaggio (applicati agli eventi di tipo batch e in tempo reale) vengono eliminati da ogni istanza di esecuzione. Non vengono più visualizzati nella **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** cartella.

* Dopo aver annullato la pubblicazione di un modello, è possibile eliminarlo dall&#39;istanza di controllo, se necessario. A tale scopo, selezionatelo dall’elenco e fate clic sul **[!UICONTROL Delete]** pulsante in alto a destra dello schermo.