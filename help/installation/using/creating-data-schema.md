---
product: campaign
title: Accesso a un database esterno
description: Accesso a un database esterno
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---

# Creazione dello schema dati {#creating-the-data-schema}

Per creare uno schema su un database esterno:

1. Fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco degli schemi di dati e scegli **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Immetti un nome e una descrizione per lo schema e seleziona l’account esterno che abiliterà la connessione al database. Ciò consente l’accesso all’elenco delle tabelle disponibili nella base esterna. Scegliere la tabella contenente i dati da raccogliere.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Fai clic su **[!UICONTROL OK]** per confermare. Adobe Campaign rileva automaticamente la struttura della tabella selezionata e genera lo schema logico. Tieni presente che Adobe Campaign non genera collegamenti.

1. Fai clic su **[!UICONTROL Save]** per confermare la creazione.

   >[!CAUTION]
   >
   >Con il Snowflake, una chiave primaria è obbligatoria.

   ![](assets/wf_new_schema_generate_fda.png)

Gli indici vengono creati automaticamente durante la mappatura di una tabella (mappatura standard o FDA).
