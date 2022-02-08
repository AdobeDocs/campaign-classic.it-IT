---
product: campaign
title: Regole di pressione
description: Regole di pressione
feature: Fatigue Management, Typology Rules
exl-id: c23212f2-fdf8-4820-b389-546f7c84db27
source-git-commit: 90c52ec144a6a3c1b534a80507e38fa3ed64fc83
workflow-type: tm+mt
source-wordcount: '3285'
ht-degree: 4%

---

# Regole di pressione{#pressure-rules}

![](../../assets/common.svg)

## Informazioni sull’affaticamento del marketing {#about-marketing-fatigue}

L’implementazione della gestione della pressione di vendita ti consente di evitare di sollecitare eccessivamente la popolazione nel database, nota anche come affaticamento del marketing. A questo scopo, puoi definire un numero massimo di messaggi per destinatario. Ti consente inoltre di implementare regole di arbitrato tra le campagne, al fine di inviare il messaggio migliore al pubblico di destinazione.

**Pressione** regole, per gestire l’affaticamento del marketing, ad esempio, per limitare il numero di lettere da inviare a una popolazione a due, per selezionare la comunicazione che meglio corrisponde agli interessi di un gruppo di abbonati, per evitare di inviare un SMS a un cliente insoddisfatto, ecc.

Le campagne vengono selezionate in base a soglie definite e al peso del messaggio.

* Una soglia è il numero massimo di consegne autorizzate per un dato destinatario in un dato periodo di tempo. Può essere impostato o variabile. Viene impostato o calcolato nelle impostazioni della regola di tipologia. Fai riferimento a [Numero massimo di messaggi](#maximum-number-of-messages).
* I pesi di distribuzione consentono di identificare le consegne prioritarie nel quadro della gestione della pressione. I messaggi con il peso maggiore hanno priorità. Fai riferimento a [Peso del messaggio](#message-weight).

L’arbitrato consiste nell’assicurarsi che le campagne pianificate il cui peso è maggiore della campagna in corso non portino a un’eccessiva sollecitazione del profilo: in questo caso, il profilo viene escluso dalla consegna.

I criteri di arbitrato (peso e/o soglia dei messaggi) possono variare in base a due tipi di informazioni:

* preferenza del destinatario, che è un&#39;informazione dichiarativa: abbonamenti a newsletter, stato del destinatario (cliente o potenziale cliente),
* comportamento del destinatario: acquisti, collegamenti visitati, ecc.

La regola di arbitrato per la definizione dei messaggi idonei viene applicata durante la fase di analisi. Per ciascun destinatario e per il periodo in questione, il messaggio viene inviato se la seguente formula è vera: **(numero di messaggi inviati) + (numero di messaggi con un peso maggiore) &lt; soglia**.

In caso contrario, il destinatario sarà **[!UICONTROL Excluded by arbitration]**. Per ulteriori informazioni, consulta [Esclusione dopo arbitrato](#exclusion-after-arbitration).

## Creazione di una regola di pressione {#creating-a-pressure-rule}

Per impostare l’arbitrato tra le campagne che utilizzano Adobe Campaign, inizia con la creazione di tipologie di campagne e la definizione di regole di tipologia collegate (**Pressione** regole).

Per creare e configurare una regola di tipologia **[!UICONTROL Pressure]**, attieniti alla seguente procedura:

1. Nell’elenco delle regole di tipologia della campagna, fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. In **[!UICONTROL General]** scheda della nuova regola, seleziona un **Pressione** digita la regola e immetti un nome e una descrizione.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. Se necessario, modifica l’ordine di esecuzione. Quando più regole di tipologia vengono applicate come **[!UICONTROL Typology]** impostate, le regole ordinate inferiori vengono applicate per prime. Per ulteriori informazioni, consulta [Ordine di esecuzione](applying-rules.md#execution-order).
1. In **[!UICONTROL Calculation parameters]** definisci una frequenza se desideri salvare il targeting oltre la successiva esecuzione giornaliera di ri-arbitraggio. Per ulteriori informazioni, consulta [Regolazione della frequenza di calcolo](applying-rules.md#adjusting-calculation-frequency).
1. Fai clic sul pulsante **[!UICONTROL Pressure]** e scegli il periodo di calendario durante il quale si applica la regola di tipologia.

   ![](assets/campaign_opt_create_a_rule_03.png)

   La regola sarà applicata alle consegne la cui data di contatto è inclusa nel periodo in questione.

   >[!NOTE]
   >
   >Le consegne programmate vengono prese in considerazione solo se **[!UICONTROL Take the deliveries into account in the provisional calendar]** è selezionata. Per ulteriori informazioni, consulta [Impostazione del periodo](#setting-the-period).
   >
   >Questa opzione non è disponibile in Campaign v8.

1. Definisci il metodo di calcolo del numero più alto di messaggi.

   La soglia rappresenta il numero massimo di messaggi che possono essere inviati a un destinatario durante il periodo in questione.

   Per impostazione predefinita, la soglia è costante e devi indicare un numero massimo di messaggi autorizzati dalla regola.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   Per definire una soglia variabile, seleziona la **[!UICONTROL Depends on the recipient]** nel **[!UICONTROL Type of threshold]** e utilizza l’icona a destra per aprire l’editor di espressioni.

   ![](assets/campaign_opt_create_a_rule_04.png)

   Per ulteriori informazioni, consulta [Numero massimo di messaggi](#maximum-number-of-messages).

1. Specificare il metodo di calcolo del peso della consegna.

   Ogni consegna ha un peso, ovvero un valore che rappresenta il suo livello di priorità: questo consente l&#39;arbitrato tra le campagne. I pesi vengono calcolati utilizzando la formula definita nella regola di tipologia e/o nelle relative proprietà. Per ulteriori informazioni, consulta [Peso del messaggio](#message-weight).

1. Per impostazione predefinita, tutti i messaggi vengono presi in considerazione per il calcolo della soglia. La **[!UICONTROL Restriction]** consente di filtrare i messaggi interessati dalla regola di tipologia:

   * La sezione superiore di questa scheda ti consente di limitare i destinatari interessati.
   * La sezione inferiore di questa scheda ti consente di filtrare i messaggi da conteggiare.

      Nell’esempio seguente, solo i destinatari salvati nel **NuoviContatti** vengono prese in considerazione e le consegne che iniziano con **Newsletter** sono preoccupati.
   ![](assets/campaign_opt_create_a_rule_05.png)

1. La **[!UICONTROL Typologies]** La scheda ti consente di visualizzare le tipologie di campagna che applicano questa regola o di collegare la regola a una o più tipologie esistenti. Per ulteriori informazioni, consulta [Applicazione delle tipologie](about-campaign-typologies.md#applying-typologies).

## Definire soglie e pesi {#defining-thresholds-and-weights}

### Numero massimo di messaggi {#maximum-number-of-messages}

Ogni regola di pressione definisce una soglia, ovvero il numero massimo di messaggi che possono essere inviati a un destinatario in un determinato periodo di tempo. Una volta raggiunta tale soglia, non potranno più essere effettuate ulteriori consegne fino alla fine del periodo considerato. Questo processo ti consente di escludere automaticamente un destinatario da una consegna se un messaggio supera la soglia impostata, evitando in tal modo un’eccessiva sollecitazione.

I valori di soglia possono essere costanti o calcolati da una formula con variabili. Ciò significa che per un determinato periodo le soglie possono variare da un destinatario all’altro o anche per lo stesso destinatario.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>Inserimento **0** come soglia impedisce tutte le consegne alla popolazione target durante il periodo in esame.

**Esempio:**

Puoi indicizzare il numero di messaggi autorizzati in base al segmento a cui appartiene il destinatario. Ciò significa che un destinatario appartenente al segmento web può ricevere più messaggi rispetto ad altri destinatari. Un **[!UICONTROL Iif (@origin='Web', 5, 3)]** la formula di tipo autorizza la consegna di 5 messaggi ai destinatari e di 3 per altri segmenti. La configurazione sarà la seguente:

![](assets/campaign_opt_pressure_sample.png)

Per definire la soglia, puoi utilizzare una dimensione collegata alla dimensione di targeting: ad esempio, per includere i messaggi inviati ai profili dei destinatari memorizzati nella tabella dei visitatori (per ulteriori informazioni sulla tabella dei visitatori, consulta [questa sezione](../../surveys/using/use-case--creating-a-refer-a-friend-form.md)) o per evitare di inviare più di un messaggio alla settimana alla stessa famiglia (che può fare riferimento a più indirizzi e-mail) identificati in una dimensione collegata a quella dei destinatari.

A tale scopo, seleziona la **[!UICONTROL Count messages on a linked dimension]** , quindi seleziona il visitatore o la tabella dei contatti.

### Peso del messaggio {#message-weight}

Ogni consegna ha un peso che rappresenta il suo livello di priorità. Per impostazione predefinita, il peso di una consegna è impostato su 5. Le regole di pressione ti consentono di definire il peso delle consegne a cui verranno applicate.

I pesi possono essere impostati o calcolati tramite una formula adatta ai destinatari. Ad esempio, puoi definire il peso di una consegna in base agli interessi dei destinatari.

>[!CAUTION]
>
>Il peso definito in una regola di tipologia può essere sovraccaricato singolarmente per ogni consegna, nel **[!UICONTROL Properties]** scheda . Fai clic sul pulsante **[!UICONTROL Typology]** per selezionare la tipologia della campagna e, se necessario, specificare il peso da applicare.\
>Tuttavia, il peso dichiarato in una regola di tipologia A non verrà utilizzato per calcolare una regola di tipologia B: questo peso riguarda solo le consegne che utilizzano la regola A.

**Esempio:**

Nell’esempio seguente, vogliamo collegare il peso delle newsletter sulla musica al punteggio di propensione dei loro destinatari. Per eseguire questa operazione:

1. Crea un nuovo campo per memorizzare i punteggi di propensione dei destinatari. Il campo, **@Musica** in questo caso, saranno arricchite con risposte a sondaggi e sondaggi online, dati di tracciamento raccolti, ecc.
1. Crea una regola di tipologia per calcolare il peso del messaggio in base a questo campo.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. Applica questa regola ai messaggi con il seguente argomento: newsletter, offerte speciali, ecc. Il peso di queste consegne, e quindi il loro livello di priorità, dipenderà dal punteggio di propensione di ciascun destinatario.

## Imposta il periodo {#setting-the-period}

Le regole di pressione sono definite in **n**- periodi continui.

Il periodo è configurato nel **[!UICONTROL Pressure]** scheda della regola. Puoi specificare il numero di giorni e, se necessario, selezionare il tipo di raggruppamento da applicare (giorno, settimana, mese, trimestre, ecc.).

Il tipo di raggruppamento consente di estendere la **[!UICONTROL Period considered]** all&#39;intero giorno, settimana, mese o anno civile per le date del periodo.

Ad esempio, una regola di pressione che definisce una soglia di 2 messaggi alla settimana, con un raggruppamento per ogni mese di calendario, impedirà la consegna di più di 2 messaggi entro la stessa settimana E nello stesso mese di calendario. Attenzione: se il periodo si sovrappone a due mesi, la soglia di calcolo terrà conto delle consegne di questi due mesi di calendario e potrebbe pertanto impedire tutte le nuove consegne nel secondo mese.

Per impostazione predefinita, nel calcolo della soglia vengono prese in considerazione solo le consegne già inviate. In Campaign Classic v7, controlla il **[!UICONTROL Take the deliveries into account in the provisional calendar]** se desideri anche considerare le consegne programmate per il periodo in questione. In questo caso, il periodo considerato è raddoppiato per consentire l’integrazione delle consegne future e di quelle precedenti.

Per limitare le consegne prese in considerazione a un periodo di 2 settimane, puoi:

1. Invio **15 quinquies** in **[!UICONTROL Concerned period]** campo: le consegne inviate fino a due settimane prima della data di consegna a cui si applica la regola saranno prese in considerazione nel calcolo,

o

1. Invio **7 quinquies** in **[!UICONTROL Period considered]** e controlla il **[!UICONTROL Take the deliveries into account in the provisional calendar]** opzione: le consegne inviate fino a 7 giorni prima della data di consegna e pianificate fino a 7 giorni dopo la data di consegna in cui viene applicata la regola saranno prese in considerazione nel calcolo.

   >[!AVAILABILITY]
   >Questo metodo non è disponibile in Campaign v8.

La data di inizio del periodo dipende dalla configurazione del database.

Ad esempio, se applichi una regola di pressione di 15 giorni senza raggruppamento a una consegna datata 12/11, le consegne saranno prese in considerazione tra il 27/11 e il 12/12. Se la regola della pressione tiene conto delle consegne nel calendario provvisorio, verranno prese in considerazione tutte le consegne programmate tra il 27/11/27 e il 12/27. Infine, se configuri un raggruppamento per mese di calendario nella regola, tutte le consegne di novembre e dicembre saranno prese in considerazione per calcolare la soglia (da 11/1 a 12/31).


**Casi frequenti**

Per garantire che le consegne della settimana civile corrente non siano prese in considerazione e non rischino di tenere conto anche di quelle della settimana precedente per la soglia di calcolo, specifica **[!UICONTROL Period considered]** a &#39;0&#39; e seleziona &#39;Raggruppamento per settimana di calendario&#39; come **[!UICONTROL Period type]**.

Quando un periodo è superiore a 0 (ad esempio 1), la soglia di calcolo può tenere conto delle consegne del giorno precedente. Pertanto, se il giorno precedente corrisponde alla settimana di calendario precedente e il tipo di periodo selezionato è &quot;Raggruppamento per settimana di calendario&quot;, verrà presa in considerazione tutta la settimana precedente per la soglia di calcolo.

**Esempio:**

Vogliamo creare una regola di pressione che limiti la sollecitazione a 3 messaggi per periodo di 2 settimane, con un raggruppamento al mese di calendario.

![](assets/campaign_opt_pressure_period_sample_1a.png)

Prendiamo 6 newsletter con lo stesso peso, in programma per il 30/05, 06/3, 06/8, 06/12, 06/22 e 06/30.

![](assets/campaign_opt_pressure_period_sample_0.png)

Le consegne programmate per il 12 e il 30 giugno non verranno inviate: la consegna 06/12 supererebbe la soglia di 3 messaggi per periodo di 2 settimane e la consegna 30 supererebbe la soglia delle comunicazioni autorizzate per mese civile.

![](assets/campaign_opt_pressure_period_sample_1.png)

Tutti i destinatari di queste consegne sono esclusi dall’arbitrato durante la fase di analisi:

![](assets/campaign_opt_pressure_period_sample_2.png)

Per la stessa regola, se raggruppi le consegne per trimestre, i destinatari di **newsletter n. 5** verranno esclusi e non verranno inviati.

Infine, se non è selezionato alcun raggruppamento, solo **newsletter n. 4** non verrà inviato, in quanto è stato pianificato per lo stesso periodo di 2 settimane delle prime tre newsletter.

>[!NOTE]
>
>Quando modifichi la definizione di una regola di tipologia, puoi creare un **Simulazione** per controllarne l’impatto sulle consegne applicate e monitorare l’impatto che le consegne esercitano sulle consegne reciproche. Per ulteriori informazioni, consulta [Simulazioni delle campagne](campaign-simulations.md).

## Esclusione dopo arbitrato {#exclusion-after-arbitration}

L&#39;arbitrato viene riapplicato ogni notte tramite il **[!UICONTROL Forecasting]** il flusso di lavoro tecnico e **[!UICONTROL Campaign jobs]** workflow.

La **[!UICONTROL Forecasting]** il flusso di lavoro precalcola i dati per il periodo in corso (dalla data di inizio alla data corrente), che consente di applicare le regole di tipologia durante l’analisi. Inoltre ricalcola i contatori di esclusione per arbitrato ogni notte.

Pertanto, per ciascun destinatario, Adobe Campaign controlla che il numero di messaggi da inviare non superi la soglia, tenendo conto del numero di messaggi già inviati per il periodo in questione. Queste informazioni sono **indicatore**, poiché tutti i calcoli vengono aggiornati al momento della consegna.

Se questo numero supera la soglia, vengono applicate le regole di arbitrato definite nella tipologia della campagna e i destinatari vengono esclusi dalle campagne con un peso inferiore.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>Se più consegne hanno lo stesso punteggio, viene inviata la campagna pianificata per la prima data.

## Casi d’uso sulle regole di pressione {#use-cases-on-pressure-rules}

### Adatta la soglia in base al criterio {#adapting-the-threshold-based-on-criterion}

Vogliamo creare una regola di tipologia per impedire la consegna di più di 4 messaggi alla settimana ai clienti e di 2 messaggi alla settimana ai potenziali clienti.

Per identificare clienti e potenziali clienti, utilizza la **[!UICONTROL Status]** , che contiene 0 per i potenziali clienti e 1 per i clienti.

Per creare la regola, esegui i seguenti passaggi:

1. Crea un nuovo **Pressione** digitare la regola di tipologia.
1. Modifica le **[!UICONTROL Pressure]** scheda: in **[!UICONTROL Maximum number of messages]** vogliamo creare una formula per calcolare la soglia in base a ciascun destinatario. Seleziona la **[!UICONTROL Depends on the recipient]** nel **[!UICONTROL Threshold type]** campo , quindi fai clic su **[!UICONTROL Edit expression]** a destra del **[!UICONTROL Formula]** campo .

   Fai clic sul pulsante **[!UICONTROL Advanced parameters]** per definire la formula di calcolo.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Seleziona la **[!UICONTROL Edit the formula using an expression]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. Nell’elenco delle funzioni, fai doppio clic sul pulsante **Iif** nella funzione **[!UICONTROL Others]** nodo.

   Quindi seleziona i destinatari **Stato** in **[!UICONTROL Available fields]** sezione .

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   Immettere la formula seguente: **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   Questa formula ti consente di assegnare il valore 2 se lo stato è uguale a 0 e il valore 4 per tutti gli altri stati.

   Fai clic su **[!UICONTROL Finish]** per approvare la formula.

1. Indicare il periodo durante il quale la regola sarà applicata: 7 giorni in questo caso, per contare il numero di messaggi alla settimana.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. Salva la regola per approvare la creazione.

Collega ora la regola appena creata a una tipologia per applicarla alle consegne. Per eseguire questa operazione:

1. Creare una tipologia di campagna.
1. Vai a **[!UICONTROL Rules]** fai clic sulla scheda **[!UICONTROL Add]** e seleziona la regola appena creata.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Salva la tipologia: viene aggiunto all’elenco delle tipologie esistenti.

Per utilizzare questa tipologia nelle consegne, selezionala nelle proprietà di consegna nella sezione **[!UICONTROL Typology]** come illustrato di seguito:

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>La tipologia può essere definita nel modello di consegna, da applicare automaticamente a tutte le consegne create utilizzando questo modello.

Durante l’analisi della consegna, i destinatari della consegna sono esclusi dalla consegna, se applicabile, in base al numero di consegne già inviate. Per visualizzare queste informazioni, puoi:

* Visualizza il risultato dell&#39;analisi:

   ![](assets/campaign_opt_pressure_sample_1_8.png)

* Modifica la consegna e fai clic sul pulsante **[!UICONTROL Delivery]** e **[!UICONTROL Exclusions]** sottoscheda:

   ![](assets/campaign_opt_pressure_sample_1_9.png)

* Fai clic sul pulsante **[!UICONTROL Audit]** , quindi la **[!UICONTROL Causes of exclusions]** sottoscheda per visualizzare il numero di esclusioni e le regole di tipologia applicate:

   ![](assets/campaign_opt_pressure_sample_1_10.png)

### Calcola il peso della consegna in base al comportamento {#calculating-the-delivery-weight-based-on-behavior}

Puoi definire regole di pressione in base al comportamento del destinatario: pertanto, il peso di una consegna può adattarsi a criteri che variano da un destinatario all&#39;altro. Ad esempio, puoi decidere di inviare un messaggio a seconda che un destinatario abbia visitato o meno il tuo sito Internet, abbia fatto clic su una sezione specifica dell’ultima newsletter, si sia iscritto a un servizio di informazione o anche in base alle risposte a un sondaggio, a un gioco online, ecc.

Nell’esempio seguente, vogliamo creare una consegna con un peso di 5. Questo peso viene arricchito con punteggi di propensione in base al comportamento del destinatario: i clienti che hanno già ordinato da questo sito avranno un punteggio di 5, mentre i clienti che non hanno mai ordinato online avranno un punteggio di 4.

Per eseguire questo tipo di configurazione, è necessario utilizzare una formula per definire lo spessore del messaggio. Le informazioni sui punteggi di propensione e le risposte ai sondaggi devono essere accessibili nel modello dati. Nel nostro esempio, il **Propensione** è stato aggiunto il campo .

Applica i seguenti passaggi di configurazione:

1. Crea un nuovo **Pressione** digitare la regola di tipologia.
1. Modifica le **[!UICONTROL Pressure]** scheda . Vogliamo creare una formula di soglia basata su ogni singolo destinatario: fai clic su **[!UICONTROL Edit expression]** a destra della **[!UICONTROL Weight formula]** campo .

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. Per impostazione predefinita, valore **5** viene visualizzato nella sezione superiore dell’editor di espressioni. Vogliamo aggiungere il punteggio di propensione di ogni destinatario a questo peso: posiziona il cursore a destra del 5, immetti il **+** e seleziona il **Propensione** campo .

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. Quindi aggiungi un valore più alto per i destinatari che hanno già effettuato un acquisto. Per loro, il peso della consegna deve essere aumentato di 5, mentre per altri aumenta di solo 4.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. Fai clic su **[!UICONTROL Finish]** per salvare questa regola.
1. Collega la regola a una tipologia di campagna e fai riferimento a questa tipologia in una consegna per approvarla.

### Invia solo messaggi con ponderazione più elevata {#sending-only-the-highest-weighted-messages}

Desideri inviare non più di 2 messaggi entro la stessa settimana, con un limite di 2 messaggi al giorno, a ciascuno dei tuoi destinatari e desideri che vengano consegnati solo i messaggi con pesi più elevati.

A questo scopo, devi pianificare diverse consegne con pesi diversi per lo stesso destinatario e applicare una regola di pressione per escludere le consegne con pesi inferiori.

Innanzitutto, configura la regola di pressione.

1. Crea una regola di pressione. Per ulteriori informazioni, consulta [Creare una regola di pressione](#creating-a-pressure-rule).
1. In **[!UICONTROL General]** seleziona la scheda **[!UICONTROL Re-apply the rule at the start of personalization]** opzione .

   ![](assets/campaign_opt_pressure_example_5.png)

   Questa opzione sovrascrive il valore definito nel **[!UICONTROL Frequency]** applica automaticamente la regola durante la fase di personalizzazione. Per ulteriori informazioni, consulta [Regola frequenza di calcolo](applying-rules.md#adjusting-calculation-frequency).

1. In **[!UICONTROL Pressure]** scheda , seleziona **[!UICONTROL 7d]** come **[!UICONTROL Period considered]** e **[!UICONTROL Grouping per day]** come **[!UICONTROL Period type]**.
1. Seleziona la **[!UICONTROL Take the deliveries into account in the provisional calendar]** per includere le consegne pianificate.

   ![](assets/campaign_opt_pressure_example_1.png)

   Nel calcolo verranno prese in considerazione le consegne inviate fino a 7 giorni prima della data di consegna e pianificate fino a 7 giorni dopo la data di consegna. Per ulteriori informazioni, consulta [Imposta il periodo](#setting-the-period).

   >[!AVAILABILITY]
   >Le consegne pianificate non possono essere prese in considerazione in Campaign v8.

1. In **[!UICONTROL Typologies]** , collega la regola a una tipologia di campagna.
1. Salva le modifiche.

Ora crea e configura un flusso di lavoro per ogni consegna su cui desideri applicare la regola di pressione.

1. Creare una campagna. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. In **[!UICONTROL Targeting and workflows]** scheda della campagna, aggiungi una **Query** al flusso di lavoro. Per ulteriori informazioni sull’utilizzo di questa attività, consulta [questa sezione](../../workflow/using/query.md).
1. Aggiungi un **[!UICONTROL Email delivery]** al flusso di lavoro e aprilo. Per ulteriori informazioni sull’utilizzo di questa attività, consulta [questa sezione](../../workflow/using/delivery.md).
1. Vai a **[!UICONTROL Approvals]** della scheda **[!UICONTROL Delivery properties]** e disattiva tutte le approvazioni.

   ![](assets/campaign_opt_pressure_example_2.png)

1. In **[!UICONTROL Typology]** della scheda **[!UICONTROL Delivery properties]**, fai riferimento alla tipologia della campagna su cui applicare la regola. Definire un peso per la consegna.

   ![](assets/campaign_opt_pressure_example_3.png)

1. Nella consegna, fai clic su **[!UICONTROL Scheduling]** e seleziona **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**. In questo esempio, seleziona la **[!UICONTROL Use a calculation formula]** opzione .
1. Imposta la data di estrazione su 10 minuti (data corrente + 10 minuti).
1. Imposta la data di contatto sul giorno successivo (data corrente + 1 giorno).

   ![](assets/campaign_opt_pressure_example_4.png)

   Affinché le esclusioni della regola di pressione siano implementate correttamente, assicurati di impostare la data e l’ora di estrazione prima della data e dell’ora di contatto, nonché prima che l’arbitrato notturno venga riapplicato. Per ulteriori informazioni, consulta [Esclusione dopo arbitrato](#exclusion-after-arbitration).

1. Deseleziona la **[!UICONTROL Confirm the delivery before sending]** e salva le modifiche.
1. Procedi in modo simile per ogni consegna che desideri inviare. Assicurati di impostare il peso desiderato per ogni consegna.
1. Esegui i flussi di lavoro pertinenti per preparare e inviare le consegne.

Quando viene applicato l&#39;arbitrato notturno, le consegne con i pesi più bassi per lo stesso destinatario saranno escluse. Per l’invio verranno considerate solo le consegne con il peso più elevato. Per ulteriori informazioni, consulta [Peso del messaggio](#message-weight).

Dato che un’e-mail è già stata inviata ai destinatari interessati all’inizio della settimana, la tabella seguente mostra un esempio delle configurazioni che possono essere applicate per altre due consegne.

<table> 
 <thead> 
  <tr> 
   <th> Consegna<br /> </th> 
   <th> Approvazioni<br /> </th> 
   <th> Peso<br /> </th> 
   <th> Data/ora di estrazione<br /> </th> 
   <th> Data di contatto<br /> </th> 
   <th> Data/ora di inizio consegna<br /> </th> 
   <th> Data/ora di esecuzione del flusso di lavoro arbitrato<br /> </th> 
   <th> Stato della consegna<br /> </th> 
   <th> Consegna inviata (data/ora)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Consegna 1<br /> </td> 
   <td> Disabilitato<br /> </td> 
   <td> 5<br /> </td> 
   <td> 3 del pomeriggio<br /> </td> 
   <td> 8 (giorno successivo)<br /> </td> 
   <td> 2 del pomeriggio<br /> </td> 
   <td> Notturno<br /> </td> 
   <td> Escluso<br /> </td> 
   <td> Escluso<br /> </td> 
  </tr> 
  <tr> 
   <td> Consegna 2<br /> </td> 
   <td> Disabilitato<br /> </td> 
   <td> 10<br /> </td> 
   <td> 4 del pomeriggio<br /> </td> 
   <td> 9 (giorno successivo)<br /> </td> 
   <td> 2 del pomeriggio<br /> </td> 
   <td> Notturno<br /> </td> 
   <td> Inviato<br /> </td> 
   <td> 9 (giorno successivo)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Dopo che la data di estrazione è passata per le due consegne, l’arbitrato notturno viene riapplicato prima delle date di contatto di entrambe le consegne. Questo consente di trovare tutte le consegne già inviate (destinatari per i quali una consegna viene elaborata, registrata tramite i registri generali) o pianificate per l’invio (destinatari idonei a ricevere una consegna, registrati tramite i registri di previsione).

Una volta che tutte le consegne inviate e potenziali sono state elencate per il periodo definito nella regola di pressione, Adobe Campaign le ordina per peso, con la ponderazione più alta per prima. Quando viene raggiunta la soglia impostata nella regola di pressione (in questo caso non più di 2 e-mail nella stessa settimana), i destinatari sono esclusi dalla consegna.
