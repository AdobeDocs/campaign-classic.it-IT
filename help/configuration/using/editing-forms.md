---
product: campaign
title: Modificare i moduli
description: Modificare i moduli
audience: configuration
content-type: reference
topic-tags: input-forms
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: f4b9ac3300094a527b5ec1b932d204f0e8e5ee86
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 4%

---


# Modificare i moduli{#editing-forms}

![](../../assets/common.svg)

## Panoramica

Gli addetti al marketing e gli operatori utilizzano moduli di input per creare, modificare e visualizzare in anteprima i record. Forms mostra una rappresentazione visiva delle informazioni.

È possibile creare e modificare i moduli di input:

* È possibile modificare i moduli di input di fabbrica consegnati per impostazione predefinita. I moduli di input di fabbrica si basano sugli schemi di dati di fabbrica.
* È possibile creare moduli di input personalizzati in base agli schemi di dati definiti dall’utente.

Forms è entità di `xtk:form` digitare. È possibile visualizzare la struttura del modulo di input nel `xtk:form` schema. Per visualizzare questo schema, scegli **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** dal menu. Ulteriori informazioni [struttura del modulo](form-structure.md).

Per accedere ai moduli di input, scegli **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** dal menu:

![](assets/d_ncs_integration_form_arbo.png)

Per progettare i moduli, modificare il contenuto XML nell’editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Leggi tutto](form-structure.md#formatting).

Per visualizzare l’anteprima di un modulo, fare clic sul pulsante **[!UICONTROL Preview]** scheda:

![](assets/d_ncs_integration_form_preview.png)

## Tipi di modulo

È possibile creare diversi tipi di moduli di input. Il tipo di modulo determina il modo in cui gli utenti navigano nel modulo:

* Schermata della console

   Questo è il tipo di modulo predefinito. Il modulo comprende una singola pagina.

   ![](assets/console_screen_form.png)

* Gestione dei contenuti

   Utilizzare questo tipo di modulo per la gestione del contenuto. Vedi questo [caso d&#39;uso](../../delivery/using/use-case--creating-content-management.md).

   ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Creazione guidata

   Questo modulo comprende più schermate mobili ordinate in sequenze specifiche. Gli utenti passano da una schermata all’altra. [Leggi tutto](form-structure.md#wizards).

* Iconbox

   Questo modulo comprende più pagine. Per spostarsi nel modulo, gli utenti selezionano le icone a sinistra del modulo.

   ![](assets/iconbox_form_preview.png)

* Notebook

   Questo modulo comprende più pagine. Per spostarsi nel modulo, gli utenti selezionano le schede nella parte superiore del modulo.

   ![](assets/notebook_form_preview.png)

* Riquadro verticale

   Questo modulo mostra una struttura di navigazione.

* Riquadro orizzontale

   Questo modulo mostra un elenco di elementi.

## Contenitori

Nei moduli è possibile utilizzare i contenitori per vari scopi:

* Organizzazione del contenuto all’interno dei moduli
* Definire l’accesso ai campi di input
* Nidificazione di moduli in altri moduli

[Leggi tutto](form-structure.md#containers).

### Organizzare i contenuti

Utilizzare i contenitori per organizzare il contenuto all’interno dei moduli:

* È possibile raggruppare i campi in sezioni.
* È possibile aggiungere pagine a moduli multipagina.

Per inserire un contenitore, utilizza le `<container>` elemento. [Leggi tutto](form-structure.md#containers).

#### Campi gruppo

Utilizza i contenitori per raggruppare i campi di input in sezioni organizzate.

Per inserire una sezione in un modulo, utilizzare questo elemento: `<container type="frame">`. Facoltativamente, per aggiungere un titolo di sezione, utilizza il `label` attributo.

Sintassi: `<container type="frame" label="`*section_title*`"> […] </container>`

In questo esempio, un contenitore definisce il **Creazione** la sezione che comprende **[!UICONTROL Created by]** e **[!UICONTROL Name]** campi di input:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Aggiungere pagine ai moduli multipagina

Per i moduli con più pagine, utilizzare un contenitore per creare una pagina del modulo.

Questo esempio mostra i contenitori per **Generale** e **Dettagli** pagine di un modulo:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Definire l’accesso ai campi

Utilizza i contenitori per definire cosa è visibile e per definire l’accesso ai campi. È possibile attivare o disattivare gruppi di campi.

### Nidificare moduli

Utilizzare i contenitori per nidificare i moduli all’interno di altri moduli. [Leggi tutto](#add-pages-to-multipage-forms).

## Riferimenti alle immagini

Per trovare le immagini, scegli **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** dal menu.

Per associare un’immagine a un elemento del modulo, ad esempio un’icona, è possibile aggiungere un riferimento a un’immagine. Utilizza la `img` , ad esempio nel `<container>` elemento.

Sintassi: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Questo esempio mostra i riferimenti al `book.png` e `detail.png` immagini dal `ncm` namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Queste immagini vengono utilizzate per le icone che gli utenti fanno clic per spostarsi in un modulo multipagina:

![](assets/nested_forms_preview.png)
