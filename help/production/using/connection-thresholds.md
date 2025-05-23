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
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 4%

---

# Soglie di connessione{#connection-thresholds}



Per i server con carichi elevati, la soglia di connessione potrebbe essere superata. In ogni caso, è utile scoprirne il motivo.

Sono disponibili tre diverse soglie:

* La **soglia di connessione Web**, configurata nel server Web. Per modificarlo, contatta l’amministratore di sistema.

* Soglia di connessione al database **&#x200B;**. Per modificarlo, contattare l&#39;amministratore del database.

* La **soglia di connessione Adobe Campaign**, disponibile in due posizioni:

   * Lato **Tomcat**: tutte le query in arrivo sul client Adobe Campaign Tomcat.

     Questa soglia è configurata nel file **nl6/tomcat-X/conf/server.xml**. L&#39;attributo **maxThreads** consente di aumentare la soglia del numero di query elaborate alla volta. Ad esempio, può essere modificato in 250.

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

     Questa soglia è configurata nel file **nl6/conf/serverConf.xml**. L&#39;attributo **maxCnx** che si trova nel **pool di origini dati** consente di aumentare la soglia delle query elaborate contemporaneamente.

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
