---
product: campaign
title: Consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro di tipo Consegna
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 0%

---

# Consegna{#delivery}

Un’attività di tipo **Consegna** ti consente di creare un’azione di consegna. Può essere costruito utilizzando elementi di input.

Per configurarlo, modifica l’attività e immetti le opzioni di consegna.

![](assets/edit_diffusion.png)

1. **Consegna**

   Puoi:

   * Agisci sulla consegna specificata nella transizione in entrata. A questo scopo, seleziona la prima opzione della sezione **[!UICONTROL Delivery]** della finestra.

      Questa opzione può essere utilizzata quando un’attività del flusso di lavoro precedente ha già creato o specificato la consegna. Questo può essere stato fatto, come nell’esempio seguente, da un’attività dello stesso tipo che ha generato una transizione in uscita.

      Nell’esempio seguente, la consegna viene creata per la prima volta. La popolazione e il contenuto vengono definiti successivamente. Successivamente, le informazioni per questi tre elementi vengono reinserite in una nuova attività di consegna utilizzando la transizione in entrata, in modo che possa essere inviata.

      ![](assets/specified_transition_option_exemple.png)

   * Selezionare direttamente la consegna interessata. A questo scopo, seleziona l’opzione **[!UICONTROL Explicit]** e seleziona la consegna dall’elenco a discesa del campo **[!UICONTROL Delivery]** .

      Per impostazione predefinita, l’elenco mostra le consegne non completate contenute nella cartella **Consegne** . Per accedere ad altre campagne, fai clic sull’icona **[!UICONTROL Select link]** .

      ![](assets/diffusion_edit_1.png)

      Seleziona la campagna dall’elenco a discesa del campo **[!UICONTROL Folder]** oppure fai clic su **[!UICONTROL Display sub-levels]** per visualizzare tutte le consegne contenute nelle sottocartelle:

      ![](assets/diffusion_edit_2.png)

      Dopo aver selezionato l’azione di consegna, puoi visualizzare il contenuto facendo clic sull’icona **[!UICONTROL Edit link]** .

   * Crea uno script per calcolare la consegna. A questo scopo, seleziona l’opzione **[!UICONTROL Computed by a script]** e immetti lo script. Per aprire una finestra di input, fai clic sull’opzione **[!UICONTROL Edit...]** . L’esempio seguente recupera l’identificatore della consegna:

      ![](assets/diffusion_edit_3.png)

   * Crea una nuova consegna. A questo scopo, seleziona l’opzione **[!UICONTROL New, created from a template]** e seleziona il modello di consegna su cui verrà basata la consegna.

      ![](assets/diffusion_edit_4.png)

      Fai clic sull&#39;icona **[!UICONTROL Select link]** per sfogliare le cartelle e fai clic sull&#39;icona **[!UICONTROL Edit link]** per visualizzare il contenuto del modello selezionato.

1. **Destinatari**

   I destinatari possono essere specificati dagli eventi in entrata, ad esempio dopo un’importazione di file, o specificati nell’azione di consegna. Possono anche essere memorizzati in uno o più file.

   ![](assets/diffusion_edit_5.png)

1. **Contenuto**

   Il contenuto del messaggio può essere definito nella consegna o nell’evento in entrata.

   ![](assets/diffusion_edit_6.png)

1. **Azione da eseguire**

   Puoi creare la consegna, prepararla, avviarla, stimare il target o inviare una bozza.

   ![](assets/diffusion_edit_7.png)

   Selezionare il tipo di azione da eseguire:

   * **[!UICONTROL Save]**: questa opzione ti consente di creare la consegna e salvarla. Non lo analizzerà né lo consegnerà.
   * **[!UICONTROL Estimate the target]**: questa opzione ti consente di calcolare il target di consegna per valutarne il potenziale (prima fase di analisi). Questa azione equivale a selezionare l’opzione **[!UICONTROL Estimate the population to be targeted]** e fare clic su **[!UICONTROL Analyze]** per inviare una consegna alla destinazione principale tramite **Consegna**.
   * **[!UICONTROL Prepare]**: questa opzione ti consente di eseguire l’intero processo di analisi (calcolo del target e preparazione del contenuto). La consegna non viene inviata. Questa azione equivale a selezionare l’opzione **[!UICONTROL Deliver as soon as possible]** e fare clic su **[!UICONTROL Analyze]** per inviare una consegna alla destinazione principale con **Consegna**.
   * **[!UICONTROL Send a proof]**: questa opzione ti consente di inviare una bozza della consegna. Questa azione equivale a fare clic sul pulsante **[!UICONTROL Send a proof]** nella barra degli strumenti di una consegna con **Consegna**
   * **[!UICONTROL Prepare and start]**: questa opzione avvia l’intero processo di analisi (calcolo di target e preparazione dei contenuti) e invia la consegna. Questa azione equivale a fare clic su **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** e **[!UICONTROL Confirm delivery]** quando si invia una consegna alla destinazione principale con **Consegna**.

   L’ attività **[!UICONTROL Act on a delivery]** utilizzata ulteriormente nel flusso di lavoro consente di avviare tutti i passaggi rimanenti necessari per avviare la consegna (calcolo di target, preparazione dei contenuti, consegna). Per ulteriori informazioni, consulta [Controllo della consegna](../../workflow/using/delivery-control.md).

   Sono disponibili anche le seguenti opzioni:

   * **[!UICONTROL Generate an outbound transition]**

      Crea una transizione in uscita che verrà attivata al termine dell’esecuzione. Puoi scegliere se recuperare o meno il target della consegna in uscita.

   * **[!UICONTROL Do not recover target]**

      Non recupera il target dell&#39;azione di consegna in uscita.

   * **[!UICONTROL Processing errors]**

      Fare riferimento a [Controllo consegna](../../workflow/using/delivery-control.md).
   La scheda **Script** ti consente di modificare i parametri di consegna.

   ![](assets/edit_diffusion_fil_script.png)

## Esempio: flusso di lavoro di consegna {#example--delivery-workflow}

Crea un nuovo flusso di lavoro e aggiungi attività come mostrato nell’immagine seguente:

![](assets/new-workflow-5.png)

Apri l&#39;attività **Consegna** e definisci le proprietà come segue:

* Nella sezione **[!UICONTROL Delivery]** , seleziona **[!UICONTROL New, created from a template]** e seleziona un modello di consegna.
* Nella sezione **[!UICONTROL Recipients]**, seleziona **[!UICONTROL Specified in the delivery]**.
* Nella sezione **[!UICONTROL Action to execute]** , mantieni l&#39;opzione **[!UICONTROL Prepare]**.

![](assets/new-workflow-param-delivery.png)

Fare clic su **[!UICONTROL OK]** per chiudere la finestra delle proprietà. Hai appena configurato un’attività che consiste nella creazione e preparazione di una nuova consegna basata su un modello di consegna il cui target sarà specificato al suo interno.

Apri l&#39;attività **Approvazione** e definisci le proprietà come segue:

1. Nel campo **[!UICONTROL Assignment type]** , seleziona un gruppo in cui sei registrato. Se sei connesso utilizzando l&#39;account &quot;admin&quot;, seleziona il gruppo Amministrazione.
1. Quindi, inserisci un titolo e il seguente testo nel corpo del messaggio:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Questo è un messaggio che include un&#39;espressione scritta in JavaScript: **[!UICONTROL vars.recCount]** rappresenta il numero di destinatari interessati dalla consegna dell&#39;attività precedente. Per ulteriori informazioni sulle espressioni JavaScript, consulta [Script e modelli JavaScript](../../workflow/using/javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   L&#39;attività Approvazione è descritta in [Approvazione](../../workflow/using/approval.md).

## Parametri di input {#input-parameters}

Identificatore di consegna, se l&#39;opzione **[!UICONTROL Specified in the transition]** è selezionata nella sezione **[!UICONTROL Delivery]**.

* deliveryId
* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.

>[!NOTE]
>
>Questo parametro viene visualizzato solo se l&#39;opzione **[!UICONTROL Specified by inbound event(s)]** è selezionata nella sezione **[!UICONTROL Recipients]**.

* nomefile

   Nome completo del file generato se l’opzione **[!UICONTROL File(s) specified by inbound event(s)]** è selezionata nella sezione **[!UICONTROL Recipients]** .

* contentId

   Identificatore del contenuto se l&#39;opzione **[!UICONTROL Specified by inbound events]** è selezionata nella sezione **[!UICONTROL Content]**.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dalla consegna. **[!UICONTROL tableName]** è il nome della tabella che memorizza gli identificatori del target,  **[!UICONTROL schema]** è lo schema del gruppo (in genere nms:recipient) ed  **[!UICONTROL recCount]** è il numero di elementi della tabella.

La transizione associata al complemento ha gli stessi parametri.

>[!NOTE]
>
>Non sono presenti parametri di output quando si seleziona l’opzione **[!UICONTROL Do not recover target]** .
