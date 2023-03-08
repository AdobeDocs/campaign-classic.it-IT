---
product: campaign
title: Pubblicare un modulo web
description: Pubblicare un modulo web
feature: Web Forms
exl-id: 1c66b8e8-7590-4767-9b2f-a9a509df4508
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '963'
ht-degree: 1%

---

# Pubblicare un modulo web{#publishing-a-web-form}

![](../../assets/common.svg)

## Precaricamento dei dati del modulo {#pre-loading-the-form-data}

Se si desidera aggiornare i profili memorizzati nel database tramite un modulo Web, è possibile utilizzare una casella di precaricamento. La casella di precaricamento consente di indicare come trovare il record da aggiornare nel database.

Sono possibili i seguenti metodi di identificazione:

* **[!UICONTROL Adobe Campaign Encryption]**

   Questo metodo di crittografia utilizza l’identificatore (ID) crittografato di Adobe Campaign. Questo metodo è applicabile solo a un oggetto Adobe Campaign e l’ID crittografato può essere generato solo dalla piattaforma Adobe Campaign.

   Quando si utilizza questo metodo, è necessario adattare l’URL del modulo da consegnare all’indirizzo e-mail aggiungendo **`<%=escapeUrl(recipient.cryptedId) %>`** parametro. Per ulteriori informazioni, consulta [Consegna di un modulo tramite e-mail](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   Questo metodo di crittografia utilizza un identificatore (ID) fornito esternamente, collegato a una chiave condivisa da Adobe Campaign e dal provider esterno. Il **[!UICONTROL Des key]** consente di immettere questa chiave di crittografia.

* **[!UICONTROL List of fields]**

   Questa opzione consente di scegliere tra i campi nel contesto corrente del modulo quelli che verranno utilizzati per trovare il profilo corrispondente nel database.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   I campi possono essere aggiunti alle proprietà del modulo tramite **[!UICONTROL Parameters]** scheda (fare riferimento a [Aggiunta di parametri](defining-web-forms-properties.md#adding-parameters)). Vengono inseriti sotto forma di URL o aree di input.

   >[!CAUTION]
   >
   >I dati nei campi selezionati non sono crittografati. Non deve essere fornito in formato crittografato perché Adobe Campaign non sarà in grado di decrittografarlo se **[!UICONTROL Field list]** è selezionata.

   Nell’esempio seguente, il precaricamento del profilo si basa sull’indirizzo e-mail.

   L’URL può includere l’indirizzo e-mail non crittografato, nel qual caso gli utenti hanno accesso diretto alle pagine che li riguardano.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   In caso contrario, verrà richiesta loro la password.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >Se nell&#39;elenco sono specificati più campi, i dati di **TUTTI I CAMPI** deve corrispondere ai dati memorizzati nel database per aggiornare il profilo. In caso contrario, viene creato un nuovo profilo.
   > 
   >Questa funzione è particolarmente utile per le applicazioni Web, ma non è consigliata per i moduli pubblici. L&#39;opzione di controllo di accesso selezionata deve essere &quot;Abilita controllo di accesso&quot;.

Il **[!UICONTROL Skip preloading if no ID]** deve essere selezionata se non desideri aggiornare i profili. In questo caso, ogni profilo inserito verrà aggiunto al database dopo l’approvazione del modulo. Questa opzione viene utilizzata, ad esempio, quando il modulo viene pubblicato su un sito Web.

Il **[!UICONTROL Auto-load data referenced in the form]** consente di precaricare automaticamente i dati che corrispondono ai campi di input e di unione nel modulo. Tuttavia, i dati a cui si fa riferimento in **[!UICONTROL Script]** e **[!UICONTROL Test]** attività non interessate. Se questa opzione non è selezionata, è necessario definire i campi utilizzando **[!UICONTROL Load additional data]** opzione.

Il **[!UICONTROL Load additional data]** consente di aggiungere informazioni non utilizzate nelle pagine del modulo, ma che verranno comunque precaricate.

Ad esempio, puoi precaricare il genere del destinatario e indirizzarlo automaticamente alla pagina appropriata tramite una casella di test.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Gestione della consegna e del tracciamento dei moduli web {#managing-web-forms-delivery-and-tracking}

Una volta creato, configurato e pubblicato il modulo, è possibile distribuirlo e tenere traccia delle risposte utente.

### Ciclo di vita di una forma {#life-cycle-of-a-form}

Il ciclo di vita di una forma prevede tre fasi:

1. **Modulo in fase di modifica**

   Questa è la fase di progettazione iniziale. Quando viene creato un nuovo modulo, questo si trova nella fase di modifica. L’accesso al modulo, solo a scopo di test, richiede quindi il parametro **[!UICONTROL __uuid]** da utilizzare nel relativo URL. Questo URL è accessibile nel **[!UICONTROL Preview]** scheda secondaria. Consulta [Parametri URL modulo](defining-web-forms-properties.md#form-url-parameters).

   >[!CAUTION]
   >
   >Durante la modifica del modulo, il relativo URL di accesso è un URL speciale.

1. **Modulo online**

   Una volta completata la fase di progettazione, il modulo può essere consegnato. Innanzitutto, deve essere pubblicato. Per ulteriori informazioni, consulta [Pubblicazione di un modulo](#publishing-a-form).

   Il modulo sarà **[!UICONTROL Live]** fino alla scadenza.

   >[!CAUTION]
   >
   >Per essere consegnato, l’URL del sondaggio non deve contenere **[!UICONTROL __uuid]** parametro.

1. **Modulo non disponibile**

   Una volta chiuso il modulo, la fase di consegna è terminata e il modulo diventa non disponibile: non è più accessibile agli utenti.

   La data di scadenza può essere definita nella finestra delle proprietà del modulo. Per ulteriori informazioni, consulta [Come rendere un modulo disponibile online](#making-a-form-available-online)

Lo stato di pubblicazione di un modulo viene visualizzato nell&#39;elenco dei moduli.

![](assets/s_ncs_admin_survey_status.png)

### Pubblicazione di un modulo {#publishing-a-form}

Per modificare lo stato di un modulo, è necessario pubblicarlo. A questo scopo, fai clic su **[!UICONTROL Publication]** sopra l&#39;elenco dei moduli Web e selezionare lo stato nella casella a discesa.

![](assets/webapp_publish_webform.png)

### Come rendere un modulo disponibile online {#making-a-form-available-online}

Per essere accessibile agli utenti, il modulo deve essere in produzione e deve essere avviato, ovvero entro il periodo di validità. Le date di validità vengono immesse tramite **[!UICONTROL Properties]** collegamento del modulo.

* Utilizza i campi in **[!UICONTROL Project]** per immettere le date di inizio e fine del modulo.

   ![](assets/webapp_availability_date.png)

* Fai clic su **[!UICONTROL Personalize the message displayed if the form is closed...]** collegamento per definire il messaggio di errore da visualizzare se l&#39;utente tenta di accedere al modulo mentre non è valido.

   Consulta [Accessibilità del modulo](defining-web-forms-properties.md#accessibility-of-the-form).

### Consegna di un modulo tramite e-mail {#delivering-a-form-via-email}

Quando invii un invito tramite e-mail, puoi utilizzare **[!UICONTROL Adobe Campaign Encryption]** opzione per la riconciliazione dei dati. A questo scopo, vai alla consegna guidata e adatta il collegamento al modulo aggiungendo il seguente parametro:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

In questo caso, la chiave di riconciliazione per l’archiviazione dei dati deve essere l’identificatore crittografato del destinatario. Per ulteriori informazioni, consulta [Precaricamento dei dati del modulo](#pre-loading-the-form-data).

In questo caso, è necessario controllare **[!UICONTROL Update the preloaded record]** nella casella di registrazione. Per ulteriori informazioni, consulta [Salvataggio delle risposte ai moduli Web](web-forms-answers.md#saving-web-forms-answers).

![](assets/s_ncs_admin_survey_save_box_option.png)

### Registro risposte {#log-responses}

Il tracciamento delle risposte può essere attivato in una scheda dedicata per monitorare l’impatto del modulo web. A questo scopo, fai clic su **[!UICONTROL Advanced parameters...]** nella finestra delle proprietà del modulo e selezionare **[!UICONTROL Log responses]** opzione.

![](assets/s_ncs_admin_survey_trace.png)

Il **[!UICONTROL Responses]** per visualizzare l&#39;identità dei partecipanti.

![](assets/s_ncs_admin_survey_trace_tab.png)

Seleziona un destinatario e fai clic su **[!UICONTROL Detail...]** per visualizzare le risposte fornite.

![](assets/s_ncs_admin_survey_trace_edit.png)

Puoi elaborare i registri di risposta forniti nelle query, ad esempio per eseguire il targeting solo dei non-rispondenti durante l’invio di promemoria o per offrire comunicazioni specifiche solo ai rispondenti.
