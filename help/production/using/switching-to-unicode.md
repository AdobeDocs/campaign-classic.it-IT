---
title: Passaggio a Unicode
seo-title: Passaggio a Unicode
description: Passaggio a Unicode
seo-description: null
page-status-flag: never-activated
uuid: 5f15b285-7377-453a-aa98-ca4cf14a4c80
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
discoiquuid: 0f5399a8-860d-4a1b-86a9-9011b973346b
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 9%

---


# Passaggio a Unicode{#switching-to-unicode}

Per un&#39;istanza **prod** esistente in Linux/PostgreSQL, i passaggi per passare a unicode sono i seguenti:

1. Arrestate i processi di scrittura nel database:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Eseguire il dump del database:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Creare un database Unicode:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Ripristinare il database:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Aggiornate l&#39;opzione per indicare che il database è Unicode:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. Sui server di monitoraggio:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Aggiungete il **carattere u** davanti al valore relativo all&#39;identificatore del database (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Sui server che chiamano il database:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Modificate il riferimento al database:

   ```
   <dataSource name="default">
    <dbcnx encrypted="1" 
    login="<dbuser>:<base_unicode>" password="xxxx="
    provider="postgresql" server="yyyy"/>
   </dataSource>
   ```

1. Riavviare tutte le macchine:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confermare l&#39;interruttore. A questo scopo, collegatevi tramite la  console Adobe Campaign e:

   * verificare che i dati siano visualizzati correttamente, in particolare i caratteri accentuati:
   * avviare una consegna e verificare che il recupero del tracciamento funzioni.

