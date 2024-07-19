---
product: campaign
title: Configurazione dei processi di esportazione
description: Scopri come configurare ed eseguire i processi di esportazione in Campaign
feature: Overview
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 2%

---

# Configurare i processi di esportazione {#executing-export-jobs}



I processi di esportazione ti consentono di accedere ed estrarre dati dal database: contatti, client, elenchi, segmenti, ecc.

Ad esempio, può essere utile utilizzare i dati di tracciamento delle campagne (cronologia di tracciamento, ecc.) in un foglio di calcolo. I dati di output possono essere in formato TXT, CSV, TAB o XML.

L’esportazione guidata consente di configurare un’esportazione, definirne le opzioni e avviarne l’esecuzione. Si tratta di una serie di schermate il cui contenuto dipende dal tipo di esportazione (semplice o multipla) e dai diritti dell’operatore.

L&#39;esportazione guidata viene visualizzata dopo la creazione di un nuovo processo di esportazione (vedere [Creare processi di importazione ed esportazione](../../platform/using/creating-import-export-jobs.md).

## Passaggio 1: scegliere il modello di esportazione {#step-1---choosing-the-export-template}

Quando si avvia l&#39;esportazione guidata, è necessario selezionare un modello. Ad esempio, per configurare l’esportazione dei destinatari che si sono registrati di recente, effettua le seguenti operazioni:

1. Selezionare la cartella **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**.
1. Fai clic su **Nuovo**, quindi su **Esporta** per creare il modello di esportazione.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Fare clic sulla freccia a destra del campo **[!UICONTROL Export template]** per selezionare il modello oppure fare clic su **[!UICONTROL Select link]** per sfogliare la struttura.

   Il modello nativo è **[!UICONTROL New text export]**. Questo modello non deve essere modificato, ma puoi duplicarlo per configurarne uno nuovo. Per impostazione predefinita, i modelli di esportazione vengono salvati nel nodo **[!UICONTROL Resources > Templates > Job templates]**.

1. Immettere un nome da esportare nel campo **[!UICONTROL Label]**. Puoi aggiungere una descrizione.
1. Seleziona il tipo di esportazione. Esistono due possibili tipi di esportazione: **[!UICONTROL Simple export]** per esportare un solo file e **[!UICONTROL Multiple export]** per esportare più file in una singola esecuzione da uno o più tipi di documenti di origine.

## Passaggio 2: tipo di file da esportare {#step-2---type-of-file-to-export}

Selezionare il tipo di documento da esportare, ovvero lo schema dei dati da esportare.

Per impostazione predefinita, quando l&#39;esportazione viene avviata dal nodo **[!UICONTROL Jobs]** i dati provengono dalla tabella dei destinatari. Quando l&#39;esportazione viene avviata da un elenco di dati (dal menu **[!UICONTROL right click > Export]**), la tabella a cui appartengono i dati viene automaticamente compilata nel campo **[!UICONTROL Document type]**.

![](assets/s_ncs_user_export_wizard02.png)

* Per impostazione predefinita, l&#39;opzione **[!UICONTROL Download the file generated on the server after the export]** è selezionata. Nel campo **[!UICONTROL Local file]**, inserire il nome e il percorso del file da creare oppure sfogliare il disco locale facendo clic sulla cartella a destra del campo. È possibile deselezionare questa opzione per immettere il percorso di accesso e il nome del file di output del server.

  >[!NOTE]
  >
  >I processi di importazione ed esportazione automatici vengono sempre eseguiti sul server.
  >
  >Per esportare solo alcuni dati, fare clic su **[!UICONTROL Advanced parameters]** e immettere il numero di righe da esportare nel campo appropriato.

* È possibile creare un&#39;esportazione differenziale per esportare solo i record modificati dopo l&#39;ultima esecuzione. A tale scopo, fare clic sul collegamento **[!UICONTROL Advanced parameters]**, quindi sulla scheda **[!UICONTROL Differential export]** e selezionare **[!UICONTROL Activate differential export]**.

  ![](assets/s_ncs_user_export_wizard02_b.png)

  Immettere la data dell&#39;ultima modifica. Può essere recuperato da un campo o calcolato.

## Passaggio 3: definire il formato di output {#step-3---defining-the-output-format}

Selezionate un formato di output per il file di esportazione. È possibile utilizzare i seguenti formati: testo, testo a colonne fisse, CSV e XML.

![](assets/s_ncs_user_export_wizard03.png)

* Per il formato **[!UICONTROL Text]**, selezionare i delimitatori per separare le colonne (tabulazioni, virgole, punti e virgola o personalizzati) e le stringhe (virgolette singole o doppie o nessuna).
* Per **[!UICONTROL text]** e **[!UICONTROL CSV]**, è possibile selezionare l&#39;opzione **[!UICONTROL Use first lines as column titles]**.
* Indicare il formato della data e del numero. A tale scopo, fare clic sul pulsante **[!UICONTROL Edit]** per il campo interessato e utilizzare l&#39;editor.
* Per i campi contenenti valori enumerati, è possibile selezionare **[!UICONTROL Export labels instead of internal values of enumerations]**. Ad esempio, il titolo può essere memorizzato nel formato **1=Sig.**, **2=Miss**, **3=Signora**. Se questa opzione è selezionata, verranno esportati **Mr**, **Miss** e **Mrs**.

## Passaggio 4: selezione dei dati {#step-4---data-selection}

Selezionare i campi da esportare. Per eseguire questa operazione:

1. Fare doppio clic sui campi desiderati nell&#39;elenco **[!UICONTROL Available fields]** per aggiungerli alla sezione **[!UICONTROL Output columns]**.
1. Utilizzare le frecce a destra dell&#39;elenco per definire l&#39;ordine dei campi nel file di output.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Fare clic sul pulsante **[!UICONTROL Add]** per richiamare le funzioni. Per ulteriori informazioni, consulta [Elenco delle funzioni](../../platform/using/defining-filter-conditions.md#list-of-functions).

## Passaggio 5: ordinare le colonne {#step-5---sorting-columns}

Selezionare l&#39;ordinamento delle colonne.

![](assets/s_ncs_user_export_wizard05.png)

## Passaggio 6 - Condizioni del filtro {#step-6---filter-conditions-}

Puoi aggiungere condizioni di filtro per evitare di esportare tutti i dati. La configurazione di questo filtro è la stessa del targeting dei destinatari nella procedura guidata di consegna. Consulta [questa pagina](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

## Passaggio 7: formattazione dei dati {#step-7---data-formatting}

È possibile modificare l&#39;ordine e l&#39;etichetta dei campi per il file di output e applicare le trasformazioni ai dati di origine.

* Per modificare l’ordine delle colonne da esportare, seleziona la colonna interessata e utilizza le frecce blu a destra della tabella.
* Per modificare l&#39;etichetta di un campo, fare clic nella cella della colonna **[!UICONTROL Label]** che corrisponde al campo da modificare e immettere la nuova etichetta. Premere Invio sulla tastiera per confermare.
* Per applicare una trasformazione di maiuscole e minuscole al contenuto di un campo, selezionarlo dalla colonna **[!UICONTROL Transformation]**. Puoi selezionare:

   * Cambia in minuscolo
   * Cambia in maiuscolo
   * Prma lettera in maiuscolo

  ![](assets/s_ncs_user_export_wizard06.png)

* Fare clic su **[!UICONTROL Add a calculated field]** per creare un nuovo campo calcolato, ad esempio una colonna contenente cognome + nome. Per ulteriori informazioni, consulta [Campi calcolati](../../platform/using/executing-import-jobs.md#calculated-fields).

Se esporti una raccolta di elementi (ad esempio le sottoscrizioni dei destinatari, gli elenchi a cui appartengono e così via), devi specificare il numero di elementi della raccolta da esportare.

![](assets/s_ncs_user_export_wizard06_c.png)

## Passaggio 8: anteprima dei dati {#step-8---data-preview}

Fare clic su **[!UICONTROL Start the preview of the data]** per visualizzare un&#39;anteprima del risultato dell&#39;esportazione. Per impostazione predefinita, vengono visualizzate le prime 200 righe. Per modificare questo valore, fare clic sulle frecce a destra del campo **[!UICONTROL Lines to display]**.

![](assets/s_ncs_user_export_wizard07.png)

Fare clic sulle schede nella parte inferiore della procedura guidata per passare dall&#39;anteprima dei risultati nelle colonne ai risultati in XML. È inoltre possibile visualizzare le query SQL generate.

## Passaggio 9: avviare l’esportazione {#step-9---launching-the-export}

Fare clic su **[!UICONTROL Start]** per avviare l&#39;esportazione dei dati.

![](assets/s_ncs_user_export_wizard08.png)

È quindi possibile monitorare l&#39;esecuzione del processo di importazione (vedere [Monitorare l&#39;esecuzione dei processi](../../platform/using/monitoring-jobs-execution.md).
