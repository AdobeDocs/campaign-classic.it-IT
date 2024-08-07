---
product: campaign
title: Progettare modelli di messaggi transazionali
description: Scopri come creare e progettare un modello di messaggio transazionale in Adobe Campaign Classic
feature: Transactional Messaging, Message Center, Templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '498'
ht-degree: 0%

---

# Progettare modelli di messaggi transazionali {#creating-the-message-template}



Per garantire che ogni evento possa essere trasformato in un messaggio personalizzato, devi creare un modello di messaggio corrispondente a ciascun tipo di evento.

>[!IMPORTANT]
>
>I tipi di evento devono essere creati in anticipo. Per ulteriori informazioni, consulta [Creare tipi di evento](../../message-center/using/creating-event-types.md).

I modelli per messaggi transazionali contengono le informazioni necessarie per personalizzare il messaggio transazionale. Puoi inoltre utilizzare i modelli per verificare l’anteprima dei messaggi e inviare bozze utilizzando indirizzi di seed prima della consegna al target finale. Per ulteriori informazioni, consulta [Test dei modelli di messaggi transazionali](../../message-center/using/testing-message-templates.md).

## Creare il modello di messaggio {#creating-message-template}

1. Passare alla cartella **[!UICONTROL Message Center >Transactional message templates]** nella struttura Adobe Campaign.

1. Nell&#39;elenco dei modelli di messaggi transazionali, fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL New]** nel menu a discesa oppure fare clic sul pulsante **[!UICONTROL New]** sopra l&#39;elenco dei modelli di messaggi transazionali.

   ![](assets/messagecenter_create_model_001.png)

1. Nella finestra di dialogo di consegna, seleziona il modello di consegna adatto al canale che desideri utilizzare.

   ![](assets/messagecenter_create_model_002.png)

1. Se necessario, modificane l’etichetta.

1. Seleziona il tipo di evento che corrisponde al messaggio da inviare.

   ![](assets/messagecenter_create_model_003.png)

   I tipi di evento devono essere creati in anticipo nella console. Per ulteriori informazioni, consulta [Creare tipi di evento](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Un tipo di evento non può essere collegato a più modelli.

1. Immettere una natura e una descrizione, quindi fare clic su **[!UICONTROL Continue]** per creare il corpo del messaggio (fare riferimento a [Creare il contenuto del messaggio](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Creare il contenuto del messaggio {#creating-message-content}

La definizione del contenuto dei messaggi transazionali è la stessa utilizzata per le consegne regolari in Adobe Campaign. Ad esempio, per una consegna e-mail, puoi creare contenuto in formato HTML o testo, aggiungere allegati o personalizzare l’oggetto di consegna. Per ulteriori informazioni, consulta il capitolo [Email delivery](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>Le immagini incluse nel messaggio devono essere accessibili al pubblico. Adobe Campaign non fornisce alcun meccanismo di caricamento di immagini per i messaggi transazionali.\
>A differenza di JSSP o WebApp, `<%=` non ha alcun escape predefinito.
>
>In questo caso, è necessario eseguire correttamente l’escape di ogni dato proveniente dall’evento. L’escape dipende da come viene utilizzato questo campo. Ad esempio, all’interno di un URL, utilizza encodeURIComponent. Per essere visualizzato in HTML, è possibile utilizzare escapeXMLString.

Dopo aver definito il contenuto del messaggio, puoi integrare le informazioni sull’evento nel corpo del messaggio e personalizzarlo. Le informazioni sull’evento vengono inserite nel corpo del testo grazie ai tag di personalizzazione.

![](assets/messagecenter_create_content_001.png)

* Tutti i campi di personalizzazione provengono dal payload.
* È possibile fare riferimento a uno o più blocchi di personalizzazione in un messaggio transazionale. Il contenuto del blocco verrà aggiunto al contenuto della consegna durante la pubblicazione nell’istanza di esecuzione.

Per inserire i tag di personalizzazione nel corpo di un messaggio e-mail, effettua le seguenti operazioni:

1. Nel modello del messaggio, fai clic sulla scheda corrispondente al formato e-mail (HTML o testo).

1. Inserisci il corpo del messaggio.

1. Nel corpo del testo, inserire il tag utilizzando il menu **[!UICONTROL Real time events > Event XML]**.

   ![](assets/messagecenter_create_custo_002.png)

1. Compila il tag utilizzando la seguente sintassi: **nome elemento**.@**nome attributo** come mostrato di seguito.

   ![](assets/messagecenter_create_custo_003.png)

1. Salva il contenuto.

Il messaggio è pronto per essere [testato](../../message-center/using/testing-message-templates.md).
