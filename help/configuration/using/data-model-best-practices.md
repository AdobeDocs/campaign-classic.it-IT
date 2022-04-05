---
product: campaign
title: Best practice per i modelli di dati
description: Scopri come utilizzare il modello dati di Campaign Classic
feature: Data Model
exl-id: 9c59b89c-3542-4a17-a46f-3a1e58de0748
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '3988'
ht-degree: 1%

---

# Best practice per i modelli di dati{#data-model-best-practices}

![](../../assets/v7-only.svg)

Questo documento delinea i consigli chiave durante la progettazione del modello dati Adobe Campaign.

Per una migliore comprensione delle tabelle integrate di Campaign e della loro interazione, consulta [questa sezione](../../configuration/using/about-data-model.md) sezione .

Leggi [questa documentazione](../../configuration/using/about-schema-reference.md) per iniziare a utilizzare gli schemi di Campaign. Scopri come configurare gli schemi di estensione per estendere il modello di dati concettuale del database Adobe Campaign in [presente documento](../../configuration/using/about-schema-edition.md).

## Panoramica {#overview}

Il sistema Adobe Campaign è estremamente flessibile e può essere esteso oltre l&#39;implementazione iniziale. Tuttavia, mentre le possibilità sono infinite, è fondamentale prendere decisioni sagge e creare solide basi per iniziare a progettare il modello dati.

Questo documento fornisce casi d’uso comuni e best practice per imparare a progettare correttamente lo strumento Adobe Campaign.

## Architettura del modello dati {#data-model-architecture}

Adobe Campaign è un potente sistema di gestione delle campagne cross-channel che consente di allineare le strategie online e offline per creare esperienze cliente personalizzate.

### Approccio incentrato sul cliente {#customer-centric-approach}

Mentre la maggior parte dei provider di servizi e-mail comunica ai clienti con un approccio incentrato sull’elenco, Adobe Campaign si basa su un database relazionale per sfruttare una visione più ampia dei clienti e dei loro attributi.

Questo approccio incentrato sul cliente è mostrato nel grafico seguente. La **Destinatario** la tabella in grigio rappresenta la tabella cliente principale intorno alla quale viene creato tutto:

![](assets/customer-centric-data-model.png)

Per accedere alla descrizione di ciascuna tabella, vai a **[!UICONTROL Admin > Configuration > Data schemas]**, seleziona una risorsa dall’elenco e fai clic sul pulsante **[!UICONTROL Documentation]** scheda .

Il modello dati predefinito di Adobe Campaign è presentato in [presente documento](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Adobe Campaign Classic consente di creare una tabella cliente personalizzata. Tuttavia, nella maggior parte dei casi, si consiglia di sfruttare lo standard [Tabella destinatari](../../configuration/using/about-data-model.md#default-recipient-table) che dispone già di tabelle e funzionalità aggiuntive predefinite.

### Dati per Adobe Campaign {#data-for-campaign}

Quali dati devono essere inviati ad Adobe Campaign? È fondamentale determinare i dati necessari per le attività di marketing.

>[!NOTE]
>
>Adobe Campaign non è né un data warehouse né uno strumento di reporting. Pertanto, non cercare di importare in Adobe Campaign tutti i possibili clienti e le relative informazioni associate, né di importare dati che verranno utilizzati solo per generare rapporti.

Per decidere se un attributo sarebbe necessario o meno in Adobe Campaign, chiedi se rientra in una di queste categorie:

* Attributo utilizzato per **segmentazione**
* Attributo utilizzato per **processi di gestione dei dati** (calcolo aggregato, ad esempio)
* Attributo utilizzato per **personalizzazione**

Se non rientra in nessuno di questi, è molto probabile che questo attributo non sarà necessario in Adobe Campaign.

### Scelta dei tipi di dati {#data-types}

Per garantire una buona architettura e prestazioni del sistema, segui le best practice riportate di seguito per configurare i dati in Adobe Campaign.

* Una tabella di grandi dimensioni deve avere per lo più campi numerici e contenere collegamenti a tabelle di riferimento (quando si lavora con un elenco di valori).
* La **expr** l’attributo consente di definire un attributo dello schema come campo calcolato anziché come valore di set fisico in una tabella. In questo modo è possibile accedere alle informazioni in un formato diverso (ad esempio per l’età e la data di nascita) senza dover memorizzare entrambi i valori. Questo è un buon modo per evitare la duplicazione dei campi. Ad esempio, la tabella Destinatario utilizza un’espressione per il dominio, già presente nel campo e-mail.
* Tuttavia, quando il calcolo dell’espressione è complesso, si sconsiglia di utilizzare la variabile **expr** l’attributo come calcolo immediato può influire sulle prestazioni delle query.
* La **XML** Il tipo è un buon modo per evitare di creare troppi campi. Ma occupa anche spazio su disco in quanto utilizza una colonna CLOB nel database. Può anche portare a query SQL complesse e può influire sulle prestazioni.
* La lunghezza di un **string** deve sempre essere definito con la colonna . Per impostazione predefinita, la lunghezza massima in Adobe Campaign è 255, ma Adobe consiglia di mantenere il campo più breve se sai già che la dimensione non supererà una lunghezza più breve.
* È accettabile avere un campo più breve in Adobe Campaign rispetto al sistema di origine se si è certi che la dimensione nel sistema di origine è stata sopravvalutata e non verrà raggiunta. Ciò potrebbe significare una stringa più breve o un numero intero più piccolo in Adobe Campaign.

### Scelta dei campi {#choice-of-fields}

Un campo deve essere memorizzato in una tabella se ha uno scopo di targeting o personalizzazione. In altre parole, se un campo non viene utilizzato per inviare un’e-mail personalizzata o come criterio in una query, occupa spazio su disco mentre è inutile.

Per le istanze ibride e on-premise, FDA (Federated Data Access, una funzione opzionale che consente di accedere ai dati esterni) copre la necessità di aggiungere un campo &quot;on-the-fly&quot; durante un processo di campagna. Non è necessario importare tutto se si dispone di FDA. Per ulteriori informazioni, consulta [Informazioni su Federated Data Access](../../installation/using/about-fda.md).

### Scelta di chiavi {#choice-of-keys}

Oltre al **autopk** definito per impostazione predefinita nella maggior parte delle tabelle, è consigliabile aggiungere alcune chiavi logiche o aziendali (numero di account, numero di client e così via). Può essere utilizzato successivamente per le importazioni/riconciliazione o i pacchetti di dati. Per ulteriori informazioni, consulta [Identificatori](#identifiers).

Le chiavi efficienti sono essenziali per le prestazioni. I tipi di dati numerici devono sempre essere preferiti come chiavi per le tabelle.

Per il database SQLServer, è possibile utilizzare &quot;indice cluster&quot; se le prestazioni sono necessarie. Poiché Adobe non gestisce questa operazione, è necessario crearla in SQL.

### Tablespace dedicate {#dedicated-tablespaces}

L&#39;attributo della tablespace nello schema consente di specificare una tablespace dedicata per una tabella.

La procedura guidata di installazione consente di memorizzare gli oggetti per tipo (dati, temporanei e indice).

Le tablespace dedicate sono migliori per il partizionamento, le regole di sicurezza e consentono un&#39;amministrazione fluida e flessibile, una migliore ottimizzazione e prestazioni.

## Identificatori {#identifiers}

Le risorse Adobe Campaign hanno tre identificatori ed è possibile aggiungere un identificatore aggiuntivo.

Nella tabella seguente sono descritti questi identificatori e il loro scopo.

| Identificatore | Descrizione | Best practice |
|--- |--- |--- |
| ID | <ul><li>L’id è la chiave primaria fisica di una tabella Adobe Campaign. Per le tabelle pronte all’uso, si tratta di un numero generato a 32 bit da una sequenza</li><li>Questo identificatore è in genere univoco per una specifica istanza di Adobe Campaign. </li><li>Un id generato automaticamente può essere visibile in una definizione dello schema. Cerca nel *autopk=&quot;true&quot;* attributo.</li></ul> | <ul><li>Gli identificatori generati automaticamente non devono essere utilizzati come riferimento in un flusso di lavoro o nella definizione di un pacchetto.</li><li>Non si deve presumere che l&#39;id sarà sempre un numero crescente.</li><li>L’ID in una tabella standard è un numero a 32 bit e questo tipo non deve essere modificato. Questo numero è tratto da una &quot;sequenza&quot; coperta nella sezione con lo stesso nome.</li></ul> |
| Nome (o nome interno) | <ul><li>Queste informazioni sono un identificatore univoco di un record in una tabella. Questo valore può essere aggiornato manualmente, in genere con un nome generato.</li><li>Questo identificatore mantiene il suo valore quando viene distribuito in un’istanza diversa di Adobe Campaign e non deve essere vuoto.</li></ul> | <ul><li>Rinomina il nome del record generato da Adobe Campaign se l’oggetto deve essere distribuito da un ambiente a un altro.</li><li>Quando un oggetto ha un attributo namespace (*schema* ad esempio), questo namespace comune verrà utilizzato in tutti gli oggetti personalizzati creati. Alcuni spazi dei nomi riservati non devono essere utilizzati: *nms*, *xtk*, *nl*, *ncl*, *crm*, *xxl*.</li><li>Quando un oggetto non ha uno spazio dei nomi (*workflow* o *consegna* ad esempio), questa nozione di namespace verrebbe aggiunta come prefisso di un oggetto nome interno: *namespaceMyObjectName*.</li><li>Non utilizzare caratteri speciali come lo spazio &quot;&quot;, la semicolonna &quot;:&quot; o il trattino &quot;-&quot;. Tutti questi caratteri verranno sostituiti da un carattere di sottolineatura &quot;_&quot; (carattere consentito). Ad esempio, &quot;abc-def&quot; e &quot;abc:def&quot; vengono memorizzati come &quot;abc_def&quot; e si sovrascrivono a vicenda.</li></ul> |
| Etichetta | <ul><li>L’etichetta è l’identificatore aziendale di un oggetto o record in Adobe Campaign.</li><li>Questo oggetto consente spazi e caratteri speciali.</li><li>Non garantisce l&#39;unicità di un documento.</li></ul> | <ul><li>È consigliabile determinare una struttura per le etichette degli oggetti.</li><li>Questa è la soluzione più semplice da usare per identificare un record o un oggetto per un utente Adobe Campaign.</li></ul> |

## Chiavi interne personalizzate {#custom-internal-keys}

Le chiavi primarie sono necessarie per ogni tabella creata in Adobe Campaign.

La maggior parte delle organizzazioni importa record da sistemi esterni. Anche se la chiave fisica della tabella Destinatario è l’attributo &quot;id&quot;, è possibile determinare anche una chiave personalizzata.

Questa chiave personalizzata è la chiave primaria del record effettiva nel sistema esterno che alimenta Adobe Campaign.

Quando una tabella preconfigurata presenta sia un&#39;autopsia che una chiave interna, la chiave interna viene impostata come un indice univoco nella tabella del database fisico.

Durante la creazione di una tabella personalizzata sono disponibili due opzioni:
* Combinazione di chiave generata automaticamente (id) e chiave interna (personalizzata). Questa opzione è interessante se la chiave di sistema è una chiave composita o non un numero intero. I numeri interi forniranno prestazioni più elevate nei grandi tavoli e uniranno ad altri tavoli.
* Utilizzo della chiave primaria come chiave primaria del sistema esterno. Questa soluzione è solitamente preferita in quanto semplifica l&#39;approccio all&#39;importazione e all&#39;esportazione di dati, con una chiave coerente tra i diversi sistemi. L’opzione Autopk deve essere disabilitata se la chiave è denominata &quot;id&quot; e deve essere compilata con valori esterni (non generato automaticamente).

>[!IMPORTANT]
>
>Un&#39;autopsia non deve essere utilizzata come riferimento nei flussi di lavoro.

## Sequenze {#sequences}

La chiave primaria di Adobe Campaign è un id generato automaticamente per tutte le tabelle predefinite e può essere lo stesso per le tabelle personalizzate. Per ulteriori informazioni, consulta [questa sezione](#identifiers).

Questo valore è tratto da ciò che viene chiamato un **sequenza**, che è un oggetto di database utilizzato per generare una sequenza numerica.

Esistono due tipi di sequenze:
* **Condiviso**: più di una tabella sceglierebbe il loro id dalla stessa sequenza. Ciò significa che se un id &#39;X&#39; viene utilizzato da una tabella, nessun&#39;altra tabella che condivide la stessa sequenza avrà un record con quell&#39;id &#39;X&#39;. **XtkNewId** è la sequenza condivisa predefinita disponibile in Adobe Campaign.
* **Dedicato**: una sola tabella sta scegliendo gli ID dalla sequenza. In genere, il nome della sequenza contiene il nome della tabella.

>[!IMPORTANT]
>
>La sequenza è un valore intero a 32 bit, con un numero massimo finito di valori disponibili: 2,14 miliardi. Una volta raggiunto il valore massimo, la sequenza torna a 0 per riciclare gli ID.
>
>Se i vecchi dati non sono stati eliminati, il risultato sarà una violazione chiave univoca, che diventa un blocco per lo stato e l’utilizzo della piattaforma. Adobe Campaign non sarebbe in grado di inviare comunicazioni (quando influisce sulla tabella dei registri di consegna) e le prestazioni sarebbero fortemente influenzate.

Pertanto, un cliente che invia 6 miliardi di e-mail all’anno con un periodo di conservazione di 180 giorni per i propri log avrebbe esaurito gli id in 4 mesi. Per evitare tale problema, assicurati di avere le impostazioni di eliminazione in base ai volumi. Per ulteriori informazioni, consulta [questa sezione](#data-retention).

Quando viene creata una tabella personalizzata in Adobe Campaign con una chiave primaria come autoPK, a tale tabella deve essere sistematicamente associata una sequenza personalizzata dedicata.

Per impostazione predefinita, una sequenza personalizzata avrà valori compresi tra +1.000 e +2,1BB. Tecnicamente, è possibile ottenere una gamma completa di 4BB abilitando gli id negativi. Questo dovrebbe essere utilizzato con cura e un ID andrà perso quando si passa da numeri negativi a numeri positivi: il record 0 viene in genere ignorato da Adobe Campaign nelle query SQL generate.

Per ulteriori informazioni sull&#39;esaurimento delle sequenze, guarda [questo video](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Indici {#indexes}

Gli indici sono essenziali per le prestazioni. Quando si dichiara una chiave nello schema, Adobe creerà automaticamente un indice sui campi della chiave. È inoltre possibile dichiarare altri indici per le query che non utilizzano la chiave.

Adobe consiglia di definire indici aggiuntivi in quanto potrebbero migliorare le prestazioni.

Tuttavia, tieni presente quanto segue:

* L&#39;utilizzo dell&#39;indice è associato al pattern di accesso. L’ottimizzazione dell’indicizzazione è spesso una parte fondamentale della progettazione del database e deve essere gestita da esperti. L’aggiunta degli indici è spesso un flusso di lavoro iterativo associato alla manutenzione del database. Viene eseguito nel tempo, passo dopo passo, per risolvere i problemi di prestazioni quando si verificano.
* Gli indici aumentano la dimensione complessiva della tabella (per memorizzare l&#39;indice stesso).
* L&#39;aggiunta di un indice sulle colonne può migliorare le prestazioni dell&#39;accesso in lettura dei dati (SELECT), ma può diminuire le prestazioni dell&#39;accesso in scrittura dei dati (UPDATE).
* Poiché questo influisce sulle prestazioni durante l’inserimento dei dati, gli indici devono avere dimensioni e numero limitati.
* Non aggiungere indici se non necessario. Assicurati che sia necessario e che aumenti le prestazioni complessive delle query (test e apprendimento).
* In generale, un indice è efficiente se sai che le tue query non restituiranno più del 10% dei record.
* Seleziona con attenzione gli indici da definire.
* Non rimuovere indici nativi dalle tabelle predefinite.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Esempio

La gestione degli indici può diventare molto complessa, quindi è importante capire come funzionano. Per illustrare questa complessità, prendiamo un esempio di base, ad esempio la ricerca dei destinatari filtrando il nome e il cognome. Per eseguire questa operazione:
1. Passa alla cartella in cui sono elencati tutti i destinatari nel database. Per ulteriori informazioni, consulta [Gestione dei profili di ](../../platform/using/managing-profiles.md).
1. Fai clic con il pulsante destro del mouse sul pulsante **[!UICONTROL First name]** campo .
1. Seleziona **[!UICONTROL Filter on this field]**.

   ![](assets/data-model-index-example.png)

1. Ripeti questa operazione per **[!UICONTROL Last name]** campo .

I due filtri corrispondenti vengono aggiunti sopra lo schermo.

![](assets/data-model-index-search.png)

È ora possibile eseguire il filtro di ricerca nel **[!UICONTROL First name]** e **[!UICONTROL Last name]** campi in base alle varie condizioni del filtro.

Ora, per velocizzare la ricerca su questi filtri, puoi aggiungere indici. Ma quali indici dovrebbero essere utilizzati?

>[!NOTE]
>
>Questo esempio si applica ai clienti in hosting che utilizzano un database PostgreSQL.

La tabella seguente mostra i casi in cui i tre indici descritti di seguito vengono utilizzati o meno in base al pattern di accesso visualizzato nella prima colonna.

| Criteri di ricerca | Indice 1 (Nome + Cognome) | Indice 2 (solo nome) | Indice 3 (solo cognome) | Commenti |
|--- |--- |--- |--- |--- |
| Nome uguale a &quot;Johnny&quot; | Utilizzato | Utilizzato | Non utilizzato | Poiché il nome è in prima posizione sull&#39;indice 1, verrà comunque utilizzato: non è necessario aggiungere un criterio al cognome. |
| Il nome è uguale a &quot;Johnny&quot; E il cognome è uguale a &quot;Smith&quot; | Utilizzato | Non utilizzato | Non utilizzato | Poiché nella stessa query vengono cercati entrambi gli attributi, verrà utilizzato solo l’indice che combina entrambi gli attributi. |
| Cognome uguale a &quot;Smith&quot; | Non utilizzato | Non utilizzato | Utilizzato | Si tiene conto dell&#39;ordine degli attributi nell&#39;indice. Se l&#39;ordine non corrisponde, l&#39;indice potrebbe non essere utilizzato. |
| Il nome inizia con &quot;Joh&quot; | Utilizzato | Utilizzato | Non utilizzato | &quot;Ricerca a sinistra&quot; abilita gli indici. |
| Il nome termina con &quot;nny&quot; | Non utilizzato | Non utilizzato | Non utilizzato | &quot;Ricerca corretta&quot; disabilita gli indici e viene eseguita una scansione completa. Alcuni tipi di indice specifici possono gestire questo caso d’uso, ma non sono disponibili per impostazione predefinita in Adobe Campaign. |
| Il nome contiene &quot;John&quot; | Non utilizzato | Non utilizzato | Non utilizzato | Questa è una combinazione di ricerche &quot;sinistra&quot; e &quot;destra&quot;. A causa di quest&#39;ultimo, disabiliterà gli indici e verrà eseguita una scansione completa. |
| Nome uguale a &quot;john&quot; | Non utilizzato | Non utilizzato | Non utilizzato | Gli indici sono sensibili all&#39;uso di maiuscole e minuscole. Per evitare la distinzione tra maiuscole e minuscole, è necessario creare un indice specifico che includa una funzione SQL come &quot;Upper(firstname)&quot;. Dovresti fare lo stesso con altre trasformazioni di dati come &quot;unaccen(firstname)&quot;. |

## Collegamenti e cardinalità {#links-and-cardinality}

### Collegamenti {#links}

Attenzione all&#39;integrità &quot;propria&quot; su grandi tavoli. L&#39;eliminazione di record con tabelle ampie con integrità &quot;propria&quot; può arrestare l&#39;istanza. La tabella è bloccata e le eliminazioni vengono effettuate una per una. Quindi è meglio utilizzare l&#39;integrità &quot;neutrale&quot; sui tavoli figli che hanno grandi volumi.

La dichiarazione di un collegamento come join esterno non è valida per le prestazioni. Il record zero-id emula la funzionalità di join esterno. Non è necessario dichiarare giunti esterni se il collegamento utilizza l&#39;autopsia.

Sebbene sia possibile unire qualsiasi tabella in un flusso di lavoro, Adobe consiglia di definire collegamenti comuni tra le risorse direttamente nella definizione della struttura dati.

Il collegamento deve essere definito in allineamento con i dati effettivi nelle tabelle. Una definizione errata potrebbe influire sui dati recuperati tramite i collegamenti, ad esempio duplicando inaspettatamente i record.

Assegna al collegamento un nome coerente con il nome della tabella: il nome del collegamento dovrebbe aiutare a comprendere cosa sia la tabella lontana.

Non denominare un collegamento con &quot;id&quot; come suffisso. Ad esempio, denominalo &quot;transaction&quot; anziché &quot;transactionId&quot;.

Per impostazione predefinita, Adobe Campaign crea un collegamento utilizzando la chiave primaria della tabella esterna. Per una maggiore chiarezza, è preferibile definire esplicitamente il join nella definizione del collegamento.

Verrà aggiunto un indice agli attributi utilizzati in un collegamento.

In molte tabelle sono presenti i collegamenti creati da e modificati da ultimo. È possibile disabilitare l&#39;indice utilizzando l&#39;attributo noDbIndex sul collegamento, se queste informazioni non vengono utilizzate dall&#39;azienda.

### Cardinalità {#cardinality}

Quando progetti un collegamento, assicurati che il record di destinazione sia univoco quando è stata dichiarata una relazione 1-1. In caso contrario, il join potrebbe restituire più record quando è previsto un solo record. Questo si traduce in errori durante la preparazione della consegna quando &quot;la query restituisce più righe del previsto&quot;. Imposta il nome del collegamento sullo stesso nome dello schema di destinazione.

Definisci un collegamento con una cardinalità (1-N) nello schema sul lato (1). Ad esempio, la transazione Destinatario relazione (1) - (N) deve essere definita nello schema della transazione.

Per impostazione predefinita, una cardinalità inversa di un collegamento è (N). È possibile definire un collegamento (1-1) aggiungendo l&#39;attributo revCardinality=&#39;single&#39; alla definizione del collegamento.

Se il link inverso non deve essere visibile all&#39;utente, puoi nasconderlo con la definizione del link revLink=&#39;_NESSUNO_&quot;. Un buon caso d’uso è quello di definire un collegamento tra il destinatario e l’ultima transazione completata, ad esempio. Devi solo visualizzare il collegamento dal destinatario all’ultima transazione e non è necessario alcun link di storno per essere visibile dalla tabella delle transazioni.

I collegamenti che eseguono un join esterno (1-0.1) devono essere utilizzati con attenzione in quanto influiranno sulle prestazioni del sistema.

## Conservazione dei dati: pulizia ed eliminazione {#data-retention}

Adobe Campaign non è né un data warehouse né uno strumento di reporting. Pertanto, per garantire buone prestazioni della soluzione Adobe Campaign, la crescita del database dovrebbe rimanere sotto controllo. A questo scopo, segui alcune delle best practice riportate di seguito.

Per impostazione predefinita, i registri di consegna e tracciamento di Adobe Campaign hanno una durata di conservazione di 180 giorni. Viene eseguito un processo di pulizia per rimuovere i registri precedenti.

* Se desideri mantenere i registri più a lungo, questa decisione deve essere presa con attenzione in base alle dimensioni del database e al volume dei messaggi inviati. Come promemoria, la sequenza Adobe Campaign è un numero intero a 32 bit.
* Si raccomanda di non avere più di 1 miliardo di record alla volta in queste tabelle (circa il 50% dei 2,14 miliardi di id disponibili) per limitare i rischi di consumo di tutti gli id disponibili. Alcuni clienti dovranno ridurre la durata di conservazione al di sotto dei 180 giorni.

Ulteriori informazioni sulla conservazione dei dati in [Linee guida sulla privacy e sulla sicurezza delle campagne](../../platform/using/privacy-and-recommendations.md).

Ulteriori informazioni sul flusso di lavoro di pulizia della base dati di Campaign [in questa sezione](../../production/using/database-cleanup-workflow.md).

>[!IMPORTANT]
>
>Le tabelle personalizzate non vengono eliminate con il processo di pulizia standard. Anche se questo potrebbe non essere necessario il primo giorno, non dimenticare di creare un processo di eliminazione per le tabelle personalizzate in quanto ciò potrebbe portare a problemi di prestazioni.

Sono disponibili alcune soluzioni per ridurre al minimo la necessità di record in Adobe Campaign:
* Esporta i dati in un data warehouse esterno ad Adobe Campaign.
* Genera valori aggregati che utilizzeranno meno spazio pur essendo sufficienti per le tue pratiche di marketing. Ad esempio, non è necessaria l’intera cronologia delle transazioni cliente in Adobe Campaign per tenere traccia degli ultimi acquisti.

È possibile dichiarare l&#39;attributo &quot;deleteStatus&quot; in uno schema. È più efficiente contrassegnare il record come eliminato, quindi rimandare l&#39;eliminazione nell&#39;attività di pulizia.

## Prestazioni {#performance}

Per garantire prestazioni migliori in qualsiasi momento, segui le best practice riportate di seguito.

### Raccomandazioni generali {#general-recommendations}

* Evitare di utilizzare operazioni come &quot;CONTAINS&quot; nelle query. Se sai cosa ci si aspetta e vuoi filtrare, applica la stessa condizione con un operatore di filtro &quot;EQUAL TO&quot; o con altri operatori di filtro specifici.
* Evita di unirsi a campi non indicizzati durante la creazione di dati nei flussi di lavoro.
* Cerca di assicurarsi che i processi come l&#39;importazione e l&#39;esportazione avvengano al di fuori dell&#39;orario di lavoro.
* Assicurati che ci sia una pianificazione per tutte le attività quotidiane e attieniti alla pianificazione.
* Se uno o pochi dei processi giornalieri non riescono e se è obbligatorio eseguirlo lo stesso giorno, assicurati che non vi siano processi in conflitto in esecuzione quando il processo manuale viene avviato in quanto ciò potrebbe influire sulle prestazioni del sistema.
* Assicurati che nessuna delle campagne giornaliere venga eseguita durante il processo di importazione o quando viene eseguito un processo manuale.
* Utilizzare una o più tabelle di riferimento anziché duplicare un campo in ogni riga. Quando si utilizzano coppie chiave/valore, è preferibile scegliere una chiave numerica.
* Una stringa breve rimane accettabile. Nel caso in cui le tabelle di riferimento siano già presenti in un sistema esterno, il riutilizzo dello stesso agevolerà l’integrazione dei dati con Adobe Campaign.

### Relazioni uno-a-molti {#one-to-many-relationships}

* La progettazione dei dati influisce su usabilità e funzionalità. Se si progetta il modello dati con molte relazioni uno-a-molti, risulta più difficile per gli utenti creare una logica significativa nell’applicazione. La logica di filtro uno-a-molti può essere difficile per gli addetti al marketing non tecnici creare e comprendere correttamente.
* È opportuno disporre di tutti i campi essenziali in una tabella, in quanto semplifica la creazione delle query da parte degli utenti. A volte è anche utile che le prestazioni duplichino alcuni campi tra le tabelle, se è possibile evitare un join.
* Alcune funzionalità integrate non saranno in grado di fare riferimento a relazioni uno-a-molti, ad esempio, formula di ponderazione delle offerte e consegne.

## Tabelle grandi {#large-tables}

Adobe Campaign si basa su motori di database di terze parti. A seconda del provider, l’ottimizzazione delle prestazioni per le tabelle più grandi può richiedere una progettazione specifica.

Di seguito sono riportate alcune best practice comuni da seguire per progettare il modello dati utilizzando tabelle di grandi dimensioni e join complessi.

* Quando utilizzi tabelle dei destinatari personalizzate aggiuntive, assicurati di disporre di una tabella di registro dedicata per ogni mappatura della consegna.
* Ridurre il numero di colonne, in particolare identificando quelle inutilizzate.
* Ottimizza le relazioni del modello dati evitando join complessi, ad esempio join su più condizioni e/o più colonne.
* Per le chiavi di join, utilizzare sempre dati numerici anziché stringhe di caratteri.
* Riduci quanto più possibile la profondità di conservazione del registro. Se hai bisogno di una cronologia più approfondita, puoi aggregare il calcolo e/o gestire tabelle di log personalizzate per memorizzare una cronologia più grande.

### Dimensioni delle tabelle {#size-of-tables}

La dimensione della tabella è una combinazione del numero di record e del numero di colonne per record. Entrambi possono influire sulle prestazioni delle query.

* A **di piccole dimensioni** è simile alla tabella Consegna .
* A **media dimensione** è uguale alla dimensione della tabella Destinatario. Ha un record per cliente.
* A **di grandi dimensioni** La tabella è simile alla tabella di registro Ampio. Ha molti documenti per cliente.
Ad esempio, se il database contiene 10 milioni di destinatari, la tabella di registro Ampio contiene da 100 a 200 milioni di messaggi e la tabella Consegna contiene alcune migliaia di record.

Su PostgreSQL, una riga non deve superare gli 8 KB per evitare [TOUR](https://wiki.postgresql.org/wiki/TOAST) meccanismo. Pertanto, cerca di ridurre il più possibile il numero di colonne e la dimensione di ogni riga per preservare le prestazioni ottimali del sistema (memoria e CPU).

Anche il numero di righe influisce sulle prestazioni. Il database Adobe Campaign non è progettato per memorizzare dati storici non utilizzati attivamente per il targeting o la personalizzazione, si tratta di un database operativo.

Per evitare problemi di prestazioni relativi al numero elevato di righe, conservare solo i record necessari nel database. Qualsiasi altro record deve essere esportato in un data warehouse di terze parti e rimosso dal database operativo Adobe Campaign.

Di seguito sono riportate alcune best practice relative alle dimensioni delle tabelle:

* Progettazione di tabelle di grandi dimensioni con meno campi e più dati numerici.
* Non utilizzare un numero elevato di colonne (ad esempio: Int64) per memorizzare numeri piccoli come valori booleani.
* Rimuovere le colonne non utilizzate dalla definizione della tabella.
* Non conservare i dati storici o inattivi nel database Adobe Campaign (esportazione e pulizia).

Ecco un esempio:

![](assets/transaction-table-example.png)

In questo esempio:
* La *Transazione* e *Articolo transazione* le tabelle sono grandi: più di 10 milioni.
* La *Prodotto* e *Store* le tabelle sono più piccole: meno di 10.000.
* L&#39;etichetta e il riferimento del prodotto sono stati inseriti nel *Prodotto* tabella.
* La *Articolo transazione* la tabella presenta solo un collegamento alla tabella *Prodotto* tabella, numerica.
