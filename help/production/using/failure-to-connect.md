---
solution: Campaign Classic
product: campaign
title: Errore di connessione
description: Errore di connessione
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 2%

---


# Errore di connessione{#failure-to-connect}

I motivi possono essere molteplici e dipendere da diversi contesti.

Controllare la configurazione generale delle zone di protezione.

>[!NOTE]
>
>Per ulteriori informazioni sulla configurazione delle aree di protezione, consultare [questa sezione](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Verificate le informazioni seguenti:

1. **Controlli di rete**

   * Avete accesso a Internet dal vostro computer?

      Verificate che sia possibile connettersi ai siti Web in Internet (ad esempio). Se non riuscite a connettervi, il problema è sul computer. Contattate l’amministratore di sistema.

   * È possibile connettersi al server che ospita  Adobe Campaign tramite un altro servizio?

      Connettersi al server tramite SSH o altri mezzi. Se questo non è possibile, la società ospitante ha un problema. Contattare l&#39;amministratore di sistema.

1. **Controlli sul lato** del server Web (IIS/apache/ecc.)

   * Il server Web risponde?

      Collegarsi all&#39;URL di accesso  server Adobe Campaign utilizzando un browser Web: **http(s)://`<urlserver>`**. Se non risponde, il server Web viene arrestato sul computer. Per riavviare il servizio, contattare l&#39;amministratore di sistema della società host.

   *  Adobe Campaign è stato integrato correttamente?

      Accedi a: **http(s):// `<urlserver>`/r/test** URL. Il server deve restituire il seguente tipo di messaggio

      ```
      <redir status='OK' date='YYYY/MM/DD HH:MM:SS' build='XXXX' host='<hostname>' localHost='<server>'/>
      ```

      Se non si ottiene questo risultato, verificare nella configurazione del server Web che l&#39;integrazione viene presa in considerazione.

1. **Controlli sul lato  Adobe Campaign**

   * È stato avviato il modulo Web  Adobe Campaign?

      Connettiti al seguente URL: **http(s)://`<URLSERVER>`/nl/jsp/logon.jsp**

      * Se ricevete un errore Tomcat Java:

         L&#39;integrazione JAVA viene eseguita correttamente?  Adobe Campaign richiede un JDK SOLE.

         È integrato nel file **`[path of application]`/nl6/customer.sh**

      * Se ottenete una pagina vuota:

         È stato avviato il modulo Web  Adobe Campaign? È necessario ottenere:

         ```
         nlserver pdump
         HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
         [...]
         web@default (27515) - 55.2 Mb
         [...]
         ```

      * In caso contrario, riavviarlo utilizzando il comando seguente:

         ```
         nlserver start web
         ```
>[!NOTE]
>
>Se si ottiene una risposta del tipo seguente quando si elencano i moduli Adobe Campaign : **nlserver pdump**
>HH:MM:SS > Application server per Adobe Campaign Classic (build 7.X AA.R XXX@SHA1) di DD/MM/YYYY Nessuna attività È necessario riavviare l&#39;intera applicazione Adobe Campaign . A questo scopo, utilizzate il comando seguente: **nlserver watchdog -svc -noconsole **
