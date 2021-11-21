---
product: campaign
title: Creazione e configurazione del database
description: Creazione e configurazione del database
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 1%

---

# Creazione e configurazione del database{#creating-and-configuring-the-database}

![](../../assets/v7-only.svg)

Quando crei un database, Adobe Campaign fornisce due opzioni diverse:

1. Creazione o riciclo di un database: scegliere questa opzione se si desidera creare un nuovo database o riutilizzarne uno esistente. Fai riferimento a [Caso 1: Creazione/riciclo di un database](#case-1--creating-recycling-a-database).
1. Utilizzo di un database esistente: scegliere questa opzione se l&#39;amministratore ha già creato un database vuoto e desideri utilizzarlo; o di estendere la struttura di un database esistente. Fai riferimento a [Caso 2: Utilizzo di un database esistente](#case-2--using-an-existing-database).

I passaggi di configurazione sono descritti di seguito.

>[!CAUTION]
>
>I nomi dei database, degli utenti e degli schemi non devono iniziare con un numero o includere caratteri speciali.
>
>Solo il **interno** identifier può eseguire queste operazioni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Caso 1: Creazione/riciclo di un database {#case-1--creating-recycling-a-database}

Di seguito sono illustrati i passaggi per la creazione di un database o per il riciclaggio di una base esistente. Alcune configurazioni dipendono dal motore di database utilizzato:

Sono previsti i seguenti passaggi:

* [Passaggio 1 - Selezione del motore di database](#step-1---selecting-the-database-engine),
* [Passaggio 2 - Connessione al server](#step-2---connecting-to-the-server),
* [Passaggio 3 - Connessione e caratteristiche della banca dati](#step-3---connection-and-characteristics-of-the-database),
* [Passaggio 4 - Pacchetti da installare](#step-4---packages-to-install),
* [Passaggio 5: fasi di creazione](#step-5---creation-steps),
* [Passaggio 6 - Creazione del database](#step-6---creating-the-database).

### Passaggio 1 - Selezione del motore di database {#step-1---selecting-the-database-engine}

Selezionare il motore di database tra quelli nell&#39;elenco a discesa.

![](assets/s_ncs_install_db_select_engine.png)

I database supportati sono elencati in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Identificare il server e scegliere il tipo di operazione da eseguire. In questo caso, **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

A seconda del motore di database selezionato, le informazioni di identificazione del server possono variare.

* Per un **Oracle** motore, popolare **Nome TNS** definito per l&#39;application server.
* Per **PostgreSQL** o **DB2** per accedere al server di database, è necessario specificare il nome DNS (o indirizzo IP) definito nel server applicazioni.
* Per **Microsoft SQL Server** motore, è necessario definire: nome DNS (o indirizzo IP) definito nel server dell&#39;applicazione per accedere al server del database: **DNS** o **DNS`\<instance>`** (modalità istanza),

   >[!CAUTION]
   >
   > A partire dalla versione 20.3, l&#39;autenticazione Windows NT è disattivata. **[!UICONTROL SQL Server authentication]** è ora l&#39;unica modalità di autenticazione disponibile per Microsoft SQL Server. [Leggi tutto](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### Passaggio 2 - Connessione al server {#step-2---connecting-to-the-server}

In **[!UICONTROL Server access]** finestra, definire l&#39;accesso al server di database.

![](assets/s_ncs_install_db_oracle_creation02.png)

A questo scopo, immetti il nome e la password di un **Account del sistema di amministrazione** che ha l&#39;autorizzazione ad accedere alle banche dati, ossia:

* **sistema** per un database di Oracle,
* **sa** per un database Microsoft SQL Server,
* **poster** per un database PostgreSQL,
* **db2inst1** per un database DB2.

### Passaggio 3 - Connessione e caratteristiche della banca dati {#step-3---connection-and-characteristics-of-the-database}

Il passaggio seguente ti consente di configurare le impostazioni per l’accesso al database.

![](assets/s_ncs_install_db_oracle_creation03.png)

È necessario definire le seguenti impostazioni:

* Specificare il nome del database da creare.

   >[!NOTE]
   >
   >Per un database DB2, il nome del database non deve superare gli 8 caratteri.

* Immettere la password dell&#39;account collegato al database.
* Indicare se il database deve essere in Unicode o meno.

   La **[!UICONTROL Unicode database]** consente di memorizzare tutti i tipi di caratteri in Unicode, indipendentemente dalla lingua.

   >[!NOTE]
   >
   >Con un database di Oracle, il **[!UICONTROL Unicode storage]** consente di utilizzare **NCLOB** e **NVARCHAR** digitare i campi.
   > 
   >Se non si seleziona questa opzione, il set di caratteri (charset) del database Oracle deve abilitare l’archiviazione dei dati in tutte le lingue (AL32UTF8 è consigliato).

* Scegliere un fuso orario per il database e specificare se si desidera che sia in UTC (se disponibile).

   Per ulteriori informazioni, consulta [Gestione del fuso orario](../../installation/using/time-zone-management.md).

### Passaggio 4 - Pacchetti da installare {#step-4---packages-to-install}

Selezionare i pacchetti da installare.

Fai riferimento al contratto di licenza per verificare quali soluzioni e opzioni hai diritto di installare, ad esempio &quot;Interazione&quot; o &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Passaggio 5: fasi di creazione {#step-5---creation-steps}

La **[!UICONTROL Creation steps]** consente di visualizzare e modificare lo script SQL utilizzato per creare le tabelle.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Ad Oracle, il database Microsoft SQL Server o PostgreSQL, l&#39;amministratore può anche definire il **parametri di archiviazione** da utilizzare per la creazione di oggetti di database.

   Questi parametri ricevono i nomi esatti della tablespace (avviso: sensibile a maiuscole e minuscole). Sono rispettivamente memorizzati nel **[!UICONTROL Administration > Platform > Options]** nelle seguenti opzioni (vedi [questa sezione](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: tabelle utente basate su uno schema
   * **WdbcOptions_TableSpaceIndex**: indice delle tabelle utente basato su uno schema
   * **WdbcOptions_TableSpaceWork**: tabelle di lavoro prive di schema
   * **WdbcOptions_TableSpaceWorkIndex**: indice di tabelle di lavoro senza schema

* Per un database di Oracle, l’utente Adobe Campaign deve avere accesso alle librerie di Oracli, in genere come membro della **oinstall** gruppo.
* La **[!UICONTROL Set or change the administrator password]** consente di inserire la password collegata all’operatore Adobe Campaign con diritti di amministratore.

   È consigliabile definire una password per l’amministratore di un account Adobe Campaign a scopo di sicurezza.

### Passaggio 6 - Creazione del database {#step-6---creating-the-database}

La fase finale della procedura guidata consente di creare il database. Fai clic su **[!UICONTROL Start]** per confermare.

![](assets/s_ncs_install_db_oracle_creation06.png)

Una volta creato il database, puoi riconnettersi per finalizzare la configurazione dell&#39;istanza.

Ora è necessario avviare la procedura guidata di distribuzione per completare la configurazione dell’istanza. Fai riferimento a [Procedura guidata di distribuzione](../../installation/using/deploying-an-instance.md#deployment-wizard).

Le impostazioni di connessione per il database collegato all&#39;istanza sono memorizzate nel file **`/conf/config-<instance>.xml`** si trova nella directory di installazione di Adobe Campaign.

Esempio di configurazione di Microsoft SQL Server nel database base61 collegato all&#39;account &#39;campaign&#39; con password crittografata:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Caso 2: Utilizzo di un database esistente {#case-2--using-an-existing-database}

Il database e l&#39;utente devono essere stati creati dall&#39;amministratore del database e i diritti di accesso devono essere configurati correttamente.

Ad Oracle, per un database di , i diritti minimi richiesti sono: CONCEDERE CONNECT, RISORSE E TABLESPACE ILLIMITATO.

Per utilizzare un database esistente, procedere come segue:

* [Passaggio 1 - Scelta del motore di database](#step-1---choosing-the-database-engine),
* [Passaggio 2: impostazioni della connessione al database](#step-2---database-connection-settings),
* [Passaggio 3 - Pacchetti da installare](#step-3---packages-to-install),
* [Passaggio 4: fasi di creazione](#step-4---creation-steps),
* [Passaggio 5 - Creazione del database](#step-5---creating-the-database).

### Passaggio 1 - Scelta del motore di database {#step-1---choosing-the-database-engine}

Scegliere il motore di database dall&#39;elenco a discesa.

![](assets/s_ncs_install_db_select_engine.png)

Identificare il server e scegliere il tipo di operazione che si desidera eseguire. In questo caso, **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

A seconda del motore di database selezionato, le informazioni di identificazione del server possono variare.

* Per un **Oracle** motore, popolare **Nome TNS** definito per l&#39;application server.
* Per **PostgreSQL** o **DB2** per accedere al server di database, è necessario specificare il nome DNS (o indirizzo IP) definito nel server applicazioni.
* Per **Microsoft SQL Server** motore, è necessario definire:

   1. il nome DNS (o indirizzo IP) definito sul server dell&#39;applicazione per accedere al server del database,
   1. metodo di protezione utilizzato per accedere a Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** o **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Passaggio 2: impostazioni della connessione al database {#step-2---database-connection-settings}

In **[!UICONTROL Database]** definire le impostazioni di connessione al database.

![](assets/s_ncs_install_db_oracle_exists_02.png)

È necessario definire le seguenti impostazioni:

* Immettere il nome del database da utilizzare,
* Immettere il nome e la password dell&#39;account associato a questo database,

   >[!NOTE]
   >
   >Assicurati che il nome dello schema e il nome utente corrispondano. Il modo consigliato per creare il database è tramite il client della console di Campaign.
   >Per un database di Oracle, non è necessario immettere il nome dell&#39;account.

* Indicare se il database deve essere Unicode o meno.

### Passaggio 3 - Pacchetti da installare {#step-3---packages-to-install}

Selezionare i pacchetti da installare.

Fai riferimento al contratto di licenza per verificare quali soluzioni e opzioni hai diritto di installare, ad esempio &quot;Interazione&quot; o &quot;Lead&quot;.

![](assets/s_ncs_install_modules.png)

### Passaggio 4: fasi di creazione {#step-4---creation-steps}

La **[!UICONTROL Creation steps]** consente di visualizzare e modificare lo script SQL utilizzato per creare le tabelle.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Ad Oracle, i database Microsoft SQL Server o PostgreSQL, l&#39;amministratore può definire il **parametri di archiviazione** da utilizzare per la creazione di oggetti di database.
* Per un database di Oracle, l’utente Adobe Campaign deve avere accesso alle librerie di Oracli, in genere come membro della **oinstall** gruppo.
* La **[!UICONTROL Set or change the administrator password]** consente di inserire la password collegata all’operatore Adobe Campaign con diritti di amministratore.

   È consigliabile definire una password per l’amministratore di un account Adobe Campaign a scopo di sicurezza.

### Passaggio 5 - Creazione del database {#step-5---creating-the-database}

La fase finale della procedura guidata consente di creare il database. Fai clic su **[!UICONTROL Start]** per confermare.

![](assets/s_ncs_install_db_oracle_creation06.png)

Una volta completata la creazione del database, puoi riconnettersi per finalizzare la configurazione dell&#39;istanza.

Ora è necessario avviare la procedura guidata di distribuzione per completare la configurazione dell’istanza. Fai riferimento a [Procedura guidata di distribuzione](../../installation/using/deploying-an-instance.md#deployment-wizard).

Le impostazioni di connessione per il database collegato all&#39;istanza sono memorizzate nel file **`/conf/config-<instance>.xml`** si trova nella directory di installazione di Adobe Campaign.

Esempio di configurazione di Microsoft SQL Server nel database base61 collegato all&#39;account &#39;campaign&#39; con password crittografata:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
