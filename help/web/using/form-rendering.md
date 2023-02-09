---
product: campaign
title: Rendering di un modulo
description: Rendering di un modulo
feature: Web Forms
exl-id: 723a6c47-5323-4914-a014-58be493852cc
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 2%

---

# Rendering di un modulo{#form-rendering}

![](../../assets/common.svg)

## Selezione del modello di rendering del modulo {#selecting-the-form-rendering-template}

Le impostazioni del modulo consentono di selezionare il modello utilizzato per generare le pagine. Per accedervi, fai clic sul pulsante **[!UICONTROL Properties]** nella barra degli strumenti dei dettagli del modulo e seleziona il pulsante **[!UICONTROL Rendering]** scheda . Per impostazione predefinita sono disponibili diversi modelli (fogli di stile).

![](assets/s_ncs_admin_survey_rendering_select.png)

La sezione inferiore dell’editor consente di visualizzare un rendering del modello selezionato.

La funzione di zoom consente di modificare il modello selezionato.

![](assets/s_ncs_admin_survey_render_edit.png)

È possibile modificare o sostituire questi modelli. A questo scopo, fai clic sul pulsante **[!UICONTROL Page layout...]** collega e personalizza le informazioni.

![](assets/s_ncs_admin_survey_render_edit_param.png)

È possibile eseguire le seguenti operazioni:

* Modificare l&#39;immagine utilizzata come logo e adattarne le dimensioni,
* Specifica anche il percorso per accedere all&#39;immagine di anteprima quando gli utenti selezionano questo modello di rendering.

La **[!UICONTROL Headers/Footers]** consente di modificare le informazioni visualizzate nelle intestazioni e nei piè di pagina di ogni pagina del modulo utilizzando questo modello.

![](assets/s_ncs_admin_survey_render_edit_header.png)

Ogni riga del **[!UICONTROL Page headers]** e **[!UICONTROL Page footers]** corrisponde a una riga nella pagina HTML. Fai clic su **[!UICONTROL Add]** per creare una nuova riga.

Seleziona una linea esistente e fai clic sul pulsante **[!UICONTROL Detail]** per personalizzarlo.

![](assets/s_ncs_admin_survey_render_edit_header_detail.png)

È possibile modificare il contenuto della riga, aggiungere bordi e modificare gli attributi dei font tramite le schede pertinenti. Fai clic su **[!UICONTROL OK]** per confermare queste modifiche.

La **[!UICONTROL Position]** I campi consentono di definire la posizione degli elementi nell’intestazione e nel piè di pagina.

![](assets/s_ncs_admin_survey_render_edit_header_position.png)

>[!NOTE]
>
>I modelli di rendering sono memorizzati nella **[!UICONTROL Administration > Configuration > Form rendering]** nodo.\
>Per ulteriori informazioni, consulta [Personalizzazione del rendering del modulo](#customizing-form-rendering)

## Personalizzazione del rendering del modulo {#customizing-form-rendering}

### Modifica del layout degli elementi {#changing-the-layout-of-elements}

È possibile sovraccaricare il foglio di stile per ciascun elemento del modulo (campi di input, immagini, pulsanti di scelta, ecc.).

Per eseguire questa operazione, utilizza la variabile **[!UICONTROL Advanced]** scheda .

![](assets/s_ncs_admin_survey_advanced_tab.png)

Consente di definire le seguenti proprietà:

* **[!UICONTROL Label position]**: vedere [Definizione della posizione delle etichette](defining-web-forms-layout.md#defining-the-position-of-labels),
* **[!UICONTROL Label format]**: Ritorno a capo o senza ritorno a capo,
* **[!UICONTROL Number of cells]** : vedere [Posizionamento dei campi nella pagina](defining-web-forms-layout.md#positioning-the-fields-on-the-page),
* **[!UICONTROL Horizontal alignment]** (A sinistra, A destra, Al centro) e **[!UICONTROL Vertical alignment]** (Alta, Bassa, Media),
* **[!UICONTROL Width]** della zona: può essere espresso in percentuale o in em, punti o pixel (valore predefinito),
* Massimo **[!UICONTROL Length]**: Numero massimo di caratteri consentiti (per i controlli di tipo Testo, Numero e Password),
* **[!UICONTROL Lines]**: numero di righe per un **[!UICONTROL Multi-line text]** zona del tipo,
* **[!UICONTROL Style inline]**: consente di sovraccaricare il foglio di stile CSS con impostazioni aggiuntive. Sono separati utilizzando **;** caratteri come mostrato nell’esempio seguente:

   ![](assets/s_ncs_admin_survey_advanced_tab_inline.png)

### Definizione di intestazioni e piè di pagina {#defining-headers-and-footers}

I campi vengono sequenziati in una struttura ad albero la cui radice ha lo stesso nome della pagina. Selezionala per modificare il nome.

Il titolo della finestra deve essere inserito nella **[!UICONTROL Page]** scheda della finestra delle proprietà del modulo. È inoltre possibile aggiungere un contenuto impostato all’intestazione e al piè di pagina della pagina (queste informazioni saranno visualizzate su ogni pagina). Questo contenuto viene immesso nelle sezioni corrispondenti del **[!UICONTROL Texts]** , come illustrato di seguito:

![](assets/s_ncs_admin_survey_titles_config.png)

### Aggiunta di elementi all’intestazione di HTML {#adding-elements-to-html-header}

È possibile inserire elementi aggiuntivi da inserire nell’intestazione HTML di una pagina del modulo. A questo scopo, immetti gli elementi nel **[!UICONTROL Header]** scheda della pagina pertinente.

Questo consente ad esempio di fare riferimento a un’icona che verrà visualizzata nella barra del titolo della pagina.

![](assets/webform_header_page_tab.png)

## Definizione delle impostazioni di controllo {#defining-control-settings}

Quando l’utente compila il modulo, su alcuni campi viene automaticamente eseguito un controllo a seconda del formato o della configurazione. Ciò ti consente di rendere obbligatori alcuni campi (consulta [Definizione dei campi obbligatori](#defining-mandatory-fields)) o controlla il formato dei dati immessi (consulta [Verifica del formato dei dati](#checking-data-format)). I controlli vengono eseguiti durante l’approvazione della pagina (facendo clic su un collegamento o un pulsante che abilita una transizione di output).

### Definizione dei campi obbligatori {#defining-mandatory-fields}

Per rendere obbligatori alcuni campi, seleziona questa opzione al momento della creazione del campo.

![](assets/s_ncs_admin_survey_required_field.png)

Se l’utente approva la pagina senza aver inserito il campo, viene visualizzato il seguente messaggio:

![](assets/s_ncs_admin_survey_required_default_msg.png)

Puoi personalizzare il messaggio facendo clic sul pulsante **[!UICONTROL Personalize this message]** link.

![](assets/s_ncs_admin_survey_required_custom_msg.png)

Se l’utente approva la pagina senza aver inserito il campo, viene visualizzato il seguente messaggio:

![](assets/s_ncs_admin_survey_required_custom_msg2.png)

### Verifica del formato dei dati {#checking-data-format}

Per i controlli del modulo i cui valori sono memorizzati in un campo esistente del database, verranno applicate le regole per il campo di archiviazione.

Per i controlli dei moduli i cui valori sono memorizzati in una variabile, le regole di approvazione dipendono dal formato della variabile.

Ad esempio, se crei una **[!UICONTROL Number]** controlla per memorizzare il numero client, come mostrato di seguito:

![](assets/s_ncs_admin_survey_choose_format.png)

L’utente deve immettere un numero intero nel campo modulo.

## Definizione della visualizzazione condizionale dei campi {#defining-fields-conditional-display}

È possibile configurare la visualizzazione dei campi nella pagina da visualizzare in base ai valori scelti dall’utente. Questo può essere applicato a un campo o a un gruppo di campi (quando sono raggruppati in un contenitore).

Per ogni elemento della pagina, il **[!UICONTROL Visibility]** consente di definire le condizioni di visualizzazione.

![](assets/s_ncs_admin_survey_condition_edit.png)

Le condizioni possono riguardare il valore dei campi o delle variabili del database.

Nella finestra di selezione del campo è possibile scegliere tra i seguenti dati:

![](assets/s_ncs_admin_survey_condition_select.png)

* La struttura ad albero principale contiene i parametri del contesto del modulo. I parametri predefiniti sono l’identificatore (che corrisponde all’identificatore crittografato del destinatario), la lingua e l’origine.

   Per ulteriori informazioni, consulta questa [pagina](defining-web-forms-properties.md#form-url-parameters).

* La **[!UICONTROL Recipients]** la sottostruttura contiene i campi di input inseriti nel modulo e memorizzati nel database.

   Per ulteriori informazioni, consulta [Memorizzazione dei dati nel database](web-forms-answers.md#storing-data-in-the-database).

* La **[!UICONTROL Variables]** nella sottostruttura sono contenute le variabili disponibili per questo modulo. Per ulteriori informazioni, consulta [Memorizzazione di dati in una variabile locale](web-forms-answers.md#storing-data-in-a-local-variable).

Per ulteriori informazioni, consulta il caso d’uso disponibile qui: [Visualizzazione di opzioni diverse a seconda dei valori selezionati](use-cases--web-forms.md#displaying-different-options-depending-on-the-selected-values).

È inoltre possibile condizionare la visualizzazione delle pagine del modulo utilizzando la **[!UICONTROL Test]** oggetto. Per ulteriori informazioni, consulta questa [pagina](defining-web-forms-page-sequencing.md#conditional-page-display).

## Importazione di elementi da un modulo esistente {#importing-elements-from-an-existing-form}

È possibile importare campi o contenitori da altri moduli Web. Questo consente di creare una libreria di blocchi riutilizzabili che verranno inseriti nei moduli, ad esempio il blocco indirizzo, l’area di abbonamento alla newsletter e così via.

Per importare un elemento in un modulo, effettua le seguenti operazioni:

1. Modifica la pagina in cui desideri inserire uno o più elementi, quindi fai clic su **[!UICONTROL Import an existing block]** nella barra degli strumenti.

   ![](assets/s_ncs_admin_survey_import_block.png)

1. Selezionare il modulo Web contenente i campi da importare e scegliere i contenitori e i campi da importare.

   ![](assets/s_ncs_admin_survey_import_block_selection.png)

   >[!NOTE]
   >
   >La **[!UICONTROL Edit link]** L’icona a destra del nome del modulo di origine consente di visualizzare il modulo Web selezionato.

1. Fai clic su **[!UICONTROL Ok]** per confermare l&#39;inserimento.

   ![](assets/s_ncs_admin_survey_import_block_rendering.png)
