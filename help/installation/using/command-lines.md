---
title: Righe di comando
seo-title: Righe di comando
description: Righe di comando
seo-description: null
page-status-flag: never-activated
uuid: fa897d6a-0326-4922-8936-2471af2f213c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: appendices
discoiquuid: 3621d4ec-8839-40c3-a574-486c408f79ba
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 5%

---


# Righe di comando{#command-lines}

Le seguenti righe di comando richiedono la capacità di accedere al server dell&#39;applicazione. Per le distribuzioni ospitate da  Adobe, questi comandi possono essere eseguiti solo da  Adobe.

## Creazione di un’istanza {#creating-an-instance}

La creazione di istanza può essere eseguita utilizzando le righe di comando, con la sintassi seguente:

```
nlserver config -addinstance:instance/masques DNS[/lang]
```

(dove **eng** e **fra** sono possibili valori per il `[lang]` parametro)

Il comando **nlserver config -addinstance:instance1/demo*/eng** consente di creare un&#39;istanza denominata **instance1** in inglese con la demo della maschera DNS*.

## Dichiarazione di un database {#declaring-a-database}

È possibile associare un database esistente a un&#39;istanza dalla riga di comando utilizzando la sintassi seguente:

```
nlserver config -setdblogin:[rbdms:]account[:database][/password]@server
```

I seguenti valori sono possibili per il **`[rdbms]`** parametro:

* **postgresql**: per PostgreSQL,
* **oracolo**: per Oracle,
* **mssql**: per Microsoft SQL Server,
* **DB2**: per il motore DB2.

Il seguente comando configura l&#39;istanza **demo** con il server di tipo SQL noto come **base6**, collegato all&#39;account **campagna** e alla relativa **password** sul server **dbsrv** :

```
 nlserver config -setdblogin:db:campaign:myBase/password@dbServer -instance:demo
```

