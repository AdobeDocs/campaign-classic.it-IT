---
product: campaign
title: Sincronizzare i tipi di pubblico
description: Scopri come sincronizzare i tipi di pubblico con il connettore ACS
feature: ACS Connector
exl-id: 88e581cf-43cd-4c43-9347-d016c62fdf42
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 1%

---

# Sincronizzare i tipi di pubblico{#synchronizing-audiences}

![](../../assets/v7-only.svg)

Puoi creare un elenco sofisticato utilizzando le funzioni avanzate di Campaign v7 e condividere questo elenco come pubblico direttamente e in tempo reale con Campaign Standard (inclusi i dati aggiuntivi) in modo semplice. L’utente di Campaign Standard può quindi utilizzare il pubblico in Adobe Campaign Standard.

Il targeting complesso che coinvolge dati aggiuntivi non replicati in Campaign Standard può essere ottenuto solo utilizzando Campaign v7.

Puoi anche semplicemente condividere elenchi di destinatari o dati provenienti da un connettore come Microsoft Dynamics con Campaign Standard.

Questo caso d’uso mostra come preparare il target della consegna in Campaign v7 e come riutilizzare questo target e i relativi dati aggiuntivi in una consegna creata e inviata con Adobe Campaign Standard.

>[!NOTE]
>
>Puoi anche arricchire i dati utilizzando aggregati e raccolte in Adobe Campaign Standard se tutti i dati necessari sono già replicati.

## Prerequisiti {#prerequisites}

A questo scopo, è necessario:

* Destinatari memorizzati nel database Campaign v7 e sincronizzati con Campaign Standard. Fai riferimento a [Sincronizzazione dei profili](../../integrations/using/synchronizing-profiles.md) sezione .
* Dati aggiuntivi, ad esempio abbonamenti o transazioni memorizzati in tabelle relative a nms:destinatari nel database Campaign v7. Questi dati possono provenire da schemi OOB di Campaign v7 o da tabelle personalizzate. Per impostazione predefinita non sono disponibili in Campaign Standard in quanto non sono sincronizzati.
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
1. Aggiungi un **[!UICONTROL Query]** e seleziona i destinatari a cui desideri inviare l’e-mail finale. Ad esempio, tutti i beneficiari tra i 18 e i 30 anni che vivono in Francia.

   ![](assets/acs_connect_query1.png)

1. Aggiungi dati aggiuntivi dall’interno della query. Per ulteriori informazioni, consulta la [Aggiunta di dati](../../workflow/using/query.md#adding-data) sezione .

   Questo esempio mostra come aggiungere un aggregato per contare quante consegne ha ricevuto un destinatario in un anno.

   In **[!UICONTROL Query]**, seleziona **[!UICONTROL Add data...]**.

   ![](assets/acs_connect_query2.png)

1. Seleziona **[!UICONTROL Data linked to the filtering dimension]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query3.png)

1. Scegli **[!UICONTROL Data linked to the filtering dimension]** quindi seleziona la **[!UICONTROL Recipient delivery logs]** nodo e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query4.png)

1. Seleziona **[!UICONTROL Aggregates]** in **[!UICONTROL Data collected]** campo e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query5.png)

1. Aggiungi una condizione di filtro per prendere in considerazione solo i registri creati negli ultimi 365 giorni e fai clic su **[!UICONTROL Next]**.

   ![](assets/acs_connect_query6.png)

1. Definisci le colonne di output. In questo caso, l’unica colonna necessaria è quella che conta il numero di consegne. Per farlo:

   * Seleziona **[!UICONTROL Add]** a destra della finestra.
   * Da **[!UICONTROL Select field]** finestra, fai clic su **[!UICONTROL Advanced selection]**.
   * Seleziona **[!UICONTROL Aggregate]**, quindi **[!UICONTROL Count]**. Controlla la **[!UICONTROL Distinct]** e fai clic su **[!UICONTROL Next]**.
   * Nell’elenco dei campi, seleziona il campo utilizzato per **Conteggio** funzione . Scegli un campo che verrà sempre compilato, ad esempio il campo **[!UICONTROL Primary key]** e fai clic su **[!UICONTROL Finish]**.
   * Modificare l’espressione nel **[!UICONTROL Alias]** colonna. Questo alias ti consente di recuperare facilmente la colonna aggiunta nella consegna finale. Esempio **NBconsegne**.
   * Fai clic su **[!UICONTROL Finish]** e salva il **[!UICONTROL Query]** configurazione dell’attività.

   ![](assets/acs_connect_query7.png)

1. Salva il flusso di lavoro. La sezione successiva mostra come condividere la popolazione con ACS.

## Condividere la destinazione con Campaign Standard {#share-the-target-with-campaign-standard}

Una volta definita la popolazione target, puoi condividerla con ACS tramite un **[!UICONTROL List update]** attività.

1. Nel flusso di lavoro creato in precedenza, aggiungi un **[!UICONTROL List update]** e specifica l’elenco da aggiornare o creare.

   Specifica la cartella in cui salvare l’elenco in Campaign v7. Gli elenchi sono soggetti alla mappatura delle cartelle definita durante l’implementazione, che può avere un impatto sulla loro visibilità una volta condivisi in Campaign Standard. Fai riferimento a [Conversione dei diritti](../../integrations/using/acs-connector-principles-and-data-cycle.md#rights-conversion) sezione .

1. Assicurati che **[!UICONTROL Share with ACS]** è selezionata. È selezionata per impostazione predefinita.

   ![](assets/acs_connect_listupdate1.png)

1. Salva ed esegui il flusso di lavoro.

   Il target e i relativi dati aggiuntivi vengono salvati in un elenco in Campaign v7 e condivisi immediatamente come pubblico di elenchi in Campaign Standard. Solo i profili replicati sono condivisi con ACS.

Se si verifica un errore nella **[!UICONTROL List update]** attività, significa che la sincronizzazione con Campaign Standard potrebbe non essere riuscita. Per avere maggiori dettagli su cosa è andato storto, vai a **[!UICONTROL Administration]** > **[!UICONTROL ACS Connector]** > **[!UICONTROL Process]** > **[!UICONTROL Diagnosis]**. Questa cartella contiene i flussi di lavoro di sincronizzazione attivati da **[!UICONTROL List update]** esecuzione dell’attività. Fai riferimento a [Risoluzione dei problemi del connettore ACS](../../integrations/using/troubleshooting-the-acs-connector.md) sezione .

## Recupera i dati in Campaign Standard e utilizzali in una consegna {#retrieve-the-data-in-campaign-standard-and-use-it-in-a-delivery}

Una volta eseguito il flusso di lavoro di targeting in Campaign v7, puoi trovare il pubblico dell’elenco in modalità di sola lettura da **[!UICONTROL Audiences]** menu di Campaign Standard.

![](assets/acs_connect_deliveryworkflow_audience.png)

Creando un flusso di lavoro di consegna in Campaign Standard, è quindi possibile utilizzare questo pubblico e i dati aggiuntivi contenuti in una consegna.

1. Crea un nuovo flusso di lavoro da **[!UICONTROL Marketing activities]** menu.
1. Aggiungi un **[!UICONTROL Read audience]** e seleziona il pubblico che hai condiviso in precedenza da Campaign v7.

   Questa attività viene utilizzata per recuperare i dati del pubblico selezionato. Puoi anche applicare un **[!UICONTROL Source Filtering]** se necessario utilizzando la scheda corrispondente di questa attività.

1. Aggiungi un **[!UICONTROL Email delivery]** e configuralo come qualsiasi altro [attività di consegna e-mail](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/channel-activities/email-delivery.html).
1. Apri il contenuto della consegna.
1. Aggiungi un campo di personalizzazione. Dalla finestra a comparsa, individua la **[!UICONTROL Additional data (targetData)]** nodo. Questo nodo contiene i dati aggiuntivi del pubblico calcolati nel flusso di lavoro di targeting iniziale. Puoi utilizzarli come qualsiasi altro campo di personalizzazione.

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

   * **In Campaign Standard**: Accesso [rapporti](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/about-reporting/about-dynamic-reports.html) e [logs](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html) relativo alla consegna come per qualsiasi consegna.
   * **in Campaign v7 e Campaign Standard**: Gli ID di consegna, i registri ampi delle e-mail e i registri di tracciamento delle e-mail sono sincronizzati con Campaign v7. Puoi quindi ottenere una visualizzazione a 360° delle campagne di marketing da Campaign v7.

      Le quarantena vengono sincronizzate automaticamente di nuovo in Campaign v7. Questo consente di tenere conto delle informazioni non recapitate per il targeting successivo eseguito in Campaign v7.

      Per ulteriori informazioni sulla gestione della quarantena, consulta Campaign Standard in [questa sezione](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en).
