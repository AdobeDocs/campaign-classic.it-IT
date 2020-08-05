---
title: Best practice per la distribuzione delle campagne
seo-title: Best practice di distribuzione
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f599bc5483779ae62dd4d5eb1936cbc2760639b5
workflow-type: tm+mt
source-wordcount: '4348'
ht-degree: 3%

---


# Best practice di distribuzione {#delivery-best-practices}

## Ottimizzazione della distribuzione {#optimize-delivery}

Prima ancora di iniziare a creare le consegne, puoi intraprendere diverse azioni per proteggere e ottimizzare il processo di invio a monte.

La sezione seguente illustra le procedure ottimali e consigliate per una configurazione ottimale di  Adobe Campaign. Seguendo queste pratiche, si riducono al minimo i problemi che si possono affrontare a valle.

### Prestazioni della piattaforma

Diversi fattori possono influire direttamente sulle prestazioni del server e rallentare la piattaforma:

* Numero e tipo di elementi di personalizzazione: la personalizzazione nelle e-mail estrae i dati dal database per ciascun destinatario. Se sono presenti molti elementi di personalizzazione, questo aumenta la quantità di dati necessari per preparare la consegna.  Ulteriori informazioni sulla personalizzazione in [questa sezione](../../delivery/using/about-personalization.md)

* Caricamento del server: quando il server di marketing gestisce contemporaneamente diverse attività, può rallentare le prestazioni. Il server di marketing deve coordinare tutti i dati in entrata e in uscita per tutte le consegne, per garantire che i dati siano corretti e puntuali.

   **SUGGERIMENTO** : per evitare questo problema, coordinare la programmazione delle consegne con gli altri membri del team al fine di garantire le migliori prestazioni.

* Esecuzione del flusso di lavoro: il monitoraggio dei flussi di lavoro è essenziale per evitare problemi di prestazioni della piattaforma. Seguire le linee guida elencate [in questo documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* In qualità di cliente ospitato, potete sfruttare le funzionalità [del Pannello di controllo](https://docs.adobe.com/content/help/en/control-panel/using/discover-control-panel/key-features.html) campagna per monitorare la vostra piattaforma, utilizzando le funzionalità di monitoraggio [delle](https://docs.adobe.com/content/help/en/control-panel/using/performance-monitoring/about-performance-monitoring.html) prestazioni.

### Verifica della configurazione di rete {#network-config}

Per ottimizzare la distribuzione quando si gestiscono e-mail in grandi volumi ed evitare errori per uno spammer, assicurarsi di disporre di una configurazione di rete legittima che non tenti di nascondere l&#39;identità del server.

**Suggerimento**:  Utilizza un indirizzo mittente trasparente corrispondente al sito Web del tuo marchio. Ad esempio, la società TravelAgency gestisce la catena alberghiera di Valentino. Possiede il dominio valentino.com per il suo sito web. Per promuovere il Valentino hotel a Parigi, utilizza il sottodominio paris.valentino.com. Pertanto, un indirizzo mittente rilevante può essere hotel@paris.valentino.com.

### Gestione della distribuzione {#deliverability-management}

Per raggiungere la casella in entrata dei destinatari senza rimbalzare o contrassegnare come spam, è necessario migliorare il tasso di recapito dei messaggi.

* Che cos&#39;è l&#39;erogabilità?

   * Si riferisce ai fattori di un&#39;e-mail che ne determinano la capacità di essere accettata dal server del destinatario. I provider di servizi Internet (Internet Service Provider) escludono i messaggi e-mail che identificano come SPAM o impediscono il download di immagini. Se determinano che un determinato dominio sta inviando troppe e-mail, verrà impostato un limite al numero di e-mail che verranno accettate da quel mittente.

   * Quando controlli la tua e-mail per verificare la recapito, vuoi concentrarti su quattro categorie principali: qualità dei dati, messaggi e contenuti, infrastruttura di invio e reputazione. Per informazioni più approfondite sull&#39;argomento, consulta [questa sezione](../../delivery/using/about-deliverability.md).

* Applicate le raccomandazioni dettagliate [in questo documento](../../delivery/using/deliverability-key-points.md).

* Contattate il rappresentante del Adobe  per assistenza.

### Gestione della quarantena {#quarantine-management}

È nel vostro interesse mantenere buoni processi di gestione della quarantena.

Quando iniziate a inviare e-mail su una nuova piattaforma, potete utilizzare un elenco di indirizzi non completi. Se si inviano a indirizzi non validi o a indirizzi per le chat (le caselle di posta solo create per gli spammers ingannevoli), questo inizierà a ridurre la reputazione della piattaforma. Una buona gestione della quarantena aiuta a: mantenere la qualità dell&#39;indirizzo, evitare  elenco Bloccati da parte dei provider di accesso a Internet e ridurre il tasso di errore, velocizzare le consegne e la velocità di trasmissione.

**Suggerimenti**

* Se si dispone di un elenco di indirizzi non validi,  Adobe consiglia di importarli nella tabella di quarantena, tramite **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* I destinatari i cui indirizzi sono posti in quarantena sono esclusi per impostazione predefinita durante l&#39;analisi del recapito: non sono mirati. In questo modo le consegne sono più rapide, poiché il tasso di errore ha un effetto significativo sulla velocità di consegna. Un indirizzo e-mail può essere messo in quarantena, ad esempio se la casella in entrata è piena o se l’indirizzo non esiste. [Ulteriori informazioni](#identifying-quarantined-addresses-for-a-delivery)

*  Adobe Campaign gestisce gli indirizzi errati in base al tipo di errore restituito. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/understanding-quarantine-management.md).


* Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena consente quindi di evitare di essere aggiunta a un elenco Bloccati  da parte di questi fornitori.

* La gestione delle scorte contribuirà anche a ridurre i costi di invio di SMS escludendo numeri di telefono errati dalle consegne.

### Doppio meccanismo di consenso {#double-opt-in}

Per evitare di inviare messaggi a indirizzi non validi, limitare le comunicazioni non corrette e migliorare la reputazione del mittente,  Adobe consiglia di implementare un meccanismo di doppio consenso per la conferma post-iscrizione. Questo aiuta a garantire che il destinatario si sia iscritto intenzionalmente.

I dettagli per l&#39;attuazione di questo meccanismo sono descritti in [questa sezione](../../web/using/use-cases--web-forms.md).

## Utilizzare i modelli {#use-templates}

I modelli di distribuzione consentono una maggiore efficienza fornendo scenari pronti per la maggior parte dei tipi di attività più comuni. Grazie ai modelli, gli esperti di marketing possono distribuire nuove campagne con una personalizzazione minima in tempi più brevi.

Ulteriori informazioni sui modelli di consegna in [questa sezione](../../delivery/using/creating-a-delivery-template.md).

### Guida introduttiva ai modelli di distribuzione {#gs-templates}

Un modello [di](../../delivery/using/creating-a-delivery-template.md) consegna consente di definire una volta un insieme di proprietà tecniche e funzionali in base alle esigenze e che possono essere riutilizzate per le consegne future. È quindi possibile risparmiare tempo e standardizzare le consegne quando necessario.

Quando gestite diversi marchi in  Adobe Campaign,  Adobe consiglia di avere un sottodominio per marchio. Ad esempio, una banca può avere diversi sottodomini corrispondenti a ciascuna delle sue agenzie regionali. Se una banca possiede il dominio bluebank.com, i relativi sottodomini possono essere @ny.bluebank.com, @ma.bluebank.com, @ca.bluebank.com, ecc. La possibilità di disporre di un modello di consegna per sottodominio consente di utilizzare sempre i parametri preconfigurati corretti per ogni marchio, evitando errori e risparmiando tempo.

**Suggerimento**:  Per evitare errori di configurazione in Campaign Standard, è consigliabile duplicare un modello nativo e modificarne le proprietà anziché creare un nuovo modello.

**Configurare gli indirizzi**

* L&#39;indirizzo del mittente è obbligatorio per consentire l&#39;invio di un&#39;e-mail.

* Alcuni ISP (provider di servizi Internet) controllano la validità dell&#39;indirizzo del mittente prima di accettare i messaggi.

* Un indirizzo con formato non corretto potrebbe essere rifiutato dal server ricevente. Devi accertarti che sia specificato l&#39;indirizzo corretto.

* L&#39;indirizzo deve identificare esplicitamente il mittente. Il dominio deve essere di proprietà e registrato del mittente.

*  Adobe consiglia di creare account e-mail corrispondenti agli indirizzi specificati per le consegne e le risposte. Consultate l’amministratore del sistema di messaggistica.

Per configurare gli indirizzi nell&#39;interfaccia di Campaign, effettua le seguenti operazioni:

1. Nel modello [di](../../delivery/using/creating-a-delivery-template.md)consegna, fate clic sul **[!UICONTROL From]** collegamento. Nella **[!UICONTROL Email header parameters]** finestra, compila i campi seguenti:

   ![](assets/d_best_practices_email_header.png)

1. Nel **[!UICONTROL Sender address]** campo, accertatevi che il dominio indirizzo sia lo stesso del sottodominio delegato al Adobe . È possibile modificare la parte che precede &#39;@&#39; ma non l&#39;indirizzo del dominio.

1. Nel **[!UICONTROL From]** campo, utilizzare un nome facilmente identificabile dai destinatari, come il nome del marchio, per aumentare il tasso di apertura delle consegne. Per migliorare ulteriormente l&#39;esperienza del destinatario, è possibile aggiungere il nome di una persona, ad esempio &quot;Emma da Megastore&quot;.

1. Nei **[!UICONTROL Reply address text]** campi, l&#39;indirizzo del mittente viene utilizzato per impostazione predefinita per le risposte. Tuttavia,  Adobe consiglia di utilizzare un indirizzo reale esistente, come l&#39;assistenza clienti del marchio. In questo caso, se un destinatario invia una risposta, l&#39;assistenza clienti sarà in grado di gestirla.

**Impostazione di un gruppo di controllo**

Una volta inviata la consegna, potete confrontare il comportamento dei destinatari esclusi con quello dei destinatari che hanno ricevuto la consegna. Potete quindi misurare l&#39;efficienza delle campagne. Ulteriori informazioni sui gruppi di controllo [in questa sezione](../../campaign/using/marketing-campaign-deliveries.md#defining-a-control-group).

Per impostare un gruppo di controllo, fare clic sul **[!UICONTROL To]** collegamento. Nella **[!UICONTROL Select target]** finestra, selezionare la **[!UICONTROL Control group]** scheda. Potete estrarre una parte della destinazione, ad esempio un campione casuale del 5%.

![](assets/d_best_practices_control_group.png)

**Utilizzare le tipologie per applicare filtri o regole di controllo**

Una tipologia contiene le regole di controllo applicate durante la fase di analisi, prima di inviare qualsiasi messaggio.

Nella **[!UICONTROL Typology]** scheda delle proprietà del modello, modificare la tipologia predefinita in base alle esigenze.

Ad esempio, per controllare meglio il traffico in uscita, potete definire gli indirizzi IP da utilizzare definendo un&#39;affinità per sottodominio e creando una tipologia per affinità. Le affinità sono definite nel file di configurazione dell&#39;istanza. Contattate l’amministratore  Adobe Campaign.

For more on typologies, refer to [this section](../../campaign/using/about-campaign-typologies.md).

## Progettazione e personalizzazione {#design-and-personalize}

Durante la progettazione del contenuto del messaggio, cercate di evitare problemi comuni che potrebbero impedire l&#39;esecuzione della distribuzione. Nella maggior parte dei casi, eventuali errori sono correlati a [personalizzazione](../../delivery/using/about-personalization.md), [formattazione](../../delivery/using/defining-the-email-content.md#message-content) e [immagini](../../delivery/using/defining-the-email-content.md#adding-images).

### Ottimizzare la personalizzazione {#optimize-personalization}

Per evitare problemi comuni che potrebbero impedire l’esecuzione della consegna e migliorare l’esperienza dei destinatari,  Adobe Campaign consente di personalizzare i messaggi.

È possibile utilizzare i dati dei destinatari memorizzati nel database Adobe Campaign  oppure raccolti tramite tracciamento, pagine di destinazione, iscrizioni ecc.
Le nozioni di base sulla personalizzazione sono presentate in [questa sezione](../../delivery/using/personalization-fields.md).

Assicurati che il contenuto del messaggio sia progettato correttamente per evitare errori, generalmente correlati alla personalizzazione.

**Suggerimenti**: Nei campi di personalizzazione provenienti da file esterni forniti da fornitori di terze parti, il contenuto HTML esterno può essere errato. Per evitare questo problema, controllare la sintassi, l&#39;uso di tag, caratteri e così via. Ad esempio, un tag di personalizzazione Adobe Campaign  ha sempre il seguente modulo: &lt;%=table.field%>. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/about-personalization.md).

L’uso non corretto dei parametri nei blocchi di personalizzazione può rappresentare un problema. Ad esempio, le variabili in JavaScript devono essere utilizzate come segue:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Per ulteriori informazioni sui blocchi di personalizzazione, consulta [questa sezione](../../delivery/using/personalization-blocks.md).

Puoi preparare i dati di personalizzazione in un flusso di lavoro per migliorare l’analisi della preparazione della distribuzione. Questo dovrebbe essere utilizzato specialmente se i dati di personalizzazione provengono da una tabella esterna tramite Federated Data Access (FDA). Questa opzione è descritta in questa [sezione](../../delivery/using/personalization-fields.md#optimizing-personalization)

### Creare contenuto ottimizzato {#optimize-content}

Durante la creazione delle e-mail, tieni presente le best practice generali riportate di seguito.

* Design semplice

* Ricordate gli utenti dei dispositivi mobili

* Evita e-mail basate interamente su immagini

* Utilizzo di font sicuri per le e-mail

* Codifica di caratteri speciali

**Linea** Oggetto - Lavori sulla [linea](../../delivery/using/defining-the-email-content.md#message-content) oggetto per migliorare le tariffe aperte:

* Evitare soggetti troppo lunghi. Utilizza un massimo di 50 caratteri

* Evitare di usare parole ripetitive come &quot;free&quot; o &quot;offer&quot;, che potrebbero essere considerate spam

* Evitare lettere maiuscole e caratteri speciali come &quot;!&quot;, &quot;€&quot;, &quot;€&quot;, &quot;$&quot;

**Mirror page** - Includi sempre un collegamento di pagina speculare. La posizione preferita è la parte superiore dell’e-mail. [Ulteriori informazioni](../../delivery/using/sending-messages.md#generating-the-mirror-page)

**Collegamento** di annullamento sottoscrizione - Il collegamento di annullamento sottoscrizione è essenziale. Deve essere visibile e valido e il modulo deve essere funzionale. Per impostazione predefinita, quando il messaggio viene analizzato, una regola di [tipologia](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) controlla se è stato incluso un collegamento di rinuncia e genera un avviso se risulta mancante.

**Suggerimento**: Poiché l’errore umano è sempre possibile, verificate che il collegamento di rinuncia funzioni correttamente prima di ogni invio. Ad esempio, al momento dell&#39;invio della prova, verificare che il collegamento sia valido, che il modulo sia online e che il campo Destinatario non contatta più sia cambiato in Sì.

Scoprite come inserire un collegamento di rifiuto [in questa sezione](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

**Dimensione** e-mail: per evitare problemi di prestazioni o di recapito, la dimensione massima consigliata per un&#39;e-mail è di circa **35 KB**. Per verificare la dimensione del messaggio, andate alla **[!UICONTROL Preview]** scheda e scegliete un profilo di prova. Una volta generata, la dimensione del messaggio verrà visualizzata nell&#39;angolo superiore destro.

Per mantenere l’e-mail al di sotto del limite, tenete presente quanto segue:

* Rimuovere stili ridondanti o inutilizzati

* Spostare parte del contenuto dell’e-mail in una pagina di destinazione

* Riduzione del codice

Verificare eventuali modifiche prima dell&#39;invio finale

**Lunghezza SMS**

Per impostazione predefinita, il numero di caratteri in un SMS soddisfa gli standard GSM (Global System for Mobile Communications). I messaggi SMS che utilizzano la codifica GSM sono limitati a 160 caratteri o 153 caratteri per SMS per messaggi inviati in più parti.

La traslitterazione consiste nel sostituire un carattere di un SMS con un altro quando quel carattere non è preso in considerazione dallo standard GSM. L&#39;inserimento di campi di personalizzazione nel contenuto del messaggio SMS potrebbe introdurre caratteri che non vengono presi in considerazione dalla codifica GSM. È possibile autorizzare la traslazione dei caratteri selezionando la casella corrispondente nella scheda delle impostazioni del canale SMPP della corrispondente **[!UICONTROL External account]**.
Ulteriori informazioni [in questa sezione](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Suggerimenti**:

* Per mantenere tutti i caratteri nei messaggi SMS così come sono, per non alterare i nomi propri, ad esempio, non abilitare la traslazione.

* Tuttavia, se i vostri messaggi SMS contengono molti caratteri che non sono presi in considerazione dallo standard GSM, abilitate la traslazione per limitare i costi di invio dei vostri messaggi.

Ulteriori informazioni [in questa sezione](../../delivery/using/sms-channel.md#about-character-transliteration).

### Operazioni di formattazione {#formatting}

Per evitare errori di formattazione comuni, verificare quanto segue:

* Correggi la formattazione **della** data:  Adobe Campaign fornisce funzioni di formattazione delle date per i modelli JavaScript e i fogli di stile XSL. [Ulteriori informazioni](../../delivery/using/formatting.md#date-display)

* Utilizzo di caratteri **** autorizzati nelle e-mail: l&#39;elenco di caratteri validi per gli indirizzi e-mail è definito nell&#39;opzione &quot;XtkEmail_Characters&quot;. Scopri come accedere alle opzioni Campagna [in questa sezione](../../installation/using/configuring-campaign-options.md). Per gestire correttamente i caratteri speciali,  Adobe Campaign deve essere installato in Unicode.

* Configurazione dell&#39;autenticazione **** e-mail: accertatevi che le intestazioni e-mail contengano la firma DKIM. L&#39;autenticazione DKIM (Domain Keys Identified Mail) consente al server di posta elettronica ricevente di verificare che un messaggio sia stato effettivamente inviato dalla persona o dall&#39;entità da cui sostiene di essere stato inviato, e se il contenuto del messaggio sia stato modificato tra il momento dell&#39;invio originale (e DKIM &quot;signed&quot;) e l&#39;ora in cui è stato ricevuto. In genere, questo standard utilizza il dominio nell’intestazione Da o Mittente. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/technical-recommendations.md#dkim).

* **La progettazione** reattiva delle e-mail garantisce il rendering ottimale di un&#39;e-mail per il dispositivo su cui viene aperta.

   * Utilizzate HTML reattivi per le e-mail invece che HTML Web.

   * Utilizzate la modalità di anteprima e inviate le prove di stampa per testare il rendering su quanti più dispositivi possibile.

   * Il modulo Adobe Campaign Classic Digital Content Editor (DCE) include alcuni modelli di progettazione reattiva per dispositivi mobili disponibili tramite **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Ulteriori informazioni [in questo articolo](https://theblog.adobe.com/responsive-email-design-101/).



### Gestire le immagini {#manage-images}

Seguite le linee guida riportate di seguito quando si tratta di usare le immagini.

* **Impedire il blocco** delle immagini: alcuni client di posta elettronica bloccano le immagini per impostazione predefinita, mentre altri modificano le impostazioni per bloccare le immagini e salvarle in base all’utilizzo dei dati. Pertanto, se le immagini non vengono scaricate, l&#39;intero messaggio può andare perso. Per evitare ciò:

   * Bilancia i contenuti con immagini e testo. Evitate e-mail basate interamente su immagini.

   * Se il testo deve essere contenuto in un’immagine, usate il testo alternativo e del titolo per essere certi che il messaggio possa essere trasmesso. Applicate uno stile al testo alt/title per migliorarne l’aspetto.

   * Evitate l’utilizzo di immagini di sfondo poiché non sono supportate da alcuni client e-mail.

* **Rendere le immagini reattive** - Provate a rendere le immagini reattive e ridimensionabili. Questo può avere un impatto sui costi in quanto la creazione richiede più tempo.

* **Utilizzare riferimenti** di immagine assoluti - Per essere accessibili dall&#39;esterno, le immagini utilizzate nelle e-mail e le risorse pubbliche collegate alle campagne devono essere presenti su un server esterno accessibile.

   * È possibile verificare se la configurazione dell&#39;istanza abilita la gestione delle risorse pubbliche. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#managing-public-resources)

   * Dalla procedura guidata di distribuzione, potete importare una pagina HTML contenente immagini o inserire immagini direttamente mediante l’editor HTML tramite l’ **[!UICONTROL Image]** icona . [Ulteriori informazioni](../../delivery/using/defining-the-email-content.md#adding-images)

   * Se le immagini non sono visualizzate, controllate che siano disponibili sul server. A questo scopo, fate clic sulla scheda Sorgente dalla consegna. Trovate le immagini e copiate l’URL di ciascuna immagine in un browser Web. Se le immagini non vengono visualizzate, contattate l’amministratore IT o il fornitore di terze parti che fornisce il contenuto per la distribuzione.

### Anteprima del messaggio {#preview-msg}

 Adobe consiglia di visualizzare in anteprima il messaggio per verificarne la personalizzazione e vedere in che modo i destinatari vedranno la consegna.

* Nella procedura di consegna, la **[!UICONTROL Preview]** sottoscheda consente di visualizzare il rendering di ciascun contenuto per un destinatario. I campi di personalizzazione e gli elementi condizionali del contenuto vengono sostituiti con le informazioni corrispondenti per il profilo selezionato. [Ulteriori informazioni](../../delivery/using/defining-the-email-content.md#message-content)

* Durante ogni anteprima viene eseguito un controllo automatico dello spam. Nella **[!UICONTROL Preview]** sottoscheda, seleziona [SpamAssassin](../../delivery/using/spamassassin.md) spam Scoring.  Fare clic **[!UICONTROL More...]** per ulteriori informazioni sull&#39;avviso.  Prima di eseguire questa operazione, assicurarsi che SpamAssassin sia correttamente installato e configurato sul server  applicazione Adobe Campaign. [Ulteriori informazioni](../../installation/using/configuring-spamassassin.md)

## Definire la destinazione giusta {#define-the-right-target}

La popolazione mirata è la chiave: create con attenzione gli elenchi, verificate i messaggi e-mail sui client e dispositivi mobili più diffusi e verificate che gli elenchi delle e-mail siano aggiornati (senza indirizzi sconosciuti o obsoleti). È inoltre possibile inviare delle prove che aiutino a configurare un ciclo di convalida completo.

Ulteriori informazioni sulle popolazioni di destinazione [in questa sezione](../../delivery/using/steps-defining-the-target-population.md)

### Targeting dell&#39;audience giusta {#target-the-right-audience}

Quando il contenuto è pronto, è necessario definire con attenzione chi riceverà il messaggio.

Per garantire il successo della distribuzione, è necessario inviare i contenuti personalizzati più rilevanti ai destinatari giusti.  Adobe Campaign consente di realizzare il target più preciso: potete selezionare i destinatari in base alla loro età, localizzazione, cosa hanno acquistato, se hanno fatto clic su un collegamento in una consegna precedente, ecc. Con  Adobe Campaign, potete anche definire profili di test, gruppi di controllo e indirizzi iniziali per essere certi che la destinazione sia corretta.

### Mappature di destinazione {#target-mappings}

In Campaign Classic, per impostazione predefinita, i modelli di consegna sono destinati **ai destinatari**.  Adobe Campaign offre altre mappature di destinazione per le consegne, che potete modificare in base alle vostre esigenze.

Ad esempio, potete trasmettere ai visitatori i cui profili sono stati raccolti tramite social network o ai visitatori che hanno sottoscritto un servizio di informazione.

Tali mappature vengono presentate [in questa sezione](../../delivery/using/selecting-a-target-mapping.md).

Potete anche creare e utilizzare una mappatura di destinazione personalizzata. Per ulteriori informazioni, consulta [questa sezione](../../configuration/using/target-mapping.md).

### Destinatari esterni {#external-recipients}

È possibile inviare i dati ai destinatari memorizzati in un file esterno anziché salvati nel database. Ulteriori informazioni [in questa sezione](../../delivery/using/steps-defining-the-target-population.md#selecting-external-recipients).

### Invia ai tuoi abbonati {#send-to-subscribers}

Per inviare messaggi agli abbonati di una newsletter, potete indirizzare direttamente gli abbonati al servizio di informazioni corrispondente. Ulteriori informazioni [in questa sezione](../../delivery/using/managing-subscriptions.md#delivering-to-the-subscribers-of-a-service).


### Destinatari del test e indirizzi iniziali {#test-recipients-seed-addresses}

Per verificare la consegna, utilizzate le prove prima di inviare alla destinazione principale.

Accertarsi di aver selezionato i destinatari della prova appropriati, in quanto convalidano il modulo e il contenuto del messaggio. Le fasi per la definizione dei destinatari della prova sono illustrate [in questa sezione](../../delivery/using/steps-defining-the-target-population.md#selecting-the-proof-target).

Gli indirizzi dei semi vengono utilizzati per i destinatari a cui non corrispondono i criteri di destinazione definiti, al fine di verificare la consegna prima dell&#39;invio alla destinazione principale. Sono presentati [in questa sezione](../../delivery/using/about-seed-addresses.md).

### Indirizzi di deduplicazione {#deduplicate-addresses}

È importante evitare di avere indirizzi e-mail duplicati, in quanto ciò può avere un impatto sulla destinazione:

* Lo stesso messaggio può essere inviato più volte quando una destinazione viene divisa.

* Se un destinatario annulla la sottoscrizione dopo aver ricevuto un messaggio, il profilo duplicato riceverà comunque messaggi futuri.

Gli indirizzi di deduplicazione proteggono la reputazione dell&#39;invio e garantiscono una buona gestione della quarantena.

Ulteriori informazioni [in questo caso](../../workflow/using/deduplication.md#example--identify-the-duplicates-before-a-delivery)di utilizzo.


### Indirizzi e-mail indice {#index-addresses}

Per ottimizzare le prestazioni delle query SQL utilizzate nell&#39;applicazione, è possibile dichiarare un indice dall&#39;elemento principale dello schema di dati.

I passaggi per aggiungere un indice all&#39;indirizzo e-mail sono descritti [in questa sezione](../../configuration/using/database-mapping.md#indexed-fields).

## Esegui tutti i controlli prima dell&#39;invio {#perform-all-checks}

Una volta che il messaggio è pronto, accertati che il contenuto sia visualizzato correttamente, su tutti i dispositivi, e non contenga errori quali personalizzazione errata o collegamenti interrotti.

Prima di inviare il messaggio, assicurati anche che i parametri e la configurazione siano coerenti con la consegna.

### Convalida è la chiave {#validation-is-key}

Prima di inviare una consegna, è necessario assicurarsi che i destinatari ricevano il messaggio che si desidera inviare. A tal fine, devi convalidare il contenuto del messaggio e i parametri di consegna.

Questo passaggio consente di rilevare eventuali errori e di correggerli prima di inviarli alla destinazione principale.

I passaggi per la convalida di una consegna sono descritti [in questa sezione](../../delivery/using/steps-validating-the-delivery.md).

### Rendering in entrata {#inbox-and-email-rendering}

Il rendering della casella in entrata consente di visualizzare l&#39;anteprima dei messaggi sui principali client e-mail, acquisire il contenuto e la reputazione, scoprire in che modo i destinatari leggono i messaggi.

**Suggerimenti**:

* Puoi visualizzare il messaggio inviato nei diversi contesti in cui potrebbe essere ricevuto: webmail, servizio messaggi, mobile, ecc.

* Le funzionalità di rendering della inbox sono fondamentali per identificare se le campagne e-mail riescono a superare i filtri dei principali provider di servizi Internet (provider di servizi Internet) e dei servizi di posta elettronica. Tali strumenti inviano una copia pre-verifica di un messaggio e-mail a una rete di caselle in entrata di prova, in modo da visualizzare il modo in cui il messaggio verrà visualizzato, o renderizzato, tra questi servizi. Possono inoltre includere rapporti e opzioni di correzione del codice che consentono di identificare e correggere rapidamente i problemi di recapito.

Ulteriori informazioni [in questa sezione](../../delivery/using/inbox-rendering.md).

### Messaggi di prova {#proof-messages}

L&#39;invio di prove consente di controllare il collegamento di rinuncia, la pagina mirror e qualsiasi altro collegamento, convalidare il messaggio, verificare che le immagini siano visualizzate, rilevare eventuali errori, ecc. È inoltre possibile controllare la progettazione e il rendering su diversi dispositivi.

Ulteriori informazioni [in questa sezione](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

### Configurare le consegne di test A/B {#a-b-testing-deliveries}

Se disponete di diversi contenuti per la consegna delle e-mail, potete utilizzare il test A/B per scoprire quale versione avrà il maggiore impatto sulla popolazione interessata.

**Suggerimenti**:

* Inviare le diverse versioni ad alcuni dei destinatari

* Seleziona quella con il tasso di successo più elevato e inviala al resto della destinazione

Ulteriori informazioni [in questa sezione](../../workflow/using/a-b-testing.md).

### Assicurati che il messaggio sia stato recapitato {#make-sure-your-message-is-delivered}

Come ultimo passo, massimizza le tue possibilità e sfrutta la potenza di Adobe Campaign Classic per garantire che il messaggio venga effettivamente recapitato ai destinatari interessati.

**Attraverso un processo** di convalida è possibile definire un processo di convalida completo, che coinvolga  operatori e gruppi Adobe Campaign, per convalidare sia la destinazione che il contenuto del messaggio. Ciò garantirà il pieno monitoraggio e controllo dei vari processi della campagna: targeting, contenuto, budget, estrazione e invio di una prova. A seconda delle autorizzazioni assegnate, gli utenti riceveranno una notifica, riceveranno prove di validità e potranno convalidare o rifiutare il messaggio. Ulteriori informazioni [in questa sezione](../../campaign/using/marketing-campaign-approval.md#approval-process).

**Usa onde** - Puoi aumentare progressivamente il volume inviato utilizzando le onde. In questo modo i messaggi non verranno contrassegnati come spam o se si desidera limitare il numero di messaggi al giorno. Utilizzando le onde è possibile dividere le consegne in più batch anziché inviare contemporaneamente volumi elevati di messaggi. Ulteriori informazioni [in questa sezione](../../delivery/using/steps-sending-the-delivery.md#sending-using-multiple-waves).

**Assegnare priorità ai messaggi** : è possibile impostare l&#39;ordine di invio per le consegne specificando il livello di priorità. Per eseguire questa operazione:

1. Modificate le proprietà di consegna e selezionate la **[!UICONTROL Delivery]** scheda.

1. Definire il livello di priorità per la consegna su una scala da **[!UICONTROL Very low]** a **[!UICONTROL Very high]**.

>[!NOTE]
>
>Non è possibile definire l&#39;ordine di invio dei messaggi dall&#39;interno di una consegna.

**Impostazione delle affinità** IP - Per controllare meglio il traffico SMTP in uscita, è possibile gestire le affinità definendo quali indirizzi IP specifici possono essere utilizzati per ogni affinità. Questo consente di limitare il numero di e-mail per consegne specifiche verso computer o indirizzi di output. Ad esempio, è possibile utilizzare un&#39;affinità per paese o sottodominio. Potete quindi creare una tipologia per paese e collegare ciascuna affinità alla tipologia corrispondente.

Puoi:

* Definite le affinità IP nel file di configurazione serverConf.xml. [Ulteriori informazioni](../../installation/using/configuring-campaign-server.md#managing-outbound-smtp-traffic-with-affinities)

* Per ogni elemento IPAffinity, dichiarare gli indirizzi IP che possono essere utilizzati. [Ulteriori informazioni](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

* Nella [tipologia](../../campaign/using/about-campaign-typologies.md) scelta, utilizza il **[!UICONTROL Managing affinities with IP addresses]** campo per collegare le consegne al server di consegna (MTA) che gestisce tale affinità. [Ulteriori informazioni](../../campaign/using/applying-rules.md#control-outgoing-smtp-traffic).

* Una volta inviato il messaggio e-mail, controllate l&#39;intestazione per verificare da quale indirizzo IP è stato inviato il messaggio. L’amministratore dell’e-mail deve essere in grado di ottenere le informazioni di intestazione.

>[!NOTE]
>
>La maggior parte di questi passaggi può essere eseguita solo da un utente esperto.

**Utilizzo di tipologie** - È possibile utilizzare regole di tipologia per escludere parte della destinazione in base a criteri specifici. Questo garantisce che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali. Ad esempio, potete filtrare i destinatari meno recenti dalla destinazione della newsletter. Ulteriori informazioni [in questo esempio](../../campaign/using/filtering-rules.md).

**Evitare allegati** - Gli allegati rimangono uno dei vettori più comuni per la proliferazione di malware, soprattutto quando sono inviati in massa. Includete un collegamento protetto al documento invece di allegarlo. Questo garantisce un ulteriore livello di sicurezza per impedire la ridistribuzione indesiderata e riduce notevolmente le possibilità che il messaggio venga rifiutato nei gateway e-mail in ingresso per motivi di dimensione o sicurezza del messaggio.

## Monitoraggio e monitoraggio {#track-and-monitor}

Hai fatto clic sul pulsante Invia? Vediamo cosa succede. Una volta inviata la consegna,  Adobe Campaign consente di tenere traccia dei messaggi inviati e di scoprire in che modo i destinatari reagiscono alla consegna. In questo modo potrai migliorare l’invio futuro e ottimizzare le campagne successive.

### Monitoraggio delle consegne {#monitoring-deliveries}

Per controllare le campagne, devi accertarti che il messaggio sia stato effettivamente recapitato ai destinatari.

Dal dashboard di distribuzione della campagna, puoi controllare i messaggi elaborati e i registri di controllo della distribuzione.
Puoi anche controllare lo stato dei messaggi nei registri di consegna. [Ulteriori informazioni](../../delivery/using/monitoring-a-delivery.md#delivery-dashboard).

Cosa succede se le consegne non vengono inviate e il loro stato rimane **In sospeso**?

* Il processo di esecuzione è in attesa della disponibilità di alcune risorse. L&#39;MTA potrebbe non essere stato avviato.
Verificate che i moduli mta@instance siano avviati sui server MTA e avviate il modulo MTA, se necessario. [Ulteriori informazioni](../../production/using/administration.md).

* La consegna potrebbe utilizzare un&#39;affinità non configurata nell&#39;istanza di invio.
Suggerimento: Controllare la configurazione della gestione del traffico (affinità IP). Per ulteriori informazioni, vedere Controllo del traffico SMTP in uscita.

>[!NOTE]
>
>Questi passaggi possono essere eseguiti solo da un utente esperto.

### Tracciamento {#tracking-deliveries}

Per conoscere meglio il comportamento dei destinatari, puoi tenere traccia delle loro reazioni: ricezione, apertura, clic su collegamenti, annullamento sottoscrizioni, ecc. In Campaign Classic, queste informazioni vengono visualizzate nella scheda Tracciamento dei destinatari destinatari della consegna e nella scheda Tracciamento della consegna. In Campaign Standard , viene visualizzato nella scheda Registri di tracciamento della consegna.

**Suggerimento**: Il tracciamento dei messaggi è abilitato per impostazione predefinita. Per configurare gli URL, selezionate l’opzione Visualizza URL nella sezione inferiore della procedura guidata di consegna. Per ciascun URL del messaggio, potete scegliere se attivare il tracciamento.

Per ulteriori informazioni, consulta la sezione [Configurazione del tracciamento](../../delivery/using/how-to-configure-tracked-links.md) e la descrizione degli indicatori [di](../../reporting/using/delivery-reports.md#tracking-indicators) tracciamento.

### Prestazioni di consegna {#delivery-performances}

Per misurare la velocità di invio dei messaggi, puoi controllare la velocità di consegna. I criteri corrispondono al numero di messaggi inviati ogni ora e alla dimensione dei messaggi (in bit al secondo). Per ulteriori informazioni, consulta [Distribuzione effettiva](../../reporting/using/global-reports.md#delivery-throughput).

**Suggerimenti**:

* Non mantenere le consegne in stato di errore nell&#39;istanza, in quanto questo mantiene le tabelle temporanee e influisce sulle prestazioni.

* Rimuovete dal database i recapiti non più necessari e i destinatari inattivi per mantenere la qualità degli indirizzi.

* Non provare a pianificare insieme consegne di grandi dimensioni. Si prega di notare che possono essere necessari da 5 a 10 minuti per distribuire uniformemente il carico sul sistema.

## Risoluzione dei problemi di consegna {#delivery-troubleshooting}

È possibile eseguire azioni specifiche quando si verificano problemi con le consegne:

* [Problemi di realizzazione](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [Problemi di visualizzazione delle immagini](../../production/using/image-display-issues.md)

* [Problemi relativi alle prestazioni di distribuzione](../../delivery/using/monitoring-a-delivery.md#performance_issues)

* [Problemi relativi](../../production/using/temporary-files.md) ai file temporanei - solo per i clienti *interni*
