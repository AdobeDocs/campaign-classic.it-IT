---
title: Comandi comuni
seo-title: Comandi comuni
description: Comandi comuni
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# Comandi comuni{#usual-commands}

In questa sezione sono elencati i consueti comandi di Adobe Campaign.

Il **server** di comando è il comando di input per l&#39;intera applicazione Adobe Campaign.

Questo comando ha la sintassi seguente: **nlserver **`<command>`****`<arguments>`****

Il parametro **`<command>`** corrisponde al modulo.

>[!NOTE]
>
>* In ogni caso, è possibile aggiungere l&#39;argomento **-noconsole** per eliminare i commenti visualizzati dopo l&#39;avvio dei moduli.
>* Al contrario, potete aggiungere l&#39;argomento **-verbose** per visualizzare ulteriori informazioni.
>



## Monitoraggio, comandi {#monitoring-commands-}

>[!NOTE]
>
>Per elencare tutti i moduli, è necessario utilizzare il comando **nlserver pdump** .

Potete aggiungere il parametro **-who** per elencare le connessioni in corso (database e applicazione).

```
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

Un altro comando utile è **nlserver monitor**. Elenca il file XML di monitoraggio (ottenuto nel client Adobe Campaign o tramite la pagina Web **monitor.jsp** ).

È possibile aggiungere il parametro **-mancante** per elencare i moduli assenti (errore in moduli, moduli chiusi, ecc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Questo corrisponde ai moduli con avvio automatico ma che non sono stati avviati.

## Comandi di avvio del modulo {#module-launch-commands}

La sintassi per l&#39;avvio dei moduli sarà ancora nel seguente formato:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corrisponde al nome dell&#39;istanza come immesso nei file di configurazione, o **predefinito** per i moduli di istanza mono.

## Arrestare i servizi {#shut-down-services}

Per arrestare i servizi di Adobe Campaign, usa uno dei comandi seguenti:

* Se disponete dell&#39;accesso principale o amministratore:

   * In Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >A partire da 20.1, si consiglia di utilizzare il seguente comando (per Linux): server di arresto **del sistema**

   * In Windows:

      ```
      net stop nlserver6
      ```

* In caso contrario, nell&#39;account Adobe Campaign:

   ```
   nlserver shutdown 
   ```

## Riavvia servizi {#restart-services}

Allo stesso modo, per riavviare Adobe Campaign puoi usare uno dei seguenti comandi:

* Se disponete dell&#39;accesso principale o amministratore:

   * In Linux:/etc/init.d di avvio/nlserver6

      >[!NOTE]
      >
      >A partire da 20.1, si consiglia di utilizzare il seguente comando (per Linux): server di avvio **del sistema**

   * In Windows:net start nlserver6

* Altrimenti, nell&#39;account Adobe Campaign: watchdog **nlserver -svc -noconsole**

## Comando config {#the-config-command}

Il comando **config** consente di gestire la configurazione del server, inclusa la riconfigurazione della connessione al database.

Utilizzate il comando **config** del file eseguibile **nlserver** con il parametro **-setdblogin** .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Immettere la password.

Per modificare la password **interna** : config **nlserver -internalpassword**

>[!CAUTION]
>
>Per accedere con l&#39;identificatore **interno** , è necessario che sia stata definita una password in anticipo. For more on this, refer to [this section](../../installation/using/campaign-server-configuration.md#internal-identifier).

>[!NOTE]
>
>* In generale, invece di modificare i file di configurazione a mano, è possibile utilizzare il comando **config**
>* Per ottenere l&#39;elenco dei parametri, utilizzare il **-?** parameter: config **nlserver -?**
>* Nel caso di un database Oracle, non è necessario specificare l&#39;account. La sintassi sarà la seguente:
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


