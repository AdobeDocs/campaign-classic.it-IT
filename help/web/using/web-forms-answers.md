---
product: campaign
title: Risposte ai moduli web
description: Risposte ai moduli web
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Web Forms
exl-id: 5d48bb27-1884-47f1-acb7-dff5113565bc
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '872'
ht-degree: 0%

---

# Risposte ai moduli web{#web-forms-answers}


## Campi di archiviazione delle risposte {#response-storage-fields}

Le risposte ai moduli possono essere salvate temporaneamente in un campo del database o in una variabile locale. La modalità di archiviazione delle risposte viene scelta durante la creazione del campo. Può essere modificato tramite **[!UICONTROL Edit storage...]** collegamento.

Per ogni campo di input di un modulo sono disponibili le seguenti opzioni di archiviazione:

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

  È possibile selezionare un campo del database: le risposte degli utenti verranno memorizzate in questo campo. Per ogni utente, viene salvato solo l’ultimo valore inserito: viene aggiunto al suo profilo: fai riferimento a [Memorizzazione dei dati nel database](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

  Se non si desidera memorizzare informazioni nel database, è possibile utilizzare una variabile. Le variabili locali possono essere dichiarate a monte. Fai riferimento a [Memorizzazione dei dati in una variabile locale](#storing-data-in-a-local-variable).

### Memorizzazione dei dati nel database {#storing-data-in-the-database}

Per salvare i dati in un campo esistente del database, fare clic sul pulsante **[!UICONTROL Edit expression]** e selezionarla dall&#39;elenco dei campi disponibili.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>Il documento di riferimento predefinito è **nms:destinatario** schema. Per visualizzarlo o sceglierne uno nuovo, selezionare il modulo dall&#39;elenco e fare clic sul pulsante **[!UICONTROL Properties]** pulsante.

### Memorizzazione dei dati in una variabile locale {#storing-data-in-a-local-variable}

È possibile utilizzare le variabili locali in modo che, anche se i dati non sono memorizzati nel database, possano essere riutilizzati nella pagina o nelle altre pagine, ad esempio per inserire condizioni nella visualizzazione di un campo o per personalizzare un messaggio.

Ciò significa che puoi utilizzare il valore di un campo non salvato per autorizzare la visualizzazione di un gruppo di opzioni sulla pagina. Nella pagina seguente, il tipo di veicolo non è memorizzato nella banca dati:

![](assets/s_ncs_admin_survey_no_storage_variable.png)

Viene memorizzato in una variabile che deve essere selezionata al momento della creazione della casella a discesa o tramite **[!UICONTROL Edit storage...]** collegamento.

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

Puoi visualizzare le variabili esistenti e crearne di nuove tramite **[!UICONTROL Edit variables...]** collegamento. Fai clic su **[!UICONTROL Add]** per creare una nuova variabile.

![](assets/s_ncs_admin_survey_add_a_variable.png)

La variabile aggiunta sarà disponibile nell’elenco delle variabili locali quando vengono creati i campi di input della pagina.

>[!NOTE]
>
>Per ogni modulo è possibile creare variabili a monte. A questo scopo, seleziona il modulo e fai clic sul pulsante **[!UICONTROL Properties]** pulsante. Il **[!UICONTROL Variables]** contiene le variabili locali per il modulo.

**Esempio di stoccaggio locale con condizionamento**

Nell’esempio precedente, il contenitore che include i dati relativi ai veicoli privati viene visualizzato solo se il **[!UICONTROL Private]** L&#39;opzione è selezionata dall&#39;elenco a discesa, come indicato nella condizione di visibilità:

![](assets/s_ncs_admin_survey_add_a_condition.png)

Se l’utente seleziona un veicolo privato, il modulo web offre le seguenti opzioni:

![](assets/s_ncs_admin_survey_no_storage_conda.png)

Il contenitore contenente i dati relativi ai veicoli commerciali sarà visualizzato se si seleziona l&#39;opzione Professionista, come espresso nella condizione di visibilità:

![](assets/s_ncs_admin_survey_view_a_condition.png)

Ciò significa che, se l’utente seleziona un veicolo commerciale, il modulo offre le seguenti opzioni:

![](assets/s_ncs_admin_survey_no_storage_condb.png)

## Utilizzo delle informazioni raccolte {#using-collected-information}

Per ogni modulo, le risposte fornite possono essere riutilizzate nei campi o nelle etichette. Devono essere utilizzate le seguenti sintassi:

* Per un contenuto memorizzato in un campo del database:

  ```
  <%=ctx.recipient.@field name%
  ```

* Per un contenuto archiviato in una variabile locale:

  ```
  <%= ctx.vars.variable name %
  ```

* Per un contenuto memorizzato in un campo di testo HTML:

  ```
  <%== HTML field name %
  ```

  >[!NOTE]
  >
  >A differenza degli altri campi per i quali `<%=` vengono sostituiti con caratteri di escape, il contenuto del HTML viene salvato così come è utilizzando `<%==` sintassi.

## Salvataggio delle risposte ai moduli Web {#saving-web-forms-answers}

Per salvare le informazioni raccolte nelle pagine di un modulo, è necessario inserire una casella di memorizzazione nel diagramma.

![](assets/s_ncs_admin_survey_save_box.png)

Esistono due modi per utilizzare questa casella:

* Se il modulo Web è accessibile tramite un collegamento inviato in un messaggio di posta elettronica e l&#39;utente che accede all&#39;applicazione si trova già nel database, è possibile controllare **[!UICONTROL Update the preloaded record]** opzione. Per ulteriori informazioni, consulta [Consegna di un modulo tramite e-mail](publishing-a-web-form.md#delivering-a-form-via-email).

  In questo caso, Adobe Campaign utilizza la chiave primaria crittografata del profilo utente, un identificatore univoco assegnato a ciascun profilo da Adobe Campaign. È necessario configurare le informazioni da precaricare tramite la casella di precaricamento. Per ulteriori informazioni, consulta [Precaricamento dei dati del modulo](publishing-a-web-form.md#pre-loading-the-form-data).

  >[!CAUTION]
  >
  >Questa opzione sostituisce i dati utente, incluso l’indirizzo e-mail se è presente un campo in cui immetterlo. Non può essere utilizzato per creare nuovi profili e richiede l’utilizzo di una casella di precaricamento nel modulo.

* Per arricchire i dati dei destinatari nel database, modifica la casella di archiviazione e seleziona la chiave di riconciliazione. Per uso interno (in genere un sistema Intranet) o per un modulo utilizzato per creare nuovi profili, ad esempio, puoi selezionare i campi di riconciliazione. Nella casella sono disponibili tutti i campi del database utilizzati nelle varie pagine dell&#39;applicazione Web:

  ![](assets/s_ncs_admin_survey_save_box_edit.png)

Per impostazione predefinita, i dati vengono importati nel database da un **[!UICONTROL Update or insertion]** operazione: se esiste nel database, l’elemento viene aggiornato (ad esempio, la newsletter selezionata o l’indirizzo e-mail inserito). Se non esiste, le informazioni vengono aggiunte.

Tuttavia, è possibile modificare questo comportamento. A questo scopo, seleziona la radice dell’elemento e l’operazione da eseguire dall’elenco a discesa:

![](assets/s_ncs_admin_survey_save_operation.png)

Puoi selezionare una cartella di ricerca per la riconciliazione e la cartella di creazione per i nuovi profili. Se questi campi sono vuoti, i profili vengono cercati e creati nella cartella predefinita dell’operatore.

>[!NOTE]
>
>Le operazioni possibili sono: **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>La cartella predefinita dell&#39;operatore è la prima cartella per la quale l&#39;operatore dispone dell&#39;autorizzazione di scrittura.\
>Fai riferimento a [questa sezione](../../platform/using/access-management.md).
