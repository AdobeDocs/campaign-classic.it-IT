---
solution: Campaign Classic
product: campaign
title: Accesso a un database esterno
description: Scopri come connettersi a un database esterno
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 2%

---


# Connessione al database {#connecting-to-the-database}

Per abilitare una connessione al database esterno, è necessario indicare i parametri di connessione, ovvero l&#39;origine dati di destinazione e il nome della tabella con i dati che richiedono il caricamento.

>[!CAUTION]
>
>L&#39;utente Adobe Campaign  necessita di diritti specifici per il database esterno e il server applicazione Adobe Campaign  per elaborare i dati da un database esterno. Per ulteriori informazioni, consulta la sezione Diritti [di accesso al database](../../installation/using/remote-database-access-rights.md) remoto.
>
>Per evitare qualsiasi malfunzionamento, gli operatori che accedono ai dati condivisi remoti devono utilizzare spazi separati.

## Creazione di una connessione condivisa {#creating-a-shared-connection}

Per abilitare una connessione a un database esterno condiviso, finché la connessione è attiva, è possibile accedere al database tramite  Adobe Campaign.

1. La configurazione deve essere definita in anticipo tramite il **[!UICONTROL Administration > Platform > External accounts]** nodo.
1. Fare clic sul **[!UICONTROL New]** pulsante e selezionare il **[!UICONTROL External database]** tipo.
1. Definire i **[!UICONTROL Connection]** parametri del database esterno.

   Per le connessioni a un database di tipo **ODBC** , il **[!UICONTROL Server]** campo deve contenere il nome dell&#39;origine dati ODBC e non il nome del server. Inoltre, alcune configurazioni aggiuntive possono essere necessarie a seconda dei database utilizzati. Fare riferimento alla sezione Configurazioni [specifiche per tipo](../../installation/using/configure-fda.md) di database.

1. Una volta inseriti i parametri, fate clic sul **[!UICONTROL Test the connection]** pulsante per approvarli.

   ![](assets/wf-external-account-create.png)

1. Se necessario, deselezionate l&#39; **[!UICONTROL Enabled]** opzione per disabilitare l&#39;accesso a questo database senza eliminarne la configurazione.
1. Per consentire  Adobe Campaign di accedere a questo database, è necessario distribuire le funzioni SQL. Fare clic sulla **[!UICONTROL Parameters]** scheda e quindi sul **[!UICONTROL Deploy functions]** pulsante.

   ![](assets/wf-external-account-functions.png)

È possibile definire tablespace di lavoro specifiche per le tabelle e per l&#39;indice nella **[!UICONTROL Parameters]** scheda.

## Creazione di una connessione temporanea {#creating-a-temporary-connection}

È possibile definire direttamente una connessione a un database esterno dalle attività del flusso di lavoro. In questo caso, si trova in un database esterno locale, riservato all&#39;utilizzo in un flusso di lavoro corrente: non verrà salvata nei conti esterni. Questo tipo di connessione puntuale può essere creato su diverse attività del flusso di lavoro, in particolare **[!UICONTROL Query]**, il **[!UICONTROL Data loading (RDBMS)]**, l&#39; **[!UICONTROL Enrichment]** attività o l&#39; **[!UICONTROL Split]** attività.

>[!CAUTION]
>
>Questo tipo di configurazione non è consigliato ma può essere utilizzato periodicamente per raccogliere i dati. Tuttavia, è necessario creare un account esterno, come illustrato nella sezione [Creazione di una connessione](#creating-a-shared-connection) condivisa.

Ad esempio, nell&#39;attività di query, i passaggi per la creazione di una connessione periodica a un database esterno sono i seguenti:

1. Fare clic sul pulsante **[!UICONTROL Add data...]** e selezionare le **[!UICONTROL External data]** opzioni.
1. Selezionate l’ **[!UICONTROL Locally defining the data source]** opzione.

   ![](assets/wf_add_data_local_external_data.png)

1. Selezionare il motore del database di destinazione nell&#39;elenco a discesa. Immettete il nome del server e fornite i parametri di autenticazione.

   Specificate anche il nome del database esterno.

   ![](assets/wf_add_data_local_external_data_param.png)

   Fai clic sul pulsante **[!UICONTROL Next]**.

1. Selezionare la tabella in cui sono memorizzati i dati.

   È possibile immettere il nome della tabella direttamente nel campo corrispondente oppure fare clic sull&#39;icona di modifica per accedere all&#39;elenco delle tabelle del database.

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. Fare clic sul **[!UICONTROL Add]** pulsante per definire uno o più campi di riconciliazione tra i dati del database esterno e i dati del database Adobe Campaign . Le **[!UICONTROL Edit expression]** icone della tabella **[!UICONTROL Remote field]** e **[!UICONTROL Local field]** consente di accedere all’elenco dei campi di ciascuna tabella.

   ![](assets/wf_add_data_local_external_data_join.png)

1. Se necessario, specificare una condizione di filtro e la modalità di ordinamento dei dati.
1. Selezionare i dati aggiuntivi da raccogliere nel database esterno. A questo scopo, fate doppio clic sui campi che desiderate aggiungere per visualizzarli nel **[!UICONTROL Output columns]**.

   ![](assets/wf_add_data_local_external_data_select.png)

   Fate clic **[!UICONTROL Finish]** per confermare la configurazione.

## Connessione sicura {#secure-connection}

>[!NOTE]
>
>La connessione protetta è disponibile solo per PostgreSQL.

È possibile proteggere l&#39;accesso a un database esterno durante la configurazione di un account FDA esterno.

A questo scopo, aggiungete &quot;**:ssl**&quot; dopo l&#39;indirizzo e l&#39;indirizzo del server della porta utilizzata. Ad esempio: **192.168.0.52:4501:ssl**.

I dati verranno quindi inviati tramite il protocollo SSL sicuro.

## Configurazioni aggiuntive {#additional-configurations}

Se necessario, è possibile creare lo schema per l&#39;elaborazione dei dati in un database esterno. Analogamente,  Adobe Campaign consente di definire la mappatura dei dati in una tabella esterna. Queste configurazioni sono generali e non si applicano esclusivamente ai flussi di lavoro.

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione di schemi in  Adobe Campaign e sulla definizione di una nuova mappatura dati, consulta [questa pagina](../../configuration/using/about-schema-edition.md).