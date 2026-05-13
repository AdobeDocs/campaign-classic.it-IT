---
product: campaign
title: Righe di comando
description: Righe di comando
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
TQID: https://experienceleague.adobe.com/e85vFL0iZ586ICGGH1CP6fgqGU717W1aPDWqmj40-3s
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 144
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
