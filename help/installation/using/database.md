---
product: campaign
title: Raccomandazioni per il database Campaign Classic
description: Raccomandazioni per il database
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 4%

---

# Database{#database}



Il server di database può essere eseguito su qualsiasi sistema operativo, indipendentemente dal sistema operativo utilizzato dal server applicazioni o dai server applicazioni, purché vi sia connettività di rete tra di essi.

Il sistema operativo del server di database non è importante finché non è disponibile la connettività con i diversi componenti di Adobe Campaign.

Controlla anche la [Livelli di accesso al database](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) sezione.

## Microsoft SQL Server {#microsoft-sql-server}

Il client nativo deve essere installato sui server applicazioni Adobe Campaign.

È possibile verificare la presenza del client nativo sul server tramite il pannello di configurazione del driver ODBC, in **Client nativo SQL Server 11.0**.

Deve essere presente la seguente DLL di accesso: **sqlncli11.dll**.

Le DLL di accesso si trovano sul sito Web Microsoft.

>[!NOTE]
>
>L&#39;accesso a Microsoft SQL Server da un server applicazioni in esecuzione in Linux non è supportato.

##  Oracle {#oracle}

>[!NOTE]
>
>I nomi di colonna con caratteri multibyte non sono supportati.

Il **NLS_NCHAR_CHARACTER SET** e **NLS_CARATTERSET** I parametri devono essere configurati correttamente affinché il database funzioni in Unicode o ANSI.

Adobe Campaign utilizza la codifica Oracle predefinita. L’utilizzo di altra codifica può causare problemi di compatibilità: in questo caso, contatta il supporto tecnico.

Per informazioni sulla codifica, utilizza quanto segue **sqlplus** comando:

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

Per accedere a **sqlplus**, utilizza il profilo utente di Oracle:

```
su - oracle 
sqlplus 
[login] [password]
```

Puoi anche fare riferimento a [Client Oracle in Linux](../../installation/using/installing-packages-with-linux.md#oracle-client-in-linux).

## PostgresSQL {#postgressql}

È consigliabile installare il supporto UTF-8 durante l&#39;installazione del motore di database. In questo modo sarà possibile creare database Unicode.

**Argomento correlato**

* [Opzione non registrata nelle tabelle di Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
