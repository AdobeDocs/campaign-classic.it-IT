---
title: Configurazione
seo-title: Configurazione
description: Configurazione
seo-description: null
page-status-flag: never-activated
uuid: 59503b54-ad49-4b00-8ffb-52e6f6c62070
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: ed4afa5e-c184-4c8e-a086-41d87b863190
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 1%

---


# Configurazione{#configuration}

Questa sezione è destinata alle persone responsabili della configurazione della gestione della risposta. Presuppone una certa quantità di conoscenze sull&#39;estensione degli schemi, sulla definizione dei flussi di lavoro e sulla programmazione SQL.

Questo consente di apprendere come adattare il modello dati standard alla natura specifica di una tabella di transazione esterna a  Adobe Campaign con il tabella dei singoli. Questa tabella di utenti può coincidere con la tabella di singoli utenti disponibili in  Adobe Campaign o con una tabella diversa

L&#39;ipotesi di misura viene avviata dal flusso di lavoro del processo di operazione ( **[!UICONTROL operationMgt]** ). Ogni ipotesi rappresenta un processo separato eseguito in modo asincrono con uno stato di esecuzione (In corso di modifica, In attesa, Completato, Non riuscito, ecc.) e controllata da un pianificatore che gestisce i vincoli di priorità, la limitazione del numero di processi simultanei, la pagina a bassa attività e l&#39;esecuzione automatica con frequenza.

## Configurazione degli schemi {#configuring-schemas}

>[!CAUTION]
>
>Non modificate gli schemi standard dell&#39;applicazione, ma utilizzate il meccanismo di estensione dello schema. In caso contrario, gli schemi modificati non verranno aggiornati al momento degli aggiornamenti futuri dell&#39;applicazione. Ciò può causare malfunzionamenti durante l&#39;utilizzo  Adobe Campaign.

L&#39;integrazione dell&#39;applicazione è necessaria prima di utilizzare il modulo di reazione, al fine di definire le varie tabelle (transazioni, dettagli della transazione) da misurare, nonché la loro relazione con consegne, offerte e individui.

### Schemi standard {#standard-schemas}

Lo schema out-of-the-box **[!UICONTROL nms:remaMatch]** contiene la tabella del registro delle reazioni, ovvero la relazione tra singoli individui, ipotesi e tabella delle transazioni. Questo schema deve essere utilizzato come schema di ereditarietà per la tabella di destinazione finale dei registri di reazione.

Lo **[!UICONTROL nms:remaMatchRcp]** schema viene inoltre fornito come standard, contiene l&#39;archiviazione dei registri di reazione per  destinatari Adobe Campaign ( **[!UICONTROL nms:recipient]** ). Per essere utilizzato, dovrà essere esteso per essere mappato a una tabella delle transazioni (contenente acquisti, ecc.).

### Tabelle di transazione e dettagli transazione {#transaction-tables-and-transaction-details}

La tabella delle transazioni deve includere collegamenti diretti verso individui.

È inoltre possibile aggiungere una tabella contenente i dettagli della transazione. Questo non è collegato direttamente ai singoli.

Se si accetta una ricevuta, ad esempio, una tabella di transazione è collegata a un contatto (tabella di incasso) e una tabella di linee di incasso è collegata solo alla tabella di incasso (tabella di dettaglio). È quindi possibile configurare l&#39;ipotesi direttamente al livello al quale la tabella della linea di ricezione è collegata alla tabella di ricezione.

>[!NOTE]
>
>Se si desidera mantenere l&#39;identificatore di ricevuta che descrive il comportamento previsto nelle ipotesi, è possibile estendere il modello di tabella nms:remaMatchRcp per aggiungervi l&#39;identificatore (in questo caso, nessun calcolo ROI è collegato a questi campi).

È vivamente consigliato aggiungere una data per l’evento.

Lo schema seguente mostra i join tra le diverse tabelle una volta completata la configurazione:

![](assets/response_data_model.png)

### Gestione delle risposte con  destinatari Adobe Campaign {#response-management-with-adobe-campaign-recipients}

In questo esempio, integreremo una tabella degli acquisti nel modulo di gestione delle risposte utilizzando la  tabella dei destinatari Adobe Campaign ( **[!UICONTROL nms:recipient]** ).

La tabella dei registri di risposta di un **[!UICONTROL nms:remaMatchRcp]** destinatario viene estesa per aggiungere un collegamento allo schema della tabella di acquisto. Nell&#39;esempio seguente, la tabella di acquisto è denominata **demo:purchase**.

1. Mediante  Adobe Campaign Explorer, selezionate il **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Target mappings]**.
1. Fai clic con il pulsante destro del mouse su **Destinatario** , quindi seleziona **[!UICONTROL Actions]** e **[!UICONTROL Modify the options of the targeting dimensions]**.

   ![](assets/delivery_mapping1.png)

1. Puoi personalizzare la finestra **[!UICONTROL Extension namespace]** nella finestra successiva, quindi fare clic su **[!UICONTROL Next]**.

   ![](assets/delivery_mapping2.png)

1. Nella **[!UICONTROL Response management]** categoria, assicurarsi che la **[!UICONTROL Generate a storage schema for reactions]** casella sia selezionata.

   Fare clic **[!UICONTROL Define additional fields...]** per selezionare le tabelle di transazione correlate e aggiungere i campi desiderati all&#39;estensione dello schema nms:remaMatchRcp.

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

In questo esempio, integreremo una tabella di acquisto nel modulo di gestione delle risposte utilizzando una tabella di utenti diversi dalla tabella di destinatari disponibile in  Adobe Campaign.

* Creazione di un nuovo schema del registro risposte derivato dallo **[!UICONTROL nms:remaMatch]** schema.

   Poiché la tabella dei singoli è diversa dalla tabella  destinatari Adobe Campaign, è necessario creare un nuovo schema dei registri di risposta basato sullo **[!UICONTROL nms:remaMatch]** schema. Quindi completarlo con i link verso i registri di consegna e la tabella di acquisto.

   Nell&#39;esempio seguente verranno utilizzati lo schema **demo:wideLogPers** e la tabella delle transazioni **demo:purchase** :

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

* Modifica del modulo di ipotesi nello **[!UICONTROL nms:remaHypothesis]** schema.

   Per impostazione predefinita, l’elenco dei registri di risposta è visibile nei registri dei destinatari. È pertanto necessario modificare il modulo di ipotesi per visualizzare i nuovi registri di risposta creati durante il passaggio precedente.

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

## Gestione degli indicatori {#managing-indicators}

Il modulo Response Manager include un elenco di indicatori predefiniti. Tuttavia, potete aggiungere altri indicatori di misura personalizzati.

A questo scopo, è necessario estendere la tabella di ipotesi inserendo due campi per ogni nuovo indicatore:

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

