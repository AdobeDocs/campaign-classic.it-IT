---
solution: Campaign Classic
product: campaign
title: Sincronizzazione dei pubblici
description: Sincronizzazione dei pubblici
audience: integrations
content-type: reference
topic-tags: acs-connector
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 1%

---

# Sincronizzazione dei pubblici{#synchronizing-audiences}

Puoi creare un elenco sofisticato utilizzando le funzioni avanzate di Campaign v7 e condividere questo elenco come pubblico direttamente e in tempo reale con Campaign Standard (inclusi i dati aggiuntivi) in modo semplice. L’utente di Campaign Standard può quindi utilizzare il pubblico in Adobe Campaign Standard.

Il targeting complesso che coinvolge dati aggiuntivi non replicati in Campaign Standard può essere ottenuto solo utilizzando Campaign v7.

Puoi anche semplicemente condividere elenchi di destinatari o dati provenienti da un connettore come Microsoft Dynamics con Campaign Standard.

Questo caso d’uso mostra come preparare il target della consegna in Campaign v7 e come riutilizzare questo target e i relativi dati aggiuntivi in una consegna creata e inviata con Adobe Campaign Standard.

>[!NOTE]
>
>Puoi anche arricchire i dati utilizzando aggregati e raccolte in Adobe Campaign Standard se tutti i dati necessari sono già replicati.

## Prerequisiti {#prerequisites}

A questo scopo, è necessario:

* Destinatari memorizzati nel database Campaign v7 e sincronizzati con Campaign Standard. Consulta la sezione [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md) .
* Dati aggiuntivi, ad esempio abbonamenti o transazioni memorizzate in tabelle relative a nms:destinatari nel database Campaign v7. Questi dati possono provenire da schemi OOB di Campaign v7 o da tabelle personalizzate. Per impostazione predefinita non sono disponibili in Campaign Standard in quanto non sono sincronizzati.
* Diritto di eseguire flussi di lavoro sia in Campaign v7 che in Campaign Standard.
* Diritto di creare ed eseguire una consegna in Campaign Standard.

## Creare un flusso di lavoro di targeting con dati aggiuntivi in Campaign v7 {#create-a-targeting-workflow-with-additional-data-in-campaign-v7}

Il targeting complesso che coinvolge dati aggiuntivi non replicati in Campaign Standard può essere ottenuto solo utilizzando Campaign v7.

Una volta definito il target e i relativi dati aggiuntivi, è possibile salvarlo come un elenco che può essere condiviso con Campaign Standard.

>[!NOTE]
>
>Questo è un esempio. A seconda delle tue esigenze, puoi semplicemente eseguire una query su un elenco di destinatari e condividerlo con ACS senza ulteriori elaborazioni. Puoi anche utilizzare altre attività di gestione dati per preparare il target finale.

Per ottenere il pubblico finale e i relativi dati aggiuntivi:

1. Crea un nuovo flusso di lavoro da **[!UICONTROL Profiles and Targets]** > **[!UICONTROL Jobs]** > **[!UICONTROL Targeting workflows]**.
1. Aggiungi un’attività **[!UICONTROL Query]** e seleziona i destinatari a cui desideri inviare l’e-mail finale. Ad esempio, tutti i beneficiari tra i 18 e i 30 anni che vivono in Francia.

   ![](assets/acs_connect_query1.png)

1. Aggiungi dati aggiuntivi dall’interno della query. Per ulteriori informazioni, consulta la sezione [Aggiunta di dati](../../workflow/using/query.md#adding-data) .

   Questo esempio mostra come aggiungere un aggregato per contare quante consegne ha ricevuto un destinatario in un anno.

   In **[!UICONTROL Query]**, seleziona **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Seleziona **[!UICONTROL Data linked to the filtering dimension]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Scegli **[!UICONTROL Data linked to the filtering dimension]**, quindi seleziona il nodo **[!UICONTROL Recipient delivery logs]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Seleziona **[!UICONTROL Aggregates]** nel campo **[!UICONTROL Data collected]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Aggiungi una condizione di filtro per prendere in considerazione solo i registri creati negli ultimi 365 giorni e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Definisci le colonne di output. In questo caso, l’unica colonna necessaria è quella che conta il numero di consegne. Per farlo:

   * Selezionare **[!UICONTROL Add]** a destra della finestra.
   * Dalla finestra **[!UICONTROL Select field]**, fai clic su **[!UICONTROL Advanced selection]**.
   * Selezionare **[!UICONTROL Aggregate]**, quindi **[!UICONTROL Count]**. Seleziona l’opzione **[!UICONTROL Distinct]** e fai clic su **[!UICONTROL Next]**.
   * Nell’elenco dei campi, seleziona il campo utilizzato per la funzione **Count** . Scegli un campo che sarà sempre popolato, ad esempio il campo **[!UICONTROL Primary key]**, quindi fai clic su **[!UICONTROL Finish]**.
   * Modifica l’espressione nella colonna **[!UICONTROL Alias]** . Questo alias ti consente di recuperare facilmente la colonna aggiunta nella consegna finale. Ad esempio **NBconsegne**.
   * Fai clic su **[!UICONTROL Finish]** e salva la configurazione dell&#39;attività **[!UICONTROL Query]**.

   ![](assets/acs_connect_query7.png)

1. Salva il flusso di lavoro. La sezione successiva mostra come condividere la popolazione con ACS.

## Condividi la destinazione con Campaign Standard {#share-the-target-with-campaign-standard}

Una volta definita la popolazione target, puoi condividerla con ACS tramite un’attività **[!UICONTROL List update]** .

1. Nel flusso di lavoro creato in precedenza, aggiungi un’attività **[!UICONTROL List update]** e specifica l’elenco da aggiornare o creare.

   Specifica la cartella in cui salvare l’elenco in Campaign v7. Gli elenchi sono soggetti alla mappatura delle cartelle definita durante l’implementazione, che può avere un impatto sulla loro visibilità una volta condivisi in Campaign Standard. Consulta la sezione [Conversione dei diritti](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) .

1. Assicurati che l&#39;opzione **[!UICONTROL Share with ACS]** sia selezionata. È selezionata per impostazione predefinita.

   ![](assets/acs_connect_listupdate1.png)

1. Salva ed esegui il flusso di lavoro.

   Il target e i relativi dati aggiuntivi vengono salvati in un elenco in Campaign v7 e condivisi immediatamente come pubblico di elenchi in Campaign Standard. Solo i profili replicati sono condivisi con ACS.

Se si verifica un errore nell&#39;attività **[!UICONTROL List update]**, significa che la sincronizzazione con Campaign Standard potrebbe non essere riuscita. Per maggiori dettagli su cosa è andato storto, vai su **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Questa cartella contiene i flussi di lavoro di sincronizzazione attivati dall&#39; **[!UICONTROL List update]** esecuzione dell&#39;attività. Consulta la sezione [Risoluzione dei problemi relativi al connettore ACS](../../integrations/using/troubleshooting-the-acs-connector.md) .

## Recupera i dati in Campaign Standard e utilizzali in una consegna {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Una volta eseguito il flusso di lavoro di targeting in Campaign v7, puoi trovare il pubblico dell’elenco in modalità di sola lettura dal menu **[!UICONTROL Audiences]** di Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Creando un flusso di lavoro di consegna in Campaign Standard, è quindi possibile utilizzare questo pubblico e i dati aggiuntivi contenuti in una consegna.

1. Crea un nuovo flusso di lavoro dal menu **[!UICONTROL Marketing activities]** .
1. Aggiungi un’attività **[!UICONTROL Read audience]** e seleziona il pubblico che hai condiviso in precedenza da Campaign v7.

   Questa attività viene utilizzata per recuperare i dati del pubblico selezionato. Puoi anche applicare un valore aggiuntivo **[!UICONTROL Source Filtering]** se necessario utilizzando la scheda corrispondente di questa attività.

1. Aggiungi un’attività **[!UICONTROL Email delivery]** e configurala come qualsiasi altra attività [di consegna e-mail](https://docs.adobe.com/content/help/en/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html).
1. Apri il contenuto della consegna.
1. Aggiungi un campo di personalizzazione. Dalla finestra a comparsa, individua il nodo **[!UICONTROL Additional data (targetData)]** . Questo nodo contiene i dati aggiuntivi del pubblico calcolati nel flusso di lavoro di targeting iniziale. Puoi utilizzarli come qualsiasi altro campo di personalizzazione.

   In questo esempio, i dati aggiuntivi provenienti dal flusso di lavoro di targeting originale corrispondono al numero di consegne inviate a ciascun destinatario negli ultimi 365 giorni. L’alias NBdeliveries specificato nel flusso di lavoro di targeting è visibile qui.

   ![](assets/acs_connect_deliveryworkflow_targetdata.png)

1. Salva la consegna e il flusso di lavoro.

   Il flusso di lavoro è ora pronto per essere eseguito. La consegna verrà analizzata e pronta per essere inviata.

   ![](assets/acs_connect_deliveryworkflow_ready.png)

## Inviare e monitorare la consegna {#send-and-monitor-your-delivery}

Una volta che la consegna e il relativo contenuto sono pronti, invia la consegna:

1. Esegui il flusso di lavoro di consegna. Questo passaggio prepara l’e-mail per l’invio.
1. Dal dashboard di consegna, conferma manualmente che la consegna può essere inviata.
1. Monitora i report e i registri della consegna:

   * **In Campaign Standard**: Accedi ai  [](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) report e  [](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) ai log relativi alla consegna come per qualsiasi consegna.
   * **in Campaign v7 e Campaign Standard**: Gli ID di consegna, i registri ampi delle e-mail e i registri di tracciamento delle e-mail sono sincronizzati con Campaign v7. Puoi quindi ottenere una visualizzazione a 360° delle campagne di marketing da Campaign v7.

      Le quarantena vengono sincronizzate automaticamente di nuovo in Campaign v7. Questo consente di tenere conto delle informazioni non recapitate per il targeting successivo eseguito in Campaign v7.

      Per ulteriori informazioni sulla gestione della quarantena in Campaign Standard, consulta [questa sezione](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en).
