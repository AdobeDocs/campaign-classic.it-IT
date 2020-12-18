---
solution: Campaign Classic
product: campaign
title: Caricamento dati (file)
description: Ulteriori informazioni sull'attività del flusso di lavoro di caricamento dei dati (file)
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 15%

---


# Caricamento dati (file){#data-loading-file}

## Usa {#use}

L&#39;attività **[!UICONTROL Data loading (File)]** consente di accedere direttamente a un&#39;origine di dati esterni e di utilizzarla in  Adobe Campaign. Infatti, tutti i dati richiesti per le operazioni di targeting non sono sempre presenti nel database Adobe Campaign : può essere reso disponibile in file esterni.

Il file da caricare può essere specificato dalla transizione o calcolato durante l&#39;esecuzione di questa attività. Ad esempio, può essere l&#39;elenco dei 10 prodotti preferiti di un cliente i cui acquisti vengono gestiti in un database esterno.

La sezione superiore della finestra di configurazione per questa attività consente di definire il formato del file. A questo scopo, usate un file di esempio con lo stesso formato di quello da importare. Questo file può essere memorizzato localmente o sul server.

>[!CAUTION]
>
>Sono supportati solo i file di struttura &quot;semplici&quot; (ad esempio CSV, TXT ecc.). Si consiglia di non utilizzare il formato XML.

![](assets/s_advuser_wf_etl_file.png)

È possibile definire un processo preliminare da eseguire durante l&#39;importazione del file, ad esempio per non decomprimere il file sul server (e quindi risparmiare spazio per il file decompresso) ma per includere la decompressione nell&#39;elaborazione del file. Selezionate l&#39;opzione **[!UICONTROL Pre-process the file]** e scegliete una delle 3 opzioni seguenti: **[!UICONTROL None]**, **[!UICONTROL Decompression]** (zcat) o **[!UICONTROL Decrypt]** (gpg).

![](assets/preprocessing-dataloading.png)

Per ulteriori informazioni, consulta questa sezione: [Estrazione o decrittografia di un file prima di elaborare](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing).

## Definizione del formato di file {#defining-the-file-format}

Quando si carica un file, il formato della colonna viene rilevato automaticamente con i parametri predefiniti per ciascun tipo di dati. È possibile modificare questi parametri predefiniti al fine di specificare i processi specifici da applicare ai dati, in particolare in caso di errore o di valore vuoto.

A questo scopo, selezionare **[!UICONTROL Click here to change the file format...]** nella finestra principale dell&#39;attività **[!UICONTROL Data loading (file)]**. Viene aperta la finestra dei dettagli del formato.

![](assets/file_loading_columns_format.png)

È quindi possibile modificare la formattazione generale del file e di ciascuna colonna.

La formattazione generale dei file consente di definire il modo in cui le colonne verranno riconosciute (codifica file, separatori utilizzati, ecc.).

La formattazione della colonna ti consente di definire il valore di elaborazione di ciascuna colonna:

* **[!UICONTROL Ignore column]**: non elabora questa colonna durante il caricamento dei dati.
* **[!UICONTROL Data type]**: specifica il tipo di dati previsto per ogni colonna.
* **[!UICONTROL Allow NULLs]**: specifica come gestire i valori vuoti.

   * **[!UICONTROL Adobe Campaign default]**: genera un errore solo per i campi numerici, altrimenti inserisce un valore NULL.
   * **[!UICONTROL Empty value allowed]**: autorizza valori vuoti. Pertanto, viene inserito il valore NULL.
   * **[!UICONTROL Always populated]**: se un valore è vuoto, genera un errore.

* **[!UICONTROL Length]**: specifica il numero massimo di caratteri per il tipo di dati  **** stringa.
* **[!UICONTROL Format]**: definisce il formato di ora e data.
* **[!UICONTROL Data transformation]**: Definisce se è necessario applicare un processo relativo alle maiuscole/minuscole in una  **stringa**.

   * **[!UICONTROL None]**: la stringa importata non viene modificata.
   * **[!UICONTROL First letter in upper case]**: la prima lettera di ciascuna parola della stringa inizia con una lettera maiuscola.
   * **[!UICONTROL Upper case]**: tutti i caratteri nella stringa sono in lettere maiuscole.
   * **[!UICONTROL Lower case]**: tutti i caratteri nella stringa sono in lettere maiuscole.

* **[!UICONTROL White space management]**: specifica se alcuni spazi devono essere ignorati in una stringa. Il valore **[!UICONTROL Ignore spaces]** consente di ignorare solo gli spazi all&#39;inizio e alla fine di una stringa.
* **[!UICONTROL Error processings]**: definisce il comportamento in caso di errore.

   * **[!UICONTROL Ignore the value]**: il valore viene ignorato. Nel registro di esecuzione del flusso di lavoro viene generato un avviso.
   * **[!UICONTROL Reject line]**: l’intera linea non viene elaborata.
   * **[!UICONTROL Use a default value in case of error]**: sostituisce il valore che causava l’errore con uno predefinito, definito nel campo **[!UICONTROL Default value]**.
   * **[!UICONTROL Reject the line when there is no remapping value]**: l&#39;intera linea viene elaborata solo se è stata definita una mappatura per il valore errato (vedere l&#39; **[!UICONTROL Mapping]** opzione di seguito).
   * **[!UICONTROL Use a default value in case the value is not remapped]**: sostituisce il valore che causava l&#39;errore con un valore predefinito, definito nel  **[!UICONTROL Default value]** campo, a meno che non sia stata definita una mappatura per il valore errato (vedere l&#39; **[!UICONTROL Mapping]** opzione seguente).

* **[!UICONTROL Default value]**: specifica il valore predefinito in base all’elaborazione dell’errore selezionata.
* **[!UICONTROL Mapping]**: questo campo è disponibile solo nella configurazione dei dettagli delle colonne (a cui si accede mediante un doppio clic o tramite le opzioni a destra dell’elenco delle colonne). In questo modo alcuni valori vengono trasformati al momento dell’importazione. Ad esempio, puoi trasformare &quot;tre&quot; in &quot;3&quot;.

## Esempio: Raccolta di dati e caricamento nel database {#example--collecting-data-and-loading-it-in-the-database}

L&#39;esempio seguente consente di raccogliere un file sul server ogni giorno, caricarne il contenuto e aggiornare i dati nel database in base alle informazioni in esso contenute. Il file da raccogliere contiene informazioni sui clienti che possono aver effettuato acquisti (per più o meno di 3.000 Euro), chiesto un rimborso per un acquisto o visitato il negozio senza acquistare nulla. A seconda di queste informazioni, nel database verranno applicati diversi processi al relativo profilo.

![](assets/s_advuser_load_file_sample_0.png)

1. Il raccoglitore di file consente di recuperare i file memorizzati in una directory, a seconda della frequenza specificata.

   La scheda **[!UICONTROL Directory]** contiene informazioni sui file da recuperare. Nel nostro esempio, tutti i file in formato testo i cui nomi contengono la parola &#39;clienti&#39; e che sono memorizzati nella directory tmp/ Adobe/Dati/file del server verranno recuperati.

   L&#39;utilizzo di **[!UICONTROL File collector]** è descritto nella sezione [Raccolta file](../../workflow/using/file-collector.md).

   ![](assets/s_advuser_load_file_sample_1.png)

   La scheda **[!UICONTROL Schedule]** consente di pianificare l&#39;esecuzione del raccoglitore, ad esempio per specificare la frequenza con cui verrà controllata la presenza di questi file.

   Qui, vogliamo attivare il collettore ogni giorno alle 22.00.

   ![](assets/s_advuser_load_file_sample_2.png)

   A questo scopo, fate clic sul pulsante **[!UICONTROL Change...]** nella parte inferiore destra dello strumento di modifica e configurate la pianificazione.

   Per ulteriori informazioni, vedere [Pianificatore](../../workflow/using/scheduler.md).

1. Quindi configurate l&#39;attività di caricamento dei dati (file) per indicare la modalità di lettura dei file raccolti. A questo scopo, selezionate un file di esempio con la stessa struttura dei file da caricare.

   ![](assets/s_advuser_load_file_sample_3.png)

   Qui il file contiene cinque colonne:

   * la prima colonna contiene un codice che coincide con l’evento: acquisto (più o meno di 3.000 euro), nessun acquisto o rimborso per uno o più acquisti.
   * le quattro colonne seguenti contengono nome, cognome, e-mail e numero di account del cliente.

   La configurazione del formato del file da caricare coincide con quella definita durante l&#39;importazione di dati in  Adobe Campaign. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/importing-data.md#step-2---source-file-selection).

1. Nell&#39;attività divisa, specificate i sottoinsiemi da creare, in base al valore della colonna **Event**.

   L&#39;attività Split è dettagliata nella sezione.

   ![](assets/s_advuser_load_file_sample_4.png)

   Per ciascun sottoinsieme, specificate uno dei valori nella colonna **Evento**.

   ![](assets/s_advuser_load_file_sample_5.png)

   L&#39;attività **[!UICONTROL Split]** conterrà pertanto le seguenti informazioni:

   ![](assets/s_advuser_load_file_sample_6.png)

1. Specificare quindi i processi da eseguire per ciascun tipo di popolazione. Nel nostro esempio, stiamo andando **[!UICONTROL Update the data]** nel database. A questo scopo, inserite un&#39;attività **[!UICONTROL Update data]** alla fine di ogni transizione in uscita dall&#39;attività divisa.

   L&#39;attività **[!UICONTROL Update data]** è dettagliata nella sezione [Aggiorna dati](../../workflow/using/update-data.md).

