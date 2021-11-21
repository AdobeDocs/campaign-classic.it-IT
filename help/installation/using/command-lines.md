---
product: campaign
title: Righe di comando
description: Righe di comando
audience: installation
content-type: reference
topic-tags: appendices
exl-id: 5cd4abb0-2bd2-4b23-902c-41b08a1d2f7a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---

# Righe di comando{#command-lines}

![](../../assets/v7-only.svg)

Le seguenti righe di comando richiedono la possibilità di accedere al server dell&#39;applicazione. Per le distribuzioni ospitate da Adobe, questi comandi possono essere eseguiti solo per Adobe.

## Creare un’istanza {#creating-an-instance}

La creazione di un&#39;istanza può essere eseguita utilizzando le righe di comando, con la sintassi seguente:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(4) **eng** e **a** sono possibili valori per `[lang]` )

Comando **nlserver config -addinstance:instance1/demo*/eng** consente di creare un’istanza denominata **instance1** in inglese con demo maschera DNS*.

## Dichiarare un database {#declaring-a-database}

È possibile associare un database esistente a un&#39;istanza dalla riga di comando utilizzando la sintassi seguente:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

I seguenti valori sono possibili per **`[rdbms]`** parametro:

* **postgresql**: per PostgreSQL,
* **oracle**: ad Oracle,
* **mssql**: per Microsoft SQL Server,
* **DB2**: per il motore DB2.

Il comando seguente configura il **demo** istanza con SQL type server noto come **base6**, collegato al **campagna** il conto e il suo **password** sulla **dbsrv** server:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```
