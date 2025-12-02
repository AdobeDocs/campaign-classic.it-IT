---
product: campaign
title: Regole di pressione
description: Scopri come utilizzare le regole di pressione in Adobe Campaign
role: User, Developer
feature: Fatigue Management, Typology Rules, Campaigns
hide: true
hidefromtoc: true
exl-id: c23212f2-fdf8-4820-b389-546f7c84db27
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '3335'
ht-degree: 6%

---

# Regole di pressione{#pressure-rules}

## Informazioni sull’eccesso di marketing {#about-marketing-fatigue}

L’implementazione della gestione della pressione di vendita consente di evitare di sollecitare eccessivamente la popolazione nel database, nota anche come affaticamento del marketing. A questo scopo, puoi definire un numero massimo di messaggi per destinatario. Consente inoltre di implementare regole di arbitrato tra le campagne, per inviare il messaggio migliore al pubblico di destinazione.

**Regole di pressione**, per gestire l&#39;eccesso di marketing, ad esempio per limitare a due il numero di lettere da inviare a una popolazione, per selezionare la comunicazione che corrisponde meglio agli interessi di un gruppo di abbonati, per evitare di inviare un SMS a un cliente insoddisfatto e così via.

Le campagne vengono selezionate in base a soglie e peso del messaggio definiti.

* Una soglia è il numero più elevato di consegne autorizzate per un determinato destinatario in un determinato periodo. Può essere impostato o variabile. Viene impostata o calcolata nelle impostazioni delle regole di tipologia. Fai riferimento a [Numero massimo di messaggi](#maximum-number-of-messages).
* Il peso delle consegne consente di individuare le consegne prioritarie nel quadro della gestione della pressione. I messaggi con il peso maggiore hanno la priorità. Consulta [Peso del messaggio](#message-weight).

L’arbitrato consiste nell’assicurarsi che le campagne pianificate il cui peso è maggiore della campagna in corso non comportino un’eccessiva sollecitazione del profilo: in questo caso, il profilo viene escluso dalla consegna.

I criteri di arbitrato (peso del messaggio e/o soglia) possono variare in base a due tipi di informazioni:

* la preferenza del destinatario, che è un&#39;informazione dichiarativa: abbonamenti a newsletter, stato del destinatario (cliente o potenziale cliente),
* comportamento del destinatario: acquisti, collegamenti visitati, ecc.

La regola di arbitrato per la definizione dei messaggi idonei viene applicata durante la fase di analisi. Per ogni destinatario e per il periodo interessato, il messaggio verrà inviato se la formula seguente è vera: **(numero di messaggi inviati) + (numero di messaggi con un peso maggiore) &lt; soglia**.

In caso contrario, il destinatario sarà **[!UICONTROL Excluded by arbitration]**. Per ulteriori informazioni, consulta [Esclusione dopo arbitrato](#exclusion-after-arbitration).

## Creazione di una regola di pressione {#creating-a-pressure-rule}

Per impostare l&#39;arbitrato tra le campagne che utilizzano Adobe Campaign, inizia creando tipologie di campagna e definendo regole di tipologia collegate (**Regole di pressione**).

Per creare e configurare una regola di tipologia **[!UICONTROL Pressure]**, attieniti alla seguente procedura:

1. Nell&#39;elenco delle regole di tipologia della campagna, fai clic sull&#39;icona **[!UICONTROL New]** sopra l&#39;elenco.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. Nella scheda **[!UICONTROL General]** della nuova regola, seleziona una regola di tipo **Pressione** e immetti un nome e una descrizione per essa.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. Se necessario, modifica l’ordine di esecuzione. Quando più regole di tipologia vengono applicate come set **[!UICONTROL Typology]**, vengono applicate prima le regole ordinate inferiori. Per ulteriori informazioni, consulta [Ordine di esecuzione](applying-rules.md#execution-order).
1. Nella sezione **[!UICONTROL Calculation parameters]**, definisci una frequenza per salvare il targeting oltre la successiva esecuzione di un nuovo arbitraggio giornaliero. Per ulteriori informazioni, vedere [Regolazione della frequenza di calcolo](applying-rules.md#adjusting-calculation-frequency).
1. Fare clic sulla scheda **[!UICONTROL Pressure]** e scegliere il periodo del calendario durante il quale si applica la regola di tipologia.

   ![](assets/campaign_opt_create_a_rule_03.png)

   La regola verrà applicata alle consegne la cui data di contatto è inclusa nel periodo in questione.

   >[!NOTE]
   >
   >Le consegne pianificate vengono prese in considerazione solo se l&#39;opzione **[!UICONTROL Take the deliveries into account in the provisional calendar]** è selezionata. Per ulteriori informazioni, consulta [Impostazione del periodo](#setting-the-period).
   >

1. Definisci il metodo di calcolo del numero massimo di messaggi.

   La soglia rappresenta il numero massimo di messaggi che possono essere inviati a un destinatario durante il periodo in questione.

   Per impostazione predefinita, la soglia è costante e devi indicare un numero massimo di messaggi autorizzati dalla regola.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   Per definire una soglia di variabile, selezionare il valore **[!UICONTROL Depends on the recipient]** nel campo **[!UICONTROL Type of threshold]** e utilizzare l&#39;icona a destra per aprire l&#39;editor di espressioni.

   ![](assets/campaign_opt_create_a_rule_04.png)

   Per ulteriori informazioni, consulta [Numero massimo di messaggi](#maximum-number-of-messages).

1. Specifica il metodo di calcolo del peso della consegna.

   Ogni consegna ha un peso, ovvero un valore che rappresenta il suo livello di priorità: questo consente l’arbitraggio tra le campagne. I pesi vengono calcolati utilizzando la formula definita nella regola di tipologia e/o nelle relative proprietà. Per ulteriori informazioni, consulta [Peso del messaggio](#message-weight).

1. Per impostazione predefinita, tutti i messaggi vengono presi in considerazione per il calcolo della soglia. La scheda **[!UICONTROL Restriction]** consente di filtrare i messaggi interessati dalla regola di tipologia:

   * La sezione superiore di questa scheda ti consente di limitare i destinatari interessati.
   * La sezione inferiore di questa scheda ti consente di filtrare i messaggi da conteggiare.

     Nell&#39;esempio seguente, vengono presi in considerazione solo i destinatari salvati nella cartella **NewContacts** e le consegne che iniziano con **Newsletter** sono interessate.

   ![](assets/campaign_opt_create_a_rule_05.png)

1. La scheda **[!UICONTROL Typologies]** ti consente di visualizzare le tipologie di campagne che applicano questa regola o di collegare la regola a una o più tipologie esistenti. Consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=it){target="_blank"}.

## Definizione di soglie e pesi {#defining-thresholds-and-weights}

### Numero massimo di messaggi {#maximum-number-of-messages}

Ogni regola di pressione definisce una soglia, ovvero il numero massimo di messaggi che possono essere inviati a un destinatario in un determinato periodo di tempo. Una volta raggiunta tale soglia, non potranno più essere effettuate ulteriori consegne fino alla fine del periodo considerato. Questo processo ti consente di escludere automaticamente un destinatario da una consegna se un messaggio supera la soglia impostata, evitando in tal modo una sollecitazione eccessiva.

I valori di soglia possono essere costanti o calcolati tramite una formula con variabili. Ciò significa che, per un dato periodo, le soglie possono variare da un destinatario all’altro, o anche per lo stesso destinatario.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>L&#39;immissione di **0** come soglia impedisce tutte le consegne alla popolazione target durante il periodo considerato.

**Esempio:**

Puoi indicizzare il numero di messaggi autorizzati in base al segmento a cui appartiene il destinatario. Ciò significa che un destinatario appartenente al segmento web può ricevere più messaggi di altri destinatari. Una formula di tipo **[!UICONTROL Iif (@origin='Web', 5, 3)]** autorizza la consegna di 5 messaggi ai destinatari e di 3 per altri segmenti. La configurazione sarà la seguente:

![](assets/campaign_opt_pressure_sample.png)

Per definire la soglia, puoi utilizzare una dimensione collegata alla dimensione di targeting: ad esempio, per includere i messaggi inviati ai profili dei destinatari memorizzati nella tabella dei visitatori (per ulteriori informazioni sulla tabella dei visitatori, consulta [questa sezione](../../surveys/using/use-case-creating-a-refer-a-friend-form.md)) o per evitare di inviare più di un messaggio alla settimana alla stessa famiglia (che può fare riferimento a più indirizzi e-mail) identificata in una dimensione collegata a quella dei destinatari.

A tale scopo, selezionare l&#39;opzione **[!UICONTROL Count messages on a linked dimension]**, quindi selezionare il visitatore o la tabella dei contatti.

### Peso del messaggio {#message-weight}

Ogni consegna ha un peso che rappresenta il suo livello di priorità. Per impostazione predefinita, il peso di una consegna è impostato su 5. Le regole di pressione ti consentono di definire il peso delle consegne a cui verranno applicate.

I pesi possono essere impostati o calcolati tramite una formula adatta ai destinatari. Ad esempio, puoi definire il peso di una consegna in base agli interessi dei destinatari.

>[!CAUTION]
>
>Il peso definito in una regola di tipologia può essere sovraccaricato singolarmente per ogni consegna, nella scheda **[!UICONTROL Properties]**. Fare clic sulla scheda **[!UICONTROL Typology]** per selezionare la tipologia della campagna e, se necessario, specificare lo spessore da applicare.\
>Tuttavia, il peso dichiarato in una regola di tipologia A non verrà utilizzato per calcolare una regola di tipologia B: questo peso riguarderà solo le consegne che utilizzano la regola A.

**Esempio:**

Nell’esempio seguente, vogliamo collegare il peso delle newsletter sulla musica al punteggio di tendenza dei destinatari. Per eseguire questa operazione:

1. Crea un nuovo campo per memorizzare i punteggi di tendenza dei destinatari. Il campo, **@Music** in questo caso, verrà arricchito con risposte a sondaggi e sondaggi online, dati di tracciamento raccolti e così via.
1. Crea una regola di tipologia per calcolare il peso del messaggio in base a questo campo.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. Applica questa regola ai messaggi con il seguente argomento: newsletter, offerte speciali, ecc. Il peso di queste consegne, e quindi il loro livello di priorità, dipenderà dal punteggio di propensione di ogni destinatario.

## Imposta il periodo {#setting-the-period}

Le regole di pressione sono definite in periodi continui di **n** giorni.

Il periodo è configurato nella scheda **[!UICONTROL Pressure]** della regola. Puoi specificare il numero di giorni e, se necessario, selezionare il tipo di raggruppamento da applicare (giorno, settimana, mese, trimestre, ecc.).

Il tipo di raggruppamento consente di estendere il campo **[!UICONTROL Period considered]** all&#39;intero giorno, alla settimana del calendario, al mese del calendario o all&#39;anno del calendario per le date del periodo.

Ad esempio, una regola di pressione che definisce una soglia di 2 messaggi alla settimana, con un raggruppamento per ogni mese di calendario, impedirà la consegna di più di 2 messaggi nella stessa settimana E nello stesso mese di calendario. Attenzione, se il periodo si sovrappone di due mesi, la soglia di calcolo terrà conto delle consegne di questi due mesi di calendario e potrebbe quindi impedire tutte le nuove consegne durante il secondo mese.

Per impostazione predefinita, nel calcolo della soglia vengono prese in considerazione solo le consegne già inviate. In Campaign Classic v7, seleziona l’opzione **[!UICONTROL Take the deliveries into account in the provisional calendar]** se desideri considerare anche le consegne pianificate per il periodo in questione. In questo caso, il periodo considerato è raddoppiato per consentire l’integrazione delle consegne future e di quelle precedenti.

Per limitare le consegne prese in considerazione a un periodo di 2 settimane, puoi effettuare le seguenti operazioni:

1. Immetti **15d** nel campo **[!UICONTROL Concerned period]**: le consegne inviate fino a due settimane prima della data della consegna a cui viene applicata la regola verranno prese in considerazione nel calcolo,

o

1. Immetti **7d** nel campo **[!UICONTROL Period considered]** E seleziona l&#39;opzione **[!UICONTROL Take the deliveries into account in the provisional calendar]**: nel calcolo verranno prese in considerazione le consegne inviate fino a 7 giorni prima della data di consegna e pianificate fino a 7 giorni dopo la data di consegna in cui viene applicata la regola.

La data di inizio del periodo dipende dalla configurazione del database.

Ad esempio, se applichi una regola di pressione di 15 giorni senza raggruppamento a una consegna dell’11/12, le consegne verranno prese in considerazione tra il 27/11 e il 12/12. Se la regola della pressione prende in considerazione le consegne nel calendario provvisorio, saranno prese in considerazione tutte le consegne programmate tra il 27/11 e il 27/12. Infine, se nella regola configuri un raggruppamento per mese di calendario, per calcolare la soglia verranno prese in considerazione tutte le consegne di novembre e dicembre (dall’11/1 al 12/31).


**Casi frequenti**

Per evitare che le consegne per la settimana di calendario corrente vengano prese in considerazione, oltre a non rischiare di prendere in considerazione anche quelle della settimana precedente per la soglia di calcolo, specifica **[!UICONTROL Period considered]** su &#39;0&#39; e seleziona &#39;Raggruppamento per settimana di calendario&#39; come **[!UICONTROL Period type]**.

Quando un periodo è superiore a 0 (ad esempio, 1), la soglia di calcolo può tenere conto delle consegne del giorno precedente. Pertanto, se il giorno precedente corrisponde alla settimana di calendario precedente e il tipo di periodo selezionato è &quot;Raggruppamento per settimana di calendario&quot;, per la soglia di calcolo verrà presa in considerazione tutta la settimana precedente.

**Esempio:**

Vogliamo creare una regola di pressione che limiti la richiesta a 3 messaggi per periodo di 2 settimane, con un raggruppamento per il mese di calendario.

![](assets/campaign_opt_pressure_period_sample_1a.png)

Prendiamo 6 newsletter con lo stesso peso, in programma per il 30/05/06, 3/06, 8/06, 12/06/06 e 22/06/30.

![](assets/campaign_opt_pressure_period_sample_0.png)

Le consegne programmate per il 12 e il 30 giugno non saranno inviate: la consegna 06/12 supererebbe la soglia di 3 messaggi per periodo di 2 settimane e la consegna 30 supererebbe la soglia di comunicazioni autorizzate per mese di calendario.

![](assets/campaign_opt_pressure_period_sample_1.png)

Tutti i destinatari di queste consegne sono esclusi per arbitrato durante la fase di analisi:

![](assets/campaign_opt_pressure_period_sample_2.png)

Per la stessa regola, se raggruppi le consegne per trimestre, verranno esclusi anche i destinatari della **newsletter n. 5** e non verranno inviati.

Infine, se non è selezionato alcun raggruppamento, non verrà inviata solo la **newsletter n. 4**, poiché è stata pianificata per lo stesso periodo di 2 settimane delle prime tre newsletter.

>[!NOTE]
>
>Quando modifichi la definizione di una regola di tipologia, puoi creare una **simulazione** per controllarne l&#39;impatto sulle consegne a cui viene applicata e monitorare l&#39;impatto reciproco delle consegne. Per ulteriori informazioni, consulta [Simulazioni campagna](campaign-simulations.md).

## Esclusione dopo arbitrato {#exclusion-after-arbitration}

L&#39;arbitrato viene riapplicato ogni notte tramite il flusso di lavoro tecnico **[!UICONTROL Forecasting]** e il flusso di lavoro **[!UICONTROL Campaign jobs]**.

Il flusso di lavoro **[!UICONTROL Forecasting]** calcola anticipatamente i dati per il periodo in corso (dalla data di inizio alla data corrente), consentendo l&#39;applicazione delle regole di tipologia durante l&#39;analisi. Inoltre, ricalcola ogni notte i contatori di esclusione per l&#39;arbitrato.

Pertanto, per ciascun destinatario, Adobe Campaign controlla che il numero di messaggi da inviare non superi la soglia, tenendo conto del numero di messaggi già inviati per il periodo in questione. Queste informazioni sono un **indicatore**, poiché tutti i calcoli vengono aggiornati al momento della consegna.

Se questo numero supera la soglia, vengono applicate le regole di arbitrato definite nella tipologia della campagna e i destinatari vengono esclusi dalle campagne con un peso inferiore.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>Se più consegne hanno lo stesso punteggio, verrà inviata la campagna pianificata per la data più vicina.

## Casi d’uso sulle regole di pressione {#use-cases-on-pressure-rules}

### Adattare la soglia in base al criterio {#adapting-the-threshold-based-on-criterion}

Vogliamo creare una regola di tipologia per impedire la consegna di più di 4 messaggi alla settimana ai clienti e di 2 messaggi alla settimana ai potenziali clienti.

Per identificare clienti e potenziali clienti, utilizzare il campo **[!UICONTROL Status]**, che contiene 0 per i potenziali clienti e 1 per i clienti.

Per creare la regola, esegui i seguenti passaggi:

1. Crea una nuova regola di tipologia di tipo **Pressione**.
1. Modifica la scheda **[!UICONTROL Pressure]**: nella sezione **[!UICONTROL Maximum number of messages]**, vogliamo creare una formula per calcolare la soglia in base a ciascun destinatario. Selezionare il valore **[!UICONTROL Depends on the recipient]** nel campo **[!UICONTROL Threshold type]**, quindi fare clic su **[!UICONTROL Edit expression]** a destra del campo **[!UICONTROL Formula]**.

   Fare clic sul pulsante **[!UICONTROL Advanced parameters]** per definire la formula di calcolo.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Selezionare l&#39;opzione **[!UICONTROL Edit the formula using an expression]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. Nell&#39;elenco delle funzioni fare doppio clic sulla funzione **Iif** nel nodo **[!UICONTROL Others]**.

   Quindi seleziona lo **Stato** dei destinatari nella sezione **[!UICONTROL Available fields]**.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   Immettere la formula seguente: **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   Questa formula ti consente di assegnare il valore 2 se lo stato è uguale a 0 e il valore 4 per tutti gli altri stati.

   Fai clic su **[!UICONTROL Finish]** per approvare la formula.

1. Indica il periodo durante il quale la regola verrà applicata: 7 giorni in questo caso, per contare il numero di messaggi alla settimana.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. Salva la regola per approvare la creazione.

Collega ora la regola appena creata a una tipologia per applicarla alle consegne. Per eseguire questa operazione:

1. Creare una tipologia di campagna.
1. Vai alla scheda **[!UICONTROL Rules]**, fai clic sul pulsante **[!UICONTROL Add]** e seleziona la regola appena creata.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Salva la tipologia: viene aggiunta all’elenco delle tipologie esistenti.

Per utilizzare questa tipologia nelle consegne, selezionala nelle proprietà di consegna, nella scheda **[!UICONTROL Typology]** come illustrato di seguito:

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>La tipologia può essere definita nel modello di consegna, da applicare automaticamente a tutte le consegne create utilizzando questo modello.

Durante l’analisi della consegna, i destinatari della consegna sono esclusi dalla consegna se applicabile, in base al numero di consegne già inviate. Per visualizzare queste informazioni, puoi effettuare le seguenti operazioni:

* Visualizzare il risultato dell&#39;analisi:

  ![](assets/campaign_opt_pressure_sample_1_8.png)

* Modifica la consegna e fai clic sulle schede **[!UICONTROL Delivery]** e **[!UICONTROL Exclusions]**:

  ![](assets/campaign_opt_pressure_sample_1_9.png)

* Fai clic sulla scheda **[!UICONTROL Audit]**, quindi sulla scheda secondaria **[!UICONTROL Causes of exclusions]** per visualizzare il numero di esclusioni e le regole di tipologia applicate:

  ![](assets/campaign_opt_pressure_sample_1_10.png)

### Calcolare il peso della consegna in base al comportamento {#calculating-the-delivery-weight-based-on-behavior}

Puoi definire regole di pressione in base al comportamento del destinatario: pertanto, il peso di una consegna può adattarsi a criteri che variano da un destinatario all’altro. Ad esempio, puoi decidere di inviare un messaggio a seconda che un destinatario abbia visitato o meno il tuo sito Internet, abbia fatto clic in una sezione specifica dell’ultima newsletter, sia abbonato a un servizio di informazioni o anche in base alle risposte a un sondaggio, a un gioco online e così via.

Nell’esempio seguente, vogliamo creare una consegna con un peso di 5. Questo peso è arricchito dai punteggi di tendenza basati sul comportamento del destinatario: i clienti che hanno già ordinato da questo sito avranno un punteggio di 5, mentre i clienti che non hanno mai ordinato online avranno un punteggio di 4.

Per eseguire questo tipo di configurazione, è necessario utilizzare una formula per definire il peso del messaggio. Le informazioni sui punteggi di tendenza e sulle risposte ai sondaggi devono essere accessibili nel modello di dati. Nel nostro esempio, il campo **Propensione** è stato aggiunto.

Applica i seguenti passaggi di configurazione:

1. Crea una nuova regola di tipologia di tipo **Pressione**.
1. Modificare la scheda **[!UICONTROL Pressure]**. Si desidera creare una formula di soglia basata su ogni singolo destinatario: fare clic sull&#39;icona **[!UICONTROL Edit expression]** a destra del campo **[!UICONTROL Weight formula]**.

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. Per impostazione predefinita, il valore **5** è visualizzato nella sezione superiore dell&#39;editor espressioni. Si desidera aggiungere il punteggio tendenza di ogni destinatario a questo peso: posizionare il cursore a destra del 5, immettere il carattere **+** e selezionare il campo **Propensione**.

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. Quindi aggiungi un valore più alto per i destinatari che hanno già effettuato un acquisto. Per loro, il peso della consegna deve essere aumentato di 5, mentre per altri aumenta solo di 4.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. Fare clic su **[!UICONTROL Finish]** per salvare la regola.
1. Collega la regola a una tipologia di campagna e fai riferimento a tale tipologia in una consegna per approvarla.

### Invia solo i messaggi con la ponderazione più alta {#sending-only-the-highest-weighted-messages}

Desideri inviare non più di 2 messaggi nella stessa settimana, con un limite di 2 messaggi al giorno, a ciascuno dei destinatari e desideri solo recapitare i messaggi con un peso maggiore.

A questo scopo, devi pianificare diverse consegne con pesi diversi per lo stesso destinatario e applicare una regola di pressione per escludere le consegne con pesi inferiori.

Innanzitutto, configura la regola di pressione.

1. Creare una regola di pressione. Per ulteriori informazioni, consulta [Creare una regola di pressione](#creating-a-pressure-rule).
1. Nella scheda **[!UICONTROL General]**, selezionare l&#39;opzione **[!UICONTROL Re-apply the rule at the start of personalization]**.

   ![](assets/campaign_opt_pressure_example_5.png)

   Questa opzione sostituisce il valore definito nel campo **[!UICONTROL Frequency]** e applica automaticamente la regola durante la fase di personalizzazione. Per ulteriori informazioni, consulta [Regolare la frequenza di calcolo](applying-rules.md#adjusting-calculation-frequency).

1. Nella scheda **[!UICONTROL Pressure]**, selezionare **[!UICONTROL 7d]** come **[!UICONTROL Period considered]** e **[!UICONTROL Grouping per day]** come **[!UICONTROL Period type]**.
1. Selezionare l&#39;opzione **[!UICONTROL Take the deliveries into account in the provisional calendar]** per includere le consegne pianificate.

   ![](assets/campaign_opt_pressure_example_1.png)

   Le consegne inviate fino a 7 giorni prima della data di consegna e pianificate fino a 7 giorni dopo la data di consegna verranno prese in considerazione nel calcolo. Per ulteriori informazioni, consulta [Imposta il periodo](#setting-the-period).

1. Nella scheda **[!UICONTROL Typologies]**, collega la regola a una tipologia di campagna.
1. Salva le modifiche.

Ora crea e configura un flusso di lavoro per ogni consegna a cui desideri applicare la regola di pressione.

1. Creare una campagna. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. Nella scheda **[!UICONTROL Targeting and workflows]** della campagna, aggiungi un&#39;attività **Query** al flusso di lavoro. Per ulteriori informazioni sull&#39;utilizzo di questa attività, consulta [questa sezione](../../workflow/using/query.md).
1. Aggiungere un&#39;attività **[!UICONTROL Email delivery]** al flusso di lavoro e aprirla. Per ulteriori informazioni sull&#39;utilizzo di questa attività, consulta [questa sezione](../../workflow/using/delivery.md).
1. Vai alla scheda **[!UICONTROL Approvals]** di **[!UICONTROL Delivery properties]** e disabilita tutte le approvazioni.

   ![](assets/campaign_opt_pressure_example_2.png)

1. Nella scheda **[!UICONTROL Typology]** di **[!UICONTROL Delivery properties]**, fai riferimento alla tipologia di campagna su cui applicare la regola. Definisci un peso per la consegna.

   ![](assets/campaign_opt_pressure_example_3.png)

1. Nella consegna, fai clic su **[!UICONTROL Scheduling]** e seleziona **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**. In questo esempio, selezionare l&#39;opzione **[!UICONTROL Use a calculation formula]**.
1. Imposta la data di estrazione su 10 minuti (data corrente + 10 minuti).
1. Impostare la data di contatto sul giorno successivo (data corrente + 1 giorno).

   ![](assets/campaign_opt_pressure_example_4.png)

   Per implementare correttamente le esclusioni della regola di pressione, assicurati di impostare la data e l’ora di estrazione prima della data e dell’ora di contatto, nonché prima di riapplicare l’arbitrato notturno. Per ulteriori informazioni, consulta [Esclusione dopo arbitrato](#exclusion-after-arbitration).

1. Deseleziona l&#39;opzione **[!UICONTROL Confirm the delivery before sending]** e salva le modifiche.
1. Procedi in modo simile per ogni consegna che desideri inviare. Assicurati di impostare il peso desiderato per ogni consegna.
1. Esegui i flussi di lavoro pertinenti per preparare e inviare le consegne.

Quando l&#39;arbitrato notturno è applicato, le consegne con i pesi inferiori per lo stesso destinatario saranno escluse. Per l’invio verranno considerate solo le consegne con il peso più alto. Per ulteriori informazioni, consulta [Peso del messaggio](#message-weight).

Considerando che un’e-mail è già stata inviata ai destinatari interessati in precedenza durante la settimana, la tabella seguente mostra un esempio delle configurazioni che possono essere applicate per altre due consegne.

<table> 
 <thead> 
  <tr> 
   <th> Consegna<br /> </th> 
   <th> Approvazioni<br /> </th> 
   <th> Peso<br /> </th> 
   <th> Data/ora di estrazione<br /> </th> 
   <th> Data di contatto<br /> </th> 
   <th> Data/ora di inizio consegna<br /> </th> 
   <th> Data/ora di esecuzione del flusso di lavoro di arbitrato<br /> </th> 
   <th> Stato consegna<br /> </th> 
   <th> Consegna inviata (data/ora)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Consegna 1<br /> </td> 
   <td> Disabilitato<br /> </td> 
   <td> 5<br /> </td> 
   <td> 15:00<br /> </td> 
   <td> 8 (giorno successivo)<br /> </td> 
   <td> 14:00<br /> </td> 
   <td> Notte<br /> </td> 
   <td> Escluso<br /> </td> 
   <td> Escluso<br /> </td> 
  </tr> 
  <tr> 
   <td> Consegna 2<br /> </td> 
   <td> Disabilitato<br /> </td> 
   <td> 10<br /> </td> 
   <td> 16:00<br /> </td> 
   <td> 09:00 (giorno successivo)<br /> </td> 
   <td> 14:00<br /> </td> 
   <td> Notte<br /> </td> 
   <td> Inviato<br /> </td> 
   <td> 09:00 (giorno successivo)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Dopo che la data di estrazione è passata per le due consegne, l&#39;arbitrato notturno viene riapplicato prima delle date di contatto di entrambe le consegne. Questo consente di trovare tutte le consegne già inviate (destinatari per i quali viene elaborata una consegna, registrate nei registri ampi) o pianificate per l’invio (destinatari idonei a ricevere una consegna, registrati nei registri di previsione).

Una volta elencate tutte le consegne inviate e potenziali per il periodo definito nella regola di pressione, Adobe Campaign le ordina in base al peso, con la prima ponderata più alta. Quando viene raggiunta la soglia impostata nella regola di pressione (in questo caso non più di 2 e-mail nella stessa settimana), i destinatari vengono esclusi dalla consegna.
