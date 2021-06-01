---
solution: Campaign Classic
product: campaign
title: Progettare modelli di messaggi transazionali
description: Scopri come creare e progettare un modello di messaggio transazionale in Adobe Campaign Classic.
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: a52bc140-072e-4f81-b6da-f1b38662bce5
source-git-commit: a9054fb8e10bef37675922b2f81c7615cd04c1bb
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Progettare modelli di messaggi transazionali {#creating-the-message-template}

Per fare in modo che ogni evento possa essere modificato in un messaggio personalizzato, devi creare un modello di messaggio per corrispondere a ciascun tipo di evento.

>[!IMPORTANT]
>
>È necessario creare in anticipo i tipi di evento. Per ulteriori informazioni, consulta [Creazione di tipi di evento](../../message-center/using/creating-event-types.md).

I modelli di messaggi transazionali contengono le informazioni necessarie per personalizzare il messaggio transazionale. Puoi inoltre utilizzare i modelli per testare l’anteprima del messaggio e inviare bozze utilizzando gli indirizzi di seed prima di consegnarle al target finale. Per ulteriori informazioni, consulta [Verifica dei modelli di messaggi transazionali](../../message-center/using/testing-message-templates.md).

## Creare il modello di messaggio {#creating-message-template}

1. Vai alla cartella **[!UICONTROL Message Center >Transactional message templates]** nella struttura di Adobe Campaign.

1. Nell’elenco dei modelli di messaggi transazionali, fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL New]** nel menu a discesa oppure fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco dei modelli di messaggi transazionali.

   ![](assets/messagecenter_create_model_001.png)

1. Nella finestra di consegna, seleziona il modello di consegna adatto al canale che desideri utilizzare.

   ![](assets/messagecenter_create_model_002.png)

1. Se necessario, modificarne l’etichetta.

1. Seleziona il tipo di evento che corrisponde al messaggio che desideri inviare.

   ![](assets/messagecenter_create_model_003.png)

   I tipi di evento devono essere creati in precedenza nella console. Per ulteriori informazioni, consulta [Creazione di tipi di evento](../../message-center/using/creating-event-types.md).

   >[!IMPORTANT]
   >
   >Un tipo di evento non può essere collegato a più di un modello.

1. Immetti una natura e una descrizione, quindi fai clic su **[!UICONTROL Continue]** per creare il corpo del messaggio (consulta [Creazione del contenuto del messaggio](#creating-message-content)).

   ![](assets/messagecenter_create_model_004.png)

## Crea il contenuto del messaggio {#creating-message-content}

La definizione del contenuto dei messaggi transazionali è la stessa utilizzata per le consegne regolari in Adobe Campaign. Ad esempio, per una consegna e-mail, puoi creare contenuto in formato HTML o testo, aggiungere allegati o personalizzare l’oggetto di consegna. Per ulteriori informazioni, consulta il capitolo su [Email delivery](../../delivery/using/about-email-channel.md).

>[!IMPORTANT]
>
>Le immagini incluse nel messaggio devono essere accessibili al pubblico. Adobe Campaign non fornisce alcun meccanismo di caricamento delle immagini per i messaggi transazionali.\
>A differenza di JSSP o webApp, `<%=` non dispone di escape predefinito.
>
>In questo caso, è necessario eseguire correttamente l’escape di ogni dato proveniente dall’evento. Questo escape dipende da come viene utilizzato questo campo. Ad esempio, all’interno di un URL, utilizza encodeURIComponent. Per essere visualizzato nell&#39;HTML, è possibile utilizzare escapeXMLString.

Una volta definito il contenuto del messaggio, puoi integrare le informazioni sull’evento nel corpo del messaggio e personalizzarlo. Le informazioni sull’evento vengono inserite nel corpo del testo grazie ai tag di personalizzazione.

![](assets/messagecenter_create_content_001.png)

* Tutti i campi di personalizzazione provengono dal payload.
* È possibile fare riferimento a uno o più blocchi di personalizzazione in un messaggio transazionale. Il contenuto del blocco verrà aggiunto al contenuto della consegna durante la pubblicazione nell’istanza di esecuzione.

Per inserire tag di personalizzazione nel corpo di un messaggio e-mail, effettua le seguenti operazioni:

1. Nel modello di messaggio, fai clic sulla scheda che corrisponde al formato dell’e-mail (HTML o testo).

1. Inserisci il corpo del messaggio.

1. Nel corpo del testo, inserisci il tag utilizzando il menu **[!UICONTROL Real time events > Event XML]** .

   ![](assets/messagecenter_create_custo_002.png)

1. Compila il tag utilizzando la seguente sintassi: **nome elemento**.@**nome dell&#39;attributo** come mostrato di seguito.

   ![](assets/messagecenter_create_custo_003.png)

1. Salva il contenuto.

Il messaggio è ora pronto per essere [testato](../../message-center/using/testing-message-templates.md).
