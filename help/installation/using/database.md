---
solution: Campaign Classic
product: campaign
title: Suggerimenti per il database Campaign Classic
description: Raccomandazioni del database
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 1%

---


# Database{#database}

Il server del database può essere eseguito su qualsiasi sistema operativo specificato, indipendentemente dal sistema operativo utilizzato dal server dell&#39;applicazione o dai server, a condizione che vi sia una connessione di rete tra di essi.

Il sistema operativo del server di database non è importante finché è disponibile la connettività con i diversi componenti di  Adobe Campaign.

Controllate anche la sezione [Livelli di accesso al database](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).

## Microsoft SQL Server {#microsoft-sql-server}

Il client nativo deve essere installato sui server applicazioni Adobe Campaign .

È possibile controllare il client nativo sul server tramite il pannello di configurazione del driver ODBC, in **SQL Server Native Client 11.0**.

La seguente DLL di accesso deve essere presente: **sqlncli11.dll**.

Le DLL di accesso si trovano nel sito Web di Microsoft.

>[!NOTE]
>
>L&#39;accesso a Microsoft SQL Server da un server applicazione in esecuzione in Linux non è supportato.

##  Oracle{#oracle}

>[!NOTE]
>
>I nomi delle colonne con caratteri multibyte non sono supportati.

I parametri **NLS_NCHAR_CHARACTERSET** e **NLS_CHARACTERSET** devono essere configurati correttamente affinché il database funzioni in Unicode o ANSI.

 Adobe Campaign utilizza  codifica Oracle predefinita. L’utilizzo di altre codifiche potrebbe causare problemi di compatibilità: in questo caso, contattare l&#39;assistenza tecnica.

Per informazioni sulla codifica, utilizzare il seguente comando **sqlplus**:

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

Per accedere a **sqlplus**, utilizzare il profilo utente Oracle :

```
su - oracle 
sqlplus 
[login] [password]
```

È inoltre possibile fare riferimento a [ Oracle Client in Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

È consigliabile installare il supporto UTF-8 quando si installa il motore di database. In questo modo sarà possibile creare database Unicode.

**Argomento correlato**

* [Opzione non registrata nelle tabelle Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
