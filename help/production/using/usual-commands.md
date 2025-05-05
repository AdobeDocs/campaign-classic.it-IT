---
product: campaign
title: Comandi abituali
description: Comandi abituali
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 3%

---

# Comandi abituali{#usual-commands}



In questa sezione sono elencati i normali comandi di Adobe Campaign.

Il comando **nlserver** è il comando di input per l&#39;intera applicazione Adobe Campaign.

Sintassi del comando: **nlserver &#x200B;**`<command>`**&#x200B;**`<arguments>`**&#x200B;**

Il parametro **`<command>`** corrisponde al modulo.

>[!NOTE]
>
>* In ogni caso, è possibile aggiungere l&#39;argomento **-noconsole** per eliminare i commenti visualizzati all&#39;avvio dei moduli.
>* Al contrario, è possibile aggiungere l&#39;argomento **-verbose** per visualizzare ulteriori informazioni.
>

## Comandi di monitoraggio {#monitoring-commands-}

>[!NOTE]
>
>Per elencare tutti i moduli, è necessario utilizzare il comando **nlserver pdump**.

È possibile aggiungere il parametro **-who** per elencare le connessioni in corso (database e applicazione).

```sql
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

Un altro comando utile è **nlserver monitor**. Elenca il file XML di monitoraggio (ottenuto nel client Adobe Campaign o tramite la pagina Web **monitor.jsp**).

È possibile aggiungere il parametro **-missing** per elencare i moduli assenti (errore nei moduli, moduli chiusi, ecc.)

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Corrisponde ai moduli con avvio automatico che non sono stati avviati.

## Comandi di avvio del modulo {#module-launch-commands}

La sintassi per i moduli di avvio avrà ancora il seguente formato:

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corrisponde al nome dell&#39;istanza immesso nei file di configurazione o **default** per i moduli a istanza mono.

## Arresta servizi {#shut-down-services}

Per arrestare i servizi di Adobe Campaign, utilizzare uno dei seguenti comandi:

* Se si dispone dell&#39;accesso root o amministratore:

   * In Linux:

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >A partire dalla versione 20.1, è consigliabile utilizzare il comando seguente (per Linux): **systemctl stop nlserver**

   * In Windows:

     ```sql
     net stop nlserver6
     ```

* In caso contrario, nell’account Adobe Campaign:

  ```sql
  nlserver shutdown 
  ```

## Riavvia servizi {#restart-services}

Allo stesso modo, per riavviare Adobe Campaign è possibile utilizzare uno dei seguenti comandi:

* Se si dispone dell&#39;accesso root o amministratore:

   * In Linux: `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >A partire dalla versione 20.1, è consigliabile utilizzare il comando seguente (per Linux): **systemctl start nlserver**

   * In Windows: `net start nlserver6`

* In caso contrario, nell&#39;account Adobe Campaign: **nlserver watchdog -svc -noconsole**

## Il comando config {#the-config-command}

Il comando **config** consente di gestire la configurazione del server, inclusa la riconfigurazione della connessione al database.

Utilizza il comando **config** del file eseguibile **nlserver** con il parametro **-setdblogin**.

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Immettere la password.

Per modificare la password **internal**: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Per accedere con l&#39;identificatore **Internal**, è necessario aver già definito una password. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* In generale, invece di modificare manualmente i file di configurazione, è possibile utilizzare il comando **config**
>* Per ottenere l&#39;elenco dei parametri, utilizzare **-?Parametro**: **nlserver config -?**
>* Nel caso di un database Oracle, non è necessario specificare l’account. La sintassi sarà la seguente:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

Di seguito è riportato un esempio per MSSQL:

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* Il login (ad esempio account:utente) e il server si trovano nel nodo dataSource del file config-&lt;nome_istanza>.xml.
* La password deve essere racchiusa tra virgolette.

