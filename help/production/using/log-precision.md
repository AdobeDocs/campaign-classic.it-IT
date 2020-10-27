---
title: Precisione dei log
seo-title: Precisione dei log
description: Precisione dei log
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 2%

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

1. La modalità **TraceFilter** , che consente di salvare il maggior numero di registri. È attivata dal seguente comando:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Se utilizzate **tracefilter:***, tutti i tipi di registro sono attivati: ncm, rdr, nms, jst, temporizzazione, wdbc, ldap, soap, xtk, xtkquery, sessione, xtkwriter, rete, pop3, inmail\
   I tipi di registro più utili sono: **wdbc** (visualizza tutte le query SQL), **soap** (visualizza tutte le chiamate SOAP), **ldap** (visualizza tutte le query LDAP dopo l&#39;autenticazione), **xtkquery** (visualizza l&#39;elenco di tutte le query).\
   Potete usarli singolarmente (ad esempio,**tracefilter:soap,wdbc** ). Potete anche attivarli tutti e escludere alcuni altri: **-tracefilter:*,!soap**

   Verificate che l&#39;errore si sia verificato, quindi riavviate il processo nel modo normale:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
I registri di questi comandi sono memorizzati nel file di registro del modulo.

Di seguito è riportato un esempio specifico per il modulo Web. Gli altri moduli funzionano come indicato sopra.

Prima di inviare questo comando, verificate che non venga interessato alcun processo in corso.

```
nlserver pdump -who
```

Quindi, arrestare e riavviare il modulo in modalità **TraceFilter** .

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Un altro esempio:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
La modalità **Tracefile** consente di salvare i file di registro. Negli esempi riportati sopra, i file di registro vengono salvati nei file **var/`<instance-name>`/mta_debug.log** e **var/default/web_debug.log** .

>[!IMPORTANT]
In Windows, non aggiungere l&#39;opzione LD_PRELOAD. Il seguente comando è sufficiente:\
nlserver web -tomcat -verbose -tracefilter:*

Verificare che il problema si verifichi di nuovo, quindi riavviare il modulo:

```
nlserver restart web -tomcat -noconsole
```

Tutte le informazioni sono disponibili nel file **/usr/local/neolane/nl6/var/default/log/web.log**.
