---
title: Caratteristiche di uno schema
seo-title: Caratteristiche di uno schema
description: Caratteristiche di uno schema
seo-description: null
page-status-flag: never-activated
uuid: ca8eb7af-ef22-403a-8f04-ece5dc903174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: 441e80e1-0559-41fd-83e8-afdf94279e75
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 2%

---


# Caratteristiche di uno schema{#schema-characteristics}

Le caratteristiche di uno schema che fa riferimento a una tabella esistente sono le seguenti:

*  Adobe Campaign non deve modificare gli oggetti SQL relativi alle tabelle esistenti,
* È necessario specificare esplicitamente i nomi delle tabelle e delle colonne,
* Gli indici devono essere dichiarati.

>[!IMPORTANT]
>
>Non eliminare i campi nella tabella dei destinatari standard, anche se inutili. Ciò potrebbe causare errori comportamentali nel database Adobe Campaign .

## L&#39;attributo view {#the-view-attribute}

Gli schemi di origine accettano l&#39;attributo **view** per l&#39;elemento radice **srcSchema** . Deve essere utilizzato quando  Adobe Campaign viene manipolato in tabelle personalizzate. L&#39;attributo **view=&quot;true&quot;** indica alla procedura guidata di aggiornamento della struttura del database di ignorare questo schema. Pertanto, all&#39;applicazione non è consentito sincronizzare la tabella, le relative colonne e i relativi indici con lo schema corrispondente.

Quando questo attributo è impostato su **true**, lo schema viene utilizzato solo per generare query SQL per accedere ai dati di questa tabella.

## Nomi di tabelle e colonne {#names-of-tables-and-columns}

Quando le tabelle vengono create dalla procedura guidata di aggiornamento delle tabelle, i nomi delle tabelle e delle colonne vengono generati automaticamente in base ai nomi dei rispettivi schemi e attributi. È tuttavia possibile imporre l&#39;uso dei nomi SQL immettendo i seguenti attributi:

* **sqltable** all&#39;interno dell&#39;elemento principale dello schema, per specificare la tabella,
* **sqlname** all&#39;interno di ciascun attributo, per specificare le colonne.

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

In questo esempio, se i nomi delle tabelle e delle colonne non fossero stati specificati in modo esplicito, l&#39;applicazione avrebbe utilizzato **CusIndividuale** per la tabella, **lastName** e **firstName** per le colonne.

In uno schema, è possibile compilare solo una parte delle colonne di una tabella esistente. Le colonne non popolate non saranno accessibili agli utenti.

## Campi indicizzati {#indexed-fields}

Quando si ordinano i record di un elenco dalla console client, si ottengono prestazioni migliori ordinando i campi indicizzati. La dichiarazione di un indice in uno schema consente alla console di visualizzare i campi indicizzati con una linea rossa sotto la freccia dell&#39;ordinamento a sinistra dell&#39;etichetta della colonna, come illustrato di seguito:

![](assets/s_ncs_integration_mapping_index.png)

In uno schema, un indice è definito come segue:

```
<dbindex name="name_of_index" unique="true/false"
  <keyfield xpath="xpath_1st_field"/
  <keyfield xpath="xpath_2nd_field"/
  ...
</dbindex
```

Per questo è importante dichiarare gli indici esistenti della tabella personalizzata nello schema corrispondente.

Un indice è implicitamente dichiarato per ogni dichiarazione di chiave e collegamento dello schema di origine. La dichiarazione dell&#39;indice può essere impedita specificando l&#39;attributo **noDbIndex=&quot;true&quot;** :

**Esempio**:

```
<key internal="true" name="customer" noDbIndex="true">
  <keyfield xpath="@customerId"/>
</key>
```

