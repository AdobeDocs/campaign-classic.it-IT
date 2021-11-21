---
product: campaign
title: Campi di personalizzazione
description: Campi di personalizzazione
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 67fd9a67-cb05-46cd-acd5-e42fde6f4d4f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 11%

---

# Campi di personalizzazione{#personalization-fields}

![](../../assets/common.svg)

I campi di personalizzazione sono utilizzati per la personalizzazione di primo livello del contenuto dei messaggi inviati. I campi inseriti in un contenuto principale mostrano la posizione in cui inserire i dati dall’origine dati selezionata.

Ad esempio, il campo di personalizzazione con **&lt;%= recipient.LastName %>** indica ad Adobe Campaign di inserire il nome del destinatario nel database (tabella dei destinatari).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#personalization-fields-video)

>[!CAUTION]
>
>Il contenuto dei campi di personalizzazione non può superare i 1024 caratteri.

## Origini dati {#data-sources}

I campi di personalizzazione possono provenire da due tipi di origine dati, in base alla modalità di consegna selezionata:

* Il database Adobe Campaign è l’origine dati. Questo è il caso più comune, ad esempio &quot;campi di personalizzazione dei destinatari&quot;. Si tratta di tutti i campi definiti nella tabella dei destinatari, siano essi campi standard (in genere: cognome, nome, indirizzo, città, data di nascita, ecc.) o campi definiti dall’utente.
* Un file esterno è l’origine dati. Si tratta di tutti i campi definiti nelle colonne del file presentato come input durante una consegna utilizzando i dati presenti in un file esterno.

>[!NOTE]
>
>Un tag di personalizzazione Adobe Campaign ha sempre il seguente modulo **&lt;%=table.field%>**.

## Inserimento di un campo di personalizzazione {#inserting-a-personalization-field}

Per inserire campi di personalizzazione, fai clic sull’icona a discesa accessibile da qualsiasi campo di intestazione, oggetto o modifica del corpo del messaggio.

![](assets/s_ncs_user_add_custom_field.png)

Dopo la selezione di un’origine dati (campi destinatario o campo file), l’inserimento assume la forma di un comando che verrà interpretato da Adobe Campaign e sostituito dal valore del campo per un determinato destinatario. La sostituzione fisica può quindi essere visualizzata nella **[!UICONTROL Preview]** scheda .

## Esempio di campi di personalizzazione {#personalization-fields-example}

Creiamo un’e-mail in cui inseriremo prima il nome del destinatario e quindi la data di creazione del profilo nel corpo del messaggio. Per eseguire questa operazione:

1. Crea una nuova consegna o apri una consegna di tipo e-mail esistente.
1. Nella procedura guidata di consegna, fai clic su **[!UICONTROL Subject]** per modificare l’oggetto del messaggio e inserire un oggetto.
1. Inserisci &quot; **[!UICONTROL Special offer for]** &quot; e utilizza il pulsante nella barra degli strumenti per inserire un campo di personalizzazione. Seleziona **[!UICONTROL Recipients>Title]**.

   ![](assets/s_ncs_user_insert_custom_field.png)

1. Ripetere l&#39;operazione per inserire il nome del destinatario. Inserisci spazi tra tutti i campi di personalizzazione.
1. Fai clic su **[!UICONTROL OK]** da convalidare.
1. Inserisci la personalizzazione nel corpo del messaggio. A questo scopo, fai clic sul contenuto del messaggio e fai clic sul pulsante di inserimento del campo .
1. Seleziona **[!UICONTROL Recipient>Other...]**.

   ![](assets/s_ncs_user_insert_custom_field_b.png)

1. Seleziona il campo con le informazioni da visualizzare e fai clic su **[!UICONTROL OK]**.

   ![](assets/s_ncs_user_insert_custom_field_c.png)

1. Fai clic sul pulsante **[!UICONTROL Preview]** per visualizzare il risultato della personalizzazione. Devi selezionare un destinatario per visualizzare il messaggio del destinatario.

   ![](assets/s_ncs_user_insert_custom_field_d.png)

   >[!NOTE]
   >
   >Quando una consegna fa parte di un flusso di lavoro, puoi utilizzare i dati della tabella del flusso di lavoro temporaneo. Questi dati sono raggruppati nel **[!UICONTROL Target extension]** menu. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/data-life-cycle.md#target-data).

## Ottimizzazione della personalizzazione {#optimizing-personalization}

Puoi ottimizzare la personalizzazione utilizzando un’opzione dedicata: **[!UICONTROL Prepare the personalization data with a workflow]**, disponibile nella **[!UICONTROL Analysis]** scheda delle proprietà di consegna. Per ulteriori informazioni sull’analisi della consegna, consulta [questa sezione](steps-validating-the-delivery.md#analyzing-the-delivery).

Durante l’analisi della consegna, questa opzione crea ed esegue automaticamente un flusso di lavoro che memorizza in una tabella temporanea tutti i dati collegati alla destinazione, inclusi i dati provenienti da tabelle collegate in FDA.

La selezione di questa opzione può migliorare notevolmente le prestazioni dell’analisi della consegna quando vengono elaborati molti dati, soprattutto se i dati di personalizzazione provengono da una tabella esterna tramite FDA. Per ulteriori informazioni, consulta [Accesso a un database esterno (FDA)](../../installation/using/about-fda.md).

Ad esempio, se riscontri problemi di prestazioni quando distribuisci a un numero elevato di destinatari utilizzando molti campi di personalizzazione e/o blocchi di personalizzazione nel contenuto dei messaggi, questa opzione può accelerare la gestione della personalizzazione e quindi la consegna dei messaggi.

Per utilizzare questa opzione, segui i passaggi seguenti:

1. Creare una campagna. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. In **[!UICONTROL Targeting and workflows]** scheda della campagna, aggiungi una **Query** al flusso di lavoro. Per ulteriori informazioni sull’utilizzo di questa attività, consulta [questa sezione](../../workflow/using/query.md).
1. Aggiungi un **[!UICONTROL Email delivery]** al flusso di lavoro e aprilo. Per ulteriori informazioni sull’utilizzo di questa attività, consulta [questa sezione](../../workflow/using/delivery.md).
1. Vai a **[!UICONTROL Analysis]** della scheda **[!UICONTROL Delivery properties]** e seleziona la **[!UICONTROL Prepare the personalization data with a workflow]** opzione .

   ![](assets/perso_optimization.png)

1. Configura la consegna e avvia il flusso di lavoro per avviare l’analisi.

Una volta effettuata l’analisi, i dati di personalizzazione vengono memorizzati in una tabella temporanea tramite un flusso di lavoro tecnico temporaneo creato al volo durante l’analisi.

Questo flusso di lavoro non è visibile nell’interfaccia di Adobe Campaign. Si tratta solo di uno strumento tecnico per archiviare e gestire rapidamente i dati di personalizzazione.

Al termine dell’analisi, passa al flusso di lavoro **[!UICONTROL Properties]** e seleziona la **[!UICONTROL Variables]** scheda . Qui puoi vedere il nome della tabella temporanea che puoi utilizzare per effettuare una chiamata SQL per visualizzare gli ID contenuti.

![](assets/perso_optimization_temp_table.png)

## Timeout della fase di personalizzazione {#timing-out-personalization}

Per migliorare la protezione della consegna, puoi impostare un periodo di timeout per la fase di personalizzazione.

In **[!UICONTROL Delivery]** della scheda **[!UICONTROL Delivery properties]**, seleziona un valore massimo in secondi per il **[!UICONTROL Maximum personalization run time]** opzione .

Durante l’anteprima o l’invio, se la fase di personalizzazione supera il tempo massimo impostato in questo campo, il processo verrà interrotto con un messaggio di errore e la consegna avrà esito negativo.

![](assets/perso_time-out.png)

Il valore predefinito è 5 secondi.

Se imposti questa opzione su 0, non ci sarà alcun limite di tempo per la fase di personalizzazione.

## Video tutorial {#personalization-fields-video}

Scopri come aggiungere un campo di personalizzazione alla riga dell’oggetto e il contenuto di una consegna e-mail.

>[!VIDEO](https://video.tv.adobe.com/v/24925?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
