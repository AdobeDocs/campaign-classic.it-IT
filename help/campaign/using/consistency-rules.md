---
product: campaign
title: Regole di coerenza
description: Regole di coerenza
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 757328fa-4698-4f85-a5fa-074b5152ec45
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 2%

---

# Regole di coerenza{#consistency-rules}

## Informazioni sulle regole di coerenza {#about-consistency-rules}

Adobe Campaign garantisce comunicazioni coerenti grazie a un set di regole contenute nelle tipologie di campagne. Il loro scopo è quello di controllare le consegne inviate ai destinatari, quali volume, natura, pertinenza, ecc.

**** Le regole di capacità, ad esempio, possono evitare di sovraccaricare la piattaforma interessata dalla consegna dei messaggi. Ad esempio, le offerte speciali contenenti un collegamento per il download non devono essere inviate a troppe persone contemporaneamente, per evitare di saturare il server; le campagne telefoniche non devono superare la capacità di elaborazione dei call center, ecc. Per ulteriori informazioni, consulta [Controllo della capacità](#controlling-capacity).

## Controllo della capacità {#controlling-capacity}

Prima di inviare i messaggi, è necessario assicurarsi che l’organizzazione disponga della capacità necessaria per elaborare la consegna (infrastruttura fisica), le risposte che la consegna può generare (messaggi in entrata) e il numero di chiamate da effettuare agli abbonati (capacità di elaborazione del call center), ad esempio.

A questo scopo, devi creare regole di tipologia **[!UICONTROL Capacity]**.

Nell’esempio seguente, creiamo una regola di tipologia per una campagna di fidelizzazione telefonica. Limitiamo il numero di messaggi a 20 al giorno, ovvero la capacità di elaborazione giornaliera di un call center. Una volta applicata la regola a due consegne, possiamo monitorare il consumo tramite i registri.

Per progettare una nuova regola di capacità, segui i passaggi seguenti:

1. Sotto il nodo **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**, fai clic su **[!UICONTROL New]**.
1. Seleziona un tipo di regola **[!UICONTROL Capacity]**.

   ![](assets/campaign_opt_create_capacity_01.png)

1. Nella scheda **[!UICONTROL Capacity]** , crea le righe di disponibilità: nel nostro esempio, si tratta di periodi di tempo durante i quali è possibile effettuare chiamate. Seleziona un periodo di 24 ore e inserisci 150 nella quantità iniziale, il che significa che il call center può gestire 150 chiamate al giorno.

   ![](assets/campaign_opt_create_capacity_02.png)

   >[!NOTE]
   >
   >Le righe di disponibilità sono solo a scopo informativo. Per escludere i messaggi quando viene raggiunto il limite di capacità, consulta [questa sezione](#exclude-messages-when-capacity-limit-reached).

1. Associa questa regola a una tipologia, quindi fai riferimento alla tipologia nella consegna per applicare questa regola di capacità. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery).
1. Puoi monitorare il consumo dalle schede delle regole **[!UICONTROL Consumptions]** e **[!UICONTROL Capacity]** .

   Quando una regola viene utilizzata in una consegna, le colonne **[!UICONTROL Consumed]** e **[!UICONTROL Remaining]** forniscono informazioni sul caricamento, come illustrato di seguito:

   ![](assets/campaign_opt_create_capacity_03.png)

   Per ulteriori informazioni al riguardo, consulta [questa sezione](#monitoring-consumption).

## Definizione del carico massimo {#defining-the-maximum-load}

Per definire il carico massimo, è necessario definire le linee di disponibilità. A questo scopo sono disponibili due opzioni: puoi creare manualmente una o più righe di disponibilità (consulta [Aggiunta di righe di disponibilità una per una](#adding-availability-lines-one-by-one)) oppure creare intervalli di disponibilità. La frequenza di questi periodi di tempo può essere automatizzata (fare riferimento a [Aggiungi un set di linee di disponibilità](#add-a-set-of-availability-lines)).

### Aggiunta di righe di disponibilità una per una {#adding-availability-lines-one-by-one}

Per creare una linea di disponibilità, fare clic sul pulsante **[!UICONTROL Add]** e selezionare **[!UICONTROL Add an availability line]**. Inserire il periodo di disponibilità e il carico disponibile.

![](assets/campaign_opt_create_capacity_02.png)

Aggiungi tutte le righe necessarie per soddisfare la tua capacità di elaborazione.

### Aggiungi un set di righe di disponibilità {#add-a-set-of-availability-lines}

Per definire i periodi di disponibilità per un determinato periodo di tempo, fai clic sul pulsante **[!UICONTROL Add]** e seleziona l&#39;opzione **[!UICONTROL Add a set of availability lines]**. Indica una durata per ogni periodo di tempo e il numero di periodi da creare.

Per automatizzare la frequenza di creazione della pagina, fai clic sul pulsante **[!UICONTROL Change]** e definisci la pianificazione del periodo di tempo.

![](assets/campaign_opt_create_capacity_07.png)

Ad esempio, definiamo una pianificazione per creare periodi di disponibilità per tutti i giorni lavorativi a una velocità di 10 chiamate all’ora compresa tra le 9 e le 5 del mattino. A questo scopo, esegui i seguenti passaggi:

1. Selezionare il tipo di periodicità e i giorni e le ore durante i quali è valida:

   ![](assets/campaign_opt_create_capacity_08.png)

1. Indicare le date di validità:

   ![](assets/campaign_opt_create_capacity_09.png)

1. Controlla la pianificazione prima di approvarla:

   ![](assets/campaign_opt_create_capacity_10.png)

Il flusso di lavoro **[!UICONTROL Forecasting]** crea automaticamente tutte le righe corrispondenti.

![](assets/campaign_opt_create_capacity_12.png)

>[!NOTE]
>
>È consigliabile creare linee di disponibilità tramite importazioni di file. Questa scheda consente di visualizzare e controllare le linee di consumo.

## Escludere i messaggi quando viene raggiunto il limite di capacità {#exclude-messages-when-capacity-limit-reached}

Le linee di disponibilità sono solo a scopo informativo. Per escludere i messaggi in eccesso, seleziona l’opzione **[!UICONTROL Exclude from the target messages in excess of capacity]** . Questo impedisce il superamento della capacità. Per la stessa popolazione dell&#39;esempio precedente, il consumo e la capacità residua non possono superare la quantità iniziale:

![](assets/campaign_opt_create_capacity_04.png)

Il numero di messaggi da elaborare viene suddiviso in modo uniforme nell’intervallo di disponibilità definito. Ciò è particolarmente importante per i call center in quanto il loro numero massimo di chiamate al giorno è limitato. Nel caso di consegne e-mail, l’opzione **[!UICONTROL Do not limit instantaneous delivery capacity]** ti consente di ignorare questo intervallo di disponibilità e di inviare contemporaneamente le e-mail.

![](assets/campaign_opt_create_capacity_05.png)

>[!NOTE]
>
>In caso di sovraccarico, i messaggi salvati vengono selezionati in base alla formula definita nelle proprietà di consegna.

![](assets/campaign_opt_create_capacity_06.png)

## Monitoraggio del consumo {#monitoring-consumption}

Per impostazione predefinita, le regole di capacità sono solo a scopo indicativo. Selezionare l&#39;opzione **[!UICONTROL Exclude messages in excess of capacity from the target]** per evitare il superamento del carico definito. In questo caso, i messaggi in eccesso verranno automaticamente esclusi dalle consegne che utilizzano questa regola di tipologia.

Per monitorare i consumi, visualizzare i valori visualizzati nella colonna **[!UICONTROL Consumed]** della scheda **[!UICONTROL Capacity]** nella regola di tipologia.

![](assets/campaign_opt_create_capacity_04.png)

Per visualizzare le linee di consumo, fai clic sulla scheda **[!UICONTROL Consumptions]** nella regola.
