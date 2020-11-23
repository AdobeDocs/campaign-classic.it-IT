---
solution: Campaign Classic
product: campaign
title: Interfaccia dell’editor di contenuti
description: Interfaccia dell’editor di contenuti
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: c93931820887306c0ef64ef05d4f0ba2ca5a98aa
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---


# Interfaccia dell’editor di contenuti{#content-editor-interface}

## Finestra di modifica {#editing-window}

La finestra di modifica DCE è suddivisa in tre diverse sezioni. Consentono di visualizzare, modificare e controllare lo stato del contenuto.

![](assets/dce_decoupe_window_nb.png)

1. La sezione **superiore** è un&#39;area di visualizzazione per i messaggi all&#39;utente. Questi messaggi indicano lo stato dell&#39;applicazione Web o la consegna in fase di creazione, nonché gli avvisi e i messaggi di errore relativi al contenuto. Per ulteriori informazioni, consultate gli stati del contenuto [HTML](../../web/using/content-editing-best-practices.md#html-content-statuses).
1. La sezione a **sinistra** della finestra è l’area da cui modificare il contenuto. Da questa area, l&#39;utente può interagire direttamente con il contenuto utilizzando la barra degli strumenti a comparsa: inserire un collegamento in un&#39;immagine, modificare il font, eliminare un campo e così via. For more on this refer to [Editing forms](../../web/using/editing-content.md#editing-forms).
1. La sezione a **destra** della finestra è l&#39;area del pannello di controllo. Quest&#39;area raggruppa le diverse opzioni per l&#39;editor, in particolare quelle relative alla configurazione dell&#39;intestazione di pagina e delle opzioni generali per un blocco: aggiungere un bordo, collegare un campo di database con un&#39;area di input, accedere alle proprietà della pagina Web, ecc. Per ulteriori informazioni, consultare le sezioni Opzioni [](#global-options) globali e [Modifica del contenuto](../../web/using/editing-content.md) .

## Opzioni globali {#global-options}

La sezione in alto a destra dell’editor consente di accedere alle opzioni globali per controllare il contenuto attualmente creato.

![](assets/dce_global_options.png)

Sono disponibili quattro icone:

![](assets/dce_icons_sidebar.png)

* L&#39;icona **Visualizza/Nascondi blocchi** consente di visualizzare cornici blu intorno ai blocchi di contenuto (corrispondenti al tag `<div>` HTML).

* L’icona **Scegli un altro contenuto** consente all’utente di caricare nuovo contenuto da un modello (modello esistente o modello out-of-the-box).

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >Il contenuto selezionato sostituisce quello corrente.

* L’icona **Salva come modello** consente di salvare il contenuto corrente come modello. È necessario immettere l&#39;etichetta e il nome interno per il modello. I modelli sono memorizzati nel **[!UICONTROL Resources > Templates > Content templates]** nodo.

   ![](assets/dce_popup_savetemplate.png)

   Una volta salvato, il modello è disponibile e può essere selezionato durante la creazione di nuovo contenuto.

   ![](assets/dce_create_fromtemplate.png)

* L&#39;icona delle proprietà **** Pagina consente di selezionare le informazioni sul contenuto nella parte superiore della pagina HTML.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >Queste informazioni corrispondono ai tag **`<title>`** e **`<meta>`** HTML della pagina.
   >
   >Le parole chiave devono essere separate da virgole.

## Opzioni di blocco {#block-options}

La sezione a destra dell’editor raggruppa le opzioni principali che consentono di agire sul contenuto. Per visualizzare queste opzioni, è necessario selezionare un blocco: la natura di queste opzioni dipende dal blocco selezionato.

![](assets/dce_right_section.png)

Puoi:

* Determinare la visualizzazione di uno o più blocchi, fare riferimento a [Definizione di una condizione](../../web/using/editing-content.md#defining-a-visibility-condition)di visibilità,
* Definire bordi e cornici, fare riferimento a [Aggiunta di un bordo e di uno sfondo](../../web/using/editing-content.md#adding-a-border-and-background),
* Definire gli attributi immagine (dimensione, didascalia), fare riferimento a [Modifica delle proprietà](../../web/using/editing-content.md#editing-image-properties)immagine,
* Collegare il database a un elemento del modulo (area di input, casella di controllo), fare riferimento a [Modifica delle proprietà dei dati per un modulo](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Rendere obbligatoria una parte di un modulo, fare riferimento a [Modifica delle proprietà dei dati per un modulo](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Definire un&#39;azione per un pulsante, fare riferimento a [Aggiunta di un&#39;azione a un pulsante](../../web/using/editing-content.md#adding-an-action-to-a-button).

## Barra degli strumenti Contenuto {#content-toolbar}

La barra degli strumenti è un elemento **a** comparsa dell&#39;interfaccia DCE che presenta funzioni diverse in base al blocco selezionato.

>[!CAUTION]
>
>Alcune funzioni della barra degli strumenti ti consentono di formattare il contenuto HTML. However, if the page contains a CSS style sheet, the **instructions** from the style sheet may prove to take **priority** over the instructions specified with the toolbar.

