---
solution: Campaign Classic
product: campaign
title: Pubblicazione di modelli
description: Pubblicazione di modelli
audience: message-center
content-type: reference
topic-tags: message-templates
translation-type: tm+mt
source-git-commit: 02dee9c4cc03784ccc20f147f816798248bd10f2
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 3%

---


# Annullamento della pubblicazione di modelli{#template-unpublication}

Una volta pubblicato il modello di messaggio sulle istanze di esecuzione, è possibile annullarne la pubblicazione. Per ulteriori informazioni sul processo di pubblicazione dei modelli, vedere [questa sezione](../../message-center/using/template-publication.md).

* In effetti, un modello pubblicato può ancora essere chiamato se viene attivato l&#39;evento corrispondente: se non utilizzi più un modello di messaggio, è consigliabile annullarne la pubblicazione. In questo modo si evita di inviare per errore un messaggio transazionale indesiderato.

   Ad esempio, hai pubblicato un modello di messaggio che utilizzavi solo per le campagne natalizie. Potrebbe essere utile annullarla la pubblicazione al termine del periodo natalizio e pubblicarla nuovamente l&#39;anno successivo.

* Inoltre, non è possibile eliminare un modello di messaggio transazionale con lo stato **[!UICONTROL Published]**. È necessario prima annullare la pubblicazione.

>[!NOTE]
>
>Questa funzionalità è disponibile a partire dalla release Campaign 20.2.

Per annullare la pubblicazione di un modello di messaggio transazionale, effettua le operazioni riportate di seguito.

1. Nell&#39;istanza di controllo, passare alla cartella **[!UICONTROL Message Center > Transactional message templates]** della struttura.
1. Selezionate il modello da annullare la pubblicazione.
1. Fai clic su **[!UICONTROL Unpublish]**.

   <!--1. Fill in the **[!UICONTROL Log of the process]** field.-->

1. Fai clic su **[!UICONTROL Start]**.

![](assets/message-center-unpublish.png)

Lo stato del modello di messaggio transazionale cambia da **[!UICONTROL Published]** a **[!UICONTROL Being edited]**.

Al termine dell&#39;annullamento della pubblicazione:

* Entrambi i modelli di messaggio (applicati agli eventi di tipo batch e in tempo reale) vengono eliminati da ogni istanza di esecuzione.

   Non vengono più visualizzati nella cartella **[!UICONTROL Administration > Production > Message Center Execution > Default > Transactional message templates]** (vedere [questa sezione](../../message-center/using/template-publication.md)).

* Dopo aver annullato la pubblicazione di un modello, è possibile eliminarlo dall’istanza di controllo.

   A tal fine, selezionatelo dall&#39;elenco e fate clic sul pulsante **[!UICONTROL Delete]** in alto a destra della schermata.