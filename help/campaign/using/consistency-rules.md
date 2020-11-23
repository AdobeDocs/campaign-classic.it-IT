---
solution: Campaign Classic
product: campaign
title: Regole di coerenza
description: Regole di coerenza
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 2%

---


# Regole di coerenza{#consistency-rules}

## Informazioni sulle regole di coerenza {#about-consistency-rules}

 Adobe Campaign garantisce comunicazioni coerenti grazie a una serie di regole contenute nelle tipologie delle campagne. L&#39;obiettivo è quello di controllare le consegne inviate ai destinatari, quali volume, natura, pertinenza, ecc.

**Le regole di capacità** , ad esempio, possono evitare di sovraccaricare la piattaforma interessata dalla consegna dei messaggi. Ad esempio, le offerte speciali che contengono un collegamento per il download non devono essere inviate a troppe persone contemporaneamente, per evitare di saturare il server; le campagne telefoniche non devono superare la capacità di elaborazione dei call center, ecc. For more on this, refer to [Controlling capacity](#controlling-capacity).

## Capacità di controllo {#controlling-capacity}

Prima di inviare i messaggi, è necessario assicurarsi che l&#39;organizzazione disponga della capacità di elaborare la consegna (infrastruttura fisica), le risposte che la consegna può generare (messaggi in entrata) e il numero di chiamate da effettuare agli abbonati (capacità di elaborazione del call center), ad esempio.

A tal fine, è necessario creare regole di **[!UICONTROL Capacity]** tipologia.

Nell&#39;esempio seguente, viene creata una regola di tipologia per una campagna di fedeltà al telefono. Limitiamo il numero di messaggi a 20 al giorno, ossia la capacità di elaborazione giornaliera di un call center. Una volta applicata la regola a due consegne, possiamo monitorare il consumo attraverso i registri.

Per progettare una nuova regola di capacità, effettuate le seguenti operazioni:

1. Sotto il **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** nodo, fare clic su **[!UICONTROL New]**.
1. Selezionare un tipo di **[!UICONTROL Capacity]** regola.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Nella **[!UICONTROL Capacity]** scheda, creare le righe di disponibilità: nel nostro esempio, si tratta di periodi di tempo durante i quali possono essere effettuate chiamate. Selezionare un periodo di 24 ore e immettere 150 nella quantità iniziale, il che significa che il call center può gestire 150 chiamate al giorno.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Le righe di disponibilità sono esclusivamente a scopo informativo. Per escludere i messaggi quando viene raggiunto il limite di capacità, consulta [questa sezione](#exclude-messages-when-capacity-limit-reached).

1. Associate questa regola a una tipologia, quindi fate riferimento alla tipologia nella distribuzione per applicare questa regola di capacità. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. È possibile monitorare il consumo dalla regola **[!UICONTROL Consumptions]** e dalle **[!UICONTROL Capacity]** schede.

   Quando una regola viene utilizzata in una consegna, le **[!UICONTROL Consumed]** colonne e **[!UICONTROL Remaining]** le colonne forniscono informazioni sul caricamento, come illustrato di seguito:

   ![](assets/campaign_opt_create_capacity_03.png)

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#monitoring-consumption).

## Definizione del carico massimo {#defining-the-maximum-load}

Per definire il carico massimo, è necessario definire le linee di disponibilità. A questo scopo sono disponibili due opzioni: potete creare manualmente una o più righe di disponibilità (consultate [Aggiunta di righe di disponibilità una per una](#adding-availability-lines-one-by-one)) o creare intervalli di disponibilità. La frequenza di questi periodi di tempo può essere automatizzata (fare riferimento a [Aggiungere una serie di righe](#add-a-set-of-availability-lines)di disponibilità).

### Aggiunta di righe di disponibilità una per una {#adding-availability-lines-one-by-one}

Per creare una linea di disponibilità, fate clic sul **[!UICONTROL Add]** pulsante e selezionate **[!UICONTROL Add an availability line]**. Immettete il periodo di disponibilità e il carico disponibile.

![](assets/campaign_opt_create_capacity_02.png)

Aggiungete tutte le righe necessarie per soddisfare la capacità di elaborazione.

### Aggiunta di un set di righe di disponibilità {#add-a-set-of-availability-lines}

Per definire i periodi di disponibilità per un determinato periodo di tempo, fare clic sul **[!UICONTROL Add]** pulsante e selezionare l&#39; **[!UICONTROL Add a set of availability lines]** opzione. Specificate una durata per ciascun periodo di tempo e il numero di periodi da creare.

Per automatizzare la frequenza di creazione della pagina, fate clic sul **[!UICONTROL Change]** pulsante e definite la pianificazione del periodo di tempo.

![](assets/campaign_opt_create_capacity_07.png)

Ad esempio, definiamo una pianificazione per creare periodi di disponibilità per tutti i giorni lavorativi a una velocità di 10 chiamate all&#39;ora comprese tra le 9 e le 5 del pomeriggio. A questo scopo, eseguire i seguenti passaggi:

1. Selezionare il tipo di periodicità e i giorni e le ore durante i quali è valida:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Indicare le date di validità:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Controllare la pianificazione prima di approvarla:

   ![](assets/campaign_opt_create_capacity_10.png)

Il **[!UICONTROL Forecasting]** flusso di lavoro crea automaticamente tutte le righe corrispondenti.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>È consigliabile creare linee di disponibilità tramite importazioni di file. Questa scheda consente di visualizzare e controllare le linee di consumo.

## Escludi messaggi quando viene raggiunto il limite di capacità {#exclude-messages-when-capacity-limit-reached}

Le righe di disponibilità sono solo a scopo informativo. Per escludere i messaggi in eccesso, selezionare l&#39; **[!UICONTROL Exclude from the target messages in excess of capacity]** opzione. Questo impedisce il superamento della capacità. Per la stessa popolazione dell&#39;esempio precedente, il consumo e la capacità residua non possono superare la quantità iniziale:

![](assets/campaign_opt_create_capacity_04.png)

Il numero di messaggi da elaborare è suddiviso in modo uniforme per l&#39;intervallo di disponibilità definito. Ciò è particolarmente importante per i call center, in quanto il loro numero massimo di chiamate al giorno è limitato. Nel caso delle consegne tramite e-mail, l&#39; **[!UICONTROL Do not limit instantaneous delivery capacity]** opzione consente di ignorare questo intervallo di disponibilità e inviare contemporaneamente i messaggi e-mail.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>In caso di sovraccarico, i messaggi salvati vengono selezionati in base alla formula definita nelle proprietà di consegna.

![](assets/campaign_opt_create_capacity_06.png)

## Monitoraggio del consumo {#monitoring-consumption}

Per impostazione predefinita, le regole di capacità sono esclusivamente a scopo indicativo. Selezionate l’ **[!UICONTROL Exclude messages in excess of capacity from the target]** opzione per impedire il superamento del carico definito. In questo caso, i messaggi in eccesso verranno automaticamente esclusi dalle consegne che utilizzano questa regola di tipologia.

Per monitorare i consumi, visualizzare i valori visualizzati nella **[!UICONTROL Consumed]** colonna della **[!UICONTROL Capacity]** scheda nella regola di tipologia.

![](assets/campaign_opt_create_capacity_04.png)

Per visualizzare le linee di consumo, fare clic sulla **[!UICONTROL Consumptions]** scheda nella regola.
