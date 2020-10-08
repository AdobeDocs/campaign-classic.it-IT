---
title: Soglie di connessione
seo-title: Soglie di connessione
description: Soglie di connessione
seo-description: null
page-status-flag: never-activated
uuid: a4b6959a-0f5b-41a2-b4c3-d7d6613d1a18
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: f3db77db-94cc-4d75-a59b-2dddce776759
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 5%

---


# Soglie di connessione{#connection-thresholds}

Per i server sovraccarichi, la soglia di connessione potrebbe essere superata. In ogni caso, è utile scoprire il perché.

Esistono tre soglie diverse:

1. La soglia di connessione Web, configurata nel server Web. Per modificarlo, contattare l&#39;amministratore di sistema.
1. La soglia di connessione del database. Per modificarlo, contattate l&#39;amministratore del database.
1. La soglia di connessione Adobe Campaign , disponibile in due posizioni:

   * Lato Tomcat: tutte le query in arrivo sul client Adobe Campaign Tomcat .

      Questa soglia è configurata nel file **nl6/tomcat-7/conf/server.xml** . L&#39;attributo **maxThread** consente di aumentare la soglia del numero di query elaborate alla volta. Può essere modificato a 250, ad esempio.

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

