---
product: campaign
title: Creazione dello schema dati per FDA
description: Scopri come creare lo schema dati per FDA
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 2%

---

# Creazione dello schema dati {#creating-the-data-schema}

![](../../assets/v7-only.svg)

Per creare uno schema su un database esterno:

1. Fai clic sul pulsante **[!UICONTROL New]** pulsante sopra l’elenco degli schemi di dati e scegli **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Inserisci un **[!UICONTROL Namespace]** e  **[!UICONTROL Name]** per lo schema e seleziona il **[!UICONTROL External account]** che consente la connessione al database. Ciò consente l’accesso all’elenco delle tabelle disponibili nella base esterna.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Da **[!UICONTROL Table name]** scegliere la tabella contenente i dati da raccogliere.

   Con il Snowflake, è possibile selezionare qui le visualizzazioni se all&#39;utente del database sono stati concessi i privilegi corretti. Tieni presente che quando utilizzi le visualizzazioni, Adobe Campaign non sarà in grado di generare automaticamente lo schema XML, dovrai crearlo tu stesso. Per ulteriori informazioni sulle visualizzazioni, consulta [Documentazione del Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Fai clic su **[!UICONTROL OK]** per confermare. Adobe Campaign rileva automaticamente la struttura della tabella selezionata e genera lo schema logico. Tieni presente che Adobe Campaign non genera collegamenti.

1. Fai clic su **[!UICONTROL Save]** per confermare la creazione.

   >[!CAUTION]
   >
   >Con il Snowflake, una chiave primaria è obbligatoria.

   ![](assets/wf_new_schema_generate_fda.png)

Gli indici vengono creati automaticamente durante la mappatura di una tabella (mappatura standard o FDA).
