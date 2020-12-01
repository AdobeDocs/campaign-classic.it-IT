---
solution: Campaign Classic
product: campaign
title: Definizione delle proprietà dei moduli web
description: Definizione delle proprietà dei moduli web
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 21219f4a85a0caec4531acda33ab8bba5c7605d6
workflow-type: tm+mt
source-wordcount: '1205'
ht-degree: 1%

---


# Definizione delle proprietà dei moduli web{#defining-web-forms-properties}

I moduli Web sono completamente configurabili e personalizzabili per soddisfare le tue esigenze. I parametri devono essere inseriti nella finestra delle proprietà.

La finestra delle proprietà è accessibile tramite il **[!UICONTROL Properties]** pulsante nella barra degli strumenti del modulo Web. Questa finestra consente di accedere a una serie di impostazioni specifiche del modulo Web. Alcune impostazioni possono derivare dalla configurazione del modello.

![](assets/s_ncs_admin_survey_properties_general.png)

## Proprietà modulo generali {#overall-form-properties}

Nella **[!UICONTROL General]** scheda della finestra delle proprietà è possibile modificare l&#39; **etichetta** del modulo. Si consiglia vivamente di non modificare il nome **** interno.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

Il modello di modulo viene scelto durante la creazione del modulo. Non può essere modificato in seguito. Per ulteriori informazioni sulla creazione e la gestione dei modelli di modulo, vedere [Uso di un modello](../../web/using/using-a-web-form-template.md)di modulo Web.

## Archiviazione dati modulo {#form-data-storage}

Per impostazione predefinita, i campi dei moduli Web sono memorizzati nella tabella dei destinatari. È possibile modificare la tabella utilizzata selezionando una nuova tabella dal **[!UICONTROL Document type]** campo. L&#39; **[!UICONTROL Zoom]** icona consente di visualizzare il contenuto della tabella selezionata.

Per impostazione predefinita, le risposte sono memorizzate nella tabella **Risposta a un modulo** destinatario.

## Configurazione di una pagina di errore {#setting-up-an-error-page}

È possibile configurare una pagina di errore: questa pagina verrà visualizzata in caso di errori durante l&#39;esecuzione del modulo.

La pagina di errore è definita nella scheda corrispondente della finestra delle proprietà del modulo.

Per impostazione predefinita, vengono visualizzate le informazioni seguenti:

![](assets/s_ncs_admin_survey_default_error_page.png)

Il contenuto delle stringhe visualizzate è definito nella **[!UICONTROL Error page]** scheda della finestra delle proprietà. La **[!UICONTROL HTML]** scheda visualizza il rendering e la **[!UICONTROL Texts]** scheda consente di modificare le stringhe di testo e aggiungere del testo, se necessario:

![](assets/s_ncs_admin_survey_error_page.png)

## Localizzazione del modulo {#form-localization}

La **[!UICONTROL Localization]** scheda consente di selezionare le lingue di progettazione e visualizzazione del modulo Web.

See [Translating a web form](../../web/using/translating-a-web-form.md).

## Esplorazione e rendering dei moduli {#form-browsing-and-rendering}

La **[!UICONTROL Rendering]** scheda consente di definire il tipo di esplorazione tra le pagine del modulo Web e il modello di rendering utilizzato.

È possibile scegliere di spostarsi tramite collegamenti o pulsanti.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Per impostazione predefinita, i pulsanti sono gli elementi di navigazione. Consentono di eseguire le azioni seguenti:

* Approva la pagina corrente e visualizza la pagina successiva facendo clic su **[!UICONTROL Next]**. Questo pulsante viene visualizzato su tutte le pagine tranne l&#39;ultima.
* Visualizzare la pagina precedente facendo clic su **[!UICONTROL Previous]**. Questo pulsante viene visualizzato su tutte le pagine tranne la prima.
* Salvare le risposte del modulo facendo clic sul **[!UICONTROL Approve]** pulsante . Questo pulsante è visibile solo nell’ultima pagina.

Questi elementi vengono visualizzati nella parte inferiore di ogni pagina. Le loro posizioni possono essere cambiate. A tal fine, è necessario modificare il foglio di stile.

>[!NOTE]
>
>È possibile nascondere il **[!UICONTROL Previous]** pulsante su alcune pagine. Per eseguire questa operazione, passare alla pagina interessata e selezionare l&#39; **[!UICONTROL Disallow returning to the previous page]** opzione. Questa opzione è accessibile quando è selezionato il livello principale della struttura delle pagine.

Il **[!UICONTROL Template]** campo della **[!UICONTROL Rendering]** scheda consente di selezionare un tema tra quelli disponibili.

I temi vengono salvati nel **[!UICONTROL Administration>Configuration>Form rendering]** nodo della struttura ad albero. Vedere [Selezione del modello di rendering del modulo](../../web/using/form-rendering.md#selecting-the-form-rendering-template)

Nella parte inferiore della finestra delle proprietà viene visualizzato un rendering di esempio. L&#39; **[!UICONTROL Edit link]** icona consente di visualizzare la configurazione del tema selezionato.

![](assets/s_ncs_admin_survey_properties_render.png)

## Testi nel modulo {#texts-in-the-form}

La **[!UICONTROL Page]** scheda consente di definire il contenuto dell&#39;intestazione e del piè di pagina del modulo. Vedere [Definizione di intestazioni e piè di pagina](../../web/using/form-rendering.md#defining-headers-and-footers).

Consente inoltre di gestire le traduzioni. See [Translating a web form](../../web/using/translating-a-web-form.md).

## Accessibilità del modulo {#accessibility-of-the-form}

Un modulo Web è accessibile agli utenti se lo è **[!UICONTROL Online]** e se la data corrente si trova entro il periodo di validità. Lo stato del modulo viene modificato durante la fase di pubblicazione (vedere [Pubblicazione di un modulo](../../web/using/publishing-a-web-form.md#publishing-a-form)). Lo stato viene visualizzato nella sezione **Progetto** della **[!UICONTROL General]** scheda della finestra delle proprietà.

Il periodo di validità va dalla **[!UICONTROL Start]** data alla **[!UICONTROL End date]**. Se in questi campi non sono specificate date, il modulo ha validità permanente.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>Se il modulo è chiuso e il periodo di validità non è stato raggiunto o è scaduto, o se è stato chiuso dall&#39;operatore Adobe Campaign , viene visualizzato un messaggio quando l&#39;utente tenta di accedervi. Puoi personalizzare il messaggio facendo clic su **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## Controllo accesso modulo {#form-access-control}

Per impostazione predefinita, l&#39;accesso ai moduli Web viene eseguito in modalità anonima: a tutti gli operatori che accedono al modulo vengono assegnati diritti di operatore WebApp.

È possibile abilitare il controllo di accesso per la visualizzazione del modulo, ad esempio per la distribuzione di un modulo su un sito Intranet, al fine di autenticare gli utenti. A tal fine, visualizzare la **[!UICONTROL Properties]** finestra del modulo interessato e fare clic sull&#39; **[!UICONTROL Enable access control]** opzione, come illustrato di seguito:

![](assets/s_ncs_admin_survey_access_ctrl.png)

Quando si accede alla pagina, viene visualizzato il seguente modulo di autenticazione:

![](assets/s_ncs_admin_survey_access_login.png)

Login e password sono quelli utilizzati dagli operatori  Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/access-management.md).

L&#39; **[!UICONTROL Use a specific account]** opzione consente di limitare l&#39;autorizzazione di lettura o scrittura dell&#39;operatore che accede al modulo. Utilizzare la casella a discesa per selezionare un operatore o un gruppo di operatori che si occuperà di concedere tali autorizzazioni.

![](assets/s_ncs_admin_survey_access_op_select.png)

## Parametri URL modulo {#form-url-parameters}

È possibile aggiungere parametri aggiuntivi nell&#39;URL di un modulo per personalizzare il contenuto e inizializzare un contesto (lingua, ID destinatario crittografato, società, formula calcolata memorizzata in una variabile, ecc.). Questo consente di accedere a un modulo tramite diversi URL e di personalizzare il contenuto della pagina in base al valore dei parametri indicati nell’URL.

Per impostazione predefinita,  Adobe Campaign offre parametri per la visualizzazione dell&#39;anteprima del modulo e per il controllo degli errori. È possibile creare nuove impostazioni collegate al modulo, che possono utilizzare i valori di un campo nel database o di una variabile locale.

## Parametri standard {#standard-parameters}

Per impostazione predefinita sono disponibili i seguenti parametri:

* **id** per indicare l’identificatore crittografato.
* **lang** per modificare la lingua di visualizzazione.
* **origine** per specificare l&#39;origine del convenuto.
* **_uuid** consente la visualizzazione del modulo prima della pubblicazione e il tracciamento degli errori. Questo parametro è per uso interno (creazione e debug): quando si accede al modulo Web tramite questo URL, i record creati non vengono presi in considerazione nel tracciamento (rapporti). L&#39;origine viene forzata al **[!UICONTROL Adobe Campaign]** valore.

   Viene utilizzato con i parametri **_preview** e/o **_debug**:

   **_anteprima** per visualizzare l&#39;ultima versione salvata. Questo parametro deve essere utilizzato solo nella fase di prova.

   **_debug** per visualizzare la traccia dei dati immessi o calcolati nelle pagine del modulo. Viene utilizzato per ottenere ulteriori informazioni sugli errori, inclusa una volta che il modulo è stato pubblicato.

   >[!CAUTION]
   >
   >Quando il modulo viene visualizzato tramite un URL con il parametro **_uuid** , il valore del **[!UICONTROL origin]** parametro viene forzato a **Adobe Campaign**.

## Aggiunta di parametri {#adding-parameters}

I parametri possono essere aggiunti tramite la **[!UICONTROL Parameters...]** scheda nella finestra Proprietà del modulo. Possono essere resi obbligatori, come indicato di seguito:

![](assets/s_ncs_admin_survey_properties_param.png)

È necessario specificare una posizione di memorizzazione dalla quale verrà recuperato il valore del parametro. A questo scopo, selezionare una delle opzioni di memorizzazione, quindi fare clic sulla **[!UICONTROL Storage]** scheda per selezionare il campo o la variabile interessata. Le opzioni di memorizzazione sono dettagliate nei campi [di archiviazione](../../web/using/web-forms-answers.md#response-storage-fields)Risposta.

Lo stato dell&#39;utente che ha risposto (0, 1 o qualsiasi altro valore) può quindi essere aggiunto all&#39;URL per l&#39;accesso al modulo. Queste informazioni possono essere riutilizzate nelle pagine del modulo o in una casella di prova. Le pagine visualizzate possono essere condizionate in base al valore del contesto, come mostrato di seguito:

1. Home page per i clienti (**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. Pagina iniziale per potenziali clienti (**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. Home page per altri profili (ad esempio, **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

Per configurare questo modulo, creare una casella di prova e posizionarla all’inizio del diagramma, come illustrato di seguito:

![](assets/s_ncs_admin_survey_test.png)

La casella di test consente di configurare le condizioni di sequenza delle pagine:

![](assets/s_ncs_admin_survey_test_box.png)

