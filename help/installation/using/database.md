---
product: campaign
title: Raccomandazioni per Campaign Classic Database
description: Raccomandazioni per il database
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: 8a0426c1-9e8d-4053-bc2b-6a550e2eed2f
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 2%

---

# Database{#database}



Il server di database può essere eseguito su qualsiasi sistema operativo specificato, indipendentemente dal sistema operativo utilizzato dal server o dai server applicazioni, purché tra di essi sia presente una connettività di rete.

Il sistema operativo del server di database non è importante finché è disponibile la connettività con i diversi componenti di Adobe Campaign.

Controlla anche il [Livelli di accesso al database](../../installation/using/prerequisites-of-campaign-installation-in-linux.md#database-access-layers) sezione .

## Microsoft SQL Server {#microsoft-sql-server}

Il client nativo deve essere installato sui server dell&#39;applicazione Adobe Campaign.

È possibile verificare la presenza del client nativo sul server tramite il pannello di configurazione del driver ODBC, in **Client nativo di SQL Server 11.0**.

La seguente DLL di accesso deve essere presente: **sqlncli11.dll**.

Le DLL di accesso si trovano sul sito web Microsoft.

>[!NOTE]
>
>L&#39;accesso a Microsoft SQL Server da un server applicazioni in esecuzione in Linux non è supportato.

##  Oracle {#oracle}

>[!NOTE]
>
>I nomi di colonna con caratteri multibyte non sono supportati.

La **NLS_NCHAR_CHARACTERSET** e **NLS_CHARACTERSET** i parametri devono essere configurati correttamente affinché il database funzioni in Unicode o ANSI.

Adobe Campaign utilizza la codifica Oracle predefinita. L’utilizzo di altre codifiche può causare problemi di compatibilità: in questo caso, contattare il supporto tecnico.

Per informazioni sulla codifica, utilizza quanto segue **sqlplus** comando:

```
SELECT * FROM nls_database_parameters ;
```

* Per un’installazione Unicode, le codifiche supportate sono:

   ```
   NLS_NCHAR_CHARACTERSET         AL16UTF16
   NLS_CHARACTERSET         AL32UTF8
   ```

* Per un&#39;installazione ANSI (non unicode), è supportata solo la seguente codifica:

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

* [Opzione non registrata nelle tabelle Adobe Campaign Classic](https://helpx.adobe.com/campaign/kb/unlogged-tables-classic.html)
