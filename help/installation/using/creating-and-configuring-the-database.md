---
product: campaign
title: Creazione e configurazione del database
description: Creazione e configurazione del database
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 2%

---

# Creazione e configurazione del database{#creating-and-configuring-the-database}

Quando si crea un database, Adobe Campaign offre due opzioni diverse:

1. Creazione o riciclo di un database: scegliere questa opzione se si desidera creare un nuovo database o riutilizzarne uno esistente. Fai riferimento a [Caso 1: creazione/riciclaggio di un database](#case-1--creating-recycling-a-database).
1. Utilizzo di un database esistente: scegliere questa opzione se l&#39;amministratore ha già creato un database vuoto e si desidera utilizzarlo oppure per estendere la struttura di un database esistente. Fai riferimento a [Caso 2: utilizzo di un database esistente](#case-2--using-an-existing-database).

I passaggi di configurazione sono descritti di seguito.

>[!CAUTION]
>
>I nomi di database, utenti e schemi non devono iniziare con un numero né includere caratteri speciali.
>
>Solo il **interno** L&#39;identificatore può eseguire queste operazioni. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Caso 1: creazione/riciclaggio di un database {#case-1--creating-recycling-a-database}

Di seguito sono riportati i passaggi per la creazione di un database o il riciclaggio di una base esistente. Alcune configurazioni dipendono dal motore di database utilizzato:

Sono previste le seguenti fasi:

* [Passaggio 1: selezione del modulo di gestione di database](#step-1---selecting-the-database-engine),
* [Passaggio 2 - Connessione al server](#step-2---connecting-to-the-server),
* [Passaggio 3: connessione e caratteristiche del database](#step-3---connection-and-characteristics-of-the-database),
* [Passaggio 4 - Pacchetti da installare](#step-4---packages-to-install),
* [Passaggio 5: passaggi di creazione](#step-5---creation-steps),
* [Passaggio 6: creazione del database](#step-6---creating-the-database).

### Passaggio 1: selezione del modulo di gestione di database {#step-1---selecting-the-database-engine}

Selezionare il modulo di gestione di database nell&#39;elenco a discesa.

![](assets/s_ncs_install_db_select_engine.png)

I database supportati sono elencati in Campaign [Matrice di compatibilità](../../rn/using/compatibility-matrix.md).

Identificare il server e scegliere il tipo di operazione da eseguire. In questo caso, **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

A seconda del motore di database selezionato, le informazioni di identificazione del server possono variare.

* Per un **Oracle** motore, compila il **Nome TNS** definito per il server applicazioni.
* Per un **PostgreSQL** o **DB2** per accedere al server di database, è necessario specificare il nome DNS (o l&#39;indirizzo IP) definito nel server applicazioni.
* Per un **Microsoft SQL Server** motore, è necessario definire: il nome DNS (o indirizzo IP) definito nel server applicazioni per accedere al server database: **DNS** o **DNS`\<instance>`** (modalità istanza),

   >[!CAUTION]
   >
   > A partire dalla versione 20.3, l&#39;autenticazione di Windows NT viene disattivata. **[!UICONTROL SQL Server authentication]** è ora l&#39;unica modalità di autenticazione disponibile per Microsoft SQL Server. [Ulteriori informazioni](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### Passaggio 2 - Connessione al server {#step-2---connecting-to-the-server}

In **[!UICONTROL Server access]** definire l&#39;accesso al server database.

![](assets/s_ncs_install_db_oracle_creation02.png)

A questo scopo, immetti il nome e la password di un **Account del sistema di amministrazione** che dispone dell’autorizzazione per accedere alle banche dati, ossia:

* **sistema** per una banca dati di Oracle,
* **sa** per un database di Microsoft SQL Server,
* **postgres** database PostgreSQL,
* **db2inst1** per un database DB2.

### Passaggio 3: connessione e caratteristiche del database {#step-3---connection-and-characteristics-of-the-database}

Il passaggio seguente consente di configurare le impostazioni per l&#39;accesso al database.

![](assets/s_ncs_install_db_oracle_creation03.png)

È necessario definire le seguenti impostazioni:

* Specificare il nome del database da creare.

   >[!NOTE]
   >
   >Per un database DB2, il nome del database non deve superare gli 8 caratteri.

* Immettere la password dell&#39;account collegato al database.
* Indicare se il database deve trovarsi o meno in Unicode.

   Il **[!UICONTROL Unicode database]** consente di memorizzare tutti i tipi di carattere in Unicode, indipendentemente dalla lingua.

   >[!NOTE]
   >
   >Con un database di Oracli, **[!UICONTROL Unicode storage]** consente di utilizzare **NCLOB** e **NVARCHAR** digita i campi.
   > 
   >Se non si seleziona questa opzione, il set di caratteri (charset) del database Oracle deve abilitare la memorizzazione dei dati in tutte le lingue (si consiglia AL32UTF8).

* Scegliere un fuso orario per il database e specificare se si desidera che sia in formato UTC (se disponibile).

   Per ulteriori informazioni, consulta [Gestione del fuso orario](../../installation/using/time-zone-management.md).

### Passaggio 4 - Pacchetti da installare {#step-4---packages-to-install}

Selezionare i pacchetti da installare.

Consulta il contratto di licenza per verificare quali soluzioni e opzioni hai il diritto di installare, ad esempio &quot;Interazione&quot; o &quot;Social Marketing&quot;.

![](assets/s_ncs_install_modules.png)

### Passaggio 5: passaggi di creazione {#step-5---creation-steps}

Il **[!UICONTROL Creation steps]** consente di visualizzare e modificare lo script SQL utilizzato per creare le tabelle.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Ad Oracle, un database Microsoft SQL Server o PostgreSQL, l&#39;amministratore può anche definire **parametri di archiviazione** da utilizzare per la creazione di oggetti di database.

   Questi parametri ricevono i nomi esatti delle tablespace (avvertenza: distinzione maiuscole/minuscole). Vengono rispettivamente archiviati in **[!UICONTROL Administration > Platform > Options]** nelle seguenti opzioni (vedere [questa sezione](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**: tabelle utente basate su uno schema
   * **WdbcOptions_TableSpaceIndex**: indice delle tabelle utente basato su uno schema
   * **WdbcOptions_TableSpaceWork**: tabelle di lavoro senza schema
   * **WdbcOptions_TableSpaceWorkIndex**: indice delle tabelle di lavoro senza schema

* Per un database di Oracle, l’utente Adobe Campaign deve avere accesso alle librerie di Oracli, in genere come membro del **oinstall** gruppo.
* Il **[!UICONTROL Set or change the administrator password]** consente di immettere la password collegata all’operatore Adobe Campaign con diritti di amministratore.

   Per motivi di sicurezza, è consigliabile definire una password di amministratore dell’account Adobe Campaign.

### Passaggio 6: creazione del database {#step-6---creating-the-database}

La fase finale della procedura guidata consente di creare il database. Fai clic su **[!UICONTROL Start]** per confermare.

![](assets/s_ncs_install_db_oracle_creation06.png)

Una volta creato il database, è possibile riconnettersi per finalizzare la configurazione dell’istanza.

Per completare la configurazione dell’istanza, è ora necessario avviare la procedura guidata di distribuzione. Fai riferimento a [Distribuzione guidata](../../installation/using/deploying-an-instance.md#deployment-wizard).

Le impostazioni di connessione per il database collegato all&#39;istanza vengono memorizzate nel file **`/conf/config-<instance>.xml`** si trova nella directory di installazione di Adobe Campaign.

Esempio di configurazione di Microsoft SQL Server nel database base61 collegato all&#39;account &#39;campaign&#39; con la relativa password crittografata:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## Caso 2: utilizzo di un database esistente {#case-2--using-an-existing-database}

Il database e l&#39;utente devono essere stati creati dall&#39;amministratore del database e i diritti di accesso devono essere configurati correttamente.

Ad Oracle, per un database i diritti minimi richiesti sono: GRANT CONNECT, RESOURCE e UNLIMITED TABLESPACE.

Per utilizzare un database esistente, effettuare le seguenti operazioni di configurazione:

* [Passaggio 1: scelta del motore di database](#step-1---choosing-the-database-engine),
* [Passaggio 2: impostazioni della connessione al database](#step-2---database-connection-settings),
* [Passaggio 3 - Pacchetti da installare](#step-3---packages-to-install),
* [Passaggio 4 - Passaggi di creazione](#step-4---creation-steps),
* [Passaggio 5: creazione del database](#step-5---creating-the-database).

### Passaggio 1: scelta del motore di database {#step-1---choosing-the-database-engine}

Scegliere il motore di database dall&#39;elenco a discesa.

![](assets/s_ncs_install_db_select_engine.png)

Identificare il server e scegliere il tipo di operazione che si desidera eseguire. In questo caso, **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

A seconda del motore di database selezionato, le informazioni di identificazione del server possono variare.

* Per un **Oracle** motore, compila il **Nome TNS** definito per il server applicazioni.
* Per un **PostgreSQL** o **DB2** per accedere al server di database, è necessario specificare il nome DNS (o l&#39;indirizzo IP) definito nel server applicazioni.
* Per un **Microsoft SQL Server** motore, è necessario definire:

   1. il nome DNS (o indirizzo IP) definito nel server applicazioni per accedere al server database,
   1. metodo di protezione utilizzato per accedere a Microsoft SQL Server: **[!UICONTROL SQL Server authentication]** o **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### Passaggio 2: impostazioni della connessione al database {#step-2---database-connection-settings}

In **[!UICONTROL Database]** definire le impostazioni di connessione al database.

![](assets/s_ncs_install_db_oracle_exists_02.png)

È necessario definire le seguenti impostazioni:

* Immettere il nome del database da utilizzare.
* Immettere il nome e la password dell&#39;account associato al database.

   >[!NOTE]
   >
   >Assicurati che il nome dello schema e il nome utente corrispondano. La modalità consigliata per la creazione del database è tramite il client della console di Campaign.
   >Per un database di Oracle, non è necessario immettere il nome dell&#39;account.

* Indicare se il database deve essere Unicode o meno.

### Passaggio 3 - Pacchetti da installare {#step-3---packages-to-install}

Selezionare i pacchetti da installare.

Consulta il contratto di licenza per verificare quali soluzioni e opzioni sei autorizzato a installare, ad esempio &quot;Interazione&quot; o &quot;Lead&quot;.

![](assets/s_ncs_install_modules.png)

### Passaggio 4 - Passaggi di creazione {#step-4---creation-steps}

Il **[!UICONTROL Creation steps]** consente di visualizzare e modificare lo script SQL utilizzato per creare le tabelle.

![](assets/s_ncs_install_db_oracle_creation04.png)

* Ad Oracle, i database Microsoft SQL Server o PostgreSQL, l&#39;amministratore può definire **parametri di archiviazione** da utilizzare per la creazione di oggetti di database.
* Per un database di Oracle, l’utente Adobe Campaign deve avere accesso alle librerie di Oracli, in genere come membro del **oinstall** gruppo.
* Il **[!UICONTROL Set or change the administrator password]** consente di immettere la password collegata all’operatore Adobe Campaign con diritti di amministratore.

   Per motivi di sicurezza, è consigliabile definire una password di amministratore dell’account Adobe Campaign.

### Passaggio 5: creazione del database {#step-5---creating-the-database}

La fase finale della procedura guidata consente di creare il database. Fai clic su **[!UICONTROL Start]** per confermare.

![](assets/s_ncs_install_db_oracle_creation06.png)

Una volta completata la creazione del database, puoi riconnetterti per finalizzare la configurazione dell’istanza.

Per completare la configurazione dell’istanza, è ora necessario avviare la procedura guidata di distribuzione. Fai riferimento a [Distribuzione guidata](../../installation/using/deploying-an-instance.md#deployment-wizard).

Le impostazioni di connessione per il database collegato all&#39;istanza vengono memorizzate nel file **`/conf/config-<instance>.xml`** si trova nella directory di installazione di Adobe Campaign.

Esempio di configurazione di Microsoft SQL Server nel database base61 collegato all&#39;account &#39;campaign&#39; con la relativa password crittografata:

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
