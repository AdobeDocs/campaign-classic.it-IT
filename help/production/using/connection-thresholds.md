---
solution: Campaign Classic
product: campaign
title: Soglie di connessione
description: Soglie di connessione
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---


# Soglie di connessione{#connection-thresholds}

Per i server sovraccarichi, la soglia di connessione potrebbe essere superata. In ogni caso, è utile scoprire il perché.

Esistono tre soglie diverse:

1. La soglia di connessione Web, configurata nel server Web. Per modificarlo, contattare l&#39;amministratore di sistema.
1. La soglia di connessione del database. Per modificarlo, contattate l&#39;amministratore del database.
1. La soglia di connessione Adobe Campaign , disponibile in due posizioni:

   * Lato Tomcat: tutte le query in arrivo sul client Adobe Campaign Tomcat .

      Questa soglia è configurata nel file **nl6/tomcat-8/conf/server.xml** . L&#39;attributo **maxThread** consente di aumentare la soglia del numero di query elaborate alla volta. Può essere modificato a 250, ad esempio.

      ```
      <Connector protocol="HTTP/1.1" port="8080"
                     maxThreads="75"
                     minSpareThreads="5"
                     enableLookups="true" redirectPort="8443"
                     acceptCount="100" connectionTimeout="20000"
                     disableUploadTimeout="true" />
          <Engine name="Tomcat-Standalone" defaultHost="localhost">
            <Host name="localhost" appBase="./"
                  unpackWARs="true" autoDeploy="true">
      ```

   * Database: insieme di tutte le connessioni aperte contemporaneamente sul database da un processo.

      Questa soglia è configurata nel file **nl6/conf/serverConf.xml**. L&#39;attributo **maxCnx** presente nel pool **di** origini dati consente di aumentare la soglia delle query elaborate simultaneamente.

      ```
          <!-- Data source
               -->
            <dataSource name="default">
              <dbcnx NChar="" bulkCopyUtility="" dbSchema="" encrypted="" login="" password="" provider="" server="" timezone="" unicodeData="" useTimestampTZ=""/>
              <sqlParams funcPrefix="">
                <postConnectSQL/>
              </sqlParams>
              <pool aliveTestDelaySec="600" freeCnx="0" maxCnx="90" maxIdleDelaySec="1200"/>
            </dataSource>
      ```

