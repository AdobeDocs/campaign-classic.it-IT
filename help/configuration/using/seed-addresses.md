---
product: campaign
title: Indirizzi di seed
description: Indirizzi di seed
role: Data Engineer, Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 6%

---

# Indirizzi di seed{#seed-addresses}



Se la tabella dei destinatari è personalizzata, sono necessarie configurazioni aggiuntive. Il **[!UICONTROL nms:seedMember]** deve essere esteso. Viene aggiunta una scheda aggiuntiva agli indirizzi di seed per definire i campi appropriati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

Per ulteriori informazioni sull’utilizzo degli indirizzi di seed, consulta [questa sezione](../../delivery/using/about-seed-addresses.md).

## Implementazione {#implementation}

Il **nms:seedingMember** Lo schema e il modulo collegato fornito con il prodotto devono essere estesi per la configurazione del cliente in modo che faccia riferimento a tutti i campi necessari. La definizione dello schema contiene commenti che ne descrivono la modalità di configurazione.

Definizione dello schema esteso della tabella dei destinatari:

```
<srcSchema label="Person" name="person" namespace="cus">
  <element autopk="true" label="Person" name="person">
      <attribute label="LastName" name="lastname" type="string"/>
      <attribute label="FirstName" name="firstname" type="string"/>
    <element label="Address" name="address">
      <attribute label="Email" name="addrEnv" type="string"/>
    </element>
    <attribute label="Code Offer" name="codeOffer" type="string"/>
  </element>
</srcSchema>
```

Applica i seguenti passaggi:

1. Crea un&#39;estensione del **nms:seedingMember** schema. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../configuration/using/extending-a-schema.md).
1. In questa nuova estensione, aggiungi un nuovo elemento nella directory principale di **[!UICONTROL seedMember]** con i seguenti parametri:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Questo elemento deve contenere i campi necessari per esportare le campagne. Questi campi devono avere lo stesso nome dei campi corrispondenti nello schema esterno. Ad esempio, se lo schema è **[!UICONTROL cus:person]** , il **[!UICONTROL nms:seedMember]** lo schema deve essere esteso come segue:

   ```
     <srcSchema extendedSchema="nms:seedMember" label="Seed addresses" labelSingular="Seed address" name="seedMember" namespace="cus">
     <element name="common">
       <element name="custom_cus_person">
         <attribute name="lastname" template="cus:person:person/@lastname"/>
         <attribute name="firstname" template="cus:person:person/@firstname"/>
         <attribute name="email" sqlname="myEmailField" template="cus:person:person/address/@addrEnv" xml="false"/>
       </element>
     </element>
     <element name="seedMember">
      <element aggregate="cus:seedMember:common"/>
     </element>
   </srcSchema>
   ```

   >[!NOTE]
   >
   >L&#39;estensione del **nms:seedingMember** lo schema deve essere conforme alle strutture di una campagna e di una consegna in Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Durante l’estensione, devi specificare un’ **Nome SQL (@sqlname)** per il campo &quot;email&quot;. Il nome SQL deve essere diverso da &#39;sEmail&#39; riservato allo schema del destinatario.
   >    * È necessario aggiornare la struttura del database con lo schema creato durante l’estensione **nms:seedingMember**.
   >    * In **nms:seedingMember** , il campo contenente l&#39;indirizzo e-mail deve avere **name=&quot;email&quot;** come attributo. Il nome SQL deve essere diverso da &#39;sEmail&#39; che è già in uso per lo schema del destinatario. Questo attributo deve essere dichiarato immediatamente in **`<element name="custom_cus_person" />`** elemento.
   >    
   >

1. Modifica il **[!UICONTROL seedMember]** per definire una nuova scheda &quot;Destinatario interno&quot; nel **[!UICONTROL Seed addresses]** finestra. Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/form-structure.md).

   ```
   <container colcount="2" label="Internal recipient" name="internal"
                xpath="custom_cus_person">
       <input colspan="2" editable="true" nolabel="true" type="treeEdit">
         <container label="Recipient (cus:person)">
           <input xpath="@last name"/>
           <input xpath="@first name"/>
           <input xpath="@email"/>
         </container>
       </input>
     </container>
   ```

Se non vengono immessi tutti gli attributi dell’indirizzo di seed, Adobe Campaign sostituisce automaticamente i profili: verranno immessi automaticamente durante la personalizzazione utilizzando i dati di un profilo esistente.
