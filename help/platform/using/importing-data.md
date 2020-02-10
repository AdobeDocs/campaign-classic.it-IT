---
title: Importazione di dati
seo-title: Importazione di dati
description: Importazione di dati
seo-description: null
page-status-flag: never-activated
uuid: ca2269ad-7cfd-4f27-88be-469445a468bf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: c886bd02-c484-443c-93ca-ca244adbf893
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 00351a7a108f74741fa15546d9bd5cf68699e5c1

---


# Importazione di dati{#importing-data}

Adobe Campaign consente di importare dati nel database da uno o più file in formato testo, CSV, TAB o XML. Questi file sono associati a una tabella (principale o collegata) e ogni campo dei file di origine è associato a un campo del database. La configurazione di importazione può essere salvata per essere riutilizzata in modo da poter pianificare le attività di importazione che automatizzeranno le operazioni di replica.

>[!NOTE]
>
>È possibile importare i dati senza mapparli con i dati del database utilizzando la **[!UICONTROL Import a list]** funzione.
> 
>I dati possono quindi essere utilizzati esclusivamente nei flussi di lavoro attraverso l&#39; **[!UICONTROL Read list]** oggetto. For more on this, refer to [this page](../../workflow/using/read-list.md).
>
>Per ulteriori informazioni, guardate il video sull’ [importazione dei profili](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/importing-profiles.html) .

## Struttura dei dati da importare {#structure-of-the-data-to-import}

Nel file di origine, ogni riga coincide con un record. I dati contenuti nei record sono separati da delimitatori (spazio, scheda, carattere e così via). Ciò significa che i dati vengono recuperati sotto forma di colonne e ogni colonna è associata a un campo del database.

## Procedura guidata di importazione {#import-wizard}

La procedura guidata di importazione consente di configurare l’importazione, definirne le opzioni (come la trasformazione dei dati) e avviare l’esecuzione. È una serie di schermate il cui contenuto dipende dal tipo di importazione (semplice o multipla) e dai diritti dell&#39;operatore.

>[!NOTE]
>
>Se utilizzate un server Web IIS, potrebbe essere necessaria una configurazione per autorizzare il caricamento di file di grandi dimensioni (>28 MB).
>
>For more information, refer to [this section](../../installation/using/integration-into-a-web-server-for-windows.md#changing-the-upload-file-size-limit).

### Passaggio 1 - Scelta del modello di importazione {#step-1---choosing-the-import-template}

Quando si avvia la procedura guidata di importazione, è innanzitutto necessario selezionare un modello. Ad esempio, per configurare l’importazione dei destinatari che hanno ricevuto una newsletter, effettuate le seguenti operazioni:

1. Selezionate la **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** cartella.
1. Fate clic su **Nuovo** e quindi su **Importa** per creare il modello di importazione.

   ![](assets/s_ncs_user_import_wizard01_1.png)

1. Fate clic sulla freccia a destra del **[!UICONTROL Import template]** campo per selezionare il modello, oppure fate clic **[!UICONTROL Select link]** per sfogliare la struttura.

   Il modello nativo è **[!UICONTROL New text import]**. Questo modello non deve essere modificato, ma può essere duplicato per configurare un nuovo modello in base ai requisiti. Per impostazione predefinita, i modelli di importazione vengono salvati nel **[!UICONTROL Profiles and targets > Templates > Job templates]** nodo.

1. Immettete un nome per l’importazione nel **[!UICONTROL Label]** campo. Potete aggiungere una descrizione.
1. Selezionate il tipo di importazione nel campo appropriato. Esistono due tipi di importazione possibili: **[!UICONTROL Simple import]** importare un solo file e **[!UICONTROL Multiple import]** importare più file in una singola esecuzione.

   Per un’importazione multipla, selezionate **[!UICONTROL Multiple import]** dall’elenco a **[!UICONTROL Import type]** discesa nella prima schermata della procedura guidata di importazione.

   ![](assets/s_ncs_user_import_wizard01_2.png)

1. Specificate i campi da importare facendo clic su **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_import_wizard01_3.png)

   Ogni volta che viene aggiunto un file, viene visualizzata la schermata della **[!UICONTROL File to import]** procedura guidata. Consultate la sezione [Passo 2 - Selezione](#step-2---source-file-selection) di file sorgente e seguite i passaggi della procedura guidata per definire le opzioni di importazione come per una semplice importazione.

   >[!NOTE]
   >
   >Le importazioni multiple devono soddisfare solo esigenze specifiche e non sono raccomandate.

#### Parametri avanzati {#advanced-parameters}

Il **[!UICONTROL Advanced parameters]** collegamento consente di accedere alle seguenti opzioni:

* **[!UICONTROL General]** tab

   * **[!UICONTROL Stop execution if there are too many rejects]**

      Questa opzione è selezionata per impostazione predefinita. Potete deselezionare questa opzione se desiderate continuare a eseguire l&#39;importazione indipendentemente dal numero di rifiutamenti. Per impostazione predefinita, l&#39;esecuzione viene arrestata se le prime 100 righe vengono rifiutate.

   * **[!UICONTROL Trace mode]**

      Selezionate questa opzione per tenere traccia dell’esecuzione dell’importazione per ogni riga.

   * **[!UICONTROL Start the job in a detached process]**

      Questa opzione è selezionata per impostazione predefinita. Consente di scollegare l’esecuzione dell’importazione in modo da non influenzare altri processi in corso nel database.

   * **[!UICONTROL Do not update enumerations]**

      Selezionate questa opzione per evitare di arricchire l&#39;elenco dei valori enumerati nel database. Consultate [Gestione delle enumerazioni](../../platform/using/managing-enumerations.md).

* **[!UICONTROL Variables]** tab

   È possibile definire le variabili associate al processo che saranno accessibili negli editor di query e nei campi calcolati. Per creare una variabile, fate clic su di essa **[!UICONTROL Add]** e utilizzate l’editor di variabili.

   >[!CAUTION]
   >
   >La **[!UICONTROL Variables]** scheda è destinata solo all&#39;uso di programmazione di tipo Workflow e deve essere configurata solo da utenti esperti.

### Passaggio 2 - Selezione del file di origine {#step-2---source-file-selection}

Il file sorgente può essere in formato testo (txt, csv, tab, fixed Columns) o xml.

Per impostazione predefinita, **[!UICONTROL Upload file on the server]** è selezionata. Fare clic sulla cartella a destra del **[!UICONTROL Local file]** campo per sfogliare il disco locale e selezionare il file da importare. Potete deselezionare questa opzione per immettere il percorso di accesso e il nome del file da importare, se presente sul server.

![](assets/s_ncs_user_import_wizard02_1.png)

Quando il file è stato specificato, è possibile visualizzarne i dati nella sezione inferiore della finestra facendo clic **[!UICONTROL Auto-detect format]**. Questa anteprima mostra le prime 200 righe del file sorgente.

![](assets/s_ncs_user_import_wizard02_2.png)

Utilizzate le opzioni offerte sopra questa visualizzazione per configurare l&#39;importazione. I parametri definiti tramite queste opzioni vengono trasferiti nell&#39;anteprima. Sono disponibili le seguenti opzioni:

* **[!UICONTROL Click here to change the file format...]** consente di controllare il formato del file e perfezionare la configurazione.
* **[!UICONTROL Update on server...]** consente di trasferire il file locale al server. Questa opzione è disponibile solo se **[!UICONTROL Upload file on the server]** è selezionata.
* **[!UICONTROL Download]** è disponibile solo se il file è stato caricato sul server.
* **[!UICONTROL Auto-detect format]** viene utilizzato per reinizializzare il formato dell&#39;origine dati. Questa opzione consente di riapplicare i formati originali ai dati formattati tramite l&#39; **[!UICONTROL Click here to change the file format...]** opzione.
* Il **[!UICONTROL Advanced parameters]** collegamento consente di filtrare i dati di origine e accedere alle opzioni avanzate. Da questa schermata potete scegliere di importare solo una parte del file. Potete anche definire un filtro, ad esempio per importare solo gli utenti di tipo &#39;Prospect&#39; o &#39;Customer&#39;, in base al valore della riga corrispondente. Queste opzioni devono essere utilizzate solo dagli utenti JavaScript esperti.

#### Modifica del formato del file {#changing-the-file-format}

L&#39; **[!UICONTROL Click here to change the file format...]** opzione consente di formattare i dati del file di origine, in particolare per specificare il separatore di colonna e il tipo di dati per ciascun campo. Questa configurazione viene eseguita tramite la finestra seguente:

![](assets/s_ncs_user_import_wizard02_3.png)

Questo passaggio consente di descrivere come devono essere letti i valori dei campi del file. Ad esempio, nel caso di una data, i dati Data o Data + Ora possono essere associati a un formato (gg/mm/aaaa, mm/gg/aa, ecc.). Se i dati di input non corrispondono al formato previsto, durante l&#39;importazione si verificheranno dei rifiuti.

Potete visualizzare il risultato della configurazione nella zona di anteprima nella parte inferiore della finestra.

Fare clic **[!UICONTROL OK]** per salvare la formattazione, quindi fare clic **[!UICONTROL Next]** per visualizzare il passaggio successivo.

### Passaggio 3 - Mappatura dei campi {#step-3---field-mapping}

È quindi necessario selezionare lo schema di destinazione e mappare i dati di ciascuna colonna sui campi del database.

![](assets/s_ncs_user_import_wizard03_1.png)

* Il **[!UICONTROL Destination schema]** campo consente di selezionare lo schema in cui verranno importati i dati. Queste informazioni sono obbligatorie. Fate clic sull&#39; **[!UICONTROL Select link]** icona per selezionare uno degli schemi esistenti. Fare clic **[!UICONTROL Edit link]** per visualizzare il contenuto della tabella selezionata.
* La tabella centrale mostra tutti i campi definiti nel file di origine. Selezionare i campi da importare per associare un file di destinazione. Questi campi possono essere mappati manualmente o automaticamente.

   Per mappare manualmente un campo, fare clic sulla casella di controllo per selezionare il campo di origine, quindi fare clic sulla seconda colonna per attivare la cella corrispondente al campo selezionato. Fare clic sull&#39; **[!UICONTROL Edit expression]** icona per visualizzare tutti i campi della tabella corrente. Selezionare il campo di destinazione e fare clic **[!UICONTROL OK]** per convalidare la mappatura.

   Per associare automaticamente i campi di origine e di destinazione, fare clic sull’ **[!UICONTROL Guess the destination fields]** icona a destra dell’elenco dei campi. Se necessario, i campi proposti possono essere modificati.

   >[!CAUTION]
   >
   >Il risultato di questa operazione deve sempre essere convalidato prima di procedere con il passaggio successivo.

* È possibile applicare una trasformazione ai campi importati. A questo scopo, fare clic nella cella della **[!UICONTROL Transformation]** colonna relativa al campo in questione e selezionare la trasformazione da applicare.

   ![](assets/s_ncs_user_import_wizard03_2.png)

   >[!CAUTION]
   >
   >La trasformazione viene applicata al momento dell&#39;importazione. Tuttavia, se sono stati definiti vincoli per il campo di destinazione (nell&#39;esempio precedente, nel campo @lastname), tali vincoli hanno la priorità.

* È possibile aggiungere campi calcolati utilizzando l&#39;icona appropriata, a destra della tabella centrale. I campi calcolati consentono di eseguire trasformazioni complesse, aggiungere colonne virtuali o unire i dati di più colonne. Per informazioni dettagliate sulle varie possibilità, consultare le sezioni seguenti.

#### Campi calcolati {#calculated-fields}

I campi calcolati sono nuove colonne aggiunte al file di origine e calcolate da altre colonne. I campi calcolati possono quindi essere associati ai campi del database Adobe Campaign. Le operazioni di riconciliazione, tuttavia, non sono possibili sui campi calcolati.

Esistono quattro tipi di campi calcolati:

* **[!UICONTROL Fixed string]**: il valore del campo calcolato è lo stesso per tutte le righe del file di origine. Consente di impostare il valore di un campo dei record inseriti o aggiornati. Ad esempio, puoi impostare un marcatore su &quot;yes&quot; per tutti i record importati.
* **[!UICONTROL String with JavaScript tags]**: il valore del campo calcolato è una stringa di caratteri contenente comandi JavaScript.
* **[!UICONTROL JavaScript expression]**: il valore del campo calcolato è il risultato della valutazione di una funzione JavaScript. Il valore restituito può essere un numero, una data e così via.
* **[!UICONTROL Enumeration]**: il valore del campo viene attribuito in base al valore contenuto nel file di origine. L&#39;editor consente di specificare la colonna di origine e immettere l&#39;elenco dei valori di enumerazione, come nell&#39;esempio seguente:

   ![](assets/s_ncs_user_import_wizard03_3.png)

   La **[!UICONTROL Preview]** scheda consente di visualizzare il risultato della configurazione definita. Qui è stata aggiunta la **[!UICONTROL Subscription]** colonna. Il valore viene calcolato dal campo **Stato** .

   ![](assets/s_ncs_user_import_wizard03_4.png)

### Passaggio 4 - Riconciliazione {#step-4---reconciliation}

Il passaggio di riconciliazione della procedura guidata di importazione consente di definire la modalità di riconciliazione dei dati del file con i dati esistenti nel database e di impostare le regole di priorità tra i dati del file e i dati del database. La finestra di configurazione si presenta così:

![](assets/s_ncs_user_import_wizard04_1.png)

La sezione centrale della schermata contiene una struttura ad albero con i campi e le tabelle del database Adobe Campaign in cui verranno importati i dati.

Sono disponibili opzioni speciali per ciascun nodo (tabella o campo). Quando si fa clic sul nodo interessato nell&#39;elenco, i relativi parametri e una breve descrizione sono visualizzati di seguito. Il comportamento definito per ciascun elemento viene visualizzato nella **[!UICONTROL Behavior]** colonna corrispondente.

![](assets/s_ncs_user_import_wizard04_2.png)

#### Tipi di operazioni {#types-of-operation}

Per ogni tabella interessata dall&#39;importazione, è necessario definire il tipo di operazione. Per l&#39;elemento principale del database sono disponibili le seguenti operazioni:

* **[!UICONTROL Update or insertion]**: aggiorna il record se esiste nel database e lo crea in caso contrario.
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

#### Tasti di riconciliazione {#reconciliation-keys}

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

#### Deduplicazione {#deduplication}

>[!NOTE]
>
>Un doppio è un elemento che esiste due o più volte nel file da importare.
>
>Un &#39;duplicato&#39; è un elemento presente sia nel file da importare che nel database.

Il **[!UICONTROL Management of doubles]** campo consente di configurare la deduplicazione dei dati. La deduplicazione riguarda i record che vengono visualizzati più volte **nel file** di origine (o i file di origine in caso di importazione di più file), vale a dire le righe per le quali i campi della chiave di riconciliazione sono identici.

* La gestione duplicata in **[!UICONTROL Update]** modalità (modalità predefinita) non esegue la deduplicazione. L&#39;ultimo record ha quindi priorità (perché aggiorna i dati dei record precedenti). Il conteggio dei duplicati non viene eseguito in questa modalità.
* La gestione duplicata in **[!UICONTROL Ignore]** modalità o **[!UICONTROL Reject entity]** esclude i duplicati dall&#39;importazione. In questo caso, non viene importato alcun record.
* In **[!UICONTROL Reject entity]** modalità, l’elemento non viene importato e nei registri di importazione viene generato un errore.
* In **[!UICONTROL Ignore]** modalità, l&#39;elemento non viene importato, ma non viene mantenuta alcuna traccia dell&#39;errore. Questa modalità consente di ottimizzare le prestazioni.

>[!CAUTION]
>
>La deduplicazione viene eseguita solo in memoria. Le dimensioni di un&#39;importazione con deduplicazione sono pertanto limitate. Il limite dipende da diversi parametri (capacità del server applicazione, attività, numero di campi nella chiave, ecc.). La dimensione massima per una deduplicazione è dell&#39;ordine di 1.000.000 righe.

La deduplicazione riguarda un record presente sia nel file di origine che nel database. Riguarda solo le operazioni con aggiornamento (cioè **[!UICONTROL Update and insertion]** o **[!UICONTROL Update]**). L&#39; **[!UICONTROL Duplicate management]** opzione consente di aggiornare o ignorare il record se si trova sia nel file di origine che nel database. L&#39; **[!UICONTROL Update or insert based on origin]** opzione appartiene al modulo facoltativo e non può essere utilizzata in un contesto standard.

Le opzioni **[!UICONTROL Reject]** e **[!UICONTROL Ignore]** funzionano come illustrato sopra.

#### Comportamento in caso di errore {#behavior-in-the-event-of-an-error}

La maggior parte delle operazioni di trasferimento dei dati genera vari tipi di errori (formato di riga incoerente, indirizzo e-mail non valido, ecc.). Tutti gli errori e tutti gli avvisi generati dal motore di importazione vengono memorizzati e collegati all’istanza di importazione.

![](assets/s_ncs_user_import_general_tab.png)

I dettagli di questi rifiuti possono essere visualizzati tramite la **[!UICONTROL Rejects]** scheda.

![](assets/s_ncs_user_import_rejets_tab.png)

Esistono due tipi di rifiuti (il tipo viene visualizzato nella **[!UICONTROL Connector]** colonna):

* I rifiuti del connettore di testo riguardano errori che si verificano durante l&#39;elaborazione della riga del file (campo calcolato, analisi dei dati, ecc.). In questo caso, in caso di errore, l&#39;intera riga viene sempre rifiutata.
* I rifiuti del connettore del database riguardano errori che si verificano durante la riconciliazione dei dati o la scrittura nel database. Nel caso di un&#39;importazione in più tabelle, il rifiuto può riguardare solo una parte del record (ad esempio, per un&#39;importazione di destinatari ed eventi associati, un errore può impedire l&#39;aggiornamento di un evento senza rifiutare il destinatario).

Nella pagina di riconciliazione dei dati è possibile definire il campo del tipo di gestione degli errori desiderato per campo e tabella per tabella.

* **[!UICONTROL Ignore and log a warning]**: tutti i campi vengono importati nel database tranne quello che ha generato un errore.
* **[!UICONTROL Reject parent element]**: l&#39;intera riga del record viene rifiutata, non solo il campo che ha causato un errore.
* **[!UICONTROL Reject all elements]**: gli arresti dell&#39;importazione e tutti gli elementi del record vengono rifiutati.

   ![](assets/s_ncs_user_import_wizard04_4.png)

La struttura ad albero nella schermata di rifiuto di un&#39;istanza di importazione indica quali campi sono stati rifiutati e dove si sono verificati gli errori.

È possibile generare un file contenente questi record tramite l&#39; **[!UICONTROL Export rejects]** icona:

![](assets/s_ncs_user_import_errors_export.png)

### Passaggio 5 - Passaggio aggiuntivo durante l&#39;importazione dei destinatari {#step-5---additional-step-when-importing-recipients}

Il passaggio successivo della procedura guidata di importazione consente di selezionare o creare la cartella in cui importare i dati, mappare automaticamente i destinatari importati con un elenco (nuovo o esistente) e i destinatari della sottoscrizione a un servizio.

![](assets/s_ncs_user_import_wizard05_1.png)

>[!NOTE]
>
>Questo passaggio viene visualizzato solo quando si importano i destinatari e quando si utilizza la tabella dei destinatari predefinita di Adobe Campaign (**nms:destinatario**).

* Fate clic sui **[!UICONTROL Edit]** collegamenti per selezionare la cartella, l’elenco o il servizio al quale desiderate associare o sottoscrivere i destinatari.

   1. Importazione in una cartella

      Il **[!UICONTROL Edit...]** collegamento della **[!UICONTROL Import into a folder]** sezione consente di selezionare o creare la cartella in cui verranno importati i destinatari. Per impostazione predefinita, se non è definita alcuna partizione, i dati vengono importati nella cartella predefinita dell&#39;operatore.

      >[!NOTE]
      >
      >La cartella predefinita per un operatore è la prima cartella a cui l&#39;operatore ha accesso in scrittura. Consultate Gestione dell’accesso alle [cartelle](../../platform/using/access-management.md#folder-access-management).

      Per selezionare la cartella di importazione, fate clic sulla freccia a destra del **[!UICONTROL Folder]** campo e selezionate la cartella in questione. Potete anche utilizzare l&#39; **[!UICONTROL Select link]** icona per visualizzare la struttura ad albero in una nuova finestra o per creare una nuova cartella.

      ![](assets/s_ncs_user_import_wizard05_2.png)

      Per creare una nuova cartella, selezionate il nodo da cui desiderate aggiungere una cartella e fate clic con il pulsante destro del mouse. Selezionare **[!UICONTROL Create a new 'Recipients' folder]**.

      ![](assets/s_ncs_user_import_wizard05_3.png)

      La cartella viene aggiunta sotto il nodo corrente. Immettete il nome della nuova cartella, premete Invio per confermare, quindi fate clic **[!UICONTROL OK]**.

      ![](assets/s_ncs_user_import_wizard05_4.png)

   1. Associazione a un elenco

      Il **[!UICONTROL Edit...]** collegamento nella **[!UICONTROL Add recipients to a list]** sezione consente di selezionare o creare un elenco in cui importare i destinatari.

      ![](assets/s_ncs_user_import_wizard05_5.png)

      Per creare un nuovo elenco per questi destinatari, fai clic su **[!UICONTROL Select link]**, quindi **[!UICONTROL Create]**. La creazione e la gestione di elenchi sono presentate in [Creazione e gestione di elenchi](../../platform/using/creating-and-managing-lists.md).

      ![](assets/s_ncs_user_import_wizard05_6.png)

      Potete decidere di aggiungere i destinatari a quelli già presenti in un elenco, oppure di ricreare l’elenco con i nuovi destinatari. In questo caso, se l’elenco conteneva già dei destinatari, questi verranno eliminati e sostituiti dai destinatari importati.

   1. Iscrizione a un servizio

      Per iscrivere tutti i destinatari importati a un servizio di informazione, fate clic sul **[!UICONTROL Edit...]** collegamento della **[!UICONTROL Subscribe recipients to a service]** sezione per selezionare o creare il servizio di informazioni a cui verranno sottoscritti i destinatari. Potete selezionare l&#39; **[!UICONTROL Send a confirmation message]** opzione: Il contenuto di questo messaggio è definito nel modello di consegna associato al servizio di iscrizione.

      ![](assets/s_ncs_user_import_wizard05_7.png)

      Per creare un nuovo servizio per questi destinatari, fai clic su **[!UICONTROL Select link]** e quindi sull’ **[!UICONTROL Create]** icona . La gestione dei servizi di informazione è presentata in [questa sezione](../../delivery/using/managing-subscriptions.md).

* Utilizzare il **[!UICONTROL Origin]** campo per aggiungere informazioni sull&#39;origine dei destinatari ai propri profili. Tali informazioni sono particolarmente utili nel quadro di un’importazione multipla.

Fare clic **[!UICONTROL Next]** per convalidare questo passaggio e visualizzare il passaggio seguente.

### Passaggio 6 - Avvio dell&#39;importazione {#step-6---launching-the-import}

L&#39;ultimo passaggio della procedura guidata consente di avviare l&#39;importazione dei dati. A tale scopo, fare clic sul **[!UICONTROL Start]** pulsante.

![](assets/s_ncs_user_import_wizard06_1.png)

### Stati del processo {#job-statuses}

Lo stato del processo indica lo stato corrente di un processo. Ogni stato è rappresentato da un’icona e un’etichetta speciali. Queste informazioni vengono visualizzate nell’elenco dei processi. Gli stati e le relative icone sono elencati di seguito:

![](assets/s_ncs_user_export_status.png)

* **Modifica in corso**

   Creazione del processo in corso.

* **Esecuzione in corso**

   Il processo viene eseguito.

* **Annulla**

   Fate clic sul **[!UICONTROL Cancel]** pulsante: il processo in corso viene annullato.

* **Annullamento in corso**

   Il comando di annullamento è stato preso in considerazione e il processo viene annullato.

* **Pausa in corso**

   Fate clic **[!UICONTROL Pause]**: il lavoro è sospeso.

* **In pausa**

   Fate clic **[!UICONTROL Pause]**: il lavoro è sospeso. È possibile riavviarlo facendo clic su **[!UICONTROL Start]**.

* **Completato**

   Esecuzione del processo completata.

* **Completato con errore**

   Il processo non è stato eseguito a causa di un errore tecnico.

* **Arresto del server in corso**

   Il processo in corso viene interrotto a causa della chiusura del server Adobe Campaign.

## Esempi di importazione generici {#generic-import-samples}

### Esempio: Importa da un elenco di destinatari {#example--import-from-a-list-of-recipients}

Per creare e fornire un elenco di destinatari dalla panoramica degli elenchi, procedere come segue:

1. Creazione dell’elenco

   * Fai clic sul **[!UICONTROL Lists]** collegamento nel **[!UICONTROL Profiles and targets]** menu della home page di Adobe Campaign.
   * Fare clic sul pulsante **[!UICONTROL Create]** e quindi sul **[!UICONTROL Import a list]** pulsante.

1. Selezione del file da importare

   Fate clic sulla cartella a destra del **[!UICONTROL Local file]** campo e selezionate il file contenente l’elenco da importare.

   ![](assets/s_ncs_user_import_example00_01.png)

1. Nome elenco e archiviazione

   Immettere il nome dell&#39;elenco e selezionare la directory in cui salvarlo.

   ![](assets/s_ncs_user_import_example00_02.png)

1. Avvio dell&#39;importazione

   Fare clic **[!UICONTROL Next]** e quindi **[!UICONTROL Start]** iniziare a importare l&#39;elenco.

   ![](assets/s_ncs_user_import_example00_03.png)

### Esempio: importare nuovi record da un file di testo {#example--import-new-records-from-a-text-file-}

Per importare i nuovi profili dei destinatari memorizzati in un file di testo nel database Adobe Campaign, effettua i seguenti passaggi:

1. Scelta di un modello

   * Dalla home page di Adobe Campaign, fai clic sul **[!UICONTROL Profiles and targets]** collegamento, quindi **[!UICONTROL Jobs]**. Sopra l’elenco dei processi, fate clic su **[!UICONTROL New import]**.
   * Mantenere il **[!UICONTROL New text import]** modello selezionato per impostazione predefinita.
   * Modificare l’etichetta e la descrizione.
   * Selezionare **[!UICONTROL Simple import]**.
   * Mantenete la cartella di processo predefinita.
   * Fate clic su **[!UICONTROL Advanced parameters]** e selezionate l’ **[!UICONTROL Tracking mode]** opzione per visualizzare i dettagli dell’importazione durante l’esecuzione.

1. Selezione del file da importare

   Fate clic sulla cartella a destra del **[!UICONTROL Local file]** campo e selezionate il file da importare.

   ![](assets/s_ncs_user_import_example01_01.png)

1. Associazione di campi

   Fate clic sull’ **[!UICONTROL Guess the destination fields]** icona per mappare automaticamente gli schemi di origine e destinazione. Controllare le informazioni in questa finestra prima di fare clic **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_import_example03_01.png)

1. Riconciliazione

   * Vai alla tabella **Destinatari (nms:destinatario)** .
   * Selezionare l&#39; **[!UICONTROL Insertion]** operazione e lasciare i valori predefiniti negli altri campi.

      ![](assets/s_ncs_user_import_example04_01.png)

1. Importazione dei destinatari

   * Se necessario, specificate una cartella in cui importare i record.

      ![](assets/s_ncs_user_import_example05_01.png)

1. Avvio dell&#39;importazione

   * Clic **[!UICONTROL Start]**.

      Nell’area centrale dell’editor, potete verificare che l’operazione di importazione sia stata completata e visualizzare il numero di record elaborati.

      ![](assets/s_ncs_user_import_example06_01.png)

      La **[!UICONTROL Tracking]** modalità consente di tenere traccia dei dettagli dell’importazione per ciascun record nel file di origine. A questo scopo, dalla home page fare clic **[!UICONTROL Profiles and Targets]** quindi **[!UICONTROL Processes]**, selezionare l&#39;importazione rilevante, quindi cercare le **[!UICONTROL General]**, **[!UICONTROL Journal]** e **[!UICONTROL Rejects]** le schede.

      * Verifica dell&#39;avanzamento dell&#39;importazione

         ![](assets/s_ncs_user_import_example07_01.png)

      * Processo di visualizzazione per ciascun record

         ![](assets/s_ncs_user_import_example07_02.png)

### Esempio: Aggiornare e inserire i destinatari {#example--update-and-insert-recipients}

Vogliamo aggiornare i record esistenti nel database e crearne di nuovi da un file di testo. Esempio di procedura:

1. Scelta di un modello

   Ripetere i passaggi descritti nell&#39;esempio 2 precedente.

1. File da importare

   Selezionate il file da importare.

   Nel nostro esempio, la panoramica delle prime righe del file mostra che il file contiene aggiornamenti per tre record e la creazione di un record.

   ![](assets/s_ncs_user_import_example02_02.png)

1. Associazione di campi

   Applicate la procedura descritta nell&#39;esempio 2 precedente.

1. Riconciliazione

   * Mantieni **[!UICONTROL Update or insert]** selezionato per impostazione predefinita.
   * Mantenere l&#39;opzione **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** modalità in modo che i record esistenti nel database vengano modificati con i dati del file di testo.
   * Selezionare i campi **[!UICONTROL Birth date]**, **[!UICONTROL Name]** quindi **[!UICONTROL Company]** assegnare loro una chiave di riconciliazione.

      ![](assets/s_ncs_user_import_example04_02.png)

1. Avvio dell&#39;importazione

   * Clic **[!UICONTROL Start]**.

      Nella finestra di tracciamento potete verificare che l’importazione sia riuscita e visualizzare il numero di record elaborati.

      ![](assets/s_ncs_user_import_example06_02.png)

   * Nella tabella dei destinatari verificare che i record siano stati modificati dall&#39;operazione.

      ![](assets/s_ncs_user_import_example06_03.png)

### Esempio: Arricchire i valori con quelli di un file esterno {#example--enrich-the-values-with-those-of-an-external-file}

È necessario modificare alcuni campi di una tabella di database da un file di testo, dando priorità ai valori contenuti nel database.

In questo esempio, è possibile vedere che alcuni campi nel file di testo hanno un valore, mentre i campi corrispondenti nel database sono vuoti. Altri campi contengono un valore diverso da quello contenuto nel database.

* Contenuto del file di testo da importare.

   ![](assets/s_ncs_user_import_example02_03.png)

* Stato del database prima dell&#39;importazione

   ![](assets/s_ncs_user_import_example06_04.png)

Effettuate le seguenti operazioni:

1. Scelta di un modello

   Applicate la procedura descritta nell&#39;esempio 2 precedente.

1. File da importare

   Selezionate il file da importare.

1. Associazione di campi

   Applicate la procedura descritta nell&#39;esempio 2 precedente.

   Nell&#39;anteprima delle prime righe del file, è possibile vedere che il file contiene aggiornamenti per alcuni record.

1. Riconciliazione

   * Passate alla tabella e selezionate l&#39; **[!UICONTROL Update]** operazione.
   * Selezionare l&#39;opzione **[!UICONTROL Reject entity]** per il **[!UICONTROL Management of doubles]** campo.
   * Mantenere l&#39;opzione **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** modalità in modo che i record esistenti nel database vengano modificati con i dati del file di testo.
   * Posizionare il cursore sul **[!UICONTROL Last name (@lastName)]** nodo e selezionare l&#39; **[!UICONTROL Update only if destination is empty]** opzione.
   * Ripetere questa operazione per il **[!UICONTROL Company (@company)]** nodo.
   * Assegnare una chiave di riconciliazione ai campi **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** e **[!UICONTROL First name]**.

      ![](assets/s_ncs_user_import_example04_03.png)

1. Avvio dell&#39;importazione

   Clic **[!UICONTROL Start]**.

   Consultare la tabella dei destinatari per verificare che i record siano stati modificati dall&#39;importazione.

   ![](assets/s_ncs_user_import_example06_05.png)

   Solo i valori vuoti sono stati sostituiti dai valori del file di testo, ma il valore esistente nel database non è stato sovrascritto dal valore del file di importazione.

### Esempio: Aggiornare e arricchire i valori da quelli di un file esterno {#example--update-and-enrich-the-values-from-those-in-an-external-file}

È necessario modificare alcuni campi di una tabella di database da un file di testo, dando priorità ai valori contenuti nel file di testo.

In questo esempio, alcuni campi nel file di testo hanno un valore vuoto, mentre i campi corrispondenti nel database non sono vuoti. Altri campi contengono un valore diverso da quello del database.

* Contenuto del file di testo da importare.

   ![](assets/s_ncs_user_import_example02_04.png)

* Stato del database prima dell&#39;importazione

   ![](assets/s_ncs_user_import_example06_07.png)

1. Scelta di un modello

   Applicate la procedura descritta nell&#39;esempio 2 precedente.

1. File da importare

   Selezionate il file da importare.

   Nell&#39;anteprima delle prime righe del file, è possibile vedere che il file contiene campi vuoti e aggiornamenti per alcuni record.

1. Associazione di campi

   Applicate la procedura descritta nell&#39;esempio 2 precedente.

1. Riconciliazione

   * Vai alla tabella e seleziona **[!UICONTROL Update]**.
   * Selezionare l&#39;opzione **[!UICONTROL Reject entity]** per il **[!UICONTROL Management of doubles]** campo.
   * Lasciare l&#39;opzione **[!UICONTROL Management of duplicates]** in **[!UICONTROL Update]** modalità per i record esistenti nel database da modificare con i dati del file di testo.
   * Posizionare il cursore sul **[!UICONTROL Account number (@account)]** nodo e selezionare l&#39;opzione **[!UICONTROL Take empty values into account]**.
   * Selezionare i campi **[!UICONTROL Birth date]**, **[!UICONTROL E-mail]** quindi **[!UICONTROL First name]** assegnare loro una chiave di riconciliazione.

      ![](assets/s_ncs_user_import_example04_04.png)

1. Avvio dell&#39;importazione

   * Clic **[!UICONTROL Start]**.
   * Consultare la tabella dei destinatari per verificare che i record siano stati modificati dall&#39;operazione.

      ![](assets/s_ncs_user_import_example06_06.png)

      I valori del file di testo vuoto hanno sovrascritto quelli presenti nel database. I valori esistenti nel database sono stati aggiornati con quelli nel file di importazione in linea con l&#39; **[!UICONTROL Update]** opzione selezionata per i duplicati al punto 4.

## Importazione di dati da un flusso di lavoro {#importing-data-from-a-workflow}

I flussi di lavoro possono essere un modo utile per automatizzare alcuni dei processi di importazione. Sia che importi dati da un file locale o da un SFTP, puoi utilizzare i flussi di lavoro per standardizzare le procedure di gestione dei dati.

Per ulteriori informazioni sull&#39;importazione di dati da un flusso di lavoro, consultare [questa sezione](../../workflow/using/importing-data.md).
