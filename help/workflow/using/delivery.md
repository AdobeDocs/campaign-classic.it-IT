---
product: campaign
title: Consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro di tipo Consegna
feature: Workflows, Channels Activity
hide: true
hidefromtoc: true
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# Consegna{#delivery}



Un&#39;attività di tipo **Consegna** consente di creare un&#39;azione di consegna. Può essere realizzata utilizzando elementi di input.

Per configurarlo, modifica l’attività e immetti le opzioni di consegna.

![](assets/edit_diffusion.png)

1. **Consegna**

   Puoi eseguire le seguenti azioni:

   * Agisci sulla consegna specificata nella transizione in entrata. A tale scopo, selezionare la prima opzione della sezione **[!UICONTROL Delivery]** della finestra.

     Questa opzione può essere utilizzata quando una precedente attività del flusso di lavoro ha già creato o specificato la consegna. Ciò può essere stato fatto, come nell’esempio seguente, da un’attività dello stesso tipo che ha generato una transizione in uscita.

     Nell’esempio seguente, la consegna viene creata per la prima volta. La popolazione e il contenuto vengono definiti in un secondo momento. Successivamente, le informazioni per questi tre elementi vengono reinserite in una nuova attività di consegna utilizzando la transizione in entrata in modo che possa essere inviata.

     ![](assets/specified_transition_option_exemple.png)

   * Seleziona direttamente la consegna interessata. A tale scopo, selezionare l&#39;opzione **[!UICONTROL Explicit]** e selezionare la consegna dall&#39;elenco a discesa del campo **[!UICONTROL Delivery]**.

     L&#39;elenco mostra le consegne non completate contenute nella cartella **Consegne** per impostazione predefinita. Per accedere ad altre campagne, fare clic sull&#39;icona **[!UICONTROL Select link]**.

     ![](assets/diffusion_edit_1.png)

     Selezionare la campagna dall&#39;elenco a discesa del campo **[!UICONTROL Folder]** oppure fare clic su **[!UICONTROL Display sub-levels]** per visualizzare tutte le consegne contenute nelle sottocartelle:

     ![](assets/diffusion_edit_2.png)

     Dopo aver selezionato l&#39;azione di consegna, puoi visualizzare il contenuto facendo clic sull&#39;icona **[!UICONTROL Edit link]**.

   * Crea uno script per calcolare la consegna. A tale scopo, selezionare l&#39;opzione **[!UICONTROL Computed by a script]** e immettere lo script. È possibile aprire una finestra di input facendo clic sull&#39;opzione **[!UICONTROL Edit...]**. L’esempio seguente recupera l’identificatore della consegna:

     ![](assets/diffusion_edit_3.png)

   * Crea una nuova consegna. A questo scopo, seleziona l’opzione **[!UICONTROL New, created from a template]** e seleziona il modello di consegna su cui basare la consegna.

     ![](assets/diffusion_edit_4.png)

     Fare clic sull&#39;icona **[!UICONTROL Select link]** per sfogliare le cartelle e fare clic sull&#39;icona **[!UICONTROL Edit link]** per visualizzare il contenuto del modello selezionato.

1. **Destinatari**

   I destinatari possono essere specificati dagli eventi in entrata, ad esempio dopo un’importazione di file, o specificati nell’azione di consegna. Possono anche essere archiviati in uno o più file.

   ![](assets/diffusion_edit_5.png)

1. **Contenuto**

   Il contenuto del messaggio può essere definito nella consegna o nell’evento in entrata.

   ![](assets/diffusion_edit_6.png)

1. **Azione da eseguire**

   Puoi creare la consegna, prepararla, avviarla, stimare il target o inviare una bozza.

   ![](assets/diffusion_edit_7.png)

   Seleziona il tipo di azione da eseguire:

   * **[!UICONTROL Save]**: questa opzione consente di creare la consegna e salvarla. Non lo analizzerà né lo consegnerà.
   * **[!UICONTROL Estimate the target]**: questa opzione consente di calcolare il target di consegna per valutarne il potenziale (prima fase di analisi). Questa azione equivale a selezionare l&#39;opzione **[!UICONTROL Estimate the population to be targeted]** e a fare clic su **[!UICONTROL Analyze]** durante l&#39;invio di una consegna alla destinazione principale tramite **Consegna**.
   * **[!UICONTROL Prepare]**: questa opzione consente di eseguire l&#39;intero processo di analisi (calcolo destinazione e preparazione contenuto). La consegna non viene inviata. Questa azione equivale a selezionare l&#39;opzione **[!UICONTROL Deliver as soon as possible]** e a fare clic su **[!UICONTROL Analyze]** quando si invia una consegna alla destinazione principale con **Consegna**.
   * **[!UICONTROL Send a proof]**: questa opzione ti consente di inviare una prova della consegna. Questa azione equivale a fare clic sul pulsante **[!UICONTROL Send a proof]** nella barra degli strumenti di una consegna con **Consegna**
   * **[!UICONTROL Prepare and start]**: questa opzione avvia l&#39;intero processo di analisi (calcolo di destinazione e preparazione dei contenuti) e invia la consegna. Questa azione equivale a fare clic sull&#39;opzione **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** e **[!UICONTROL Confirm delivery]** durante l&#39;invio di una consegna alla destinazione principale con **Consegna**.

   L&#39;attività **[!UICONTROL Act on a delivery]** utilizzata in seguito nel flusso di lavoro consente di avviare tutti i passaggi rimanenti necessari per avviare la consegna (calcolo del target, preparazione del contenuto, consegna). Per ulteriori informazioni, consulta [Controllo della consegna](delivery-control.md).

   Sono inoltre disponibili le seguenti opzioni:

   * **[!UICONTROL Generate an outbound transition]**

     Crea una transizione in uscita che verrà attivata alla fine dell’esecuzione. Puoi scegliere se recuperare o meno la destinazione della consegna in uscita.

   * **[!UICONTROL Do not recover target]**

     Non recupera il target dell’azione di consegna in uscita.

   * **[!UICONTROL Processing errors]**

     Consulta [Controllo della consegna](delivery-control.md).

   La scheda **Script** consente di modificare i parametri di consegna.

   ![](assets/edit_diffusion_fil_script.png)

## Esempio: flusso di lavoro di consegna {#example--delivery-workflow}

Crea un nuovo flusso di lavoro e aggiungi le attività come mostrato nell’immagine seguente:

![](assets/new-workflow-5.png)

Apri l&#39;attività **Consegna** e definisci le proprietà come segue:

* Nella sezione **[!UICONTROL Delivery]**, selezionare **[!UICONTROL New, created from a template]** e selezionare un modello di consegna.
* Nella sezione **[!UICONTROL Recipients]**, selezionare **[!UICONTROL Specified in the delivery]**.
* Nella sezione **[!UICONTROL Action to execute]**, mantenere l&#39;opzione **[!UICONTROL Prepare]**.

![](assets/new-workflow-param-delivery.png)

Fare clic su **[!UICONTROL OK]** per chiudere la finestra delle proprietà. Hai appena configurato un’attività che consiste nella creazione e preparazione di una nuova consegna basata su un modello di consegna il cui target verrà specificato al suo interno.

Apri l&#39;attività **Approval** e definisci le proprietà come segue:

1. Nel campo **[!UICONTROL Assignment type]**, selezionare un gruppo in cui si è registrati. Se si è connessi utilizzando l&#39;account &#39;admin&#39;, selezionare il gruppo Amministrazione.
1. Quindi, inserisci un titolo e il testo seguente nel corpo del messaggio:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Questo messaggio include un&#39;espressione scritta in JavaScript: **[!UICONTROL vars.recCount]** rappresenta il numero di destinatari interessati dalla consegna dell&#39;attività precedente. Per ulteriori informazioni sulle espressioni di JavaScript, fare riferimento a [Script e modelli di JavaScript](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   L&#39;attività Approvazione è descritta in [Approvazione](approval.md).

## Parametri di input {#input-parameters}

Identificatore di consegna, se l&#39;opzione **[!UICONTROL Specified in the transition]** è selezionata nella sezione **[!UICONTROL Delivery]**.

* deliveryId
* tableName
* schema

Ogni evento in entrata deve specificare una destinazione definita da questi parametri.

>[!NOTE]
>
>Questo parametro viene visualizzato solo se l&#39;opzione **[!UICONTROL Specified by inbound event(s)]** è selezionata nella sezione **[!UICONTROL Recipients]**.

* nome file

  Nome completo del file generato se l&#39;opzione **[!UICONTROL File(s) specified by inbound event(s)]** è selezionata nella sezione **[!UICONTROL Recipients]**.

* contentId

  Identificatore di contenuto se l&#39;opzione **[!UICONTROL Specified by inbound events]** è selezionata nella sezione **[!UICONTROL Content]**.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo set di tre valori identifica il target risultante dalla consegna. **[!UICONTROL tableName]** è il nome della tabella che memorizza gli identificatori della destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.

>[!NOTE]
>
>Non sono presenti parametri di output quando l&#39;opzione **[!UICONTROL Do not recover target]** è selezionata.
