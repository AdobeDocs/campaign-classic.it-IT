---
product: campaign
title: Interfaccia dell’editor di contenuti
description: Interfaccia dell’editor di contenuti
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: cb76f3dc-7f3a-49de-89cb-c106865ecb17
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 3%

---

# Interfaccia dell’editor di contenuti{#content-editor-interface}



## Finestra di modifica {#editing-window}

La finestra di modifica DCE è suddivisa in tre diverse sezioni. Consentono di visualizzare, modificare e controllare lo stato del contenuto.

![](assets/dce_decoupe_window_nb.png)

1. La sezione **top** è un&#39;area di visualizzazione per i messaggi inviati all&#39;utente. Questi messaggi indicano lo stato dell’applicazione web o della consegna in fase di creazione, nonché avvisi e messaggi di errore relativi al contenuto. Per ulteriori informazioni, consulta [Stati del contenuto di HTML](content-editing-best-practices.md#html-content-statuses).
1. La sezione a **sinistra** della finestra è l&#39;area per la modifica del contenuto. Da quest’area, l’utente può interagire direttamente con il contenuto utilizzando la barra degli strumenti pop-up: inserire un collegamento in un’immagine, modificare il font, eliminare un campo e così via. Per ulteriori informazioni, consulta [Modifica dei moduli](editing-content.md#editing-forms).
1. La sezione a **destra** della finestra è l&#39;area del Pannello di controllo. In quest’area sono raggruppate le diverse opzioni per l’editor, in particolare quelle relative alla configurazione dell’intestazione della pagina e le opzioni generali per un blocco: aggiungi un bordo, collega un campo del database con un’area di input, accedi alle proprietà della pagina web e così via. Per ulteriori informazioni, consulta le sezioni [Opzioni globali](#global-options) e [Modifica del contenuto](editing-content.md).

## Opzioni globali {#global-options}

La sezione in alto a destra dell’editor ti consente di accedere alle opzioni globali che ti consentono di controllare il contenuto attualmente in fase di creazione.

![](assets/dce_global_options.png)

Sono disponibili quattro icone:

![](assets/dce_icons_sidebar.png)

* L&#39;icona **Visualizza/Nascondi blocchi** consente di visualizzare frame blu intorno ai blocchi di contenuto (corrispondenti al tag HTML `<div>`).

* L&#39;icona **Scegli un altro contenuto** consente all&#39;utente di caricare nuovo contenuto da un modello (modello esistente o predefinito).

  ![](assets/dce_popup_templatechoice.png)

  >[!CAUTION]
  >
  >Il contenuto selezionato sostituisce il contenuto corrente.

* L&#39;icona **Salva come modello** consente di salvare il contenuto corrente come modello. Immettere l&#39;etichetta e il nome interno per il modello. I modelli sono archiviati nel nodo **[!UICONTROL Resources > Templates > Content templates]**.

  ![](assets/dce_popup_savetemplate.png)

  Una volta salvato, il modello è disponibile e può essere selezionato durante la creazione di nuovo contenuto.

  ![](assets/dce_create_fromtemplate.png)

* L&#39;icona **Proprietà pagina** consente di selezionare le informazioni sul contenuto nella parte superiore della pagina di HTML.

  ![](assets/dce_popup_headerhtml.png)

  >[!NOTE]
  >
  >Queste informazioni corrispondono ai tag HTML **`<title>`** e **`<meta>`** sulla pagina.
  >
  >Le parole chiave devono essere separate da virgole.

## Opzioni di blocco {#block-options}

La sezione a destra dell’editor raggruppa le opzioni principali che ti consentono di agire sul contenuto. Per visualizzare queste opzioni, devi selezionare un blocco: la natura di queste opzioni dipende dal blocco selezionato.

![](assets/dce_right_section.png)

Puoi eseguire le seguenti azioni:

* Determinare la visualizzazione per uno o più blocchi. Fare riferimento a [Definizione di una condizione di visibilità](editing-content.md#defining-a-visibility-condition),
* Definire i bordi e le cornici. Fare riferimento a [Aggiunta di un bordo e di uno sfondo](editing-content.md#adding-a-border-and-background),
* Definisci gli attributi dell&#39;immagine (dimensioni, didascalia). Fai riferimento a [Modifica delle proprietà dell&#39;immagine](editing-content.md#editing-image-properties),
* Collegare il database a un elemento modulo (zona di input, casella di controllo). Fare riferimento a [Modifica delle proprietà dei dati per un modulo](editing-content.md#changing-the-data-properties-for-a-form),
* Rendere obbligatoria una parte di un modulo, fare riferimento a [Modifica delle proprietà dei dati per un modulo](editing-content.md#changing-the-data-properties-for-a-form),
* Definire un&#39;azione per un pulsante. Vedere [Aggiunta di un&#39;azione a un pulsante](editing-content.md#adding-an-action-to-a-button).

## Barra degli strumenti Contenuto {#content-toolbar}

La barra degli strumenti è un **elemento popup** dell&#39;interfaccia DCE che presenta funzioni diverse in base al blocco selezionato.

>[!CAUTION]
>
>Alcune funzioni della barra degli strumenti ti consentono di formattare il contenuto HTML. Tuttavia, se la pagina contiene un foglio di stile CSS, le **istruzioni** del foglio di stile potrebbero avere **priorità** rispetto alle istruzioni specificate con la barra degli strumenti.
