---
title: Procedura guidata per l’aggiunta di nuovi campi
seo-title: Procedura guidata per l’aggiunta di nuovi campi
description: Procedura guidata per l’aggiunta di nuovi campi
seo-description: null
page-status-flag: never-activated
uuid: 2c8d35db-042a-47cf-a7a6-3bb63bf40d94
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 6da65fb5-18a1-41a0-96d8-588e383f944b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 5%

---


# Procedura guidata per l’aggiunta di nuovi campi{#new-field-wizard}

Una procedura guidata accessibile tramite **[!UICONTROL Tools > Advanced > Add new fields]** consente di aggiungere uno o più campi a una tabella del database.

La convalida della procedura guidata aggiorna lo schema di estensione della tabella da estendere e avvia lo script SQL per modificare la struttura fisica del database.

Questo assistente ha il vantaggio di aggiungere rapidamente un campo senza dover conoscere la struttura di uno schema dati.

Lo svantaggio principale è la limitazione dei dati e delle proprietà da estendere.

Le schermate della procedura guidata contengono i seguenti passaggi:

1. La prima pagina consente di inserire il nome dello schema da estendere e lo spazio dei nomi dello schema di estensione in cui verranno salvate le modifiche:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. La pagina successiva consente di immettere le proprietà del campo da aggiungere.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Per confermare le modifiche, fate clic sul **[!UICONTROL Finish]** pulsante .

Viene creato automaticamente un file di estensione, denominato &quot;cus:Recipient&quot; nel nostro esempio, e viene eseguito lo script SQL corrispondente:

```
<srcSchema extendedSchema="nms:recipient" label="Recipients" name="recipient"  namespace="cus">  
  <element name="recipient">    
    <attribute belongsTo="cus:recipient" dataPolicy="email" label="Email" length="80" name="email1" sqlname="sEmail1" type="string" user="true"/>  
  </element>
</srcSchema>
```

>[!NOTE]
>
>Per impostazione predefinita, i campi aggiunti sono dichiarati con la proprietà **user** (con il valore &quot;true&quot;). Questo consente di visualizzare e modificare il campo nel modulo di input dello schema esteso utilizzando un controllo di tipo &quot;treeEdit&quot; (fare riferimento a Modulo di input).

