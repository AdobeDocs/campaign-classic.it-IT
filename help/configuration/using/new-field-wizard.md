---
product: campaign
title: Procedura guidata per l’aggiunta di nuovi campi
description: Procedura guidata per l’aggiunta di nuovi campi
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 2350a531-7a26-4f26-90fe-8dac0cc26605
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 4%

---

# Procedura guidata per l’aggiunta di nuovi campi{#new-field-wizard}

![](../../assets/v7-only.svg)

Una procedura guidata accessibile tramite **[!UICONTROL Tools > Advanced > Add new fields]** consente di aggiungere uno o più campi a una tabella del database.

La convalida della procedura guidata aggiorna lo schema di estensione della tabella da estendere e avvia lo script SQL per modificare la struttura fisica del database.

L’assistente ha il vantaggio di aggiungere rapidamente un campo senza dover conoscere la struttura di uno schema di dati.

Lo svantaggio principale è la limitazione dei dati e delle proprietà da estendere.

Le schermate della procedura guidata contengono i seguenti passaggi:

1. La prima pagina ti consente di immettere il nome dello schema da estendere e lo spazio dei nomi dello schema di estensione in cui verranno salvate le modifiche:

   ![](assets/d_ncs_integration_schema_addfield.png)

1. La pagina successiva ti consente di immettere le proprietà del campo da aggiungere.

   ![](assets/d_ncs_integration_schema_addfield2.png)

1. Per confermare le modifiche, fai clic sul pulsante **[!UICONTROL Finish]** .

Nel nostro esempio viene creato automaticamente un file di estensione denominato &quot;cus:recipient&quot; e viene eseguito lo script SQL corrispondente:

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
