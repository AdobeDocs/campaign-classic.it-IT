---
product: campaign
title: Precisione dei registri
description: Precisione dei registri
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 4%

---

# Precisione dei registri{#log-precision}



Per aumentare la precisione del registro, puoi applicare questo processo a tutti i moduli di Adobe Campaign.

Comporta il rilancio dei processi con un livello più elevato di registri.

>[!IMPORTANT]
>
>Questa procedura annulla i servizi in corso su questo modulo.

Adobe Campaign può funzionare con due livelli di registro:

1. Il **Dettagliato** mode è il primo livello dopo il livello standard. Il comando seguente lo attiva:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Verificare che l&#39;errore si sia verificato, quindi riavviare il processo nel modo normale:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Il **TraceFilter** che consente di salvare il maggior numero di registri. Viene attivato dal comando seguente:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Se usa **tracefilter:&#42;**, vengono attivati tutti i tipi di registro: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   I tipi di registro più utili sono: **wdbc** (visualizza tutte le query SQL), **sapone** (visualizza tutte le chiamate SOAP), **ldap** (visualizza tutte le query LDAP dopo l’autenticazione), **xtkquery** (visualizza l&#39;elenco di tutti i querydef).\
   Puoi utilizzarli singolarmente (**tracefilter:soap,wdbc** ad esempio). Puoi anche attivarli tutti e scegliere di escluderne altri: **-tracefilter:&#42;,!soap**

   Verificare che l&#39;errore si sia verificato, quindi riavviare il processo nel modo normale:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
I registri di questi comandi vengono memorizzati nel file di registro del modulo.

Di seguito è riportato un esempio specifico per il modulo Web. Gli altri moduli funzionano come indicato sopra.

Prima di inviare questo comando, verificare che non vi siano problemi per i processi in corso:

```
nlserver pdump -who
```

Chiudere e riavviare il modulo in **TraceFilter** modalità:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Un altro esempio:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
Il **File di traccia** consente di salvare i registri. Negli esempi precedenti, i registri vengono salvati in **var/`<instance-name>`/mta_debug.log** e **var/default/web_debug.log** file.

>[!IMPORTANT]
>
In Windows, non aggiungere l&#39;opzione LD_PRELOAD. Il comando seguente è sufficiente:\
nlserver web -tomcat -verbose -tracefilter:&#42;

Verificare che il problema si verifichi di nuovo, quindi riavviare il modulo:

```
nlserver restart web -tomcat -noconsole
```

Tutte le informazioni sono disponibili nel file **/usr/local/neolane/nl6/var/default/log/web.log**.
