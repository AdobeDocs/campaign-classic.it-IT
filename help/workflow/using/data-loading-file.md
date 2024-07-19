---
product: campaign
title: Caricamento dati (file)
description: Ulteriori informazioni sull’attività del flusso di lavoro Caricamento dati (file)
feature: Workflows, Data Management Activity
exl-id: a380e486-a40c-4bf6-b7f4-7dcd76c34085
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1140'
ht-degree: 14%

---

# Caricamento dati (file){#data-loading-file}

## Utilizzare {#use}

L&#39;attività **[!UICONTROL Data loading (File)]** ti consente di accedere direttamente a un&#39;origine di dati esterni e di utilizzarla in Adobe Campaign. Infatti, tutti i dati necessari per le operazioni di targeting non sempre si trovano nel database di Adobe Campaign: possono essere resi disponibili in file esterni.

Il file da caricare può essere specificato dalla transizione o calcolato durante l’esecuzione di questa attività. Ad esempio, può essere l’elenco dei 10 prodotti preferiti di un cliente i cui acquisti vengono gestiti in un database esterno.

La sezione superiore della finestra di configurazione per questa attività ti consente di definire il formato del file. A questo scopo, utilizza un file di esempio con lo stesso formato di quello da importare. Questo file può essere archiviato localmente o sul server.

>[!CAUTION]
>
>Sono supportati solo i file con struttura &quot;flat&quot; (ad esempio CSV, TXT, ecc.). Non è consigliabile utilizzare il formato XML.

![](assets/s_advuser_wf_etl_file.png)

## Applica fase di pre-elaborazione {#pre-processing}

È possibile definire un pre-processo da eseguire durante l&#39;importazione dei file, ad esempio per non dover decomprimere il file sul server (e quindi risparmiare spazio per il file decompresso) ma per includere la decompressione nell&#39;elaborazione dei file. [Scopri come decomprimere o decrittografare un file prima dell&#39;elaborazione](../../platform/using/unzip-decrypt.md).

A tale scopo, selezionare l&#39;opzione **[!UICONTROL Pre-process the file]** e scegliere una delle tre opzioni seguenti: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) o **[!UICONTROL Decrypt]** (gpg).

![](assets/preprocessing-dataloading.png)

>[!CAUTION]
>
>Se si utilizza una distribuzione ibrida o on-premise, i comandi di pre-elaborazione potrebbero non funzionare come preconfigurati, in quanto la configurazione predefinita utilizza &#39;zcat&#39;, che non è disponibile in Windows. In tal caso, è necessario modificare il nodo **preProcessCommand** nel file di configurazione del server (serverConf.xml) in base alle proprie esigenze. [Scopri come configurare i comandi di pre-elaborazione nel file di configurazione del server](../../installation/using/the-server-configuration-file.md#preprocesscommand)

## Definizione del formato del file {#defining-the-file-format}

Quando si carica un file, il formato colonna viene rilevato automaticamente con i parametri predefiniti per ogni tipo di dati. È possibile modificare questi parametri predefiniti al fine di specificare i processi specifici da applicare ai dati, in particolare in caso di errore o di valore vuoto.

A tale scopo, selezionare **[!UICONTROL Click here to change the file format...]** nella finestra principale dell&#39;attività **[!UICONTROL Data loading (file)]**. Viene visualizzata la finestra dei dettagli del formato.

![](assets/file_loading_columns_format.png)

È quindi possibile modificare la formattazione generale del file e la formattazione di ogni colonna.

La formattazione generale del file consente di definire il modo in cui le colonne verranno riconosciute (codifica file, separatori utilizzati, ecc.).

La formattazione della colonna ti consente di definire il valore di elaborazione di ciascuna colonna:

>[!NOTE]
>
>Puoi aggiungere tutte le colonne che desideri. La lunghezza massima dei valori in ogni colonna è determinata dal tipo di dati scelto.

* **[!UICONTROL Ignore column]**: non elabora questa colonna durante il caricamento dei dati.
* **[!UICONTROL Data type]**: specifica il tipo di dati previsto per ogni colonna.
* **[!UICONTROL Allow NULLs]**: specifica come gestire i valori vuoti.

   * **[!UICONTROL Adobe Campaign default]**: genera un errore solo per i campi numerici, altrimenti inserisce un valore NULL.
   * **[!UICONTROL Empty value allowed]**: autorizza valori vuoti. Pertanto, viene inserito il valore NULL.
   * **[!UICONTROL Always populated]**: se un valore è vuoto, genera un errore.

* **[!UICONTROL Length]**: specifica il numero massimo di caratteri per il tipo di dati **string**.
* **[!UICONTROL Format]**: definisce il formato di data e ora.
* **[!UICONTROL Data transformation]**: definisce se è necessario applicare un processo relativo alle maiuscole/minuscole dei caratteri a una **stringa**.

   * **[!UICONTROL None]**: la stringa importata non è modificata.
   * **[!UICONTROL First letter in upper case]**: la prima lettera di ogni parola della stringa inizia con una maiuscola.
   * **[!UICONTROL Upper case]**: tutti i caratteri nella stringa sono in maiuscolo.
   * **[!UICONTROL Lower case]**: tutti i caratteri nella stringa sono in minuscolo.

* **[!UICONTROL White space management]**: specifica se alcuni spazi devono essere ignorati in una stringa. Il valore **[!UICONTROL Ignore spaces]** consente di ignorare solo gli spazi all&#39;inizio e alla fine di una stringa.
* **[!UICONTROL Error processings]**: definisce il comportamento in caso di errore.

   * **[!UICONTROL Ignore the value]**: il valore viene ignorato. Nel registro di esecuzione del flusso di lavoro viene generato un avviso.
   * **[!UICONTROL Reject line]**: l’intera linea non viene elaborata.
   * **[!UICONTROL Use a default value in case of error]**: sostituisce il valore che causava l’errore con uno predefinito, definito nel campo **[!UICONTROL Default value]**.
   * **[!UICONTROL Reject the line when there is no remapping value]**: l&#39;intera riga viene elaborata solo se è stata definita una mappatura per il valore errato (vedere l&#39;opzione **[!UICONTROL Mapping]** di seguito).
   * **[!UICONTROL Use a default value in case the value is not remapped]**: sostituisce il valore che causava l&#39;errore con un valore predefinito, definito nel campo **[!UICONTROL Default value]**, a meno che non sia stata definita una mappatura per il valore errato (vedere l&#39;opzione **[!UICONTROL Mapping]** di seguito).

* **[!UICONTROL Default value]**: specifica il valore predefinito in base all’elaborazione dell’errore selezionata.
* **[!UICONTROL Mapping]**: questo campo è disponibile solo nella configurazione dei dettagli delle colonne (accessibile tramite un doppio clic o tramite le opzioni a destra dell&#39;elenco delle colonne). Questo trasforma alcuni valori quando vengono importati. Ad esempio, puoi trasformare &quot;tre&quot; in &quot;3&quot;.

## Esempio: raccolta dei dati e caricamento nel database {#example--collecting-data-and-loading-it-in-the-database}

L&#39;esempio seguente consente di raccogliere un file sul server ogni giorno, caricarne il contenuto e aggiornare i dati nel database in base alle informazioni in esso contenute. Il fascicolo da raccogliere contiene informazioni sui clienti che possono aver effettuato acquisti (per un valore superiore o inferiore a 3,000 euro), chiesto un rimborso su un acquisto o visitato il negozio senza acquistare nulla. A seconda di queste informazioni, vari processi verranno applicati al loro profilo nel database.

![](assets/s_advuser_load_file_sample_0.png)

1. Il raccoglitore di file consente di recuperare i file memorizzati in una directory, a seconda della frequenza specificata.

   La scheda **[!UICONTROL Directory]** contiene informazioni sui file da recuperare. Nel nostro esempio, verranno recuperati tutti i file in formato testo i cui nomi contengono la parola &quot;clienti&quot; e che sono memorizzati nella directory tmp/Adobe/Data/files del server.

   L&#39;utilizzo di **[!UICONTROL File collector]** è descritto nella sezione [Raccoglitore file](file-collector.md).

   ![](assets/s_advuser_load_file_sample_1.png)

   La scheda **[!UICONTROL Schedule]** consente di pianificare l&#39;esecuzione dell&#39;agente di raccolta, ovvero di specificare la frequenza con cui verrà verificata la presenza di questi file.

   In questo caso, vogliamo attivare il raccoglitore ogni giorno alle 21.

   ![](assets/s_advuser_load_file_sample_2.png)

   A tale scopo, fare clic sul pulsante **[!UICONTROL Change...]** situato nella sezione inferiore destra dello strumento di modifica e configurare la pianificazione.

   Per ulteriori informazioni, consulta [Scheduler](scheduler.md).

1. Quindi configura l’attività di caricamento dei dati (file) per indicare come devono essere letti i file raccolti. A questo scopo, seleziona un file di esempio con la stessa struttura dei file da caricare.

   ![](assets/s_advuser_load_file_sample_3.png)

   In questo caso, il file contiene cinque colonne:

   * la prima colonna contiene un codice che coincide con l’evento: acquisto (più o meno di 3.000 euro), nessun acquisto o rimborso per uno o più acquisti.
   * le quattro colonne seguenti contengono il nome, il cognome, l’e-mail e il numero di account del cliente.

   La configurazione del formato del file da caricare coincide con quella definita durante un’importazione di dati in Adobe Campaign. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/executing-import-jobs.md#step-2---source-file-selection).

1. Nell&#39;attività divisa, specificare i sottoinsiemi da creare, in base al valore della colonna **Event**.

   L’attività Dividi è descritta nella sezione.

   ![](assets/s_advuser_load_file_sample_4.png)

   Per ogni sottoinsieme, specifica uno dei valori nella colonna **Evento**.

   ![](assets/s_advuser_load_file_sample_5.png)

   L&#39;attività **[!UICONTROL Split]** conterrà pertanto le seguenti informazioni:

   ![](assets/s_advuser_load_file_sample_6.png)

1. Specificare quindi i processi da eseguire per ciascun tipo di popolazione. Nel nostro esempio, andremo a **[!UICONTROL Update the data]** nel database. A questo scopo, inserisci un&#39;attività **[!UICONTROL Update data]** alla fine di ogni transizione in uscita dall&#39;attività divisa.

   L&#39;attività **[!UICONTROL Update data]** è descritta nella sezione [Update data](update-data.md).
