---
title: Indirizzi di seed
seo-title: Indirizzi di seed
description: Indirizzi di seed
seo-description: null
page-status-flag: never-activated
uuid: 0ebdeb73-be67-4c34-9f59-9fd4fb5241ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 41338d32-b95c-45ae-bee6-17b2af5bd837
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '325'
ht-degree: 2%

---


# Indirizzi di seed{#seed-addresses}

Se la tabella del destinatario è una tabella personalizzata, sono necessarie configurazioni aggiuntive. Lo **[!UICONTROL nms:seedMember]** schema deve essere esteso. Agli indirizzi iniziali viene aggiunta una scheda aggiuntiva per la definizione dei campi adeguati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

Per ulteriori informazioni sull&#39;uso degli indirizzi di base, consultare [questa sezione](../../delivery/using/about-seed-addresses.md).

## Implementazione {#implementation}

Lo schema **nms:seedMember** e il modulo collegato che esce fuori dalla casella devono essere estesi per la configurazione del cliente, per fare riferimento a tutti i campi necessari. La definizione dello schema contiene commenti che ne descrivono la modalità di configurazione.

Definizione dello schema esteso della tabella destinatari:

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

Effettuate le seguenti operazioni:

1. Create un&#39;estensione dello schema **nms:seedMember** . Per ulteriori informazioni, vedere [Estensione di uno schema](../../configuration/using/extending-a-schema.md).
1. In questa nuova estensione, aggiungete un nuovo elemento alla radice di **[!UICONTROL seedMember]** con i seguenti parametri:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Questo elemento deve contenere i campi necessari per esportare le campagne. Questi campi devono avere lo stesso nome dei campi corrispondenti nello schema esterno. Ad esempio, se lo schema è **[!UICONTROL cus:person]** , lo **[!UICONTROL nms:seedMember]** schema deve essere esteso come segue:

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
   >L&#39;estensione dello schema **nms:seedMember** deve essere conforme alle strutture di una campagna e di una distribuzione in  Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Durante l&#39;estensione, è necessario specificare un nome **SQL (@sqlname)** per il campo &#39;email&#39;. Il nome SQL deve essere diverso da &#39;sEmail&#39; riservato allo schema del destinatario.
   >    * È necessario aggiornare la struttura del database con lo schema creato durante l&#39;estensione **nms:seedMember**.
   >    * Nell’estensione **nms:seedMember** , il campo contenente l’indirizzo e-mail deve avere come attributo **name=&quot;email&quot;** . Il nome SQL deve essere diverso da &#39;sEmail&#39; già utilizzato per lo schema del destinatario. Questo attributo deve essere dichiarato immediatamente sotto l&#39; **`<element name="custom_cus_person" />`** elemento .


1. Modificare di conseguenza il **[!UICONTROL seedMember]** modulo per definire una nuova scheda &quot;Destinatario interno&quot; nella **[!UICONTROL Seed addresses]** finestra. For more on this, refer to [Form structure](../../configuration/using/form-structure.md).

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

Se tutti gli attributi dell&#39;indirizzo seed non vengono inseriti,  Adobe Campaign sostituisce automaticamente i profili: verranno inseriti automaticamente durante la personalizzazione utilizzando i dati di un profilo esistente.
