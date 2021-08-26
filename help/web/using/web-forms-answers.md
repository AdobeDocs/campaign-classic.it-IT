---
product: campaign
title: Risposte ai moduli web
description: Risposte ai moduli web
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 5d48bb27-1884-47f1-acb7-dff5113565bc
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '860'
ht-degree: 1%

---

# Risposte ai moduli web{#web-forms-answers}

![](../../assets/common.svg)

## Campi di archiviazione della risposta {#response-storage-fields}

Le risposte ai moduli possono essere salvate in un campo del database o temporaneamente in una variabile locale. La modalità di archiviazione delle risposte viene scelta durante la creazione del campo. Può essere modificato tramite il collegamento **[!UICONTROL Edit storage...]** .

Per ciascun campo di input di un modulo sono disponibili le seguenti opzioni di archiviazione:

![](assets/s_ncs_admin_survey_select_storage.png)

* **[!UICONTROL Edit a recipient]**

   È possibile selezionare un campo del database: le risposte degli utenti verranno memorizzate in questo campo. Per ogni utente, viene salvato solo l’ultimo valore immesso: viene aggiunto al loro profilo: Fare riferimento a [Memorizzazione dei dati nel database](#storing-data-in-the-database).

* **[!UICONTROL Variable]**

   Se non si desidera memorizzare le informazioni nel database, è possibile utilizzare una variabile. Le variabili locali possono essere dichiarate a monte. Fare riferimento a [Memorizzazione di dati in una variabile locale](#storing-data-in-a-local-variable).

### Memorizzazione dei dati nel database {#storing-data-in-the-database}

Per salvare i dati in un campo esistente del database, fai clic sull&#39;icona **[!UICONTROL Edit expression]** e selezionala dall&#39;elenco dei campi disponibili.

![](assets/s_ncs_admin_survey_storage_type1.png)

>[!NOTE]
>
>Il documento di riferimento predefinito è lo schema **nms:recipient** . Per visualizzarlo o sceglierne uno nuovo, selezionare il modulo dall&#39;elenco e fare clic sul pulsante **[!UICONTROL Properties]**.

### Memorizzazione di dati in una variabile locale {#storing-data-in-a-local-variable}

È possibile utilizzare variabili locali in modo che, anche se i dati non sono memorizzati nel database, possano essere riutilizzati nella pagina o nelle altre pagine, ad esempio per inserire condizioni sulla visualizzazione di un campo o per personalizzare un messaggio.

Ciò significa che è possibile utilizzare il valore di un campo non salvato per autorizzare la visualizzazione di un gruppo di opzioni sulla pagina. Nella pagina seguente, il tipo di veicolo non è memorizzato nella banca dati:

![](assets/s_ncs_admin_survey_no_storage_variable.png)

Viene memorizzato in una variabile che deve essere selezionata al momento della creazione della casella a discesa oppure tramite il collegamento **[!UICONTROL Edit storage...]** .

![](assets/s_ncs_admin_survey_no_storage_variable2.png)

Puoi visualizzare le variabili esistenti e crearne di nuove tramite il collegamento **[!UICONTROL Edit variables...]** . Fai clic sul pulsante **[!UICONTROL Add]** per creare una nuova variabile.

![](assets/s_ncs_admin_survey_add_a_variable.png)

La variabile aggiunta sarà disponibile nell’elenco delle variabili locali quando vengono creati i campi di input della pagina.

>[!NOTE]
>
>Per ciascun modulo è possibile creare variabili a monte. A questo scopo, seleziona il modulo e fai clic sul pulsante **[!UICONTROL Properties]** . La scheda **[!UICONTROL Variables]** contiene le variabili locali del modulo.

**Esempio di deposito locale con condizionamento**

Nell’esempio precedente, il contenitore contenente i dati relativi ai veicoli privati viene visualizzato solo se l’opzione **[!UICONTROL Private]** è selezionata dall’elenco a discesa, come indicato nella condizione di visibilità:

![](assets/s_ncs_admin_survey_add_a_condition.png)

Se l&#39;utente seleziona un veicolo privato, il modulo Web offre le seguenti opzioni:

![](assets/s_ncs_admin_survey_no_storage_conda.png)

Il contenitore contenente i dati relativi ai veicoli commerciali sarà visualizzato se è selezionata l&#39;opzione Professionale, come espresso nella condizione di visibilità:

![](assets/s_ncs_admin_survey_view_a_condition.png)

Ciò significa che, se l’utente seleziona un veicolo commerciale, il modulo offre le seguenti opzioni:

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
   >A differenza degli altri campi per i quali i caratteri `<%=` vengono sostituiti con caratteri di escape, il contenuto HTML viene salvato così come è utilizzando la sintassi `<%==`.

## Salvataggio delle risposte ai moduli web {#saving-web-forms-answers}

Per salvare le informazioni raccolte nelle pagine di un modulo, è necessario inserire una casella di archiviazione nel diagramma.

![](assets/s_ncs_admin_survey_save_box.png)

Esistono due modi per utilizzare questa casella:

* Se l’accesso al modulo web è effettuato tramite un collegamento inviato in un messaggio e-mail e se l’utente che accede all’applicazione è già nel database, è possibile selezionare l’opzione **[!UICONTROL Update the preloaded record]**. Per ulteriori informazioni, consulta [Consegna di un modulo tramite e-mail](publishing-a-web-form.md#delivering-a-form-via-email).

   In questo caso, Adobe Campaign utilizza la chiave primaria crittografata del profilo utente, un identificatore univoco assegnato a ciascun profilo da Adobe Campaign. Devi configurare le informazioni da precaricare tramite la casella di precaricamento. Per ulteriori informazioni, consulta [Precaricamento dei dati del modulo](publishing-a-web-form.md#pre-loading-the-form-data).

   >[!CAUTION]
   >
   >Questa opzione sostituisce i dati utente, incluso l’indirizzo e-mail, se è presente un campo in cui immetterli. Non può essere utilizzato per creare nuovi profili e richiede l’utilizzo di una casella di precaricamento nel modulo.

* Per arricchire i dati dei destinatari nel database, modifica la casella di archiviazione e seleziona la chiave di riconciliazione. Per uso interno (in genere un sistema Intranet) o per un modulo utilizzato per creare nuovi profili, è possibile selezionare i campi di riconciliazione. La casella offre tutti i campi del database utilizzati nelle varie pagine dell&#39;applicazione Web:

   ![](assets/s_ncs_admin_survey_save_box_edit.png)

Per impostazione predefinita, i dati vengono importati nel database tramite un&#39;operazione **[!UICONTROL Update or insertion]**: se esiste nel database, l’elemento viene aggiornato (ad esempio, la newsletter selezionata o l’indirizzo e-mail inserito). Se non esiste, vengono aggiunte le informazioni.

È tuttavia possibile modificare tale comportamento. A questo scopo, seleziona la radice dell’elemento e seleziona l’operazione da eseguire dall’elenco a discesa:

![](assets/s_ncs_admin_survey_save_operation.png)

Puoi selezionare una cartella di ricerca per la riconciliazione e la cartella di creazione per i nuovi profili. Se questi campi sono vuoti, la ricerca e la creazione dei profili avviene nella cartella predefinita dell’operatore.

>[!NOTE]
>
>Le operazioni possibili sono: **[!UICONTROL Simple reconciliation]**, **[!UICONTROL Update or insertion]**, **[!UICONTROL Insertion]**, **[!UICONTROL Update]**, **[!UICONTROL Deletion]**.\
>La cartella predefinita dell’operatore è la prima cartella per la quale l’operatore dispone dell’autorizzazione di scrittura.\
>Fai riferimento a [questa sezione](../../platform/using/access-management.md).
