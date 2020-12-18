---
solution: Campaign Classic
product: campaign
title: Rendering di un modulo
description: Rendering di un modulo
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---


# Rendering di un modulo{#form-rendering}

## Selezione del modello di rendering del modulo {#selecting-the-form-rendering-template}

Le impostazioni del modulo consentono di selezionare il modello utilizzato per generare le pagine. Per accedervi, fare clic sul pulsante **[!UICONTROL Settings]** nella barra degli strumenti dei dettagli del modulo, quindi selezionare la scheda **[!UICONTROL Rendering]**. Per impostazione predefinita sono disponibili diversi modelli (fogli di stile).

![](assets/s_ncs_admin_survey_rendering_select.png)

La sezione inferiore dell’editor consente di visualizzare un rendering del modello selezionato.

La funzione di zoom consente di modificare il modello selezionato.

![](assets/s_ncs_admin_survey_render_edit.png)

Potete modificare o ignorare questi modelli. A tal fine, fate clic sul collegamento **[!UICONTROL Page layout...]** e personalizzate le informazioni.

![](assets/s_ncs_admin_survey_render_edit_param.png)

Puoi:

* Modificate l’immagine usata come logo e adattatene le dimensioni,
* Specificate inoltre il percorso per accedere all&#39;immagine di anteprima quando gli utenti selezionano questo modello di rendering.

La scheda **[!UICONTROL Headers/Footers]** consente di modificare le informazioni visualizzate nelle intestazioni e nei piè di pagina di ciascuna pagina del modulo utilizzando questo modello.

![](assets/s_ncs_admin_survey_render_edit_header.png)

Ogni riga della sezione **[!UICONTROL Page headers]** e **[!UICONTROL Page footers]** corrisponde a una riga nella pagina HTML. Fare clic su **[!UICONTROL Add]** per creare una nuova riga.

Selezionate una riga esistente e fate clic sul pulsante **[!UICONTROL Detail]** per personalizzarla.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

È possibile modificare il contenuto della riga, aggiungere bordi e modificare gli attributi dei font tramite le relative schede. Fare clic su **[!UICONTROL OK]** per confermare le modifiche.

I campi **[!UICONTROL Position]** consentono di definire la posizione degli elementi nell&#39;intestazione e nel piè di pagina della pagina.

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>I modelli di rendering sono memorizzati nel nodo **[!UICONTROL Administration > Configuration > Form rendering]**.\
>Per ulteriori informazioni, vedere [Personalizzazione del rendering del modulo](#customizing-form-rendering)

## Personalizzazione del rendering del modulo {#customizing-form-rendering}

### Modifica del layout degli elementi {#changing-the-layout-of-elements}

È possibile sovraccaricare il foglio di stile per ciascun elemento del modulo (campi di input, immagini, pulsanti di scelta, ecc.).

A tal fine, utilizzare la scheda **[!UICONTROL Advanced]**.

![](assets/s_ncs_admin_survey_advanced_tab.png)

Consente di definire le seguenti proprietà:

* **[!UICONTROL Label position]**: vedere  [Definizione della posizione delle etichette](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**: ritorno a capo automatico o senza ritorno a capo automatico,
* **[!UICONTROL Number of cells]** : vedere  [Posizionamento dei campi sulla pagina](../../web/using/defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** (A sinistra, A destra, Al centro) e  **[!UICONTROL Vertical alignment]** (Alto, Basso, Centro),
* **[!UICONTROL Width]** della zona: può essere espresso come percentuale o in em, punti o pixel (valore predefinito),
* Massimo **[!UICONTROL Length]**: Numero massimo di caratteri consentiti (per i controlli di tipo Testo, Numero e Password),
* **[!UICONTROL Lines]**: numero di righe per una zona  **[!UICONTROL Multi-line text]** tipo,
* **[!UICONTROL Style inline]**: consente di sovraccaricare il foglio di stile CSS con impostazioni aggiuntive. Queste sono separate utilizzando i caratteri **;** come illustrato nell&#39;esempio seguente:

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### Definizione di intestazioni e piè di pagina {#defining-headers-and-footers}

I campi sono ordinati in sequenza in una struttura ad albero con il nome della radice uguale a quello della pagina. Selezionatela per modificare il nome.

Il titolo della finestra deve essere immesso nella scheda **[!UICONTROL Page]** della finestra delle proprietà del modulo. È inoltre possibile aggiungere un set di contenuti all’intestazione e al piè di pagina della pagina (queste informazioni verranno visualizzate su ogni pagina). Il contenuto viene immesso nelle sezioni corrispondenti della scheda **[!UICONTROL Texts]**, come illustrato di seguito:

![](assets/s_ncs_admin_survey_titles_config.png)

### Aggiunta di elementi all&#39;intestazione HTML {#adding-elements-to-html-header}

È possibile inserire elementi aggiuntivi da inserire nell&#39;intestazione HTML di una pagina del modulo. A tal fine, immettete gli elementi nella scheda **[!UICONTROL Header]** della pagina corrispondente.

Questo consente di fare riferimento a un&#39;icona che verrà visualizzata, ad esempio, nella barra del titolo della pagina.

![](assets/webform_header_page_tab.png)

## Definizione delle impostazioni di controllo {#defining-control-settings}

Quando l&#39;utente compila il modulo, viene automaticamente effettuato un controllo su alcuni campi, a seconda del formato o della configurazione. Questo consente di rendere obbligatori alcuni campi (fare riferimento a [Definizione di campi obbligatori](#defining-mandatory-fields)) o di controllare il formato dei dati immessi (fare riferimento a [Controllo del formato dei dati](#checking-data-format)). I controlli vengono eseguiti durante l&#39;approvazione della pagina (facendo clic su un collegamento o un pulsante che consente una transizione di output).

### Definizione di campi obbligatori {#defining-mandatory-fields}

Per rendere obbligatori alcuni campi, selezionare questa opzione al momento della creazione del campo.

![](assets/s_ncs_admin_survey_required_field.png)

Se l&#39;utente approva la pagina senza aver inserito il campo, verrà visualizzato il seguente messaggio:

![](assets/s_ncs_admin_survey_required_default_msg.png)

Puoi personalizzare il messaggio facendo clic sul collegamento **[!UICONTROL Personalize this message]**.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

Se l&#39;utente approva la pagina senza aver inserito il campo, verrà visualizzato il seguente messaggio:

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### Verifica del formato dei dati {#checking-data-format}

Per i controlli modulo i cui valori sono memorizzati in un campo esistente del database, verranno applicate le regole per il campo di memorizzazione.

Per i controlli modulo i cui valori sono memorizzati in una variabile, le regole di approvazione dipendono dal formato della variabile.

Ad esempio, se create un controllo **[!UICONTROL Number]** per memorizzare il numero client, come illustrato di seguito:

![](assets/s_ncs_admin_survey_choose_format.png)

L&#39;utente deve immettere un numero intero nel campo modulo.

## Definizione della visualizzazione condizionale dei campi {#defining-fields-conditional-display}

È possibile configurare la visualizzazione dei campi sulla pagina da visualizzare in base ai valori scelti dall&#39;utente. Questo può essere applicato a un campo o a un gruppo di campi (quando sono raggruppati in un contenitore).

Per ciascun elemento della pagina, la sezione **[!UICONTROL Visibility]** consente di definire le condizioni di visualizzazione.

![](assets/s_ncs_admin_survey_condition_edit.png)

Le condizioni possono riguardare il valore dei campi del database o delle variabili.

Nella finestra di selezione del campo è possibile scegliere tra i dati seguenti:

![](assets/s_ncs_admin_survey_condition_select.png)

* La struttura ad albero principale contiene i parametri del contesto del modulo. I parametri predefiniti sono l&#39;Identificatore (che corrisponde all&#39;identificatore crittografato del destinatario), la Lingua e l&#39;Origine.

   Per ulteriori informazioni, consulta questa [pagina](../../web/using/defining-web-forms-properties.md#form-url-parameters).

* La sottostruttura **[!UICONTROL Recipients]** contiene i campi di input inseriti nel modulo e memorizzati nel database.

   Per ulteriori informazioni, vedere [Memorizzazione dei dati nel database](../../web/using/web-forms-answers.md#storing-data-in-the-database).

* La sottostruttura **[!UICONTROL Variables]** contiene le variabili disponibili per questo modulo. Per ulteriori informazioni, vedere [Memorizzazione dei dati in una variabile locale](../../web/using/web-forms-answers.md#storing-data-in-a-local-variable).

Per ulteriori informazioni, consulta il caso d’uso qui: [Visualizzazione di opzioni diverse a seconda dei valori selezionati](../../web/using/use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values).

È inoltre possibile condizionare la visualizzazione delle pagine del modulo utilizzando l&#39;oggetto **[!UICONTROL Test]**. Per ulteriori informazioni, consulta questa [pagina](../../web/using/defining-web-forms-page-sequencing.md#conditional-page-display).

## Importazione di elementi da un modulo esistente {#importing-elements-from-an-existing-form}

È possibile importare campi o contenitori da altri moduli Web. Questo consente di creare una libreria di blocchi riutilizzabili che verranno inseriti nei moduli, ad esempio il blocco indirizzo, l&#39;area di iscrizione alla newsletter e così via.

Per importare un elemento in un modulo, procedere come segue:

1. Modificate la pagina in cui desiderate inserire uno o più elementi, quindi fate clic su **[!UICONTROL Import an existing block]** nella barra degli strumenti.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. Selezionare il modulo Web che contiene i campi da importare e scegliere i contenitori e i campi da importare.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >L&#39;icona **[!UICONTROL Edit link]** a destra del nome del modulo di origine consente di visualizzare il modulo Web selezionato.

1. Fare clic su **[!UICONTROL Ok]** per confermare l&#39;inserimento.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)

