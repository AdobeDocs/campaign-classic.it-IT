---
solution: Campaign Classic
product: campaign
title: Configurazione dei processi di importazione
description: Scoprite come configurare ed eseguire i processi di importazione in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: ba460d8347c987291681641a1be208027acf1d2f
workflow-type: tm+mt
source-wordcount: '2958'
ht-degree: 0%

---


# Configurazione di processi di importazione {#executing-import-jobs}

 Adobe Campaign consente di importare dati nel database da uno o più file in formato testo, CSV, TAB o XML. Questi file sono associati a una tabella (principale o collegata) e ogni campo dei file di origine è associato a un campo del database.

>[!NOTE]
>
>È possibile importare i dati senza mapparli con i dati del database utilizzando la funzione **[!UICONTROL Import a list]**. I dati possono quindi essere utilizzati esclusivamente in flussi di lavoro tramite l&#39;oggetto **[!UICONTROL Read list]**. Per ulteriori informazioni, consulta [questa pagina](../../workflow/using/read-list.md).

La procedura guidata di importazione consente di configurare un&#39;importazione, definirne le opzioni (come la trasformazione dei dati) e avviare l&#39;esecuzione. Si tratta di una serie di schermate il cui contenuto dipende dal tipo di importazione (semplice o multipla) e dai diritti dell&#39;operatore.

La procedura guidata di importazione viene visualizzata dopo la creazione di un nuovo processo di importazione (vedere [Creazione di processi di importazione ed esportazione](../../platform/using/creating-import-export-jobs.md).

>[!NOTE]
>
>Se utilizzate un server Web IIS, potrebbe essere necessaria una configurazione per autorizzare il caricamento di file di grandi dimensioni (>28 MB). Per ulteriori informazioni, consulta [questa sezione](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit).

## File di origine {#source-file}

Nel file di origine, ogni riga coincide con un record. I dati contenuti nei record sono separati da delimitatori (spazio, scheda, carattere e così via). Ciò significa che i dati vengono recuperati sotto forma di colonne e ogni colonna è associata a un campo del database.

## Passaggio 1 - Scelta del modello di importazione {#step-1---choosing-the-import-template}

Quando si avvia la procedura guidata di importazione, è innanzitutto necessario selezionare un modello. Ad esempio, per configurare l’importazione dei destinatari che hanno ricevuto una newsletter, effettuate le seguenti operazioni:

1. Selezionare la cartella **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**.
1. Fate clic su **Nuovo**, quindi fate clic su **Importa** per creare il modello di importazione.

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. Fare clic sulla freccia a destra del campo **[!UICONTROL Import template]** per selezionare il modello, oppure fare clic su **[!UICONTROL Select link]** per sfogliare la struttura.

   Il modello nativo è **[!UICONTROL New text import]**. Questo modello non deve essere modificato, ma può essere duplicato per configurare un nuovo modello in base ai requisiti. Per impostazione predefinita, i modelli di importazione vengono salvati nel nodo **[!UICONTROL Profiles and targets > Templates > Job templates]**.

1. Immettere un nome per l&#39;importazione nel campo **[!UICONTROL Label]**. Potete aggiungere una descrizione.
1. Selezionate il tipo di importazione nel campo appropriato. Esistono due tipi di importazione possibili: **[!UICONTROL Simple import]** per importare un solo file e **[!UICONTROL Multiple import]** per importare più file in una singola esecuzione.

   Per un&#39;importazione multipla, selezionate **[!UICONTROL Multiple import]** dall&#39;elenco a discesa **[!UICONTROL Import type]** nella prima schermata della procedura guidata di importazione.

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. Specificate i campi da importare facendo clic su **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_import_wizard01_3.png)

   Ogni volta che viene aggiunto un file, viene visualizzata la schermata della procedura guidata **[!UICONTROL File to import]**. Consultate la sezione [Passaggio 2 - Selezione del file di origine](#step-2---source-file-selection) e seguite i passaggi della procedura guidata per definire le opzioni di importazione come per una semplice importazione.

   >[!NOTE]
   >
   >Le importazioni multiple devono soddisfare solo esigenze specifiche e non sono raccomandate.

### Parametri avanzati {#advanced-parameters}

Il collegamento **[!UICONTROL Advanced parameters]** consente di accedere alle seguenti opzioni:

* **[!UICONTROL General]** tab

   * **[!UICONTROL Stop execution if there are too many rejects]**

      Questa opzione è selezionata per impostazione predefinita. Potete deselezionare questa opzione se desiderate continuare a eseguire l&#39;importazione indipendentemente dal numero di rifiutamenti. Per impostazione predefinita, l&#39;esecuzione viene arrestata se le prime 100 righe vengono rifiutate.

   * **[!UICONTROL Trace mode]**

      Selezionate questa opzione per tenere traccia dell’esecuzione dell’importazione per ogni riga.

   * **[!UICONTROL Start the job in a detached process]**

      Questa opzione è selezionata per impostazione predefinita. Consente di scollegare l’esecuzione dell’importazione in modo che non influisca sugli altri processi in corso nel database.

   * **[!UICONTROL Do not update enumerations]**

      Selezionate questa opzione per evitare di arricchire l&#39;elenco dei valori enumerati nel database. Vedere [Gestione delle enumerazioni](../../platform/using/managing-enumerations.md).

* **[!UICONTROL Variables]** tab

   È possibile definire le variabili associate al processo che saranno accessibili negli editor di query e nei campi calcolati. Per creare una variabile, fare clic su **[!UICONTROL Add]** e utilizzare l&#39;editor di variabili.

   >[!IMPORTANT]
   >
   >La scheda **[!UICONTROL Variables]** è destinata solo all&#39;uso di programmazione di tipo Workflow e deve essere configurata solo da utenti esperti.

## Passaggio 2 - Selezione del file di origine {#step-2---source-file-selection}

Il file di origine può essere in formato testo (txt, csv, tab, fixed Columns) o xml.

Per impostazione predefinita, è selezionato **[!UICONTROL Upload file on the server]**. Fare clic sulla cartella a destra del campo **[!UICONTROL Local file]** per individuare il disco locale e selezionare il file da importare. Potete deselezionare questa opzione per immettere il percorso di accesso e il nome del file da importare, se presente sul server.

![](assets/s_ncs_user_import_wizard02_1.png)

Quando il file è stato specificato, è possibile visualizzarne i dati nella sezione inferiore della finestra facendo clic su **[!UICONTROL Auto-detect format]**. Questa anteprima mostra le prime 200 righe del file sorgente.

![](assets/s_ncs_user_import_wizard02_2.png)

Utilizzate le opzioni offerte sopra questa visualizzazione per configurare l&#39;importazione. I parametri definiti tramite queste opzioni vengono trasferiti nell&#39;anteprima. Sono disponibili le seguenti opzioni:

* **[!UICONTROL Click here to change the file format...]** consente di controllare il formato del file e perfezionare la configurazione.
* **[!UICONTROL Update on server...]** consente di trasferire il file locale al server. Questa opzione è disponibile solo se è selezionato **[!UICONTROL Upload file on the server]**.
* **[!UICONTROL Download]** è disponibile solo se il file è stato caricato sul server.
* **[!UICONTROL Auto-detect format]** viene utilizzato per reinizializzare il formato dell&#39;origine dati. Questa opzione consente di riapplicare i formati originali ai dati formattati tramite l&#39;opzione **[!UICONTROL Click here to change the file format...]**.
* Il collegamento **[!UICONTROL Advanced parameters]** consente di filtrare i dati di origine e accedere alle opzioni avanzate. Da questa schermata potete scegliere di importare solo una parte del file. Potete anche definire un filtro, ad esempio per importare solo gli utenti di tipo &#39;Prospect&#39; o &#39;Customer&#39;, in base al valore della riga corrispondente. Queste opzioni devono essere utilizzate solo dagli utenti JavaScript esperti.

### Modifica del formato di file {#changing-the-file-format}

L&#39;opzione **[!UICONTROL Click here to change the file format...]** consente di formattare i dati del file di origine, in particolare per specificare il separatore di colonna e il tipo di dati per ciascun campo. Questa configurazione viene eseguita tramite la finestra seguente:

![](assets/s_ncs_user_import_wizard02_3.png)

Questo passaggio consente di descrivere come devono essere letti i valori dei campi del file. Ad esempio, nel caso di una data, i dati Data o Data + Ora possono essere associati a un formato (gg/mm/aaaa, mm/gg/aa, ecc.). Se i dati di input non corrispondono al formato previsto, durante l&#39;importazione si verificheranno dei rifiuti.

Potete visualizzare il risultato della configurazione nella zona di anteprima nella parte inferiore della finestra.

Fare clic su **[!UICONTROL OK]** per salvare la formattazione, quindi fare clic su **[!UICONTROL Next]** per visualizzare il passaggio successivo.

## Passaggio 3 - Mappatura dei campi {#step-3---field-mapping}

È quindi necessario selezionare lo schema di destinazione e mappare i dati di ciascuna colonna sui campi del database.

![](assets/s_ncs_user_import_wizard03_1.png)

* Il campo **[!UICONTROL Destination schema]** consente di selezionare lo schema in cui verranno importati i dati. Queste informazioni sono obbligatorie. Fate clic sull&#39;icona **[!UICONTROL Select link]** per selezionare uno degli schemi esistenti. Fare clic su **[!UICONTROL Edit link]** per visualizzare il contenuto della tabella selezionata.
* La tabella centrale mostra tutti i campi definiti nel file di origine. Selezionare i campi da importare per associare un file di destinazione. Questi campi possono essere mappati manualmente o automaticamente.

   Per mappare manualmente un campo, fare clic sulla casella di controllo per selezionare il campo di origine, quindi fare clic sulla seconda colonna per attivare la cella corrispondente al campo selezionato. Fare clic sull&#39;icona **[!UICONTROL Edit expression]** per visualizzare tutti i campi della tabella corrente. Selezionate il campo di destinazione e fate clic su **[!UICONTROL OK]** per convalidare la mappatura.

   Per associare automaticamente i campi di origine e di destinazione, fare clic sull&#39;icona **[!UICONTROL Guess the destination fields]** a destra dell&#39;elenco dei campi. Se necessario, i campi proposti possono essere modificati.

   >[!IMPORTANT]
   >
   >Il risultato di questa operazione deve sempre essere convalidato prima di procedere con il passaggio successivo.

* È possibile applicare una trasformazione ai campi importati. A tal fine, fare clic nella cella della colonna **[!UICONTROL Transformation]** relativa al campo in questione e selezionare la trasformazione da applicare.

   ![](assets/s_ncs_user_import_wizard03_2.png)

   >[!IMPORTANT]
   >
   >La trasformazione viene applicata al momento dell&#39;importazione. Tuttavia, se sono stati definiti vincoli per il campo di destinazione (nell&#39;esempio precedente, nel campo @lastname), tali vincoli hanno la priorità.

* È possibile aggiungere campi calcolati utilizzando l&#39;icona appropriata, a destra della tabella centrale. I campi calcolati consentono di eseguire trasformazioni complesse, aggiungere colonne virtuali o unire i dati di più colonne. Per informazioni dettagliate sulle varie possibilità, fare riferimento alle sezioni seguenti.

### Campi calcolati {#calculated-fields}

I campi calcolati sono nuove colonne aggiunte al file di origine e calcolate da altre colonne. I campi calcolati possono quindi essere associati ai campi del database Adobe Campaign . Le operazioni di riconciliazione, tuttavia, non sono possibili sui campi calcolati.

Esistono quattro tipi di campi calcolati:

* **[!UICONTROL Fixed string]**: il valore del campo calcolato è lo stesso per tutte le righe del file di origine. Consente di impostare il valore di un campo dei record inseriti o aggiornati. Ad esempio, puoi impostare un marcatore su &quot;yes&quot; per tutti i record importati.
* **[!UICONTROL String with JavaScript tags]**: il valore del campo calcolato è una stringa di caratteri contenente comandi JavaScript.
* **[!UICONTROL JavaScript expression]**: il valore del campo calcolato è il risultato della valutazione di una funzione JavaScript. Il valore restituito può essere un numero, una data e così via.
* **[!UICONTROL Enumeration]**: il valore del campo viene attribuito in base al valore contenuto nel file di origine. L&#39;editor consente di specificare la colonna di origine e immettere l&#39;elenco dei valori di enumerazione, come nell&#39;esempio seguente:

   ![](assets/s_ncs_user_import_wizard03_3.png)

   La scheda **[!UICONTROL Preview]** consente di visualizzare il risultato della configurazione definita. Qui è stata aggiunta la colonna **[!UICONTROL Subscription]**. Il valore viene calcolato dal campo **Status**.

   ![](assets/s_ncs_user_import_wizard03_4.png)

## Passaggio 4 - Riconciliazione {#step-4---reconciliation}

Il passaggio di riconciliazione della procedura guidata di importazione consente di definire la modalità di riconciliazione dei dati del file con i dati esistenti nel database e di impostare le regole di priorità tra i dati del file e i dati del database. La finestra di configurazione si presenta così:

![](assets/s_ncs_user_import_wizard04_1.png)

La sezione centrale della schermata contiene una struttura ad albero con i campi e le tabelle del database Adobe Campaign  a cui verranno importati i dati.

Sono disponibili opzioni speciali per ciascun nodo (tabella o campo). Quando si fa clic sul nodo interessato nell&#39;elenco, i relativi parametri e una breve descrizione sono visualizzati di seguito. Il comportamento definito per ciascun elemento viene visualizzato nella colonna **[!UICONTROL Behavior]** corrispondente.

![](assets/s_ncs_user_import_wizard04_2.png)

### Tipi di operazione {#types-of-operation}

Per ogni tabella interessata dall&#39;importazione, è necessario definire il tipo di operazione. Per l&#39;elemento principale del database sono disponibili le seguenti operazioni:

* **[!UICONTROL Update or insertion]**: aggiorna il record, se presente nel database, e lo crea in caso contrario.
* **[!UICONTROL Insertion]**: inserisce i record nel database.
* **[!UICONTROL Update]**: aggiorna solo i record esistenti (ignora gli altri record).
* **[!UICONTROL Reconciliation only]**: cerca il record nel database, ma non esegue un aggiornamento. Ad esempio, consente di associare la cartella dei destinatari da importare in base a una colonna del file senza aggiornare i dati nelle cartelle.
* **[!UICONTROL Deletion]**: consente di eliminare i record nel database.

Per ciascun campo della tabella interessata dall’importazione sono disponibili le seguenti opzioni:

* **[!UICONTROL Update (empty) if source value is empty]**: in caso di aggiornamento, il valore nel campo rimuoverà il valore del database se il campo è vuoto nel file di origine. In caso contrario, il campo del database viene mantenuto.
* **[!UICONTROL Update only if destination is empty]**: il valore del file di origine non sovrascrive il valore nel campo del database, a meno che il campo del database non sia vuoto. In tal caso, prende il valore del file di origine.
* **[!UICONTROL Update the field only when the record is inserted]**: durante un&#39;operazione di aggiornamento o inserimento, verranno importati solo i record del file di origine nuovi.

>[!NOTE]
>
>La definizione di chiave di riconciliazione è sempre **obbligatoria**, tranne nel caso di inserimento senza deduplicazione.

### Tasti di riconciliazione {#reconciliation-keys}

Per gestire la deduplicazione è necessario compilare almeno una chiave di riconciliazione.

Una chiave di riconciliazione è un insieme di campi utilizzati per identificare un record. Ad esempio, per importare i destinatari, la chiave di riconciliazione può essere il numero di account, il campo &quot;e-mail&quot; o i campi &quot;Cognome, Nome, Società&quot; ecc.

In questo caso, per verificare se una riga di un file corrisponde a un destinatario esistente nel database, il motore di importazione confronta i valori del file con quelli del database per tutti i campi della chiave. Quando i campi sono specifici di un record, è possibile eseguire un confronto preciso tra i dati di origine e di destinazione, garantendo l&#39;integrità dei dati dopo l&#39;importazione. È possibile inserire una seconda chiave di riconciliazione per la stessa tabella; viene utilizzata per le righe la cui prima chiave è vuota.

evitare di scegliere un campo che potrebbe essere modificato durante l&#39;importazione; in tal caso, il motore potrebbe creare record aggiuntivi.

![](assets/s_ncs_user_import_wizard04_3.png)

>[!NOTE]
>
>Per l’importazione di un destinatario, l’identificatore della cartella selezionata viene aggiunto implicitamente alla chiave.
>
>Pertanto, la riconciliazione viene eseguita solo su questa cartella (a meno che non sia selezionata alcuna cartella).

### Deduplication {#deduplication}

>[!NOTE]
>
>Un doppio è un elemento che esiste due o più volte nel file da importare.
>
>Un &#39;duplicato&#39; è un elemento presente sia nel file da importare che nel database.

Il campo **[!UICONTROL Management of doubles]** consente di configurare la deduplicazione dei dati. La deduplicazione riguarda i record che vengono visualizzati più volte **nel file di origine** (o i file di origine nel caso di un&#39;importazione di più file), ovvero le righe per le quali i campi della chiave di riconciliazione sono identici.

* La gestione duplicata in modalità **[!UICONTROL Update]** (modalità predefinita) non esegue la deduplicazione. L&#39;ultimo record ha quindi priorità (perché aggiorna i dati dei record precedenti). Il conteggio dei duplicati non viene eseguito in questa modalità.
* La gestione duplicata in modalità **[!UICONTROL Ignore]** o **[!UICONTROL Reject entity]** esclude i duplicati dall&#39;importazione. In questo caso, non viene importato alcun record.
* In modalità **[!UICONTROL Reject entity]**, l&#39;elemento non viene importato e nei registri di importazione viene generato un errore.
* In modalità **[!UICONTROL Ignore]**, l&#39;elemento non viene importato, ma non viene mantenuta alcuna traccia dell&#39;errore. Questa modalità consente di ottimizzare le prestazioni.

>[!IMPORTANT]
>
>La deduplicazione viene eseguita solo in memoria. Le dimensioni di un&#39;importazione con deduplicazione sono pertanto limitate. Il limite dipende da diversi parametri (capacità del server applicazione, attività, numero di campi nella chiave, ecc.). La dimensione massima per una deduplicazione è dell&#39;ordine di 1.000.000 righe.

La deduplicazione riguarda un record presente sia nel file di origine che nel database. Riguarda solo le operazioni con aggiornamento (cioè **[!UICONTROL Update and insertion]** o **[!UICONTROL Update]**). L&#39;opzione **[!UICONTROL Duplicate management]** consente di aggiornare o ignorare il record se si trova sia nel file di origine che nel database. L&#39;opzione **[!UICONTROL Update or insert based on origin]** appartiene al modulo facoltativo e non può essere utilizzata in un contesto standard.

Le opzioni **[!UICONTROL Reject]** e **[!UICONTROL Ignore]** funzionano come illustrato sopra.

### Comportamento in caso di errore {#behavior-in-the-event-of-an-error}

La maggior parte delle operazioni di trasferimento dei dati genera vari tipi di errori (formato di riga incoerente, indirizzo e-mail non valido, ecc.). Tutti gli errori e tutti gli avvisi generati dal motore di importazione vengono memorizzati e collegati all’istanza di importazione.

![](assets/s_ncs_user_import_general_tab.png)

I dettagli di questi rifiuti possono essere visualizzati tramite la scheda **[!UICONTROL Rejects]**.

![](assets/s_ncs_user_import_rejets_tab.png)

Esistono due tipi di rifiuti (il tipo viene visualizzato nella colonna **[!UICONTROL Connector]**):

* I rifiuti del connettore di testo riguardano errori che si verificano durante l&#39;elaborazione della riga del file (campo calcolato, analisi dei dati, ecc.). In questo caso, in caso di errore, l&#39;intera riga viene sempre rifiutata.
* I rifiuti del connettore del database riguardano errori che si verificano durante la riconciliazione dei dati o la scrittura nel database. Nel caso di un&#39;importazione in più tabelle, il rifiuto può riguardare solo una parte del record (ad esempio, per un&#39;importazione di destinatari ed eventi associati, un errore può impedire l&#39;aggiornamento di un evento senza rifiutare il destinatario).

Nella pagina di riconciliazione dei dati è possibile definire il campo del tipo di gestione degli errori desiderato per campo e tabella per tabella.

* **[!UICONTROL Ignore and log a warning]**: tutti i campi vengono importati nel database tranne quello che ha generato un errore.
* **[!UICONTROL Reject parent element]**: l&#39;intera riga del record viene rifiutata, non solo il campo che ha causato un errore.
* **[!UICONTROL Reject all elements]**: gli arresti dell&#39;importazione e tutti gli elementi del record vengono rifiutati.

   ![](assets/s_ncs_user_import_wizard04_4.png)

La struttura ad albero nella schermata di rifiuto di un&#39;istanza di importazione indica quali campi sono stati rifiutati e dove si sono verificati gli errori.

È possibile generare un file contenente questi record tramite l&#39;icona **[!UICONTROL Export rejects]**:

![](assets/s_ncs_user_import_errors_export.png)

## Passaggio 5 - Passaggio aggiuntivo durante l&#39;importazione di destinatari {#step-5---additional-step-when-importing-recipients}

Il passaggio successivo della procedura guidata di importazione consente di selezionare o creare la cartella in cui importare i dati, mappare automaticamente i destinatari importati con un elenco (nuovo o esistente) e i destinatari della sottoscrizione a un servizio.

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>Questo passaggio viene visualizzato solo quando si importano i destinatari e quando si utilizza la tabella  destinatari Adobe Campaign predefinita (**nms:Recipients**).

* Fate clic sui collegamenti **[!UICONTROL Edit]** per selezionare la cartella, l&#39;elenco o il servizio al quale desiderate associare o sottoscrivere i destinatari.

   1. Importazione in una cartella

      Il collegamento **[!UICONTROL Edit...]** della sezione **[!UICONTROL Import into a folder]** consente di selezionare o creare la cartella in cui verranno importati i destinatari. Per impostazione predefinita, se non è definita alcuna partizione, i dati vengono importati nella cartella predefinita dell&#39;operatore.

      >[!NOTE]
      >
      >La cartella predefinita per un operatore è la prima cartella a cui l&#39;operatore ha accesso in scrittura. Vedere [Gestione dell&#39;accesso alle cartelle](../../platform/using/access-management.md#folder-access-management).

      Per selezionare la cartella di importazione, fate clic sulla freccia a destra del campo **[!UICONTROL Folder]** e selezionate la cartella in questione. È inoltre possibile utilizzare l&#39;icona **[!UICONTROL Select link]** per visualizzare la struttura ad albero in una nuova finestra o per creare una nuova cartella.

      ![](assets/s_ncs_user_import_wizard05_2.png)

      Per creare una nuova cartella, selezionate il nodo da cui desiderate aggiungere una cartella e fate clic con il pulsante destro del mouse. Seleziona **[!UICONTROL Create a new 'Recipients' folder]**.

      ![](assets/s_ncs_user_import_wizard05_3.png)

      La cartella viene aggiunta sotto il nodo corrente. Immettete il nome della nuova cartella, premete Invio per confermare, quindi fate clic su **[!UICONTROL OK]**.

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. Associazione a un elenco

      Il collegamento **[!UICONTROL Edit...]** nella sezione **[!UICONTROL Add recipients to a list]** consente di selezionare o creare un elenco in cui importare i destinatari.

      ![](assets/s_ncs_user_import_wizard05_5.png)

      Per creare un nuovo elenco per questi destinatari, fare clic su **[!UICONTROL Select link]**, quindi su **[!UICONTROL Create]**. La creazione e la gestione di elenchi sono presentate in [Creazione e gestione di elenchi](../../platform/using/creating-and-managing-lists.md).

      ![](assets/s_ncs_user_import_wizard05_6.png)

      Potete decidere di aggiungere i destinatari a quelli già presenti in un elenco, oppure di ricreare l’elenco con i nuovi destinatari. In questo caso, se l’elenco conteneva già dei destinatari, questi verranno eliminati e sostituiti dai destinatari importati.

   1. Iscrizione a un servizio

      Per iscrivere tutti i destinatari importati a un servizio di informazione, fate clic sul collegamento **[!UICONTROL Edit...]** della sezione **[!UICONTROL Subscribe recipients to a service]** per selezionare o creare il servizio di informazioni a cui verranno sottoscritti i destinatari. È possibile selezionare l&#39;opzione **[!UICONTROL Send a confirmation message]**: Il contenuto di questo messaggio è definito nel modello di consegna associato al servizio di iscrizione.

      ![](assets/s_ncs_user_import_wizard05_7.png)

      Per creare un nuovo servizio per questi destinatari, fai clic su **[!UICONTROL Select link]** e quindi sull&#39;icona **[!UICONTROL Create]**. La gestione dei servizi di informazione è presentata in [questa sezione](../../delivery/using/managing-subscriptions.md).

* Utilizzare il campo **[!UICONTROL Origin]** per aggiungere informazioni sull&#39;origine dei destinatari ai propri profili. Tali informazioni sono particolarmente utili nel quadro di un’importazione multipla.

Fare clic su **[!UICONTROL Next]** per convalidare questo passaggio e visualizzare il passaggio seguente.

## Passaggio 6 - Avvio dell&#39;importazione {#step-6---launching-the-import}

L&#39;ultimo passaggio della procedura guidata consente di avviare l&#39;importazione dei dati. A tale scopo, fare clic sul pulsante **[!UICONTROL Start]**.

![](assets/s_ncs_user_import_wizard06_1.png)

È quindi possibile monitorare l&#39;esecuzione del processo di importazione (vedere [Esecuzione dei processi di monitoraggio](../../platform/using/monitoring-jobs-execution.md).
