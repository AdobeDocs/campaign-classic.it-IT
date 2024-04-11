---
product: campaign
title: Comandi abituali
description: Comandi abituali
feature: Monitoring
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 3%

---

# Comandi abituali{#usual-commands}



In questa sezione sono elencati i normali comandi di Adobe Campaign.

Il comando **nlserver** è il comando di input per l’intera applicazione Adobe Campaign.

Questo comando ha la seguente sintassi: **nlserver **`<command>`****`<arguments>`****

Il parametro **`<command>`** corrisponde al modulo.

>[!NOTE]
>
>* In ogni caso, puoi aggiungere **-noconsole** per eliminare i commenti visualizzati all&#39;avvio dei moduli.
>* Al contrario, è possibile aggiungere l’argomento **-verboso** per visualizzare ulteriori informazioni.
>

## Comandi di monitoraggio {#monitoring-commands-}

>[!NOTE]
>
>Per elencare tutti i moduli, è necessario utilizzare **nlserver pdump** comando.

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

Un altro comando utile è **monitor nlserver**. Elenca il file XML di monitoraggio (ottenuto nel client Adobe Campaign o tramite **monitor.jsp** pagina web).

Puoi aggiungere il parametro **-mancante** per elencare i moduli assenti (errore nei moduli, moduli chiusi, ecc.)

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

Corrisponde ai moduli con avvio automatico che non sono stati avviati.

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
>**`<instance>`** corrisponde al nome dell’istanza immesso nei file di configurazione, oppure **predefinito** per moduli a mono istanza.

## Arresta servizi {#shut-down-services}

Per arrestare i servizi di Adobe Campaign, utilizzare uno dei seguenti comandi:

* Se si dispone dell&#39;accesso root o amministratore:

   * In Linux:

     ```
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >A partire dalla versione 20.1, si consiglia invece di utilizzare il seguente comando (per Linux): **systemctl stop nlserver**

   * In Windows:

     ```
     net stop nlserver6
     ```

* In caso contrario, nell’account Adobe Campaign:

  ```
  nlserver shutdown 
  ```

## Riavvia servizi {#restart-services}

Allo stesso modo, per riavviare Adobe Campaign è possibile utilizzare uno dei seguenti comandi:

* Se si dispone dell&#39;accesso root o amministratore:

   * In Linux: /etc/init.d/nlserver6 start

     >[!NOTE]
     >
     >A partire dalla versione 20.1, si consiglia invece di utilizzare il seguente comando (per Linux): **systemctl start nlserver**

   * In Windows: net start nlserver6

* In caso contrario, nell’account Adobe Campaign: **watchdog nlserver -svc -noconsole**

## Il comando config {#the-config-command}

Il **config** consente di gestire la configurazione del server, inclusa la riconfigurazione della connessione al database.

Utilizza il **config** comando del **nlserver** file eseguibile con **-setdblogin** parametro.

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

Immettere la password.

Per modificare il **interno** password: **nlserver config -internalpassword**

>[!IMPORTANT]
>
>Per accedere con **Interno** identificatore, è necessario aver già definito una password. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

>[!NOTE]
>
>* In generale, invece di modificare manualmente i file di configurazione, è possibile utilizzare **config** comando
>* Per ottenere l’elenco dei parametri, utilizza **-?** parametro: **Configurazione nlserver -?**
>* Nel caso di un database Oracle, non è necessario specificare l&#39;account. La sintassi sarà la seguente:
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>
