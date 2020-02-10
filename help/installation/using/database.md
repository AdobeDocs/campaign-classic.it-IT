---
title: Database
seo-title: Database
description: Database
seo-description: null
page-status-flag: never-activated
uuid: b318365c-8846-4c1d-b5f7-ece55fb8c4af
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
discoiquuid: 1dcf01af-c2f3-4975-ba05-628d52952064
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 28614a6b0c45deef17d9b3275a16e65bdff4538b

---


# Database{#database}

Il server del database può essere eseguito su qualsiasi sistema operativo specificato, indipendentemente dal sistema operativo utilizzato dal server dell&#39;applicazione o dai server, a condizione che vi sia una connessione di rete tra di essi.

Il sistema operativo del server del database non è importante finché è disponibile la connettività con i diversi componenti di Adobe Campaign.

Controlla anche la sezione Livelli [di accesso al](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) database.

## Microsoft SQL Server {#microsoft-sql-server}

Il client nativo deve essere installato sui server delle applicazioni Adobe Campaign.

È possibile verificare il client nativo sul server tramite il pannello di configurazione del driver ODBC, in Client **nativo** SQL (per client Microsoft SQL Server 2005) o client nativo **SQL Server 10.0** (per client Microsoft SQL Server 2008 e 2008 R2), o client nativo **SQL Server 11.0** (per Microsoft SQL Server 2 012 clienti).

Devono essere presenti le seguenti DLL di accesso:

* **sqlncli.dll** per il client Microsoft SQL Server 2005,
* **sqlncli10.dll** per client Microsoft SQL Server 2008 e 2008 R2,
* **sqlncli11.dll** per il client Microsoft SQL Server 2012.

   Le DLL di accesso si trovano nel sito Web di Microsoft.

>[!NOTE]
>
>L&#39;accesso a Microsoft SQL Server da un server applicazione in esecuzione in Linux non è supportato.

## Oracle {#oracle}

>[!NOTE]
>
>I nomi delle colonne con caratteri multibyte non sono supportati.

Affinché il database funzioni in modalità Unicode o ANSI, i parametri **NLS_NCHAR_CHARACTERSET** e **NLS_CHARACTERSET** devono essere configurati correttamente.

Adobe Campaign utilizza la codifica Oracle predefinita. L’utilizzo di altre codifiche potrebbe causare problemi di compatibilità: in questo caso, contattare l&#39;assistenza tecnica.

Per informazioni sulla codifica, utilizzate il seguente **comando sqlplus** :

```
SELECT * FROM nls_database_parameters ;
```

* Per un&#39;installazione Unicode, le codifiche supportate sono:

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* Per un&#39;installazione ANSI (non Unicode), è supportata solo la seguente codifica:

```
  NLS_CHARACTERSET WE8MSWIN1252
```

Per accedere a **sqlplus**, utilizzare il profilo utente Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

È inoltre possibile fare riferimento a [Oracle Client in Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

È consigliabile installare il supporto UTF-8 quando si installa il motore di database. In questo modo sarà possibile creare database Unicode.

**Argomento correlato**

* [Opzione non registrata nelle tabelle di Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)