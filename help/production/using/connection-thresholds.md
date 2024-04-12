---
product: campaign
title: Soglie di connessione
description: Soglie di connessione
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 4ee05559-e719-4e6e-b42c-1e82df428871
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 4%

---

# Soglie di connessione{#connection-thresholds}



Per i server con carichi elevati, la soglia di connessione potrebbe essere superata. In ogni caso, è utile scoprirne il motivo.

Sono disponibili tre diverse soglie:

* Il **Soglia di connessione web**, configurato nel server web. Per modificarlo, contatta l’amministratore di sistema.

* Il **soglia di connessione al database**. Per modificarlo, contattare l&#39;amministratore del database.

* Il **Soglia di connessione Adobe Campaign**, disponibile in due posizioni:

   * **Tomcat** side: tutte le query in arrivo sul client Adobe Campaign Tomcat.

     Questa soglia è configurata in **nl6/tomcat-8/conf/server.xml** file. Il **maxThreads** attribute consente di aumentare la soglia del numero di query elaborate alla volta. Ad esempio, può essere modificato in 250.

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

   * **Database**: set di tutte le connessioni aperte contemporaneamente nel database da un processo.

     Questa soglia è configurata nel file **nl6/conf/serverConf.xml**. Il **maxCnx** attributo situato in **pool di origini dati** consente di aumentare la soglia di query elaborate simultaneamente.

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
