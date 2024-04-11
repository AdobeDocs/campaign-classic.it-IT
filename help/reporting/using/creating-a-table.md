---
product: campaign
title: Creare una tabella
description: Creare una tabella
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Reporting, Monitoring
exl-id: 05f76bdf-6dcd-4360-9e72-0ba6a4dd0d5e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '2512'
ht-degree: 1%

---

# Creare una tabella{#creating-a-table}



È possibile aggiungere una tabella a un report per visualizzare i dati. Può trattarsi di una tabella pivot creata in base alle misurazioni del cubo, di un elenco con gruppo o di una tabella contenente una suddivisione dei valori.

![](assets/s_advuser_report_page_activity_05.png)

## Crea un elenco con gruppo {#creating-a-list-with-group}

A **[!UICONTROL List with group]** tipo tabella consente di raggruppare i dati nella tabella e di produrre statistiche su di essa. Ad esempio, puoi creare totali e subtotali per i dati. Ogni gruppo ha una propria linea di intestazione, dettagli e piè di pagina.

>[!CAUTION]
>
>Il **[!UICONTROL Page]** l’attività contenente la tabella deve essere preceduta da un **[!UICONTROL Query]** o **[!UICONTROL Script]** attività per raccogliere i dati da analizzare nel rapporto. Per ulteriori informazioni su queste attività, consulta [Raccogliere dati da analizzare](../../reporting/using/collecting-data-to-analyze.md) e [Attività script](../../reporting/using/advanced-functionalities.md#script-activity).

### Principio di funzionamento {#operating-principle}

Potrebbe essere necessario analizzare diverse categorie di dati contemporaneamente. Un elenco con gruppo consente di combinare i dati e creare statistiche su vari gruppi di dati all’interno della stessa tabella. A questo scopo, potete creare un gruppo nella tabella.

Nell’esempio seguente, il gruppo mostra tutte le campagne nel database, le consegne e il numero di messaggi inviati per consegna e per campagna.

Ti consente di elencare le campagne (**[!UICONTROL Label (Campaign)]**, l&#39;elenco delle consegne (**[!UICONTROL Label]** ) collegato alla campagna e consente di contare il numero di messaggi inviati per consegna (**[!UICONTROL Processed)]**, prima di aggiungerle per ogni campagna (**[!UICONTROL Sum(@processed)]** ).

![](assets/s_advuser_ergo_listgroup_005.png)

### Passaggi di implementazione {#implementation-steps}

Un esempio di implementazione completa è fornito qui: [Caso d’uso: creare un rapporto con un elenco di gruppi](#use-case--create-a-report-with-a-group-list).

Per creare una tabella di tipo &quot;Elenco con gruppo&quot;, tieni presente quanto segue:

1. Vai al grafico del rapporto e inserisci un **[!UICONTROL Query]** attività. Fai riferimento a [Raccogliere dati da analizzare](../../reporting/using/collecting-data-to-analyze.md).
1. Compila la tabella di origine e seleziona i campi della tabella che saranno interessati dalle statistiche.
1. Inserisci un **[!UICONTROL Page]** attività nel grafico. Per ulteriori informazioni, consulta [Elementi statici](../../reporting/using/creating-a-new-report.md#static-elements).
1. Inserisci un **[!UICONTROL List with group]** digita tabella nella pagina.
1. Specificare il percorso dei dati o la tabella selezionata come origine dati nella query.

   Questo passaggio è obbligatorio se si desidera recuperare i campi nella tabella di origine in un secondo momento e inserirli nelle celle della tabella.

1. Creazione della tabella e del relativo contenuto.
1. Visualizzare il rapporto finalizzato in **[!UICONTROL Preview]** scheda. Puoi quindi pubblicare il rapporto ed esportarlo in un formato diverso, se necessario. Per ulteriori informazioni, consulta [Esportare un rapporto](../../reporting/using/actions-on-reports.md#exporting-a-report).

### Aggiungi righe e colonne {#adding-lines-and-columns}

Per impostazione predefinita, un **[!UICONTROL List with group]** la tabella del tipo include un&#39;intestazione, una linea di dettaglio e una linea piè di pagina.

Il gruppo include linee di intestazione, dettagli e piè di pagina.

* **Riga di intestazione**: questa riga ti consente di assegnare un titolo alle colonne della tabella.

  ![](assets/s_advuser_ergo_listgroup_003a.png)

* **Riga dettagli**: questa riga contiene valori statistici.

  ![](assets/s_advuser_ergo_listgroup_004.png)

* **Riga piè di pagina**: questa riga consente di visualizzare i valori totali.

  ![](assets/s_advuser_ergo_listgroup_003.png)

È possibile aggiungere linee e colonne in base alle proprie esigenze.

Il gruppo può essere posizionato su qualsiasi riga della tabella e include le proprie linee di intestazione, dettagli e piè di pagina.

![](assets/s_advuser_ergo_listgroup_019.png)

**Riga e colonna**: per aggiungere o eliminare una riga o una colonna, passa a una riga o colonna esistente e utilizza il menu di scelta rapida.

![](assets/s_advuser_ergo_listgroup_006.png)

La natura della riga aggiunta dipende dalla posizione del cursore. Ad esempio, per aggiungere una riga di intestazione, posiziona i cursori su un’intestazione, quindi fai clic su **[!UICONTROL Add > A line above/below]**.

![](assets/s_advuser_ergo_listgroup_006a.png)

La larghezza delle colonne può essere modificata tramite **[!UICONTROL Column format]** elemento.

**Gruppo**: per aggiungere un gruppo, passa a una riga e seleziona l’elemento corrispondente nel menu a discesa.

![](assets/s_advuser_ergo_listgroup_007.png)

### Definire il contenuto della cella {#defining-cell-content}

Per modificare una cella della tabella e definirne il contenuto e il formato, passare alla cella e utilizzare il menu di scelta rapida.

Utilizza il **[!UICONTROL Expression]** voce di menu per selezionare i valori da visualizzare.

![](assets/s_advuser_ergo_listgroup_010.png)

* Per inserire i valori da analizzare direttamente nella tabella, selezionali tra i campi disponibili.

  L’elenco dei campi disponibili coincide con il contenuto della query prima della tabella nel grafico di costruzione del rapporto.

  ![](assets/s_advuser_ergo_listgroup_011.png)

* Immettere un&#39;etichetta per una cella, ad esempio l&#39;intestazione 1.

  A questo scopo, utilizza lo stesso processo utilizzato per inserire un campo nel database, ma non seleziona un’espressione. Inserisci l’etichetta nella **[!UICONTROL Label]** campo. Verrà visualizzato così com’è.

* Calcolo di un aggregato (media, somma, ecc.) e visualizzarla nella cella.

  A tale scopo, utilizza **[!UICONTROL Aggregates]** voce di menu e selezionare la campagna desiderata.

  ![](assets/s_advuser_ergo_listgroup_008.png)

### Definire il formato delle celle {#defining-cell-format}

![](assets/s_advuser_ergo_listgroup_017.png)

Per definire il formato della cella, **[!UICONTROL Cell format...]** consente di accedere a tutte le opzioni di formattazione disponibili per la cella selezionata.

Queste opzioni consentono di personalizzare il rendering finale del rapporto e di semplificare la lettura delle informazioni.

Utilizza il **[!UICONTROL Carriage return]** quando si esportano dati in Excel: selezionare il campo **[!UICONTROL Yes]** valore per forzare il ritorno a capo. Questo valore verrà mantenuto durante l’esportazione. Per ulteriori informazioni, consulta [Esportare un rapporto](../../reporting/using/actions-on-reports.md#exporting-a-report).

Il **[!UICONTROL Cell format]** consente di accedere alla scheda seguente:

* Il **[!UICONTROL Value]** scheda
* Il **[!UICONTROL Borders]** scheda
* Il **[!UICONTROL Click]** scheda
* Il **[!UICONTROL Extra]** scheda

Il **[!UICONTROL Value]** scheda consente di modificare il font e i vari attributi di valore o di definire un formato in base alla loro natura.

![](assets/s_advuser_ergo_listgroup_009.png)

Il formato cambia la visualizzazione dei dati: ad esempio, il **[!UICONTROL Number]**, **[!UICONTROL Monetary]** e **[!UICONTROL Percentage]** I formati consentono di allineare le figure a destra e visualizzare i punti decimali.

Esempio di configurazione di un formato di valuta: puoi specificare la valuta in cui sono espressi i valori, scegliere se separare le migliaia o meno e visualizzare i valori negativi in rosso. La posizione del simbolo di valuta dipende dalla lingua dell’operatore definita nel suo profilo.

![](assets/s_advuser_ergo_listgroup_012.png)

Esempio di configurazione per le date: puoi scegliere se visualizzare o meno l’ora.

![](assets/s_advuser_ergo_listgroup_013.png)

Il **Bordi** scheda consente di aggiungere bordi alle righe e alle colonne della tabella. L’aggiunta di bordi alle celle può causare problemi di prestazioni durante l’esportazione di rapporti di grandi dimensioni in Excel.

![](assets/s_advuser_ergo_listgroup_014.png)

Se necessario, è possibile definire i bordi nel modello di tabella (**[!UICONTROL Administration > Configuration > Form rendering]** ).

In questo caso, la sintassi è la seguente:

Nella scheda Web:

```
 .tabular td {
 border: solid 1px #000000;
 }
```

Nella scheda Excel:

```
 <style name="odd" fillColor="#fdfdfd">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
 
 <style name="even" fillColor="#f7f8fa">
  <border>
   <borderTop value="solid 0.05pt #000000" />
   <borderBottom value="solid 0.05pt #000000" />
   <borderLeft value="solid 0.05pt #000000" />
   <borderRight value="solid 0.05pt #000000" />
  </border>
 </style> 
```

Il **[!UICONTROL Click]** Questa scheda consente di definire un’azione quando l’utente fa clic sul contenuto di una cella o della tabella.

Nell’esempio seguente, facendo clic sul valore nella cella, puoi visualizzare la seconda pagina del rapporto: conterrà informazioni sulla consegna nella cella.

![](assets/s_advuser_ergo_listgroup_015.png)

Il **Extra** Questa scheda consente di collegare un elemento visivo ai dati, ad esempio un contrassegno colorato o una barra dei valori. Il contrassegno colorato viene utilizzato quando la tabella viene visualizzata come legenda in un grafico. Per ulteriori informazioni, consulta l’esempio di implementazione: [Passaggio 5: creare la seconda pagina](#step-5---create-the-second-page)

![](assets/s_advuser_ergo_listgroup_016.png)

## Caso d’uso: creare un rapporto con un elenco di gruppi {#use-case--create-a-report-with-a-group-list}

In questo esempio creeremo un rapporto di due pagine: la prima pagina conterrà l’elenco e il totale delle consegne per campagna, nonché il numero di messaggi inviati. I nomi delle consegne saranno collegamenti selezionabili che ti consentiranno di passare alla seconda pagina del rapporto per visualizzare il raggruppamento delle consegne per dominio e-mail per la consegna selezionata, con una tabella e un grafico. Nella seconda pagina, la tabella fungerà da legenda per il grafico.

![](assets/reporting_quick_start_report-final.png)

### Passaggio 1: creare un rapporto {#step-1---create-a-report}

Creare un nuovo rapporto relativo allo schema della campagna **[!UICONTROL Campaigns (nms)]**.

![](assets/s_advuser_report_listgroup_001.png)

Clic **[!UICONTROL Save]** per creare il rapporto.

Vai al grafico e aggiungi i primi componenti da utilizzare per progettare il contenuto del rapporto: una prima query e una prima pagina.

![](assets/reporting_quick_start_diagram.png)

### Passaggio 2: creare la prima query {#step-2---create-the-first-query}

La prima query ti consente di raccogliere le consegne collegate a ogni campagna. L’obiettivo è quello di visualizzare un rapporto sulle varie consegne del database di Adobe Campaign collegato a ogni campagna.

Fai doppio clic sulla prima query per modificarla, quindi applica i seguenti passaggi per configurarla:

1. Inizia modificando lo schema in cui viene applicata l’origine della query: seleziona la **[!UICONTROL Deliveries (nms)]** schema.
1. Fai clic su **[!UICONTROL Edit query]** collegare e visualizzare i campi avanzati.

   ![](assets/reporting_quick_start_query-1.png)

1. Selezionare i campi seguenti:

   * l’etichetta di consegna,
   * la chiave primaria della consegna,
   * l’etichetta della campagna,
   * l’indicatore delle consegne trasformate,
   * la chiave esterna del collegamento Campaign,
   * l’indicatore del tasso di errore.

   ![](assets/s_advuser_report_listgroup_002.png)

   Collega un alias a ciascun campo: questa operazione è consigliata per facilitare la selezione dei dati dalla tabella che verranno aggiunti alla prima pagina del rapporto.

   Per questo esempio, utilizzeremo i seguenti alias:

   * Etichetta: **@label**
   * Chiave primaria: **@deliveryId**
   * Etichetta (Campagna): **@label1**
   * Elaborato: **@processed**
   * Chiave esterna del collegamento &#39;Campagna&#39; (campo &#39;id&#39;): **@operationId**
   * Frequenza errori: **@errorRatio**

1. Fai clic su **[!UICONTROL Next]** due volte per arrivare al **[!UICONTROL Data filtering]** passaggio.

   Aggiungi una condizione di filtro per raccogliere solo le consegne collegate a una campagna.

   La sintassi di questo filtro è la seguente: &quot;Chiave esterna del collegamento &#39;Campagne&#39; maggiore di 0&quot;.

   ![](assets/reporting_quick_start_query_filter.png)

1. Clic **[!UICONTROL Finish]** per salvare queste condizioni, fai clic su **[!UICONTROL Ok]** per chiudere l’editor delle query.

### Passaggio 3: creare la prima pagina {#step-3--create-the-first-page}

In questo passaggio verrà configurata la prima pagina del rapporto. Per configurarlo, effettua le seguenti operazioni:

1. Apri **[!UICONTROL Page]** e inserirne il titolo, ad esempio **Consegne** in questo caso.

   ![](assets/s_advuser_report_listgroup_003.png)

1. Inserisci un elenco con gruppo tramite la barra degli strumenti e immettine l’etichetta, ad esempio: Elenco di consegne per campagna.

   ![](assets/s_advuser_report_listgroup_004.png)

1. Fai clic su **[!UICONTROL Table data XPath...]** e seleziona il collegamento di consegna, ad esempio `[query/delivery]`.

   ![](assets/s_advuser_report_listgroup_005.png)

1. Fai clic su **[!UICONTROL Data]** scheda e modifica del layout della tabella: aggiungi tre colonne a destra.

   ![](assets/s_advuser_report_listgroup_006.png)

1. Aggiungi un gruppo.

   ![](assets/s_advuser_report_listgroup_008.png)

   Questo gruppo consente di raggruppare le campagne e le consegne ad esse collegate.

1. Nella finestra del gruppo, fare riferimento a **Chiave esterna del collegamento &#39;Campagna&#39;** e chiudi la finestra.

   ![](assets/s_advuser_report_listgroup_007.png)

1. Modificare la prima cella dell&#39;intestazione del gruppo e inserire **[!UICONTROL Label]** delle campagne come espressione.

   ![](assets/s_advuser_report_listgroup_009.png)

1. Modifica la seconda cella della riga dei dettagli e seleziona le consegne **[!UICONTROL Label]**.

   ![](assets/s_advuser_report_listgroup_011.png)

1. Modifica il formato di questa cella e apri **[!UICONTROL Click]** scheda. Configura le opzioni appropriate in modo che, quando gli utenti fanno clic sul nome di una consegna, questa si apra nella stessa finestra.

   ![](assets/s_advuser_report_listgroup_0111.png)

   A questo scopo, seleziona una **[!UICONTROL Next page]** digita azione e seleziona **[!UICONTROL In the same window]** come opzione di apertura.

   ![](assets/s_advuser_report_listgroup_0112.png)

1. Nella sezione inferiore della finestra, fare clic su **[!UICONTROL Add]** e specificare **`/vars/selectedDelivery`** percorso e **[!UICONTROL @deliveryId]** espressione che corrisponde all’alias della chiave primaria della consegna, come definito nella query creata in precedenza. Questa formula ti consente di accedere alla consegna selezionata.

   ![](assets/s_advuser_report_listgroup_010.png)

1. Modificate la seconda cella della linea del piè di pagina del gruppo e immettete **[!UICONTROL Total per campaign]** come etichetta.

   ![](assets/s_advuser_report_listgroup_012.png)

1. Modificate la terza cella della linea di intestazione del gruppo e immettete **[!UICONTROL Number of messages sent]** come etichetta.

   ![](assets/s_advuser_report_listgroup_013.png)

   Queste informazioni coincidono con il titolo della colonna.

1. Modificare la terza cella della riga di dettaglio e selezionare l&#39;indicatore del messaggio elaborato come espressione.

   ![](assets/s_advuser_report_listgroup_014.png)

1. Modifica la terza cella della riga del piè di pagina del gruppo, seleziona l’indicatore di consegna elaborato e applica il **[!UICONTROL Sum]** aggregare a esso.

   ![](assets/s_advuser_report_listgroup_015.png)

1. Modificate la quarta cella della linea di dettaglio e selezionate **tasso di errore di consegna** come espressione.

   ![](assets/s_advuser_report_listgroup_016.png)

1. Seleziona questa cella per visualizzare una barra dei valori che rappresenta il tasso di errore di consegna.

   A tale scopo, accedere al formato della cella, quindi passare al **[!UICONTROL More]** scheda. Seleziona la **[!UICONTROL Value bar]** nell&#39;elenco a discesa e selezionare il **[!UICONTROL Hide the cell value]** opzione.

   ![](assets/s_advuser_report_listgroup_023.png)

   Ora puoi visualizzare un rendering del rapporto. Fai clic su **[!UICONTROL Preview]** e seleziona la scheda **[!UICONTROL Global]** opzione: mostra l’elenco di tutte le consegne nel database di Adobe Campaign collegate a una campagna.

   ![](assets/s_advuser_report_listgroup_025.png)

   È consigliabile utilizzare **[!UICONTROL Preview]** per assicurarsi che i dati nella tabella siano selezionati e configurati correttamente. Al termine, puoi continuare a formattare la tabella.

1. Applica **[!UICONTROL Bold]** alle celle che mostrano il totale per campagna e il numero totale di messaggi elaborati.

   ![](assets/s_advuser_report_listgroup_024.png)

1. Fai clic sulla prima cella della riga di intestazione del gruppo, quella che visualizza il nome della campagna, quindi seleziona **[!UICONTROL Edit > Merge to right]**.

   ![](assets/s_advuser_report_listgroup_026.png)

   L’unione delle prime due celle della riga di intestazione del gruppo riallinea il titolo della campagna e l’elenco delle consegne collegate.

   ![](assets/s_advuser_report_listgroup_027.png)

   >[!CAUTION]
   >
   >È consigliabile attendere che il report venga generato prima di unire le celle, poiché l’unione è irreversibile.

### Passaggio 4: creare la seconda query {#step-4---create-the-second-query}

Vogliamo aggiungere una seconda query e una seconda pagina per visualizzare i dettagli di una consegna quando l’utente del rapporto fa clic su di essa. Prima di aggiungere la query, modifica la pagina creata e abilita la transizione in uscita in modo che possa essere collegata alla query.

1. Aggiungi una nuova query dopo il **[!UICONTROL Page]** attività e modificarne lo schema: seleziona la **[!UICONTROL Recipient delivery logs]** schema.

   ![](assets/reporting_quick_start_query-2.png)

1. Modifica la query e definisci le colonne di output. Per visualizzare il numero di consegne per dominio e-mail, è necessario:

   * calcola la somma delle chiavi primarie per conteggiare il numero di registri di consegna:

     ![](assets/reporting_quick_start_query-2_count.png)

   * raccogliere i domini e-mail dei destinatari e le informazioni sui gruppi in questo campo: a questo scopo, seleziona la **[!UICONTROL Group]** nella colonna del nome di dominio.

   ![](assets/reporting_quick_start_query-2_filter.png)

   Collega i seguenti alias ai campi:

   * count(chiave primaria): **@count**
   * Dominio e-mail (destinatario): **@domain**

     ![](assets/reporting_quick_start_query-2_alias.png)

1. Fai clic su **[!UICONTROL Next]** due volte: questo pulsante consente di visualizzare **[!UICONTROL Data filtering]** passaggio.

   Aggiungi una condizione di filtro per raccogliere solo le informazioni collegate alla consegna selezionata.

   La sintassi è la seguente: La chiave esterna del collegamento &quot;Consegna&quot; è uguale al valore dell’impostazione `$([vars/selectedDelivery])`

   ![](assets/s_advuser_report_listgroup_017.png)

1. Chiudi la finestra di configurazione della query e aggiungi una pagina al grafico, subito dopo la seconda query.

### Passaggio 5: creare la seconda pagina {#step-5---create-the-second-page}

1. Modifica la pagina e immetti la relativa etichetta: **Domini e-mail**.
1. Deseleziona la **[!UICONTROL Enable output transitions]** opzione: questa è l’ultima pagina del rapporto e non sarà seguita da un’altra attività.

   ![](assets/s_advuser_report_listgroup_028.png)

1. Aggiungere un nuovo elenco con un gruppo utilizzando il menu di scelta rapida e richiamarlo **Domini e-mail per destinatario**.
1. Fai clic su **[!UICONTROL Table data XPath...]** e seleziona la **[!UICONTROL Recipient delivery logs]** collegamento.

   ![](assets/s_advuser_report_listgroup_029.png)

1. In **[!UICONTROL Data]** , adattare la tabella come segue:

   * Aggiungi due colonne a destra.
   * Nella prima cella della riga di dettaglio, aggiungi **[!UICONTROL rowNum()-1]** espressione per contare il numero di righe. Quindi modifica il formato della cella: nel **[!UICONTROL Extra]** , seleziona **[!UICONTROL Color tab]** e fai clic su **[!UICONTROL Ok]**.

     ![](assets/s_advuser_report_listgroup_018.png)

     Questa configurazione consente di utilizzare la tabella come didascalia del grafico.

   * Nella seconda cella della riga di dettaglio, aggiungi **[!UICONTROL Email domain(Recipient)]** espressione.
   * Nella terza cella della riga di dettaglio, aggiungi **[!UICONTROL count(primary key)]** espressione.

   ![](assets/s_advuser_report_listgroup_019.png)

1. Aggiungi un grafico a torta alla pagina utilizzando il menu di scelta rapida e assegna il **Domini e-mail** su di esso. Per ulteriori informazioni, consulta [Tipi di grafico e varianti](../../reporting/using/creating-a-chart.md#chart-types-and-variants).
1. Fai clic su **[!UICONTROL Variants]** collega e deseleziona il **[!UICONTROL Display label]** e **[!UICONTROL Display caption]** opzioni.
1. Verifica che non sia configurato alcun ordinamento dei valori. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../reporting/using/processing-a-report.md#configuring-the-layout-of-a-descriptive-analysis-report).

   ![](assets/s_advuser_report_listgroup_0191.png)

1. In **[!UICONTROL Data]** , modificare l&#39;origine dati: selezionare **[!UICONTROL Context data]** dall’elenco a discesa.

   ![](assets/s_advuser_report_listgroup_020.png)

1. Quindi fai clic su **[!UICONTROL Advanced settings]** e seleziona il collegamento ai registri di consegna del destinatario.

   ![](assets/s_advuser_report_listgroup_0201.png)

1. In **[!UICONTROL Chart type]** , seleziona la sezione **[!UICONTROL Email domain]** variabile.
1. Quindi aggiungi il calcolo da eseguire: seleziona la somma come operatore.

   ![](assets/s_advuser_report_listgroup_0202.png)

1. Fai clic su **[!UICONTROL Detail]** per selezionare il campo relativo al conteggio, quindi chiudere la finestra di configurazione.

   ![](assets/s_advuser_report_listgroup_030.png)

1. Salva il rapporto.

   La pagina è ora configurata.

### Passaggio 6: visualizzare il rapporto {#step-6---viewing-the-report}

Per visualizzare il risultato di questa configurazione, fare clic sul pulsante **[!UICONTROL Preview]** e seleziona la scheda **[!UICONTROL Global]** opzione.

La prima pagina del rapporto fornisce dettagli sull’elenco di tutte le consegne incluse nel database.

![](assets/s_advuser_report_listgroup_021.png)

Se fai clic sul collegamento di una di queste consegne, viene visualizzato il grafico che mostra il raggruppamento dei domini e-mail per questa consegna. Ora ti trovi nella seconda pagina del rapporto e puoi tornare alla pagina precedente facendo clic sul pulsante appropriato.

![](assets/s_advuser_report_listgroup_022.png)

## Creare una suddivisione o una tabella pivot {#creating-a-breakdown-or-pivot-table}

Questo tipo di tabella consente di visualizzare le statistiche calcolate sui dati nel database.

La configurazione di questi tipi di rapporti è simile a quella utilizzata per l’analisi guidata descrittiva. Per ulteriori informazioni, consulta [questa pagina](../../reporting/using/using-the-descriptive-analysis-wizard.md#configuring-the-quantitative-distribution-template).

Per ulteriori informazioni sulla creazione di una tabella pivot, consulta [questa sezione](../../reporting/using/ac-cubes.md).
