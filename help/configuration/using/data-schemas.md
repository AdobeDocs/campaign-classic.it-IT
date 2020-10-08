---
title: Schemi di dati
seo-title: Schemi di dati
description: Schemi di dati
seo-description: null
page-status-flag: never-activated
uuid: 9f08750a-e125-4531-8c2c-1ab218190210
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b65e8d27-f427-464e-ad42-51c0a88eee86
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 2%

---


# Schemi di dati{#data-schemas}

## Principi {#principles}

Per modificare, creare e configurare gli schemi, fate clic sul **[!UICONTROL Administration > Configuration > Data schemas]** nodo della console client Adobe Campaign .

>[!NOTE]
>
>Gli schemi di dati forniti possono essere eliminati solo da un amministratore della console Adobe Campaign Classic.

![](assets/d_ncs_integration_schema_navtree.png)

Il campo di modifica mostra il contenuto XML dello schema di origine:

![](assets/d_ncs_integration_schema_edition.png)

>[!NOTE]
>
>Il controllo di modifica &quot;Name&quot; consente di inserire la chiave dello schema composta dal nome e dallo spazio dei nomi. Gli attributi &quot;name&quot; e &quot;namespace&quot; dell&#39;elemento principale dello schema vengono aggiornati automaticamente nella zona di modifica XML dello schema.

L&#39;anteprima genera automaticamente lo schema esteso:

![](assets/d_ncs_integration_schema_edition2.png)

>[!NOTE]
>
>Quando lo schema di origine viene salvato, la generazione dello schema esteso viene avviata automaticamente.

Per verificare la struttura completa di uno schema, è possibile utilizzare la scheda Anteprima. Se lo schema è stato esteso, sarà possibile visualizzare tutte le sue estensioni. Come complemento, nella scheda Documentazione sono visualizzati tutti gli attributi e gli elementi dello schema e le relative proprietà (Campo SQL, tipo/lunghezza, etichetta, descrizione). La scheda Documentazione si applica solo agli schemi generati. For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.

## Esempio: creazione di una tabella di contratto {#example--creating-a-contract-table}

Nell&#39;esempio seguente, si desidera creare una nuova tabella per **i contratti** nel modello di database del database Adobe Campaign . Questa tabella consente di memorizzare i nomi e i cognomi e gli indirizzi e-mail di titolari e co-possessori, per ogni contratto.

A tal fine, è necessario creare lo schema della tabella e aggiornare la struttura del database per generare la tabella corrispondente. Applicate le seguenti fasi:

1. Modificate il **[!UICONTROL Administration > Configuration > Data schemas]** nodo della struttura di Adobe Campaign  e fate clic su **[!UICONTROL New]** .
1. Scegliete l’ **[!UICONTROL Create a new table in the data model]** opzione e fate clic su **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_create_new_schema.png)

1. Specificare un nome per la tabella e uno spazio dei nomi.

   ![](assets/s_ncs_configuration_create_new_param.png)

   >[!NOTE]
   >
   >Per impostazione predefinita, gli schemi creati dagli utenti sono memorizzati nello spazio dei nomi &#39;cus&#39;. Per ulteriori informazioni, vedere [Identificazione di uno schema](../../configuration/using/about-schema-reference.md#identification-of-a-schema).

1. Creare il contenuto della tabella. È consigliabile utilizzare la procedura guidata di immissione per verificare che non manchino le impostazioni. A questo scopo, fate clic sul **[!UICONTROL Insert]** pulsante e scegliete il tipo di impostazione da aggiungere.

   ![](assets/s_ncs_configuration_create_new_content.png)

1. Definire le impostazioni per la tabella del contratto:

   ```
   <srcSchema desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract" mappingType="sql" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <element desc="Active contracts" img="ncm:channels.png" label="Contracts" labelSingular="Contract"
              name="Contracts" autopk="true">
              <attribute name="holderName" label="Holder last name" type="string"/>
              <attribute name="holderFirstName" label="Holder first name" type="string"/>
              <attribute name="holderEmail" label="Holder email" type="string"/>
              <attribute name="co-holderName" label="Co-holder last name" type="string"/>           
              <attribute name="co-holderFirstName" label="Co-holder first name" type="string"/>           
              <attribute name="co-holderEmail" label="Co-holder email" type="string"/>    
              <attribute name="date" label="Subscription date" type="date"/>     
              <attribute name="noContract" label="Contract number" type="long"/>  
     </element>
   </srcSchema>
   ```

   Aggiungere il tipo di contratto e inserire un indice sul numero del contratto.

   ```
   <srcSchema _cs="Contracts (cus)" desc="Active contracts" entitySchema="xtk:srcSchema" img="ncm:channels.png"
              label="Contracts" labelSingular="Contract" name="Contracts" namespace="cus" xtkschema="xtk:srcSchema">
     <enumeration basetype="byte" name="typeContract">
       <value label="Home" name="home" value="0"/>
       <value label="Car" name="car" value="1"/>
       <value label="Health" name="health" value="2"/>
       <value label="Pension fund" name="pension fund" value="2"/>
     </enumeration>
     <element autopk="true" desc="Active contracts" img="ncm:channels.png" label="Contracts"
              labelSingular="Contract" name="Contracts">
       <attribute label="Holder last name" name="holderName" type="string"/>
       <attribute label="Holder first name" name="holderFirstName" type="string"/>
       <attribute label="Holder email" name="holderEmail" type="string"/>
       <attribute label="Co-holder last name" name="co-holderName" type="string"/>
       <attribute label="Co-holder first name" name="co-holderFirstName" type="string"/>
       <attribute label="Co-holder email" name="co-holderEmail" type="string"/>
       <attribute label="Subscription date" name="date" type="date"/>
      <attribute desc="Type of contract" enum="cus:Contracts:typeContract" label="Type of contract"
                  name="type" type="byte"/>
       <attribute label="Contract number" name="noContract" type="long"/>
       <dbindex name="noContract" unique="true">
         <keyfield xpath="@noContract"/>
       </dbindex>
     </element>
   </srcSchema>
   ```

1. Salvate lo schema per generare la struttura:

   ![](assets/s_ncs_configuration_structure.png)

1. Aggiornare la struttura del database per creare la tabella a cui verrà collegato lo schema. For more on this, refer to [Updating the database structure](../../configuration/using/updating-the-database-structure.md).

