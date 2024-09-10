---
product: campaign
title: Caratteristiche di uno schema
description: Caratteristiche di uno schema
feature: Custom Resources
role: Data Engineer, Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 099161b4-b4cb-433c-aed6-71157269a536
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 1%

---

# Caratteristiche di uno schema{#schema-characteristics}



Le caratteristiche di uno schema che fa riferimento a una tabella esistente sono le seguenti:

* Adobe Campaign non deve modificare gli oggetti SQL relativi alle tabelle esistenti,
* I nomi di tabelle e colonne devono essere specificati in modo esplicito.
* Gli indici devono essere dichiarati.

>[!IMPORTANT]
>
>Non eliminare i campi nella tabella dei destinatari incorporata, anche se sono inutili. Questo può causare errori comportamentali nel database di Adobe Campaign.

## Attributo view {#the-view-attribute}

Gli schemi di Source accettano l&#39;attributo **view** per l&#39;elemento radice **srcSchema**. Deve essere utilizzato quando Adobe Campaign viene manipolato in tabelle personalizzate. L&#39;attributo **view=&quot;true&quot;** indica all&#39;assistente di aggiornamento della struttura del database di ignorare questo schema. L’applicazione non può quindi sincronizzare la tabella, le sue colonne e i suoi indici con lo schema corrispondente.

Quando questo attributo è impostato su **true**, lo schema viene utilizzato solo per generare query SQL per accedere ai dati di questa tabella.

## Nomi di tabelle e colonne {#names-of-tables-and-columns}

Quando le tabelle vengono create dall&#39;Assistente all&#39;aggiornamento delle tabelle, i nomi delle tabelle e delle colonne vengono generati automaticamente in base ai nomi dei rispettivi schemi e attributi. È tuttavia possibile forzare l&#39;utilizzo dei nomi SQL immettendo i seguenti attributi:

* **sqltable** nell&#39;elemento principale dello schema, per specificare la tabella,
* **sqlname** all&#39;interno di ogni attributo, per specificare le colonne.

**Esempio**:

```
<element label="Individual" name="individual" sqltable="individual">
    <key internal="true" name="id">
      <keyfield xpath="@id"/>
    </key> 
    <attribute name="id" type="long" length="32" />
    <attribute name="lastName" type="string" length="100" sqlname="Last_Name"/>
    <attribute name="firstName" type="string" length="100" sqlname="First_Name"/>
    <attribute name="email" type="string" length="100"/>
    <attribute name="mobile" type="string" length="100"/>
</element>
```

In questo esempio, se i nomi delle tabelle e delle colonne non fossero stati specificati in modo esplicito, l&#39;applicazione avrebbe utilizzato **CusIndividual** per la tabella, **lastName** e **firstName** per le colonne.

In uno schema, è possibile compilare solo una parte delle colonne di una tabella esistente. Le colonne non compilate non saranno accessibili all&#39;utente.

## Campi indicizzati {#indexed-fields}

Quando si ordinano i record di un elenco dalla console client, si ottengono prestazioni migliori ordinando i campi indicizzati. La dichiarazione di un indice in uno schema fa sì che la console visualizzi i campi indicizzati con una linea rossa sotto la freccia di ordinamento a sinistra dell’etichetta della colonna, come mostrato di seguito:

![](assets/s_ncs_integration_mapping_index.png)

In uno schema, un indice è definito come segue:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

Per questo motivo è importante dichiarare gli indici esistenti della tabella personalizzata nello schema corrispondente.

Un indice viene dichiarato in modo implicito per ogni chiave e dichiarazione di collegamento dello schema di origine. È possibile impedire la dichiarazione dell&#39;indice specificando l&#39;attributo **noDbIndex=&quot;true&quot;**:

**Esempio**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```
