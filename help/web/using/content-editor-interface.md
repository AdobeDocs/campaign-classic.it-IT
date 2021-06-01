---
product: campaign
title: Interfaccia dell’editor di contenuti
description: Interfaccia dell’editor di contenuti
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 3%

---

# Interfaccia dell’editor di contenuti{#content-editor-interface}

## Finestra di modifica {#editing-window}

La finestra di modifica DCE è suddivisa in tre diverse sezioni. Consentono di visualizzare, modificare e controllare lo stato del contenuto.

![](assets/dce_decoupe_window_nb.png)

1. La sezione **top** è un&#39;area di visualizzazione per i messaggi inviati all&#39;utente. Questi messaggi indicano lo stato dell’applicazione Web o la consegna in fase di creazione, nonché gli avvisi e i messaggi di errore relativi al contenuto. Per ulteriori informazioni, consulta [Stato del contenuto HTML](../../web/using/content-editing-best-practices.md#html-content-statuses).
1. La sezione a **sinistra** della finestra è l’area da modificare. Da quest’area, l’utente può interagire direttamente con il contenuto utilizzando la barra degli strumenti a comparsa: inserire un collegamento in un’immagine, modificare il font, eliminare un campo, ecc. Per ulteriori informazioni, consulta [Modifica di moduli](../../web/using/editing-content.md#editing-forms).
1. La sezione a **destra** della finestra è l&#39;area del pannello di controllo. Quest’area raggruppa le diverse opzioni per l’editor, in particolare quelle relative alla configurazione dell’intestazione di pagina e delle opzioni generali per un blocco: aggiungere un bordo, collegare un campo di database con un&#39;area di input, accedere alle proprietà della pagina Web, ecc. Per ulteriori informazioni, consulta le sezioni [Opzioni globali](#global-options) e [Modifica del contenuto](../../web/using/editing-content.md) .

## Opzioni globali {#global-options}

La sezione in alto a destra dell’editor consente di accedere alle opzioni globali che consentono di controllare il contenuto attualmente creato.

![](assets/dce_global_options.png)

Sono disponibili quattro icone:

![](assets/dce_icons_sidebar.png)

* L’icona **Mostra/Nascondi blocchi** consente di visualizzare fotogrammi blu intorno ai blocchi di contenuto (corrispondente al tag HTML `<div>` ).

* L’icona **Scegli un altro contenuto** consente all’utente di caricare nuovi contenuti da un modello (modello esistente o modello preconfigurato).

   ![](assets/dce_popup_templatechoice.png)

   >[!CAUTION]
   >
   >Il contenuto selezionato sostituisce il contenuto corrente.

* L&#39;icona **Salva come modello** consente di salvare il contenuto corrente come modello. È necessario immettere l&#39;etichetta e il nome interno per il modello. I modelli sono memorizzati nel nodo **[!UICONTROL Resources > Templates > Content templates]** .

   ![](assets/dce_popup_savetemplate.png)

   Una volta salvato, il modello è disponibile e può essere selezionato al momento della creazione del nuovo contenuto.

   ![](assets/dce_create_fromtemplate.png)

* L&#39;icona **Proprietà pagina** consente di selezionare le informazioni sul contenuto nella parte superiore della pagina HTML.

   ![](assets/dce_popup_headerhtml.png)

   >[!NOTE]
   >
   >Queste informazioni corrispondono ai tag HTML **`<title>`** e **`<meta>`** nella pagina.
   >
   >Le parole chiave devono essere separate da virgole.

## Opzioni blocco {#block-options}

La sezione a destra dell’editor raggruppa le opzioni principali che ti consentono di agire in base al contenuto. Per visualizzare queste opzioni, è necessario selezionare un blocco: la natura di queste opzioni dipende dal blocco selezionato.

![](assets/dce_right_section.png)

Puoi:

* Determinare la visualizzazione di uno o più blocchi, fare riferimento a [Definizione di una condizione di visibilità](../../web/using/editing-content.md#defining-a-visibility-condition),
* Definire bordi e fotogrammi, fare riferimento a [Aggiunta di un bordo e uno sfondo](../../web/using/editing-content.md#adding-a-border-and-background),
* Definire gli attributi immagine (dimensione, didascalia), fare riferimento a [Modifica delle proprietà immagine](../../web/using/editing-content.md#editing-image-properties),
* Collegare il database a un elemento del modulo (area di input, casella di controllo), fare riferimento a [Modifica delle proprietà dei dati per un modulo](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Rendere obbligatoria una parte di un modulo, fare riferimento a [Modifica delle proprietà dei dati per un modulo](../../web/using/editing-content.md#changing-the-data-properties-for-a-form),
* Definire un&#39;azione per un pulsante, fare riferimento a [Aggiunta di un&#39;azione a un pulsante](../../web/using/editing-content.md#adding-an-action-to-a-button).

## Barra dei contenuti {#content-toolbar}

La barra degli strumenti è un **elemento a comparsa** dell’interfaccia DCE che presenta funzioni diverse in base al blocco selezionato.

>[!CAUTION]
>
>Alcune funzioni della barra degli strumenti ti consentono di formattare il contenuto HTML. Tuttavia, se la pagina contiene un foglio di stile CSS, le **istruzioni** del foglio di stile potrebbero assumere **priorità** rispetto alle istruzioni specificate nella barra degli strumenti.
