---
product: campaign
title: Definire le proprietà dei moduli web
description: Definire le proprietà dei moduli web
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Forms
exl-id: 37aaaa03-0656-4a9b-bcae-74de33e3737b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1220'
ht-degree: 1%

---

# Definizione delle proprietà dei moduli web{#defining-web-forms-properties}



Puoi configurare e personalizzare completamente i moduli web per soddisfare le tue esigenze. I parametri devono essere immessi nella finestra delle proprietà.

La finestra delle proprietà è accessibile tramite **[!UICONTROL Properties]** nella barra degli strumenti del modulo Web. Questa finestra consente di accedere a una serie di impostazioni specifiche del modulo Web. Alcune impostazioni potrebbero derivare dalla configurazione del modello.

![](assets/s_ncs_admin_survey_properties_general.png)

## Proprietà modulo generali {#overall-form-properties}

In **[!UICONTROL General]** della finestra delle proprietà, è possibile modificare la scheda **Etichetta** del modulo. Si consiglia vivamente di non modificare **Nome interno**.

![](assets/s_ncs_admin_survey_properties_general_tab.png)

Il modello di modulo viene scelto durante la creazione del modulo. Non può essere modificato in un secondo momento. Per ulteriori informazioni sulla creazione e la gestione dei modelli di modulo, fare riferimento a [Utilizzo di un modello di modulo web](using-a-web-form-template.md).

## Archiviazione dati modulo {#form-data-storage}

Per impostazione predefinita, i campi dei moduli Web vengono memorizzati nella tabella dei destinatari. È possibile modificare la tabella utilizzata selezionando una nuova tabella dal menu **[!UICONTROL Document type]** campo. Il **[!UICONTROL Zoom]** consente di visualizzare il contenuto della tabella selezionata.

Per impostazione predefinita, le risposte sono memorizzate in **Rispondere a un modulo destinatario** tabella.

## Impostazione di una pagina di errore {#setting-up-an-error-page}

Puoi configurare una pagina di errore: questa pagina verrà visualizzata in caso di errori durante l’esecuzione del modulo.

La pagina di errore viene definita nella scheda corrispondente della finestra delle proprietà del modulo.

Per impostazione predefinita, vengono visualizzate le seguenti informazioni:

![](assets/s_ncs_admin_survey_default_error_page.png)

Il contenuto delle stringhe visualizzate è definito nel **[!UICONTROL Error page]** della finestra delle proprietà. Il **[!UICONTROL HTML]** visualizza il rendering e il **[!UICONTROL Texts]** La scheda consente di modificare le stringhe di testo e aggiungere testo, se necessario:

![](assets/s_ncs_admin_survey_error_page.png)

## Localizzazione dei moduli {#form-localization}

Il **[!UICONTROL Localization]** Questa scheda consente di selezionare le lingue di progettazione e visualizzazione per il modulo Web.

Consulta [Traduzione di un modulo web](translating-a-web-form.md).

## Esplorazione e rendering dei moduli {#form-browsing-and-rendering}

Il **[!UICONTROL Rendering]** Questa scheda consente di definire il tipo di esplorazione tra le pagine del modulo Web e il modello di rendering utilizzato.

Puoi scegliere di navigare tramite collegamenti o pulsanti.

![](assets/s_ncs_admin_survey_wz_02_navig_type.png)

Per impostazione predefinita, i pulsanti sono gli elementi di navigazione. Consentono di eseguire le azioni seguenti:

* Approvare la pagina corrente e visualizzare la pagina successiva facendo clic su **[!UICONTROL Next]**. Questo pulsante viene visualizzato su tutte le pagine, tranne l’ultima.
* Visualizzare la pagina precedente facendo clic su **[!UICONTROL Previous]**. Questo pulsante viene visualizzato in tutte le pagine, tranne la prima.
* Salvare le risposte del modulo facendo clic sul pulsante **[!UICONTROL Approve]** pulsante. Questo pulsante viene visualizzato solo nell&#39;ultima pagina.

Questi elementi vengono visualizzati nella parte inferiore di ogni pagina. Le loro posizioni possono essere cambiate. A tale scopo, è necessario modificare il foglio di stile.

>[!NOTE]
>
>È possibile nascondere **[!UICONTROL Previous]** su alcune pagine. A questo scopo, vai alla pagina interessata e controlla **[!UICONTROL Disallow returning to the previous page]** opzione. Questa opzione è accessibile quando si seleziona la directory principale della struttura ad albero della pagina.

Il **[!UICONTROL Template]** campo del **[!UICONTROL Rendering]** Questa scheda ti consente di selezionare un tema tra quelli disponibili.

I temi vengono salvati in **[!UICONTROL Administration>Configuration>Form rendering]** dell&#39;albero. Consulta [Selezione del modello di rendering del modulo](form-rendering.md#selecting-the-form-rendering-template)

Nella parte inferiore della finestra delle proprietà viene visualizzato un rendering di esempio. Il **[!UICONTROL Edit link]** consente di visualizzare la configurazione per il tema selezionato.

![](assets/s_ncs_admin_survey_properties_render.png)

## Testi nel modulo {#texts-in-the-form}

Il **[!UICONTROL Page]** Questa scheda ti consente di definire il contenuto dell’intestazione e del piè di pagina del modulo. Consulta [Definizione di intestazioni e piè di pagina](form-rendering.md#defining-headers-and-footers).

Consente inoltre di gestire le traduzioni. Consulta [Traduzione di un modulo web](translating-a-web-form.md).

## Accessibilità del modulo {#accessibility-of-the-form}

Un modulo web è accessibile agli utenti se è **[!UICONTROL Online]** e se la data corrente rientra nel relativo periodo di validità. Lo stato del modulo viene modificato durante la fase di pubblicazione (vedere [Pubblicazione di un modulo](publishing-a-web-form.md#publishing-a-form)). Lo stato viene visualizzato nel **Progetto** sezione del **[!UICONTROL General]** della finestra delle proprietà.

Il periodo di validità inizia dal **[!UICONTROL Start]** data a **[!UICONTROL End date]**. Se in questi campi non è specificata alcuna data, il modulo ha validità permanente.

![](assets/s_ncs_admin_survey_properties_date.png)

>[!NOTE]
>
>Se il modulo è chiuso e quindi il periodo di validità non è stato raggiunto o è scaduto, oppure se è stato chiuso dall’operatore Adobe Campaign, quando l’utente tenta di accedervi viene visualizzato un messaggio. Puoi personalizzare questo messaggio facendo clic su **[!UICONTROL Personalize the message displayed if the form is closed...]**.

## Controllo dell’accesso ai moduli {#form-access-control}

Per impostazione predefinita, l’accesso ai moduli web viene eseguito in modalità anonima: a tutti gli operatori che accedono al modulo vengono assegnati diritti di operatore WebApp.

È possibile abilitare il controllo degli accessi per la visualizzazione del modulo, ad esempio durante la consegna di un modulo in un sito Intranet, al fine di autenticare gli utenti. A tale scopo, visualizzare **[!UICONTROL Properties]** del modulo in questione e fare clic sul pulsante **[!UICONTROL Enable access control]** come mostrato di seguito:

![](assets/s_ncs_admin_survey_access_ctrl.png)

Quando si accede alla pagina, viene visualizzato il seguente modulo di autenticazione:

![](assets/s_ncs_admin_survey_access_login.png)

L’accesso e la password sono quelli utilizzati dagli operatori Adobe Campaign. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../platform/using/access-management.md).

Il **[!UICONTROL Use a specific account]** consente di limitare l&#39;autorizzazione di lettura o scrittura dell&#39;operatore che accede al modulo. Utilizza la casella a discesa per selezionare un operatore o un gruppo di operatori che saranno responsabili della concessione di queste autorizzazioni.

![](assets/s_ncs_admin_survey_access_op_select.png)

## Parametri URL modulo {#form-url-parameters}

Puoi aggiungere parametri aggiuntivi nell’URL di un modulo per personalizzarne il contenuto e inizializzare un contesto (lingua, ID destinatario crittografato, società, formula calcolata memorizzata in una variabile, ecc.). Ciò ti consente di accedere a un modulo tramite diversi URL diversi e di personalizzare il contenuto della pagina in base al valore dei parametri indicati nell’URL.

Per impostazione predefinita, Adobe Campaign offre parametri per la visualizzazione in anteprima del modulo e il controllo degli errori. È possibile creare nuove impostazioni collegate al modulo, che possono utilizzare i valori di un campo del database o di una variabile locale.

## Parametri standard {#standard-parameters}

Per impostazione predefinita sono disponibili i seguenti parametri:

* **id** per indicare l&#39;identificatore crittografato.
* **lang** per modificare la lingua di visualizzazione.
* **origine** specificare l&#39;origine del convenuto.
* **_uuid** consente la visualizzazione dei moduli prima della pubblicazione e il tracciamento degli errori. Questo parametro è per uso interno (creazione ed debug): quando accedi al modulo Web tramite questo URL, i record creati non vengono presi in considerazione nel tracciamento (report). L’origine è forzata a **[!UICONTROL Adobe Campaign]** valore.

  Viene utilizzato con **_anteprima** parametri e/o **_debug**:

  **_anteprima** per visualizzare l&#39;ultima versione salvata. Questo parametro deve essere utilizzato solo nella fase di test.

  **_debug** per visualizzare la traccia dei dati immessi o calcolati nelle pagine del modulo. Viene utilizzato per ottenere ulteriori informazioni sugli errori, anche dopo la pubblicazione del modulo.

  >[!CAUTION]
  >
  >Quando il modulo viene visualizzato tramite un URL con **_uuid** parametro, il valore della proprietà **[!UICONTROL origin]** il parametro è forzato a **Adobe Campaign**.

## Aggiunta di parametri {#adding-parameters}

I parametri possono essere aggiunti tramite il **[!UICONTROL Parameters...]** nella finestra Proprietà della maschera. Possono essere rese obbligatorie, come illustrato di seguito:

![](assets/s_ncs_admin_survey_properties_param.png)

Specificare un percorso di archiviazione da cui recuperare il valore del parametro. A tale scopo, selezionare una delle opzioni di archiviazione e fare clic sul pulsante **[!UICONTROL Storage]** per selezionare il campo o la variabile interessata. Le opzioni di archiviazione sono descritte in [Campi di archiviazione delle risposte](web-forms-answers.md#response-storage-fields).

Lo stato del partecipante (0, 1 o qualsiasi altro valore) può quindi essere aggiunto all’URL per accedere al modulo. Queste informazioni possono essere riutilizzate nelle pagine del modulo o in una casella di prova. Le pagine visualizzate possono essere condizionate in base al valore del contesto, come illustrato di seguito:

1. Home page per i clienti (**status=1**):

   ![](assets/s_ncs_admin_survey_test_client.png)

1. Home page per i potenziali clienti (**status=0**):

   ![](assets/s_ncs_admin_survey_test_prospect.png)

1. Home page per altri profili (ad es. **status=12**):

   ![](assets/s_ncs_admin_survey_test_other.png)

Per configurare questo modulo, creare una casella di prova e posizionarla all&#39;inizio del diagramma, come illustrato di seguito:

![](assets/s_ncs_admin_survey_test.png)

La casella di test consente di configurare le condizioni di sequenza della pagina:

![](assets/s_ncs_admin_survey_test_box.png)
