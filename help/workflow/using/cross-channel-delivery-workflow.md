---
solution: Campaign Classic
product: campaign
title: Flusso di lavoro di consegna cross-channel
description: Ulteriori informazioni sui flussi di lavoro per la distribuzione tra canali
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 3%

---


# Flusso di lavoro di consegna cross-channel{#cross-channel-delivery-workflow}

Questo caso d’uso presenta un esempio che coinvolge un flusso di lavoro per la distribuzione tra canali. Il concetto generale di consegne tra canali è presentato in [questa sezione](../../workflow/using/cross-channel-deliveries.md).

L&#39;obiettivo è quello di segmentare un&#39;audience dai destinatari del database in diversi gruppi allo scopo di inviare un&#39;e-mail a un gruppo e un messaggio SMS a un altro gruppo.

Le fasi di implementazione principali per questo caso di utilizzo sono le seguenti:

1. Creazione di un&#39;attività **[!UICONTROL Query]** destinata al pubblico.
1. Creazione di un&#39;attività **[!UICONTROL Email delivery]** contenente un collegamento a un&#39;offerta.
1. Utilizzo di un&#39;attività **[!UICONTROL Split]** per:

   * Inviare un altro messaggio e-mail ai destinatari che non hanno aperto il primo messaggio e-mail.
   * Inviate un SMS ai destinatari che hanno aperto l’e-mail ma non hanno fatto clic sul collegamento all’offerta.
   * Aggiungete al database i destinatari che hanno aperto l’e-mail e hanno fatto clic sul collegamento.

![](assets/wkf_cross-channel_7.png)

## Passaggio 1: Targeting dell&#39;audience {#step-1--targeting-the-audience}

Per definire la destinazione, create una query per identificare i destinatari.

1. Creare una campagna. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. Nella scheda **[!UICONTROL Targeting and workflows]** della campagna, aggiungi un&#39;attività **Query** al flusso di lavoro. Per ulteriori informazioni sull&#39;utilizzo di questa attività, consultare [questa sezione](../../workflow/using/query.md).
1. Definite i destinatari che riceveranno le vostre consegne. Ad esempio, selezionare i membri &quot;Gold&quot; come dimensione di destinazione.
1. Aggiungere condizioni di filtraggio alla query. In questo esempio, selezionate i destinatari che dispongono di un indirizzo e-mail e di un numero mobile.

   ![](assets/wkf_cross-channel_3.png)

1. Salva le modifiche.

## Passaggio 2: Creazione di un&#39;e-mail con un&#39;offerta {#step-2--creating-an-email-including-an-offer}

1. Create un&#39;attività **[!UICONTROL Email delivery]** e fate doppio clic su di essa nel flusso di lavoro per modificarla. Per ulteriori informazioni sulla creazione di un&#39;e-mail, consultare [questa sezione](../../delivery/using/about-email-channel.md).
1. Progettate il messaggio e inserite un collegamento che includa un&#39;offerta nel contenuto.

   ![](assets/wkf_cross-channel_1.png)

   Per ulteriori informazioni sull&#39;integrazione di un&#39;offerta nel corpo di un messaggio, fare riferimento a [questa sezione](../../interaction/using/integrating-an-offer-via-the-wizard.md#delivering-with-a-call-to-the-offer-engine).

1. Salva le modifiche.
1. Fare clic con il pulsante destro del mouse sull&#39;attività **[!UICONTROL Email delivery]** per aprirla.
1. Selezionare l&#39;opzione **[!UICONTROL Generate an outbound transition]** per recuperare la popolazione e i registri di monitoraggio.

   ![](assets/wkf_cross-channel_2.png)

   In questo modo potrete utilizzare queste informazioni per inviare un&#39;altra consegna a seconda del comportamento dei destinatari che ricevono la prima e-mail.

1. Aggiungete un&#39;attività **[!UICONTROL Wait]** per consentire ai destinatari di aprire l&#39;e-mail entro alcuni giorni.

   ![](assets/wkf_cross-channel_4.png)

## Passaggio 3: Segmentazione dell&#39;audience risultante {#step-3--segmenting-the-resulting-audience}

Una volta identificato il target e creata la prima consegna, è necessario segmentare il target in popolazioni diverse utilizzando le condizioni di filtro.

1. Aggiungete un&#39;attività **Dividi** al flusso di lavoro e apritela. Per ulteriori informazioni sull&#39;utilizzo di questa attività, consultare [questa sezione](../../workflow/using/split.md).
1. Crea tre segmenti dalla popolazione calcolata a monte nella query.

   ![](assets/wkf_cross-channel_6.png)

1. Per il primo sottoinsieme, selezionare l&#39;opzione **[!UICONTROL Add a filtering condition on the inbound population]** e fare clic su **[!UICONTROL Edit]**.

   ![](assets/wkf_cross-channel_8.png)

1. Selezionare **[!UICONTROL Recipients of a delivery]** come filtro di restrizione e fare clic su **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_9.png)

1. Nelle impostazioni del filtro, selezionate **[!UICONTROL Recipients who have not opened or clicked (email)]** dall&#39;elenco a discesa **[!UICONTROL Behavior]** e selezionate l&#39;e-mail che include l&#39;offerta da inviare dall&#39;elenco di consegna. Fai clic su **[!UICONTROL Finish]**.

   ![](assets/wkf_cross-channel_10.png)

1. Procedere in modo simile per il secondo sottoinsieme e selezionare **[!UICONTROL Recipients who have not clicked (email)]** dall&#39;elenco a discesa **[!UICONTROL Behavior]**.

   ![](assets/wkf_cross-channel_11.png)

1. Per il terzo sottoinsieme, dopo aver selezionato **[!UICONTROL Add a filtering condition on the inbound population]** e aver fatto clic su **[!UICONTROL Edit]**, selezionare l&#39;opzione **[!UICONTROL Use a specific filtering dimension]**.
1. Selezionare **[!UICONTROL Recipient tracking log]** dall&#39;elenco a discesa **[!UICONTROL Filtering dimension]**, evidenziare **[!UICONTROL Filtering conditions]** dal **[!UICONTROL List of restriction filters]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/wkf_cross-channel_12.png)

1. Selezionate le condizioni del filtro come segue:

   ![](assets/wkf_cross-channel_13.png)

1. Fare clic su **[!UICONTROL Finish]** per salvare le modifiche.

## Passaggio 4: Finalizzazione del flusso di lavoro {#step-4--finalizing-the-workflow}

1. Aggiungete le attività pertinenti al flusso di lavoro dopo i tre sottoinsiemi risultanti dall&#39;attività **[!UICONTROL Split]**:

   * Aggiungete un&#39;attività **[!UICONTROL Email delivery]** per inviare un messaggio e-mail di promemoria al primo sottoinsieme.
   * Aggiungete un&#39;attività **[!UICONTROL Mobile delivery]** per inviare un messaggio SMS al secondo sottoinsieme.
   * Aggiungete un&#39;attività **[!UICONTROL List update]** per aggiungere i destinatari corrispondenti al database.

1. Fate doppio clic sulle attività di consegna nel flusso di lavoro per modificarle. Per ulteriori informazioni sulla creazione di un&#39;e-mail e di un SMS, fare riferimento a [Canale e-mail](../../delivery/using/about-email-channel.md) e [Canale SMS](../../delivery/using/sms-channel.md).
1. Fare doppio clic sull&#39;attività **[!UICONTROL List update]** e selezionare l&#39;opzione **[!UICONTROL Generate an outbound transition]**.

   Potete quindi esportare i destinatari risultanti da  Adobe Campaign nell’Adobe Experience Cloud. Ad esempio, potete utilizzare il pubblico in  Adobe Target aggiungendo un&#39;attività **[!UICONTROL Update shared audience]** al flusso di lavoro. Per ulteriori informazioni, vedere [Esportazione di un&#39;audience](../../integrations/using/importing-and-exporting-audiences.md#exporting-an-audience).

1. Fate clic sul pulsante **Start** nella barra delle azioni per eseguire il flusso di lavoro.

La popolazione di destinazione dell&#39;attività **Query** verrà segmentata per ricevere un&#39;e-mail o un SMS in base ai comportamenti dei destinatari. La popolazione rimanente verrà aggiunta al database utilizzando l&#39;attività **[!UICONTROL List update]**.
