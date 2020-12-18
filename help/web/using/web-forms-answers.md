---
solution: Campaign Classic
product: campaign
title: Risposte ai moduli web
description: Risposte ai moduli web
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---


# Risposte ai moduli web{#web-forms-answers}

## Campi di archiviazione risposta {#response-storage-fields}

Le risposte ai moduli possono essere salvate in un campo del database o temporaneamente in una variabile locale. La modalità di memorizzazione delle risposte viene scelta durante la creazione del campo. Può essere modificato tramite il collegamento **[!UICONTROL Edit storage...]**.

Per ciascun campo di immissione in un modulo sono disponibili le seguenti opzioni di memorizzazione:

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   È possibile selezionare un campo del database: le risposte degli utenti saranno memorizzate in questo campo. Per ogni utente, viene salvato solo l&#39;ultimo valore immesso: viene aggiunto al relativo profilo: Fare riferimento a [Memorizzazione dei dati nel database](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   Se non si desidera memorizzare informazioni nel database, è possibile utilizzare una variabile. Le variabili locali possono essere dichiarate a monte. Fare riferimento a [Memorizzazione dei dati in una variabile locale](#storing-data-in-a-local-variable).

### Memorizzazione dei dati nel database {#storing-data-in-the-database}

Per salvare i dati in un campo esistente del database, fare clic sull&#39;icona **[!UICONTROL Edit expression]** e selezionarla dall&#39;elenco dei campi disponibili.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>Il documento di riferimento predefinito è lo schema **nms:Recipients**. Per visualizzarlo o sceglierne uno nuovo, selezionare il modulo dall&#39;elenco e fare clic sul pulsante **[!UICONTROL Properties]**.

### Memorizzazione dei dati in una variabile locale {#storing-data-in-a-local-variable}

È possibile utilizzare le variabili locali in modo che, anche se i dati non sono memorizzati nel database, possano essere riutilizzati sulla pagina o sulle altre pagine, ad esempio per posizionare le condizioni sulla visualizzazione di un campo o per personalizzare un messaggio.

Ciò significa che è possibile utilizzare il valore di un campo non salvato per autorizzare la visualizzazione di un gruppo di opzioni sulla pagina. Nella pagina seguente, il tipo di veicolo non è memorizzato nella banca dati:

![](assets/s_ncs_admin_survey_no_storage_variable.png)

È memorizzato in una variabile che deve essere selezionata al momento della creazione della casella di riepilogo o tramite il collegamento **[!UICONTROL Edit storage...]**.

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

È possibile visualizzare le variabili esistenti e crearne di nuove tramite il collegamento **[!UICONTROL Edit variables...]**. Fate clic sul pulsante **[!UICONTROL Add]** per creare una nuova variabile.

![](assets/s_ncs_admin_survey_add_a_variable.png)

La variabile aggiunta sarà disponibile nell&#39;elenco delle variabili locali al momento della creazione dei campi di input della pagina.

>[!NOTE]
>
>Per ciascun modulo è possibile creare variabili a monte. A tal fine, selezionare il modulo e fare clic sul pulsante **[!UICONTROL Properties]**. La scheda **[!UICONTROL Variables]** contiene le variabili locali per il modulo.

**Esempio di deposito locale con condizionamento**

Nell&#39;esempio precedente, il contenitore che include i dati relativi ai veicoli privati viene visualizzato solo se l&#39;opzione **[!UICONTROL Private]** è selezionata dall&#39;elenco a discesa, come indicato nella condizione di visibilità:

![](assets/s_ncs_admin_survey_add_a_condition.png)

Se l&#39;utente seleziona un veicolo privato, il modulo Web offre le seguenti opzioni:

![](assets/s_ncs_admin_survey_no_storage_conda.png)

Il contenitore che contiene i dati relativi ai veicoli commerciali sarà visualizzato se l&#39;opzione Professional è selezionata, come espresso nella condizione di visibilità:

![](assets/s_ncs_admin_survey_view_a_condition.png)

Ciò significa che, se l&#39;utente seleziona un veicolo commerciale, il modulo offre le seguenti opzioni:

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## Utilizzo delle informazioni raccolte {#using-collected-information}

Per ciascun modulo, le risposte fornite possono essere riutilizzate nei campi o nelle etichette. Devono essere utilizzate le seguenti sintassi:

* Per un contenuto memorizzato in un campo del database:

   ```
   <%=ctx.recipient.@field name%
   ```

* Per un contenuto memorizzato in una variabile locale:

   ```
   <%= ctx.vars.variable name %
   ```

* Per un contenuto memorizzato in un campo di testo HTML:

   ```
   <%== HTML field name %
   ```

   >[!NOTE]
   >
   >A differenza degli altri campi per i quali i caratteri `<%=` vengono sostituiti con caratteri escape, il contenuto HTML viene salvato come accade utilizzando la sintassi `<%==`.

## Salvataggio delle risposte dei moduli Web {#saving-web-forms-answers}

Per salvare le informazioni raccolte nelle pagine di un modulo, è necessario inserire una casella di archiviazione nel diagramma.

![](assets/s_ncs_admin_survey_save_box.png)

Questa casella può essere utilizzata in due modi:

* Se l&#39;accesso al modulo Web è effettuato tramite un collegamento inviato in un&#39;e-mail e se l&#39;utente che accede all&#39;applicazione è già presente nel database, è possibile selezionare l&#39;opzione **[!UICONTROL Update the preloaded record]**. Per ulteriori informazioni, vedere [Distribuzione di un modulo tramite e-mail](../../web/using/publishing-a-web-form.md#delivering-a-form-via-email).

   In questo caso,  Adobe Campaign utilizza la chiave primaria crittografata del profilo utente, un identificatore univoco assegnato a ciascun profilo da  Adobe Campaign. È necessario configurare le informazioni per il precaricamento tramite la casella di precaricamento. Per ulteriori informazioni, vedere [Precaricamento dei dati del modulo](../../web/using/publishing-a-web-form.md#pre-loading-the-form-data).

   >[!CAUTION]
   >
   >Questa opzione sostituisce i dati utente, incluso l&#39;indirizzo e-mail se è presente un campo in cui immetterlo. Non può essere utilizzato per creare nuovi profili e richiede l&#39;uso di una casella di precaricamento nel modulo.

* Per arricchire i dati dei destinatari nel database, modificare la casella di memorizzazione e selezionare la chiave di riconciliazione. Per uso interno (in genere un sistema Intranet) o per un modulo utilizzato per creare nuovi profili, ad esempio, è possibile selezionare i campi di riconciliazione. La casella include tutti i campi del database utilizzati nelle varie pagine dell&#39;applicazione Web:

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

Per impostazione predefinita, i dati vengono importati nel database tramite un&#39;operazione **[!UICONTROL Update or insertion]**: se esiste nel database, l’elemento viene aggiornato (ad esempio, la newsletter selezionata o l’indirizzo e-mail immesso). Se non esiste, le informazioni vengono aggiunte.

Potete tuttavia modificare questo comportamento. A questo scopo, selezionate la radice dell&#39;elemento e selezionate l&#39;operazione da eseguire dall&#39;elenco a discesa:

![](assets/s_ncs_admin_survey_save_operation.png)

Potete selezionare una cartella di ricerca per la riconciliazione e la cartella di creazione per i nuovi profili. Se questi campi sono vuoti, la ricerca e la creazione dei profili vengono effettuate nella cartella predefinita dell&#39;operatore.

>[!NOTE]
>
>Le operazioni possibili sono: **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>La cartella predefinita dell&#39;operatore è la prima cartella per la quale l&#39;operatore dispone dell&#39;autorizzazione di scrittura.\
>Fai riferimento a [questa sezione](../../platform/using/access-management.md).

