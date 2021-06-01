---
product: campaign
title: Accesso a un database esterno
description: Scopri come connettersi a un database esterno
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 240d7e11-da3a-4d64-8986-1f1c8ebcea3c
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---

# Connessione al database {#connecting-to-the-database}

Per abilitare una connessione al database esterno, è necessario indicare i parametri di connessione, ovvero l’origine dati di destinazione e il nome della tabella con i dati che richiedono il caricamento.

>[!CAUTION]
>
>Per elaborare i dati da un database esterno, l’utente Adobe Campaign necessita di diritti specifici per il database esterno e il server applicazioni Adobe Campaign. Per ulteriori informazioni, consulta la sezione [Diritti di accesso al database remoto](../../installation/using/remote-database-access-rights.md) .
>
>Per evitare eventuali malfunzionamenti, gli operatori che accedono ai dati condivisi remoti devono utilizzare spazi separati.

## Creazione di una connessione condivisa {#creating-a-shared-connection}

Per abilitare una connessione a un database esterno condiviso, purché questa connessione sia attiva, è possibile accedere al database tramite Adobe Campaign.

1. La configurazione deve essere definita in precedenza tramite il nodo **[!UICONTROL Administration > Platform > External accounts]** .
1. Fare clic sul pulsante **[!UICONTROL New]** e selezionare il tipo **[!UICONTROL External database]**.
1. Definisci i parametri **[!UICONTROL Connection]** del database esterno.

   Per le connessioni a un database di tipo **ODBC**, il campo **[!UICONTROL Server]** deve contenere il nome dell&#39;origine dati ODBC e non il nome del server. Inoltre, alcune configurazioni aggiuntive possono essere necessarie a seconda dei database utilizzati. Consulta la sezione [Configurazioni specifiche per tipo di database](../../installation/using/configure-fda.md) .

1. Una volta inseriti i parametri, fai clic sul pulsante **[!UICONTROL Test the connection]** per approvarli.

   ![](assets/wf-external-account-create.png)

1. Se necessario, deselezionare l&#39;opzione **[!UICONTROL Enabled]** per disabilitare l&#39;accesso a questo database senza eliminarne la configurazione.
1. Per consentire ad Adobe Campaign di accedere a questo database, è necessario distribuire le funzioni SQL. Fai clic sulla scheda **[!UICONTROL Parameters]** , quindi sul pulsante **[!UICONTROL Deploy functions]** .

   ![](assets/wf-external-account-functions.png)

È possibile definire tablespace di lavoro specifiche per le tabelle e per l&#39;indice nella scheda **[!UICONTROL Parameters]** .

## Creazione di una connessione temporanea {#creating-a-temporary-connection}

Puoi definire direttamente una connessione a un database esterno dalle attività del flusso di lavoro. In questo caso, si trova in un database esterno locale, riservato all’interno di un flusso di lavoro corrente: non verrà salvato negli account esterni. Questo tipo di connessione puntuale può essere creato su diverse attività del flusso di lavoro, in particolare l’ **[!UICONTROL Query]**, l’ **[!UICONTROL Data loading (RDBMS)]**, l’ attività **[!UICONTROL Enrichment]** o l’ attività **[!UICONTROL Split]**.

>[!CAUTION]
>
>Questo tipo di configurazione non è consigliato ma può essere utilizzato periodicamente per raccogliere i dati. Tuttavia, devi creare un account esterno, come illustrato nella sezione [Creazione di una connessione condivisa](#creating-a-shared-connection) .

Ad esempio, nell’attività Query, i passaggi per la creazione di una connessione periodica a un database esterno sono i seguenti:

1. Fai clic su **[!UICONTROL Add data...]** e seleziona le opzioni **[!UICONTROL External data]** .
1. Selezionare l&#39;opzione **[!UICONTROL Locally defining the data source]**.

   ![](assets/wf_add_data_local_external_data.png)

1. Selezionare il motore di database di destinazione nell&#39;elenco a discesa. Immetti il nome del server e fornisci i parametri di autenticazione.

   Specifica anche il nome del database esterno.

   ![](assets/wf_add_data_local_external_data_param.png)

   Fai clic sul pulsante **[!UICONTROL Next]**.

1. Selezionare la tabella in cui sono memorizzati i dati.

   È possibile immettere il nome della tabella direttamente nel campo corrispondente oppure fare clic sull&#39;icona di modifica per accedere all&#39;elenco delle tabelle del database.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Fai clic sul pulsante **[!UICONTROL Add]** per definire uno o più campi di riconciliazione tra i dati del database esterno e i dati nel database Adobe Campaign. Le icone **[!UICONTROL Edit expression]** di **[!UICONTROL Remote field]** e **[!UICONTROL Local field]** consentono di accedere all’elenco dei campi di ciascuna tabella.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Se necessario, specifica una condizione di filtro e la modalità di ordinamento dei dati.
1. Selezionare i dati aggiuntivi da raccogliere nel database esterno. A questo scopo, fai doppio clic sui campi che desideri aggiungere per visualizzarli in **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Fai clic su **[!UICONTROL Finish]** per confermare questa configurazione.

## Connessione sicura {#secure-connection}

>[!NOTE]
>
>La connessione protetta è disponibile solo per PostgreSQL.

Puoi proteggere l’accesso a un database esterno durante la configurazione di un account FDA esterno.

A questo scopo, aggiungi &quot;**:ssl**&quot; dopo l&#39;indirizzo e l&#39;indirizzo del server della porta utilizzata. Ad esempio: **192.168.0.52:4501:ssl**.

I dati verranno quindi inviati tramite il protocollo SSL sicuro.

## Configurazioni aggiuntive {#additional-configurations}

Se necessario, puoi creare lo schema per l’elaborazione dei dati in un database esterno. Allo stesso modo, Adobe Campaign ti consente di definire la mappatura dei dati in una tabella esterna. Queste configurazioni sono generali e non si applicano esclusivamente ai flussi di lavoro.

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione di schemi in Adobe Campaign e sulla definizione di una nuova mappatura dati, consulta [questa pagina](../../configuration/using/about-schema-edition.md).
