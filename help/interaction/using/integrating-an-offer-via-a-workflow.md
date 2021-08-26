---
product: campaign
title: Integrazione di un’offerta tramite un flusso di lavoro
description: Integrazione di un’offerta tramite un flusso di lavoro
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
exl-id: 33d318f3-1eb4-4c74-8c20-8b9f0442c7c3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 3%

---

# Integrazione di un’offerta tramite un flusso di lavoro{#integrating-an-offer-via-a-workflow}

![](../../assets/v7-only.svg)

Al di fuori dell’attività di consegna stessa, diverse attività del flusso di lavoro ti consentono di definire il modo in cui vengono presentate le offerte:

* Profilo di consegna
* Arricchimento
* Motore di offerta
* Offerte per cella

## Profilo di consegna {#delivery-outline}

L’attività di profilo della consegna, disponibile nei flussi di lavoro delle campagne, consente di presentare offerte a cui viene fatto riferimento in una struttura di consegna dalla campagna corrente in corso.

1. In un flusso di lavoro, aggiungi un’attività di profilo della consegna prima di aggiungere un’attività di consegna.
1. Nell’attività di struttura della consegna, specifica il profilo da utilizzare.

   Per ulteriori informazioni su come specificare i contorni di consegna, consulta la guida [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline) .

1. Completa i campi disponibili in base alla consegna.
1. Esistono due casi possibili:

   * Se desideri chiamare il motore di offerta, seleziona la casella **[!UICONTROL Restrict the number of propositions selected]** . Specifica lo spazio di offerta e il numero di proposte da presentare nella consegna.

      Il motore di offerta terrà conto dei fattori di ponderazione e delle regole di idoneità dell’offerta.

   * Se non selezioni la casella , tutte le offerte nel profilo di consegna verranno presentate senza effettuare una chiamata al motore di offerta.
   >[!NOTE]
   >
   >L’anteprima tiene conto del numero di offerte specificate nella consegna. Quando esegui un flusso di lavoro, viene preso in considerazione il numero specificato nel profilo di consegna.

   ![](assets/int_compo_offre_wf1.png)

## Arricchimento {#enrichment}

L’attività di arricchimento ti consente di aggiungere offerte o collegamenti alle offerte per i destinatari della consegna.

>[!NOTE]
>
>Per ulteriori informazioni sull&#39;attività di arricchimento, consulta la documentazione dedicata nella [Guida ai flussi di lavoro](../../workflow/using/enrichment.md).

Ad esempio, puoi arricchire i dati di una query del destinatario prima di una consegna.

![](assets/int_enrichment_offer1.png)

Esistono due metodi per specificare le proposte di offerta.

* Specifica di un&#39;offerta o di una chiamata al motore di offerta.
* Riferimento a un collegamento a un’offerta.

### Specifica di un’offerta o di una chiamata al motore di offerta {#specifying-an-offer-or-a-call-to-the-offer-engine}

Dopo aver configurato la query (consulta la [Guida ai flussi di lavoro](../../workflow/using/query.md)):

1. Aggiungi e apri un’attività di arricchimento.
1. Nella scheda **[!UICONTROL Enrichment]**, seleziona **[!UICONTROL Add data]**.
1. Seleziona **[!UICONTROL An offer proposition]** nei tipi di dati da aggiungere.

   ![](assets/int_enrichment_offer2.png)

1. Specifica un identificatore e un’etichetta per la proposta che verrà aggiunta.
1. Specifica la selezione dell’offerta. Sono disponibili due opzioni possibili:

   * **[!UICONTROL Search for the best offer in a category]** : seleziona questa opzione e specifica i parametri di chiamata del motore di offerta (spazio di offerta, categoria o tema/i, data di contatto, numero di offerte da mantenere). Il motore calcola automaticamente le offerte da aggiungere in base a questi parametri. È consigliabile completare il campo **[!UICONTROL Category]** o **[!UICONTROL Theme]** anziché entrambi allo stesso tempo.

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : seleziona questa opzione e specifica uno spazio di offerta, un’offerta specifica e una data di contatto per configurare direttamente l’offerta che desideri aggiungere, senza chiamare il motore di offerta.

      ![](assets/int_enrichment_offer4.png)

1. Quindi configura un’attività di consegna corrispondente al canale scelto. Per ulteriori informazioni, consulta la sezione [Inserimento di una proposta di offerta in una consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >Il numero di proposte disponibili per l’anteprima dipende dalla configurazione effettuata nell’attività di arricchimento, anziché da qualsiasi configurazione possibile eseguita direttamente nella consegna.

### Riferimento a un collegamento a un’offerta {#referencing-a-link-to-an-offer}

Puoi anche fare riferimento a un collegamento a un’offerta in un’attività di arricchimento.

A questo scopo, utilizza il seguente processo:

1. Seleziona **[!UICONTROL Add data]** nella scheda **[!UICONTROL Enrichment]** dell’attività.
1. Nella finestra in cui scegli il tipo di dati da aggiungere, seleziona **[!UICONTROL A link]**.
1. Seleziona il tipo di collegamento che desideri stabilire e la relativa destinazione. In questo caso, la destinazione è lo schema dell&#39;offerta.

   ![](assets/int_enrichment_link1.png)

1. Specifica il join tra i dati della tabella in entrata nell’attività di arricchimento (in questo caso la tabella dei destinatari) e la tabella delle offerte. Ad esempio, puoi collegare un codice di offerta a un destinatario.

   ![](assets/int_enrichment_link2.png)

1. Quindi configura un’attività di consegna corrispondente al canale scelto. Per ulteriori informazioni, consulta la sezione [Inserimento di una proposta di offerta in una consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

   >[!NOTE]
   >
   >Il numero di proposte disponibili per l’anteprima dipende dalla configurazione eseguita nella consegna.

### Memorizzazione di ranking e pesi delle offerte {#storing-offer-rankings-and-weights}

Per impostazione predefinita, quando un&#39;attività **Arricchimento** viene utilizzata per fornire offerte, le loro classificazioni e i loro pesi non vengono memorizzati nella tabella delle proposte.

>[!NOTE]
>
>Ricorda: L’attività **[!UICONTROL Offer engine]** memorizza tali informazioni per impostazione predefinita.

Tuttavia, è possibile memorizzare queste informazioni come segue:

1. Crea una chiamata al motore di offerta in un’attività di arricchimento inserita dopo una query e prima di un’attività di consegna. Consulta la sezione [Specifica di un&#39;offerta o di una chiamata al motore di offerta](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine) .
1. Nella finestra principale dell’attività, seleziona **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Aggiungi le colonne **[!UICONTROL @rank]** per la classificazione e **[!UICONTROL @weight]** per il peso dell’offerta.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Conferma l’aggiunta e salva il flusso di lavoro.

La consegna memorizza automaticamente la classificazione e il peso delle offerte. Queste informazioni sono visibili nella scheda **[!UICONTROL Offers]** della consegna.

## Motore di offerta {#offer-engine}

L’attività **[!UICONTROL Offer engine]** ti consente inoltre di specificare una chiamata al motore di offerta prima della consegna.

Questa attività funziona sullo stesso principio dell’attività di arricchimento con una chiamata al motore, arricchendo i dati della popolazione in entrata con un’offerta calcolata dal motore, prima di una consegna.

![](assets/int_offerengine_activity2.png)

Dopo aver configurato la query (consulta la [Guida ai flussi di lavoro](../../workflow/using/query.md)):

1. Aggiungi e apri un&#39;attività **[!UICONTROL Offer engine]** .
1. Completa i vari campi disponibili per specificare la chiamata ai parametri del motore di offerta (spazio di offerta, categoria o tema/i, data di contatto, numero di offerte da mantenere). Il motore calcola automaticamente le offerte da aggiungere in base a questi parametri.

   >[!NOTE]
   >
   >Avviso: se utilizzi questa attività, verranno memorizzate solo le proposte di offerta utilizzate nella consegna.

   ![](assets/int_offerengine_activity1.png)

1. Quindi configura un’attività di consegna corrispondente al canale scelto. Per ulteriori informazioni, consulta la sezione [Inserimento di una proposta di offerta in una consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .

## Offerte per cella {#offers-by-cell}

L’attività **[!UICONTROL Offers by cell]** ti consente di distribuire il gruppo in entrata (da una query, ad esempio) in diversi segmenti e di specificare un’offerta da presentare per ciascuno di questi segmenti.

A questo scopo, utilizza il seguente processo:

1. Aggiungi l’attività **[!UICONTROL Offers by cell]** una volta specificata la popolazione target, quindi aprila.
1. Nella scheda **[!UICONTROL General]** , seleziona lo spazio di offerta in cui desideri presentare le offerte.
1. Nella scheda **[!UICONTROL Cells]** , specifica i diversi sottoinsiemi utilizzando il pulsante **[!UICONTROL Add]** :

   * Specifica il gruppo di sottoinsiemi utilizzando le regole di filtraggio e limitazione disponibili.
   * Quindi seleziona l’offerta da presentare al set secondario. Le offerte disponibili sono quelle idonee nell’ambiente delle offerte selezionato al passaggio precedente.

      ![](assets/int_offer_per_cell1.png)

1. Quindi configura un’attività di consegna corrispondente al canale scelto. Per ulteriori informazioni, consulta la sezione [Inserimento di una proposta di offerta in una consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery) .
