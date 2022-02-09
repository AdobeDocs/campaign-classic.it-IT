---
product: campaign
title: Query
description: Ulteriori informazioni sull’attività del flusso di lavoro Query
feature: Query Editor
exl-id: 20d03627-cd56-46da-bc02-73b48a02a350
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1629'
ht-degree: 0%

---

# Query{#query}

![](../../assets/common.svg)

## Creazione di una query {#creating-a-query}

Una query ti consente di selezionare un target in base ai criteri. Puoi associare un codice di segmento al risultato della query e inserire dati aggiuntivi al risultato.
Per ulteriori informazioni sugli esempi di query, consulta questo [questa sezione](querying-recipient-table.md).

>[!NOTE]
>
>Le attività di query non sono compatibili con i campi CLOB quando si utilizza Oracle.

![](assets/s_user_segmentation_wizard_9.png)

Per ulteriori informazioni sull’utilizzo e la gestione di dati aggiuntivi, consulta [Aggiunta di dati](#adding-data).

La **[!UICONTROL Edit query...]** link ti consente di definire il tipo di targeting, le restrizioni e i criteri di selezione per la popolazione nel modo seguente:

1. Seleziona la dimensione di targeting e filtro. Per impostazione predefinita, il target viene selezionato dai destinatari. L’elenco dei filtri con restrizioni è lo stesso utilizzato per il targeting di consegna.

   La dimensione di targeting coincide con il tipo di elemento su cui lavoreremo, ad esempio la popolazione target dell’operazione.

   La dimensione di filtro consente di raccogliere questi elementi, ad esempio informazioni relative alla persona oggetto del targeting (contratti, regolamenti completi e finali, ecc.).

   Per ulteriori informazioni, consulta [Dimensioni di targeting e filtro](building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   Se necessario, una query può essere basata sui dati della transizione in entrata selezionando **[!UICONTROL Temporary schema]** quando scegli il targeting e il filtro delle dimensioni.

   ![](assets/query_temporary_table.png)

1. Definisci le popolazioni utilizzando la procedura guidata. I campi da immettere possono variare a seconda del tipo di target. Puoi visualizzare in anteprima la popolazione target con i criteri correnti utilizzando **[!UICONTROL Preview]** scheda .

   Per ulteriori informazioni sulla creazione e l’utilizzo di filtri o query, consulta questo [sezione](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. Se hai selezionato **[!UICONTROL Filtering conditions]** al punto 1 o utilizzando **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]** in seguito dovrai aggiungere manualmente i criteri di filtro.

   Puoi anche aggiungere condizioni di raggruppamento dei dati selezionando la casella corrispondente. A questo scopo, la dimensione di filtro deve essere diversa dalla dimensione di targeting della query. Per ulteriori informazioni sui raggruppamenti, consulta questo [sezione](querying-using-grouping-management.md).

   È inoltre possibile aggiungere altri criteri utilizzando il generatore di espressioni e combinarli con le opzioni logiche AND, OR ed EXCEPT. È quindi possibile visualizzare in anteprima il **[!UICONTROL Corresponding SQL query...]** per la combinazione di criteri. Per ulteriori informazioni, consulta questo articolo [sezione](../../platform/using/defining-filter-conditions.md#building-expressions).

   Salva il filtro se desideri riutilizzarlo in un secondo momento.

   ![](assets/s_user_segmentation_query_advanced.png)

## Aggiunta di dati {#adding-data}

Le colonne aggiuntive consentono di raccogliere informazioni aggiuntive sulla popolazione target, ad esempio numeri di contratto, abbonamenti a newsletter o origine. Questi dati possono essere memorizzati nel database Adobe Campaign o in un database esterno.

La **[!UICONTROL Add data...]** link ti consente di selezionare i dati aggiuntivi da raccogliere.

![](assets/wf_add_data_link.png)

Inizia selezionando il tipo di dati da aggiungere:

![](assets/wf_add_data_1st_option.png)

* Seleziona **[!UICONTROL Data linked to the filtering dimension]** per selezionare i dati nel database Adobe Campaign.
* Seleziona **[!UICONTROL External data]** per aggiungere dati da un database esterno. Questa opzione è disponibile solo se hai acquistato il **Federated Data Access** opzione . Per ulteriori informazioni, consulta [Accesso a un database esterno (FDA)](accessing-an-external-database--fda-.md).
* Seleziona la **[!UICONTROL An offer proposition]** per aggiungere un set di colonne che consente di memorizzare la proposta migliore generata dal motore di offerta. Questa opzione è disponibile solo se hai acquistato il **Interazione** modulo .

Se sulla piattaforma non è installato alcun modulo opzionale, questa fase non viene visualizzata. Verrà portato direttamente al prossimo stadio.

Per aggiungere dati dal database Adobe Campaign:

1. Seleziona il tipo di dati da aggiungere. Può trattarsi di dati appartenenti alla dimensione di filtro o di dati memorizzati in tabelle collegate.

   ![](assets/query_add_columns.png)

1. Se i dati appartengono alla dimensione di filtro della query, è sufficiente selezionarla nell’elenco dei campi disponibili per visualizzarla nelle colonne di output.

   ![](assets/wf_add_data_field_selection.png)

   Puoi aggiungere:

   * Campo calcolato in base ai dati provenienti dalla popolazione target o da un aggregato (numero di acquisti in sospeso nell’ultimo mese, importo medio di una ricevuta, ecc.). Ad esempio, vai a [Selezione dei dati](targeting-data.md#selecting-data).
   * Un nuovo campo, creato utilizzando **[!UICONTROL Add]** a destra dell&#39;elenco delle colonne di output.

      Puoi anche aggiungere una raccolta di informazioni, ad esempio un elenco di contratti, le ultime 5 consegne, ecc. Le raccolte coincidono con i campi che possono avere più valori per lo stesso profilo (relazione 1-N). Per ulteriori informazioni, consulta [Modifica di dati aggiuntivi](targeting-data.md#editing-additional-data).

Per aggiungere una raccolta di informazioni collegate a una popolazione target:

1. Al primo passaggio della procedura guidata, seleziona la **[!UICONTROL Data linked to the filtering dimension]** opzione:
1. Seleziona la tabella contenente le informazioni da raccogliere e fai clic su **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. Se necessario, specifica il numero di elementi della raccolta che desideri mantenere selezionando uno dei valori nella **[!UICONTROL Data collected]** campo . Per impostazione predefinita, tutte le righe della raccolta vengono recuperate e quindi filtrate in base alle condizioni specificate nel passaggio seguente.

   * Se un singolo elemento della raccolta coincide con le condizioni di filtro per questa raccolta, seleziona **[!UICONTROL Single row]** in **[!UICONTROL Data collected]** campo .

      >[!IMPORTANT]
      >
      >Questa modalità ottimizza la query SQL generata grazie a un juncture diretto sugli elementi della raccolta.
      >
      >Se la condizione iniziale non viene rispettata, il risultato potrebbe essere errato (linee mancanti o sovrapposte).

   * Se scegli di recuperare diverse linee (**[!UICONTROL Limit the line count]**) puoi specificare il numero di righe da raccogliere.
   * Se le colonne raccolte contengono aggregati, ad esempio il numero di errori dichiarati, la spesa media su un sito, ecc. è possibile utilizzare **[!UICONTROL Aggregates]** valore.

   ![](assets/query_add_collection_param.png)

1. Specifica la sottoselezione della raccolta. Ad esempio: acquisti effettuati solo negli ultimi 15 giorni.

   ![](assets/query_add_columns_collection_filter.png)

1. Se hai selezionato la **[!UICONTROL Limit the line count]** definire l’ordine in cui i dati raccolti devono essere filtrati. Una volta che il numero di righe raccolte è superiore al numero di righe specificato per mantenere, l&#39;ordine di filtro consente di specificare quali righe mantenere.

## Esempio: Targeting su attributi di destinatari semplici {#example--targeting-on-simple-recipient-attributes}

Nell&#39;esempio seguente, la query cerca di identificare gli uomini di età compresa tra i 18 e i 30 anni che vivono in Francia. Questa query verrà utilizzata in un flusso di lavoro che mira a renderli ad esempio un’offerta esclusiva.

>[!NOTE]
>
>Sono presentati ulteriori esempi di query in [questa sezione](querying-recipient-table.md).

1. Denomina la query e seleziona la **[!UICONTROL Edit query...]** link.
1. Seleziona **[!UICONTROL Filtering conditions]** nell’elenco dei tipi di filtro disponibili.
1. Inserire i diversi criteri per il target proposto. Qui i criteri vengono combinati utilizzando l’opzione AND . Per essere inclusi nella selezione, i destinatari dovranno soddisfare le seguenti quattro condizioni:

   * I destinatari il cui titolo è &quot;Mr&quot; (si possono trovare anche utilizzando il **Genere** campo e selezione **Maschio** come valore).
   * Destinatari di età inferiore ai 30 anni.
   * Destinatari di oltre 18 anni.
   * Destinatari che vivono in Francia.

   ![](assets/query_example.png)

   È possibile visualizzare l&#39;SQL che corrisponde alla combinazione di criteri:

   ![](assets/query_example_sql.png)

1. Puoi verificare che i criteri siano corretti visualizzando in anteprima i destinatari che corrispondono alla query nella scheda pertinente:

   ![](assets/query_example_preview.png)

1. Salva i filtri in modo da poterli utilizzare nuovamente in un secondo momento facendo clic su **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. Continua a modificare il flusso di lavoro aggiungendo altre attività. Una volta avviato e completato il passaggio della query precedente, verrà visualizzato il numero di destinatari trovati. Puoi visualizzare ulteriori dettagli utilizzando il menu a comparsa del mouse (fai clic con il pulsante destro del mouse sulla transizione > **[!UICONTROL Display the target...]**).

   ![](assets/query_example_result.png)

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica la popolazione oggetto della query. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

Questo valore è lo schema della tabella di lavoro. Questo parametro è valido per tutte le transizioni con **[!UICONTROL tableName]** e **[!UICONTROL schema]**.

## Ottimizzazione delle query {#optimizing-queries}

La sezione seguente fornisce best practice per ottimizzare le query in esecuzione su Adobe Campaign per limitare il carico di lavoro sul database e migliorare l’esperienza utente.

### Iscrizioni e indici {#joins-and-indexes}

* Le query efficienti si basano sugli indici.
* Utilizzare un indice per tutti i join.
* La definizione dei collegamenti sullo schema determinerà le condizioni di join. La tabella collegata deve avere un indice univoco sulla chiave primaria e il join deve trovarsi in questo campo.
* Eseguire i join definendo i tasti sui campi numerici anziché sui campi stringa.
* Evitare di eseguire join esterni. Quando possibile, utilizza il record Zero ID per ottenere la funzionalità di join esterno.
* Utilizzare il tipo di dati corretto per i join.

   Assicurati che `where` La clausola è dello stesso tipo del campo.

   Un errore comune è: `iBlacklist='3'` dove `iBlacklist` è un campo numerico, e `3` indica un valore di testo.

   Assicurati di sapere quale sarà il piano di esecuzione della query. Evita l’esecuzione di analisi complete delle tabelle, in particolare per query in tempo reale o query quasi in tempo reale eseguite ogni minuto.

   Per ulteriori informazioni, a seconda della versione di Campaign, consulta queste sezioni:

   ![](assets/do-not-localize/v7.jpeg)[  Documentazione di Campaign v7](../../configuration/using/database-mapping.md)

   ![](assets/do-not-localize/v8.png)[  Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/shemas-forms/database-mapping.html)

### Funzioni {#functions}

* Attenzione a funzioni come `Lower(...)`. Quando si utilizza la funzione Lower, l&#39;indice non viene utilizzato.
* Controllare attentamente le query utilizzando l&#39;istruzione &quot;like&quot; o le istruzioni &quot;Upper&quot; o &quot;Lower&quot;. Applicare &quot;Upper&quot; all&#39;input dell&#39;utente, non al campo del database.

   Per ulteriori informazioni sulle funzioni, consulta [questa sezione](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Filtrare le dimensioni {#filtering-dimensions}

Utilizza la dimensione di filtro della query invece di utilizzare l’operatore &quot;esiste come&quot;.

![](assets/optimize-queries-filtering.png)

Nelle query, le condizioni &quot;esiste come&quot; nei filtri non sono efficienti. Sono l’equivalente di una sottoquery in SQL:

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

La best practice consiste nell’utilizzare al suo posto la dimensione di filtro della query:

![](assets/optimize-queries-filtering2.png)

L&#39;equivalente della dimensione filtro in SQL è il join interno:

`select iRecipientId from nmsRecipient INNER JOIN nmsBroadLog ON (...)`

Per ulteriori informazioni sul filtro delle dimensioni, consulta [questa sezione](building-a-workflow.md#targeting-and-filtering-dimensions).

### Architettura {#architecture}

* Crea una piattaforma di sviluppo con volumi, parametri e architettura simili a quelli della piattaforma di produzione.
* Utilizza gli stessi valori per gli ambienti di sviluppo e produzione. Per quanto possibile, utilizza lo stesso:

   * Sistema operativo,
   * Versione,
   * Dati,
   * Applicazione,
   * Volumi.

   >[!NOTE]
   >
   >Una funzione che funziona in un ambiente di sviluppo potrebbe non funzionare in un ambiente di produzione in cui i dati possono essere diversi. Cercare di individuare le principali differenze al fine di anticipare i rischi e preparare soluzioni.

* Crea configurazioni corrispondenti ai volumi di destinazione. I grandi volumi richiedono configurazioni specifiche. Una configurazione che funzionava per 100.000 destinatari potrebbe non funzionare per 10.000.000 destinatari.

   Considera come il sistema si svilupperà quando sarà attivo. Solo perché qualcosa funziona su piccola scala non significa che sarà adatto con volumi maggiori. Le prove devono essere effettuate con volumi simili al volume in produzione. È inoltre necessario valutare l’effetto delle modifiche dei volumi (numero di chiamate, dimensione del database) nelle ore di picco, nei giorni di picco e durante tutta la durata del progetto.
