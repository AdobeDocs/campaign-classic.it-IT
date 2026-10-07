---
product: campaign
title: Righe di comando
description: Righe di comando
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: 'https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 7f0a1ee5-eeb8-5478-a9cd-b1896f033118
    internal-label: Instance Settings
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: e656c701-3899-4db3-989c-de0980ddfffa
    internal-label: Installation
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 4%
---
# Righe di comando{#command-lines}



Le seguenti righe di comando richiedono la possibilità di accedere al server applicazioni. Per le distribuzioni in hosting da Adobe, questi comandi possono essere eseguiti solo da Adobe.

## Creare un’istanza {#creating-an-instance}

La creazione di un’istanza può essere eseguita utilizzando le righe di comando con la sintassi:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(dove **eng** e **fra** sono valori possibili per il parametro `[lang]`)

Il comando **nlserver config -addinstance:instance1/demo&#42;/eng** consente di creare un&#39;istanza denominata **instance1** in inglese con la demo della maschera DNS&#42;.

## Dichiarare un database {#declaring-a-database}

È possibile associare un database esistente a un&#39;istanza dalla riga di comando utilizzando la sintassi seguente:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

Per il parametro **`[rdbms]`** sono possibili i seguenti valori:

* **postgresql**: per PostgreSQL,
* **oracle**: per Oracle,
* **mssql**: per Microsoft SQL Server,

Il comando seguente configura l&#39;istanza **demo** con il server dei tipi SQL noto come **base6**, collegato all&#39;account **campaign** e alla relativa **password** nel server **dbsrv**:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
