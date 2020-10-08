---
title: Regole di pressione
seo-title: Regole di pressione
description: Regole di pressione
seo-description: null
page-status-flag: never-activated
uuid: 653d8336-8765-4938-88c1-a96cd76c3b7e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 3710768e-ab7f-40a4-9c48-830695adc990
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '3255'
ht-degree: 4%

---


# Regole di pressione{#pressure-rules}

## La fatica del marketing {#about-marketing-fatigue}

L&#39;implementazione della gestione della pressione di vendita consente di evitare l&#39;eccesso di sollecitazione della popolazione nel database, noto anche come affaticamento del marketing. A tal fine, puoi definire un numero massimo di messaggi per destinatario. Consente inoltre di implementare regole di arbitrato tra campagne, per inviare il messaggio migliore al pubblico di destinazione.

**Regole di pressione** , per gestire la stanchezza di marketing, ad esempio, per limitare il numero di lettere da inviare a una popolazione a due, per selezionare la comunicazione che meglio corrisponde agli interessi di un gruppo di abbonati, per evitare di inviare un SMS a un cliente insoddisfatto, ecc.

Le campagne vengono selezionate in base a soglie definite e allo spessore del messaggio.

* Una soglia è il numero massimo di consegne autorizzate per un dato destinatario in un dato periodo. Può essere impostata o variabile. Viene impostato o calcolato nelle impostazioni delle regole di tipologia. Fare riferimento al numero [massimo di messaggi](#maximum-number-of-messages).
* I pesi di distribuzione consentono di identificare le consegne prioritarie nel quadro della gestione della pressione. I messaggi con lo spessore maggiore hanno la priorità. Fare riferimento a Spessore [](#message-weight)messaggio.

L&#39;arbitrato consiste nel fare in modo che le campagne pianificate il cui peso sia maggiore della campagna in corso non portino a un&#39;eccessiva richiesta di profilo: in questo caso, il profilo viene escluso dalla consegna.

I criteri di arbitraggio (spessore e/o soglia del messaggio) possono variare in base a due tipi di informazioni:

* preferenza del destinatario, che è informazione dichiarativa: abbonamenti a newsletter, stato del destinatario (cliente o potenziale),
* comportamento del destinatario: acquisti, collegamenti visitati, ecc.

La regola di arbitrato per la definizione dei messaggi idonei viene applicata durante la fase di analisi. Per ciascun destinatario e per il periodo in questione, il messaggio verrà inviato se la formula seguente è vera: **(numero di messaggi inviati) + (numero di messaggi con maggior peso) &lt; soglia**.

In caso contrario, il destinatario sarà **[!UICONTROL Excluded by arbitration]**. Per ulteriori informazioni, consulta [Esclusione dopo l&#39;arbitrato](#exclusion-after-arbitration).

## Creating a pressure rule {#creating-a-pressure-rule}

Per impostare l&#39;arbitrato tra le campagne che utilizzano  Adobe Campaign, iniziare creando tipologie di campagne e definendo regole di tipologia collegate (regole di **pressione** ).

Per creare e configurare una regola di tipologia **[!UICONTROL Pressure]**, attieniti alla seguente procedura:

1. Nell&#39;elenco delle regole di tipologia della campagna, fai clic sull&#39; **[!UICONTROL New]** icona sopra l&#39;elenco.

   ![](assets/campaign_opt_create_a_rule_01.png)

1. Nella **[!UICONTROL General]** scheda della nuova regola, selezionare una regola di tipo **Pressione** e immettere un nome e una descrizione per tale regola.

   ![](assets/campaign_opt_create_a_rule_02.png)

1. Se necessario, modificate l&#39;ordine di esecuzione. Quando più regole di tipologia vengono applicate come **[!UICONTROL Typology]** set, le regole di ordine inferiore vengono applicate per prime. For more on this, refer to [Execution order](../../campaign/using/applying-rules.md#execution-order).
1. Nella **[!UICONTROL Calculation parameters]** sezione, definite una frequenza se desiderate salvare il targeting oltre la successiva esecuzione di ri-arbitraggio giornaliera. Per ulteriori informazioni, vedere [Regolazione della frequenza](../../campaign/using/applying-rules.md#adjusting-calculation-frequency)di calcolo.
1. Fare clic sulla **[!UICONTROL Pressure]** scheda e scegliere il periodo di calendario durante il quale si applica la regola di tipologia.

   ![](assets/campaign_opt_create_a_rule_03.png)

   La regola sarà applicata alle consegne la cui data di contatto è inclusa nel periodo in questione.

   >[!NOTE]
   >
   >Le consegne programmate vengono prese in considerazione solo se l&#39; **[!UICONTROL Take the deliveries into account in the provisional calendar]** opzione è selezionata. For more on this, refer to [Setting the period](#setting-the-period).

1. Definire il metodo per il calcolo del numero massimo di messaggi.

   La soglia rappresenta il numero più alto di messaggi che possono essere inviati a un destinatario durante il periodo in questione.

   Per impostazione predefinita, la soglia è costante e devi indicare un numero massimo di messaggi autorizzati dalla regola.

   ![](assets/campaign_opt_create_a_rule_03b.png)

   Per definire una soglia di variabile, selezionate il **[!UICONTROL Depends on the recipient]** valore nel **[!UICONTROL Type of threshold]** campo e utilizzate l&#39;icona a destra per aprire l&#39;editor di espressioni.

   ![](assets/campaign_opt_create_a_rule_04.png)

   Per ulteriori informazioni, vedere [Numero massimo di messaggi](#maximum-number-of-messages).

1. Specificare il metodo per il calcolo del peso della consegna.

   Ogni consegna ha un peso, ovvero un valore che rappresenta il suo livello di priorità: questo consente l&#39;arbitrato tra le campagne. I pesi vengono calcolati utilizzando la formula definita nella regola di tipologia e/o nelle relative proprietà. For more on this, refer to [Message weight](#message-weight).

1. Per impostazione predefinita, tutti i messaggi vengono presi in considerazione per il calcolo della soglia. La **[!UICONTROL Restriction]** scheda consente di filtrare i messaggi interessati dalla regola di tipologia:

   * La sezione superiore di questa scheda consente di limitare i destinatari interessati.
   * La sezione inferiore di questa scheda consente di filtrare i messaggi da conteggiare.

      Nell’esempio seguente, vengono presi in considerazione solo i destinatari salvati nella cartella **NewContatti** , mentre per le consegne che iniziano con **Newsletter** .
   ![](assets/campaign_opt_create_a_rule_05.png)

1. La **[!UICONTROL Typologies]** scheda consente di visualizzare i tipi di campagna che applicano questa regola o di collegare la regola a uno o più tipi esistenti. For more on this, refer to [Applying typologies](../../campaign/using/about-campaign-typologies.md#applying-typologies).

## Definizione di soglie e pesi {#defining-thresholds-and-weights}

### Numero massimo di messaggi {#maximum-number-of-messages}

Ogni regola di pressione definisce una soglia, ovvero il numero massimo di messaggi che possono essere inviati a un destinatario in un dato periodo di tempo. Una volta raggiunta tale soglia, non potranno più essere effettuate ulteriori consegne fino alla fine del periodo considerato. Questa procedura consente di escludere automaticamente un destinatario da una consegna se un messaggio supera la soglia impostata, evitando in tal modo un eccesso di richieste.

I valori di soglia possono essere costanti o calcolati da una formula con variabili. Ciò significa che per un determinato periodo, le soglie possono variare da un destinatario all&#39;altro, o persino per lo stesso destinatario.

![](assets/campaign_opt_create_a_rule_threshold.png)

>[!CAUTION]
>
>L&#39;inserimento di **0** come soglia impedisce tutte le consegne alla popolazione bersaglio durante il periodo in esame.

**Esempio:**

Puoi indicizzare il numero di messaggi autorizzati in base al segmento a cui appartiene il destinatario. Ciò significa che un destinatario appartenente al segmento Web può ricevere più messaggi di altri destinatari. Una formula **[!UICONTROL Iif (@origin='Web', 5, 3)]** di tipo autorizza la consegna di 5 messaggi ai destinatari e 3 per altri segmenti. La configurazione sarà la seguente:

![](assets/campaign_opt_pressure_sample.png)

Per definire la soglia, potete utilizzare una dimensione collegata alla dimensione di targeting: ad esempio, per includere i messaggi inviati ai profili dei destinatari memorizzati nella tabella dei visitatori (per ulteriori informazioni sulla tabella dei visitatori, consultare [questa sezione](../../web/using/use-case--creating-a-refer-a-friend-form.md)) o per evitare di inviare più messaggi alla settimana alla stessa famiglia (che possono fare riferimento a più indirizzi e-mail) identificati in una dimensione collegata a quella dei destinatari.

A tal fine, selezionate l&#39; **[!UICONTROL Count messages on a linked dimension]** opzione, quindi selezionate il visitatore o la tabella dei contatti.

### Spessore messaggio {#message-weight}

Ogni consegna ha un peso che rappresenta il suo livello di priorità. Per impostazione predefinita, il peso di una consegna è impostato su 5. Le regole di pressione consentono di definire il peso delle consegne a cui verranno applicate.

I pesi possono essere impostati o calcolati utilizzando una formula in base alle esigenze dei destinatari. Ad esempio, puoi definire il peso di una consegna in base agli interessi dei destinatari.

>[!CAUTION]
>
>Lo spessore definito in una regola di tipologia può essere sovraccaricato singolarmente per ogni consegna, nella **[!UICONTROL Properties]** scheda. Fate clic sulla **[!UICONTROL Typology]** scheda per selezionare il tipo di campagna e, se necessario, specificate il peso da applicare.\
>Tuttavia, il peso dichiarato in una regola di tipologia A non sarà utilizzato per calcolare una regola di tipologia B: questo peso riguarda solo le consegne che utilizzano la regola A.

**Esempio:**

Nell&#39;esempio seguente, vogliamo collegare il peso delle newsletter sulla musica al punteggio di propensione dei destinatari. Per eseguire questa operazione:

1. Crea un nuovo campo per memorizzare i punteggi di propensione dei destinatari. Il campo, **@Music** in questo caso, sarà arricchito di risposte a sondaggi e sondaggi online, dati di tracciamento raccolti, ecc.
1. Crea una regola di tipologia per calcolare lo spessore del messaggio in base a questo campo.

   ![](assets/campaign_opt_pressure_weight_sample.png)

1. Applica questa regola ai messaggi con il seguente argomento: newsletter, offerte speciali, ecc. Il peso di queste consegne, e quindi il loro livello di priorità, dipenderà dal punteggio di propensione di ciascun destinatario.

## Setting the period {#setting-the-period}

Le regole di pressione sono definite nei periodi **giornalieri**.

Il punto è configurato nella **[!UICONTROL Pressure]** scheda della regola. Potete specificare il numero di giorni e, se necessario, selezionare il tipo di raggruppamento da applicare (giorno, settimana, mese, trimestre ecc.).

Il tipo di raggruppamento consente di estendere il **[!UICONTROL Period considered]** campo all’intero giorno, alla settimana, al mese di calendario o all’anno di calendario per le date del periodo.

Ad esempio, una regola di pressione che definisce una soglia di 2 messaggi alla settimana, con un raggruppamento per ogni mese di calendario, impedirà la consegna di più di 2 messaggi entro la stessa settimana e nello stesso mese di calendario. Avvertenza: se il periodo si sovrappone a due mesi, la soglia di calcolo terrà conto delle consegne di questi due mesi di calendario e potrebbe pertanto impedire tutte le nuove consegne nel corso del secondo mese.

>[!NOTE]
>
>Per impostazione predefinita, nel calcolo della soglia vengono prese in considerazione solo le consegne già inviate. Selezionare l&#39; **[!UICONTROL Take the deliveries into account in the provisional calendar]** opzione se si desidera anche considerare le consegne programmate per il periodo in questione. In questo caso, il periodo considerato è raddoppiato per consentire l&#39;integrazione delle consegne future e di quelle precedenti.\
>Per limitare le consegne prese in considerazione a un periodo di 2 settimane, potete:
>
>* Immettere **15d** nel **[!UICONTROL Concerned period]** campo: le consegne inviate fino a due settimane prima della data di consegna cui si applica la regola saranno prese in considerazione nel calcolo,
>
>  
o
>
>* Immettere **7d** nel **[!UICONTROL Period considered]** campo E controllare il **[!UICONTROL Take the deliveries into account in the provisional calendar]**\
   >opzione: le consegne inviate fino a 7 giorni prima della data di consegna e programmate fino a 7 giorni dopo la data di consegna alla quale si applica la regola saranno prese in considerazione nel calcolo.
>
>
La data di inizio del periodo dipende dalla configurazione del database.

Ad esempio, se si applica una regola di pressione di 15 giorni senza raggruppamento a una consegna datata 12/11, le consegne saranno prese in considerazione tra 11/27 e 12/12. Se la regola della pressione tiene conto delle consegne nel calendario provvisorio, si terrà conto di tutte le consegne previste tra l&#39;11/27 e il 12/27. Infine, se configurate un raggruppamento per mese di calendario nella regola, tutte le consegne in novembre e dicembre saranno prese in considerazione per il calcolo della soglia (da 11/1 a 12/31).

>[!CAUTION]
>
>**Casi frequenti**
>Per garantire che le consegne per la settimana di calendario corrente non siano prese in considerazione, e per non rischiare anche tenendo conto di quelle della settimana precedente per la soglia di calcolo, specificate il **[!UICONTROL Period considered]** valore &quot;0&quot; e selezionate &quot;Raggruppamento per settimana di calendario&quot; come **[!UICONTROL Period type]**.
> 
>Quando un periodo è superiore a 0 (ad esempio 1), la soglia di calcolo può tenere conto delle consegne del giorno precedente. Pertanto, se il giorno precedente corrisponde alla settimana di calendario precedente e il tipo di periodo selezionato è &quot;Raggruppamento per settimana di calendario&quot;, per la soglia di calcolo verrà presa in considerazione tutta la settimana precedente.

**Esempio:**

Vogliamo creare una regola di pressione che limiti l&#39;offerta a 3 messaggi per ogni periodo di 2 settimane, con un raggruppamento per il mese di calendario.

![](assets/campaign_opt_pressure_period_sample_1a.png)

Prendiamo 6 newsletter con lo stesso peso, in programma per il 30/05, 06/3, 06/8, 06/12, 06/22 e 06/30.

![](assets/campaign_opt_pressure_period_sample_0.png)

Le consegne previste per il 12 e il 30 giugno non saranno inviate: la consegna 06/12 supererebbe la soglia di 3 messaggi per periodo di 2 settimane e la 30° consegna supererebbe la soglia delle comunicazioni autorizzate per mese civile.

![](assets/campaign_opt_pressure_period_sample_1.png)

Tutti i destinatari di queste consegne sono esclusi dall&#39;arbitrato durante la fase di analisi:

![](assets/campaign_opt_pressure_period_sample_2.png)

Per la stessa regola, se raggruppate le consegne per trimestre, verranno esclusi anche i destinatari della **newsletter n. 5** e non verranno inviati.

Infine, se non è selezionato alcun raggruppamento, non verrà inviata solo la **newsletter n. 4** , dal momento che è stata pianificata per lo stesso periodo di 2 settimane delle prime tre newsletter.

>[!NOTE]
>
>Quando si modifica la definizione di una regola di tipologia, è possibile creare una **simulazione** per controllarne l&#39;impatto sulle consegne a cui è applicata e monitorare l&#39;impatto che le consegne hanno l&#39;una sull&#39;altra. For more on this, refer to [Campaign simulations](../../campaign/using/campaign-simulations.md).

## Esclusione dopo l&#39;arbitrato {#exclusion-after-arbitration}

L&#39;arbitraggio viene riapplicato ogni notte tramite il flusso di lavoro **[!UICONTROL Forecasting]** tecnico e il **[!UICONTROL Campaign jobs]** flusso di lavoro.

Il **[!UICONTROL Forecasting]** flusso di lavoro precalcola i dati per il periodo in corso (dalla data di inizio alla data corrente), consentendo di applicare le regole di tipologia durante l&#39;analisi. Inoltre ricalcola i contatori di esclusione per l&#39;arbitrato ogni notte.

Pertanto, per ciascun destinatario,  Adobe Campaign controlla che il numero di messaggi da inviare non superi la soglia, tenendo conto del numero di messaggi già inviati per il periodo in questione. Queste informazioni sono un **indicatore**, poiché tutti i calcoli vengono aggiornati al momento della consegna.

Se questo numero supera la soglia, vengono applicate le regole di arbitrato definite nella tipologia della campagna e i destinatari vengono esclusi dalle campagne con peso inferiore.

![](assets/campaign_opt_pressure_exclusion.png)

>[!NOTE]
>
>Se più consegne dispongono di punteggi uguali, verrà inviata la campagna pianificata per la prima data.

## Casi di utilizzo delle regole di pressione {#use-cases-on-pressure-rules}

### Adeguamento della soglia in base al criterio {#adapting-the-threshold-based-on-criterion}

Vogliamo creare una regola di tipologia per impedire la consegna di più di 4 messaggi alla settimana ai clienti e di 2 messaggi alla settimana ai potenziali clienti.

Per identificare clienti e potenziali clienti, utilizzate il **[!UICONTROL Status]** campo, che contiene 0 per i potenziali clienti e 1 per i clienti.

Per creare la regola, esegui i seguenti passaggi:

1. Create a new **Pressure** type typology rule.
1. Edit the **[!UICONTROL Pressure]** tab: in the **[!UICONTROL Maximum number of messages]** section, we want to create a formula to calculate the threshold depending on each recipient. Selezionare il **[!UICONTROL Depends on the recipient]** valore nel **[!UICONTROL Threshold type]** campo, quindi fare clic **[!UICONTROL Edit expression]** a destra del **[!UICONTROL Formula]** campo.

   Fare clic sul **[!UICONTROL Advanced parameters]** pulsante per definire la formula di calcolo.

   ![](assets/campaign_opt_pressure_sample_1_1.png)

1. Select the **[!UICONTROL Edit the formula using an expression]** option and click **[!UICONTROL Next]**.

   ![](assets/campaign_opt_pressure_sample_1_2.png)

1. In the list of functions, double-click the **Iif** function in the **[!UICONTROL Others]** node.

   Then select the recipients&#39; **Status** in the **[!UICONTROL Available fields]** section.

   ![](assets/campaign_opt_pressure_sample_1_3.png)

   Immettere la formula seguente: **Iif(@status=0,2,4)**

   ![](assets/campaign_opt_pressure_sample_1_4.png)

   Questa formula ti consente di assegnare il valore 2 se lo stato è uguale a 0 e il valore 4 per tutti gli altri stati.

   Fai clic su **[!UICONTROL Finish]** per approvare la formula.

1. Indicare il periodo durante il quale si applicherà la regola: 7 giorni in questo caso, per conteggiare il numero di messaggi alla settimana.

   ![](assets/campaign_opt_pressure_sample_1_5.png)

1. Salva la regola per approvare la creazione.

Collegate ora la regola appena creata a una tipologia per applicarla alle consegne. Per eseguire questa operazione:

1. Creare una tipologia di campagna.
1. Passate alla **[!UICONTROL Rules]** scheda, fate clic sul **[!UICONTROL Add]** pulsante e selezionate la regola appena creata.

   ![](assets/campaign_opt_pressure_sample_1_6.png)

1. Salva la tipologia: viene aggiunto all&#39;elenco delle tipologie esistenti.

Per utilizzare questa tipologia nelle consegne, selezionatela nelle proprietà di consegna, nella **[!UICONTROL Typology]** scheda come illustrato di seguito:

![](assets/campaign_opt_pressure_sample_1_7.png)

>[!NOTE]
>
>La tipologia può essere definita nel modello di consegna, da applicare automaticamente a tutte le consegne create utilizzando questo modello.

Durante l&#39;analisi della consegna, i destinatari della consegna sono esclusi dalla consegna, se applicabile, a seconda del numero di consegne già inviate. Per visualizzare queste informazioni, potete:

* Visualizzare il risultato dell&#39;analisi:

   ![](assets/campaign_opt_pressure_sample_1_8.png)

* Modificate la consegna e fate clic sulla **[!UICONTROL Delivery]** scheda e sulla **[!UICONTROL Exclusions]** sottoscheda:

   ![](assets/campaign_opt_pressure_sample_1_9.png)

* Fare clic sulla **[!UICONTROL Audit]** scheda, quindi sulla **[!UICONTROL Causes of exclusions]** sottoscheda per visualizzare il numero di esclusioni e le regole di tipologia applicate:

   ![](assets/campaign_opt_pressure_sample_1_10.png)

### Calcolo del peso della consegna in base al comportamento {#calculating-the-delivery-weight-based-on-behavior}

Puoi definire regole di pressione in base al comportamento del destinatario: pertanto, il peso di una consegna può adattarsi a criteri che variano da un destinatario all&#39;altro. Ad esempio, puoi decidere di inviare un messaggio a seconda che un destinatario abbia visitato o meno il tuo sito Internet, che abbia fatto clic in una sezione specifica dell’ultima newsletter, che abbia effettuato l’iscrizione a un servizio di informazione o che si basasse anche sulle risposte a un sondaggio, a un gioco online, ecc.

Nell&#39;esempio seguente, vogliamo creare una consegna con un peso pari a 5. Questo peso è arricchito con punteggi di propensione in base al comportamento del destinatario: i clienti che hanno già ordinato da questo sito avranno un punteggio di 5, mentre i clienti che non hanno mai ordinato online avranno un punteggio di 4.

Per eseguire questo tipo di configurazione, è necessario utilizzare una formula per definire lo spessore del messaggio. Le informazioni sui punteggi di propensione e le risposte ai sondaggi devono essere accessibili nel modello dati. Nel nostro esempio, è stato aggiunto il campo **Propensity (Propensità** ).

Effettuate le seguenti operazioni di configurazione:

1. Create a new **Pressure** type typology rule.
1. Modificate la **[!UICONTROL Pressure]** scheda. Vogliamo creare una formula di soglia basata su ciascun singolo destinatario: fare clic sull&#39; **[!UICONTROL Edit expression]** icona a destra del **[!UICONTROL Weight formula]** campo.

   ![](assets/campaign_opt_pressure_sample_2_1.png)

1. Per impostazione predefinita, il valore **5** è visualizzato nella sezione superiore dell&#39;editor di espressioni. Vogliamo aggiungere il punteggio di propensione di ogni destinatario a questo peso: posizionate il cursore a destra del punto 5, immettete il **+** carattere e selezionate il campo **Propensità** .

   ![](assets/campaign_opt_pressure_sample_2_2.png)

1. Quindi aggiungete un valore più alto per i destinatari che hanno già effettuato un acquisto. Per loro, il peso della consegna deve essere aumentato di 5, mentre per altri aumenta di solo 4.

   ![](assets/campaign_opt_pressure_sample_2_3.png)

1. Fate clic **[!UICONTROL Finish]** per salvare la regola.
1. Collegate la regola a una tipologia di campagna e fate riferimento a questa tipologia in una consegna per approvarla.

### Invio dei messaggi con la ponderazione più elevata {#sending-only-the-highest-weighted-messages}

Desiderate inviare a ciascuno dei vostri destinatari non più di 2 messaggi entro la stessa settimana, con un limite di 2 messaggi al giorno, e desiderate inviare solo i messaggi con pesi più elevati.

A tal fine, è necessario pianificare diverse consegne con diversi pesi per lo stesso destinatario e applicare una regola di pressione per escludere le consegne con pesi inferiori.

Innanzitutto, configurate la regola di pressione.

1. Creare una regola di pressione. Per ulteriori informazioni, vedere [Creazione di una regola](#creating-a-pressure-rule)di pressione.
1. In the **[!UICONTROL General]** tab, select the **[!UICONTROL Re-apply the rule at the start of personalization]** option.

   ![](assets/campaign_opt_pressure_example_5.png)

   Questa opzione sovrascrive il valore definito nel **[!UICONTROL Frequency]** campo e applica automaticamente la regola durante la fase di personalizzazione. Per ulteriori informazioni, vedere [Regolazione della frequenza](../../campaign/using/applying-rules.md#adjusting-calculation-frequency)di calcolo.

1. In the **[!UICONTROL Pressure]** tab, select **[!UICONTROL 7d]** as the **[!UICONTROL Period considered]** and **[!UICONTROL Grouping per day]** as the **[!UICONTROL Period type]**.
1. Selezionare l&#39; **[!UICONTROL Take the deliveries into account in the provisional calendar]** opzione per includere le consegne programmate.

   ![](assets/campaign_opt_pressure_example_1.png)

   Le consegne inviate fino a 7 giorni prima della data di consegna e programmate fino a 7 giorni dopo la data di consegna saranno prese in considerazione nel calcolo. For more on this, refer to [Setting the period](#setting-the-period).

1. Nella **[!UICONTROL Typologies]** scheda, collegate la regola a una tipologia di campagna.
1. Salva le modifiche.

Ora create e configurate un flusso di lavoro per ogni consegna a cui desiderate applicare la regola di pressione.

1. Creare una campagna. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign).
1. Nella **[!UICONTROL Targeting and workflows]** scheda della campagna, aggiungete un&#39;attività **Query** al flusso di lavoro. For more on using this activity, refer to [this section](../../workflow/using/query.md).
1. Aggiungete un&#39; **[!UICONTROL Email delivery]** attività al flusso di lavoro e apritela. For more on using this activity, refer to [this section](../../workflow/using/delivery.md).
1. Passate alla **[!UICONTROL Approvals]** scheda dell&#39;elenco **[!UICONTROL Delivery properties]** e disattivate tutte le approvazioni.

   ![](assets/campaign_opt_pressure_example_2.png)

1. Nella **[!UICONTROL Typology]** scheda della **[!UICONTROL Delivery properties]**, fate riferimento alla tipologia della campagna in cui applicare la regola. Definire un peso per la consegna.

   ![](assets/campaign_opt_pressure_example_3.png)

1. Nella consegna, fare clic **[!UICONTROL Scheduling]** e selezionare **[!UICONTROL Schedule delivery (automatic execution when the scheduled date is reached)]**. In questo esempio, selezionare l&#39; **[!UICONTROL Use a calculation formula]** opzione.
1. Impostare la data di estrazione su 10 minuti (data corrente + 10 minuti).
1. Imposta la data del contatto sul giorno successivo (data corrente + 1 giorno).

   ![](assets/campaign_opt_pressure_example_4.png)

   Affinché le esclusioni delle regole di pressione vengano implementate correttamente, accertatevi di impostare la data e l&#39;ora di estrazione prima della data e dell&#39;ora di contatto, nonché prima che l&#39;arbitrato notturno venga nuovamente applicato. Per ulteriori informazioni, consulta [Esclusione dopo l&#39;arbitrato](#exclusion-after-arbitration).

1. Deselezionate l’ **[!UICONTROL Confirm the delivery before sending]** opzione e salvate le modifiche.
1. Procedere in modo simile per ogni consegna che si desidera inviare. Accertatevi di impostare il peso desiderato per ogni consegna.
1. Esegui i flussi di lavoro pertinenti per preparare e inviare le consegne.

Quando viene applicato l&#39;arbitrato notturno, le consegne con i pesi più bassi per lo stesso destinatario saranno escluse. Solo le consegne con il peso più alto saranno prese in considerazione per l&#39;invio. For more on this, refer to [Message weight](#message-weight).

Considerando che un&#39;e-mail è già stata inviata ai destinatari interessati all&#39;inizio della settimana, la tabella seguente mostra un esempio delle configurazioni che possono essere applicate per altre due consegne.

<table> 
 <thead> 
  <tr> 
   <th> Consegna<br /> </th> 
   <th> Approvazioni<br /> </th> 
   <th> Peso<br /> </th> 
   <th> Data/ora estrazione<br /> </th> 
   <th> Data contatto<br /> </th> 
   <th> Data/ora inizio consegna<br /> </th> 
   <th> Data/ora di esecuzione del flusso di lavoro arbitrario<br /> </th> 
   <th> Stato consegna<br /> </th> 
   <th> Consegna inviata (data/ora)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Delivery 1<br /> </td> 
   <td> Disattivato<br /> </td> 
   <td> 5<br /> </td> 
   <td> 3pm<br /> </td> 
   <td> 8 del mattino (giorno successivo)<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> Notte<br /> </td> 
   <td> Escluso<br /> </td> 
   <td> Escluso<br /> </td> 
  </tr> 
  <tr> 
   <td> Delivery 2<br /> </td> 
   <td> Disattivato<br /> </td> 
   <td> 10<br /> </td> 
   <td> 4pm<br /> </td> 
   <td> 9 (giorno successivo)<br /> </td> 
   <td> 2pm<br /> </td> 
   <td> Notte<br /> </td> 
   <td> Inviato<br /> </td> 
   <td> 9 (giorno successivo)<br /> </td> 
  </tr> 
 </tbody> 
</table>

Dopo che la data di estrazione è scaduta per le due consegne, l&#39;arbitrato notturno viene riapplicato prima delle date di contatto di entrambe le consegne. Questo consente di trovare tutte le consegne già inviate (destinatari per i quali viene elaborata una consegna, registrati attraverso i registri generali) o pianificate per l&#39;invio (destinatari idonei a ricevere una consegna, registrati attraverso i registri delle previsioni).

Una volta che tutte le consegne inviate e potenziali sono state elencate per il periodo definito nella regola di pressione,  Adobe Campaign le ordina in base al peso, con la ponderazione più alta prima. Quando viene raggiunta la soglia impostata nella regola di pressione (qui non più di 2 e-mail nella stessa settimana), i destinatari sono esclusi dalla consegna.
