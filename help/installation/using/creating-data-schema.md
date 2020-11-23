---
solution: Campaign Classic
product: campaign
title: Accesso a un database esterno
description: Accesso a un database esterno
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 3%

---


# Creazione dello schema dati {#creating-the-data-schema}

Per creare uno schema su un database esterno:

1. Fare clic sul **[!UICONTROL New]** pulsante sopra l&#39;elenco degli schemi di dati e scegliere **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Immettete un nome e una descrizione per lo schema e selezionate l&#39;account esterno che consentirà la connessione al database. Questo consente di accedere all&#39;elenco delle tabelle disponibili nella base esterna. Scegliere la tabella che contiene i dati da raccogliere.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Fate clic **[!UICONTROL OK]** per confermare.  Adobe Campaign rileva automaticamente la struttura della tabella selezionata e genera lo schema logico.  Adobe Campaign non genera collegamenti.

1. Fate clic **[!UICONTROL Save]** per confermare la creazione.

   >[!CAUTION]
   >
   >Ad Snowflake, una chiave primaria è obbligatoria.

   ![](assets/wf_new_schema_generate_fda.png)

Gli indici vengono creati automaticamente durante la mappatura di una tabella (mappatura standard o FDA).
