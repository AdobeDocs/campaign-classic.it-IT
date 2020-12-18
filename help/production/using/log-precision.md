---
solution: Campaign Classic
product: campaign
title: Precisione dei log
description: Precisione dei log
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---


# Precisione dei log{#log-precision}

È possibile applicare questo processo a tutti  moduli Adobe Campaign per aumentare la precisione del registro.

Si tratta di riavviare i processi con un livello più elevato di registri.

>[!IMPORTANT]
>
>Questa procedura annulla i servizi in corso su questo modulo.

 Adobe Campaign può funzionare con due livelli di registro:

1. La modalità **Verbose** è il primo livello dopo il livello standard. Il seguente comando lo attiva:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Verificate che l&#39;errore si sia verificato, quindi riavviate il processo nel modo normale:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. La modalità **TraceFilter**, che consente di salvare il maggior numero di registri. È attivata dal seguente comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Se si utilizza **tracefilter:***, tutti i tipi di registro sono attivati: ncm, rdr, nms, jst, temporizzazione, wdbc, ldap, soap, xtk, xtkquery, sessione, xtkwriter, rete, pop3, inmail\
   I tipi di registro più utili sono: **wdbc** (visualizza tutte le query SQL), **soap** (visualizza tutte le chiamate SOAP), **ldap** (visualizza tutte le query LDAP dopo l&#39;autenticazione), **xtkquery** (visualizza l&#39;elenco di tutte le query).\
   È possibile utilizzarli singolarmente (**tracefilter:soap,wdbc** ad esempio). Potete anche attivarli tutti e escludere alcuni altri: **-tracefilter:*,!soap**

   Verificate che l&#39;errore si sia verificato, quindi riavviate il processo nel modo normale:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
I registri di questi comandi sono memorizzati nel file di registro del modulo.

Di seguito è riportato un esempio specifico del modulo Web. Gli altri moduli funzionano come indicato sopra.

Prima di inviare questo comando, verificate che non venga interessato alcun processo in corso.

```
nlserver pdump -who
```

Quindi, arrestare e riavviare il modulo in modalità **TraceFilter**.

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Un altro esempio:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
La modalità **Tracefile** consente di salvare i file di registro. Negli esempi riportati sopra, i file di registro vengono salvati nei file **var/`<instance-name>`/mta_debug.log** e **var/default/web_debug.log**.

>[!IMPORTANT]
In Windows, non aggiungere l&#39;opzione LD_PRELOAD. Il seguente comando è sufficiente:\
nlserver web -tomcat -verbose -tracefilter:*

Verificare che il problema si verifichi di nuovo, quindi riavviare il modulo:

```
nlserver restart web -tomcat -noconsole
```

Tutte le informazioni sono disponibili nel file **/usr/local/neolane/nl6/var/default/log/web.log**.
