---
product: campaign
title: Best practice per la modifica dei contenuti
description: Best practice per la modifica dei contenuti
audience: web
content-type: reference
topic-tags: editing-html-content
exl-id: c1eccb48-59bf-412f-9c18-9cda2a022096
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 6%

---

# Best practice per la modifica dei contenuti{#content-editing-best-practices}

![](../../assets/common.svg)

Per garantire il funzionamento ottimale dell’editor, si consiglia di osservare le seguenti linee guida:

* Prima di **importare un modello di pagina HTML** in Adobe Campaign, assicurati che il modello si apra e venga visualizzato correttamente nei vari browser.
* Se la pagina HTML contiene **script JavaScript**, devono eseguire **senza errori** all&#39;esterno dell&#39;editor.
* Durante la creazione di un modello, è consigliabile aggiungere un attributo **“type”** ai tag. `<input>` Queste informazioni verranno elaborate dall&#39;editor e consentiranno all&#39;utente di collegare un campo del database al campo del modulo durante la configurazione dell&#39;applicazione Web.

   Esempio di codice HTML nel modello:

   ```
   <input id="email" type="email" name="email"/>
   ```

   L&#39;attributo **&#39;type&#39;** è visibile nell&#39;interfaccia nel seguente modulo:

   ![](assets/dce_sidebar_inputtypechanges.png)

   L&#39;elenco ufficiale degli attributi &quot;type&quot; è disponibile [in questo sito web](https://www.w3schools.com/tags/att_input_type.asp).

* Passaggi per simulare una pagina finale con il DCE:

   ![](assets/dce_enchainement.png)

* Assicurati che nella pagina sia presente un solo elemento `<body> </body>`.
* Quando viene caricato un file CSS o JS, le immagini contenute nel file .zip non vengono caricate. I riferimenti a queste immagini presenti nel CSS non vengono quindi aggiornati.

## Formati supportati dall’editor dei contenuti {#content-editor-supported-formats}

L’editor di contenuti digitali supporta il formato HTML: puoi passare in qualsiasi momento alla modalità **sorgente** .

La funzione di importazione di Digital Content Editor funziona come segue con i seguenti formati supportati:

* CSS: le immagini presenti nel file .zip non vengono importate. I riferimenti a queste immagini nel CSS non vengono aggiornati.
* JS: le immagini presenti nel file .zip non vengono importate. I riferimenti a queste immagini nel JS non vengono aggiornati.
* Iframe: le pagine collegate non vengono importate.
* Pagine di destinazione e app web: se manca un tag **form**, viene visualizzato un avviso. Un `<form> </form>` deve essere sempre presente nel corpo del messaggio.

L’editor di contenuti digitali funziona anche con le seguenti pagine di codice supportate:

* iso-8859-1
* iso-8859-2
* utf-7
* utf-8 (consigliato quando si utilizza una distinta base)
* iso-8859-15
* us-ascii
* turno jis
* iso-2022-jp
* big-5
* euc-kr
* utf-16

>[!NOTE]
>
>La tabella codici HTML deve essere definita in un tag meta (HTML 4 o HTML 5) o nella distinta base. Se non è disponibile alcuna tabella codici, apri il file in latino1.

## Stati del contenuto HTML {#html-content-statuses}

Nella sezione superiore dell’editor vengono visualizzati i messaggi relativi allo stato del contenuto. I codici colore dei messaggi sono i seguenti:

* **Messaggio** grigio: messaggio informativo, non è necessario eseguire azioni nell’editor.
* **Messaggio** blu: messaggio informativo relativo al contenuto in corso di modifica.
* **Messaggio** giallo: avviso o messaggio di errore che richiede un&#39;azione per conto dell&#39;utente.

### Elenco dei messaggi durante la modifica di un&#39;applicazione Web {#list-of-messages-when-editing-a-web-application}

* Il contenuto HTML funziona.
* L&#39;applicazione Web non è stata pubblicata e non è possibile accedervi online.
* L&#39;applicazione Web è online. Per applicare eventuali modifiche, eseguire di nuovo la pubblicazione.
* Il contenuto della pagina non funziona. Deve includere un modulo HTML (`<form>`)
* Non sono presenti aree di input o pulsanti da configurare.
* Per abilitare la transizione alla pagina successiva, devi collegare l’azione &quot;Pagina successiva&quot; a un pulsante o a un collegamento nella pagina corrente.

### Elenco dei messaggi durante la modifica di una consegna {#list-of-messages-when-editing-a-delivery}

* Il contenuto della consegna è funzionale
* Non ci sono campi o blocchi di personalizzazione da configurare.
* Il contenuto della consegna è pronto. Esegui di nuovo l’analisi per applicare eventuali modifiche.
* La consegna è pronta per essere inviata.
