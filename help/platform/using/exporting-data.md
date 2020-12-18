---
solution: Campaign Classic
product: campaign
title: Esportazione dei dati
description: Esportazione dei dati
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 1%

---


# Esportazione di dati{#exporting-data}

## Esportazione guidata {#export-wizard}

I parametri di esportazione vengono registrati tramite una procedura guidata. Il modulo di esportazione generico è disponibile come standard e consente di accedere ed estrarre dati dal database: contatti, client, elenchi, segmenti, ecc. Ad esempio, può essere utile utilizzare i dati di tracciamento campagna (cronologia di tracciamento, ecc.) in un foglio di calcolo. I dati di output possono essere in formato testo, CSV, TAB o XML.

### Passaggio 1 - Scelta del modello di esportazione {#step-1---choosing-the-export-template}

Quando si avvia la procedura guidata di esportazione, è innanzitutto necessario selezionare un modello. Ad esempio, per configurare l’esportazione dei destinatari che si sono registrati di recente, effettuate le seguenti operazioni:

1. Selezionare la cartella **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**.
1. Fate clic su **Nuovo**, quindi fate clic su **Esporta** per creare il modello di esportazione.

   ![](assets/s_ncs_user_export_wizard01.png)

1. Fare clic sulla freccia a destra del campo **[!UICONTROL Export template]** per selezionare il modello, oppure fare clic su **[!UICONTROL Select link]** per sfogliare la struttura.

   Il modello nativo è **[!UICONTROL New text export]**. Questo modello non deve essere modificato, ma può essere duplicato per configurare un nuovo modello. Per impostazione predefinita, i modelli di esportazione vengono salvati nel nodo **[!UICONTROL Resources > Templates > Job templates]**.

1. Immettete un nome per l&#39;esportazione nel campo **[!UICONTROL Label]**. Potete aggiungere una descrizione.
1. Selezionare il tipo di esportazione. Esistono due tipi possibili di esportazione: **[!UICONTROL Simple export]** per esportare un solo file e **[!UICONTROL Multiple export]** per esportare più file in una singola esecuzione, da uno o più tipi di documento di origine.

### Passaggio 2 - Tipo di file da esportare {#step-2---type-of-file-to-export}

Selezionare il tipo di documento da esportare, ad esempio lo schema dei dati da esportare.

Per impostazione predefinita, quando l&#39;esportazione viene avviata dal nodo **[!UICONTROL Jobs]**, i dati provengono dalla tabella del destinatario. Quando l&#39;esportazione viene avviata da un elenco di dati (dal menu **[!UICONTROL right click > Export]**), la tabella alla quale i dati appartengono viene automaticamente compilata nel campo **[!UICONTROL Document type]**.

![](assets/s_ncs_user_export_wizard02.png)

* Per impostazione predefinita, l&#39;opzione **[!UICONTROL Download the file generated on the server after the export]** è selezionata. Nel campo **[!UICONTROL Local file]**, immettere il nome e il percorso del file da creare, oppure sfogliare il disco locale facendo clic sulla cartella a destra del campo. Potete deselezionare questa opzione per immettere il percorso di accesso e il nome del file di output del server.

   >[!NOTE]
   >
   >I processi di importazione ed esportazione automatici vengono sempre eseguiti sul server.
   >
   >Per esportare solo alcuni dati, fare clic su **[!UICONTROL Advanced parameters]** e immettere il numero di righe da esportare nel campo appropriato.

* È possibile creare un&#39;esportazione differenziale per esportare solo i record modificati dall&#39;ultima esecuzione. A tal fine, fare clic sul collegamento **[!UICONTROL Advanced parameters]**, quindi fare clic sulla scheda **[!UICONTROL Differential export]**, quindi selezionare **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   È necessario immettere la data dell&#39;ultima modifica. Può essere recuperato da un campo o calcolato.

### Passaggio 3 - Definizione del formato di output {#step-3---defining-the-output-format}

Selezionare un formato di output per il file di esportazione. È possibile utilizzare i seguenti formati: testo, testo a colonna fissa, CSV e XML.

![](assets/s_ncs_user_export_wizard03.png)

* Per il formato **[!UICONTROL Text]**, selezionare i delimitatori in modo da separare le colonne (tabulazioni, virgole, punti e virgola o punti () e le stringhe (virgolette singole o doppie o nessuna).
* Per **[!UICONTROL text]** e **[!UICONTROL CSV]**, è possibile selezionare l&#39;opzione **[!UICONTROL Use first lines as column titles]**.
* Indica il formato della data e il formato del numero. A tale scopo, fare clic sul pulsante **[!UICONTROL Edit]** relativo al campo e utilizzare l&#39;editor.
* Per i campi contenenti valori enumerati, è possibile selezionare **[!UICONTROL Export labels instead of internal values of enumerations]**. Ad esempio, il titolo può essere memorizzato nel modulo **1=Sig.**,  **2=Miss**,  **3=Sig.ra**. Se questa opzione è selezionata, verranno esportati **Sig.**, **Miss** e **Sig.**.

### Passaggio 4 - Selezione dei dati {#step-4---data-selection}

Selezionare i campi da esportare. Per eseguire questa operazione:

1. Fare doppio clic sui campi desiderati nell&#39;elenco **[!UICONTROL Available fields]** per aggiungerli alla sezione **[!UICONTROL Output columns]**.
1. Utilizzare le frecce a destra dell&#39;elenco per definire l&#39;ordine dei campi nel file di output.

   ![](assets/s_ncs_user_export_wizard04.png)

1. Fare clic sul pulsante **[!UICONTROL Add]** per attivare le funzioni. Per ulteriori informazioni, fare riferimento a [Elenco di funzioni](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Passaggio 5 - Ordinamento delle colonne {#step-5---sorting-columns}

Selezionare l&#39;ordine di ordinamento delle colonne.

![](assets/s_ncs_user_export_wizard05.png)

### Passaggio 6 - Condizioni del filtro {#step-6---filter-conditions-}

È possibile aggiungere condizioni di filtro per evitare di esportare tutti i dati. La configurazione di questo filtro è la stessa del targeting del destinatario nella procedura guidata di consegna. Consulta [questa pagina](../../delivery/using/steps-defining-the-target-population.md).

![](assets/s_ncs_user_export_wizard05_b.png)

### Passaggio 7 - Formattazione dei dati {#step-7---data-formatting}

È possibile modificare l&#39;ordine e l&#39;etichetta dei campi per il file di output e applicare trasformazioni ai dati di origine.

* Per modificare l’ordine delle colonne da esportare, selezionare la colonna interessata e utilizzare le frecce blu a destra della tabella.
* Per modificare l&#39;etichetta di un campo, fare clic nella cella della colonna **[!UICONTROL Label]** che corrisponde al campo da modificare e immettere la nuova etichetta. Premere Invio sulla tastiera per confermare.
* Per applicare una trasformazione di maiuscole e minuscole al contenuto di un campo, selezionatelo dalla colonna **[!UICONTROL Transformation]**. Potete selezionare:

   * Passa alla lettera minuscola
   * Passa alla lettera maiuscola
   * Prima lettera in maiuscolo

   ![](assets/s_ncs_user_export_wizard06.png)

* Fare clic su **[!UICONTROL Add a calculated field]** se si desidera creare un nuovo campo calcolato (ad esempio, una colonna contenente cognome + nome). Per ulteriori informazioni, fare riferimento a [Campi calcolati](../../platform/using/importing-data.md#calculated-fields).

Se state esportando una raccolta di elementi (ad esempio, iscrizioni dei destinatari, elenchi a cui appartengono, ecc.), dovete specificare il numero di elementi nella raccolta che desiderate esportare.

![](assets/s_ncs_user_export_wizard06_c.png)

### Passaggio 8 - Anteprima dati {#step-8---data-preview}

Fate clic su **[!UICONTROL Start the preview of the data]** per un&#39;anteprima del risultato dell&#39;esportazione. Per impostazione predefinita, vengono visualizzate le prime 200 righe. Per modificare questo valore, fare clic sulle frecce a destra del campo **[!UICONTROL Lines to display]**.

![](assets/s_ncs_user_export_wizard07.png)

Fare clic sulle schede nella parte inferiore della procedura guidata per passare dall&#39;anteprima dei risultati in colonne ai risultati in XML. È inoltre possibile visualizzare le query SQL generate.

### Passaggio 9 - Avvio dell&#39;esportazione {#step-9---launching-the-export}

Fare clic su **[!UICONTROL Start]** per avviare l&#39;esportazione dei dati.

![](assets/s_ncs_user_export_wizard08.png)

## Esportazione di dati tramite un flusso di lavoro {#exporting-data-via-a-workflow}

I flussi di lavoro possono essere un modo utile per automatizzare alcuni dei processi di esportazione o per esportare insiemi precisi di dati dopo aver utilizzato alcune delle attività di gestione dei dati disponibili per trasformare i dati.

Per ulteriori informazioni sull&#39;esportazione di dati da un flusso di lavoro, consultare [questa sezione](../../workflow/using/how-to-use-workflow-data.md).
