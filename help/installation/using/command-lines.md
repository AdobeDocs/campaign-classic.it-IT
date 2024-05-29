---
product: campaign
title: Righe di comando
description: Righe di comando
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: b7dedddc080d1ea8db700fabc9ee03238b3706cc
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Righe di comando{#command-lines}



Le seguenti righe di comando richiedono la possibilità di accedere al server applicazioni. Per le distribuzioni in hosting da Adobe, questi comandi possono essere eseguiti solo da Adobe.

## Creare un’istanza {#creating-an-instance}

La creazione di un’istanza può essere eseguita utilizzando le righe di comando con la sintassi:

```sql
nlserver config -addinstance:instance/masques DNS[/lang]
```

(dove **eng** e **fra** sono valori possibili per `[lang]` parameter)

Il comando **configurazione nlserver -addinstance:instance1/demo&#42;/eng** consente di creare un’istanza denominata **instance1** in inglese con la demo della maschera DNS&#42;.

## Dichiarare un database {#declaring-a-database}

È possibile associare un database esistente a un&#39;istanza dalla riga di comando utilizzando la sintassi seguente:

```sql
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

I seguenti valori sono possibili per **`[rdbms]`** parametro:

* **postgresql**: per PostgreSQL
* **oracle**: ad Oracle,
* **mssql**: per Microsoft SQL Server,
* **DB2**: per il motore DB2.

Il comando seguente configura **demo** istanza con il tipo di server SQL noto come **base6**, collegato al **campagna** account e relativi **password** il **dbsrv** server:

```sql
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
