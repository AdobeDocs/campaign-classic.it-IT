---
title: Best practice per la modifica del contenuto
seo-title: Best practice per la modifica del contenuto
description: Best practice per la modifica del contenuto
seo-description: null
page-status-flag: never-activated
uuid: badc6806-b474-4cad-94a3-003a50271281
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 3ad38469-8e22-4bfc-8029-5d360f76d6bb
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 7%

---


# Best practice per la modifica del contenuto{#content-editing-best-practices}

Per garantire il funzionamento ottimale dell&#39;editor, si consiglia di osservare le seguenti linee guida:

* Before **importing an HTML page template** in Adobe Campaign, please make sure the template opens and displays correctly in the various browsers.
* If the HTML page contains **JavaScript scripts**, they need to execute **without errors** outside of the editor.
* Durante la creazione di un modello, è consigliabile aggiungere un attributo **“type”** ai tag. `<input>` Queste informazioni verranno elaborate dall&#39;editor e aiuteranno l&#39;utente a collegare un campo del database al campo del modulo durante la configurazione dell&#39;applicazione Web.

   Esempio di codice HTML nel modello:

   ```
   <input id="email" type="email" name="email"/>
   ```

   L&#39;attributo **&#39;type&#39;** è visibile nell&#39;interfaccia nel seguente modulo:

   ![](assets/dce_sidebar_inputtypechanges.png)

   L&#39;elenco ufficiale degli attributi &#39;type&#39; è disponibile [in questo sito Web](https://www.w3schools.com/tags/att_input_type.asp).

* Passaggi per simulare una pagina finale con DCE:

   ![](assets/dce_enchainement.png)

* Accertatevi che sia presente solo una `<body> </body>` nella pagina.
* Quando viene caricato un file CSS o JS, le immagini contenute nel file .zip non vengono caricate. I riferimenti a queste immagini presenti nel CSS non vengono quindi aggiornati.

## Formati supportati per l&#39;editor di contenuti {#content-editor-supported-formats}

Digital Content Editor supporta il formato HTML: è possibile passare alla modalità **sorgente** in qualsiasi momento.

La funzione di importazione di Digital Content Editor funziona come segue con i seguenti formati supportati:

* CSS: le immagini presenti nel file .zip non vengono importate. I riferimenti a queste immagini nel CSS non vengono aggiornati.
* JS: le immagini presenti nel file .zip non vengono importate. I riferimenti a queste immagini in JS non vengono aggiornati.
* Iframe: le pagine collegate non vengono importate.
* Pagine di destinazione e app Web: se manca un tag **modulo** , viene visualizzato un avviso. Un messaggio `<form> </form>` deve essere sempre presente nel corpo del messaggio.

Digital Content Editor funziona anche con le seguenti pagine di codice supportate:

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8 (consigliato quando si utilizza una distinta base)
* iso-8859-15
* us-ascii
* shift jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>La tabella codici HTML deve essere definita in un tag meta (HTML 4 o HTML 5) o nella distinta base. Se non è disponibile alcuna tabella codici, aprite il file in latin1.

## Stati del contenuto HTML {#html-content-statuses}

Nella sezione superiore dell&#39;editor vengono visualizzati messaggi relativi allo stato del contenuto. I codici colore dei messaggi sono i seguenti:

* **Messaggio** grigio: messaggio di informazioni, non è necessario eseguire alcuna azione nell&#39;editor.
* **Messaggio** blu: messaggio informativo relativo al contenuto in corso di modifica.
* **Messaggio** giallo: messaggio di avviso o di errore che richiede un&#39;azione per conto dell&#39;utente.

### Elenco di messaggi durante la modifica di un&#39;applicazione Web {#list-of-messages-when-editing-a-web-application}

* Il contenuto HTML è funzionale.
* L&#39;applicazione Web non è stata pubblicata e non è possibile accedervi online.
* L&#39;applicazione Web è online. Pubblicare di nuovo per applicare eventuali modifiche.
* Il contenuto della pagina non funziona. Deve includere un modulo HTML (`<form>`)
* Nessuna zona di input o pulsanti da configurare.
* Per abilitare la transizione alla pagina successiva, è necessario collegare l&#39;azione &quot;Pagina successiva&quot; a un pulsante o a un collegamento sulla pagina corrente.

### Elenco dei messaggi durante la modifica di una consegna {#list-of-messages-when-editing-a-delivery}

* Il contenuto della distribuzione è funzionale
* Non ci sono campi o blocchi di personalizzazione da configurare.
* Il contenuto della distribuzione è pronto. Eseguire di nuovo l&#39;analisi per applicare eventuali modifiche.
* La consegna è pronta per essere inviata.

