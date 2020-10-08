---
title: Regole di filtro
seo-title: Regole di filtro
description: Regole di filtro
seo-description: null
page-status-flag: never-activated
uuid: 24238a99-1f0f-4d04-9807-557ec2a5ba16
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 0d50826e-2211-4c3b-8413-ca1453bba6c4
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '507'
ht-degree: 3%

---


# Regole di filtro{#filtering-rules}

Le regole di filtro consentono di definire i messaggi da escludere in base ai criteri definiti in una query. Queste regole sono collegate a una dimensione di targeting.

Le regole di filtro possono essere collegate ad altri tipi di regole (controllo, pressione, ecc.) in tipologie o raggruppate in una specifica tipologia di **filtro** . Per ulteriori informazioni, vedere [Creazione e utilizzo di una tipologia](#creating-and-using-a-filtering-typology)di filtro.

## Creating a filtering rule {#creating-a-filtering-rule}

Ad esempio, potete filtrare gli utenti iscritti alla newsletter in modo da impedire l’invio di comunicazioni ai destinatari minorenni.

Per definire questo filtro, procedere come segue:

1. Creare una regola di **[!UICONTROL Filtering]** tipologia applicabile a tutti i canali di comunicazione.

   ![](assets/campaign_opt_create_filter_01.png)

1. Modificate la dimensione di targeting predefinita e selezionate le sottoscrizioni (**nms:subscription**).

   ![](assets/campaign_opt_create_filter_02.png)

1. Create il filtro utilizzando il **[!UICONTROL Edit the query from the targeting dimension...]** collegamento.

   ![](assets/campaign_opt_create_filter_03.png)

1. Collegate questa regola a una tipologia di campagna e salvatela.

   ![](assets/campaign_opt_create_filter_04.png)

Quando questa regola viene utilizzata in una consegna, gli abbonati minorenni vengono automaticamente esclusi. Un messaggio specifico indica l&#39;applicazione della regola:

![](assets/campaign_opt_create_filter_05.png)

## Condizionamento di una regola di filtro {#conditioning-a-filtering-rule}

È possibile limitare il campo applicazione della regola di filtraggio in base al profilo di consegna o consegna collegato.

A questo scopo, andate alla **[!UICONTROL General]** scheda della regola di tipologia, selezionate il tipo di restrizione da applicare e create il filtro, come illustrato di seguito:

![](assets/campaign_opt_create_filter_06.png)

In questo caso, anche se la regola è collegata a tutte le consegne, verrà applicata solo a quelle che corrispondono ai criteri del filtro definito.

>[!NOTE]
>
>Le tipologie e le regole di filtro possono essere utilizzate in un flusso di lavoro, in un&#39; **[!UICONTROL Delivery outline]** attività. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/delivery-outline.md).

## Creazione e utilizzo di una tipologia di filtro {#creating-and-using-a-filtering-typology}

È possibile creare **[!UICONTROL Filtering]** tipologie: contengono solo regole di filtro.

![](assets/campaign_opt_create_typo_filtering.png)

Queste tipologie specifiche possono essere collegate a una consegna quando la destinazione è selezionata: nella procedura guidata di consegna fare clic sul **[!UICONTROL To]** collegamento, quindi fare clic sulla **[!UICONTROL Exclusions]** scheda.

![](assets/campaign_opt_apply_typo_filtering.png)

Selezionate quindi la tipologia di filtro da applicare alla consegna. A questo scopo, fare clic sul **[!UICONTROL Add]** pulsante e selezionare le tipologie da applicare.

Potete anche collegare le regole di filtro direttamente tramite questa scheda, senza raggrupparle in una tipologia. A tale scopo, utilizzare la sezione inferiore della finestra.

![](assets/campaign_opt_select_typo_filtering.png)

>[!NOTE]
>
>Nella finestra di selezione sono disponibili solo le tipologie e le regole di filtro.
>
>Queste configurazioni possono essere definite nel modello di consegna da applicare automaticamente a tutte le nuove consegne create utilizzando il modello.


## Regole di esclusione recapito predefinite {#default-deliverability-exclusion-rules}

Per impostazione predefinita sono disponibili due regole di filtro: **[!UICONTROL Exclude addresses]** ( **[!UICONTROL addressExclusions]** ) e **[!UICONTROL Exclude domains]** ( **[!UICONTROL domainExclusions]** ). Durante l&#39;analisi delle e-mail, queste regole confrontano gli indirizzi e-mail dei destinatari con gli indirizzi o i nomi di dominio vietati contenuti in un elenco di soppressione globale crittografato gestito nell&#39;istanza di recapito. In caso di corrispondenza, il messaggio non viene inviato al destinatario.

Questo per evitare di essere aggiunti al elenco Bloccati  a causa di attività dannose, soprattutto l&#39;uso di uno Spamtrap. Ad esempio, se si utilizza uno Spamtrap per effettuare la sottoscrizione tramite uno dei moduli Web, viene automaticamente inviato un messaggio e-mail di conferma a tale Spamtrap, con l&#39;aggiunta automatica dell&#39;indirizzo al elenco Bloccati .

>[!NOTE]
>
>Gli indirizzi e i nomi di dominio contenuti nell&#39;elenco di soppressione globale sono nascosti. Solo il numero di destinatari esclusi è indicato nei registri di analisi della consegna.

