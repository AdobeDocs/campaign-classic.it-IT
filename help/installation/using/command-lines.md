---
solution: Campaign Classic
product: campaign
title: Righe di comando
description: Righe di comando
audience: installation
content-type: reference
topic-tags: appendices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 4%

---


# Righe di comando{#command-lines}

Le seguenti righe di comando richiedono la capacità di accedere al server dell&#39;applicazione. Per le distribuzioni ospitate da  Adobe, questi comandi possono essere eseguiti solo da  Adobe.

## Creazione di un&#39;istanza {#creating-an-instance}

La creazione di istanza può essere eseguita utilizzando le righe di comando, con la sintassi seguente:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(dove **eng** e **fra** sono valori possibili per il parametro `[lang]`)

Il comando **config -addinstance:instance1/demo*/eng** consente di creare un&#39;istanza denominata **instance1** in inglese con la demo della maschera DNS*.

## Dichiarazione di un database {#declaring-a-database}

È possibile associare un database esistente a un&#39;istanza dalla riga di comando utilizzando la sintassi seguente:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

I seguenti valori sono possibili per il parametro **`[rdbms]`**:

* **postgresql**: per PostgreSQL,
* **oracle**: per  Oracle,
* **mssql**: per Microsoft SQL Server,
* **DB2**: per il motore DB2.

Il seguente comando configura l&#39;istanza **demo** con il server di tipo SQL noto come **base6**, collegata all&#39;account **campaign** e alla relativa **password** sul server **dbsrv**:

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

