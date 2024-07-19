---
product: campaign
title: Creare lo script
description: Scopri come eseguire il test A/B tramite un caso d’uso dedicato
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: A/B Testing
role: User
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 3%

---

# Test AB: creare lo script {#step-5--creating-the-script}


La scelta del contenuto di consegna destinato al gruppo rimanente viene calcolata da uno script. Questo script recupera le informazioni relative alla consegna con il tasso più elevato di aperture e copia il contenuto nella consegna finale.

## Esempio di script {#example-of-a-script}

Lo script seguente può essere utilizzato così come è nel flusso di lavoro di targeting. Per ulteriori informazioni al riguardo, consulta [questa sezione](#implementation).

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

Per una spiegazione dettagliata dello script, consultare [questa sezione](#details-of-the-script).

## Implementazione {#implementation}

1. Apri l&#39;attività **[!UICONTROL JavaScript code]**.
1. Copiare lo script offerto in [Esempio di uno script](#example-of-a-script) nella finestra **[!UICONTROL JavaScript code]**.

   ![](assets/use_case_abtesting_configscript_002.png)

1. Nel campo **[!UICONTROL Label]**, immettere il nome dello script, ad esempio

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Chiudere l&#39;attività **[!UICONTROL JavaScript code]**.
1. Salva il flusso di lavoro.

## Dettagli dello script {#details-of-the-script}

Questa sezione descrive le varie parti dello script e la relativa modalità operativa.

* La prima parte dello script è una query. Il comando **queryDef** consente di recuperare dalla tabella **NmsDelivery** le consegne create eseguendo il flusso di lavoro di targeting e di ordinarle in base alla frequenza stimata di aperture, quindi vengono recuperate le informazioni della consegna con la frequenza più elevata di aperture.

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

* La consegna con la più alta frequenza di aperture viene duplicata.

  ```
   // create a new delivery object and initialize it by doing a copy of
   // the winner delivery
  var delivery = nms.delivery.create()
  delivery.Duplicate("nms:delivery|" + winner.@id)
  ```

* L&#39;etichetta della consegna duplicata è stata modificata e vi è stata aggiunta la parola **final**.

  ```
  // append 'final' to the delivery label
  delivery.label = winner.@label + " final"
  ```

* La consegna viene copiata nel dashboard della campagna.

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

## Altri criteri di selezione {#other-selection-criteria}

L’esempio precedente ti consente di selezionare il contenuto di una consegna in base alla frequenza di aperture delle e-mail. Puoi adattarlo per basarti su altri indicatori specifici per la consegna:

* Throughput clic migliore: `[indicators/@recipientClickRatio]`,
* Tasso di reattività massimo (apertura e clic dell&#39;e-mail nel messaggio): `[indicators/@reactivity]`,
* Frequenza reclami più bassa: `[indicators/@refusedRatio]` (utilizzare il valore false per l&#39;attributo sortDesc),
* Tasso di conversione massimo: `[indicators/@transactionRatio]`,
* Numero di pagine visitate dopo la ricezione di un messaggio: `[indicators/@totalWebPage]`,
* Percentuale di annullamento abbonamento più bassa: `[indicators/@optOutRatio]`,
* Importo transazione: `[indicators/@amount]`.

Ora puoi definire la consegna finale. [Ulteriori informazioni](a-b-testing-uc-final-delivery.md).
