---
product: campaign
title: Creare lo script
description: Scopri come eseguire test A/B tramite un caso d’uso dedicato
feature: A/B Testing
exl-id: 4143d1b7-0e2b-4672-ad57-e4d7f8fea028
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 4%

---

# Creare lo script {#step-5--creating-the-script}

![](../../assets/common.svg)

La scelta del contenuto di consegna destinato alla popolazione rimanente viene calcolata da uno script. Questo script recupera le informazioni relative alla consegna con il tasso di apertura più elevato e copia il contenuto nella consegna finale.

## Esempio di script {#example-of-a-script}

Il seguente script può essere utilizzato così come è nel flusso di lavoro di targeting. Per ulteriori informazioni al riguardo, consulta [questa sezione](#implementation).

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

Per una spiegazione dettagliata dello script, fare riferimento a [questa sezione](#details-of-the-script).

## Implementazione {#implementation}

1. Apri il tuo **[!UICONTROL JavaScript code]** attività.
1. Copia lo script offerto in [Esempio di script](#example-of-a-script) nel **[!UICONTROL JavaScript code]** finestra.

   ![](assets/use_case_abtesting_configscript_002.png)

1. In **[!UICONTROL Label]** immettere il nome dello script, ovvero

   ```
   <%= vars.deliveryId %>
   ```

   ![](assets/use_case_abtesting_configscript_003.png)

1. Chiudi **[!UICONTROL JavaScript code]** attività.
1. Salva il flusso di lavoro.

## Dettagli dello script {#details-of-the-script}

Questa sezione descrive le varie parti dello script e la relativa modalità operativa.

* La prima parte dello script è una query. La **queryDef** consente di recuperare dal **NmsDelivery** tabella delle consegne create eseguendo il flusso di lavoro di targeting e per ordinarle in base al tasso di apertura stimato, vengono recuperate le informazioni dalla consegna con il tasso di apertura più elevato.

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

* La consegna con il tasso di apertura più alto è duplicata.

   ```
    // create a new delivery object and initialize it by doing a copy of
    // the winner delivery
   var delivery = nms.delivery.create()
   delivery.Duplicate("nms:delivery|" + winner.@id)
   ```

* L’etichetta della consegna duplicata viene modificata e la parola **finale** viene aggiunto a esso.

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

L’esempio precedente ti consente di selezionare il contenuto di una consegna in base al tasso di apertura delle e-mail. Puoi adattarlo in base ad altri indicatori specifici per la consegna:

* Velocità effettiva di clic migliore: `[indicators/@recipientClickRatio]`,
* Tasso di reattività più alto (apertura e-mail e clic nel messaggio): `[indicators/@reactivity]`,
* Tasso di reclamo inferiore: `[indicators/@refusedRatio]` (usa il valore false per l&#39;attributo sortDesc),
* Tasso di conversione più alto: `[indicators/@transactionRatio]`,
* Numero di pagine visitate dopo la ricezione di un messaggio: `[indicators/@totalWebPage]`,
* Tasso minimo di annullamento sottoscrizione: `[indicators/@optOutRatio]`,
* Importo transazione: `[indicators/@amount]`.

Ora puoi definire la consegna finale. [Ulteriori informazioni](a-b-testing-uc-final-delivery.md).
