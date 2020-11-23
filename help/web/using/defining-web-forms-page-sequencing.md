---
solution: Campaign Classic
product: campaign
title: Definizione della sequenza di pagine dei moduli web
description: Definizione della sequenza di pagine dei moduli web
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 2%

---


# Definizione della sequenza di pagine dei moduli web{#defining-web-forms-page-sequencing}

Il modulo può contenere una o più pagine. È costruito tramite un diagramma che consente di sequenziare pagine e test, esecuzione di script e fasi di registrazione di salto di pagina. La modalità di costruzione del diagramma è la stessa di un flusso di lavoro.

## La pagina precedente e la pagina successiva {#about-previous-page-and-next-page}

Per ogni pagina, è possibile eliminare i **[!UICONTROL Next]** pulsanti o **[!UICONTROL Previous]** . A questo scopo, selezionate la pagina in questione e selezionate l’opzione **[!UICONTROL Disable next page]** o **[!UICONTROL Disallow returning to the previous page]** .

![](assets/s_ncs_admin_survey_no_next_page.png)

È possibile sostituire questi pulsanti con collegamenti. Consultate [Inserimento di contenuto](../../web/using/static-elements-in-a-web-form.md#inserting-html-content)HTML.

## Inserimento di un salto {#inserting-a-jump}

L&#39; **[!UICONTROL Jump]** oggetto consente di accedere a un&#39;altra pagina o a un altro modulo quando l&#39;utente fa clic su di esso **[!UICONTROL Next]**.

La destinazione può essere:

* Un&#39;altra pagina del modulo. A questo scopo, selezionate **[!UICONTROL Internal activity]** e specificate la pagina desiderata, come segue:

   ![](assets/s_ncs_admin_jump_param1.png)

* Un altro modulo. A questo scopo, selezionare l&#39; **[!UICONTROL Explicit]** opzione e specificare il modulo di destinazione.

   ![](assets/s_ncs_admin_jump_param2.png)

* La destinazione può essere memorizzata in una variabile. In questo caso, selezionatelo dall&#39;elenco a discesa, come mostrato di seguito:

   ![](assets/s_ncs_admin_jump_param3.png)

* La **[!UICONTROL Comment]** scheda consente di immettere informazioni che saranno visibili dall&#39;operatore quando l&#39;operatore fa clic sull&#39;oggetto nel diagramma.

   ![](assets/s_ncs_admin_survey_jump_comment.png)

## Esempio: accesso a un altro modulo in base a un parametro dell&#39;URL {#example--accessing-another-form-according-to-a-parameter-of-the-url}

Nell&#39;esempio seguente, si desidera configurare un modulo Web che, una volta approvato, visualizzerà un altro modulo designato da un parametro dell&#39;URL. A questo scopo, eseguire i seguenti passaggi:

1. Inserire un salto alla fine di un modulo: sostituisce la **[!UICONTROL End]** casella.

   ![](assets/s_ncs_admin_survey_jump_sample1.png)

1. Nelle proprietà del modulo, aggiungere un parametro (**successivo**) memorizzato in una variabile locale (**successivo**). Le variabili locali sono descritte in [Memorizzazione dei dati in una variabile](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable)locale.

   ![](assets/s_ncs_admin_survey_jump_sample2.png)

1. Modificate l&#39; **[!UICONTROL Jump]** oggetto, selezionate l&#39; **[!UICONTROL Stored in a variable]** opzione e selezionate la variabile **successiva** dalla casella a discesa.

   ![](assets/s_ncs_admin_survey_jump_sample3.png)

1. L&#39;URL di consegna deve includere il nome interno del modulo di destinazione, ad esempio:

   ```
   https://[myserver]/webForm/APP62?&next=APP22
   ```

   Quando l&#39;utente fa clic sul **[!UICONTROL Approve]** pulsante, viene visualizzato il modulo **APP22** .

## Inserimento di un collegamento a un’altra pagina del modulo {#inserting-a-link-to-another-page-of-the-form}

È possibile inserire collegamenti ad altre pagine del modulo. A questo scopo, aggiungete alla pagina un elemento statico **[!UICONTROL Link]** tipo. Per ulteriori informazioni, consulta [Inserimento di un collegamento](../../web/using/static-elements-in-a-web-form.md#inserting-a-link).

## Visualizzazione della pagina condizionale {#conditional-page-display}

### Visualizzazione in base alle risposte {#display-based-on-responses}

La **[!UICONTROL Test]** casella consente di condizionare la sequenza delle pagine di un modulo. Consente di definire varie linee di ramo in base ai risultati del test. Questo consente di visualizzare pagine diverse a seconda delle risposte fornite dagli utenti.

Ad esempio, potete visualizzare una pagina diversa per i clienti che hanno già effettuato l’ordine online e un’altra per coloro che hanno effettuato più di dieci ordini. A questo scopo, nella prima pagina del modulo inserire un campo di immissione **[!UICONTROL Number]** tipo in cui l&#39;utente può indicare il numero di ordini inseriti.

![](assets/s_ncs_admin_survey_test_ex0.png)

È possibile memorizzare queste informazioni in un campo del database o utilizzare una variabile locale.

>[!NOTE]
>
>Le modalità di memorizzazione sono dettagliate nei campi [di memorizzazione](../../web/using/web-forms-answers.md#response-storage-fields)Risposta.

Nel nostro esempio, vogliamo usare una variabile:

![](assets/s_ncs_admin_survey_test_ex1.png)

Nel diagramma del modulo, inserire una casella di prova per definire le condizioni. Per ogni condizione, verrà aggiunto un nuovo ramo all&#39;uscita della casella di prova.

![](assets/s_ncs_admin_survey_test_ex2.png)

Selezionate l’ **[!UICONTROL Activate the default branching]** opzione per aggiungere una transizione per i casi in cui nessuna delle condizioni è vera. Questa opzione non è necessaria se ogni possibile caso è coperto dalle condizioni definite.

Quindi, definite la sequenza delle pagine quando una delle condizioni è vera, ad esempio:

![](assets/s_ncs_admin_survey_test_ex3.png)

### Visualizzazione in base ai parametri {#display-based-on-parameters}

È inoltre possibile personalizzare la sequenza delle pagine in base ai parametri di inizializzazione del modulo Web o ai valori memorizzati nel database. Consultate Parametri [URL](../../web/using/defining-web-forms-properties.md#form-url-parameters)modulo.

## Aggiunta di script {#adding-scripts}

L&#39; **[!UICONTROL Script]** oggetto consente di immettere direttamente uno script JavaScript, ad esempio per modificare il valore di un campo, recuperare dati dal database o chiamare un&#39;API Adobe Campaign .

## Personalizzazione della pagina finale {#personalizing-the-end-page}

Posizionare una pagina finale alla fine del diagramma. La pagina finale viene visualizzata quando l&#39;utente fa clic sul **[!UICONTROL Approve]** pulsante nel modulo Web.

Per personalizzare questa pagina, fate doppio clic **[!UICONTROL End]** e immettete il contenuto della pagina nell’editor centrale.

![](assets/s_ncs_admin_survey_end_page_edit.png)

* Potete copiare e incollare contenuto HTML esistente. A questo scopo, fate clic **[!UICONTROL Display source code]** e inserite il codice HTML.
* Potete usare un URL esterno; a questo scopo, selezionate l’opzione corrispondente e immettete l’URL della pagina da visualizzare.

