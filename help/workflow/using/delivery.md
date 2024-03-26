---
product: campaign
title: Consegna
description: Ulteriori informazioni sull’attività del flusso di lavoro di tipo Consegna
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Channels Activity
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 2%

---

# Consegna{#delivery}



A **Consegna** L’attività -type ti consente di creare un’azione di consegna. Può essere realizzata utilizzando elementi di input.

Per configurarlo, modifica l’attività e immetti le opzioni di consegna.

![](assets/edit_diffusion.png)

1. **Consegna**

   Puoi eseguire le seguenti azioni:

   * Agisci sulla consegna specificata nella transizione in entrata. A questo scopo, seleziona la prima opzione della **[!UICONTROL Delivery]** sezione della finestra.

     Questa opzione può essere utilizzata quando una precedente attività del flusso di lavoro ha già creato o specificato la consegna. Ciò può essere stato fatto, come nell’esempio seguente, da un’attività dello stesso tipo che ha generato una transizione in uscita.

     Nell’esempio seguente, la consegna viene creata per la prima volta. La popolazione e il contenuto vengono definiti in un secondo momento. Successivamente, le informazioni per questi tre elementi vengono reinserite in una nuova attività di consegna utilizzando la transizione in entrata in modo che possa essere inviata.

     ![](assets/specified_transition_option_exemple.png)

   * Seleziona direttamente la consegna interessata. A questo scopo, seleziona la **[!UICONTROL Explicit]** e seleziona la consegna dall’elenco a discesa del **[!UICONTROL Delivery]** campo.

     L’elenco mostra le consegne non completate contenute in **Consegne** cartella per impostazione predefinita. Per accedere ad altre campagne, fai clic su **[!UICONTROL Select link]** icona.

     ![](assets/diffusion_edit_1.png)

     Seleziona la campagna dall’elenco a discesa della **[!UICONTROL Folder]** o fai clic su **[!UICONTROL Display sub-levels]** per visualizzare tutte le consegne contenute nelle sottocartelle:

     ![](assets/diffusion_edit_2.png)

     Dopo aver selezionato l’azione di consegna, puoi visualizzare il contenuto facendo clic sulla **[!UICONTROL Edit link]** icona.

   * Crea uno script per calcolare la consegna. A questo scopo, seleziona la **[!UICONTROL Computed by a script]** e immettere lo script. È possibile aprire una finestra di input facendo clic sul pulsante **[!UICONTROL Edit...]** opzione. L’esempio seguente recupera l’identificatore della consegna:

     ![](assets/diffusion_edit_3.png)

   * Crea una nuova consegna. A questo scopo, seleziona la **[!UICONTROL New, created from a template]** e seleziona il modello di consegna su cui basare la consegna.

     ![](assets/diffusion_edit_4.png)

     Fai clic su **[!UICONTROL Select link]** per sfogliare le cartelle e fare clic su **[!UICONTROL Edit link]** se desideri visualizzare il contenuto del modello selezionato.

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

   * **[!UICONTROL Save]**: questa opzione ti consente di creare la consegna e salvarla. Non lo analizzerà né lo consegnerà.
   * **[!UICONTROL Estimate the target]**: questa opzione ti consente di calcolare il target di consegna per valutarne il potenziale (prima fase di analisi). Questa azione equivale a selezionare **[!UICONTROL Estimate the population to be targeted]** opzione e clic **[!UICONTROL Analyze]** quando si invia una consegna al target principale tramite **Consegna**.
   * **[!UICONTROL Prepare]**: questa opzione consente di eseguire l’intero processo di analisi (calcolo del target e preparazione del contenuto). La consegna non viene inviata. Questa azione equivale a selezionare **[!UICONTROL Deliver as soon as possible]** opzione e clic **[!UICONTROL Analyze]** quando si invia una consegna al target principale con **Consegna**.
   * **[!UICONTROL Send a proof]**: questa opzione ti consente di inviare una prova della consegna. Questa azione equivale a fare clic su **[!UICONTROL Send a proof]** nella barra degli strumenti di una consegna con **Consegna**
   * **[!UICONTROL Prepare and start]**: questa opzione avvia l’intero processo di analisi (calcolo del target e preparazione dei contenuti) e invia la consegna. Questa azione equivale a fare clic su **[!UICONTROL Deliver as soon as possible]**, **[!UICONTROL Analyze]**, e **[!UICONTROL Confirm delivery]** opzione durante l’invio di una consegna al target principale con **Consegna**.

   Il **[!UICONTROL Act on a delivery]** l’attività utilizzata ulteriormente nel flusso di lavoro ti consente di avviare tutti i passaggi rimanenti necessari per avviare la consegna (calcolo del target, preparazione dei contenuti, consegna). Per ulteriori informazioni, consulta [Controllo della consegna](delivery-control.md).

   Sono inoltre disponibili le seguenti opzioni:

   * **[!UICONTROL Generate an outbound transition]**

     Crea una transizione in uscita che verrà attivata alla fine dell’esecuzione. Puoi scegliere se recuperare o meno la destinazione della consegna in uscita.

   * **[!UICONTROL Do not recover target]**

     Non recupera il target dell’azione di consegna in uscita.

   * **[!UICONTROL Processing errors]**

     Fai riferimento a [Controllo della consegna](delivery-control.md).

   Il **Script** Questa scheda ti consente di modificare i parametri di consegna.

   ![](assets/edit_diffusion_fil_script.png)

## Esempio: flusso di lavoro di consegna {#example--delivery-workflow}

Crea un nuovo flusso di lavoro e aggiungi le attività come mostrato nell’immagine seguente:

![](assets/new-workflow-5.png)

Apri **Consegna** e definisci le proprietà come segue:

* In **[!UICONTROL Delivery]** sezione, seleziona **[!UICONTROL New, created from a template]** e seleziona un modello di consegna.
* In **[!UICONTROL Recipients]** sezione, seleziona **[!UICONTROL Specified in the delivery]**.
* In **[!UICONTROL Action to execute]** sezione, mantieni **[!UICONTROL Prepare]** opzione.

![](assets/new-workflow-param-delivery.png)

Clic **[!UICONTROL OK]** per chiudere la finestra proprietà. Hai appena configurato un’attività che consiste nella creazione e preparazione di una nuova consegna basata su un modello di consegna il cui target verrà specificato al suo interno.

Apri **Approvazione** e definisci le proprietà come segue:

1. In **[!UICONTROL Assignment type]** selezionare un gruppo in cui si è registrati. Se si è connessi utilizzando l&#39;account &#39;admin&#39;, selezionare il gruppo Amministrazione.
1. Quindi, inserisci un titolo e il testo seguente nel corpo del messaggio:

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   Questo è un messaggio che include un’espressione scritta in JavaScript: **[!UICONTROL vars.recCount]** rappresenta il numero di destinatari interessati dalla consegna dell’attività precedente. Per ulteriori informazioni sulle espressioni JavaScript, consulta [Script e modelli JavaScript](javascript-scripts-and-templates.md).

   ![](assets/new-workflow-param-validation.png)

   L’attività Approvazione è descritta in [Approvazione](approval.md).

## Parametri di input {#input-parameters}

Identificatore della consegna, se **[!UICONTROL Specified in the transition]** è selezionata in **[!UICONTROL Delivery]** sezione.

* deliveryId
* tableName
* schema

Ogni evento in entrata deve specificare una destinazione definita da questi parametri.

>[!NOTE]
>
>Questo parametro viene visualizzato solo se **[!UICONTROL Specified by inbound event(s)]** è selezionata in **[!UICONTROL Recipients]** sezione.

* nome file

  Nome completo del file generato se **[!UICONTROL File(s) specified by inbound event(s)]** è selezionata in **[!UICONTROL Recipients]** sezione.

* contentId

  Identificatore del contenuto se **[!UICONTROL Specified by inbound events]** è selezionata in **[!UICONTROL Content]** sezione.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo set di tre valori identifica il target risultante dalla consegna. **[!UICONTROL tableName]** è il nome della tabella che memorizza gli identificatori del target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.

>[!NOTE]
>
>Non sono presenti parametri di output quando **[!UICONTROL Do not recover target]** è selezionata.
