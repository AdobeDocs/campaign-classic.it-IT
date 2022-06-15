---
product: campaign
title: Configurare Campaign Response Manager
description: Scopri come configurare Campaign Response Manager
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1a115ca9-2532-4bd3-be77-814e43250c51
source-git-commit: d36e1881726af6238c4e0caecb7b299b594691f2
workflow-type: tm+mt
source-wordcount: '750'
ht-degree: 0%

---

# Configurare Campaign Response Manager{#configuration}

![](../../assets/common.svg)

Questa sezione è destinata alle persone responsabili della configurazione della gestione della risposta. Si presuppone una certa quantità di conoscenze sull&#39;estensione degli schemi, sulla definizione dei flussi di lavoro e sulla programmazione SQL.

Questo ti consente di comprendere come adattare il modello dati standard alla natura specifica di una tabella di transazioni esterna ad Adobe Campaign con la tabella dei singoli utenti. Questa tabella può coincidere con la tabella dei singoli utenti disponibile in Adobe Campaign o con una tabella diversa

L&#39;ipotesi di misurazione viene lanciata dal flusso di lavoro del processo di operazione ( **[!UICONTROL operationMgt]** ). Ciascuna ipotesi rappresenta un processo separato eseguito in modo asincrono con uno stato di esecuzione (In corso di modifica, In sospeso, Completato, Non riuscito, ecc.) e controllata da un programmatore che gestisce i vincoli di priorità, la limitazione del numero di processi simultanei, la pagina a bassa attività e l&#39;esecuzione automatica con frequenza.

## Configurare gli schemi {#configuring-schemas}

>[!CAUTION]
>
>Non modificare gli schemi incorporati dell&#39;applicazione, ma utilizzare il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento degli aggiornamenti futuri dell’applicazione. Questo può causare malfunzionamenti durante l’utilizzo di Adobe Campaign.

L’integrazione dell’applicazione è necessaria prima di utilizzare il modulo di reazione, al fine di definire le varie tabelle (transazioni, dettagli delle transazioni) da misurare e il loro rapporto con consegne, offerte e singoli individui.

### Schemi standard {#standard-schemas}

Il prodotto pronto all&#39;uso **[!UICONTROL nms:remaMatch]** schema contiene la tabella del registro di reazione, ovvero la relazione tra singoli utenti, ipotesi e tabella delle transazioni. Questo schema deve essere utilizzato come schema di ereditarietà per la tabella di destinazione finale dei registri di reazione.

La **[!UICONTROL nms:remaMatchRcp]** Lo schema viene inoltre fornito come standard e contiene l’archiviazione dei registri di reazione per i destinatari di Adobe Campaign ( **[!UICONTROL nms:recipient]** ). Per poter essere utilizzato, dovrà essere esteso per essere mappato a una tabella di transazione (contenente acquisti, ecc.).

### Tabelle di transazione e dettagli della transazione {#transaction-tables-and-transaction-details}

La tabella delle transazioni deve includere collegamenti diretti verso persone fisiche.

Puoi anche aggiungere una tabella contenente i dettagli della transazione. Questo non è direttamente collegato agli individui.

Se si accetta una ricevuta, ad esempio, una tabella di transazione è collegata a un contatto (tabella di ricezione) e una tabella di linee di ricezione è collegata solo alla tabella di ricezione (tabella di dettaglio). È quindi possibile configurare l&#39;ipotesi direttamente al livello a cui la tabella della linea di ricezione è collegata alla tabella di ricezione.

>[!NOTE]
>
>Se si desidera mantenere l&#39;identificatore di ricezione che descrive il comportamento previsto nelle ipotesi, è possibile estendere il modello di tabella nms:remaMatchRcp per aggiungere l&#39;identificatore (in questo caso, nessun calcolo del ROI è collegato a questi campi).

Si consiglia vivamente di aggiungere una data evento.

Al termine della configurazione, lo schema seguente mostra i join tra le diverse tabelle:

![](assets/response_data_model.png)

### Gestione della risposta e destinatari {#response-management-with-adobe-campaign-recipients}

In questo esempio, integreremo una tabella degli acquisti nel modulo di gestione delle risposte utilizzando la tabella dei destinatari integrata in Adobe Campaign **[!UICONTROL nms:recipient]**.

La tabella delle risposte registra su un **[!UICONTROL nms:remaMatchRcp]** il destinatario viene esteso per aggiungere un collegamento allo schema della tabella di acquisto. Nell’esempio seguente, la tabella di acquisto è denominata **demo:acquisto**.

1. Tramite Adobe Campaign Explorer, seleziona il **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Fai clic con il pulsante destro del mouse **Destinatario** quindi seleziona **[!UICONTROL Actions]** e **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. Puoi personalizzare la **[!UICONTROL Extension namespace]** nella finestra successiva, quindi fai clic su **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. In **[!UICONTROL Response management]** assicurati che la **[!UICONTROL Generate a storage schema for reactions]** casella selezionata.

   Quindi fai clic su **[!UICONTROL Define additional fields...]** per selezionare le tabelle di transazione correlate e aggiungere i campi desiderati all&#39;estensione dello schema nms:remaMatchRcp.

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

In questo esempio, integreremo una tabella di acquisto nel modulo di gestione delle risposte utilizzando una tabella di singoli utenti diversa dalla tabella dei destinatari disponibile in Adobe Campaign.

* Crea un nuovo schema del registro di risposta derivato da **[!UICONTROL nms:remaMatch]** schema.

   Poiché la tabella dei singoli utenti è diversa dalla tabella dei destinatari di Adobe Campaign, è necessario creare un nuovo schema dei registri di risposta basato sui **[!UICONTROL nms:remaMatch]** schema. Quindi completalo con i collegamenti verso i registri di consegna e la tabella di acquisto.

   Nell’esempio seguente, utilizzeremo il **demo:wideLogPers** schema e **demo:acquisto** tabella delle transazioni:

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

* Modifica la forma dell&#39;ipotesi nel **[!UICONTROL nms:remaHypothesis]** schema.

   Per impostazione predefinita, l’elenco dei registri di risposta è visibile nei registri dei destinatari. È quindi necessario modificare il modulo di ipotesi per visualizzare i nuovi registri di risposta creati durante il passaggio precedente.

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

## Gestire gli indicatori {#managing-indicators}

Il modulo Response Manager viene fornito con un elenco di indicatori predefiniti. Tuttavia, puoi aggiungere altri indicatori di misurazione personalizzati.

A questo scopo, è necessario estendere la tabella delle ipotesi inserendo due campi per ogni nuovo indicatore:

* il primo per la popolazione bersaglio,
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
