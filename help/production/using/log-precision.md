---
product: campaign
title: Precisione dei registri
description: Precisione dei registri
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# Precisione dei registri{#log-precision}

![](../../assets/v7-only.svg)

Puoi applicare questo processo a tutti i moduli Adobe Campaign per aumentare la precisione del registro.

Si tratta di riavviare i processi con un livello di log più elevato.

>[!IMPORTANT]
>
>Questa procedura annulla i servizi in corso su questo modulo.

Adobe Campaign può funzionare con due livelli di log:

1. La **Verbose** mode è il primo livello dopo il livello standard. Il comando seguente lo attiva:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Controlla che l&#39;errore si sia effettivamente verificato, quindi riavvia il processo nel modo normale:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. La **TraceFilter** , che consente di salvare il maggior numero di registri. Viene attivato dal seguente comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Se utilizzi **tracefilter:&#42;**, vengono attivati tutti i tipi di log: ncm, rdr, nms, jst, temporizzazione, wdbc, ldap, sapone, xtk, xtkquery, sessione, xtkwriter, rete, pop3, inmail\
   >I tipi di log più utili sono: **wdbc** (visualizza tutte le query SQL), **sapone** (visualizza tutte le chiamate SOAP), **ldap** (visualizza tutte le query LDAP dopo l&#39;autenticazione), **xtkquery** (visualizza l&#39;elenco di tutte le querydef).\
   >Puoi utilizzarli singolarmente (**tracefilter:soap,wdbc** ad esempio). Puoi anche attivarli tutti e scegliere di escluderne alcuni altri: **-tracefilter:&#42;,!soap**

   Controlla che l&#39;errore si sia effettivamente verificato, quindi riavvia il processo nel modo normale:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>I registri di questi comandi sono memorizzati nel file di registro del modulo.

Ecco un esempio specifico del modulo Web. Gli altri moduli funzionano come indicato sopra.

Prima di inviare questo comando, controlla che non venga interessato alcun processo in corso:

```
nlserver pdump -who
```

Quindi, arresta e riavvia il modulo in **TraceFilter** modalità:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Un altro esempio:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>La **Tracefile** consente di salvare i registri. Negli esempi precedenti, i registri vengono salvati nel **var/`<instance-name>`/mta_debug.log** e **var/default/web_debug.log** file.

>[!IMPORTANT]
>
>In Windows, non aggiungere l&#39;opzione LD_PRELOAD. Il comando seguente è sufficiente:\
>nlserver web -tomcat -verbose -tracefilter:&#42;

Verifica che il problema si verifichi di nuovo, quindi riavvia il modulo:

```
nlserver restart web -tomcat -noconsole
```

Tutte le informazioni sono disponibili nel file **/usr/local/neolane/nl6/var/default/log/web.log**.
