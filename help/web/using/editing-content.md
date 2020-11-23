---
solution: Campaign Classic
product: campaign
title: Modifica del contenuto
description: Modifica del contenuto
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1234'
ht-degree: 1%

---


# Modifica del contenuto{#editing-content}

## Definizione di una condizione di visibilità {#defining-a-visibility-condition}

Potete specificare una condizione di visibilità su un elemento di pagina Web: questo elemento sarà visibile solo se la condizione è rispettata.

Per aggiungere una condizione di visibilità, selezionare un blocco e immettere la condizione nel **[!UICONTROL Visibility condition]** campo utilizzando l&#39;editor di espressioni.

![](assets/dce_add_condition.png)

>[!NOTE]
>
>La modifica avanzata delle espressioni viene presentata in [questa pagina](../../platform/using/defining-filter-conditions.md#list-of-functions).

![](assets/dce_popup_visibilitycondition.png)

Queste condizioni adottano la sintassi dell&#39;espressione XTK (ad esempio, **ctx.Recipients).@email!= &quot;&quot;** o **ctx.Recipients.@status==&quot;0&quot;**). Per impostazione predefinita, tutti i campi sono visibili.

>[!NOTE]
>
>I blocchi dinamici non visibili, come i menu a discesa, non possono essere modificati.

## Aggiunta di un bordo e uno sfondo {#adding-a-border-and-background}

You can add a **border** to a selected block. I bordi sono definiti utilizzando tre opzioni: stile, dimensione e colore.

![](assets/dce_popup_border.png)

You can also define a **background color** by selecting a color from the color chart.

![](assets/dce_popup_background.png)

## Modifica dei moduli {#editing-forms}

### Modifica delle proprietà dei dati per un modulo {#changing-the-data-properties-for-a-form}

È possibile collegare i campi del database con aree di input, pulsanti di scelta o blocchi di tipo casella di controllo.

![](assets/dce_sidebar_field.png)

>[!NOTE]
>
>I campi predefiniti sono quelli dello schema di memorizzazione dell&#39;applicazione Web.

The **field** input zone lets you select a database field to link with the form field.

Per impostazione predefinita, i campi offerti sono quelli della tabella **nms:Recipients** .

![](assets/dce_field_selection.png)

The **Required field** option lets you only authorize the page&#39;s approval if the user has filled in the field. Se non viene compilato un campo obbligatorio, verrà visualizzato un messaggio di errore.

Per i pulsanti di scelta e le caselle di controllo, è necessaria **una configurazione** aggiuntiva.

Se il modello utilizzato non contiene un valore per impostazione predefinita, è necessario completarlo nell&#39;editor.

Per eseguire questa operazione:

* Fate clic sull&#39; **[!UICONTROL Edit]** icona.

   ![](assets/dce_sidebar_options.png)

* Immettere il valore dell&#39;elenco dettagliato (definito dal campo selezionato) nel **[!UICONTROL Value]** campo.

   ![](assets/dce_sidebar_completeoptionradio.png)

### Modifica di campi modulo {#modifying-form-fields}

Campi modulo come pulsanti di scelta, aree di input, elenchi a discesa e così via. può essere modificato dalle relative barre degli strumenti.

Questo consente di:

* Eliminare il blocco contenente i campi del modulo utilizzando l&#39; **[!UICONTROL Delete]** icona .
* Duplica il campo selezionato creando un nuovo blocco utilizzando l&#39; **[!UICONTROL Duplicate]** icona .
* Modificare la **[!UICONTROL Form data]** finestra per collegare un campo di database all&#39;area del modulo utilizzando l&#39; **[!UICONTROL Edit]** icona .

   ![](assets/dce_toolbar_formblock_edition.png)

## Aggiunta di un&#39;azione a un pulsante {#adding-an-action-to-a-button}

Quando l&#39;utente fa clic su un pulsante, è possibile definire un&#39;azione associata. A tale scopo, selezionare l&#39;azione da eseguire dall&#39;elenco a discesa.

![](assets/dce_sidebar_button.png)

Le azioni disponibili sono le seguenti:

* **[!UICONTROL Refresh]** : aggiorna la pagina corrente.
* **[!UICONTROL Next page]** : crea un collegamento alla pagina successiva nell’applicazione Web.
* **[!UICONTROL Previous page]** : crea un collegamento alla pagina precedente nell’applicazione Web.

>[!NOTE]
>
>Il **[!UICONTROL None]** valore consente di non attivare il pulsante.

È possibile modificare l&#39;etichetta collegata al pulsante nel campo corrispondente.

## Aggiunta di un collegamento {#adding-a-link}

Puoi inserire un collegamento in qualsiasi elemento di pagina: immagine, parola, gruppo di parole, blocco di testo, ecc.

A questo scopo, selezionate l&#39;elemento e utilizzate la prima icona dal menu a comparsa.

![](assets/dce_insertlink_icon.png)

Questa icona consente di accedere a tutti i tipi di collegamenti disponibili.

![](assets/dce_insertlink_menu.png)

I blocchi e i campi di personalizzazione possono essere inseriti solo nei blocchi di tipo Testo.

>[!NOTE]
>
>Per ogni tipo di collegamento, puoi configurare la modalità di apertura: selezionate la finestra di destinazione nell&#39;elenco a discesa **Target** . Questo valore corrisponde al tag **`<target>`** HTML.
>
>L&#39;elenco delle **destinazioni** disponibili è il seguente:
>
>* Altro (IFrame)
>* Finestra superiore (_top)
>* Finestra principale (_parent)
>* Nuova finestra (_blank)
>* Finestra corrente (_self)
>* Comportamento browser predefinito

>



### Collegamento a un URL {#link-to-a-url}

L’opzione **Collega a un URL** esterno consente di aprire qualsiasi URL dal contenuto sorgente.

![](assets/dce_toolbar_imgblock_externallink.png)

Immettete l’indirizzo del collegamento in questione nel campo **URL** . Il campo URL deve essere immesso come segue: **https://www.myURL.com**.

### Collegamento a un&#39;applicazione Web {#link-to-a-web-application}

L&#39;opzione **Collega a un&#39;applicazione** Web consente di accedere a un&#39;applicazione Web  Adobe Campaign.

![](assets/dce_toolbar_imgblock_appweb.png)

Selezionare l&#39;applicazione Web dal campo corrispondente.

L&#39;elenco delle applicazioni Web suggerite corrisponde alle applicazioni disponibili nel **[!UICONTROL Resources > Online > Web Applications]** nodo.

### Collegamento a un&#39;azione {#link-to-an-action}

Il **collegamento che definisce un&#39;opzione di azione** consente di configurare un&#39;azione quando si fa clic su un elemento sorgente.

![](assets/dce_toolbar_imgblock_action.png)

>[!NOTE]
>
>Le azioni disponibili sono descritte in [Aggiunta di un&#39;azione a una sezione di pulsante](#adding-an-action-to-a-button) .

### Eliminare un collegamento {#delete-a-link}

Quando è stato inserito un collegamento, la barra degli strumenti offre due nuove icone: **Modifica il collegamento** e **interrompi il collegamento** che consente di interagire con il collegamento creato.

* **[!UICONTROL Edit link]** consente di visualizzare una finestra con tutti i parametri del collegamento.
* **[!UICONTROL Break the link]** consente di eliminare, dopo la conferma, il collegamento e tutti i parametri correlati.

>[!NOTE]
>
>Se il collegamento viene eliminato, il contenuto continua a essere mantenuto.

## Modifica degli attributi di font {#changing-font-attributes}

Quando selezionate un elemento di testo, potete modificare gli attributi del font (stile, formato).

![](assets/dce_toolbar_txt.png)

Le opzioni disponibili sono le seguenti:

* **Icona Ingrandimento font** : aumenta le dimensioni del testo selezionato (aggiungi `<span style="font size:">`)
* **Icona Riduci font** : riduce le dimensioni del testo selezionato (aggiungi `<span style="font size:">`)
* **Icona Grassetto** : rende il testo selezionato in grassetto (con il `<strong> </strong>` tag)
* **Icona Corsivo** : rende il testo selezionato in corsivo (il testo va a capo con il `<em> </em>` tag)
* **Icona sottolineatura** : rende sottolineato il testo selezionato (racchiude il testo con il `<span style="text-decoration: underline;">` tag)
* **Icona Allinea a sinistra** : allinea il testo a sinistra del blocco selezionato (aggiungi stile=&quot;text-align: left;&quot;)
* **Icona Centro** : centra il testo per il blocco selezionato (add style=&quot;text-align: center;&quot;)
* **Icona Allinea a destra** : allinea il testo a destra del blocco selezionato (aggiungi stile=&quot;text-align: right;&quot;)
* **Cambia l’icona del colore** di sfondo: consente di modificare il colore di sfondo del blocco selezionato (aggiungere stile=&quot;background-color: rgba(170, 86, 255, 0.87)
* **Icona Cambia colore** testo: consente di modificare il colore del testo del blocco selezionato o solo del testo selezionato (`<span style="color: #CODE">`)

>[!NOTE]
>
>* **Icona Elimina** : elimina il blocco e tutto il relativo contenuto.
   >
   >
* **Icona duplicata** : duplica il blocco e tutti gli stili correlati al blocco.


## Gestione di immagini e animazioni {#managing-images-and-animations}

Digital Content Editor consente di lavorare su **qualsiasi tipo di immagine** compatibile con i browser.

Per essere compatibile con DCE, le animazioni **di tipo** &quot;Flash&quot; devono essere inserite in una pagina HTML nel modo seguente:

```
<object type="application/x-shockwave-flash" data="https://www.mydomain.com/flash/your_animation.swf" width="200" height="400">
 <param name="movie" value="https://www.mydomain.com/flash/your_animation.swf" />
 <param name="quality" value="high" />
 <param name="play" value="true"/>
 <param name="loop" value="true"/> 
</object>
```

>[!CAUTION]
>
>Non è necessario richiamare file esterni in un tag **script** della pagina HTML. Questi file non verranno importati nel server Adobe Campaign .

### Aggiunta/eliminazione/duplicazione di un’immagine {#adding---deleting---duplicating-an-image}

Per inserire un’immagine, selezionare un blocco per il tipo di immagine e fare clic sull’icona **Immagine** .

![](assets/dce_insert_image.png)

Selezionate un file di immagine salvato localmente.

![](assets/dce_popup_imgupload.png)

L’icona **Elimina** elimina il ![]() tag che contiene l’immagine.

L’icona **Duplica** duplica il ![]() tag e il relativo contenuto.

>[!CAUTION]
>
>Quando duplicate un’immagine, gli identificatori relativi alla nuova immagine vengono eliminati.

### Modifica delle proprietà immagine {#editing-image-properties}

Quando si seleziona un blocco contenente un&#39;immagine, è possibile accedere alle proprietà seguenti:

* **Didascalia** consente di definire la didascalia collegata all’immagine (corrisponde all’attributo **HTML alt** ).
* **Dimension** consente di specificare le dimensioni dell’immagine, in pixel.

   ![](assets/dce_popup_imgsize.png)

## Aggiunta di contenuti personalizzati {#adding-personalization-content}

### Inserimento di un campo di personalizzazione {#inserting-a-personalization-field}

L&#39;opzione Campo **di** personalizzazione per l&#39;icona di inserimento consente di aggiungere al contenuto un campo di database, ad esempio il nome del destinatario. Questa opzione è disponibile solo per i blocchi di testo.

![](assets/dce_toolbar_textblock_persofield.png)

Per impostazione predefinita, i campi offerti sono tratti dalla **[!UICONTROL Recipient]** tabella. Se necessario, modificare le proprietà dell&#39;applicazione Web per selezionare un&#39;altra tabella.

Il nome del campo viene visualizzato nell’editor, evidenziato in giallo. Sarà sostituito dal profilo del destinatario di destinazione quando viene generata la personalizzazione (ad esempio, quando si visualizza l&#39;anteprima di una pagina di destinazione).

Un esempio è presentato nella sezione [Inserimento di un campo](../../web/using/creating-a-landing-page.md#inserting-a-personalization-field) di personalizzazione.

### Inserimento di un blocco di personalizzazione {#inserting-a-personalization-block}

L&#39;opzione per il blocco **di** personalizzazione consente di inserire blocchi dinamici e personalizzati nel contenuto. Ad esempio, potete aggiungere un logo o un messaggio di saluto. Non è disponibile per i blocchi di tipo Testo.

![](assets/dce_toolbar_textblock_persoblock.png)

Una volta inserito, il nome del blocco di personalizzazione viene visualizzato nell’editor, evidenziato in giallo. Viene adattata automaticamente al profilo del destinatario quando viene generata la personalizzazione.

Per ulteriori informazioni sui blocchi di personalizzazione incorporati e su come definire blocchi di personalizzazione personalizzati, consulta [questa pagina](../../delivery/using/personalization-blocks.md).
