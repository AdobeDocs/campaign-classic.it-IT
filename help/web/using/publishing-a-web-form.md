---
solution: Campaign Classic
product: campaign
title: Pubblicazione di un modulo web
description: Pubblicazione di un modulo web
audience: web
content-type: reference
topic-tags: web-forms
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 2%

---


# Pubblicazione di un modulo web{#publishing-a-web-form}

## Precaricamento dei dati del modulo {#pre-loading-the-form-data}

Se si desidera aggiornare i profili memorizzati nel database tramite un modulo Web, è possibile utilizzare una casella di precaricamento. La casella di precaricamento consente di indicare come trovare il record da aggiornare nel database.

Sono possibili i seguenti metodi di identificazione:

* **[!UICONTROL Adobe Campaign Encryption]**

   Questo metodo di cifratura utilizza l’identificatore Adobe Campaign (ID)  cifrato. Questo metodo è applicabile solo a un oggetto Adobe Campaign  e l&#39;ID crittografato può essere generato solo dalla piattaforma Adobe Campaign .

   Quando si utilizza questo metodo, è necessario adattare l&#39;URL del modulo per inviarlo all&#39;indirizzo e-mail aggiungendo il **`<%=escapeUrl(recipient.cryptedId) %>`** parametro. Per ulteriori informazioni, vedere [Distribuzione di un modulo tramite e-mail](#delivering-a-form-via-email).

* **[!UICONTROL DES encryption]**

   ![](assets/s_ncs_admin_survey_preload_methods_001.png)

   Questo metodo di cifratura utilizza un identificatore (ID) fornito esternamente, collegato a una chiave condivisa da  Adobe Campaign e dal provider esterno. Il **[!UICONTROL Des key]** campo consente di immettere questa chiave di crittografia.

* **[!UICONTROL List of fields]**

   Questa opzione consente di scegliere tra i campi del contesto corrente del modulo, quelli che verranno utilizzati per trovare il profilo corrispondente nel database.

   ![](assets/s_ncs_admin_survey_preload_methods_002.png)

   I campi possono essere aggiunti alle proprietà del modulo tramite la **[!UICONTROL Parameters]** scheda (fare riferimento a [Aggiunta di parametri](../../web/using/defining-web-forms-properties.md#adding-parameters)). Vengono inseriti nell’URL del modulo o nelle aree di input.

   >[!CAUTION]
   >
   >I dati nei campi selezionati non sono crittografati. Non deve essere fornito in un modulo crittografato perché  Adobe Campaign non sarà in grado di decifrarlo se l&#39; **[!UICONTROL Field list]** opzione è selezionata.

   Nell&#39;esempio seguente, il precaricamento del profilo si basa sull&#39;indirizzo e-mail.

   L&#39;URL può includere l&#39;indirizzo e-mail non crittografato, nel qual caso gli utenti possono accedere direttamente alle pagine che li riguardano.

   ![](assets/s_ncs_admin_survey_preload_methods_003.png)

   In caso contrario, verrà loro richiesto di immettere la password.

   ![](assets/s_ncs_admin_survey_preload_methods_004.png)

   >[!CAUTION]
   >
   >Se nell&#39;elenco sono specificati più campi, i dati di **TUTTI I CAMPI** devono corrispondere ai dati memorizzati nel database per poter aggiornare il profilo. In caso contrario, viene creato un nuovo profilo.
   > 
   >Questa funzione è particolarmente utile per le applicazioni Web, ma non è consigliata per i moduli pubblici. L&#39;opzione di controllo di accesso selezionata deve essere &quot;Abilita controllo di accesso&quot;.

L’ **[!UICONTROL Skip preloading if identification is empty]** opzione deve essere selezionata se non si desidera aggiornare i profili. In questo caso, ogni profilo immesso verrà aggiunto al database dopo l&#39;approvazione del modulo. Questa opzione è utilizzata, ad esempio, quando il modulo viene pubblicato su un sito Web.

L&#39; **[!UICONTROL Auto-load data referenced in the form]** opzione consente di precaricare automaticamente i dati corrispondenti ai campi di input e di unione del modulo. Tuttavia, i dati cui si fa riferimento nelle **[!UICONTROL Script]** attività e nelle attività **[!UICONTROL Test]** non sono pertinenti. Se questa opzione non è selezionata, è necessario definire i campi utilizzando l&#39; **[!UICONTROL Load additional data]** opzione.

L&#39; **[!UICONTROL Load additional data]** opzione consente di aggiungere informazioni che non vengono utilizzate nelle pagine del modulo, ma che verranno comunque precaricate.

Ad esempio, è possibile precaricare il genere del destinatario e indirizzarlo automaticamente alla pagina appropriata tramite una casella di prova.

![](assets/s_ncs_admin_survey_preload_ex.png)

## Gestione della distribuzione e del tracciamento dei moduli Web {#managing-web-forms-delivery-and-tracking}

Una volta creato, configurato e pubblicato il modulo, è possibile distribuirlo e tenere traccia delle risposte degli utenti.

### Ciclo di vita di un modulo {#life-cycle-of-a-form}

Il ciclo di vita di un modulo è suddiviso in tre fasi:

1. **Modulo in corso di modifica**

   Questa è la fase di progettazione iniziale. Quando viene creato un nuovo modulo, questo si trova nella fase di modifica. L&#39;accesso al modulo, solo a scopo di test, richiede che il parametro sia utilizzato **[!UICONTROL __uuid]** nel relativo URL. Questo URL è accessibile nella **[!UICONTROL Preview]** sottoscheda. Consultate Parametri [URL](../../web/using/defining-web-forms-properties.md#form-url-parameters)modulo.

   >[!CAUTION]
   >
   >Finché il modulo viene modificato, il relativo URL di accesso è un URL speciale.

1. **Modulo online**

   Una volta completata la fase di progettazione, il modulo può essere consegnato. In primo luogo, deve essere pubblicato. Per ulteriori informazioni, vedere [Pubblicazione di un modulo](#publishing-a-form).

   Il modulo scade **[!UICONTROL Live]** finché non scade.

   >[!CAUTION]
   >
   >Per essere recapitato, l’URL del sondaggio non deve contenere il **[!UICONTROL __uuid]** parametro.

1. **Modulo non disponibile**

   Una volta chiuso il modulo, la fase di consegna è terminata e il modulo non è più disponibile: non è più accessibile agli utenti.

   La data di scadenza può essere definita nella finestra delle proprietà del modulo. Per ulteriori informazioni, vedere [Come rendere disponibile un modulo online](#making-a-form-available-online)

Lo stato di pubblicazione di un modulo viene visualizzato nell&#39;elenco dei moduli.

![](assets/s_ncs_admin_survey_status.png)

### Publishing a form {#publishing-a-form}

Per modificare lo stato di un modulo, è necessario pubblicarlo. A tal fine, fare clic sul **[!UICONTROL Publication]** pulsante sopra l&#39;elenco dei moduli Web e selezionare lo stato nella casella a discesa.

![](assets/webapp_publish_webform.png)

### Rendere il modulo disponibile online {#making-a-form-available-online}

Per essere accessibile dagli utenti, il modulo deve essere in produzione e avviato, ovvero entro il periodo di validità. Le date di validità vengono inserite tramite il **[!UICONTROL Properties]** collegamento del modulo.

* Utilizzare i campi della **[!UICONTROL Project]** sezione per inserire le date di inizio e di fine del modulo.

   ![](assets/webapp_availability_date.png)

* Fare clic sul **[!UICONTROL Personalize the message displayed if the form is closed...]** collegamento per definire il messaggio di errore da visualizzare se l&#39;utente tenta di accedere al modulo mentre non è valido.

   Vedere [Accessibilità del modulo](../../web/using/defining-web-forms-properties.md#accessibility-of-the-form).

### Distribuzione di un modulo tramite e-mail {#delivering-a-form-via-email}

Quando distribuite un invito tramite e-mail, potete utilizzare l&#39; **[!UICONTROL Adobe Campaign Encryption]** opzione per la riconciliazione dei dati. A tal fine, passare alla procedura guidata di consegna e adattare il collegamento al modulo aggiungendo il seguente parametro:

```
<a href="https://server/webApp/APP264?&id=<%=escapeUrl(recipient.cryptedId) %>">
```

In questo caso, la chiave di riconciliazione per l&#39;archiviazione dei dati deve essere l&#39;identificatore crittografato del destinatario. Per ulteriori informazioni, vedere [Precaricamento dei dati](#pre-loading-the-form-data)del modulo.

In questo caso, è necessario selezionare l&#39; **[!UICONTROL Update the preloaded record]** opzione nella casella di record. Per ulteriori informazioni, vedere [Salvataggio delle risposte](../../web/using/web-forms-answers.md#saving-web-forms-answers)ai moduli Web.

![](assets/s_ncs_admin_survey_save_box_option.png)

### Risposte ai registri {#log-responses}

Il tracciamento delle risposte può essere attivato in una scheda dedicata per monitorare l&#39;impatto del modulo Web. A tal fine, fare clic sul **[!UICONTROL Advanced parameters...]** collegamento nella finestra delle proprietà del modulo e selezionare l&#39; **[!UICONTROL Log responses]** opzione.

![](assets/s_ncs_admin_survey_trace.png)

Viene visualizzata la **[!UICONTROL Responses]** scheda che consente di visualizzare l’identità degli utenti che hanno risposto.

![](assets/s_ncs_admin_survey_trace_tab.png)

Selezionate un destinatario e fate clic sul **[!UICONTROL Detail...]** pulsante per visualizzare le risposte fornite.

![](assets/s_ncs_admin_survey_trace_edit.png)

Potete elaborare i registri di risposta forniti nelle query, ad esempio per indirizzare solo gli utenti che non hanno risposto quando inviano promemoria, o per offrire comunicazioni specifiche solo agli utenti che hanno risposto.

>[!NOTE]
>
>Per un monitoraggio completo delle risposte fornite, esportate le risposte e visualizzate o create rapporti dedicati, utilizzate il modulo **Survey** facoltativo. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../web/using/about-surveys.md).

