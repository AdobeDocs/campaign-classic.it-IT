---
product: campaign
title: Sincronizzare i tipi di pubblico
description: Scopri come sincronizzare i tipi di pubblico con il connettore ACS
feature: ACS Connector
hide: true
hidefromtoc: true
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1110'
ht-degree: 1%

---

# Sincronizzare i tipi di pubblico{#synchronizing-audiences}



Puoi creare un elenco sofisticato utilizzando le funzioni avanzate di Campaign v7 e condividere questo elenco come pubblico direttamente e in tempo reale con Campaign Standard (inclusi i dati aggiuntivi) in modo semplice. L’utente Campaign Standard può quindi utilizzare il pubblico in Adobe Campaign Standard.

Il targeting complesso che coinvolge dati aggiuntivi non replicati in Campaign Standard può essere ottenuto solo utilizzando Campaign v7.

Puoi anche semplicemente condividere elenchi di destinatari o dati provenienti da un connettore come Microsoft Dynamics con Campaign Standard.

Questo caso d’uso mostra come preparare il target della consegna in Campaign v7 e come riutilizzare tale target e i relativi dati aggiuntivi in una consegna creata e inviata con Adobe Campaign Standard.

>[!NOTE]
>
>Puoi anche arricchire i dati utilizzando aggregati e raccolte in Adobe Campaign Standard, se tutti i dati necessari sono già replicati.

## Prerequisiti {#prerequisites}

Per ottenere questo risultato, è necessario:

* Destinatari memorizzati nel database di Campaign v7 e sincronizzati con Campaign Standard. Consulta la sezione [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md).
* Dati aggiuntivi come sottoscrizioni o transazioni memorizzate in tabelle correlate a nms:recipients nel database di Campaign v7. Questi dati possono provenire da schemi OOB o tabelle personalizzate di Campaign v7. Per impostazione predefinita, non sono disponibili in Campaign Standard in quanto non sono sincronizzati.
* Diritto di eseguire flussi di lavoro in Campaign v7 e Campaign Standard.
* Diritto di creare ed eseguire una consegna in Campaign Standard.

## Creare un flusso di lavoro di targeting con dati aggiuntivi in Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Il targeting complesso che coinvolge dati aggiuntivi non replicati in Campaign Standard può essere ottenuto solo utilizzando Campaign v7.

Una volta definiti il target e i relativi dati aggiuntivi, è possibile salvarlo come elenco che può essere condiviso con Campaign Standard.

>[!NOTE]
>
>Questo è un esempio. A seconda delle tue esigenze, puoi semplicemente eseguire una query su un elenco di destinatari e condividerlo con ACS senza ulteriori elaborazioni. Puoi anche utilizzare altre attività di gestione dati per preparare il target finale.

Per ottenere il pubblico finale e i relativi dati aggiuntivi:

1. Crea un nuovo flusso di lavoro da **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Aggiungere un&#39;attività **[!UICONTROL Query]** e selezionare i destinatari a cui si desidera inviare l&#39;e-mail finale. Ad esempio, tutti i destinatari tra i 18 e i 30 anni che vivono in Francia.

   ![](assets/acs_connect_query1.png)

1. Aggiungi dati aggiuntivi dall’interno della query. Per ulteriori informazioni, consulta la sezione [Aggiunta di dati](../../workflow/using/query.md#adding-data).

   Questo esempio mostra come aggiungere un aggregato per contare quante consegne ha ricevuto un destinatario in un anno.

   In **[!UICONTROL Query]**, selezionare **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Seleziona **[!UICONTROL Data linked to the filtering dimension]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Scegliere **[!UICONTROL Data linked to the filtering dimension]**, quindi selezionare il nodo **[!UICONTROL Recipient delivery logs]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Selezionare **[!UICONTROL Aggregates]** nel campo **[!UICONTROL Data collected]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Aggiungi una condizione di filtro per tenere conto solo dei registri creati negli ultimi 365 giorni e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Definisci le colonne di output. In questo caso, l’unica colonna necessaria è quella che conta il numero di consegne. Per eseguire questa operazione:

   * Selezionare **[!UICONTROL Add]** a destra della finestra.
   * Dalla finestra **[!UICONTROL Select field]**, fare clic su **[!UICONTROL Advanced selection]**.
   * Selezionare **[!UICONTROL Aggregate]**, quindi **[!UICONTROL Count]**. Selezionare l&#39;opzione **[!UICONTROL Distinct]** e fare clic su **[!UICONTROL Next]**.
   * Nell&#39;elenco dei campi selezionare il campo utilizzato per la funzione **Count**. Scegliere un campo che verrà sempre popolato, ad esempio il campo **[!UICONTROL Primary key]**, quindi fare clic su **[!UICONTROL Finish]**.
   * Modificare l&#39;espressione nella colonna **[!UICONTROL Alias]**. Questo alias ti consentirà di recuperare facilmente la colonna aggiunta nella consegna finale. Ad esempio **NBdeliveries**.
   * Fare clic su **[!UICONTROL Finish]** e salvare la configurazione dell&#39;attività **[!UICONTROL Query]**.

   ![](assets/acs_connect_query7.png)

1. Salva il flusso di lavoro. La sezione successiva mostra come condividere la popolazione con ACS.

## Condividere la destinazione con Campaign Standard {#share-the-target-with-campaign-standard}

Una volta definita la popolazione target, è possibile condividerla con ACS tramite un&#39;attività **[!UICONTROL List update]**.

1. Nel flusso di lavoro creato in precedenza, aggiungere un&#39;attività **[!UICONTROL List update]** e specificare l&#39;elenco da aggiornare o creare.

   Specifica la cartella in cui desideri salvare l’elenco in Campaign v7. Gli elenchi sono soggetti alla mappatura delle cartelle definita durante l’implementazione, che può avere un impatto sulla loro visibilità una volta condivisi in Campaign Standard. Consulta la sezione [Conversione dei diritti](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion).

1. Verificare che l&#39;opzione **[!UICONTROL Share with ACS]** sia selezionata. È selezionata per impostazione predefinita.

   ![](assets/acs_connect_listupdate1.png)

1. Salva ed esegui il flusso di lavoro.

   Il target e i relativi dati aggiuntivi vengono salvati in un elenco in Campaign v7 e condivisi immediatamente come pubblico di elenco in Campaign Standard. Solo i profili replicati vengono condivisi con ACS.

Se si verifica un errore nell&#39;attività **[!UICONTROL List update]**, è possibile che la sincronizzazione con Campaign Standard non sia riuscita. Per visualizzare ulteriori dettagli sul problema, passa a **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Questa cartella contiene flussi di lavoro di sincronizzazione attivati dall&#39;esecuzione dell&#39;attività **[!UICONTROL List update]**. Consulta la sezione [Risoluzione dei problemi del connettore ACS](../../integrations/using/troubleshooting-the-acs-connector.md).

## Recuperare i dati in Campaign Standard e utilizzarli in una consegna {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Una volta eseguito il flusso di lavoro di targeting in Campaign v7, puoi trovare il pubblico dell’elenco in modalità di sola lettura dal menu **[!UICONTROL Audiences]** di Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Creando un flusso di lavoro di consegna in Campaign Standard, è quindi possibile utilizzare questo pubblico e i dati aggiuntivi in essa contenuti in una consegna.

1. Creare un nuovo flusso di lavoro dal menu **[!UICONTROL Marketing activities]**.
1. Aggiungi un&#39;attività **[!UICONTROL Read audience]** e seleziona il pubblico condiviso in precedenza da Campaign v7.

   Questa attività viene utilizzata per recuperare i dati del pubblico selezionato. Puoi anche applicare un **[!UICONTROL Source Filtering]** aggiuntivo, se necessario, utilizzando la scheda corrispondente di questa attività.

1. Aggiungi un&#39;attività **[!UICONTROL Email delivery]** e configurala come qualsiasi altra [attività di consegna e-mail](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html?lang=it).
1. Apri il contenuto della consegna.
1. Aggiungi un campo di personalizzazione. Individuare il nodo **[!UICONTROL Additional data (targetData)]** dalla finestra a comparsa. Questo nodo contiene i dati aggiuntivi del pubblico calcolati nel flusso di lavoro di targeting iniziale. Puoi utilizzarli come qualsiasi altro campo di personalizzazione.

   Per questo esempio, i dati aggiuntivi provenienti dal flusso di lavoro di targeting originale corrispondono al numero di consegne inviate a ciascun destinatario negli ultimi 365 giorni. L’alias NBdeliveries specificato nel flusso di lavoro di targeting è visibile qui.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Salva la consegna e il flusso di lavoro.

   Il flusso di lavoro è ora pronto per essere eseguito. La consegna verrà analizzata e pronta per essere inviata.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Inviare e monitorare la consegna {#send-and-monitor-your-delivery}

Una volta che la consegna e il relativo contenuto sono pronti, invia la consegna:

1. Esegui il flusso di lavoro di consegna. Questo passaggio prepara l’e-mail per l’invio.
1. Dal dashboard di consegna, conferma manualmente che la consegna può essere inviata.
1. Monitora i rapporti e i registri della consegna:

   * **In Campaign Standard**: accedere a [report](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html?lang=it) e [log](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=it) relativi alla consegna come per qualsiasi consegna.
   * **in Campaign v7 e Campaign Standard**: gli ID consegna, i registri di indirizzi e-mail generali e i registri di tracciamento e-mail sono sincronizzati con Campaign v7. Potrai quindi ottenere una visualizzazione a 360° delle campagne di marketing da Campaign v7.

     Le quarantene vengono sincronizzate automaticamente con Campaign v7. Ciò consente di tenere conto delle informazioni non consegnabili per il targeting successivo eseguito in Campaign v7.

     Ulteriori informazioni sulla gestione della quarantena in Campaign Standard sono disponibili in [questa sezione](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=it).
