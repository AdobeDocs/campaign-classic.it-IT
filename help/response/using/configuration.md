---
product: campaign
title: Configurare Campaign Response Manager
description: Scopri come configurare Campaign Response Manager
feature: Campaigns
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Configurare Campaign Response Manager{#configuration}



Questa sezione è destinata alle persone responsabili della configurazione della gestione della risposta. È necessario disporre di una certa quantità di conoscenze sull&#39;estensione degli schemi, la definizione dei flussi di lavoro e la programmazione SQL.

Questo consente di comprendere come adattare il modello dati standard alla natura specifica di una tabella di transazione esterna ad Adobe Campaign con la tabella dei singoli utenti. Questa tabella di singoli utenti può coincidere con la tabella degli utenti singoli disponibili in Adobe Campaign o con una tabella diversa

L&#39;ipotesi di misurazione viene avviata dal flusso di lavoro del processo di operazione ( **[!UICONTROL operationMgt]** ). Ogni ipotesi rappresenta un processo separato eseguito in modo asincrono con uno stato di esecuzione (In corso di modifica, In sospeso, Completato, Non riuscito, ecc.) e controllata da un modulo di pianificazione che gestisce i vincoli di priorità, la limitazione del numero di processi simultanei, la pagina a bassa attività e l’esecuzione automatica con frequenza.

## Configurare gli schemi {#configuring-schemas}

>[!CAUTION]
>
>Non modificare gli schemi integrati dell’applicazione, ma utilizzare il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento di aggiornamenti futuri dell’applicazione. Questo può causare malfunzionamenti durante l’utilizzo di Adobe Campaign.

L’integrazione dell’applicazione è necessaria prima di utilizzare il modulo di reazione per definire le varie tabelle (transazioni, dettagli della transazione) da misurare e il loro rapporto con consegne, offerte e singoli utenti.

### Schemi standard {#standard-schemas}

Lo schema predefinito **[!UICONTROL nms:remaMatch]** contiene la tabella del registro delle reazioni, ovvero la relazione tra singoli utenti, l&#39;ipotesi e la tabella delle transazioni. Questo schema è utilizzato come schema di ereditarietà per la tabella di destinazione finale dei registri di reazione.

Anche lo schema **[!UICONTROL nms:remaMatchRcp]** è standard e contiene l&#39;archiviazione dei registri di reazione per i destinatari di Adobe Campaign ( **[!UICONTROL nms:recipient]** ). Per essere utilizzata, deve essere estesa per essere mappata a una tabella di transazione (contenente acquisti, ecc.).

### Tabelle delle transazioni e dettagli delle transazioni {#transaction-tables-and-transaction-details}

La tabella delle operazioni deve includere collegamenti diretti verso singoli utenti.

È inoltre possibile aggiungere una tabella contenente i dettagli della transazione. Questo non è collegato direttamente ai singoli individui.

Se ad esempio si considera un incasso, la tabella delle transazioni viene collegata a un contatto (tabella degli incassi) e la tabella delle linee degli incassi viene collegata solo alla tabella degli incassi (tabella dei dettagli). È quindi possibile configurare l&#39;ipotesi direttamente al livello in cui la tabella della riga di ricezione è collegata alla tabella di ricezione.

>[!NOTE]
>
>Se si desidera mantenere l&#39;identificatore di ricezione che descrive il comportamento previsto nelle ipotesi, è possibile estendere il modello di tabella nms:remaMatchRcp per aggiungervi l&#39;identificatore (in questo caso, a questi campi non è collegato alcun calcolo del ROI).

Si consiglia vivamente di aggiungere una data evento.

Lo schema seguente mostra i join tra le diverse tabelle al termine della configurazione:

![](assets/response_data_model.png)

### Gestione della risposta e destinatari {#response-management-with-adobe-campaign-recipients}

In questo esempio, integreremo una tabella di acquisti nel nostro modulo di gestione delle risposte utilizzando la tabella dei destinatari integrata di Adobe Campaign **[!UICONTROL nms:recipient]**.

La tabella dei registri di risposta su un destinatario **[!UICONTROL nms:remaMatchRcp]** è stata estesa per aggiungere un collegamento allo schema della tabella di acquisto. Nell&#39;esempio seguente, la tabella degli acquisti è denominata **demo:purchase**.

1. Tramite Adobe Campaign Explorer, seleziona **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Fare clic con il pulsante destro del mouse su **Destinatario**, quindi selezionare **[!UICONTROL Actions]** e **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. È possibile personalizzare **[!UICONTROL Extension namespace]** nella finestra successiva, quindi fare clic su **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. Nella categoria **[!UICONTROL Response management]**, assicurarsi che la casella **[!UICONTROL Generate a storage schema for reactions]** sia selezionata.

   Quindi fare clic su **[!UICONTROL Define additional fields...]** per selezionare le tabelle di transazione correlate e aggiungere i campi desiderati all&#39;estensione dello schema nms:remaMatchRcp.

   ![](assets/delivery_mapping3.png)

Lo schema creato si presenta come segue:

```
<srcSchema _cs="Reactions (Recipients) (cus)" entitySchema="xtk:srcSchema" extendedSchema="nms:remaMatchRcp" 
img="nms:remaMatch.png" implements="xtk:persist" label="Reactions (Recipients)" mappingType="sql"
name="remaMatchRcp" namespace="cus">  
 <element label="Reactions (Recipients)" name="remaMatchRcp">    
  <key internal="true" name="match">      
   <keyfield xlink="hypothesis"/>      
   <keyfield xlink="broadLog"/>      
   <keyfield xlink="proposition"/>    
  </key>    
  <attribute label="Quantity" name="quantity" type="long"/>    
  <element name="purchase" target="demo:purchase" type="link"/>    
  <element name="hypothesis" revLabel="Reactions (Recipients)" revLink="remaMatchRcp"/>    
  <element applicableIf="HasPackage('nms:coreInteraction')" label="Proposition" name="proposition" target="nms:propositionRcp" type="link"/>   
  <element desc="Message (Delivery log)" label="Message" name="broadLog" target="nms:broadLogRcp" type="link"/>    
  <element label="Respondent" name="responder" target="nms:recipient" type="link"/>  
 </element>  
 <createdBy _cs="Administrator (admin)"/>  
 <modifiedBy _cs="Administrator (admin)"/>
</srcSchema>
```

### Gestione delle risposte con una tabella dei destinatari personalizzata {#response-management-with-a-personalized-recipient-table}

In questo esempio, integreremo una tabella acquisti nel nostro modulo di gestione delle risposte utilizzando una tabella di singoli utenti diversa dalla tabella dei destinatari disponibile in Adobe Campaign.

* Creare un nuovo schema di log delle risposte derivato dallo schema **[!UICONTROL nms:remaMatch]**.

  Poiché la tabella dei singoli utenti è diversa dalla tabella dei destinatari di Adobe Campaign, è necessario creare un nuovo schema dei registri di risposta basati sullo schema **[!UICONTROL nms:remaMatch]**. Quindi completalo con i collegamenti verso i registri di consegna e la tabella di acquisto.

  Nell&#39;esempio seguente verranno utilizzati lo schema **demo:broadLogPers** e la tabella delle transazioni **demo:purchase**:

  ```
  <srcSchema desc="Linking of a recipient transaction to a hypothesis"    
  img="nms:remaMatch.png" label="Responses on persons" labelSingular="Responses on a person" name="remaMatchPers" namespace="nms">
    <element name="remaMatchPers" template="nms:remaMatch">
      <key internal="true" name="match">
        <keyfield xlink="hypothesis"/>
       <keyfield xlink="purchase"/>
      </key>
  
      <element name="hypothesis" revLabel="Response logs for persons" revLink="remaMatchPers"/>
      <element applicableIf="HasPackage('nms:interaction')" label="Proposition" name="proposition"
               target="demo:propositionPers" type="link"/>
      <element label="Delivery log" name="broadLog" target="demo:broadLogPers" type="link"/>
    </element>
  </srcSchema>
  ```

* Modificare il modulo di ipotesi nello schema **[!UICONTROL nms:remaHypothesis]**.

  Per impostazione predefinita, l’elenco dei registri di risposta è visibile nei registri dei destinatari. Pertanto, devi modificare il modulo dell’ipotesi per visualizzare i nuovi registri di risposta creati durante il passaggio precedente.

  Ad esempio:

  ```
   <container type="visibleGroup" visibleIf="[context/@remaMatchStorage]= 'demo:remaMatchPers'">
                <input hideEditButtons="true" img="nms:remaMatch.png" nolabel="true" refresh="true"
                 toolbarCaption="Responses generated by the hypothesis" type="linklist"
                 xpath="remaMatchPers">
            <input xpath="[.]"/>
            <input xpath="@controlGroup"/>
          </input>
     </container> 
  ```

## Gestione indicatori {#managing-indicators}

Il modulo Response Manager viene fornito con un elenco di indicatori predefiniti. Tuttavia, puoi aggiungere altri indicatori di misurazione personalizzati.

A questo scopo, devi estendere la tabella delle ipotesi inserendo due campi per ogni nuovo indicatore:

* la prima per la popolazione bersaglio,
* il secondo per il gruppo di controllo.

Ad esempio:

```
<srcSchema entitySchema="xtk:srcSchema" extendedSchema="nms:remaHypothesis" label="Measurement hypothesis" 
md5="1D4DED54FF8EC2432AED6736EDE6F547" name="remaHypothesis" namespace="demo" xtkschema="xtk:srcSchema">  
    <element name="remaHypothesis">    
        <element name="indicators">      
            <!-- Quantity -->      
            <attribute label="Total contacted" name="contactReactedTotalQuantity" type="long"/>
            <attribute label="Total number of people in the control group" name="proofReactedTotalquantity" type="long"/> 
        </element> 
    </element>
</srcSchema>
```
