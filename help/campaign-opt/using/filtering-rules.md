---
product: campaign
title: Regole di filtro
description: Scopri come utilizzare le regole di filtro in Adobe Campaign
role: User, Developer
feature: Typology Rules, Campaigns
hide: true
exl-id: a4d12445-5680-4704-9c67-e43e0ea6631b
TQID: https://experienceleague.adobe.com/4EMN3dCYWlCIIevYAbZsBxH1u2EaPl-izrzCKqyr1eA
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
subfeature_v2:
  - id: ed29abcd-b6a8-4d4b-ab8b-b7e746973281
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 509
ht-degree: 2%

---

# Regole di filtro{#filtering-rules}

Le regole di filtro consentono di definire i messaggi da escludere in base ai criteri definiti in una query. Queste regole sono collegate a una dimensione di targeting.

Le regole di filtro possono essere collegate ad altri tipi di regole (controllo, pressione, ecc.) nelle tipologie o raggruppate in una tipologia **Filtro** dedicata. Per ulteriori informazioni, consulta [Creazione e utilizzo di una tipologia di filtro](#creating-and-using-a-filtering-typology).

## Creare una regola di filtro {#creating-a-filtering-rule}

Ad esempio, puoi filtrare gli abbonati alle newsletter per evitare che le comunicazioni vengano inviate a destinatari minorenni.

Per definire questo filtro, effettua le seguenti operazioni:

1. Creare una regola di tipologia **[!UICONTROL Filtering]** applicabile a tutti i canali di comunicazione.

   ![](assets/campaign_opt_create_filter_01.png)

1. Modifica la dimensione di targeting predefinita e seleziona le sottoscrizioni (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Creare il filtro utilizzando il collegamento **[!UICONTROL Edit the query from the targeting dimension...]**.

   ![](assets/campaign_opt_create_filter_03.png)

1. Collega questa regola a una tipologia di campagna e salvala.

   ![](assets/campaign_opt_create_filter_04.png)

Quando questa regola viene utilizzata in una consegna, gli abbonati minorenni vengono esclusi automaticamente. Un messaggio specifico indica l’applicazione della regola:

![](assets/campaign_opt_create_filter_05.png)

## Condizione di una regola di filtro {#conditioning-a-filtering-rule}

Puoi limitare il campo dell’applicazione della regola di filtro in base alla consegna o alla struttura della consegna collegata.

A questo scopo, vai alla scheda **[!UICONTROL General]** della regola di tipologia, seleziona il tipo di restrizione da applicare e crea il filtro, come illustrato di seguito:

![](assets/campaign_opt_create_filter_06.png)

In questo caso, anche se la regola è collegata a tutte le consegne, verrà applicata solo a quelle che corrispondono ai criteri del filtro definito.

>[!NOTE]
>
>Le tipologie e le regole di filtro possono essere utilizzate in un flusso di lavoro, nell&#39;attività **[!UICONTROL Delivery outline]**. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/delivery-outline.md).

## Creare e utilizzare una tipologia di filtro {#creating-and-using-a-filtering-typology}

È possibile creare **[!UICONTROL Filtering]** tipologie: contengono solo regole di filtro.

![](assets/campaign_opt_create_typo_filtering.png)

Queste tipologie specifiche possono essere collegate a una consegna quando la destinazione è selezionata: nell&#39;assistente alla consegna, fai clic sul collegamento **[!UICONTROL To]**, quindi sulla scheda **[!UICONTROL Exclusions]**.

![](assets/campaign_opt_apply_typo_filtering.png)

Quindi seleziona la tipologia di filtro da applicare alla consegna. A tale scopo, fare clic sul pulsante **[!UICONTROL Add]** e selezionare le tipologie da applicare.

Puoi anche collegare le regole di filtro direttamente tramite questa scheda, senza raggrupparle in una tipologia. A tale scopo, utilizzare la sezione inferiore della finestra.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Nella finestra di selezione sono disponibili solo le tipologie e le regole di filtro.
>
>Queste configurazioni possono essere definite nel modello di consegna e applicate automaticamente a tutte le nuove consegne create utilizzando il modello.
>

## Regole di esclusione del recapito messaggi predefinite {#default-deliverability-exclusion-rules}

Per impostazione predefinita sono disponibili due regole di filtro: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) e **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Durante l’analisi e-mail, queste regole confrontano gli indirizzi e-mail dei destinatari con gli indirizzi o i nomi di dominio non consentiti contenuti in un elenco di soppressione globale crittografato gestito nell’istanza di recapito messaggi. In caso di corrispondenza, il messaggio non viene inviato al destinatario.

Questo per evitare di essere aggiunti al inserisco nell&#39;elenco Bloccati di a causa di attività dannose, in particolare l’utilizzo di uno Spamtrap. Ad esempio, se utilizzi uno Spamtrap per abbonarti tramite uno dei tuoi moduli web, un’e-mail di conferma viene inviata automaticamente a quello Spamtrap, e il tuo indirizzo viene aggiunto automaticamente al inserisco nell&#39;elenco Bloccati di.

>[!NOTE]
>
>Gli indirizzi e i nomi di dominio contenuti nell’elenco di soppressione globale sono nascosti. Nei registri di analisi della consegna è indicato solo il numero di destinatari esclusi.
