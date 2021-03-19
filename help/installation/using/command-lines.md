---
solution: Campaign Classic
product: campaign
title: Righe di comando
description: Righe di comando
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 95d0686c4ddeb4e25eb918ca92cbd6a0b1aa1f3c
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Righe di comando{#command-lines}

Le seguenti righe di comando richiedono la possibilità di accedere al server dell&#39;applicazione. Per le distribuzioni ospitate da Adobe, questi comandi possono essere eseguiti solo per Adobe.

## Creare un&#39;istanza {#creating-an-instance}

La creazione di un&#39;istanza può essere eseguita utilizzando le righe di comando, con la sintassi seguente:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(dove **eng** e **fra** sono valori possibili per il parametro `[lang]`)

Il comando **nlserver config -addinstance:instance1/demo*/eng** consente di creare un&#39;istanza chiamata **instance1** in inglese con la demo della maschera DNS*.

## Dichiarare un database {#declaring-a-database}

È possibile associare un database esistente a un&#39;istanza dalla riga di comando utilizzando la sintassi seguente:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

I seguenti valori sono possibili per il parametro **`[rdbms]`**:

* **postgresql**: per PostgreSQL,
* **oracle**: ad Oracle,
* **mssql**: per Microsoft SQL Server,
* **DB2**: per il motore DB2.

Il seguente comando configura l&#39;istanza **demo** con il server di tipo SQL noto come **base6**, collegata all&#39;account **campaign** e alla relativa **password** sul server **dbsrv**:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

