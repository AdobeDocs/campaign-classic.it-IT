---
product: campaign
title: Indirizzi di seed
description: Indirizzi di seed
role: Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Seed Address
level: Intermediate, Experienced
exl-id: a16103bf-0498-4f59-ad96-8bfdeea26577
TQID: https://experienceleague.adobe.com/xEP-TmMNJ0On70jE2PdjywSXeXw5oF0LVeCDiA7nKB8
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 329
ht-degree: 6%

---

# Indirizzi di seed{#seed-addresses}



Se la tabella dei destinatari è personalizzata, sono necessarie configurazioni aggiuntive. Lo schema **[!UICONTROL nms:seedMember]** deve essere esteso. Viene aggiunta una scheda aggiuntiva agli indirizzi di seed per definire i campi appropriati, come illustrato di seguito:

![](assets/s_ncs_user_seedlist_new_tab.png)

Per ulteriori informazioni sull&#39;utilizzo degli indirizzi di seed, fare riferimento a [questa sezione](../../delivery/using/about-seed-addresses.md).

## Implementazione {#implementation}

Lo schema **nms:seedMember** e il modulo collegato fornito con il prodotto devono essere estesi per la configurazione del cliente in modo che faccia riferimento a tutti i campi necessari. La definizione dello schema contiene commenti che ne descrivono la modalità di configurazione.

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

1. Crea un&#39;estensione dello schema **nms:seedMember**. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../configuration/using/extending-a-schema.md).
1. In questa nuova estensione, aggiungere un nuovo elemento nella radice di **[!UICONTROL seedMember]** con i seguenti parametri:

   ```
   name="custom_customNamespace_customSchema"
   ```

   Questo elemento deve contenere i campi necessari per esportare le campagne. Questi campi devono avere lo stesso nome dei campi corrispondenti nello schema esterno. Ad esempio, se lo schema è **[!UICONTROL cus:person]** , lo schema **[!UICONTROL nms:seedMember]** deve essere esteso come segue:

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
   >L&#39;estensione dello schema **nms:seedMember** deve essere conforme alle strutture di una campagna e di una consegna in Adobe Campaign.

   >[!IMPORTANT]
   >
   >
   >    
   >    
   >    * Durante l&#39;estensione, è necessario specificare un **nome SQL (@sqlname)** per il campo &#39;email&#39;. Il nome SQL deve essere diverso da &#39;sEmail&#39; riservato allo schema del destinatario.
   >    * È necessario aggiornare la struttura del database con lo schema creato durante l&#39;estensione di **nms:seedMember**.
   >    * Nell&#39;estensione **nms:seedMember**, il campo contenente l&#39;indirizzo e-mail deve avere **name=&quot;email&quot;** come attributo. Il nome SQL deve essere diverso da &#39;sEmail&#39; che è già in uso per lo schema del destinatario. Questo attributo deve essere dichiarato immediatamente nell&#39;elemento **`<element name="custom_cus_person" />`**.
   >    
   >

1. Modificare di conseguenza il modulo **[!UICONTROL seedMember]** per definire una nuova scheda &quot;Destinatario interno&quot; nella finestra **[!UICONTROL Seed addresses]**. Per ulteriori informazioni, consulta [questa pagina](../../configuration/using/form-structure.md).

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
