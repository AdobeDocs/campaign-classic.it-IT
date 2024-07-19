---
product: campaign
title: Regole di coerenza
description: Scopri come utilizzare le regole di coerenza in Adobe Campaign
role: User, Data Engineer
feature: Typology Rules, Campaigns
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 3%

---

# Regole di coerenza{#consistency-rules}

## Informazioni sulle regole di coerenza {#about-consistency-rules}

Adobe Campaign garantisce comunicazioni coerenti grazie a un set di regole contenute nelle tipologie di campagne. Il loro obiettivo è controllare le consegne inviate ai destinatari, ad esempio volume, natura, pertinenza e così via.

**Regole di capacità**, ad esempio, possono evitare di sovraccaricare la piattaforma interessata dalla consegna dei messaggi. Ad esempio, le offerte speciali che contengono un collegamento di download non devono essere inviate a troppe persone contemporaneamente, per evitare di saturare il server; le campagne telefoniche non devono superare la capacità di elaborazione dei call center, ecc. Per ulteriori informazioni, consulta [Capacità di controllo](#controlling-capacity).

## Capacità di controllo {#controlling-capacity}

Prima di consegnare i messaggi, è necessario assicurarsi che l’organizzazione abbia la capacità di elaborare la consegna (infrastruttura fisica), le risposte che la consegna può generare (messaggi in entrata) e il numero di chiamate da effettuare per contattare gli abbonati (capacità di elaborazione del call center), ad esempio.

A tale scopo, è necessario creare **[!UICONTROL Capacity]** regole di tipologia.

Nell’esempio seguente viene creata una regola di tipologia per una campagna fedeltà telefonica. Limitiamo il numero di messaggi a 20 al giorno, ovvero la capacità di elaborazione giornaliera di un call center. Una volta applicata la regola a due consegne, possiamo monitorare il consumo tramite i registri.

Per progettare una nuova regola di capacità, effettuare le seguenti operazioni:

1. Nel nodo **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** fare clic su **[!UICONTROL New]**.
1. Selezionare un tipo di regola **[!UICONTROL Capacity]**.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Nella scheda **[!UICONTROL Capacity]**, crea le righe di disponibilità: nel nostro esempio, si tratta di periodi di tempo durante i quali è possibile effettuare chiamate. Selezionare un periodo di 24 ore e immettere 150 nella quantità iniziale, il che significa che il call center è in grado di gestire 150 chiamate al giorno.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Le linee di disponibilità sono solo a scopo informativo. Se devi escludere i messaggi quando viene raggiunto il limite di capacità, fai riferimento a [questa sezione](#exclude-messages-when-capacity-limit-reached).

1. Associa questa regola a una tipologia e fai riferimento a essa nella consegna per applicare questa regola di capacità. Per ulteriori informazioni al riguardo, consulta [questa sezione](applying-rules.md#applying-a-typology-to-a-delivery).
1. È possibile monitorare il consumo dalle schede delle regole **[!UICONTROL Consumptions]** e **[!UICONTROL Capacity]**.

   Quando una regola viene utilizzata in una consegna, le colonne **[!UICONTROL Consumed]** e **[!UICONTROL Remaining]** forniscono informazioni sul caricamento, come illustrato di seguito:

   ![](assets/campaign_opt_create_capacity_03.png)

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#monitoring-consumption).

## Definire il carico massimo {#defining-the-maximum-load}

Per definire il carico massimo, è necessario definire le linee di disponibilità. A tale scopo, sono disponibili due opzioni: è possibile creare manualmente una o più righe di disponibilità (fare riferimento a [Aggiungere righe di disponibilità una alla volta](#adding-availability-lines-one-by-one)) o creare intervalli di disponibilità. La frequenza di questi periodi di tempo può essere automatizzata (fare riferimento a [Aggiungere un set di righe di disponibilità](#add-a-set-of-availability-lines)).

### Aggiungere righe di disponibilità una alla volta {#adding-availability-lines-one-by-one}

Per creare una riga di disponibilità, fare clic sul pulsante **[!UICONTROL Add]** e selezionare **[!UICONTROL Add an availability line]**. Inserire il periodo di disponibilità e il carico disponibile.

![](assets/campaign_opt_create_capacity_02.png)

Aggiungi tutte le righe necessarie per adattarle alla capacità di elaborazione.

### Aggiungere un set di righe di disponibilità {#add-a-set-of-availability-lines}

Per definire i periodi di disponibilità per un determinato periodo di tempo, fare clic sul pulsante **[!UICONTROL Add]** e selezionare l&#39;opzione **[!UICONTROL Add a set of availability lines]**. Indica una durata per ogni periodo di tempo e il numero di periodi da creare.

Per automatizzare la frequenza di creazione delle pagine, fare clic sul pulsante **[!UICONTROL Change]** e definire la pianificazione dei periodi di tempo.

![](assets/campaign_opt_create_capacity_07.png)

Ad esempio, definiamo una pianificazione per creare periodi di disponibilità per tutti i giorni lavorativi a una velocità di 10 chiamate all’ora tra le 9 e le 17. A questo scopo, esegui i seguenti passaggi:

1. Selezionare il tipo di periodicità e i giorni e le ore di validità:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Indicare le date di validità:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Controlla la pianificazione prima di approvarla:

   ![](assets/campaign_opt_create_capacity_10.png)

Il flusso di lavoro **[!UICONTROL Forecasting]** crea automaticamente tutte le righe corrispondenti.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>È consigliabile creare righe di disponibilità tramite importazioni di file. Questa scheda consente di visualizzare e controllare le linee di consumo.

## Escludi messaggi al raggiungimento del limite di capacità {#exclude-messages-when-capacity-limit-reached}

Le righe di disponibilità sono solo a scopo informativo. Per escludere i messaggi in eccesso, selezionare l&#39;opzione **[!UICONTROL Exclude from the target messages in excess of capacity]**. Questo impedisce il superamento della capacità. Per la stessa popolazione dell&#39;esempio precedente, il consumo e la capacità rimanente non possono superare la quantità iniziale:

![](assets/campaign_opt_create_capacity_04.png)

Il numero massimo di messaggi che possono essere elaborati viene suddiviso in modo uniforme nell’intervallo di disponibilità definito. Ciò è particolarmente importante per i call center, poiché il loro numero massimo di chiamate al giorno è limitato. Nel caso di consegne di e-mail, l&#39;opzione **[!UICONTROL Do not limit instantaneous delivery capacity]** consente di ignorare questo intervallo di disponibilità e di inviare contemporaneamente le e-mail.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>In caso di sovraccarico, i messaggi salvati vengono selezionati in base alla formula definita nelle proprietà di consegna.

![](assets/campaign_opt_create_capacity_06.png)

## Consumo monitor {#monitoring-consumption}

Per impostazione predefinita, le regole di capacità sono solo a scopo indicativo. Selezionare l&#39;opzione **[!UICONTROL Exclude messages in excess of capacity from the target]** per evitare il superamento del carico definito. In questo caso, i messaggi in eccesso verranno automaticamente esclusi dalle consegne utilizzando questa regola di tipologia.

Per monitorare i consumi, visualizzare i valori visualizzati nella colonna **[!UICONTROL Consumed]** della scheda **[!UICONTROL Capacity]** nella regola di tipologia.

![](assets/campaign_opt_create_capacity_04.png)

Per visualizzare le righe di consumo, fare clic sulla scheda **[!UICONTROL Consumptions]** nella regola.
