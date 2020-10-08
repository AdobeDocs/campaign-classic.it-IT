---
title: Test A/B
seo-title: Test A/B
description: Test A/B
seo-description: null
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1350'
ht-degree: 2%

---


# Test A/B{#a-b-testing}

Se disponete di diversi contenuti per la consegna di un&#39;e-mail e desiderate scoprire quale versione avrà il maggiore impatto sulla popolazione di destinazione, potete inviare le diverse versioni ad alcuni dei vostri destinatari, quindi selezionare quello con il tasso di successo più alto e inviarlo agli altri destinatari.

In questo caso di utilizzo, confronteremo due contenuti di distribuzione delle e-mail tramite un flusso di lavoro di targeting. Il messaggio e il testo sono identici in entrambe le consegne: cambia solo il layout.

La popolazione interessata è divisa in tre parti: due gruppi di test e la popolazione rimanente. A ogni gruppo di test viene inviata una versione diversa della consegna. Dopo la consegna, viene configurato un periodo di attesa di 5 giorni prima di raccogliere i risultati delle migliori tariffe aperte. Il contenuto della distribuzione con il punteggio più alto viene quindi recuperato da uno script e inviato alla popolazione che non è stata utilizzata come gruppo di test.

Si prega di notare che i criteri che decideranno quale consegna è migliore possono essere modificati per soddisfare le vostre esigenze. Può trattarsi del tasso di apertura, del tasso di click-through, del tasso di sottoscrizione, della reattività, ecc.

Inoltre, il test dettagliato in questo caso d&#39;uso riguarda solo due consegne, ma potete testare tutte le versioni necessarie. È sufficiente aggiungere attività al flusso di lavoro.

Per creare il test A/B, eseguite i seguenti passaggi:

* [Passaggio 1: Creazione di un flusso di lavoro di targeting](#step-1--creating-a-targeting-workflow)
* [Passaggio 2: Configurazione dei campioni di popolazione](#step-2--configuring-population-samples)
* [Passaggio 3: Creazione di due modelli di consegna](#step-3--creating-two-delivery-templates)
* [Passaggio 4: Configurazione delle consegne nel flusso di lavoro](#step-4--configuring-the-deliveries-in-the-workflow)
* [Passaggio 5: Creazione dello script](#step-5--creating-the-script)
* [Passaggio 7: Avvio del flusso di lavoro](#step-7--starting-the-workflow)
* [Passaggio 8: Analisi del risultato](#step-8--analyzing-the-result).

## Step 1: Creating a targeting workflow {#step-1--creating-a-targeting-workflow}

È necessario creare il flusso di lavoro nella **[!UICONTROL Targeting and Workflows]** scheda di una campagna. È composta da un&#39; **[!UICONTROL Query]** attività, un&#39; **[!UICONTROL Split]** attività collegata a due **[!UICONTROL Email delivery]** attività, un&#39; **[!UICONTROL Wait]** attività, un&#39; **[!UICONTROL JavaScript code]** attività e un&#39; **[!UICONTROL Delivery]** attività.

1. Se non lo avete ancora fatto, create una campagna (per ulteriori informazioni, consultate questa [sezione](../../campaign/using/setting-up-marketing-campaigns.md#creating-a-campaign)).

   ![](assets/use_case_abtesting_targetwkfl_001.png)

1. Vai alla scheda **[!UICONTROL Targeting and Workflows]**. 

   ![](assets/use_case_abtesting_targetwkfl_002.png)

1. Modificate l’etichetta del flusso di lavoro esistente o fate clic **[!UICONTROL Add]** per crearne uno nuovo (per ulteriori informazioni, consultate questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#selecting-the-target-population)).

   ![](assets/use_case_abtesting_targetwkfl_003.png)

1. Utilizzate il mouse per trascinare e rilasciare attività nel diagramma del flusso di lavoro, incluse **[!UICONTROL Query]** (**[!UICONTROL Target]** scheda), una **[!UICONTROL Split]** (**[!UICONTROL Target]** scheda), due **[!UICONTROL Email deliveries]** (**[!UICONTROL Deliveries]** scheda), un&#39; **[!UICONTROL Wait]** attività (**[!UICONTROL Flow Control]** scheda), un&#39;attività ( **[!UICONTROL JavaScript code]****[!UICONTROL Actions]** **[!UICONTROL Delivery]****[!UICONTROL Actions]** scheda) e un&#39;attività (scheda) ).

![](assets/use_case_abtesting_targetwkfl_004.png)

## Passaggio 2: Configurazione dei campioni di popolazione {#step-2--configuring-population-samples}

### Configurazione dell&#39;attività Query {#configuring-the-query-activity}

* Double-click the **[!UICONTROL Query]** activity.

   ![](assets/use_case_abtesting_createrecipients_001.png)

* Fai clic sul **[!UICONTROL Edit query]** collegamento e seleziona i destinatari a cui vuoi indirizzare.

   ![](assets/use_case_abtesting_createrecipients_002.png)

* Collegate l&#39; **[!UICONTROL Query]** attività all&#39; **[!UICONTROL Split]** attività.

   ![](assets/use_case_abtesting_createrecipients_003.png)

### Configurazione dell&#39;attività Split {#configuring-the-split-activity}

Questa attività consente di creare diverse popolazioni: quella che riceve la consegna A, quella che riceve la consegna B, e la popolazione rimanente. Utilizzando la selezione casuale è possibile eseguire il targeting di una parte della popolazione di ciascuna consegna.

1. Creazione popolazione A:

   * Double-click the **[!UICONTROL Split]** activity.

      ![](assets/use_case_abtesting_createrecipients_004.png)

   * Nella scheda esistente, modificare l&#39;etichetta nella popolazione A.

      ![](assets/use_case_abtesting_createrecipients_005.png)

   * Selezionate l’ **[!UICONTROL Limit the selected records]** opzione.

      ![](assets/use_case_abtesting_createrecipients_006.png)

   * Fate clic sul **[!UICONTROL Edit]** collegamento, selezionate **[!UICONTROL Activate random sampling]**, quindi fate clic su **[!UICONTROL Next]**.

      ![](assets/use_case_abtesting_createrecipients_007.png)

   * Imposta la soglia su 10%, quindi fai clic su **[!UICONTROL Finish]**.

      ![](assets/use_case_abtesting_createrecipients_008.png)

1. Creazione popolazione B:

   * Fate clic **[!UICONTROL Add]** per creare una nuova scheda per la popolazione B.

      ![](assets/use_case_abtesting_createrecipients_009.png)

   * Limitare la popolazione al 10% come in precedenza.

      ![](assets/use_case_abtesting_createrecipients_010.png)

1. Creazione della popolazione rimanente:

   * Vai alla scheda **[!UICONTROL General]**. 

      ![](assets/use_case_abtesting_createrecipients_011.png)

   * Seleziona **[!UICONTROL Generate complement]**.

      ![](assets/use_case_abtesting_createrecipients_012.png)

   * Modificate l&#39;etichetta per specificare che la popolazione non include né A né B, quindi fate clic **[!UICONTROL OK]** per chiudere l&#39;attività.

      ![](assets/use_case_abtesting_createrecipients_013.png)

## Passaggio 3: Creazione di due modelli di consegna {#step-3--creating-two-delivery-templates}

Ora vogliamo creare due modelli di consegna. A ogni modello verrà fatto riferimento in un&#39; **[!UICONTROL Email delivery]** attività collegata all&#39; **[!UICONTROL Split]** attività. Per ulteriori informazioni, consulta questa [sezione](../../delivery/using/about-templates.md).

1. Go to the **[!UICONTROL Resources > Delivery template]** folder.
1. Duplica il modello di **[!UICONTROL Email]** consegna.

   ![](assets/use_case_abtesting_deliverymodel_001.png)

1. Create il contenuto da utilizzare per la consegna A.

   ![](assets/use_case_abtesting_deliverymodel_002.png)

1. Ripetete questa procedura per creare un modello per la consegna B.

   ![](assets/use_case_abtesting_deliverymodel_003.png)

## Passaggio 4: Configurazione delle consegne nel flusso di lavoro {#step-4--configuring-the-deliveries-in-the-workflow}

Il passo successivo consiste nel configurare le consegne. Sono destinati alle tre popolazioni create nella fase precedente: [Passaggio 2: Configurazione dei campioni](#step-2--configuring-population-samples)di popolazione. Le prime due consegne consentono di inviare contenuti diversi alla popolazione A e B. La terza consegna è destinata alla popolazione che non ha ricevuto né A né B. Il contenuto verrà calcolato da uno script e sarà identico a A o B, a seconda di quale dei due avrà ottenuto il punteggio più alto. Dobbiamo configurare un periodo di attesa per la terza consegna, per conoscere il risultato delle consegne A e B. Per questo motivo la terza consegna include un&#39; **[!UICONTROL Wait]** attività.

1. Andate all&#39; **[!UICONTROL Split]** attività e collegate la transizione per la popolazione A a una delle consegne di e-mail già presenti nel flusso di lavoro.

   ![](assets/use_case_abtesting_createdeliveries_001.png)

1. Fate doppio clic sulla consegna per aprirla.
1. Utilizzando l&#39;elenco a discesa, selezionate il modello per la consegna A.

   ![](assets/use_case_abtesting_createdeliveries_003.png)

1. Fate clic **[!UICONTROL Continue]** per visualizzare la consegna, quindi salvatela.

   ![](assets/use_case_abtesting_createdeliveries_002.png)

1. Collegate la transizione dell&#39; **[!UICONTROL Split]** attività destinata alla popolazione B alla seconda consegna tramite e-mail.

   ![](assets/use_case_abtesting_createdeliveries_004.png)

1. Aprite la consegna e selezionate il modello nella consegna B, quindi salvate la consegna.

   ![](assets/use_case_abtesting_createdeliveries_005.png)

1. Collegare la transizione destinata alla popolazione rimanente all&#39; **[!UICONTROL Wait]** attività.

   ![](assets/use_case_abtesting_createdeliveries_006.png)

1. Aprite l&#39; **[!UICONTROL Wait]** attività e configurate un periodo di attesa di 5 giorni.

   ![](assets/use_case_abtesting_createdeliveries_007.png)

1. Collegate l&#39; **[!UICONTROL Wait]** attività all&#39; **[!UICONTROL JavaScript code]** attività.

   ![](assets/use_case_abtesting_createdeliveries_008.png)

## Passaggio 5: Creazione dello script {#step-5--creating-the-script}

La scelta del contenuto di distribuzione destinato alla popolazione rimanente viene calcolata da uno script. Questo script recupera le informazioni relative alla distribuzione con la frequenza più elevata di aperture e copia il contenuto nella distribuzione finale.

### Esempio di script {#example-of-a-script}

Lo script seguente può essere utilizzato come nel flusso di lavoro di targeting. For more on this, refer to [Implementation](#implementation).

```
 // query the database to find the winner (best open rate)
   var winner = xtk.queryDef.create(
     <queryDef schema="nms:delivery" operation="get">
       <select>
         <node expr="@id"/>
         <node expr="@label"/>
         <node expr="[@operation-id]"/>
         <node expr="[@workflow-id]"/>
       </select>
       <where>
         <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
       </where>
       <orderBy>
         <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
       </orderBy>
     </queryDef>).ExecuteQuery()
   
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)

   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"

   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]

   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
 
   // save the delivery in database
   delivery.save()
 
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
```

Per una spiegazione dettagliata dello script, fare riferimento a [Dettagli dello script](#details-of-the-script).

### Implementazione {#implementation}

1. Aprite l&#39; **[!UICONTROL JavaScript code]** attività.
1. Copiare lo script offerto in [Esempio di script](#example-of-a-script) nella **[!UICONTROL JavaScript code]** finestra.

   ![](assets/use_case_abtesting_configscript_002.png)

1. Nel **[!UICONTROL Label]** campo, immettere il nome dello script, ovvero

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Chiudete l&#39; **[!UICONTROL JavaScript code]** attività.
1. Salva il flusso di lavoro.

### Dettagli dello script {#details-of-the-script}

In questa sezione vengono descritte le varie parti dello script e la relativa modalità operativa.

* La prima parte dello script è una query. Il comando **queryDef** consente di recuperare dalla tabella **NmsDelivery** le consegne create eseguendo il flusso di lavoro di targeting e di ordinarle in base al tasso stimato di apertura, quindi le informazioni dalla consegna con il tasso più alto di aperture vengono recuperate.

   ```
   // query the database to find the winner (best open rate)
      var winner = xtk.queryDef.create(
        <queryDef schema="nms:delivery" operation="get">
          <select>
            <node expr="@id"/>
            <node expr="@label"/>
            <node expr="[@operation-id]"/>
          </select>
          <where>
            <condition expr={"@FCP=0 and [@workflow-id]= " + instance.id}/>
          </where>
          <orderBy>
            <node expr="[indicators/@estimatedRecipientOpenRatio]" sortDesc="true"/>
          </orderBy>
        </queryDef>).ExecuteQuery()
   ```

* La distribuzione con la frequenza più elevata di aperture viene duplicata.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* L&#39;etichetta della consegna duplicata viene modificata e vi viene aggiunta la parola **finale** .

   ```
   // append 'final' to the delivery label
   delivery.label = winner.@label + " final"
   ```

* La distribuzione viene copiata nel dashboard della campagna.

   ```
   // link the delivery to the operation to make sure it will be displayed in
   // the campaign dashboard. This attribute needs to be set manually here since 
   // the Duplicate() method has reset it to its default value => 0
   delivery.operation_id = winner.@["operation-id"]
   delivery.workflow_id = winner.@["workflow-id"]
   ```

   ```
   // adjust some delivery parameters to make it compatible with the 
   // "Prepare and start" option selected in the Delivery tab of this activity
   delivery.scheduling.validationMode = "manual"
   delivery.scheduling.delayed = 0
   ```

* La consegna viene salvata nel database.

   ```
   // save the delivery in database
   delivery.save()
   ```

* L’identificatore univoco della consegna duplicata viene memorizzato nella variabile del flusso di lavoro.

   ```
   // store the new delivery Id in event variables
   vars.deliveryId = delivery.id
   ```

### Altri criteri di selezione {#other-selection-criteria}

L&#39;esempio precedente consente di selezionare il contenuto di una consegna in base al tasso di apertura delle e-mail. Puoi adattarlo in base ad altri indicatori specifici per la consegna:

* Velocità effettiva clic ottimale: `[indicators/@recipientClickRatio]`,
* Velocità di reattività più elevata (apertura e clic dell’e-mail nel messaggio): `[indicators/@reactivity]`,
* Tasso di reclamo più basso: `[indicators/@refusedRatio]` (utilizzate il valore false per l&#39;attributo sortDesc),
* Tasso di conversione più elevato: `[indicators/@transactionRatio]`,
* Numero di pagine visitate dopo la ricezione di un messaggio: `[indicators/@totalWebPage]`,
* Tasso di annullamento sottoscrizione inferiore: `[indicators/@optOutRatio]`,
* Importo transazione: `[indicators/@amount]`.

## Passaggio 6: Definizione della consegna finale {#step-6--defining-the-final-delivery}

Una volta creato lo script per selezionare il vincitore del test A/B, è possibile definire i parametri del recapito finale.

1. Collegate l&#39; **[!UICONTROL JavaScript code]** attività all&#39; **[!UICONTROL Delivery]** attività rimanente.
1. Aprite l&#39; **[!UICONTROL Delivery]** attività.
1. Deselezionate l&#39; **[!UICONTROL Generate an outbound transition]** opzione per completare il flusso di lavoro con questa attività.
1. Lasciate le altre opzioni ai valori predefiniti.

   ![](assets/ab_test_final_delivery.png)

Preparando la consegna specificata nella transizione (definita tramite l&#39; **[!UICONTROL Javascript Code]** attività), potrai quindi approvarla e avviare l&#39;invio, come descritto nel passaggio successivo.

## Passaggio 7: Avvio del flusso di lavoro {#step-7--starting-the-workflow}

1. Fate clic **[!UICONTROL Start]** sul flusso di lavoro.

   ![](assets/use_case_abtesting_startwkfl_001.png)

1. Approvare target e contenuti per le consegne A e B tramite il dashboard della campagna.
1. Conferma la consegna.
1. Attendete fino alla fine del periodo di 5 giorni per scoprire quale contenuto è stato calcolato dopo i risultati dell&#39;apertura della consegna.

   ![](assets/use_case_abtesting_startwkfl_002.png)

   In questo caso, è stato scelto il modello B.

1. Una volta determinato il contenuto della terza distribuzione, approvate la destinazione e il contenuto.

## Passaggio 8: Analisi del risultato {#step-8--analyzing-the-result}

Una volta inviate le consegne di test, potete verificare a quali destinatari sono stati inviati e se sono stati aperti o meno.

* Per scoprire quali destinatari sono stati assegnati, aprite un invio tramite il dashboard della campagna e fate clic sulla **[!UICONTROL Delivery]** scheda.

   ![](assets/use_case_abtesting_analysis_001.png)

* Per verificare se la consegna è stata aperta, andate alla **[!UICONTROL Tracking]** scheda.

   ![](assets/use_case_abtesting_analysis_002.png)

* Confronta con l&#39;altra consegna.

   ![](assets/use_case_abtesting_analysis_003.png)

Nel nostro esempio, la consegna B ha ottenuto il massimo tasso di apertura. Ciò significa che il contenuto B verrà utilizzato per la distribuzione finale.

![](assets/use_case_abtesting_analysis_004.png)

