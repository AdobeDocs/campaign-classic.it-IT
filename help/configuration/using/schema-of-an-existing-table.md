---
product: campaign
title: Schema di una tabella esistente
description: Schema di una tabella esistente
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 964f1027-627c-4f12-91b5-f258e9ba458b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 10%

---

# Schema di una tabella esistente{#schema-of-an-existing-table}

## Panoramica {#overview}

Quando l&#39;applicazione deve accedere ai dati di una tabella esistente, di una vista SQL o ai dati di un database remoto, creare lo schema in Adobe Campaign con i seguenti dati:

* Nome della tabella: inserire il nome della tabella (con il relativo alias quando viene utilizzato un collegamento) con l’attributo &quot;sqltable&quot;,
* chiave di schema: fare riferimento ai campi di riconciliazione,
* indici: utilizzato per generare query,
* I campi e la relativa posizione nella struttura XML: compilare solo i campi utilizzati nell’applicazione,
* collegamenti: se ci sono giunti con le altre tabelle della base.

## Implementazione {#implementation}

Per creare lo schema corrispondente, applicare le seguenti fasi:

1. Modifica le **[!UICONTROL Administration>Configuration>Data schemas]** nodo della struttura di Adobe Campaign e fai clic su **[!UICONTROL New]** .
1. Seleziona la **[!UICONTROL Access data from an existing table or an SQL view]** e fai clic su **[!UICONTROL Next]** .

   ![](assets/s_ncs_configuration_extand_a_schema.png)

1. Scegliere la tabella o la vista esistente:

   ![](assets/s_ncs_configuration_select_table.png)

1. Adatta il contenuto dello schema in base alle tue esigenze.

   ![](assets/s_ncs_configuration_view_create_schema.png)

   Lo schema deve essere compilato con l&#39;attributo view=&quot;true&quot; nel `<srcSchema>` elemento principale per non generare uno script SQL per la creazione di tabelle.

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

La **Federated Data Access - FDA** consente di accedere ai dati archiviati in un database esterno.

La configurazione da eseguire sugli schemi per accedere ai dati in un database esterno è descritta in [questa pagina](../../installation/using/creating-data-schema.md).
