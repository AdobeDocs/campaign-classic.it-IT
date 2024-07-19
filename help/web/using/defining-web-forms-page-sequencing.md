---
product: campaign
title: Definire la sequenza di pagine dei moduli web
description: Definire la sequenza di pagine dei moduli web
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Forms
exl-id: c5b5c398-c13b-4ebe-88b2-8ff84741422e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 0%

---

# Definire la sequenza di pagine dei moduli web{#defining-web-forms-page-sequencing}



Il modulo può contenere una o più pagine. Viene creato tramite un diagramma che consente di sequenziare le pagine, testare, eseguire script, passare da una pagina all’altra e registrare i passaggi. La modalità di progettazione dei diagrammi globali è la stessa di un flusso di lavoro di Campaign.

## Informazioni sulla pagina precedente e su quella successiva {#about-previous-page-and-next-page}

Per ogni pagina è possibile eliminare i pulsanti **[!UICONTROL Next]** o **[!UICONTROL Previous]**. A tale scopo, selezionare la pagina interessata e selezionare l&#39;opzione **[!UICONTROL Disable next page]** o **[!UICONTROL Disallow returning to the previous page]**.

![](assets/s_ncs_admin_survey_no_next_page.png)

È possibile sostituire questi pulsanti con collegamenti. Vedere [Inserimento di contenuto HTML](static-elements-in-a-web-form.md#inserting-html-content).

## Inserimento di un salto {#inserting-a-jump}

L&#39;oggetto **[!UICONTROL Jump]** consente l&#39;accesso a un&#39;altra pagina o a un altro modulo quando l&#39;utente fa clic su **[!UICONTROL Next]**.

La destinazione può essere:

* Un&#39;altra pagina del modulo. A tale scopo, selezionare **[!UICONTROL Internal activity]** e quindi specificare la pagina desiderata, come indicato di seguito:

  ![](assets/s_ncs_admin_jump_param1.png)

* Un altro modulo. A tale scopo, selezionare l&#39;opzione **[!UICONTROL Explicit]** e specificare il modulo di destinazione.

  ![](assets/s_ncs_admin_jump_param2.png)

* La destinazione può essere memorizzata in una variabile. In questo caso, selezionalo dall’elenco a discesa, come illustrato di seguito:

  ![](assets/s_ncs_admin_jump_param3.png)

* La scheda **[!UICONTROL Comment]** consente di immettere informazioni che saranno visibili dall&#39;operatore quando farà clic sull&#39;oggetto nel diagramma.

  ![](assets/s_ncs_admin_survey_jump_comment.png)

## Esempio: accesso a un altro modulo in base a un parametro dell’URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

Nell’esempio seguente, vogliamo configurare un modulo web che, se approvato, visualizzerà un altro modulo designato da un parametro dell’URL. A questo scopo, esegui i seguenti passaggi:

1. Inserisce un salto alla fine di un modulo: sostituisce la casella **[!UICONTROL End]**.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. Nelle proprietà del modulo, aggiungi un parametro (**next**) memorizzato in una variabile locale (**next**). Le variabili locali sono descritte in dettaglio in [Memorizzazione dei dati in una variabile locale](web-forms-answers.md#storing-data-in-a-local-variable).

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Modifica l&#39;oggetto **[!UICONTROL Jump]**, seleziona l&#39;opzione **[!UICONTROL Stored in a variable]** e seleziona la variabile **next** dalla casella a discesa.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. L’URL di consegna deve includere il nome interno del modulo di destinazione, ad esempio:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   Quando l&#39;utente fa clic sul pulsante **[!UICONTROL Approve]**, viene visualizzato il modulo **APP22**.

## Inserimento di un collegamento a un&#39;altra pagina del modulo {#inserting-a-link-to-another-page-of-the-form}

È possibile inserire collegamenti ad altre pagine del modulo. Per eseguire questa operazione, aggiungere alla pagina un elemento statico di tipo **[!UICONTROL Link]**. Per ulteriori informazioni, consulta [Inserimento di un collegamento](static-elements-in-a-web-form.md#inserting-a-link).

## Visualizzazione pagina condizionale {#conditional-page-display}

### Visualizza in base alle risposte {#display-based-on-responses}

La casella **[!UICONTROL Test]** consente di condizionare la sequenza delle pagine in un modulo. Consente di definire varie linee di diramazione in base ai risultati del test. Questo consente di visualizzare pagine diverse a seconda delle risposte fornite dagli utenti.

Ad esempio, puoi visualizzare una pagina diversa per i clienti che hanno già effettuato un ordine online e un’altra per quelli che hanno effettuato più di dieci ordini. A tale scopo, nella prima pagina del modulo inserire un campo di input di tipo **[!UICONTROL Number]** in modo che l&#39;utente possa indicare il numero di ordini che ha effettuato.

![](assets/s_ncs_admin_survey_test_ex0.png)

È possibile memorizzare queste informazioni in un campo del database oppure utilizzare una variabile locale.

>[!NOTE]
>
>Le modalità di archiviazione sono descritte in dettaglio nei [campi di archiviazione delle risposte](web-forms-answers.md#response-storage-fields).

Nel nostro esempio, vogliamo utilizzare una variabile:

![](assets/s_ncs_admin_survey_test_ex1.png)

Nel diagramma del modulo inserire una casella di prova per definire le condizioni. Per ogni condizione, verrà aggiunto un nuovo ramo all’output della casella di test.

![](assets/s_ncs_admin_survey_test_ex2.png)

Selezionare l&#39;opzione **[!UICONTROL Activate the default branching]** per aggiungere una transizione per i casi in cui nessuna delle condizioni è vera. Questa opzione non è necessaria se le condizioni definite riguardano tutti i casi possibili.

Quindi, definisci la sequenza di pagine quando una delle due condizioni è vera, ad esempio:

![](assets/s_ncs_admin_survey_test_ex3.png)

### Visualizza in base ai parametri {#display-based-on-parameters}

È inoltre possibile personalizzare la sequenza di pagine in base ai parametri di inizializzazione del modulo Web o ai valori memorizzati nel database. Vedi [Parametri URL modulo](defining-web-forms-properties.md#form-url-parameters).

## Aggiunta di script {#adding-scripts}

L&#39;oggetto **[!UICONTROL Script]** consente di immettere direttamente uno script JavaScript, ad esempio per modificare il valore di un campo, recuperare dati dal database o chiamare un&#39;API Adobe Campaign.

## Personalizzazione della pagina finale {#personalizing-the-end-page}

Inserire una pagina finale alla fine del diagramma. La pagina finale viene visualizzata quando l&#39;utente fa clic sul pulsante **[!UICONTROL Approve]** nel modulo Web.

Per personalizzare la pagina, fare doppio clic su **[!UICONTROL End]** e immettere il contenuto della pagina nell&#39;editor centrale.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* Puoi copiare e incollare il contenuto HTML esistente. A tale scopo, fare clic su **[!UICONTROL Display source code]** e inserire il codice HTML.
* Puoi utilizzare un URL esterno; a questo scopo, seleziona l’opzione corrispondente e immetti l’URL della pagina da visualizzare.
