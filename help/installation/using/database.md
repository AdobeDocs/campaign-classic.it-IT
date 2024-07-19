---
product: campaign
title: Raccomandazioni per il database Campaign Classic
description: Raccomandazioni per il database
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 2%

---

# Database{#database}



Il server di database può essere eseguito su qualsiasi sistema operativo, indipendentemente dal sistema operativo utilizzato dal server applicazioni o dai server applicazioni, purché vi sia connettività di rete tra di essi.

Il sistema operativo del server di database non è importante finché non è disponibile la connettività con i diversi componenti di Adobe Campaign.

Controllare anche la sezione [Livelli di accesso al database](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers).

## Microsoft SQL Server {#microsoft-sql-server}

Il client nativo deve essere installato sui server applicazioni Adobe Campaign.

È possibile verificare la presenza del client nativo nel server tramite il pannello di configurazione del driver ODBC, in **SQL Server Native Client 11.0**.

La seguente DLL di accesso deve essere presente: **sqlncli11.dll**.

Le DLL di accesso si trovano sul sito Web Microsoft.

>[!NOTE]
>
>L&#39;accesso a Microsoft SQL Server da un server applicazioni in esecuzione in Linux non è supportato.

## Oracle {#oracle}

>[!NOTE]
>
>I nomi di colonna con caratteri multibyte non sono supportati.

I parametri **NLS_NCHAR_CARATTERSET** e **NLS_CARATTERSET** devono essere configurati correttamente affinché il database possa funzionare in Unicode o ANSI.

Adobe Campaign utilizza la codifica Oracle predefinita. L’utilizzo di altra codifica può causare problemi di compatibilità: in questo caso, contatta il supporto tecnico.

Per informazioni sulla codifica, utilizzare il comando **sqlplus** seguente:

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

Per accedere a **sqlplus**, utilizzare il profilo utente di Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

È inoltre possibile fare riferimento a [Oracle Client in Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

È consigliabile installare il supporto UTF-8 durante l&#39;installazione del motore di database. In questo modo sarà possibile creare database Unicode.

**Argomento correlato**

* [Opzione non registrata nelle tabelle di Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
