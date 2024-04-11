---
product: campaign
title: Regole di filtro
description: Scopri come utilizzare le regole di filtro in Adobe Campaign
role: User, Data Engineer
feature: Typology Rules, Campaigns
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 2%

---

# Regole di filtro{#filtering-rules}

Le regole di filtro consentono di definire i messaggi da escludere in base ai criteri definiti in una query. Queste regole sono collegate a una dimensione di targeting.

Le regole di filtro possono essere collegate ad altri tipi di regole (controllo, pressione, ecc.) in tipologie, o raggruppati in un **Filtraggio** tipologia. Per ulteriori informazioni, consulta [Creazione e utilizzo di una tipologia di filtro](#creating-and-using-a-filtering-typology).

## Creare una regola di filtro {#creating-a-filtering-rule}

Ad esempio, puoi filtrare gli abbonati alle newsletter per evitare che le comunicazioni vengano inviate a destinatari minorenni.

Per definire questo filtro, effettua le seguenti operazioni:

1. Creare un **[!UICONTROL Filtering]** regola di tipologia applicabile a tutti i canali di comunicazione.

   ![](assets/campaign_opt_create_filter_01.png)

1. Modifica la dimensione di targeting predefinita e seleziona le sottoscrizioni (**nms:sottoscrizione**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Creare il filtro utilizzando **[!UICONTROL Edit the query from the targeting dimension...]** collegamento.

   ![](assets/campaign_opt_create_filter_03.png)

1. Collega questa regola a una tipologia di campagna e salvala.

   ![](assets/campaign_opt_create_filter_04.png)

Quando questa regola viene utilizzata in una consegna, gli abbonati minorenni vengono esclusi automaticamente. Un messaggio specifico indica l’applicazione della regola:

![](assets/campaign_opt_create_filter_05.png)

## Condizione di una regola di filtro {#conditioning-a-filtering-rule}

Puoi limitare il campo dell’applicazione della regola di filtro in base alla consegna o alla struttura della consegna collegata.

Per eseguire questa operazione, passare al **[!UICONTROL General]** della regola di tipologia, seleziona il tipo di restrizione da applicare e crea il filtro, come illustrato di seguito:

![](assets/campaign_opt_create_filter_06.png)

In questo caso, anche se la regola è collegata a tutte le consegne, verrà applicata solo a quelle che corrispondono ai criteri del filtro definito.

>[!NOTE]
>
>Le tipologie e le regole di filtro possono essere utilizzate in un flusso di lavoro, nel **[!UICONTROL Delivery outline]** attività. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/delivery-outline.md).

## Creare e utilizzare una tipologia di filtro {#creating-and-using-a-filtering-typology}

Puoi creare **[!UICONTROL Filtering]** tipologie: contengono solo regole di filtro.

![](assets/campaign_opt_create_typo_filtering.png)

Queste tipologie specifiche possono essere collegate a una consegna quando viene selezionato il target: nella procedura guidata di consegna, fai clic su **[!UICONTROL To]** , quindi fare clic sul pulsante **[!UICONTROL Exclusions]** scheda.

![](assets/campaign_opt_apply_typo_filtering.png)

Quindi seleziona la tipologia di filtro da applicare alla consegna. A questo scopo, fai clic su **[!UICONTROL Add]** e selezionare le tipologie da applicare.

Puoi anche collegare le regole di filtro direttamente tramite questa scheda, senza raggrupparle in una tipologia. A tale scopo, utilizzare la sezione inferiore della finestra.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Nella finestra di selezione sono disponibili solo le tipologie e le regole di filtro.
>
>Queste configurazioni possono essere definite nel modello di consegna e applicate automaticamente a tutte le nuove consegne create utilizzando il modello.
>

## Regole di esclusione del recapito messaggi predefinite {#default-deliverability-exclusion-rules}

Per impostazione predefinita, sono disponibili due regole di filtro: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) e **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Durante l’analisi e-mail, queste regole confrontano gli indirizzi e-mail dei destinatari con gli indirizzi o i nomi di dominio non consentiti contenuti in un elenco di soppressione globale crittografato gestito nell’istanza di recapito messaggi. In caso di corrispondenza, il messaggio non viene inviato al destinatario.

In questo modo si evita di essere aggiunti al elenco Bloccati a causa di attività dannose, in particolare l’uso di una spamtrap. Ad esempio, se utilizzi uno Spamtrap per abbonarti tramite uno dei tuoi moduli web, un’e-mail di conferma viene inviata automaticamente a quello Spamtrap, e il tuo indirizzo viene aggiunto automaticamente al inserisco nell&#39;elenco Bloccati di.

>[!NOTE]
>
>Gli indirizzi e i nomi di dominio contenuti nell’elenco di soppressione globale sono nascosti. Nei registri di analisi della consegna è indicato solo il numero di destinatari esclusi.
