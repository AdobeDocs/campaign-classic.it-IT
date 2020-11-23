---
solution: Campaign Classic
product: campaign
title: Aggiunta di campi a un modulo web
description: Aggiunta di campi a un modulo web
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '2446'
ht-degree: 1%

---


# Aggiunta di campi a un modulo web{#adding-fields-to-a-web-form}

In un modulo Web, i campi consentono agli utenti di immettere informazioni e selezionare opzioni. I moduli Web offrono campi di input, campi di selezione, contenuto statico e avanzato (didascalie, iscrizioni, ecc.).

Quando si utilizza la procedura guidata per aggiungere i campi, il tipo di campo viene rilevato automaticamente in base al campo o alla variabile di memorizzazione selezionati. È possibile modificarlo utilizzando la casella a **[!UICONTROL Type]** discesa nella **[!UICONTROL General]** scheda.

![](assets/s_ncs_admin_webform_change_type.png)

Quando si utilizzano i pulsanti nella barra degli strumenti, selezionare il tipo di campo da aggiungere.

Sono disponibili i seguenti tipi di campo:

* Testo/numero immesso. Consultate [Aggiunta di campi](#adding-input-fields)di input.
* Selezione elenco a discesa. Vedere [Aggiunta di elenchi](#adding-drop-down-lists)a discesa.
* Scelta multipla tramite caselle di controllo. Vedere [Aggiunta di caselle](#adding-checkboxes)di controllo.
* Selezione esclusiva tramite pulsanti di scelta. Vedere [Aggiunta di pulsanti](#adding-radio-buttons)di scelta.
* Votate in una griglia di opzioni. Consultate [Aggiunta di griglie](#adding-grids).
* Numeri e date. Consultate [Aggiunta di date e numeri](#adding-dates-and-numbers).
* Iscrizione/annullamento dell’iscrizione a un servizio di informazioni. Consultate [Caselle](#subscription-checkboxes)di controllo Iscrizione.
* Convalida Captcha. Consultate [Inserimento di un captcha](#inserting-a-captcha).
* Pulsante Scarica. [Caricamento di un file](#uploading-a-file).
* Costante nascosta. Vedere [Inserimento di una costante](#inserting-a-hidden-constant)nascosta.

Specificare la modalità di memorizzazione della risposta: aggiornare un campo nel database (memorizza solo l&#39;ultimo valore salvato) o memorizzare in una variabile (la risposta non è memorizzata). Per ulteriori informazioni, consultare i campi [di archiviazione](../../web/using/web-forms-answers.md#response-storage-fields)Risposta.

>[!NOTE]
>
>Per impostazione predefinita, il campo è inserito nella parte inferiore della struttura ad albero corrente. Utilizzate le frecce nella barra degli strumenti per spostarle verso l’alto o il basso.

## Creazione guidata campo {#field-creation-wizard}

Per ciascuna pagina del modulo è possibile aggiungere un campo utilizzando il primo pulsante nella barra degli strumenti. Per fare ciò, andate al **[!UICONTROL Add using the wizard]** menu.

![](assets/s_ncs_admin_survey_add_field_menu.png)

Selezionate il tipo di campo da creare: è possibile scegliere di aggiungere un campo nel database, una variabile o di importare un gruppo di campi creati in un altro modulo e raccolti in un contenitore.

Fare clic **[!UICONTROL Next]** e selezionare il campo di memorizzazione o la variabile oppure il contenitore da importare.

![](assets/s_ncs_admin_webform_wz_confirm_db.png)

Fare clic **[!UICONTROL Finish]** per inserire il campo selezionato nella pagina.

![](assets/s_ncs_admin_webform_wz_insert_field.png)

## Aggiunta di campi di input {#adding-input-fields}

Per aggiungere un campo di input, fare clic sul **[!UICONTROL Input control]** pulsante e scegliere il tipo di campo da aggiungere.

![](assets/s_ncs_admin_webform_select_field.png)

### Tipi di campi di input {#types-of-input-fields}

In una pagina del modulo è possibile inserire cinque tipi diversi di campi di testo:

* **Testo**: consente all&#39;utente di inserire un testo su una riga.

   ![](assets/s_ncs_admin_survey_txt_ex.png)

* **Numero**: consente all&#39;utente di immettere un numero su una riga. for more on this, refer to [Adding numbers](#adding-numbers).

   Quando la pagina viene approvata, il contenuto del campo viene controllato per verificare che il valore immesso sia compatibile con il campo. For more on this, refer to [Defining control settings](../../web/using/form-rendering.md#defining-control-settings).

* **Password**: consente all&#39;utente di inserire il testo su una sola riga. Durante l&#39;immissione del testo, i caratteri vengono sostituiti da punti:

   ![](assets/s_ncs_admin_survey_passwd_ex.png)

   >[!CAUTION]
   >
   >Le password sono memorizzate non crittografate nel database.

* **Testo** multiriga: consente all&#39;utente di inserire il testo su più righe.

   ![](assets/s_ncs_admin_survey_txtmulti_ex.png)

   >[!CAUTION]
   >
   >I campi di testo su più righe sono campi specifici che possono contenere ritorni a capo. Lo spazio di archiviazione deve essere associato a un campo mappato su un elemento XML, non a un attributo XML. Per ulteriori informazioni sui tipi di dati negli schemi, vedere il capitolo &quot;Riferimento allo schema&quot; in [questa sezione](../../configuration/using/about-schema-reference.md).
   >   
   >Se utilizzate il modulo **Sondaggio** , potete memorizzare questo tipo di campo in un campo archiviato che si adatterà automaticamente al formato. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/about-surveys.md).

* **Testo** multiriga con riciclo: consente all&#39;utente di immettere del testo con un layout che verrà memorizzato in formato HTML.

   ![](assets/s_ncs_admin_survey_txthtmli_ex.png)

   Potete selezionare il tipo di editor offerto agli utenti. A tal fine, utilizzare la casella a discesa del **[!UICONTROL HTML editor]** campo nella **[!UICONTROL Advanced]** scheda.

   ![](assets/webapp_enrich_text_type.png)

   Il numero di icone visualizzate varia a seconda del tipo di editor. Per un **[!UICONTROL Advanced]** editor, il rendering sarà il seguente:

   ![](assets/webapp_enrich_text_max.png)

### Configurare i campi di input {#configure-input-fields}

I campi di input sono tutti configurati in base alla stessa modalità, utilizzando le seguenti opzioni:

![](assets/s_ncs_admin_survey_txt_param.png)

La **[!UICONTROL General]** scheda consente di inserire il nome del campo e di attribuire un valore predefinito al campo, se necessario.

La modalità di memorizzazione delle risposte può essere modificata tramite il **[!UICONTROL Edit storage...]** collegamento. I valori possono essere memorizzati in un campo esistente del database; oppure potete scegliere di non salvare le informazioni nel database (usare una variabile locale).

>[!NOTE]
>
>Le modalità di memorizzazione sono dettagliate nei campi di memorizzazione [Risposta](../../web/using/web-forms-answers.md#response-storage-fields)

La **[!UICONTROL Advanced]** scheda consente di definire i parametri di visualizzazione del campo (posizione delle etichette, allineamento, ecc.). See [Defining web forms layout](../../web/using/defining-web-forms-layout.md).

## Aggiunta di elenchi a discesa {#adding-drop-down-lists}

Potete inserire un elenco a discesa in una pagina di sondaggio. Questo consente all&#39;utente di selezionare un valore tra quelli disponibili in un menu a discesa.

![](assets/s_ncs_admin_survey_dropdown_sample.png)

Per aggiungere una casella a discesa a una pagina del modulo, fare clic sul **[!UICONTROL Selection controls > Drop-down list]** pulsante nella barra degli strumenti dell&#39;Editor pagina.

![](assets/s_ncs_admin_survey_create_dropdown.png)

Selezionare la modalità di memorizzazione delle risposte e confermare la scelta.

Definire le etichette e i valori dell&#39;elenco nella sezione inferiore della **[!UICONTROL General]** scheda. Se le informazioni sono memorizzate in un campo esistente del database ed è un campo di enumerazione, è possibile compilare automaticamente i valori facendo clic **[!UICONTROL Initialize the list of values from the database]** , come mostrato di seguito:

![](assets/s_ncs_admin_survey_database_values.png)

>[!NOTE]
>
>Utilizzate le frecce a destra dell’elenco di valori per modificarne la sequenza.

Se i dati sono memorizzati in una tabella collegata, è possibile selezionare il campo in cui vengono salvati i valori suggeriti nell&#39;elenco. Ad esempio, se si seleziona la tabella dei paesi, fare clic **[!UICONTROL Initialize the list of values from the database...]** e selezionare il campo desiderato.

![](assets/s_ncs_admin_survey_preload_values.png)

Quindi, fate clic sul **[!UICONTROL Load]** collegamento per recuperare i valori:

![](assets/s_ncs_admin_survey_load_button.png)

>[!CAUTION]
>
>Ripetete questa operazione ogni volta che l&#39;elenco viene aggiornato per aggiornare i valori dell&#39;offerta.

## Aggiunta di caselle di controllo {#adding-checkboxes}

Affinché l’utente possa selezionare un’opzione, è necessario utilizzare una casella di controllo.

![](assets/s_ncs_admin_survey_check_box.png)

Per aggiungere una casella di controllo a un modulo, fare clic sull&#39; **[!UICONTROL Selection controls > Checkbox...]** icona nella barra degli strumenti dell&#39;Editor pagina.

Selezionare la modalità di memorizzazione delle risposte e confermare la scelta.

Immettere l&#39;etichetta della casella nel **[!UICONTROL Label]** campo della **[!UICONTROL General]** scheda.

![](assets/s_ncs_admin_survey_check_box_edit.png)

Una casella di controllo consente di assegnare un valore al campo di memorizzazione (o valore) a seconda che la casella sia selezionata o meno. La **[!UICONTROL Values]** sezione consente di immettere il valore da assegnare se la casella è selezionata (nel **[!UICONTROL Value]** campo) e il valore da assegnare se non è selezionata (nel **[!UICONTROL Empty value]** campo). Questi valori dipendono dal formato di memorizzazione dei dati.

Se il campo di memorizzazione (o variabile) è booleano, il valore da assegnare se la casella non è selezionata viene dedotto automaticamente. In questo caso, viene offerto solo il **[!UICONTROL Value if checked]** campo, come mostrato di seguito:

![](assets/s_ncs_admin_survey_check_box_enum.png)

## Esempio: Assegnare un valore a un campo se è selezionata una casella {#example--assign-a-value-to-a-field-if-a-box-is-checked}

Inserire una casella di controllo in un modulo per inviare una richiesta di manutenzione, come illustrato di seguito:

![](assets/s_ncs_admin_survey_check_box_ex.png)

Le informazioni verranno caricate nel database e in un campo esistente (in questo caso, il **[!UICONTROL Comment]** campo):

![](assets/s_ncs_admin_survey_check_box_ex_list.png)

Se la casella &quot;Manutenzione richiesta&quot; è selezionata, la **[!UICONTROL Comment]** colonna conterrà &quot;Manutenzione richiesta&quot;. Se la casella non è selezionata, nella colonna viene visualizzato &quot;Manutenzione non necessaria&quot;. Per ottenere questo risultato, applicare la seguente configurazione alla casella di controllo nella pagina del modulo:

![](assets/s_ncs_admin_survey_check_box_ex_edit.png)

## Aggiunta di pulsanti di scelta {#adding-radio-buttons}

I pulsanti di scelta consentono di offrire all’utente una serie di opzioni esclusive tra cui scegliere. Si tratta di valori diversi per lo stesso campo.

![](assets/s_ncs_admin_survey_radio_button.png)

È possibile creare pulsanti di scelta individualmente (pulsanti di unità) o tramite un elenco a scelta multipla, ma poiché il punto dei pulsanti di scelta è quello di selezionare una o più opzioni, sarà sempre possibile creare almeno una coppia di pulsanti di scelta, mai un solo pulsante.

>[!CAUTION]
>
>Per rendere la selezione obbligatoria, è necessario creare un elenco a scelta multipla.

### Aggiunta di pulsanti singoli {#add-single-buttons}

Per aggiungere un pulsante di scelta a una pagina del modulo, andare al **[!UICONTROL Selection controls > Radio button]** menu nella barra degli strumenti dell&#39;editor pagina e scegliere una modalità di memorizzazione.

![](assets/s_ncs_admin_survey_radio_button_sample.png)

I pulsanti di scelta sono configurati in modo simile alle caselle di controllo (vedere [Aggiunta di caselle](#adding-checkboxes)di controllo). Tuttavia, non viene assegnato alcun valore se l&#39;opzione non è selezionata. Affinché diversi pulsanti siano interdipendenti, ossia selezionandone uno automaticamente deseleziona gli altri, è necessario memorizzarli nello stesso campo. Se non sono memorizzati nel database, la stessa variabile locale deve essere utilizzata per la memorizzazione temporanea. Consultate Campi [di memorizzazione](../../web/using/web-forms-answers.md#response-storage-fields)risposte.

### Aggiungere un elenco di pulsanti {#add-a-list-of-buttons}

Per aggiungere pulsanti di scelta tramite un elenco, scegliere il **[!UICONTROL Selection controls>Multiple choice]** menu nella barra degli strumenti dell’editor pagina.

![](assets/s_ncs_admin_survey_radio_button_sample2.png)

Aggiungete tutti i pulsanti di scelta quante sono le etichette. Il vantaggio di questa funzione è che è possibile importare valori da un campo esistente (nel caso di un campo dettagliato) e fare in modo che l&#39;utente scelga un&#39;opzione. Tuttavia, il layout dei pulsanti è meno flessibile.

>[!NOTE]
>
>I moduli Web non autorizzano la selezione di diversi valori. La selezione multipla può essere attivata solo per i moduli di tipo **Sondaggio** . Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/about-surveys.md).\
>È tuttavia possibile inserire un campo di **[!UICONTROL Multiple choice]** tipo in un&#39;applicazione Web; ma senza autorizzare la selezione di più valori: le opzioni offerte possono essere selezionate utilizzando i pulsanti di scelta.

## Aggiunta di griglie {#adding-grids}

Le griglie vengono utilizzate per progettare le pagine di voto nelle applicazioni Web. Questo consente di offrire elenchi di pulsanti di scelta per rispondere a un sondaggio o a un tipo di valutazione Moduli Web, come illustrato di seguito:

![](assets/s_ncs_admin_survey_vote_param.png)

Per utilizzare questo tipo di elemento in un modulo, creare una griglia semplice e aggiungere una riga per ciascun elemento da valutare.

![](assets/s_ncs_admin_survey_vote_sample.png)

Il numero di pulsanti di scelta in ciascuna riga della griglia corrisponde al numero di valori definiti nella griglia semplice.

![](assets/s_ncs_admin_survey_vote_ex.png)

È possibile selezionare una sola opzione per ogni linea della griglia.

>[!NOTE]
>
>Nel nostro esempio, l&#39;etichetta della griglia è nascosta. A questo scopo, andate alla **[!UICONTROL Advanced]** scheda, il **[!UICONTROL Label position]** display è definito come **[!UICONTROL Hidden]** . Vedere [Definizione della posizione delle etichette](../../web/using/defining-web-forms-layout.md#defining-the-position-of-labels).

## Aggiunta di date e numeri {#adding-dates-and-numbers}

Il contenuto dei campi modulo può essere formattato in modo che corrisponda ai dati memorizzati nel database o per soddisfare un requisito particolare. È possibile creare campi adatti per l&#39;immissione di numeri e date.

### Aggiunta di date {#adding-dates}

![](assets/s_ncs_admin_survey_date_calendar.png)

Per consentire all&#39;utente di immettere una data in una pagina del modulo, selezionare **[!UICONTROL Add input field > Date...]** nella barra degli strumenti o nell&#39;editor pagina.

Immettere un&#39;etichetta per il campo e configurare la modalità di memorizzazione dei dati.

![](assets/s_ncs_admin_survey_date_edit.png)

La sezione inferiore della finestra consente di selezionare i formati di data e ora per i valori memorizzati in questo campo.

![](assets/s_ncs_admin_survey_date_edit_values.png)

Potete anche scegliere di non visualizzare la data (o l’ora).

Le date possono essere selezionate tramite un calendario o caselle a discesa. È anche possibile inserirli direttamente nel campo, ma devono corrispondere al formato specificato nella schermata precedente.

>[!NOTE]
>
>Per impostazione predefinita, le date utilizzate nei moduli vengono immesse tramite un calendario. Per i moduli multilingue, verificare che i calendari siano disponibili in tutte le lingue utilizzate. See [Translating a web form](../../web/using/translating-a-web-form.md).

Tuttavia, in alcuni casi (ad esempio per le date di nascita) può essere più semplice utilizzare elenchi a discesa.

![](assets/s_ncs_admin_survey_date_list_select.png)

A questo scopo, fare clic sulla **[!UICONTROL Advanced]** scheda e scegliere la modalità di input utilizzando **[!UICONTROL Drop-down lists]**.

![](assets/s_ncs_admin_survey_date_selection.png)

Potete quindi impostare dei limiti per i valori offerti nell&#39;elenco.

![](assets/s_ncs_admin_survey_date_first_last_y.png)

### Aggiunta di numeri {#adding-numbers}

È possibile creare campi adatti per l&#39;immissione di numeri.

![](assets/s_ncs_admin_survey_number.png)

In un campo numerico, l&#39;utente può immettere solo numeri. Il controllo della voce viene applicato automaticamente quando la pagina viene approvata.

A seconda del campo in cui sono memorizzati i dati nel database, è possibile applicare una formattazione speciale o alcune restrizioni. Potete inoltre specificare i valori massimo e minimo. Questo tipo di campo è configurato come segue:

![](assets/s_ncs_admin_survey_number_edit.png)

Il valore predefinito è il valore visualizzato nel campo quando il modulo viene pubblicato. Può essere corretto dall’utente.

È possibile aggiungere un prefisso e/o un suffisso al campo numerico tramite la **[!UICONTROL Advanced]** scheda, come illustrato di seguito:

![](assets/s_ncs_admin_survey_number_ex_conf.png)

Nel modulo, il rendering sarà il seguente:

![](assets/s_ncs_admin_survey_number_ex.png)

## Caselle di controllo Iscrizione {#subscription-checkboxes}

Potete aggiungere controlli per consentire agli utenti di effettuare o annullare l’iscrizione a uno o più servizi di informazione (newsletter, avvisi, notifiche in tempo reale, ecc.). Per effettuare la sottoscrizione, l&#39;utente verifica il servizio corrispondente.

Per creare una casella di controllo per l’iscrizione, fate clic su **[!UICONTROL Advanced controls>Subscription]**.

![](assets/s_ncs_admin_survey_subscription_edit.png)

Indicate l’etichetta della casella di controllo e selezionate il servizio di informazioni interessato utilizzando la casella a **[!UICONTROL Service]** discesa.

>[!NOTE]
>
>I servizi di informazione sono descritti in [questa pagina](../../delivery/using/managing-subscriptions.md).

L&#39;utente si iscrive al servizio selezionando l&#39;opzione appropriata.

![](assets/s_ncs_admin_survey_subscribe.png)

>[!CAUTION]
>
>Se l’utente ha già effettuato la sottoscrizione a un servizio informazioni e la casella collegata a questo servizio non è selezionata al momento dell’approvazione del modulo, verrà annullata la sottoscrizione.

Esempi di iscrizioni e riferimenti sono disponibili in [questa sezione](../../web/using/about-surveys.md).

## Inserimento di un captcha {#inserting-a-captcha}

Lo scopo dei test **captcha** è impedire l&#39;uso fraudolento dei moduli Web.

>[!CAUTION]
>
>Se il modulo contiene più pagine, è necessario posizionare sempre il Captcha sull&#39;ultima pagina, subito prima della casella di archiviazione, per evitare qualsiasi elusione delle misure di sicurezza.

Per inserire un Captcha in un modulo, fare clic sul primo pulsante sulla barra degli strumenti e selezionare **[!UICONTROL Advanced controls>Captcha]**.

![](assets/s_ncs_admin_survey_add_captcha.png)

Immettere l&#39;etichetta del campo. Questa etichetta verrà visualizzata davanti all&#39;area di visualizzazione Captcha. È possibile modificare la posizione di questa etichetta nella **[!UICONTROL Advanced]** scheda.

![](assets/s_ncs_admin_survey_captcha_adv.png)

>[!NOTE]
>
>Per i controlli **[!UICONTROL captcha]** di tipo, non è necessario indicare un campo di memorizzazione o una variabile.

Il Captcha viene inserito nella pagina con un campo di input posizionato sotto l’elemento visivo. Questi due elementi sono inseparabili e sono considerati come un elemento singolo ai fini del layout di pagina (occupano una singola cella).

![](assets/s_ncs_admin_survey_captcha_sample.png)

Quando la pagina viene confermata, il campo di immissione viene visualizzato in rosso se il contenuto del Captcha non è stato immesso correttamente.

![](assets/s_ncs_admin_survey_captcha_error.png)

È possibile creare un messaggio di errore da visualizzare. A tal fine, utilizzate il **[!UICONTROL Personalize the message]** collegamento nella **[!UICONTROL General]** scheda.

![](assets/s_ncs_admin_survey_captcha_error_msg.png)

>[!NOTE]
>
>Le didascalie sono sempre lunghe 8 caratteri. Non è possibile modificare questo valore.

## Caricamento di un file {#uploading-a-file}

Potete aggiungere un campo di caricamento a una pagina. Questa funzionalità può essere utile per la condivisione di file Intranet, ad esempio.

![](assets/s_ncs_admin_survey_download_file.png)

Per inserire un campo di caricamento in una pagina del modulo, selezionate il **[!UICONTROL Advanced controls > File...]** menu nella barra degli strumenti dell’editor pagina.

Per impostazione predefinita, i file caricati sono memorizzati in file di risorse accessibili tramite il **[!UICONTROL Resources > Online > Public resources]** menu. È possibile utilizzare uno script per modificare questo comportamento. Questo script può utilizzare le funzioni definite nella documentazione [JSAPI di](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)Campaign, incluse quelle relative alla manipolazione dei file.

È possibile memorizzare il collegamento a questi file in una variabile locale o in un campo del database. Ad esempio, è possibile estendere lo schema del destinatario per aggiungere un collegamento a risorse basate su file.

>[!CAUTION]
>
>* Questo tipo di file deve essere riservato ai moduli con accesso protetto (utilizzando le credenziali).
>*  Adobe Campaign non controlla la dimensione o il tipo di risorsa caricata: si consiglia pertanto di utilizzare i campi di caricamento solo per i siti Intranet di tipo protetto.
>* Se diversi server sono collegati all&#39;istanza (architettura di bilanciamento del carico), è necessario assicurarsi che le chiamate al modulo Web arrivino sullo stesso server.
>* Queste implementazioni richiedono l&#39;assistenza del team  Adobe Campaign Consulting.

>



## Inserimento di una costante nascosta {#inserting-a-hidden-constant}

È possibile evidenziare un campo quando l&#39;utente passa una delle pagine del modulo. A tal fine, inserire una costante nella pagina e specificare il valore e la posizione di archiviazione.

Questo campo non è visibile all’utente, ma può essere utilizzato per arricchire i dati nel profilo utente.

Nell&#39;esempio seguente, il file di **origine** del profilo del destinatario viene compilato automaticamente ogni volta che un utente approva la pagina. La costante non viene visualizzata sulla pagina.

![](assets/s_ncs_admin_survey_constante.png)

