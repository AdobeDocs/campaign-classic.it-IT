---
product: campaign
title: Query delle informazioni di consegna
description: Scopri come eseguire query sulle informazioni di consegna
feature: Query Editor, Workflows
hide: true
hidefromtoc: true
exl-id: b699b064-1287-41c9-8d94-1c1aa2c145ab
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1252'
ht-degree: 7%

---

# Eseguire una query sulle informazioni di consegna {#querying-delivery-information}



## Numero di clic per una consegna specifica {#number-of-clicks-for-a-specific-delivery}

In questo esempio, stiamo cercando di recuperare il numero di clic per una consegna specifica. Questi clic vengono registrati grazie ai registri di tracciamento dei destinatari acquisiti in un dato periodo. Il destinatario viene identificato tramite il suo indirizzo e-mail. Questa query utilizza la tabella **[!UICONTROL Recipient tracking logs]**.

* Quale tabella deve essere selezionata?

  Tabella di rilevamento del registro destinatari (**[!UICONTROL nms:trackingLogRcp]**)

* Campi da selezionare per le colonne di output?

  Chiave primaria (con conteggio) e e-mail

* Su quali criteri verranno filtrate le informazioni?

  Un periodo specifico e un elemento dell’etichetta di consegna

Per eseguire questo esempio, attieniti alla seguente procedura:

1. Aprire **[!UICONTROL Generic query editor]** e selezionare lo schema **[!UICONTROL Recipient tracking logs]**.

   ![](assets/query_editor_tracklog_05.png)

1. Nella finestra **[!UICONTROL Data to extract]**, si desidera creare un aggregato per raccogliere informazioni. A questo scopo, aggiungere la chiave primaria (situata sopra l&#39;elemento principale **[!UICONTROL Recipient tracking logs]**): il conteggio del registro di tracciamento viene eseguito su questo campo **[!UICONTROL Primary key]**. L&#39;espressione modificata sarà **[!UICONTROL x=count(primary key)]**. Collega la somma dei vari registri di tracciamento a un singolo indirizzo e-mail.

   Per eseguire questa operazione:

   * Fare clic sull&#39;icona **[!UICONTROL Add]** a destra del campo **[!UICONTROL Output columns]**. Nella finestra **[!UICONTROL Formula type]**, selezionare l&#39;opzione **[!UICONTROL Edit the formula using an expression]** e fare clic su **[!UICONTROL Next]**. Nella finestra **[!UICONTROL Field to select]**, fare clic su **[!UICONTROL Advanced selection]**.

     ![](assets/query_editor_tracklog_06.png)

   * Nella finestra **[!UICONTROL Formula type]** eseguire un processo sulla funzione di aggregazione. Questo processo sarà un conteggio di chiavi primarie.

     Selezionare **[!UICONTROL Process on an aggregate function]** nella sezione **[!UICONTROL Aggregate]** e fare clic su **[!UICONTROL Count]**.

     ![](assets/query_editor_nveau_18.png)

     Fai clic su **[!UICONTROL Next]**.

   * Selezionare il campo **[!UICONTROL Primary key (@id)]**. La colonna di output **[!UICONTROL count (primary key)]** è configurata.

     ![](assets/query_editor_nveau_19.png)

1. Selezionare l&#39;altro campo da visualizzare nella colonna di output. Nella colonna **[!UICONTROL Available fields]** aprire il nodo **[!UICONTROL Recipient]** e scegliere **[!UICONTROL Email]**. Selezionare la casella **[!UICONTROL Group]** in **[!UICONTROL Yes]** per raggruppare i registri di tracciamento per indirizzo e-mail: questo gruppo collega ogni registro al relativo destinatario.

   ![](assets/query_editor_nveau_20.png)

1. Configura l’ordinamento delle colonne in modo che vengano visualizzati per primi i destinatari più attivi (con il maggior numero di registri di tracciamento). Selezionare **[!UICONTROL Yes]** nella colonna **[!UICONTROL Descending sort]**.

   ![](assets/query_editor_nveau_64.png)

1. Devi quindi filtrare i registri che ti interessano, ovvero quelli che hanno meno di 2 settimane e che riguardano le consegne relative alle vendite.

   Per eseguire questa operazione:

   * Configura il filtro dei dati. A tale scopo, selezionare **[!UICONTROL Filter conditions]** e fare clic su **[!UICONTROL Next]**.

     ![](assets/query_editor_nveau_22.png)

   * Recupera i registri di tracciamento in un determinato periodo per una consegna specifica. Sono necessarie tre condizioni di filtro: due condizioni di data per impostare il periodo di ricerca tra 2 settimane prima della data corrente e il giorno prima della data corrente; e un’altra condizione per limitare la ricerca a una consegna specifica.

     Nella finestra **[!UICONTROL Target element]**, configura la data a partire dalla quale i registri di tracciamento verranno presi in considerazione. Fai clic su **[!UICONTROL Add]**. Viene visualizzata una riga di condizione. Modificare la colonna **[!UICONTROL Expression]** facendo clic sulla funzione **[!UICONTROL Edit expression]**. Nella finestra **[!UICONTROL Field to select]**, scegliere **[!UICONTROL Date (@logDate)]**.

     ![](assets/query_editor_nveau_23.png)

     Selezionare l&#39;operatore **[!UICONTROL greater than]**. Nella colonna **[!UICONTROL Value]** fare clic su **[!UICONTROL Edit expression]** e nella finestra **[!UICONTROL Formula type]** selezionare **[!UICONTROL Process on dates]**. Infine, in **[!UICONTROL Current date minus n days]**, immettere &quot;15&quot;.

     Fai clic su **[!UICONTROL Finish]**.

     ![](assets/query_editor_nveau_24.png)

   * Per selezionare la data di fine della ricerca nel registro di tracciamento, creare una seconda condizione facendo clic su **[!UICONTROL Add]**. Nella colonna **[!UICONTROL Expression]**, scegli di nuovo **[!UICONTROL Date (@logDate)]**.

     Selezionare l&#39;operatore **[!UICONTROL less than]**. Nella colonna **[!UICONTROL Value]** fare clic su **[!UICONTROL Edit expression]**. Per l&#39;elaborazione della data, passare alla finestra **[!UICONTROL Formula type]** e immettere &quot;1&quot; in **[!UICONTROL Current date minus n days]**.

     Fai clic su **[!UICONTROL Finish]**.

     ![](assets/query_editor_nveau_65.png)

     Ora vogliamo configurare la terza condizione di filtro, ovvero l’etichetta di consegna interessata dalla query.

   * Fare clic sulla funzione **[!UICONTROL Add]** per creare un&#39;altra condizione di filtro. Nella colonna **[!UICONTROL Expression]** fare clic su **[!UICONTROL Edit expression]**. Nella finestra **[!UICONTROL Field to select]**, scegli **[!UICONTROL Label]** nel nodo **[!UICONTROL Delivery]**.

     Fai clic su **[!UICONTROL Finish]**.

     ![](assets/query_editor_nveau_66.png)

     Cerca una consegna contenente la parola &quot;vendite&quot;. Poiché non si ricorda l&#39;etichetta esatta, è possibile scegliere l&#39;operatore **[!UICONTROL contains]** e immettere &quot;sales&quot; nella colonna **[!UICONTROL Value]**.

     ![](assets/query_editor_nveau_25.png)

1. Fare clic su **[!UICONTROL Next]** fino a visualizzare la finestra **[!UICONTROL Data preview]**: qui non è necessaria alcuna formattazione.
1. Nella finestra **[!UICONTROL Data preview]**, fai clic su **[!UICONTROL Start the preview of the data]** per visualizzare il numero di registri di tracciamento per ogni destinatario della consegna.

   Il risultato viene visualizzato in ordine decrescente.

   ![](assets/query_editor_tracklog_04.png)

   Il numero più alto di registri per un utente è 6 per questa consegna. 5 utenti diversi hanno aperto l’e-mail di consegna o fatto clic su uno dei collegamenti presenti nell’e-mail.

## Destinatari che non hanno aperto alcuna consegna {#recipients-who-did-not-open-any-delivery}

In questo esempio, vogliamo filtrare i destinatari che non hanno aperto un’e-mail negli ultimi 7 giorni.

Per creare questo esempio, attieniti alla seguente procedura:

1. Trascinare e rilasciare un&#39;attività **[!UICONTROL Query]** in un flusso di lavoro e aprire l&#39;attività.
1. Fare clic su **[!UICONTROL Edit query]** e impostare la destinazione e le dimensioni filtro su **[!UICONTROL Recipients]**.

   ![](assets/query_recipients_1.png)

1. Selezionare **[!UICONTROL Filtering conditions]**, quindi fare clic su **[!UICONTROL Next]**.
1. Fare clic sul pulsante **[!UICONTROL Add]** e selezionare **[!UICONTROL Tracking logs]**.
1. Impostare **[!UICONTROL Operator]** dell&#39;espressione **[!UICONTROL Tracking logs]** su **[!UICONTROL Do not exist such as]**.

   ![](assets/query_open_1.png)

1. Aggiungi un’altra espressione. Selezionare **[!UICONTROL Type]** nella categoria **[!UICONTROL URL]**.
1. Quindi, impostare **[!UICONTROL Operator]** su **[!UICONTROL equal to]** e **[!UICONTROL Value]** su **[!UICONTROL Open]**.

   ![](assets/query_open_2.png)

1. Aggiungere un&#39;altra espressione e selezionare **[!UICONTROL Date]**. **[!UICONTROL Operator]** deve essere impostato su **[!UICONTROL on or after]**.

   ![](assets/query_open_3.png)

1. Per impostare il valore negli ultimi 7 giorni, fare clic sul pulsante **[!UICONTROL Edit expression]** nel campo **[!UICONTROL Value]**.
1. Nella categoria **[!UICONTROL Function]**, selezionare **[!UICONTROL Current date minus n days]** e aggiungere il numero di giorni di cui si desidera eseguire il targeting. In questo caso, vogliamo puntare agli ultimi 7 giorni.

   ![](assets/query_open_4.png)

La transizione in uscita conterrà destinatari che non hanno aperto un’e-mail negli ultimi 7 giorni.

Se, al contrario, desideri filtrare i destinatari che hanno aperto almeno un’e-mail, la query deve essere la seguente. Tieni presente che in questo caso **[!UICONTROL Filtering dimension]** deve essere impostato su **[!UICONTROL Tracking logs (Recipients)]**.

![](assets/query_open_5.png)

## Destinatari che hanno aperto una consegna {#recipients-who-have-opened-a-delivery}

L’esempio seguente mostra come eseguire il targeting dei profili che hanno aperto una consegna nelle ultime 2 settimane:

1. Per eseguire il targeting dei profili che hanno aperto una consegna, devi utilizzare i registri di tracciamento. sono archiviati in una tabella collegata: iniziare selezionando questa tabella nell&#39;elenco a discesa del campo **[!UICONTROL Filtering dimension]**, come illustrato di seguito:

   ![](assets/s_advuser_query_sample1.0.png)

1. Per quanto riguarda le condizioni di filtro, fai clic sull&#39;icona **[!UICONTROL Edit expression]** dei criteri mostrati nella struttura ad albero secondaria dei registri di tracciamento. Selezionare il campo **[!UICONTROL Date]**.

   ![](assets/s_advuser_query_sample1.1.png)

   Fare clic su **[!UICONTROL Finish]** per confermare la selezione.

   Per ripristinare solo i registri di tracciamento di meno di due settimane, selezionare l&#39;operatore **[!UICONTROL Greater than]**.

   ![](assets/s_advuser_query_sample1.4.png)

   Fare quindi clic sull&#39;icona **[!UICONTROL Edit expression]** nella colonna **[!UICONTROL Value]** per definire la formula di calcolo da applicare. Selezionare la formula **[!UICONTROL Current date minus n days]** e immettere 15 nel campo correlato.

   ![](assets/s_advuser_query_sample1.5.png)

   Fare clic sul pulsante **[!UICONTROL Finish]** della finestra della formula. Nella finestra del filtro fare clic sulla scheda **[!UICONTROL Preview]** per verificare i criteri di targeting.

   ![](assets/s_advuser_query_sample1.6.png)

## Filtrare il comportamento dei destinatari dopo una consegna {#filtering-recipients--behavior-folllowing-a-delivery}

In un flusso di lavoro, le caselle **[!UICONTROL Query]** e **[!UICONTROL Split]** consentono di selezionare un comportamento dopo una consegna precedente. Questa selezione viene eseguita tramite il filtro **[!UICONTROL Delivery recipient]**.

* Scopo dell’esempio

  In un flusso di lavoro di consegna sono disponibili diversi modi per dare seguito a una prima comunicazione e-mail. Questo tipo di operazione comporta l&#39;utilizzo della casella **[!UICONTROL Split]**.

* Contesto

  Viene inviata una consegna per un’“offerta di sport estivi”. Quattro giorni dopo la consegna, vengono inviate altre due consegne. Uno di questi è &quot;offerta di sport acquatici&quot;, l&#39;altro è un follow-up della prima consegna &quot;Offerta di sport estivi&quot;.

  La consegna “Offerta sport acquatici” viene inviata ai destinatari che hanno fatto clic sul collegamento “sport acquatici” nella prima consegna. Questi clic mostrano che il destinatario è interessato all’argomento. Ha senso indirizzarli verso offerte simili. Tuttavia, i destinatari che non hanno fatto clic sull’“offerta sport estivi” riceveranno nuovamente lo stesso contenuto.

Nei passaggi seguenti viene illustrato come configurare la casella **[!UICONTROL Split]** integrando due comportamenti diversi:

1. Inserire la casella **[!UICONTROL Split]** nel flusso di lavoro. In questa casella i destinatari della prima consegna vengono suddivisi nelle due consegne successive. Il raggruppamento si verifica in base alle condizioni di filtro collegate al comportamento del destinatario durante la prima consegna.

   ![](assets/query_editor_ex_09.png)

1. Aprire la casella **[!UICONTROL Split]**. Nella scheda **[!UICONTROL General]**, immetti un&#39;etichetta: **Dividi in base al comportamento**, ad esempio.

   ![](assets/query_editor_ex_04.png)

1. Nella scheda **[!UICONTROL Subsets]**, definisci il primo ramo diviso. Ad esempio, immetti l&#39;etichetta **Clic** per questo ramo.
1. Selezionare l&#39;opzione **[!UICONTROL Add a filtering condition on the incoming population]**. Fai clic su **[!UICONTROL Edit]**.
1. Nella finestra **[!UICONTROL Targeting and filtering dimension]** fare doppio clic sul filtro **[!UICONTROL Recipients of a delivery]**.

   ![](assets/query_editor_ex_05.png)

1. Nella finestra **[!UICONTROL Target element]** selezionare il comportamento da applicare al ramo: **[!UICONTROL Recipients having clicked (email)]**.

   Di seguito, selezionare l&#39;opzione **[!UICONTROL Delivery specified by the transition]**. Questa funzionalità ripristina automaticamente le persone target durante la prima consegna.

   Questa è la consegna &quot;Offerta sport acquatici&quot;.

   ![](assets/query_editor_ex_08.png)

1. Definite il secondo ramo. Questo ramo includerà l’e-mail di follow-up con lo stesso contenuto della prima consegna. Passare alla scheda **[!UICONTROL Subsets]** e fare clic su **[!UICONTROL Add]** per crearla.

   ![](assets/query_editor_ex_06.png)

1. Viene visualizzata un’altra scheda secondaria. Denomina &quot;**Non ho fatto clic**&quot;.
1. Fai clic su **[!UICONTROL Add a filtering condition for the incoming population]**. Quindi fai clic su **[!UICONTROL Edit...]**.

   ![](assets/query_editor_ex_07.png)

1. Fare clic su **[!UICONTROL Delivery recipients]** nella finestra **[!UICONTROL Targeting and filtering dimension]**.
1. Nella finestra **[!UICONTROL Target element]**, selezionare il comportamento **[!UICONTROL Recipients who did not click (email)]**. Selezionare l&#39;opzione **[!UICONTROL Delivery specified by the transition]** come mostrato per l&#39;ultimo ramo.

   La casella **[!UICONTROL Split]** è ora completamente configurata.

   ![](assets/query_editor_ex_03.png)

Di seguito è riportato l’elenco dei vari componenti configurati per impostazione predefinita:

* **[!UICONTROL All recipients]**
* **[!UICONTROL Recipients of successfully sent messages,]**
* **[!UICONTROL Recipients who opened or clicked (email),]**
* **[!UICONTROL Recipients who clicked (email),]**
* **[!UICONTROL Recipients of a failed message,]**
* **[!UICONTROL Recipients who didn't open or click (email),]**
* **[!UICONTROL Recipients who didn't click (email).]**

  ![](assets/query_editor_ex_02.png)
