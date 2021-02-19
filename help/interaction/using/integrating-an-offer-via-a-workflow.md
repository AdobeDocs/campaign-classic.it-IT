---
solution: Campaign Classic
product: campaign
title: Integrazione di un’offerta tramite un flusso di lavoro
description: Integrazione di un’offerta tramite un flusso di lavoro
audience: interaction
content-type: reference
topic-tags: delivering-an-offer
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1043'
ht-degree: 3%

---


# Integrazione di un’offerta tramite un flusso di lavoro{#integrating-an-offer-via-a-workflow}

Al di fuori dell&#39;attività di distribuzione stessa, diverse attività del flusso di lavoro consentono di definire il modo in cui vengono presentate le offerte:

* Profilo di consegna
* Enrichment
* Motore di offerta
* Offerte per cella

## Profilo di consegna {#delivery-outline}

L&#39;attività del profilo di consegna, disponibile nei flussi di lavoro della campagna, consente di presentare offerte alle quali viene fatto riferimento in un profilo di consegna a partire dalla campagna corrente in corso.

1. In un flusso di lavoro, aggiungete un&#39;attività di struttura della consegna prima di aggiungere un&#39;attività di consegna.
1. Nell&#39;attività del profilo di consegna, specificate il profilo da utilizzare.

   Per ulteriori informazioni sulla specifica dei contorni di consegna, fare riferimento alla guida [Campaign - MRM](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

1. Completa i campi disponibili in base alla consegna.
1. Esistono due casi possibili:

   * Se desiderate chiamare il motore delle offerte, selezionate la casella **[!UICONTROL Restrict the number of propositions selected]**. Specificate lo spazio dell&#39;offerta e il numero di proposte che verranno presentate nella consegna.

      I pesi delle offerte e le regole di ammissibilità saranno prese in considerazione dal motore delle offerte.

   * Se non selezionate la casella, tutte le offerte nel profilo di consegna verranno presentate senza effettuare una chiamata al motore delle offerte.
   >[!NOTE]
   >
   >L&#39;anteprima tiene conto del numero di offerte specificate nella consegna. Quando si esegue un flusso di lavoro, viene preso in considerazione il numero specificato nel profilo di consegna.

   ![](assets/int_compo_offre_wf1.png)

## Enrichment {#enrichment}

L&#39;attività di arricchimento consente di aggiungere offerte o collegamenti alle offerte per i destinatari della distribuzione.

>[!NOTE]
>
>Per ulteriori informazioni sull&#39;attività di arricchimento, fare riferimento alla documentazione dedicata nella [Guida ai flussi di lavoro](../../workflow/using/enrichment.md).

Ad esempio, è possibile arricchire i dati per una query del destinatario prima della consegna.

![](assets/int_enrichment_offer1.png)

Esistono due metodi per specificare le proposte di offerta.

* Specifica di un&#39;offerta o di una chiamata al motore di offerta.
* Riferimento a un collegamento a un&#39;offerta.

### Specifica di un&#39;offerta o di una chiamata al motore di offerta {#specifying-an-offer-or-a-call-to-the-offer-engine}

Dopo aver configurato la query (fare riferimento alla [Guida ai flussi di lavoro](../../workflow/using/query.md)):

1. Aggiungere e aprire un&#39;attività di arricchimento.
1. Nella scheda **[!UICONTROL Enrichment]**, seleziona **[!UICONTROL Add data]**.
1. Selezionare **[!UICONTROL An offer proposition]** nei tipi di dati da aggiungere.

   ![](assets/int_enrichment_offer2.png)

1. Specificate un identificatore e un&#39;etichetta per la proposta che verrà aggiunta.
1. Specificate la selezione dell&#39;offerta. Sono disponibili due opzioni:

   * **[!UICONTROL Search for the best offer in a category]** : selezionate questa opzione e specificate i parametri di chiamata del motore di offerte (spazio di offerta, categoria o tema/i, data di contatto, numero di offerte da mantenere). Il motore calcolerà automaticamente le offerte da aggiungere in base a questi parametri. È consigliabile completare il campo **[!UICONTROL Category]** o **[!UICONTROL Theme]**, anziché entrambi allo stesso tempo.

      ![](assets/int_enrichment_offer3.png)

   * **[!UICONTROL A predefined offer]** : selezionate questa opzione e specificate uno spazio di offerta, un&#39;offerta specifica e una data di contatto per configurare direttamente l&#39;offerta che desiderate aggiungere, senza chiamare il motore delle offerte.

      ![](assets/int_enrichment_offer4.png)

1. Quindi configurate un&#39;attività di consegna che corrisponda al canale scelto. Per ulteriori informazioni, consultare la sezione [Inserimento di una proposta di offerta in una sezione consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >Il numero di proposte disponibili per l&#39;anteprima dipende dalla configurazione effettuata nell&#39;attività di arricchimento, piuttosto che da qualsiasi possibile configurazione effettuata direttamente nella consegna.

### Riferimento a un collegamento a un&#39;offerta {#referencing-a-link-to-an-offer}

Potete anche fare riferimento a un collegamento a un&#39;offerta in un&#39;attività di arricchimento.

A tal fine, attenersi alla procedura seguente:

1. Selezionare **[!UICONTROL Add data]** nella scheda **[!UICONTROL Enrichment]** dell&#39;attività.
1. Nella finestra in cui si sceglie il tipo di dati da aggiungere, selezionare **[!UICONTROL A link]**.
1. Seleziona il tipo di collegamento che desideri stabilire e la destinazione. In questo caso, la destinazione è lo schema dell&#39;offerta.

   ![](assets/int_enrichment_link1.png)

1. Specificate il join tra i dati della tabella in entrata nell&#39;attività di arricchimento (qui la tabella dei destinatari) e la tabella delle offerte. Ad esempio, potete collegare un codice di offerta a un destinatario.

   ![](assets/int_enrichment_link2.png)

1. Quindi configurate un&#39;attività di consegna che corrisponda al canale scelto. Per ulteriori informazioni, consultare la sezione [Inserimento di una proposta di offerta in una sezione consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

   >[!NOTE]
   >
   >Il numero di proposte disponibili per l&#39;anteprima dipende dalla configurazione eseguita nella distribuzione.

### Memorizzazione delle classificazioni e dei pesi delle offerte {#storing-offer-rankings-and-weights}

Per impostazione predefinita, quando si utilizza un&#39;attività **arricchimento** per distribuire le offerte, le loro classificazioni e i loro pesi non vengono memorizzati nella tabella delle proposte.

>[!NOTE]
>
>Ricorda: Per impostazione predefinita, l&#39;attività **[!UICONTROL Offer engine]** memorizza tali informazioni.

Tuttavia, potete memorizzare queste informazioni nel modo seguente:

1. Crea una chiamata al motore delle offerte in un&#39;attività di arricchimento inserita dopo una query e prima di un&#39;attività di consegna. Fare riferimento alla sezione [Specifica di un&#39;offerta o di una chiamata al motore dell&#39;offerta](../../interaction/using/integrating-an-offer-via-a-workflow.md#specifying-an-offer-or-a-call-to-the-offer-engine).
1. Nella finestra principale dell&#39;attività, selezionare **[!UICONTROL Edit additional data...]**.

   ![](assets/ita_enrichment_rankweight_1.png)

1. Aggiungete le colonne **[!UICONTROL @rank]** per la classificazione e **[!UICONTROL @weight]** per lo spessore dell&#39;offerta.

   ![](assets/ita_enrichment_rankweight_2.png)

1. Conferma l’aggiunta e salva il flusso di lavoro.

La consegna memorizza automaticamente la classifica e il peso delle offerte. Queste informazioni sono visibili nella scheda **[!UICONTROL Offers]** della consegna.

## Motore di offerta {#offer-engine}

L&#39;attività **[!UICONTROL Offer engine]** consente inoltre di specificare una chiamata al motore delle offerte prima della consegna.

Questa attività funziona sullo stesso principio dell&#39;attività di arricchimento con una chiamata al motore, arricchendo i dati della popolazione in entrata con un&#39;offerta calcolata dal motore, prima della consegna.

![](assets/int_offerengine_activity2.png)

Dopo aver configurato la query (fare riferimento alla [Guida ai flussi di lavoro](../../workflow/using/query.md)):

1. Aggiungete e aprite un&#39;attività **[!UICONTROL Offer engine]**.
1. Completate i vari campi disponibili per specificare i parametri del motore di chiamata (spazio di offerta, categoria o tema/i, data di contatto, numero di offerte da mantenere). Il motore calcolerà automaticamente le offerte da aggiungere in base a questi parametri.

   >[!NOTE]
   >
   >Avviso: se utilizzate questa attività, verranno memorizzate solo le proposte di offerta utilizzate nella consegna.

   ![](assets/int_offerengine_activity1.png)

1. Quindi configurate un&#39;attività di consegna che corrisponda al canale scelto. Per ulteriori informazioni, consultare la sezione [Inserimento di una proposta di offerta in una sezione consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

## Offerte per cella {#offers-by-cell}

L&#39;attività **[!UICONTROL Offers by cell]** consente di distribuire la popolazione in entrata (ad esempio da una query) in diversi segmenti e di specificare un&#39;offerta da presentare per ciascuno di questi segmenti.

A tal fine, attenersi alla procedura seguente:

1. Aggiungete l&#39;attività **[!UICONTROL Offers by cell]** una volta specificata la popolazione di destinazione, quindi apritela.
1. Nella scheda **[!UICONTROL General]**, selezionate lo spazio di offerta su cui desiderate presentare le offerte.
1. Nella scheda **[!UICONTROL Cells]**, specificare i diversi sottoinsiemi utilizzando il pulsante **[!UICONTROL Add]**:

   * Specificate la popolazione di sottoinsiemi utilizzando le regole di filtraggio e limitazione disponibili.
   * Selezionate quindi l’offerta da presentare al set secondario. Le offerte disponibili sono quelle idonee nell&#39;ambiente delle offerte selezionato al passaggio precedente.

      ![](assets/int_offer_per_cell1.png)

1. Quindi configurate un&#39;attività di consegna che corrisponda al canale scelto. Per ulteriori informazioni, consultare la sezione [Inserimento di una proposta di offerta in una sezione consegna](../../interaction/using/integrating-an-offer-via-the-wizard.md#inserting-an-offer-proposition-into-a-delivery).

