---
product: campaign
title: Best practice per la modifica dei contenuti
description: Best practice per la modifica dei contenuti
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 3%

---

# Best practice per la modifica dei contenuti{#content-editing-best-practices}



Per garantire il funzionamento ottimale dell’editor, si consiglia di osservare le seguenti linee guida:

* Prima di **importare un modello di pagina HTML** in Adobe Campaign, accertati che il modello si apra e venga visualizzato correttamente nei vari browser.
* Se la pagina HTML contiene **script JavaScript**, è necessario eseguirli **senza errori** all&#39;esterno dell&#39;editor.
* Durante la creazione di un modello, è consigliabile aggiungere un attributo &quot;type&quot;**di tipo** ai tag `<input>`. Queste informazioni verranno elaborate dall&#39;editor e consentiranno all&#39;utente di collegare un campo del database al campo del modulo durante la configurazione dell&#39;applicazione Web.

  Esempio di codice HTML nel modello:

  ```
  <input id="email" type="email" name="email"/>
  ```

  L&#39;attributo **&#39;type&#39;** è visibile nell&#39;interfaccia nel seguente formato:

  ![](assets/dce_sidebar_inputtypechanges.png)

  L&#39;elenco ufficiale degli attributi &#39;type&#39; è disponibile [in questo sito Web](https://www.w3schools.com/tags/att_input_type.asp).

* Passaggi per simulare una pagina finale con DCE:

  ![](assets/dce_enchainement.png)

* Assicurarsi che nella pagina sia presente un solo `<body> </body>`.
* Quando viene caricato un file CSS o JS, le immagini contenute nel file.zip non vengono caricate. I riferimenti a queste immagini presenti nel CSS non vengono quindi aggiornati.

## Formati supportati dall’editor di contenuti {#content-editor-supported-formats}

Digital Content Editor supporta il formato HTML: è possibile passare alla modalità **sorgente** in qualsiasi momento.

La funzione di importazione dell&#39;Editor di contenuti digitali funziona come segue con i seguenti formati supportati:

* CSS: le immagini presenti nel file .zip non vengono importate. I riferimenti a queste immagini nel CSS non vengono aggiornati.
* JS: le immagini presenti nel file .zip non vengono importate. I riferimenti a queste immagini in JS non vengono aggiornati.
* Iframe: le pagine collegate non vengono importate.
* Pagine di destinazione e app Web: se manca un tag **form**, verrà visualizzato un avviso. Un `<form> </form>` deve essere sempre presente nel corpo del messaggio.

Digital Content Editor funziona anche con le seguenti tabelle codici supportate:

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
>La tabella codici di HTML deve essere definita in un tag meta (HTML 4 o HTML 5) o nella distinta base. Se non è disponibile alcuna tabella codici, aprire il file in latino1.

## Stati dei contenuti HTML {#html-content-statuses}

La sezione superiore dell’editor visualizza i messaggi relativi allo stato del contenuto. I codici colore per i messaggi sono i seguenti:

* **Messaggio grigio**: messaggio informativo, non è necessario eseguire alcuna azione nell&#39;editor.
* **Messaggio blu**: messaggio informativo relativo al contenuto in fase di modifica.
* **Messaggio giallo**: messaggio di avviso o di errore che richiede un&#39;azione da parte dell&#39;utente.

### Elenco dei messaggi durante la modifica di un’applicazione web {#list-of-messages-when-editing-a-web-application}

* Il contenuto HTML funziona.
* L&#39;applicazione Web non è stata pubblicata e non è possibile accedervi online.
* L&#39;applicazione Web è online. Pubblicare di nuovo per applicare le modifiche.
* Il contenuto della pagina non funziona. Deve includere un modulo HTML (`<form>`)
* Nessuna zona o pulsante di input da configurare.
* Per attivare la transizione alla pagina successiva, è necessario collegare l&#39;azione &#39;Pagina successiva&#39; a un pulsante o a un collegamento nella pagina corrente.

### Elenco dei messaggi durante la modifica di una consegna {#list-of-messages-when-editing-a-delivery}

* Il contenuto della consegna è funzionale
* Non sono presenti campi o blocchi di personalizzazione da configurare.
* Il contenuto della consegna è pronto, esegui nuovamente l’analisi per applicare eventuali modifiche.
* La consegna è pronta per essere inviata.
