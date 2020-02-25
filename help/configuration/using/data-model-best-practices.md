---
title: Utilizzo della tabella Destinatari classici di Adobe Campaign
description: Scopri come utilizzare la tabella dei destinatari out-of-the-box in Adobe Campaign Classic durante la progettazione del modello dati.
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8bfeaecc8a4832cac96f479ea1a0b11cd73c1e8

---


# Best practice per i modelli di dati{#data-model-best-practices}

Questo documento delinea le raccomandazioni chiave durante la progettazione del modello dati di Adobe Campaign.

Per una migliore comprensione delle tabelle integrate in Campaign e della loro interazione, consulta la sezione relativa al modello [di dati](../../configuration/using/about-data-model.md) Campaign Classic.

Leggi questa [documentazione](../../configuration/using/about-schema-reference.md) per iniziare a usare gli schemi di Campaign. Scopri come configurare gli schemi di estensione per estendere il modello di dati concettuali del database Adobe Campaign in questo [documento](../../configuration/using/about-schema-edition.md).

## Panoramica {#overview}

Il sistema Adobe Campaign è estremamente flessibile e può essere esteso oltre l&#39;implementazione iniziale. Tuttavia, mentre le possibilità sono infinite, è fondamentale prendere decisioni sagge e creare solide basi per iniziare a progettare il modello dati.

Questo documento fornisce esempi d&#39;uso comuni e procedure ottimali per imparare a progettare correttamente lo strumento Adobe Campaign.

## Architettura del modello dati {#data-model-architecture}

Adobe Campaign Standard è un potente sistema di gestione delle campagne multicanale che consente di allineare le strategie online e offline per creare esperienze cliente personalizzate.

### Metodo incentrato sul cliente {#customer-centric-approach}

Mentre la maggior parte dei provider di servizi e-mail comunica ai clienti tramite un approccio incentrato sugli elenchi, Adobe Campaign si avvale di un database relazionale per sfruttare una visione più ampia dei clienti e dei loro attributi.

Questo approccio incentrato sul cliente è riportato nel grafico seguente. La tabella **Destinatario** in grigio rappresenta la tabella cliente principale intorno alla quale viene creato tutto:

![](assets/customer-centric-data-model.png)

Per accedere alla descrizione di ciascuna tabella, passare a **[!UICONTROL Admin > Configuration > Data schemas]**, selezionare una risorsa dall&#39;elenco e fare clic sulla **[!UICONTROL Documentation]** scheda.

Il modello dati predefinito di Adobe Campaign è presentato in questo [documento](https://final-docs.campaign.adobe.com/doc/AC/en/technicalResources/_Datamodel_Description_of_the_main_tables.html).

>[!NOTE]
>
>Adobe Campaign Classic consente di creare una tabella cliente personalizzata. Tuttavia, nella maggior parte dei casi, si consiglia di utilizzare la tabella [](../../configuration/using/default-recipient-table.md) Destinatario standard che dispone già di tabelle e funzionalità aggiuntive preconfigurate.

### Dati per Adobe Campaign {#data-for-campaign}

Quali dati devono essere inviati ad Adobe Campaign? È fondamentale determinare i dati richiesti per le attività di marketing.

>[!NOTE]
>
>Adobe Campaign non è né un data warehouse né uno strumento di reporting. Pertanto, non cercare di importare in Adobe Campaign tutti i possibili clienti e le relative informazioni associate, né di importare dati che verranno utilizzati solo per creare rapporti.

Per decidere se un attributo sarebbe necessario o meno in Adobe Campaign, chiedi se rientra in una delle seguenti categorie:

* Attributo utilizzato per la **segmentazione**
* Attributo utilizzato per i processi **di gestione dei** dati (ad esempio, calcolo aggregato)
* Attributo utilizzato per la **personalizzazione**

Se non rientri in nessuno di questi elementi, molto probabilmente non avrai bisogno di questo attributo in Adobe Campaign.

## Scelta dei tipi di dati {#data-types}

Per garantire una buona architettura e prestazioni del sistema, segui le best practice riportate di seguito per configurare i dati in Adobe Campaign.

* Una tabella di grandi dimensioni deve avere principalmente campi numerici e contenere collegamenti alle tabelle di riferimento (quando si utilizza un elenco di valori).
* L&#39;attributo **espr** consente di definire un attributo di schema come campo calcolato anziché come valore di set fisico in una tabella. In questo modo è possibile accedere alle informazioni in un formato diverso (ad esempio per l’età e la data di nascita) senza dover memorizzare entrambi i valori. Questo è un buon modo per evitare la duplicazione di campi. Ad esempio, la tabella Destinatario utilizza un&#39;espressione per il dominio, già presente nel campo e-mail.
* Tuttavia, quando il calcolo dell&#39;espressione è complesso, si consiglia di non utilizzare l&#39;attributo **espr** come calcolo al volo potrebbe influire sulle prestazioni delle query.
* Il tipo **XML** è un metodo utile per evitare di creare troppi campi. ma occupa anche spazio su disco in quanto utilizza una colonna CLOB nel database. Può inoltre causare query SQL complesse e avere un impatto sulle prestazioni.
* La lunghezza di un campo **stringa** deve essere sempre definita con la colonna. Per impostazione predefinita, la lunghezza massima in Adobe Campaign è 255, ma Adobe consiglia di ridurre la lunghezza del campo se già sai che la dimensione non supererà una lunghezza inferiore.
* In Adobe Campaign è accettabile avere un campo più breve rispetto a quello del sistema di origine, se sei certo che la dimensione nel sistema di origine sia stata sopravvalutata e che non venga raggiunta. Ciò potrebbe significare una stringa più corta o un numero intero più piccolo in Adobe Campaign.

## Identificatori {#identifiers}

Le risorse di Adobe Campaign hanno tre identificatori ed è possibile aggiungere un identificatore aggiuntivo.

La tabella seguente descrive questi identificatori e la loro funzione.

| Identificatore | Descrizione | Best practice |
|--- |--- |--- |
| Id | <ul><li>L&#39;ID è la chiave primaria fisica di una tabella di Adobe Campaign. Per le tabelle pronte all&#39;uso, si tratta di un numero generato a 32 bit da una sequenza</li><li>Questo identificatore è in genere univoco per una specifica istanza di Adobe Campaign. </li><li>Un ID generato automaticamente può essere visibile in una definizione dello schema. Cercate l&#39;attributo *autopk=&quot;true&quot;* .</li></ul> | <ul><li>Gli identificatori generati automaticamente non devono essere utilizzati come riferimento in un flusso di lavoro o in una definizione di pacchetto.</li><li>Non si deve presumere che l&#39;ID sia sempre un numero crescente.</li><li>L’ID in una tabella out-of-the-box è un numero a 32 bit e questo tipo non deve essere modificato. Questo numero è tratto da una &quot;sequenza&quot; coperta nella sezione con lo stesso nome.</li></ul> |
| Nome (o nome interno) | <ul><li>Queste informazioni sono un identificatore univoco di un record in una tabella. Questo valore può essere aggiornato manualmente, in genere con un nome generato.</li><li>Questo identificatore mantiene il suo valore quando viene distribuito in un&#39;altra istanza di Adobe Campaign e non deve essere vuoto.</li></ul> | <ul><li>Rinominare il nome del record generato da Adobe Campaign se l&#39;oggetto è destinato a essere distribuito da un ambiente a un altro.</li><li>Quando un oggetto dispone di un attributo spazio nomi (*schema* ad esempio), lo spazio nomi comune verrà utilizzato in tutti gli oggetti personalizzati creati. Alcuni spazi dei nomi riservati non devono essere utilizzati: *nms*, *xtk*.</li><li>Quando un oggetto non ha uno spazio nomi (ad esempio,*flusso* di lavoro o *consegna* ), questa nozione dello spazio nomi viene aggiunta come prefisso di un oggetto nome interno: *namespaceMyObjectName*.</li><li>Non utilizzate caratteri speciali come lo spazio &quot;&quot;, la colonna &quot;:&quot; o il trattino &quot;-&quot;. Tutti questi caratteri vengono sostituiti da un carattere di sottolineatura &quot;_&quot; (caratteri consentiti). Ad esempio, &quot;abc-def&quot; e &quot;abc:def&quot; vengono memorizzati come &quot;abc_def&quot; e si sovrascrivono a vicenda.</li></ul> |
| Etichetta | <ul><li>L&#39;etichetta è l&#39;identificatore aziendale di un oggetto o di un record in Adobe Campaign.</li><li>Questo oggetto consente spazi e caratteri speciali.</li><li>Non garantisce l&#39;unicità di un documento.</li></ul> | <ul><li>È consigliabile determinare una struttura per le etichette degli oggetti.</li><li>Questa è la soluzione più semplice da usare per identificare un record o un oggetto per un utente di Adobe Campaign.</li></ul> |

## Chiavi interne personalizzate {#custom-internal-keys}

Le chiavi primarie sono necessarie per ogni tabella creata in Adobe Campaign.

La maggior parte delle organizzazioni sta importando record da sistemi esterni. Mentre la chiave fisica della tabella Recipient è l&#39;attributo &quot;id&quot;, è possibile determinare anche una chiave personalizzata.

Questa chiave personalizzata è la chiave primaria del record effettiva nel sistema esterno che alimenta Adobe Campaign.

Quando una tabella out-of-the-box ha sia un pilota automatico che una chiave interna, la chiave interna sarà impostata come un indice univoco nella tabella del database fisico.

Quando si crea una tabella personalizzata, sono disponibili due opzioni:
* Combinazione di chiave generata automaticamente (id) e chiave interna (personalizzata). Questa opzione è interessante se la chiave di sistema è una chiave composita o non un numero intero. Gli interi forniranno prestazioni più elevate nelle grandi tabelle e uniranno ad altre tabelle.
* Utilizzo della chiave primaria come chiave primaria del sistema esterno. Questa soluzione è generalmente preferita in quanto semplifica l&#39;approccio all&#39;importazione e all&#39;esportazione dei dati, con una chiave coerente tra i diversi sistemi. L&#39;opzione Autopk deve essere disabilitata se la chiave è denominata &quot;id&quot; e deve essere compilata con valori esterni (non generato automaticamente).

>[!IMPORTANT]
>
>Un&#39;autopsia non deve essere utilizzata come riferimento nei flussi di lavoro.

## Sequenze {#sequences}

La chiave primaria di Adobe Campaign è un ID generato automaticamente per tutte le tabelle pronte all&#39;uso e può essere lo stesso per le tabelle personalizzate. Per ulteriori informazioni, consulta [questa sezione](#identifiers).

Questo valore viene ricavato da quella che viene chiamata **sequenza**, ovvero un oggetto di database utilizzato per generare una sequenza numerica.

Esistono due tipi di sequenze:
* **Condiviso**: più di una tabella sceglierebbe il proprio ID dalla stessa sequenza. Significa che se un id &#39;X&#39; viene utilizzato da una tabella, nessun&#39;altra tabella che condivide la stessa sequenza avrà un record con quell&#39;id &#39;X&#39;. **XtkNewId** è la sequenza condivisa predefinita disponibile in Adobe Campaign.
* **Dedicato**: una sola tabella sta raccogliendo i relativi ID dalla sequenza. Il nome della sequenza in genere contiene il nome della tabella.

La sequenza è un valore intero a 32 bit, con un numero massimo finito di valori disponibili: 2,14 miliardi. Una volta raggiunto il valore massimo, la sequenza torna a 0 per riciclare gli ID. Se i vecchi dati non sono stati eliminati, il risultato sarà una violazione chiave univoca, che diventa un blocco per lo stato e l&#39;utilizzo della piattaforma. Adobe Campaign non sarebbe in grado di inviare comunicazioni (quando ha un impatto sulla tabella del registro di consegna) e le prestazioni sarebbero fortemente influenzate.

Di conseguenza, un cliente che invia 6 miliardi di e-mail ogni anno con un periodo di conservazione di 180 giorni per i propri registri avrebbe esaurito gli ID in 4 mesi. Per evitare una simile situazione, accertatevi di avere le impostazioni di rimozione in base ai volumi. Per ulteriori informazioni, consulta [questa sezione](#data-retention).

Quando viene creata una tabella personalizzata in Adobe Campaign con una chiave primaria come autoPK, una sequenza dedicata personalizzata deve essere sistematicamente associata a tale tabella.

Per impostazione predefinita, una sequenza personalizzata avrà valori compresi tra +1.000 e +2.1BB. Tecnicamente, è possibile ottenere una gamma completa di 4BB abilitando ID negativi. Questo dovrebbe essere utilizzato con cura e un ID andrà perso quando si passa da numeri negativi a numeri positivi: il record 0 viene in genere ignorato da Adobe Campaign Classic nelle query SQL generate.

**Argomenti correlati:**
* Per ulteriori informazioni sulla funzione di generazione **automatica della** sequenza, consultate questo [documento](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html).
* Per ulteriori informazioni sull&#39;esaurimento delle sequenze, guardate questo [video](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Indici {#indexes}

Gli indici sono essenziali per le prestazioni. Quando si dichiara una chiave nello schema, Adobe creerà automaticamente un indice sui campi della chiave. È inoltre possibile dichiarare altri indici per le query che non utilizzano la chiave.

Adobe consiglia di definire indici aggiuntivi in quanto potrebbero migliorare le prestazioni.

Tenete tuttavia presente quanto segue:

* L&#39;utilizzo dell&#39;indice è associato al pattern di accesso. L&#39;ottimizzazione dell&#39;indicizzazione è spesso una parte chiave della progettazione del database e deve essere gestita da esperti. L&#39;aggiunta di indici è spesso un flusso di lavoro iterativo associato alla manutenzione del database. Viene eseguito nel tempo, passo dopo passo, per risolvere i problemi di prestazioni quando si verifica.
* Gli indici aumentano la dimensione complessiva della tabella (per memorizzare l&#39;indice stesso).
* L&#39;aggiunta di un indice sulle colonne può migliorare le prestazioni dell&#39;accesso in lettura dei dati (SELECT), ma può diminuire le prestazioni dell&#39;accesso in scrittura dei dati (UPDATE).
* Poiché questo influisce sulle prestazioni durante l&#39;inserimento dei dati, gli indici devono essere limitati in dimensione e numero.
* Non aggiungere indici se non necessario. Accertatevi che sia necessario e che aumenti le prestazioni complessive delle query (test e learn).
* In genere, un indice è efficiente se si è certi che le query non restituiranno più del 10% dei record.
* Selezionare attentamente gli indici da definire.
* Non rimuovere indici nativi dalle tabelle pronte all&#39;uso.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

## Collegamenti e cardinalità {#links-and-cardinality}

### Collegamenti {#links}

Attenzione all&#39;integrità &quot;propria&quot; sui grandi tavoli. L&#39;eliminazione di record con tabelle ampie con integrità &quot;propria&quot; può arrestare l&#39;istanza. La tabella è bloccata e le eliminazioni vengono effettuate una per una. Quindi è meglio utilizzare l&#39;integrità &quot;neutra&quot; sui tavoli secondari con grandi volumi.

La dichiarazione di un collegamento come join esterno non è valida per le prestazioni. Il record id zero emula la funzionalità di join esterno. Non è necessario dichiarare giunti esterni se il collegamento utilizza l&#39;autopsia.

Sebbene sia possibile unire qualsiasi tabella in un flusso di lavoro, Adobe consiglia di definire collegamenti comuni tra le risorse direttamente nella definizione della struttura dati.

Il collegamento deve essere definito in linea con i dati effettivi nelle tabelle. Una definizione errata potrebbe avere un impatto sui dati recuperati tramite collegamenti, ad esempio la duplicazione inattesa di record.

Denominate il collegamento in modo coerente con il nome della tabella: il nome del collegamento deve essere utile per comprendere la tabella lontana.

Non assegnate un nome a un collegamento con &quot;id&quot; come suffisso. Ad esempio, denominatelo &quot;transaction&quot; anziché &quot;transactionId&quot;.

Per impostazione predefinita, Adobe Campaign crea un collegamento utilizzando la chiave primaria della tabella esterna. Per maggiore chiarezza, è preferibile definire esplicitamente il join nella definizione del collegamento.

Un indice verrà aggiunto agli attributi utilizzati in un collegamento.

I collegamenti creati e modificati per ultimo sono presenti in molte tabelle. È possibile disattivare l&#39;indice utilizzando l&#39;attributo noDbIndex sul collegamento, se queste informazioni non vengono utilizzate dall&#39;azienda.

### Cardinalità {#cardinality}

Quando progettate un collegamento, accertatevi che il record di destinazione sia univoco quando è stata dichiarata una relazione 1-1. In caso contrario, il join potrebbe restituire più record quando ne è previsto solo uno. Ciò genera errori durante la preparazione della consegna quando &quot;la query restituisce più righe del previsto&quot;. Impostate il nome del collegamento con lo stesso nome dello schema di destinazione.

Definire un collegamento con una cardinalità (1-N) nello schema sul lato (1). Ad esempio, la transazione destinatario relazione (1) - (N) deve essere definita nello schema della transazione.

Nota: per impostazione predefinita, la cardinalità inversa di un collegamento è (N). È possibile definire un collegamento (1-1) aggiungendo l&#39;attributo revCardinality=&#39;single&#39; alla definizione del collegamento.

Se il collegamento inverso non deve essere visibile all&#39;utente, è possibile nasconderlo con la definizione del collegamento revLink=&#39;_NONE_&#39;. Un buon esempio per questo è definire un collegamento tra il destinatario e l&#39;ultima transazione completata, ad esempio. Devi solo visualizzare il collegamento dal destinatario all&#39;ultima transazione e non è necessario alcun collegamento inverso per essere visibile dalla tabella delle transazioni.

I collegamenti che eseguono un join esterno (1-0.1) devono essere utilizzati con attenzione in quanto influiranno sulle prestazioni del sistema.

## Conservazione dei dati - Pulizia ed eliminazione {#data-retention}

Adobe Campaign non è né un data warehouse né uno strumento di reporting. Pertanto, per garantire buone prestazioni della soluzione Adobe Campaign, la crescita del database dovrebbe rimanere sotto controllo. A tal fine, seguire alcune delle best practice riportate di seguito può essere di aiuto.

Per impostazione predefinita, i registri di consegna e tracciamento di Adobe Campaign hanno una durata di conservazione di 180 giorni. Viene eseguito un processo di pulizia per rimuovere eventuali file di registro precedenti.

* Se si desidera mantenere i log più lunghi, questa decisione deve essere presa attentamente in base alle dimensioni del database e al volume dei messaggi inviati. Come promemoria, la sequenza Adobe Campaign è un numero intero a 32 bit.
* Si raccomanda di non avere più di 1 miliardo di record alla volta in queste tabelle (circa il 50% dei 2,14 miliardi di ID disponibili) per limitare i rischi di consumo di tutti gli ID disponibili. Per ridurre la durata di conservazione al di sotto dei 180 giorni, è necessario che alcuni clienti utilizzino questa funzione.

>[!IMPORTANT]
>
>Le tabelle personalizzate non vengono eliminate con il processo di pulizia standard. Anche se questo potrebbe non essere necessario al primo giorno, non dimenticare di creare un processo di eliminazione per le tabelle personalizzate, in quanto ciò potrebbe causare problemi di prestazioni.

Ci sono alcune soluzioni per ridurre al minimo la necessità di record in Adobe Campaign:
* Esporta i dati in un data warehouse esterno ad Adobe Campaign.
* Genera valori aggregati che utilizzeranno meno spazio pur essendo sufficienti per le tue prassi di marketing. Ad esempio, non hai bisogno dell&#39;intera cronologia delle transazioni cliente in Adobe Campaign per tenere traccia degli ultimi acquisti.

## Prestazioni {#performance}

Per garantire prestazioni migliori in qualsiasi momento, segui le best practice riportate di seguito.

### Raccomandazioni generali {#general-recommendations}

* Evitare di utilizzare operazioni come &quot;CONTAINS&quot; nelle query. Se sai cosa ci si aspetta e vuoi filtrare, applica la stessa condizione con &quot;EQUAL TO&quot; o altri operatori filtro specifici.
* Evitare di unirsi a campi non indicizzati durante la creazione di dati nei flussi di lavoro.
* Cercate di fare in modo che processi come l&#39;importazione e l&#39;esportazione avvengano al di fuori delle ore lavorative.
* Assicurarsi che ci sia un programma per tutte le attività giornaliere e attenersi al programma.
* Se uno o pochi processi giornalieri non riescono e se è obbligatorio eseguirli nello stesso giorno, assicurarsi che non siano in esecuzione processi in conflitto quando il processo manuale viene avviato, in quanto ciò potrebbe influire sulle prestazioni del sistema.
* Accertatevi che nessuna delle campagne giornaliere venga eseguita durante il processo di importazione o quando viene eseguito un processo manuale.
* Utilizzare una o più tabelle di riferimento anziché duplicare un campo in ogni riga. Quando si utilizzano coppie chiave/valore, è preferibile scegliere una chiave numerica.
* Una stringa breve rimane accettabile. Nel caso in cui le tabelle di riferimento siano già presenti in un sistema esterno, il riutilizzo dello stesso agevolerà l&#39;integrazione dei dati con Adobe Campaign.

### Relazioni uno-a-molti {#one-to-many-relationships}

* La progettazione dei dati influisce su usabilità e funzionalità. Se si progetta il modello dati con molte relazioni uno-a-molti, diventa più difficile per gli utenti costruire logiche significative nell&#39;applicazione. La logica del filtro uno-molti può essere difficile per gli addetti al marketing non tecnico da costruire e comprendere correttamente.
* È utile avere tutti i campi essenziali in una tabella, perché semplifica la creazione di query da parte degli utenti. A volte è anche utile che le prestazioni di alcuni campi vengano duplicate tra le tabelle, se è possibile evitare un join.
* Alcune funzionalità integrate non saranno in grado di fare riferimento a relazioni uno-molti, ad esempio, formula di ponderazione dell&#39;offerta e consegne.

### Tabelle grandi {#large-tables}

Di seguito sono riportate alcune best practice da seguire per la progettazione del modello dati utilizzando tabelle di grandi dimensioni e join complessi.

* Quando utilizzi tabelle di destinatari personalizzate aggiuntive, accertati di disporre di una tabella di registro dedicata per ogni mapping di consegna.
* Ridurre il numero di colonne, in particolare identificando quelle non utilizzate.
* Ottimizzate le relazioni del modello dati evitando join complessi, ad esempio join su più condizioni e/o più colonne.
* Per le chiavi di join, utilizzare sempre dati numerici anziché stringhe di caratteri.
* Ridurre al massimo la profondità di conservazione del registro. Se si desidera una cronologia più approfondita, è possibile aggregare il calcolo e/o gestire tabelle di registro personalizzate per memorizzare una cronologia più grande.

Per best practice dettagliate su come ottimizzare la progettazione del database per volumi più grandi, consulta [Campaign Classic Data Model Best practice](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).