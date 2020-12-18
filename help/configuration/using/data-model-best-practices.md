---
solution: Campaign Classic
product: campaign
title: Best practice per i modelli di dati
description: Scopri come utilizzare il modello dati Campaign Classic
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '4014'
ht-degree: 1%

---


# Best practice per i modelli di dati{#data-model-best-practices}

In questo documento vengono delineate le raccomandazioni chiave durante la progettazione del modello dati Adobe Campaign .

Per una migliore comprensione delle tabelle integrate di Campaign e della loro interazione, fare riferimento alla sezione [Campaign Classic data model](../../configuration/using/about-data-model.md).

Leggi [questa documentazione](../../configuration/using/about-schema-reference.md) per iniziare a usare gli schemi delle campagne. Scoprite come configurare gli schemi di estensione per estendere il modello di dati concettuali del database Adobe Campaign  in [questo documento](../../configuration/using/about-schema-edition.md).

## Panoramica {#overview}

 sistema Adobe Campaign è estremamente flessibile e può essere esteso oltre l&#39;implementazione iniziale. Tuttavia, mentre le possibilità sono infinite, è fondamentale prendere decisioni sagge e creare solide basi per iniziare a progettare il modello dati.

Questo documento contiene esempi di utilizzo comuni e procedure ottimali per apprendere come architettare correttamente lo strumento Adobe Campaign .

## Architettura del modello dati {#data-model-architecture}

 Adobe Campaign Standard è un potente sistema di gestione delle campagne multicanale che consente di allineare le strategie online e offline per creare esperienze cliente personalizzate.

### Approccio incentrato sul cliente {#customer-centric-approach}

Mentre la maggior parte dei provider di servizi e-mail comunica ai clienti tramite un approccio incentrato sugli elenchi,  Adobe Campaign si affida a un database relazionale per sfruttare una visione più ampia dei clienti e dei loro attributi.

Questo approccio incentrato sul cliente è riportato nel grafico seguente. La tabella **Recipient** in grigio rappresenta la tabella cliente principale intorno alla quale viene creato tutto:

![](assets/customer-centric-data-model.png)

Per accedere alla descrizione di ciascuna tabella, passare a **[!UICONTROL Admin > Configuration > Data schemas]**, selezionare una risorsa dall&#39;elenco e fare clic sulla scheda **[!UICONTROL Documentation]**.

Il modello dati predefinito  Adobe Campaign è presentato in [questo documento](../../configuration/using/data-model-description.md).

>[!NOTE]
>
>Adobe Campaign Classic consente di creare una tabella cliente personalizzata. Tuttavia, nella maggior parte dei casi, si consiglia di utilizzare la [tabella destinatari](../../configuration/using/about-data-model.md#default-recipient-table) standard che dispone già di tabelle e funzionalità aggiuntive preconfigurate.

### Dati per  Adobe Campaign {#data-for-campaign}

Quali dati devono essere inviati a  Adobe Campaign? È fondamentale determinare i dati richiesti per le attività di marketing.

>[!NOTE]
>
> Adobe Campaign non è né un data warehouse né uno strumento di reporting. Pertanto, non cercare di importare tutti i possibili clienti e le relative informazioni in  Adobe Campaign, né di importare dati che verranno utilizzati solo per creare rapporti.

Per decidere se un attributo sarebbe necessario o meno in  Adobe Campaign, chiedetevi se rientrerebbe in una delle seguenti categorie:

* Attributo utilizzato per **segmentazione**
* Attributo utilizzato per **processi di gestione dei dati** (ad esempio, per il calcolo aggregato)
* Attributo utilizzato per **personalizzazione**

Se non si rientra in nessuno di questi, molto probabilmente non sarà necessario questo attributo in  Adobe Campaign.

### Scelta dei tipi di dati {#data-types}

Per garantire una buona architettura e prestazioni del sistema, segui le best practice riportate di seguito per configurare i dati in  Adobe Campaign.

* Una tabella di grandi dimensioni deve avere principalmente campi numerici e contenere collegamenti alle tabelle di riferimento (quando si utilizza un elenco di valori).
* L&#39;attributo **expr** consente di definire un attributo di schema come campo calcolato anziché come valore di set fisico in una tabella. In questo modo è possibile accedere alle informazioni in un formato diverso (ad esempio per l’età e la data di nascita) senza dover memorizzare entrambi i valori. Questo è un buon modo per evitare la duplicazione di campi. Ad esempio, la tabella Destinatario utilizza un&#39;espressione per il dominio, già presente nel campo e-mail.
* Tuttavia, quando il calcolo dell&#39;espressione è complesso, si consiglia di non utilizzare l&#39;attributo **expr** come calcolo al volo potrebbe influire sulle prestazioni delle query.
* Il tipo **XML** è un modo corretto per evitare di creare troppi campi. ma occupa anche spazio su disco in quanto utilizza una colonna CLOB nel database. Può inoltre causare query SQL complesse e avere un impatto sulle prestazioni.
* La lunghezza di un campo **stringa** deve essere sempre definita con la colonna. Per impostazione predefinita, la lunghezza massima in  Adobe Campaign è di 255, ma  Adobe consiglia di ridurre la lunghezza del campo se si è già certi che la dimensione non supererà una lunghezza inferiore.
* È accettabile avere un campo più breve in  Adobe Campaign rispetto a quello nel sistema di origine, se si è certi che la dimensione nel sistema di origine è stata sopravvalutata e non sarebbe stato raggiunto. Ciò potrebbe significare una stringa più corta o un numero intero più piccolo in  Adobe Campaign.

### Scelta dei campi {#choice-of-fields}

Un campo deve essere memorizzato in una tabella se ha uno scopo di targeting o personalizzazione. In altre parole, se un campo non viene utilizzato per inviare un&#39;e-mail personalizzata o come criterio in una query, occupa spazio su disco mentre è inutile.

Per le istanze ibride e locali, FDA (Federated Data Access, una funzione opzionale che consente di accedere ai dati esterni) copre la necessità di aggiungere un campo &quot;on-the-fly&quot; durante un processo della campagna. Non è necessario importare tutto se si dispone di FDA. Per ulteriori informazioni, vedere [Informazioni su Federated Data Access](../../installation/using/about-fda.md).

### Scelta di tasti {#choice-of-keys}

Oltre al **autopk** definito per impostazione predefinita nella maggior parte delle tabelle, è consigliabile aggiungere alcune chiavi logiche o aziendali (numero di conto, numero di cliente e così via). Può essere utilizzato successivamente per le importazioni/riconciliazione o per i pacchetti di dati. Per ulteriori informazioni, vedere [Identificatori](#identifiers).

Le chiavi efficienti sono essenziali per le prestazioni. I tipi di dati numerici devono sempre essere preferiti come chiavi per le tabelle.

Per il database SQLServer, è possibile utilizzare &quot;indice cluster&quot; se sono necessarie prestazioni. Poiché  Adobe non è in grado di gestire questo problema, è necessario crearlo in SQL.

### Spazi da tavolo dedicati {#dedicated-tablespaces}

L&#39;attributo tablespace nello schema consente di specificare una tablespace dedicata per una tabella.

La procedura guidata di installazione consente di memorizzare gli oggetti per tipo (dati, temporanei e indice).

Le tablespace dedicate sono migliori per il partizionamento, le regole di sicurezza e consentono un&#39;amministrazione fluida e flessibile, una migliore ottimizzazione e prestazioni.

## Identificatori {#identifiers}

 risorse Adobe Campaign hanno tre identificatori ed è possibile aggiungere un identificatore aggiuntivo.

La tabella seguente descrive questi identificatori e la loro funzione.

| Identificatore | Descrizione | Best practice |
|--- |--- |--- |
| Id | <ul><li>L’ID è la chiave primaria fisica di una tabella Adobe Campaign . Per le tabelle pronte all&#39;uso, si tratta di un numero generato a 32 bit da una sequenza</li><li>Questo identificatore è in genere univoco per una specifica istanza di Adobe Campaign . </li><li>Un ID generato automaticamente può essere visibile in una definizione dello schema. Cercare l&#39;attributo *autopk=&quot;true&quot;*.</li></ul> | <ul><li>Gli identificatori generati automaticamente non devono essere utilizzati come riferimento in un flusso di lavoro o in una definizione di pacchetto.</li><li>Non si deve presumere che l&#39;ID sia sempre un numero crescente.</li><li>L’ID in una tabella out-of-the-box è un numero a 32 bit e questo tipo non deve essere modificato. Questo numero è tratto da una &quot;sequenza&quot; coperta nella sezione con lo stesso nome.</li></ul> |
| Nome (o nome interno) | <ul><li>Queste informazioni sono un identificatore univoco di un record in una tabella. Questo valore può essere aggiornato manualmente, in genere con un nome generato.</li><li>Questo identificatore mantiene il suo valore quando viene distribuito in un&#39;altra istanza di  Adobe Campaign e non deve essere vuoto.</li></ul> | <ul><li>Rinominare il nome del record generato da  Adobe Campaign se l&#39;oggetto è destinato alla distribuzione da un ambiente a un altro.</li><li>Quando un oggetto ha un attributo spazio nomi (*schema* ad esempio), lo spazio nomi comune verrà utilizzato in tutti gli oggetti personalizzati creati. Alcuni spazi dei nomi riservati non devono essere utilizzati: *nms*, *xtk*.</li><li>Se un oggetto non dispone di uno spazio dei nomi ( ad esempio *workflow* o *consegna*), questa nozione dello spazio dei nomi viene aggiunta come prefisso di un oggetto nome interno: *namespaceMyObjectName*.</li><li>Non utilizzate caratteri speciali come lo spazio &quot;&quot;, la semicolona &quot;:&quot; o il trattino &quot;-&quot;. Tutti questi caratteri vengono sostituiti da un carattere di sottolineatura &quot;_&quot; (caratteri consentiti). Ad esempio, &quot;abc-def&quot; e &quot;abc:def&quot; vengono memorizzati come &quot;abc_def&quot; e si sovrascrivono a vicenda.</li></ul> |
| Etichetta | <ul><li>L&#39;etichetta è l&#39;identificatore aziendale di un oggetto o di un record in  Adobe Campaign.</li><li>Questo oggetto consente spazi e caratteri speciali.</li><li>Non garantisce l&#39;unicità di un documento.</li></ul> | <ul><li>È consigliabile determinare una struttura per le etichette degli oggetti.</li><li>Si tratta della soluzione più semplice da utilizzare per identificare un record o un oggetto per un utente Adobe Campaign .</li></ul> |

## Tasti interni personalizzati {#custom-internal-keys}

Le chiavi primarie sono necessarie per ogni tabella creata in  Adobe Campaign.

La maggior parte delle organizzazioni sta importando record da sistemi esterni. Anche se la chiave fisica della tabella Recipient è l&#39;attributo &quot;id&quot;, è possibile determinare anche una chiave personalizzata.

Questa chiave personalizzata è la chiave primaria del record effettiva nel sistema esterno di alimentazione  Adobe Campaign.

Quando una tabella out-of-the-box ha sia un pilota automatico che una chiave interna, la chiave interna sarà impostata come un indice univoco nella tabella del database fisico.

Quando si crea una tabella personalizzata, sono disponibili due opzioni:
* Combinazione di chiave generata automaticamente (id) e chiave interna (personalizzata). Questa opzione è interessante se la chiave di sistema è una chiave composita o non un numero intero. Gli interi forniranno prestazioni più elevate nelle grandi tabelle e uniranno ad altre tabelle.
* Utilizzo della chiave primaria come chiave primaria del sistema esterno. Questa soluzione è generalmente preferita in quanto semplifica l&#39;approccio all&#39;importazione e all&#39;esportazione dei dati, con una chiave coerente tra i diversi sistemi. L&#39;opzione Autopk deve essere disabilitata se la chiave è denominata &quot;id&quot; e deve essere compilata con valori esterni (non generato automaticamente).

>[!IMPORTANT]
>
>Un&#39;autopsia non deve essere utilizzata come riferimento nei flussi di lavoro.

## Sequenze {#sequences}

 chiave primaria Adobe Campaign è un ID generato automaticamente per tutte le tabelle pronte all&#39;uso e può essere lo stesso per le tabelle personalizzate. Per ulteriori informazioni, consulta [questa sezione](#identifiers).

Questo valore viene ricavato da una **sequenza**, ovvero da un oggetto di database utilizzato per generare una sequenza numerica.

Esistono due tipi di sequenze:
* **Condiviso**: più di una tabella sceglierebbe il proprio ID dalla stessa sequenza. Significa che se un id &#39;X&#39; viene utilizzato da una tabella, nessun&#39;altra tabella che condivide la stessa sequenza avrà un record con quell&#39;id &#39;X&#39;. **** XtkNewIdis la sequenza condivisa predefinita disponibile in  Adobe Campaign.
* **Dedicato**: una sola tabella sta raccogliendo i relativi ID dalla sequenza. Il nome della sequenza in genere contiene il nome della tabella.

>[!IMPORTANT]
>
>La sequenza è un valore intero a 32 bit, con un numero massimo finito di valori disponibili: 2,14 miliardi. Una volta raggiunto il valore massimo, la sequenza torna a 0 per riciclare gli ID.
>
>Se i vecchi dati non sono stati eliminati, il risultato sarà una violazione chiave univoca, che diventa un blocco per lo stato e l&#39;utilizzo della piattaforma.  Adobe Campaign non sarebbe in grado di inviare comunicazioni (quando ha un impatto sulla tabella di log di consegna) e le prestazioni sarebbero fortemente influenzate.

Di conseguenza, un cliente che invia 6 miliardi di e-mail ogni anno con un periodo di conservazione di 180 giorni per i propri registri avrebbe esaurito gli ID in 4 mesi. Per evitare una simile situazione, accertatevi di avere le impostazioni di rimozione in base ai volumi. Per ulteriori informazioni, consulta [questa sezione](#data-retention).

Quando viene creata una tabella personalizzata in  Adobe Campaign con una chiave primaria come autoPK, una sequenza dedicata personalizzata deve essere sistematicamente associata a tale tabella.

Per impostazione predefinita, una sequenza personalizzata avrà valori compresi tra +1.000 e +2.1BB. Tecnicamente, è possibile ottenere una gamma completa di 4BB abilitando ID negativi. Questo dovrebbe essere utilizzato con cura e un ID andrà perso quando si passa da numeri negativi a numeri positivi: il record 0 viene in genere ignorato da Adobe Campaign Classic nelle query SQL generate.

**Argomenti correlati:**
* Per ulteriori informazioni sulla funzione di generazione automatica della sequenza **Sequenza**, vedere [questo documento](https://helpx.adobe.com/it/campaign/kb/sequence_auto_generation.html).
* Per ulteriori informazioni sull&#39;esaurimento delle sequenze, guardate [questo video](https://helpx.adobe.com/customer-care-office-hours/campaign/sequences-exhaustion-campaign-classic.html).

## Indici {#indexes}

Gli indici sono essenziali per le prestazioni. Quando si dichiara una chiave nello schema,  Adobe crea automaticamente un indice sui campi della chiave. È inoltre possibile dichiarare altri indici per le query che non utilizzano la chiave.

 Adobe consiglia di definire indici aggiuntivi in quanto potrebbero migliorare le prestazioni.

Tuttavia, tenete presente quanto segue:

* L&#39;utilizzo dell&#39;indice è associato al pattern di accesso. L&#39;ottimizzazione dell&#39;indicizzazione è spesso una parte chiave della progettazione del database e deve essere gestita da esperti. L&#39;aggiunta di indici è spesso un flusso di lavoro iterativo associato alla manutenzione del database. Viene eseguito nel tempo, passo dopo passo, per risolvere i problemi di prestazioni quando si verifica.
* Gli indici aumentano la dimensione complessiva della tabella (per memorizzare l&#39;indice stesso).
* L&#39;aggiunta di un indice sulle colonne può migliorare le prestazioni dell&#39;accesso in lettura dei dati (SELECT), ma può diminuire le prestazioni dell&#39;accesso in scrittura dei dati (UPDATE).
* Poiché questo influisce sulle prestazioni durante l&#39;inserimento dei dati, gli indici devono essere limitati in dimensione e numero.
* Non aggiungere indici se non necessario. Accertatevi che sia necessario e che aumenti le prestazioni complessive delle query (test e learn).
* In genere, un indice è efficiente se si è certi che le query non restituiranno più del 10% dei record.
* Selezionare attentamente gli indici da definire.
* Non rimuovere indici nativi dalle tabelle pronte all&#39;uso.

<!--When you are performing an initial import with very high volumes of data insert in Adobe Campaign database, it is recommended to run that import without custom indexes at first. It will allow to accelerate the insertion process. Once you’ve completed this important import, it is possible to enable the index(es).-->

### Esempio

La gestione degli indici può diventare molto complessa, quindi è importante capire come funzionano. Per illustrare questa complessità, prendiamo un esempio di base, ad esempio la ricerca dei destinatari tramite filtro sul nome e il cognome. Per eseguire questa operazione:
1. Passate alla cartella in cui sono elencati tutti i destinatari presenti nel database. Per ulteriori informazioni, consulta [Gestione dei profili di ](../../platform/using/managing-profiles.md).
1. Fare clic con il pulsante destro del mouse sul campo **[!UICONTROL First name]**.
1. Seleziona **[!UICONTROL Filter on this field]**.

   ![](assets/data-model-index-example.png)

1. Ripetere questa operazione per il campo **[!UICONTROL Last name]**.

I due filtri corrispondenti vengono aggiunti nella parte superiore dello schermo.

![](assets/data-model-index-search.png)

Ora è possibile eseguire il filtraggio delle ricerche nei campi **[!UICONTROL First name]** e **[!UICONTROL Last name]** in base alle diverse condizioni del filtro.

Ora, per velocizzare la ricerca su questi filtri, è possibile aggiungere indici. Ma quali indici dovrebbero essere utilizzati?

>[!NOTE]
>
>Questo esempio si applica ai clienti ospitati che utilizzano un database PostgreSQL.

La tabella seguente mostra in quali casi i tre indici descritti di seguito vengono utilizzati o meno in base al pattern di accesso visualizzato nella prima colonna.

| Criteri di ricerca | Indice 1 (Nome + Cognome) | Indice 2 (solo nome) | Indice 3 (solo cognome) | Commenti |
|--- |--- |--- |--- |--- |
| Nome uguale a &quot;Johnny&quot; | Usato | Usato | Non utilizzato | Poiché il primo nome si trova nella prima posizione dell&#39;indice 1, verrà comunque utilizzato: non è necessario aggiungere un criterio per il cognome. |
| Il nome è uguale a &quot;Johnny&quot; E il cognome è uguale a &quot;Smith&quot; | Usato | Non utilizzato | Non utilizzato | Poiché entrambi gli attributi vengono ricercati nella stessa query, verrà utilizzato solo l&#39;indice che combina entrambi gli attributi. |
| Cognome uguale a &quot;Smith&quot; | Non utilizzato | Non utilizzato | Usato | Si tiene conto dell&#39;ordine degli attributi nell&#39;indice. Se l&#39;ordine non corrisponde, l&#39;indice potrebbe non essere utilizzato. |
| Il nome inizia con &quot;Joh&quot; | Usato | Usato | Non utilizzato | &quot;Ricerca a sinistra&quot; consente gli indici. |
| Il nome termina con &quot;nny&quot; | Non utilizzato | Non utilizzato | Non utilizzato | &quot;Right search&quot; disattiverà gli indici e verrà eseguita una scansione completa. Alcuni tipi di indice specifici potrebbero gestire questo caso di utilizzo, ma non sono disponibili per impostazione predefinita in  Adobe Campaign. |
| Il nome contiene &quot;John&quot; | Non utilizzato | Non utilizzato | Non utilizzato | Questa è una combinazione di ricerche &quot;a sinistra&quot; e &quot;a destra&quot;. A causa di quest&#39;ultimo, disabiliterà gli indici e verrà eseguita una scansione completa. |
| Nome uguale a &quot;john&quot; | Non utilizzato | Non utilizzato | Non utilizzato | Per gli indici viene fatta distinzione tra maiuscole e minuscole. Per evitare la distinzione tra maiuscole e minuscole, è necessario creare un indice specifico che includa una funzione SQL come &quot;high(firstname)&quot;. È necessario eseguire le stesse operazioni con altre trasformazioni di dati, ad esempio &quot;unaccentuate(firstname)&quot;. |

## Collegamenti e cardinalità {#links-and-cardinality}

### Collegamenti {#links}

Attenzione all&#39;integrità &quot;propria&quot; sui grandi tavoli. L&#39;eliminazione di record con tabelle ampie con integrità &quot;propria&quot; può arrestare l&#39;istanza. La tabella è bloccata e le eliminazioni vengono effettuate una per una. Quindi è meglio utilizzare l&#39;integrità &quot;neutra&quot; sui tavoli secondari che hanno grandi volumi.

La dichiarazione di un collegamento come join esterno non è valida per le prestazioni. Il record id zero emula la funzionalità di join esterno. Non è necessario dichiarare giunti esterni se il collegamento utilizza l&#39;autopsia.

Sebbene sia possibile unire qualsiasi tabella in un flusso di lavoro,  Adobe consiglia di definire collegamenti comuni tra le risorse direttamente nella definizione della struttura dati.

Il collegamento deve essere definito in linea con i dati effettivi nelle tabelle. Una definizione errata potrebbe avere un impatto sui dati recuperati tramite collegamenti, ad esempio la duplicazione inattesa di record.

Denominate il collegamento in modo coerente con il nome della tabella: il nome del collegamento deve essere utile per comprendere la tabella lontana.

Non assegnate un nome a un collegamento con &quot;id&quot; come suffisso. Ad esempio, denominatelo &quot;transaction&quot; anziché &quot;transactionId&quot;.

Per impostazione predefinita,  Adobe Campaign crea un collegamento utilizzando la chiave primaria della tabella esterna. Per maggiore chiarezza, è preferibile definire esplicitamente il join nella definizione del collegamento.

Un indice verrà aggiunto agli attributi utilizzati in un collegamento.

Il   i collegamenti creati da e modificati da ultimo sono presenti in molte tabelle. È possibile disattivare l&#39;indice utilizzando l&#39;attributo noDbIndex sul collegamento, se queste informazioni non vengono utilizzate dall&#39;azienda.

### Cardinalità {#cardinality}

Quando progettate un collegamento, accertatevi che il record di destinazione sia univoco quando è stata dichiarata una relazione 1-1. In caso contrario, il join potrebbe restituire più record quando ne è previsto solo uno. Ciò genera errori durante la preparazione della consegna quando &quot;la query restituisce più righe del previsto&quot;. Impostate il nome del collegamento con lo stesso nome dello schema di destinazione.

Definire un collegamento con una cardinalità (1-N) nello schema sul lato (1). Ad esempio, la transazione destinatario relazione (1) - (N) deve essere definita nello schema della transazione.

Nota: per impostazione predefinita, la cardinalità inversa di un collegamento è (N). È possibile definire un collegamento (1-1) aggiungendo l&#39;attributo revCardinality=&#39;single&#39; alla definizione del collegamento.

Se il collegamento inverso non deve essere visibile all&#39;utente, è possibile nasconderlo con la definizione del collegamento revLink=&#39;_NONE_&#39;. Un buon esempio per questo è definire un collegamento tra il destinatario e l&#39;ultima transazione completata, ad esempio. Devi solo visualizzare il collegamento dal destinatario all&#39;ultima transazione e non è necessario alcun collegamento inverso per essere visibile dalla tabella delle transazioni.

I collegamenti che eseguono un join esterno (1-0.1) devono essere utilizzati con attenzione in quanto influiranno sulle prestazioni del sistema.

## Conservazione dei dati - pulizia ed eliminazione {#data-retention}

 Adobe Campaign non è né un data warehouse né uno strumento di reporting. Pertanto, per garantire buone prestazioni della soluzione Adobe Campaign , la crescita del database dovrebbe rimanere sotto controllo. A tal fine, seguire alcune delle best practice riportate di seguito può essere di aiuto.

Per impostazione predefinita,  registri di consegna e tracciamento Adobe Campaign hanno una durata di conservazione di 180 giorni. Viene eseguito un processo di pulizia per rimuovere eventuali file di registro precedenti.

* Se si desidera mantenere i log più lunghi, questa decisione deve essere presa attentamente in base alle dimensioni del database e al volume dei messaggi inviati. Come promemoria,  sequenza Adobe Campaign è un numero intero a 32 bit.
* Si raccomanda di non avere più di 1 miliardo di record alla volta in queste tabelle (circa il 50% dei 2,14 miliardi di ID disponibili) per limitare i rischi di consumo di tutti gli ID disponibili. Per ridurre la durata di conservazione al di sotto dei 180 giorni, è necessario che alcuni clienti utilizzino questa funzione.

Ulteriori informazioni sulla conservazione dei dati sono disponibili in [Campaign Privacy and Security guidelines](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#consent).

Ulteriori informazioni sul flusso di lavoro di pulizia della base dati della campagna [in questa sezione](../../production/using/database-cleanup-workflow.md).

>[!IMPORTANT]
>
>Le tabelle personalizzate non vengono eliminate con il processo di pulizia standard. Anche se questo potrebbe non essere necessario al primo giorno, non dimenticare di creare un processo di eliminazione per le tabelle personalizzate, in quanto ciò potrebbe causare problemi di prestazioni.

Esistono alcune soluzioni per ridurre al minimo la necessità di record in  Adobe Campaign:
* Esportare i dati in un data warehouse all&#39;esterno di  Adobe Campaign.
* Genera valori aggregati che utilizzeranno meno spazio pur essendo sufficienti per le tue prassi di marketing. Ad esempio, non è necessario disporre dell&#39;intera cronologia delle transazioni cliente in  Adobe Campaign per tenere traccia degli ultimi acquisti.

È possibile dichiarare l&#39;attributo &quot;deleteStatus&quot; in uno schema. È più efficace contrassegnare il record come eliminato, quindi rimandare l&#39;eliminazione nell&#39;attività di pulizia.

## Prestazioni {#performance}

Per garantire prestazioni migliori in qualsiasi momento, segui le best practice riportate di seguito.

### Raccomandazioni generali {#general-recommendations}

* Evitare di utilizzare operazioni come &quot;CONTAINS&quot; nelle query. Se sai cosa ci si aspetta e vuoi filtrare, applica la stessa condizione con &quot;EQUAL TO&quot; o altri operatori filtro specifici.
* Evitare di unirsi a campi non indicizzati durante la creazione di dati nei flussi di lavoro.
* Cercate di assicurarsi che i processi come l&#39;importazione e l&#39;esportazione avvengano al di fuori dell&#39;orario di lavoro.
* Assicurarsi che ci sia un programma per tutte le attività giornaliere e attenersi al programma.
* Se uno o pochi processi giornalieri non riescono e se è obbligatorio eseguirli nello stesso giorno, assicurarsi che non siano in esecuzione processi in conflitto quando il processo manuale viene avviato, in quanto ciò potrebbe influire sulle prestazioni del sistema.
* Accertatevi che nessuna delle campagne giornaliere venga eseguita durante il processo di importazione o quando viene eseguito un processo manuale.
* Utilizzare una o più tabelle di riferimento anziché duplicare un campo in ogni riga. Quando si utilizzano coppie chiave/valore, è preferibile scegliere una chiave numerica.
* Una stringa breve rimane accettabile. Nel caso in cui le tabelle di riferimento siano già presenti in un sistema esterno, il riutilizzo dello stesso agevolerà l&#39;integrazione dei dati con  Adobe Campaign.

### Relazioni uno-a-molti {#one-to-many-relationships}

* La progettazione dei dati influisce su usabilità e funzionalità. Se si progetta il modello dati con molte relazioni uno-a-molti, diventa più difficile per gli utenti costruire logiche significative nell&#39;applicazione. La logica del filtro uno-molti può essere difficile per gli addetti al marketing non tecnico da costruire e comprendere correttamente.
* È utile avere tutti i campi essenziali in una tabella, perché semplifica la creazione di query da parte degli utenti. A volte è anche utile che le prestazioni di alcuni campi vengano duplicate tra le tabelle, se è possibile evitare un join.
* Alcune funzionalità integrate non saranno in grado di fare riferimento a relazioni uno-molti, ad esempio, formula di ponderazione dell&#39;offerta e consegne.

## Tabelle grandi {#large-tables}

 Adobe Campaign si basa su motori di database di terze parti. A seconda del provider, l&#39;ottimizzazione delle prestazioni per le tabelle più grandi potrebbe richiedere una progettazione specifica.

Di seguito sono riportate alcune best practice comuni da seguire per la progettazione del modello dati utilizzando tabelle di grandi dimensioni e join complessi.

* Quando utilizzi tabelle di destinatari personalizzate aggiuntive, accertati di disporre di una tabella di registro dedicata per ogni mapping di consegna.
* Ridurre il numero di colonne, in particolare identificando quelle non utilizzate.
* Ottimizzate le relazioni del modello dati evitando join complessi, ad esempio join su più condizioni e/o più colonne.
* Per le chiavi di join, utilizzare sempre dati numerici anziché stringhe di caratteri.
* Ridurre al massimo la profondità di conservazione del registro. Se si desidera una cronologia più approfondita, è possibile aggregare il calcolo e/o gestire tabelle di registro personalizzate per memorizzare una cronologia più grande.

### Dimensioni delle tabelle {#size-of-tables}

La dimensione della tabella è una combinazione del numero di record e del numero di colonne per record. Entrambi possono influire sulle prestazioni delle query.

* Una tabella **di piccole dimensioni** è simile alla tabella Consegna.
* Una tabella di **dimensioni medie** corrisponde alla dimensione della tabella Recipient. Ha un record per cliente.
* Una tabella di **grandi dimensioni** è simile alla tabella di registro di grandi dimensioni. Ha molti record per cliente.
Ad esempio, se il database contiene 10 milioni di destinatari, la tabella di registro Ampio contiene da 100 a 200 milioni di messaggi e la tabella Consegna contiene poche migliaia di record.

In PostgreSQL, una riga non deve superare gli 8 KB per evitare il meccanismo [TOAST](https://wiki.postgresql.org/wiki/TOAST). Pertanto, cercare di ridurre il più possibile il numero di colonne e la dimensione di ogni riga per mantenere le prestazioni ottimali del sistema (memoria e CPU).

Anche il numero di righe influisce sulle prestazioni. Il database Adobe Campaign  non è progettato per memorizzare i dati storici non utilizzati attivamente per il targeting o la personalizzazione; si tratta di un database operativo.

Per evitare problemi di prestazioni relativi al numero elevato di righe, conservare solo i record necessari nel database. Qualsiasi altro record deve essere esportato in un data warehouse di terze parti e rimosso dal database operativo Adobe Campaign .

Di seguito sono riportate alcune best practice relative alle dimensioni delle tabelle:

* Creare tabelle di grandi dimensioni con un numero inferiore di campi e più dati numerici.
* Non utilizzare un numero elevato di colonne (ad esempio: Int64) per memorizzare numeri piccoli come valori booleani.
* Rimuovere le colonne non utilizzate dalla definizione della tabella.
* Non conservare dati storici o inattivi nel database Adobe Campaign  (esportazione e pulizia).

Esempio:

![](assets/transaction-table-example.png)

In questo esempio:
* Le tabelle *Transaction* e *Transaction Item* sono grandi: più di 10 milioni.
* Le tabelle *Product* e *Store* sono più piccole: meno di 10.000.
* L&#39;etichetta e il riferimento del prodotto sono stati inseriti nella tabella *Product*.
* La tabella *Elemento transazione* ha solo un collegamento alla tabella *Prodotto*, che è numerica.

<!--For more detailed best practices on how to optimize the database design for larger volumes, see [Campaign Classic Data model Best practices](https://helpx.adobe.com/campaign/kb/acc-data-model-best-practices.html).-->