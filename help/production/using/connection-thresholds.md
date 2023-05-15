---
product: campaign
title: Soglie di connessione
description: Soglie di connessione
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 3%

---

# Soglie di connessione{#connection-thresholds}



Per i server con carichi elevati, la soglia di connessione potrebbe essere superata. In ogni caso, è utile scoprire il perché.

Esistono tre soglie diverse:

* La **Soglia connessione web**, configurato nel server web. Per modificarlo, contattare l&#39;amministratore di sistema.

* La **soglia di connessione al database**. Per modificarlo, contattare l&#39;amministratore del database.

* La **Soglia di connessione Adobe Campaign**, disponibile in due posizioni:

   * **Tomcat** lato: tutte le query in arrivo sul client Adobe Campaign Tomcat.

      Questa soglia è configurata nella **nl6/tomcat-8/conf/server.xml** file. La **maxThreads** attributo ti consente di aumentare la soglia del numero di query elaborate alla volta. Può essere cambiato a 250, per esempio.

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

   * **Database**: insieme di tutte le connessioni aperte contemporaneamente nel database da un processo.

      Questa soglia è configurata nel file **nl6/conf/serverConf.xml**. La **maxCnx** attributo situato in **pool di dati** consente di aumentare la soglia delle query elaborate simultaneamente.

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
