---
product: campaign
title: Modificare i contenuti
description: Modificare i contenuti
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: 968430d6-b1dd-47f8-8b31-39aaa18bc05c
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1230'
ht-degree: 0%

---

# Modificare i contenuti{#editing-content}



## Definizione di una condizione di visibilità {#defining-a-visibility-condition}

Puoi specificare una condizione di visibilità in un elemento della pagina web: questo elemento sarà visibile solo se la condizione viene rispettata.

Per aggiungere una condizione di visibilità, selezionate un blocco e immettete la condizione nella **[!UICONTROL Visibility condition]** utilizzando l’editor di espressioni.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>La modifica avanzata delle espressioni viene presentata il [questa pagina](../../platform/using/defining-filter-conditions.md#list-of-functions).

![](assets/dce_popup_visibilitycondition.png)

Queste condizioni adottano la sintassi dell’espressione XTK (ad esempio **ctx.recipient.@email!= &quot;&quot;** o **ctx.recipient.@status==&quot;0&quot;**). Per impostazione predefinita, tutti i campi sono visibili.

>[!NOTE]
>
>Non è possibile modificare i blocchi dinamici non visibili, ad esempio i menu a discesa.

## Aggiunta di un bordo e uno sfondo {#adding-a-border-and-background}

Puoi aggiungere una **bordo** a un blocco selezionato. I bordi vengono definiti utilizzando tre opzioni: stile, dimensione e colore.

![](assets/dce_popup_border.png)

È inoltre possibile definire un **colore di sfondo** selezionando un colore dalla tabella colori.

![](assets/dce_popup_background.png)

## Modifica dei moduli {#editing-forms}

### Modifica delle proprietà dei dati per un modulo {#changing-the-data-properties-for-a-form}

Puoi collegare i campi del database con zone di input, pulsanti di scelta o blocchi di tipo casella di controllo.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>I campi predefiniti sono quelli dello schema di archiviazione dell&#39;applicazione Web.

Il **campo** zona di input consente di selezionare un campo di database da collegare a quello del modulo.

Per impostazione predefinita, i campi offerti sono quelli della **nms:destinatario** tabella.

![](assets/dce_field_selection.png)

Il **Campo obbligatorio** Questa opzione ti consente di autorizzare l’approvazione della pagina solo se l’utente ha compilato il campo. Se non viene compilato un campo obbligatorio, viene visualizzato un messaggio di errore.

Per i pulsanti di scelta e le caselle di controllo, **è necessaria una configurazione aggiuntiva**.

In effetti, se il modello utilizzato non contiene un valore per impostazione predefinita, devi completarlo nell’editor.

Per eseguire questa operazione:

* Fai clic su **[!UICONTROL Edit]** icona.

  ![](assets/dce_sidebar_options.png)

* Immetti il valore dell’elenco dettagliato (definito dal campo selezionato) in **[!UICONTROL Value]** campo.

  ![](assets/dce_sidebar_completeoptionradio.png)

### Modifica dei campi modulo {#modifying-form-fields}

Campi modulo come pulsanti di scelta, aree di input, elenchi a discesa e così via. possono essere modificati dalle rispettive barre degli strumenti.

Ciò significa che è possibile:

* Elimina il blocco contenente i campi modulo utilizzando **[!UICONTROL Delete]** icona.
* Duplica il campo selezionato creando un nuovo blocco utilizzando **[!UICONTROL Duplicate]** icona.
* Modifica il **[!UICONTROL Form data]** finestra per collegare un campo di database all&#39;area del modulo, utilizzando **[!UICONTROL Edit]** icona.

  ![](assets/dce_toolbar_formblock_edition.png)

## Aggiunta di un&#39;azione a un pulsante {#adding-an-action-to-a-button}

Quando l’utente fa clic su un pulsante, puoi definire un’azione associata. A questo scopo, seleziona l’azione da eseguire dall’elenco a discesa.

![](assets/dce_sidebar_button.png)

Le azioni disponibili sono le seguenti:

* **[!UICONTROL Refresh]** : aggiorna la pagina corrente.
* **[!UICONTROL Next page]** : crea un collegamento alla pagina successiva nell’applicazione Web.
* **[!UICONTROL Previous page]** : crea un collegamento alla pagina precedente nell’applicazione web.

>[!NOTE]
>
>Il **[!UICONTROL None]** consente di non attivare il pulsante.

Puoi modificare l’etichetta collegata al pulsante nel campo corrispondente.

## Aggiunta di un collegamento {#adding-a-link}

Puoi inserire un collegamento in qualsiasi elemento della pagina: immagine, parola, gruppo di parole, blocco di testo, ecc.

A questo scopo, seleziona l’elemento e utilizza la prima icona dal menu a comparsa.

![](assets/dce_insertlink_icon.png)

Questa icona ti consente di accedere a tutti i tipi di collegamenti disponibili.

![](assets/dce_insertlink_menu.png)

I blocchi e i campi di personalizzazione possono essere inseriti solo in blocchi di tipo Testo.

>[!NOTE]
>
>Per ogni tipo di collegamento, puoi configurare la modalità di apertura: seleziona la finestra di destinazione in **Target** elenco a discesa. Questo valore corrisponde al **`<target>`** HTML.
>
>L’elenco delle **target** è il seguente:
>
>* Altro (IFrame)
>* Finestra superiore (_top)
>* Finestra padre (_parent)
>* Nuova finestra (_blank)
>* Finestra corrente (_self)
>* Comportamento predefinito del browser
>

### Collegamento a un URL {#link-to-a-url}

Il **Collegamento a un URL esterno** consente di aprire qualsiasi URL dal contenuto sorgente.

![](assets/dce_toolbar_imgblock_externallink.png)

Inserisci l’indirizzo del collegamento in questione in **URL** campo. Il campo URL deve essere immesso come: **https://www.myURL.com**.

### Collegamento a un’applicazione web {#link-to-a-web-application}

Il **Collegamento a un’applicazione web** consente di accedere a un’applicazione web Adobe Campaign.

![](assets/dce_toolbar_imgblock_appweb.png)

Selezionare l&#39;applicazione Web dal campo corrispondente.

L&#39;elenco delle applicazioni Web suggerite corrisponde alle applicazioni disponibili nella **[!UICONTROL Resources > Online > Web Applications]** nodo.

### Collegamento a un’azione {#link-to-an-action}

Il **Collegamento che definisce un’azione** consente di configurare un’azione quando si fa clic su un elemento sorgente.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>Le azioni disponibili sono descritte in dettaglio nella [Aggiunta di un&#39;azione a un pulsante](#adding-an-action-to-a-button) sezione.

### Eliminare un collegamento {#delete-a-link}

Quando viene inserito un collegamento, la barra degli strumenti offre due nuove icone: **Modifica collegamento** e **Interrompi il collegamento** che ti consente di interagire con il collegamento creato.

* **[!UICONTROL Edit link]** consente di visualizzare una finestra con tutti i parametri del collegamento.
* **[!UICONTROL Break the link]** consente di eliminare, dopo la conferma, il collegamento e tutti i parametri correlati.

>[!NOTE]
>
>Se il collegamento viene eliminato, il contenuto viene comunque mantenuto.

## Modifica degli attributi dei caratteri {#changing-font-attributes}

Quando selezionate un elemento di testo, potete modificare gli attributi del carattere (stile, formato).

![](assets/dce_toolbar_txt.png)

Le opzioni disponibili sono le seguenti:

* **Ingrandisci font** icona: aumenta le dimensioni del testo selezionato (aggiungi `<span style="font size:">`)
* **Riduci font** icona: riduce le dimensioni del testo selezionato (aggiungi `<span style="font size:">`)
* **Bold** icona: applica il grassetto al testo selezionato (applica al testo il formato `<strong> </strong>` tag )
* **Corsivo** icona: rende il testo selezionato corsivo (applica al testo il formato  `<em> </em>` tag )
* **Sottolinea** icona: rende il testo selezionato sottolineato (applica al testo il formato `<span style="text-decoration: underline;">` tag )
* **Allinea a sinistra** icona: allinea il testo a sinistra del blocco selezionato (aggiungi style=&quot;text-align: left;&quot;)
* **Al centro** icona: centra il testo per il blocco selezionato (aggiungi style=&quot;text-align: center;&quot;)
* **Allinea a destra** icona: allinea il testo a destra del blocco selezionato (aggiungi style=&quot;text-align: right;&quot;)
* **Modificare il colore di sfondo** icona: consente di modificare il colore di sfondo per il blocco selezionato (aggiungi style=&quot;background-color: rgba(170, 86, 255, 0.87))
* **Cambia colore del testo** icona: consente di modificare il colore del testo del blocco selezionato o solo del testo selezionato (`<span style="color: #CODE">`)

>[!NOTE]
>
>* **Elimina** icona: elimina il blocco e tutto il relativo contenuto.
>
>* **Duplica** icona: duplica il blocco e tutti gli stili ad esso correlati.

## Gestione di immagini e animazioni {#managing-images-and-animations}

Digital Content Editor consente di lavorare su **qualsiasi tipo di immagine** compatibile con i browser.

>[!CAUTION]
>
>Non è necessario richiamare file esterni in un **script** della pagina HTML. Questi file non verranno importati sul server Adobe Campaign.

### Aggiunta/eliminazione/duplicazione di un’immagine {#adding---deleting---duplicating-an-image}

Per inserire un’immagine, seleziona un blocco di tipo Immagine e fai clic su **Immagine** icona.

![](assets/dce_insert_image.png)

Selezionare un file di immagine salvato localmente.

![](assets/dce_popup_imgupload.png)

Il **Elimina** elimina il tag contenente l&#39;immagine.

Il **Duplica** duplica il tag e il relativo contenuto.

>[!CAUTION]
>
>Quando si duplica un&#39;immagine, gli identificatori relativi alla nuova immagine vengono eliminati.

### Modifica delle proprietà dell’immagine {#editing-image-properties}

Quando selezioni un blocco contenente un’immagine, puoi accedere alle seguenti proprietà:

* **Didascalia** consente di definire la didascalia collegata all&#39;immagine (corrisponde alla **Alt** HTML).
* **Dimension** consente di specificare la dimensione dell’immagine, in pixel.

  ![](assets/dce_popup_imgsize.png)

## Aggiunta di contenuti di personalizzazione {#adding-personalization-content}

### Inserimento di un campo di personalizzazione {#inserting-a-personalization-field}

Il **Campo di personalizzazione** l’opzione per l’icona inserisci ti consente di aggiungere al contenuto un campo di database, ad esempio il nome del destinatario. Questa opzione è disponibile solo per i blocchi di testo.

![](assets/dce_toolbar_textblock_persofield.png)

Per impostazione predefinita, i campi offerti sono dal **[!UICONTROL Recipient]** tabella. Se necessario, modificare le proprietà dell&#39;applicazione Web per selezionare un&#39;altra tabella.

Il nome del campo viene visualizzato nell’editor ed evidenziato in giallo. Verrà sostituito dal profilo del destinatario di destinazione al momento della generazione della personalizzazione (ad esempio, quando si visualizza l’anteprima di una pagina di destinazione).

Un esempio è presentato nel [Inserimento di un campo di personalizzazione](creating-a-landing-page.md#inserting-a-personalization-field) sezione.

### Inserimento di un blocco di personalizzazione {#inserting-a-personalization-block}

Il **Blocco di personalizzazione** consente di inserire blocchi dinamici e personalizzati nel contenuto. Ad esempio, puoi aggiungere un logo o un messaggio di saluto. Non è disponibile per i blocchi di tipo Testo.

![](assets/dce_toolbar_textblock_persoblock.png)

Una volta inserito, il nome del blocco di personalizzazione viene visualizzato nell’editor ed evidenziato in giallo. Viene adattato automaticamente al profilo del destinatario quando viene generata la personalizzazione.

Per ulteriori informazioni sui blocchi di personalizzazione incorporati e su come definire blocchi di personalizzazione personalizzati, consulta [questa pagina](../../delivery/using/personalization-blocks.md).
