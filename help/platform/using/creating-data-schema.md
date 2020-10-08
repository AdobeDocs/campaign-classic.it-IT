---
title: Accesso a un database esterno
seo-title: Accesso a un database esterno
description: Accesso a un database esterno
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '130'
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
   >Con  Snowflake, una chiave primaria è obbligatoria.

   ![](assets/wf_new_schema_generate_fda.png)

Gli indici vengono creati automaticamente durante la mappatura di una tabella (mappatura standard o FDA).
