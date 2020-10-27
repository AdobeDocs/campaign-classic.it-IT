---
title: Creazione e configurazione del database
seo-title: Creazione e configurazione del database
description: Creazione e configurazione del database
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
translation-type: tm+mt
source-git-commit: fe7ce92bde3405fed3429475cdd5681e5837876f
workflow-type: tm+mt
source-wordcount: '1305'
ht-degree: 2%

---


# Creazione e configurazione del database{#creating-and-configuring-the-database}

Quando create un database,  Adobe Campaign offre due opzioni diverse:

1. Creazione o riciclo di un database: scegliete questa opzione se desiderate creare un nuovo database o riutilizzarne uno esistente. Fare riferimento al [caso 1: Creazione/riciclo di un database](#case-1--creating-recycling-a-database).
1. Utilizzo di un database esistente: scegliete questa opzione se l’amministratore ha già creato un database vuoto e desiderate usarlo; o per estendere la struttura di un database esistente. Fare riferimento al [caso 2: Utilizzo di un database](#case-2--using-an-existing-database)esistente.

I passaggi di configurazione sono descritti di seguito.

>[!CAUTION]
>
>I nomi di database, utenti e schemi non devono iniziare con un numero o includere caratteri speciali.
>
>Queste operazioni possono essere eseguite solo dall’identificatore **interno** . For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

## Caso 1: Creazione/riciclo di un database {#case-1--creating-recycling-a-database}

Di seguito sono illustrati i passaggi per la creazione di un database o il riciclaggio di una base esistente. Alcune configurazioni dipendono dal motore di database utilizzato:

Sono previsti i seguenti passaggi:

* [Passaggio 1 - Selezione del motore](#step-1---selecting-the-database-engine)del database
* [Passaggio 2 - Connessione al server](#step-2---connecting-to-the-server),
* [Fase 3 - Connessione e caratteristiche della banca dati](#step-3---connection-and-characteristics-of-the-database),
* [Passo 4 - Pacchetti da installare](#step-4---packages-to-install),
* [Passaggio 5 - Passaggi](#step-5---creation-steps)di creazione,
* [Passaggio 6 - Creazione del database](#step-6---creating-the-database).

### Passaggio 1 - Selezione del motore del database {#step-1---selecting-the-database-engine}

Selezionare il motore del database tra quelli presenti nell&#39;elenco a discesa.

![](assets/s_ncs_install_db_select_engine.png)

I database supportati sono presentati nella sezione [Matrice](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)di compatibilità.

Identificare il server e scegliere il tipo di operazione da eseguire. In questo caso, **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

A seconda del motore di database selezionato, le informazioni di identificazione del server possono variare.

* Per un motore **Oracle** , compilare il nome **** TNS definito per il server applicazioni.
* Per un motore **PostgreSQL** o **DB2** , è necessario specificare il nome DNS (o l&#39;indirizzo IP) definito nel server dell&#39;applicazione per accedere al server del database.
* Per un motore **Microsoft SQL Server** , è necessario definire: il nome DNS (o indirizzo IP) definito sul server dell’applicazione per accedere al server del database: **DNS** o **DNS`\<instance>`** (modalità di istanza),

   >[!CAUTION]
   >
   > A partire dalla versione 20.3, l&#39;autenticazione di Windows NT è disattivata. **[!UICONTROL SQL Server authentication]** è ora l&#39;unica modalità di autenticazione disponibile per Microsoft SQL Server. [Leggi tutto](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### Passaggio 2 - Connessione al server {#step-2---connecting-to-the-server}

Nella **[!UICONTROL Server access]** finestra, definite l&#39;accesso al server del database.

![](assets/s_ncs_install_db_oracle_creation02.png)

A tal fine, immettete il nome e la password di un account **di sistema** Amministrazione che dispone dell&#39;autorizzazione per accedere ai database, ad esempio:

* **sistema** per un database Oracle,
* **come** per un database di Microsoft SQL Server,
* **postgres** per un database PostgreSQL,
* **db2inst1** per un database DB2.

### Passaggio 3 - Connessione e caratteristiche del database {#step-3---connection-and-characteristics-of-the-database}

La procedura seguente consente di configurare le impostazioni per l’accesso al database.

![](assets/s_ncs_install_db_oracle_creation03.png)

È necessario definire le seguenti impostazioni:

* Specificate il nome del database da creare.

   >[!NOTE]
   >
   >Per un database DB2, il nome del database non deve superare gli 8 caratteri.

* Immettere la password dell&#39;account collegato al database.
* Specificate se il database deve essere in Unicode o meno.

   L&#39; **[!UICONTROL Unicode database]** opzione consente di memorizzare tutti i tipi di caratteri in Unicode, indipendentemente dalla lingua.

   >[!NOTE]
   >
   >Con un database Oracle, l&#39; **[!UICONTROL Unicode storage]** opzione consente di utilizzare i campi di tipo **NCLOB** e **NVARCHAR** .
   > 
   >Se non si seleziona questa opzione, il set di caratteri (charset) del database Oracle deve abilitare la memorizzazione dei dati in tutte le lingue (SI consiglia AL32UTF8).

* Scegliete un fuso orario per il database e specificate se deve essere in UTC (se disponibile).

   Per ulteriori informazioni, consulta Gestione del fuso [orario](../../installation/using/time-zone-management.md).

### Passaggio 4 - Pacchetti da installare {#step-4---packages-to-install}

Selezionate i pacchetti da installare.

Fate riferimento al contratto di licenza per verificare quali soluzioni e opzioni sono autorizzate a installare, ad esempio &quot;Interazione&quot; o &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Passaggio 5 - Fase di creazione {#step-5---creation-steps}

La **[!UICONTROL Creation steps]** finestra consente di visualizzare e modificare lo script SQL utilizzato per creare le tabelle.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Per un database Oracle, Microsoft SQL Server o PostgreSQL, l&#39;amministratore può anche definire i parametri **di** memorizzazione da utilizzare per la creazione di oggetti del database.

   Questi parametri ricevono i nomi esatti della tablespace (avviso: con distinzione tra maiuscole e minuscole). Sono rispettivamente memorizzati nel **[!UICONTROL Administration > Platform > Options]** nodo nelle seguenti opzioni (vedere [](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: tabelle utente basate su uno schema
   * **WdbcOptions_TableSpaceIndex**: indice di tabelle utente basate su uno schema
   * **WdbcOptions_TableSpaceWork**: tabelle di lavoro senza schema
   * **WdbcOptions_TableSpaceWorkIndex**: indice di tabelle di lavoro senza schema

* Per un database Oracle, l&#39;utente Adobe Campaign  deve avere accesso alle librerie Oracle, in genere come membro del gruppo **oinstall** .
* L&#39; **[!UICONTROL Set or change the administrator password]** opzione consente di inserire la password collegata all&#39;operatore Adobe Campaign  con diritti di amministratore.

   È consigliabile definire una password amministratore  account Adobe Campaign a scopo di sicurezza.

### Passaggio 6 - Creazione del database {#step-6---creating-the-database}

La fase finale della procedura guidata consente di creare il database. Fate clic **[!UICONTROL Start]** per confermare.

![](assets/s_ncs_install_db_oracle_creation06.png)

Una volta creato il database, potete riconnettervi per finalizzare la configurazione dell&#39;istanza.

È ora necessario avviare la procedura guidata di distribuzione per completare la configurazione dell&#39;istanza. Fare riferimento alla procedura guidata [di distribuzione](../../installation/using/deploying-an-instance.md#deployment-wizard).

Le impostazioni di connessione per il database collegato all&#39;istanza sono memorizzate nel file **`/conf/config-<instance>.xml`** presente nella directory di installazione di Adobe Campaign .

Esempio di configurazione di Microsoft SQL Server nel database base61 collegato all&#39;account &#39;campaign&#39; con password crittografata:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Caso 2: Utilizzo di un database esistente {#case-2--using-an-existing-database}

Il database, così come l&#39;utente, devono essere stati creati dall&#39;amministratore del database e i diritti di accesso devono essere stati configurati correttamente.

Ad esempio, per un database Oracle, i diritti minimi richiesti sono: CONCEDERE CONNECT, RISORSE E TABLESPACE ILLIMITATI.

Per utilizzare un database esistente, procedere come segue:

* [Passaggio 1 - Scelta del motore](#step-1---choosing-the-database-engine)del database,
* [Passaggio 2 - Impostazioni](#step-2---database-connection-settings)di connessione del database,
* [Passo 3 - Pacchetti da installare](#step-3---packages-to-install),
* [Passaggio 4 - Passaggi](#step-4---creation-steps)di creazione,
* [Passaggio 5 - Creazione del database](#step-5---creating-the-database).

### Passaggio 1 - Scelta del motore del database {#step-1---choosing-the-database-engine}

Scegliete il motore del database dall&#39;elenco a discesa.

![](assets/s_ncs_install_db_select_engine.png)

Identificare il server e scegliere il tipo di operazione da eseguire. In questo caso, **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

A seconda del motore di database selezionato, le informazioni di identificazione del server possono variare.

* Per un motore **Oracle** , compilare il nome **** TNS definito per il server applicazioni.
* Per un motore **PostgreSQL** o **DB2** , è necessario specificare il nome DNS (o l&#39;indirizzo IP) definito nel server dell&#39;applicazione per accedere al server del database.
* Per un motore **Microsoft SQL Server** , è necessario definire:

   1. il nome DNS (o indirizzo IP) definito sul server dell’applicazione per accedere al server del database,
   1. metodo di protezione utilizzato per accedere a Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** o **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Passaggio 2 - Impostazioni connessione database {#step-2---database-connection-settings}

Nella **[!UICONTROL Database]** finestra, definite le impostazioni di connessione al database.

![](assets/s_ncs_install_db_oracle_exists_02.png)

È necessario definire le seguenti impostazioni:

* Immettere il nome del database da utilizzare,
* Immettere il nome e la password dell&#39;account associato al database,

   >[!NOTE]
   >
   >Accertatevi che il nome dello schema e il nome utente corrispondano. Il modo consigliato per creare il database è tramite il client della console della campagna.
   >Per un database Oracle, non è necessario inserire il nome account.

* Specificate se il database deve essere Unicode o meno.

### Passaggio 3 - Pacchetti da installare {#step-3---packages-to-install}

Selezionate i pacchetti da installare.

Fate riferimento al contratto di licenza per verificare quali soluzioni e opzioni avete diritto di installare, ad esempio &quot;Interazione&quot; o &quot;Lead&quot;.

![](assets/s_ncs_install_modules.png)

### Passaggio 4 - Passaggi di creazione {#step-4---creation-steps}

La **[!UICONTROL Creation steps]** finestra consente di visualizzare e modificare lo script SQL utilizzato per creare le tabelle.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Per i database Oracle, Microsoft SQL Server o PostgreSQL, l&#39;amministratore può definire i parametri **di** memorizzazione da utilizzare per la creazione degli oggetti del database.
* Per un database Oracle, l&#39;utente Adobe Campaign  deve avere accesso alle librerie Oracle, in genere come membro del gruppo **oinstall** .
* L&#39; **[!UICONTROL Set or change the administrator password]** opzione consente di inserire la password collegata all&#39;operatore Adobe Campaign  con diritti di amministratore.

   È consigliabile definire una password amministratore  account Adobe Campaign a scopo di sicurezza.

### Passaggio 5 - Creazione del database {#step-5---creating-the-database}

La fase finale della procedura guidata consente di creare il database. Fate clic **[!UICONTROL Start]** per confermare.

![](assets/s_ncs_install_db_oracle_creation06.png)

Una volta completata la creazione del database, potete riconnettervi per finalizzare la configurazione dell&#39;istanza.

È ora necessario avviare la procedura guidata di distribuzione per completare la configurazione dell&#39;istanza. Fare riferimento alla procedura guidata [di distribuzione](../../installation/using/deploying-an-instance.md#deployment-wizard).

Le impostazioni di connessione per il database collegato all&#39;istanza sono memorizzate nel file **`/conf/config-<instance>.xml`** presente nella directory di installazione di Adobe Campaign .

Esempio di configurazione di Microsoft SQL Server nel database base61 collegato all&#39;account &#39;campaign&#39; con password crittografata:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

