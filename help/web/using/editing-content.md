---
product: campaign
title: Modificare i contenuti
description: Modificare i contenuti
feature: Web Apps, Web Forms, Landing Pages
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 1%

---

# Modificare i contenuti{#editing-content}

![](../../assets/common.svg)

## Definizione di una condizione di visibilità {#defining-a-visibility-condition}

Puoi specificare una condizione di visibilità su un elemento di pagina web: questo elemento sarà visibile solo se la condizione viene rispettata.

Per aggiungere una condizione di visibilità, seleziona un blocco e immetti la condizione nella **[!UICONTROL Visibility condition]** utilizzando l’editor di espressioni.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>La modifica avanzata delle espressioni è presentata il [questa pagina](../../platform/using/defining-filter-conditions.md#list-of-functions).

![](assets/dce_popup_visibilitycondition.png)

Queste condizioni adottano la sintassi dell&#39;espressione XTK (ad esempio **ctx.recipient.@e-mail != &quot;&quot;** o **ctx.recipient.@status==&quot;0&quot;**). Per impostazione predefinita, tutti i campi sono visibili.

>[!NOTE]
>
>Non è possibile modificare i blocchi dinamici non visibili, ad esempio i menu a discesa.

## Aggiunta di un bordo e uno sfondo {#adding-a-border-and-background}

Puoi aggiungere una **border** a un blocco selezionato. I bordi sono definiti utilizzando tre opzioni: stile, dimensione e colore.

![](assets/dce_popup_border.png)

Puoi anche definire un **colore di sfondo** selezionando un colore dalla tavola colori.

![](assets/dce_popup_background.png)

## Modifica dei moduli {#editing-forms}

### Modifica delle proprietà dei dati di un modulo {#changing-the-data-properties-for-a-form}

È possibile collegare i campi del database con aree di input, pulsanti di scelta o blocchi di tipo casella di controllo.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>I campi predefiniti sono quelli dello schema di archiviazione dell&#39;applicazione Web.

La **field** la zona di input consente di selezionare un campo del database da collegare al campo del modulo.

Per impostazione predefinita, i campi offerti sono quelli **nms:recipient** tabella.

![](assets/dce_field_selection.png)

La **Campo obbligatorio** consente di autorizzare l’approvazione della pagina solo se l’utente ha compilato il campo. Se non viene compilato un campo obbligatorio, viene visualizzato un messaggio di errore.

Per pulsanti di scelta e caselle di controllo, **è necessaria una configurazione aggiuntiva**.

Infatti, se il modello utilizzato non contiene un valore per impostazione predefinita, è necessario completarlo nell’editor.

Per eseguire questa operazione:

* Fai clic sul pulsante **[!UICONTROL Edit]** icona.

   ![](assets/dce_sidebar_options.png)

* Immetti il valore dell’elenco dettagliato (definito dal campo selezionato) nel campo **[!UICONTROL Value]** campo .

   ![](assets/dce_sidebar_completeoptionradio.png)

### Modifica dei campi modulo {#modifying-form-fields}

Campi modulo quali pulsanti di scelta, aree di input, elenchi a discesa, ecc. possono essere modificate dalle relative barre degli strumenti.

Ciò significa che puoi:

* Elimina il blocco contenente i campi del modulo utilizzando **[!UICONTROL Delete]** icona.
* Duplica il campo selezionato creando un nuovo blocco utilizzando la **[!UICONTROL Duplicate]** icona.
* Modifica le **[!UICONTROL Form data]** per collegare un campo di database alla zona del modulo, utilizzando **[!UICONTROL Edit]** icona.

   ![](assets/dce_toolbar_formblock_edition.png)

## Aggiunta di un’azione a un pulsante {#adding-an-action-to-a-button}

Quando l’utente fa clic su un pulsante, è possibile definire un’azione associata. A questo scopo, seleziona l’azione da eseguire dall’elenco a discesa.

![](assets/dce_sidebar_button.png)

Le azioni disponibili sono le seguenti:

* **[!UICONTROL Refresh]** : aggiorna la pagina corrente.
* **[!UICONTROL Next page]** : crea un collegamento alla pagina successiva nell&#39;applicazione Web.
* **[!UICONTROL Previous page]** : crea un collegamento alla pagina precedente nell&#39;applicazione Web.

>[!NOTE]
>
>La **[!UICONTROL None]** consente di non attivare il pulsante.

Puoi modificare l’etichetta collegata al pulsante nel campo corrispondente.

## Aggiunta di un collegamento {#adding-a-link}

Puoi inserire un collegamento in qualsiasi elemento di pagina: immagine, parola, gruppo di parole, blocco di testo, ecc.

A questo scopo, seleziona l’elemento e utilizza la prima icona dal menu a comparsa.

![](assets/dce_insertlink_icon.png)

Questa icona consente di accedere a tutti i tipi di collegamenti disponibili.

![](assets/dce_insertlink_menu.png)

I blocchi e i campi di personalizzazione possono essere inseriti solo nei blocchi di tipo Testo .

>[!NOTE]
>
>Per ogni tipo di collegamento, puoi configurare la modalità di apertura: seleziona la finestra di destinazione nel **Target** elenco a discesa. Questo valore corrisponde a **`<target>`** Tag HTML.
>
>Elenco dei **target** è il seguente:
>
>* Altro (IFrame)
>* Finestra superiore (_top)
>* Finestra padre (_parent)
>* Nuova finestra (_blank)
>* Finestra corrente (_self)
>* Comportamento del browser predefinito
>


### Collegamento a un URL {#link-to-a-url}

La **Collegamento a un URL esterno** consente di aprire qualsiasi URL dal contenuto sorgente.

![](assets/dce_toolbar_imgblock_externallink.png)

Inserisci l&#39;indirizzo di collegamento in questione nel **URL** campo . Il campo URL deve essere immesso come: **https://www.myURL.com**.

### Collegamento a un&#39;applicazione Web {#link-to-a-web-application}

La **Collegamento a un&#39;applicazione Web** consente di accedere a un&#39;applicazione Web Adobe Campaign.

![](assets/dce_toolbar_imgblock_appweb.png)

Selezionare l&#39;applicazione Web dal campo corrispondente.

L&#39;elenco delle applicazioni Web suggerite corrisponde alle applicazioni disponibili nel **[!UICONTROL Resources > Online > Web Applications]** nodo.

### Collegamento a un’azione {#link-to-an-action}

La **Collegamento che definisce un’azione** consente di configurare un’azione quando fai clic su un elemento sorgente.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>Le azioni disponibili sono descritte in dettaglio nella sezione [Aggiunta di un’azione a un pulsante](#adding-an-action-to-a-button) sezione .

### Eliminare un collegamento {#delete-a-link}

Quando è stato inserito un collegamento, la barra degli strumenti offre due nuove icone: **Modifica collegamento** e **Interruzione del collegamento** che consente di interagire con il collegamento creato.

* **[!UICONTROL Edit link]** consente di visualizzare una finestra con tutti i parametri del collegamento.
* **[!UICONTROL Break the link]** consente di eliminare, dopo la conferma, il collegamento e tutti i parametri correlati.

>[!NOTE]
>
>Se il collegamento viene eliminato, il contenuto viene comunque mantenuto.

## Modifica degli attributi del font {#changing-font-attributes}

Quando si seleziona un elemento di testo, è possibile modificare gli attributi del font (stile, formato).

![](assets/dce_toolbar_txt.png)

Le opzioni disponibili sono le seguenti:

* **Ingrandisci font** icona: aumenta le dimensioni del testo selezionato (aggiungi `<span style="font size:">`)
* **Riduci font** icona: riduce le dimensioni del testo selezionato (aggiungi `<span style="font size:">`)
* **Grassetto** icona: rende il testo selezionato in grassetto (applica il ritorno a capo automatico al testo) `<strong> </strong>` tag)
* **Corsivo** icona: rende il testo selezionato in corsivo (il testo viene racchiuso con il pulsante  `<em> </em>` tag)
* **Sottolineato** icona: rende sottolineato il testo selezionato (il testo viene racchiuso con `<span style="text-decoration: underline;">` tag)
* **Allinea a sinistra** icona: allinea il testo a sinistra del blocco selezionato (aggiungi style=&quot;text-align: sinistra;&quot;)
* **Centro** icona: centra il testo per il blocco selezionato (aggiungi style=&quot;text-align: centrale;&quot;)
* **Allinea a destra** icona: allinea il testo a destra del blocco selezionato (aggiungi style=&quot;text-align: a destra;&quot;)
* **Modificare il colore di sfondo** icona: consente di modificare il colore di sfondo del blocco selezionato (aggiungi style=&quot;background-color: rgba(170, 86, 255, 0.87))
* **Cambia colore del testo** icona: consente di modificare il colore del testo del blocco selezionato o solo del testo selezionato (`<span style="color: #CODE">`)

>[!NOTE]
>
>* **Elimina** icona: elimina il blocco e tutto il relativo contenuto.
>
>* **Duplica** icona: duplica il blocco e tutti gli stili correlati al blocco.


## Gestione di immagini e animazioni {#managing-images-and-animations}

L’editor dei contenuti digitali consente di lavorare su **qualsiasi tipo di immagine** compatibile con i browser.

>[!CAUTION]
>
>Non è necessario richiamare file esterni in un **script** tag della pagina HTML. Questi file non verranno importati sul server Adobe Campaign.

### Aggiunta/eliminazione/duplicazione di un’immagine {#adding---deleting---duplicating-an-image}

Per inserire un’immagine, seleziona un blocco di tipo Immagine e fai clic sul pulsante **Immagine** icona.

![](assets/dce_insert_image.png)

Selezionare un file immagine salvato localmente.

![](assets/dce_popup_imgupload.png)

La **Elimina** elimina la ![]() tag contenente l’immagine.

La **Duplica** l&#39;icona duplica ![]() e il relativo contenuto.

>[!CAUTION]
>
>Quando si duplica un’immagine, gli identificatori relativi alla nuova immagine vengono eliminati.

### Modifica delle proprietà immagine {#editing-image-properties}

Quando selezioni un blocco contenente un’immagine, accedi alle seguenti proprietà:

* **Didascalia** consente di definire la didascalia collegata all’immagine (corrisponde alla variabile **alt** (attributo HTML).
* **Dimension** consente di specificare la dimensione dell’immagine, in pixel.

   ![](assets/dce_popup_imgsize.png)

## Aggiunta di contenuto di personalizzazione {#adding-personalization-content}

### Inserimento di un campo di personalizzazione {#inserting-a-personalization-field}

La **Campo di personalizzazione** l’opzione per l’icona di inserimento consente di aggiungere al contenuto un campo di database, ad esempio il nome del destinatario. Questa opzione è disponibile solo per i blocchi di testo.

![](assets/dce_toolbar_textblock_persofield.png)

Per impostazione predefinita, i campi offerti sono **[!UICONTROL Recipient]** tabella. Se necessario, modificare le proprietà dell&#39;applicazione Web per selezionare un&#39;altra tabella.

Il nome del campo viene visualizzato nell’editor, evidenziato in giallo. Al momento della generazione della personalizzazione (ad esempio, durante l’anteprima di una pagina di destinazione), questa viene sostituita dal profilo del destinatario con targeting.

Un esempio è presentato nella [Inserimento di un campo di personalizzazione](creating-a-landing-page.md#inserting-a-personalization-field) sezione .

### Inserimento di un blocco di personalizzazione {#inserting-a-personalization-block}

La **Blocco di personalizzazione** consente di inserire blocchi dinamici e personalizzati nel contenuto. Ad esempio, puoi aggiungere un logo o un messaggio di saluto. Non è disponibile per i blocchi di tipo Testo .

![](assets/dce_toolbar_textblock_persoblock.png)

Una volta inserito, il nome del blocco di personalizzazione viene visualizzato nell’editor, evidenziato in giallo. Viene automaticamente adattato al profilo del destinatario quando viene generata la personalizzazione.

Per ulteriori informazioni sui blocchi di personalizzazione incorporati e su come definire blocchi di personalizzazione personalizzati, consulta [questa pagina](../../delivery/using/personalization-blocks.md).
