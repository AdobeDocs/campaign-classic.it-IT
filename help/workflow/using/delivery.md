---
product: campaign
title: Consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro di tipo Consegna
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# Consegna{#delivery}



A **Consegna** L’attività -type ti consente di creare un’azione di consegna. Può essere realizzata utilizzando elementi di input.

Per configurarlo, modifica l’attività e immetti le opzioni di consegna.

![](assets/edit_diffusion.png)

1. **Consegna**

   È possibile eseguire le seguenti operazioni:

   * Agisci sulla consegna specificata nella transizione in entrata. A questo scopo, seleziona la prima opzione del **[!UICONTROL Delivery]** della finestra.

      Questa opzione può essere utilizzata quando un’attività del flusso di lavoro precedente ha già creato o specificato la consegna. Questo può essere stato fatto, come nell’esempio seguente, da un’attività dello stesso tipo che ha generato una transizione in uscita.

      Nell’esempio seguente, la consegna viene creata per la prima volta. La popolazione e il contenuto vengono definiti successivamente. Successivamente, le informazioni per questi tre elementi vengono reinserite in una nuova attività di consegna utilizzando la transizione in entrata, in modo che possa essere inviata.

      ![](assets/specified_transition_option_exemple.png)

   * Selezionare direttamente la consegna interessata. A questo scopo, seleziona la **[!UICONTROL Explicit]** e seleziona la consegna dall’elenco a discesa del **[!UICONTROL Delivery]** campo .

      L’elenco mostra le consegne non completate contenute in **Consegne** per impostazione predefinita. Per accedere ad altre campagne, fai clic sul pulsante **[!UICONTROL Select link]** icona.

      ![](assets/diffusion_edit_1.png)

      Seleziona la campagna dall’elenco a discesa della **[!UICONTROL Folder]** o fai clic su **[!UICONTROL Display sub-levels]** per visualizzare tutte le consegne contenute nelle sottocartelle:

      ![](assets/diffusion_edit_2.png)

      Dopo aver selezionato l’azione di consegna, puoi visualizzare il contenuto facendo clic sul pulsante **[!UICONTROL Edit link]** icona.

   * Crea uno script per calcolare la consegna. A questo scopo, seleziona la **[!UICONTROL Computed by a script]** e immetti lo script. Per aprire una finestra di input, fai clic sul pulsante **[!UICONTROL Edit...]** opzione . L’esempio seguente recupera l’identificatore della consegna:

      ![](assets/diffusion_edit_3.png)

   * Crea una nuova consegna. A questo scopo, seleziona la **[!UICONTROL New, created from a template]** e seleziona il modello di consegna su cui verrà basata la consegna.

      ![](assets/diffusion_edit_4.png)

      Fai clic sul pulsante **[!UICONTROL Select link]** per sfogliare le cartelle e fare clic sul pulsante **[!UICONTROL Edit link]** per visualizzare il contenuto del modello selezionato.

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
   * **[!UICONTROL Estimate the target]**: questa opzione ti consente di calcolare il target di consegna per valutarne il potenziale (prima fase di analisi). Questa azione equivale a selezionare la **[!UICONTROL Estimate the population to be targeted]** opzione e clic **[!UICONTROL Analyze]** quando si invia una consegna al target principale tramite **Consegna**.
   * **[!UICONTROL Prepare]**: questa opzione ti consente di eseguire l’intero processo di analisi (calcolo del target e preparazione del contenuto). La consegna non viene inviata. Questa azione equivale a selezionare la **[!UICONTROL Deliver as soon as possible]** opzione e clic **[!UICONTROL Analyze]** quando si invia una consegna al target principale con **Consegna**.
   * **[!UICONTROL Send a proof]**: questa opzione ti consente di inviare una bozza della consegna. Equivale a fare clic sul pulsante **[!UICONTROL Send a proof]** nella barra degli strumenti di una consegna con **Consegna**
   * **[!UICONTROL Prepare and start]**: questa opzione avvia l’intero processo di analisi (calcolo di target e preparazione dei contenuti) e invia la consegna. Equivale a fare clic su **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]** e **[!UICONTROL Confirm delivery]** quando si invia una consegna al target principale con **Consegna**.

   La **[!UICONTROL Act on a delivery]** l’attività ulteriormente utilizzata nel flusso di lavoro ti consente di avviare tutti i passaggi rimanenti necessari per avviare la consegna (calcolo di target, preparazione dei contenuti, consegna). Per ulteriori informazioni, consulta [Controllo della consegna](delivery-control.md).

   Sono disponibili anche le seguenti opzioni:

   * **[!UICONTROL Generate an outbound transition]**

      Crea una transizione in uscita che verrà attivata al termine dell’esecuzione. Puoi scegliere se recuperare o meno il target della consegna in uscita.

   * **[!UICONTROL Do not recover target]**

      Non recupera il target dell&#39;azione di consegna in uscita.

   * **[!UICONTROL Processing errors]**

      Fai riferimento a [Controllo della consegna](delivery-control.md).
   La **Script** consente di modificare i parametri di consegna.

   ![](assets/edit_diffusion_fil_script.png)

## Esempio: flusso di lavoro di consegna {#example--delivery-workflow}

Crea un nuovo flusso di lavoro e aggiungi attività come mostrato nell’immagine seguente:

![](assets/new-workflow-5.png)

Apri **Consegna** e definisci le proprietà come segue:

* In **[!UICONTROL Delivery]** sezione , seleziona **[!UICONTROL New, created from a template]** e seleziona un modello di consegna.
* In **[!UICONTROL Recipients]** sezione , seleziona **[!UICONTROL Specified in the delivery]**.
* In **[!UICONTROL Action to execute]** sezione, mantenere **[!UICONTROL Prepare]** opzione .

![](assets/new-workflow-param-delivery.png)

Fai clic su **[!UICONTROL OK]** per chiudere la finestra delle proprietà. Hai appena configurato un’attività che consiste nella creazione e preparazione di una nuova consegna basata su un modello di consegna il cui target sarà specificato al suo interno.

Apri **Approvazione** e definisci le proprietà come segue:

1. In **[!UICONTROL Assignment type]** selezionare un gruppo in cui si è registrati. Se sei connesso utilizzando l&#39;account &quot;admin&quot;, seleziona il gruppo Amministrazione.
1. Quindi, inserisci un titolo e il seguente testo nel corpo del messaggio:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Questo è un messaggio che include un&#39;espressione scritta in JavaScript: **[!UICONTROL vars.recCount]** rappresenta il numero di destinatari interessati dalla consegna dell&#39;attività precedente. Per ulteriori informazioni sulle espressioni JavaScript, consulta [Script e modelli JavaScript](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   L&#39;attività Approvazione è descritta in [Approvazione](approval.md).

## Parametri di input {#input-parameters}

Identificatore di consegna, se **[!UICONTROL Specified in the transition]** è selezionata nella **[!UICONTROL Delivery]** sezione .

* deliveryId
* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.

>[!NOTE]
>
>Questo parametro viene visualizzato solo se la **[!UICONTROL Specified by inbound event(s)]** è selezionata nella **[!UICONTROL Recipients]** sezione .

* nomefile

   Nome completo del file generato se il **[!UICONTROL File(s) specified by inbound event(s)]** è selezionata nella **[!UICONTROL Recipients]** sezione .

* contentId

   Identificatore del contenuto se **[!UICONTROL Specified by inbound events]** è selezionata nella **[!UICONTROL Content]** sezione .

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dalla consegna. **[!UICONTROL tableName]** è il nome della tabella che memorizza gli identificatori del target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.

>[!NOTE]
>
>Non ci sono parametri di output quando la variabile **[!UICONTROL Do not recover target]** è selezionata.
