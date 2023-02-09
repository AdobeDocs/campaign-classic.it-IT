---
product: campaign
title: Configurazione dei processi di esportazione
description: Scopri come configurare ed eseguire processi di esportazione in Campaign Classic.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '926'
ht-degree: 2%

---

# Configurare i processi di esportazione {#executing-export-jobs}

![](../../assets/common.svg)

I processi di esportazione consentono di accedere ed estrarre dati dal database: contatti, client, elenchi, segmenti, ecc.

Ad esempio, può essere utile utilizzare i dati di tracciamento delle campagne (cronologia di tracciamento, ecc.) in un foglio di calcolo. I dati di output possono essere in formato TXT, CSV, TAB o XML.

La procedura guidata di esportazione consente di configurare un’esportazione, definirne le opzioni e avviarne l’esecuzione. Si tratta di una serie di schermate il cui contenuto dipende dal tipo di esportazione (semplice o multipla) e dai diritti dell’operatore.

Viene visualizzata la procedura guidata di esportazione dopo la creazione di un nuovo processo di esportazione (vedi [Creazione di processi di importazione ed esportazione](../../platform/using/creating-import-export-jobs.md).

## Passaggio 1: scegli il modello di esportazione {#step-1---choosing-the-export-template}

Quando si avvia la procedura guidata di esportazione, è innanzitutto necessario selezionare un modello. Ad esempio, per configurare l’esportazione dei destinatari che si sono registrati di recente, effettua le seguenti operazioni:

1. Seleziona la **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** cartella.
1. Fai clic su **Nuovo** quindi fai clic su **Esporta** per creare il modello di esportazione.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Fai clic sulla freccia a destra della **[!UICONTROL Export template]** per selezionare il modello, oppure fai clic su **[!UICONTROL Select link]** per sfogliare l&#39;albero.

   Il modello nativo è **[!UICONTROL New text export]**. Questo modello non deve essere modificato, ma puoi duplicarlo per configurarne uno nuovo. Per impostazione predefinita, i modelli di esportazione vengono salvati in **[!UICONTROL Resources > Templates > Job templates]** nodo.

1. Immettere un nome per l&#39;esportazione nel **[!UICONTROL Label]** campo . Puoi aggiungere una descrizione.
1. Seleziona il tipo di esportazione. Esistono due possibili tipi di esportazione: **[!UICONTROL Simple export]** per esportare un solo file, e **[!UICONTROL Multiple export]** per esportare più file in una singola esecuzione, da uno o più tipi di documento di origine.

## Passaggio 2 - Tipo di file da esportare {#step-2---type-of-file-to-export}

Selezionare il tipo di documento da esportare, ovvero lo schema dei dati da esportare.

Per impostazione predefinita, quando l’esportazione viene avviata dalla **[!UICONTROL Jobs]** i dati provengono dalla tabella dei destinatari. Quando l’esportazione viene avviata da un elenco di dati (dal **[!UICONTROL right click > Export]** , la tabella a cui appartengono i dati viene automaticamente compilata nel **[!UICONTROL Document type]** campo .

![](assets/s_ncs_user_export_wizard02.png)

* Per impostazione predefinita, la **[!UICONTROL Download the file generated on the server after the export]** è selezionata. In **[!UICONTROL Local file]** compilare il nome e il percorso del file da creare oppure sfogliare il disco locale facendo clic sulla cartella a destra del campo. È possibile deselezionare questa opzione per immettere il percorso di accesso e il nome del file di output del server.

   >[!NOTE]
   >
   >I processi di importazione ed esportazione automatici vengono sempre eseguiti sul server.
   >
   >Per esportare solo alcuni dati, fai clic su **[!UICONTROL Advanced parameters]** e immettere il numero di righe da esportare nel campo appropriato.

* Puoi creare un’esportazione differenziale per esportare solo i record modificati dall’ultima esecuzione. A questo scopo, fai clic sul pulsante **[!UICONTROL Advanced parameters]** fai clic sul collegamento **[!UICONTROL Differential export]** , quindi seleziona **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   Devi immettere la data dell’ultima modifica. Può essere recuperato da un campo o calcolato.

## Passaggio 3: definire il formato di output {#step-3---defining-the-output-format}

Selezionare un formato di output per il file di esportazione. È possibile utilizzare i seguenti formati: testo, testo a colonna fissa, CSV e XML.

![](assets/s_ncs_user_export_wizard03.png)

* Per **[!UICONTROL Text]** selezionare i delimitatori per separare le colonne (tabulazioni, virgole, punti o punti o personalizzati) e le stringhe (virgolette singole o doppie o nessuna).
* Per **[!UICONTROL text]** e **[!UICONTROL CSV]**, puoi selezionare l’opzione **[!UICONTROL Use first lines as column titles]**.
* Indicare il formato della data e il formato del numero. A questo scopo, fai clic sul pulsante **[!UICONTROL Edit]** per il campo interessato e utilizza l&#39;editor.
* Per i campi contenenti valori enumerati, puoi selezionare **[!UICONTROL Export labels instead of internal values of enumerations]**. Ad esempio, il titolo può essere memorizzato nel modulo **1=Sig.**, **2=Mancanza**, **3=Sig.ra**. Se questa opzione è selezionata, **Sig.**, **Miss** e **Sig.ra** verranno esportati.

## Passaggio 4: selezione dei dati {#step-4---data-selection}

Seleziona i campi da esportare. Per eseguire questa operazione:

1. Fai doppio clic sui campi desiderati nella sezione **[!UICONTROL Available fields]** per aggiungerli al **[!UICONTROL Output columns]** sezione .
1. Utilizzare le frecce a destra dell’elenco per definire l’ordine dei campi nel file di output.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Fai clic sul pulsante **[!UICONTROL Add]** per attivare le funzioni. Per ulteriori informazioni, consulta [Elenco delle funzioni](../../platform/using/defining-filter-conditions.md#list-of-functions).

## Passaggio 5 - Ordinare le colonne {#step-5---sorting-columns}

Selezionare l’ordinamento delle colonne.

![](assets/s_ncs_user_export_wizard05.png)

## Passaggio 6: filtrare le condizioni {#step-6---filter-conditions-}

Puoi aggiungere condizioni di filtro per evitare di esportare tutti i dati. La configurazione di questo filtro è la stessa del targeting del destinatario nella procedura guidata di consegna. Consulta [questa pagina](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

## Passaggio 7 - Formattazione dei dati {#step-7---data-formatting}

È possibile modificare l’ordine e l’etichetta dei campi per il file di output e applicare le trasformazioni ai dati di origine.

* Per modificare l’ordine delle colonne da esportare, selezionare la colonna interessata e utilizzare le frecce blu a destra della tabella.
* Per modificare l’etichetta di un campo, fai clic nella cella del **[!UICONTROL Label]** che corrisponde al campo da modificare e immettere la nuova etichetta. Premere Invio sulla tastiera per confermare.
* Per applicare una trasformazione caso al contenuto di un campo, selezionala dalla **[!UICONTROL Transformation]** colonna. Puoi selezionare:

   * Passa al carattere minuscolo
   * Passa al carattere maiuscolo
   * Prima lettera in carattere maiuscolo

   ![](assets/s_ncs_user_export_wizard06.png)

* Fai clic su **[!UICONTROL Add a calculated field]** per creare un nuovo campo calcolato (ad esempio, una colonna contenente cognome + nome). Per ulteriori informazioni, consulta [Campi calcolati](../../platform/using/executing-import-jobs.md#calculated-fields).

Se esporti una raccolta di elementi (ad esempio le sottoscrizioni dei destinatari, gli elenchi a cui appartengono, ecc.), devi specificare il numero di elementi nella raccolta da esportare.

![](assets/s_ncs_user_export_wizard06_c.png)

## Passaggio 8: anteprima dei dati {#step-8---data-preview}

Fai clic su **[!UICONTROL Start the preview of the data]** per un’anteprima del risultato dell’esportazione. Per impostazione predefinita, vengono visualizzate le prime 200 righe. Per modificare questo valore, fai clic sulle frecce a destra del **[!UICONTROL Lines to display]** campo .

![](assets/s_ncs_user_export_wizard07.png)

Fai clic sulle schede nella parte inferiore della procedura guidata per passare dall’anteprima dei risultati in colonne ai risultati in XML. È inoltre possibile visualizzare le query SQL generate.

## Passaggio 9: avviare l’esportazione {#step-9---launching-the-export}

Fai clic su **[!UICONTROL Start]** per avviare l’esportazione dei dati.

![](assets/s_ncs_user_export_wizard08.png)

Puoi quindi monitorare l’esecuzione del processo di importazione (vedi [Monitorare l’esecuzione dei processi](../../platform/using/monitoring-jobs-execution.md).
