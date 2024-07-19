---
product: campaign
title: Schema di una tabella esistente
description: Schema di una tabella esistente
feature: Custom Resources
role: Data Engineer, Developer
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 7%

---

# Schema di una tabella esistente{#schema-of-an-existing-table}

## Panoramica {#overview}

Quando l’applicazione deve accedere ai dati di una tabella esistente, di una vista SQL o di dati provenienti da un database remoto, crea lo schema in Adobe Campaign con i dati seguenti:

* Nome della tabella: immettere il nome della tabella (con il relativo alias quando si utilizza un collegamento dblink) con l&#39;attributo &quot;sqltable&quot;.
* chiave dello schema: fare riferimento ai campi di riconciliazione,
* indici: utilizzati per generare query,
* I campi e la loro posizione nella struttura XML: compilare solo i campi utilizzati nell’applicazione,
* collegamenti: se sono presenti join con le altre tabelle della base.

## Implementazione {#implementation}

Per creare lo schema corrispondente, attieniti alle seguenti fasi:

1. Modificare il nodo **[!UICONTROL Administration>Configuration>Data schemas]** della struttura Adobe Campaign e fare clic su **[!UICONTROL New]**.
1. Selezionare l&#39;opzione **[!UICONTROL Access data from an existing table or an SQL view]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Scegliere la tabella o la vista esistente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adatta il contenuto dello schema in base alle tue esigenze.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Per non generare uno script SQL per la creazione di tabelle, è necessario compilare lo schema con l&#39;attributo view=&quot;true&quot; sull&#39;elemento principale `<srcSchema>`.

**Esempio**:

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

L&#39;opzione **Federated Data Access - FDA** consente di accedere ai dati archiviati in un database esterno.

La configurazione da eseguire sugli schemi per accedere ai dati in un database esterno è descritta in [questa pagina](../../installation/using/creating-data-schema.md).
