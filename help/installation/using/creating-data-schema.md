---
product: campaign
title: Creazione dello schema dati per FDA
description: Scopri come creare lo schema dati per FDA
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---

# Creazione dello schema dati {#creating-the-data-schema}



Per creare uno schema su un database esterno:

1. Fare clic sul pulsante **[!UICONTROL New]** sopra l&#39;elenco degli schemi di dati e scegliere **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. Immettere **[!UICONTROL Namespace]** e **[!UICONTROL Name]** per lo schema e selezionare **[!UICONTROL External account]** che consentirà la connessione al database. Ciò consente di accedere all’elenco di tabelle disponibili nella base esterna.

   ![](assets/wf_new_schema_select_table_fda.png)

1. Dal campo **[!UICONTROL Table name]**, scegliere la tabella contenente i dati da raccogliere.

   Con Snowflake, è possibile selezionare qui le viste se all&#39;utente del database sono stati concessi i privilegi corretti. Tieni presente che quando utilizzi le viste, Adobe Campaign non sarà in grado di generare automaticamente lo schema XML, dovrai crearlo tu stesso. Per ulteriori informazioni sulle visualizzazioni, consulta la [documentazione del Snowflake](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. Fai clic su **[!UICONTROL OK]** per confermare. Adobe Campaign rileva automaticamente la struttura della tabella selezionata e genera lo schema logico. Tieni presente che Adobe Campaign non genera collegamenti.

1. Fare clic su **[!UICONTROL Save]** per confermare la creazione.

   >[!CAUTION]
   >
   >Con il Snowflake, una chiave primaria è obbligatoria.

   ![](assets/wf_new_schema_generate_fda.png)

Gli indici vengono creati automaticamente durante la mappatura di una tabella (mappatura standard o FDA).
