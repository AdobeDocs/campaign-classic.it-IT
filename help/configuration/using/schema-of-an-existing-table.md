---
title: Schema di una tabella esistente
seo-title: Schema di una tabella esistente
description: Schema di una tabella esistente
seo-description: null
page-status-flag: never-activated
uuid: cb766259-8ed7-40a1-8df7-75a8a3f9986d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6877d94d-d6e5-4080-a537-ef1bb6e6f8cf
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---


# Schema di una tabella esistente{#schema-of-an-existing-table}

## Panoramica {#overview}

Quando l&#39;applicazione deve accedere ai dati di una tabella esistente, di una vista SQL o di dati da un database remoto, crearne lo schema in  Adobe Campaign con i dati seguenti:

* Nome della tabella: immettere il nome della tabella (con il relativo alias quando viene utilizzato un collegamento) con l&#39;attributo &quot;sqltable&quot;,
* chiave di schema: fare riferimento ai campi di riconciliazione,
* indici: utilizzato per generare query,
* I campi e la relativa posizione nella struttura XML: compilare solo i campi utilizzati nell’applicazione,
* collegamenti: se esistono join con le altre tabelle della base.

## Implementazione {#implementation}

Per creare lo schema corrispondente, procedere come segue:

1. Modificate il **[!UICONTROL Administration>Configuration>Data schemas]** nodo della struttura di Adobe Campaign  e fate clic su **[!UICONTROL New]** .
1. Select the **[!UICONTROL Access data from an existing table or an SQL view]** option and click **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Scegliere la tabella o la visualizzazione esistente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adattare il contenuto dello schema in base alle esigenze.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Lo schema deve essere compilato con l&#39;attributo view=&quot;true&quot; sull&#39;elemento `<srcSchema>` principale per non generare uno script SQL per la creazione di tabelle.

**Esempio** :

```
<srcSchema name="recipient" namespace="cus" view="true">
  <element name="recipient" sqltable="dbsrv.recipient">
    <key name="email">
      <keyfield xpath="@email"/>
    </key>   
    <attribute name="email" type="string" length="80" sqlname="email"/>
  </element>
</srcSchema>
```

## Accesso a un database esterno {#accessing-an-external-database}

L&#39;opzione **Federated Data Access - FDA** consente di accedere ai dati memorizzati in un database esterno.

La configurazione da eseguire sugli schemi per accedere ai dati in un database esterno è descritta in [questa pagina](../../platform/using/creating-data-schema.md).
