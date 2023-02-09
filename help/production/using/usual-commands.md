---
product: campaign
title: Comandi abituali
description: Comandi abituali
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 3%

---

# Comandi abituali{#usual-commands}

![](../../assets/v7-only.svg)

In questa sezione sono elencati i comandi consueti in Adobe Campaign.

Comando **nlserver** è il comando di input per l’intera applicazione Adobe Campaign.

Questo comando ha la seguente sintassi: **nlserver **`<command>`****`<arguments>`****

Il parametro **`<command>`** corrisponde al modulo .

>[!NOTE]
>
>* In ogni caso, puoi aggiungere la **-noconsole** argomento per eliminare i commenti visualizzati dopo l’avvio dei moduli.
>* Al contrario, puoi aggiungere l’argomento **-verboso** per visualizzare ulteriori informazioni.
>


## Comandi di monitoraggio {#monitoring-commands-}

>[!NOTE]
>
>Per elencare tutti i moduli, è necessario utilizzare il **pdump nlserver** comando.

Puoi aggiungere il parametro **-chi** per elencare le connessioni in corso (database e applicazione).

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

Un altro comando utile è **monitor nlserver**. Elenca il file XML di monitoraggio (ottenuto nel client Adobe Campaign o tramite il **monitor.jsp** pagina web).

Puoi aggiungere il parametro **-mancante** per elencare i moduli assenti (errore nei moduli, moduli chiusi, ecc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Questo corrisponde ai moduli con avvio automatico ma che non sono stati avviati.

## Comandi di avvio del modulo {#module-launch-commands}

La sintassi per i moduli di avvio avrà ancora il seguente formato:

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** corrisponde al nome dell’istanza immesso nei file di configurazione, oppure **default** per i moduli mono-instance.

## Servizi di arresto {#shut-down-services}

Per interrompere i servizi Adobe Campaign, utilizza uno dei seguenti comandi:

* Se disponi di accesso root o amministratore:

   * In Linux:

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >A partire da 20.1, si consiglia di utilizzare invece il seguente comando (per Linux): **system stop nlserver**

   * In Windows:

      ```
      net stop nlserver6
      ```

* In caso contrario, nell’account Adobe Campaign:

   ```
   nlserver shutdown 
   ```

## Riavvia i servizi {#restart-services}

Allo stesso modo, per riavviare Adobe Campaign è possibile utilizzare uno dei seguenti comandi:

* Se disponi di accesso root o amministratore:

   * In Linux: /etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >A partire da 20.1, si consiglia di utilizzare invece il seguente comando (per Linux): **system start nlserver**

   * In Windows: net start nlserver6

* In caso contrario, nell’account Adobe Campaign: **nlserver watchdog -svc -noconsole**

## Comando di configurazione {#the-config-command}

La **config** consente di gestire la configurazione del server, inclusa la riconfigurazione della connessione al database.

Utilizza la **config** comando **nlserver** file eseguibile con **-setdblogin** parametro .

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Immetti la password.

Per modificare la variabile **interno** password: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Per accedere con **Interno** identificatore, devi aver definito una password in precedenza. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* In generale, invece di modificare i file di configurazione a mano, puoi utilizzare il **config** command
>* Per ottenere l’elenco dei parametri, utilizza il **-?** parametro: **configurazione nlserver -?**
>* Nel caso di un database di Oracle, non è necessario specificare l&#39;account. La sintassi sarà la seguente:
>
>  nlserver config -setdblogin:Oracle:test6@dbserver
