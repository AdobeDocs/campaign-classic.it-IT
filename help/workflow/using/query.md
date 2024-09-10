---
product: campaign
title: Query
description: Ulteriori informazioni sull’attività del flusso di lavoro Query
feature: Workflows, Targeting Activity, Query Editor
exl-id: 20d03627-cd56-46da-bc02-73b48a02a350
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1631'
ht-degree: 0%

---

# Query{#query}



## Creare una query {#creating-a-query}

Una query consente di selezionare una destinazione in base ai criteri. È possibile associare un codice di segmento al risultato della query e inserirvi dati aggiuntivi.
Per ulteriori informazioni sugli esempi di query, consulta questa [sezione](querying-recipient-table.md).

>[!NOTE]
>
>Le attività di query non sono compatibili con i campi CLOB quando si utilizza Oracle.

![](assets/s_user_segmentation_wizard_9.png)

Per ulteriori informazioni sull&#39;utilizzo e sulla gestione di dati aggiuntivi, fare riferimento a [Aggiungi dati](#adding-data).

Il collegamento **[!UICONTROL Edit query...]** consente di definire il tipo di targeting, le restrizioni e i criteri di selezione per la popolazione nel modo seguente:

1. Seleziona la dimensione di targeting e filtro. Per impostazione predefinita, il target viene selezionato dai destinatari. L’elenco dei filtri di restrizione è lo stesso di quelli utilizzati per il targeting della consegna.

   La dimensione di targeting coincide con il tipo di elemento su cui lavoreremo, ad esempio la popolazione target dell’operazione.

   La dimensione di filtro consente di raccogliere questi elementi, ad esempio informazioni relative alla persona target (contratti, liquidazioni complete e finali, ecc.).

   Per ulteriori informazioni, consulta [Dimensioni di targeting e filtro](building-a-workflow.md#targeting-and-filtering-dimensions).

   ![](assets/s_user_segmentation_query_edit.png)

   Una query può essere basata sui dati della transizione in entrata, se necessario, selezionando **[!UICONTROL Temporary schema]** durante la scelta delle dimensioni di targeting e filtro.

   ![](assets/query_temporary_table.png)

1. Definisci le popolazioni utilizzando l’assistente. I campi da immettere possono variare a seconda del tipo di destinazione. È possibile visualizzare in anteprima la popolazione di destinazione con i criteri correnti utilizzando la scheda **[!UICONTROL Preview]**.

   Per ulteriori informazioni sulla creazione e l&#39;utilizzo di filtri o query, consulta questa [sezione](../../platform/using/filtering-options.md).

   ![](assets/s_user_segmentation_wizard.png)

1. Se hai selezionato **[!UICONTROL Filtering conditions]** al passaggio 1 o utilizzando l&#39;opzione **[!UICONTROL Filters]** > **[!UICONTROL Advanced filter...]**, in seguito dovrai aggiungere manualmente i criteri di filtro.

   È inoltre possibile aggiungere condizioni di raggruppamento dei dati selezionando la casella corrispondente. A questo scopo, la dimensione di filtro deve essere diversa dalla dimensione di targeting della query. Per ulteriori informazioni sul raggruppamento, consulta questa [sezione](querying-using-grouping-management.md).

   È inoltre possibile aggiungere altri criteri utilizzando il generatore di espressioni e combinarlo con le opzioni logiche AND, OR e EXCEPT. È quindi possibile visualizzare in anteprima **[!UICONTROL Corresponding SQL query...]** per la combinazione di criteri. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/defining-filter-conditions.md#building-expressions).

   Salva il filtro se desideri riutilizzarlo in un secondo momento.

   ![](assets/s_user_segmentation_query_advanced.png)

## Aggiungi dati {#adding-data}

Le colonne aggiuntive consentono di raccogliere informazioni aggiuntive sulla popolazione target, ad esempio numeri di contratto, abbonamenti a newsletter o origini. Questi dati possono essere memorizzati nel database di Adobe Campaign o in un database esterno.

Il collegamento **[!UICONTROL Add data...]** consente di selezionare i dati aggiuntivi da raccogliere.

![](assets/wf_add_data_link.png)

Per iniziare, seleziona il tipo di dati da aggiungere:

![](assets/wf_add_data_1st_option.png)

* Selezionare **[!UICONTROL Data linked to the filtering dimension]** per selezionare i dati nel database di Adobe Campaign.
* Selezionare **[!UICONTROL External data]** per aggiungere dati da un database esterno. Questa opzione è disponibile solo se hai acquistato l&#39;opzione **Federated Data Access**. Per ulteriori informazioni, vedere [Accedere a un database esterno (FDA)](accessing-an-external-database-fda.md).
* Seleziona l&#39;opzione **[!UICONTROL An offer proposition]** per aggiungere un set di colonne che ti consenta di memorizzare la proposta migliore generata dal motore di offerta. Questa opzione è disponibile solo se hai acquistato il modulo **Interaction**.

Se sulla piattaforma non è installato alcun modulo opzionale, questa fase non viene visualizzata. Si passerà direttamente alla fase successiva.

Per aggiungere dati dal database di Adobe Campaign:

1. Seleziona il tipo di dati da aggiungere. Possono essere dati appartenenti alla dimensione di filtro o dati memorizzati in tabelle collegate.

   ![](assets/query_add_columns.png)

1. Se i dati appartengono alla dimensione di filtro della query, selezionali semplicemente nell’elenco dei campi disponibili per visualizzarli nelle colonne di output.

   ![](assets/wf_add_data_field_selection.png)

   Puoi aggiungere:

   * Un campo calcolato in base ai dati ottenuti dalla popolazione target o a un aggregato (numero di acquisti in sospeso nell’ultimo mese, importo medio di una ricevuta, ecc.). Ad esempio, vai a [Seleziona dati](targeting-data.md#selecting-data).
   * Nuovo campo creato con il pulsante **[!UICONTROL Add]** a destra dell&#39;elenco delle colonne di output.

     Puoi anche aggiungere una raccolta di informazioni, ad esempio un elenco di contratti, le ultime 5 consegne e così via. Le raccolte coincidono con campi che possono avere più valori per lo stesso profilo (relazione 1-N). Per ulteriori informazioni, consulta [Modifica dati aggiuntivi](targeting-data.md#editing-additional-data).

Per aggiungere una raccolta di informazioni collegate a una popolazione target:

1. Al primo passaggio dell&#39;assistente, selezionare l&#39;opzione **[!UICONTROL Data linked to the filtering dimension]**:
1. Selezionare la tabella contenente le informazioni da raccogliere e fare clic su **[!UICONTROL Next]**.

   ![](assets/wf_add_data_linked_table.png)

1. Se necessario, specificare il numero di elementi della raccolta da mantenere selezionando uno dei valori nel campo **[!UICONTROL Data collected]**. Per impostazione predefinita, tutte le righe della raccolta vengono recuperate e quindi filtrate in base alle condizioni specificate al passaggio successivo.

   * Se un singolo elemento della raccolta coincide con le condizioni di filtro per questa raccolta, selezionare **[!UICONTROL Single row]** nel campo **[!UICONTROL Data collected]**.

     >[!IMPORTANT]
     >
     >Questa modalità ottimizza la query SQL generata grazie a una giunzione diretta sugli elementi di raccolta.
     >
     >Se la condizione iniziale non viene rispettata, il risultato potrebbe essere difettoso (linee mancanti o sovrapposte).

   * Se si sceglie di recuperare più righe (**[!UICONTROL Limit the line count]**), è possibile specificare il numero di righe da raccogliere.
   * Se le colonne raccolte contengono aggregati, ad esempio il numero di errori dichiarati, la spesa media in un sito e così via. è possibile utilizzare il valore **[!UICONTROL Aggregates]**.

   ![](assets/query_add_collection_param.png)

1. Specifica la sottoselezione della raccolta. Ad esempio: acquisti effettuati solo negli ultimi 15 giorni.

   ![](assets/query_add_columns_collection_filter.png)

1. Se è stata selezionata l&#39;opzione **[!UICONTROL Limit the line count]**, definire l&#39;ordine in cui filtrare i dati raccolti. Quando il numero di righe raccolte è superiore al numero di righe che si è specificato di mantenere, l&#39;ordine di filtraggio consente di specificare quali righe mantenere.

## Esempio: targeting su attributi di destinatari semplici {#example--targeting-on-simple-recipient-attributes}

Nell’esempio che segue, l’interrogazione mira a individuare gli uomini di età compresa tra i 18 e i 30 anni che vivono in Francia. Questa query verrà utilizzata in un flusso di lavoro che, ad esempio, mira a renderle un’offerta esclusiva.

>[!NOTE]
>
>Ulteriori esempi di query sono presentati in [questa sezione](querying-recipient-table.md).

1. Assegna un nome alla query, quindi seleziona il collegamento **[!UICONTROL Edit query...]**.
1. Selezionare **[!UICONTROL Filtering conditions]** nell&#39;elenco dei tipi di filtro disponibili.
1. Inserire i diversi criteri per il target proposto. I criteri di seguito vengono combinati utilizzando l’opzione E. Per essere inclusi nella selezione, i destinatari dovranno soddisfare le quattro condizioni seguenti:

   * Destinatari il cui titolo è &quot;Sig.&quot; (è possibile trovare anche utilizzando il campo **Genere** e selezionando **Maschio** come valore).
   * Destinatari di età inferiore a 30 anni.
   * Destinatari di età superiore a 18 anni.
   * Destinatari che vivono in Francia.

   ![](assets/query_example.png)

   È possibile visualizzare il codice SQL corrispondente alla combinazione di criteri:

   ![](assets/query_example_sql.png)

1. Per verificare che il criterio sia corretto, visualizza in anteprima i destinatari che corrispondono alla query nella scheda pertinente:

   ![](assets/query_example_preview.png)

1. Salvare i filtri per poterli riutilizzare in un secondo momento facendo clic su **[!UICONTROL Finish]** > **[!UICONTROL OK]**.
1. Continua a modificare il flusso di lavoro aggiungendovi altre attività. Una volta avviato e completato il passaggio di query precedente, verrà visualizzato il numero di destinatari trovati. È possibile visualizzare ulteriori dettagli utilizzando il menu a comparsa del mouse (fare clic con il pulsante destro del mouse sulla transizione > **[!UICONTROL Display the target...]**).

   ![](assets/query_example_result.png)

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo set di tre valori identifica la popolazione target della query. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

Questo valore è lo schema della tabella di lavoro. Questo parametro è valido per tutte le transizioni con **[!UICONTROL tableName]** e **[!UICONTROL schema]**.

## Ottimizzazione delle query {#optimizing-queries}

La sezione seguente fornisce le best practice per ottimizzare le query in esecuzione su Adobe Campaign al fine di limitare il carico di lavoro sul database e migliorare l’esperienza utente.

### Join e indici {#joins-and-indexes}

* Le query efficienti si basano sugli indici.
* Utilizzare un indice per tutti i join.
* La definizione dei collegamenti nello schema determinerà le condizioni di join. La tabella collegata deve avere un indice univoco sulla chiave primaria e il join deve trovarsi su questo campo.
* Eseguire join definendo chiavi in campi numerici anziché campi stringa.
* Evitare di eseguire outer join. Se possibile, utilizza il record ID zero per ottenere la funzionalità outer join.
* Utilizza il tipo di dati corretto per i join.

  Verificare che la clausola `where` sia dello stesso tipo del campo.

  Errore comune: `iBlacklist='3'` dove `iBlacklist` è un campo numerico e `3` indica un valore di testo.

  Assicurati di sapere quale sarà il piano di esecuzione della query. Evita scansioni complete delle tabelle, in particolare per query in tempo reale o quasi query in tempo reale in esecuzione ogni minuto.

  Per ulteriori informazioni, a seconda della versione di Campaign in uso, consulta le sezioni seguenti:

  ![](assets/do-not-localize/v7.jpeg)[Documentazione di Campaign v7](../../configuration/using/database-mapping.md)

  ![](assets/do-not-localize/v8.png)[Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/shemas-forms/database-mapping.html)

### Funzioni {#functions}

* Attenzione a funzioni come `Lower(...)`. Quando si utilizza la funzione Lower, non viene utilizzato Index.
* Controlla attentamente le query utilizzando l’istruzione &quot;like&quot; o le istruzioni &quot;upper&quot; o &quot;lower&quot;. Applica &quot;Upper&quot; all&#39;input dell&#39;utente, non al campo del database.

  Per ulteriori informazioni sulle funzioni, consulta [questa sezione](../../platform/using/defining-filter-conditions.md#list-of-functions).

### Filtrare le dimensioni {#filtering-dimensions}

Utilizza la dimensione di filtro della query invece di utilizzare l’operatore &quot;esiste come&quot;.

![](assets/optimize-queries-filtering.png)

Nelle query, le condizioni &quot;esiste come&quot; nei filtri non sono efficienti. Equivale a una sottoquery in SQL:

`select iRecipientId from nmsRecipient where iRecipientId IN (select iRecipientId from nmsBroadLog where (...))`

La best practice prevede invece di utilizzare la dimensione di filtro della query:

![](assets/optimize-queries-filtering2.png)

L&#39;equivalente della dimensione di filtro in SQL è l&#39;inner join:

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
  >Una funzione che funziona in un ambiente di sviluppo potrebbe non funzionare in un ambiente di produzione in cui i dati potrebbero essere diversi. Cercare di individuare le principali differenze per anticipare i rischi e preparare soluzioni.

* Creare configurazioni corrispondenti ai volumi di destinazione. Volumi di grandi dimensioni richiedono configurazioni specifiche. Una configurazione che ha funzionato per 100.000 destinatari potrebbe non funzionare per 10.000.000 di destinatari.

  Considera come il sistema si ridimensionerà quando andrà in diretta. Solo perché qualcosa funziona su piccola scala non significa che sarà adatto con volumi maggiori. Le prove devono essere eseguite con volumi simili al volume in produzione. È inoltre necessario valutare l’effetto delle modifiche nei volumi (numero di chiamate, dimensioni del database) nelle ore di picco, nei giorni di picco e per tutta la durata del progetto.
