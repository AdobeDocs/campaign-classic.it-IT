---
product: campaign
title: Passaggio a Unicode
description: Passaggio a Unicode
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 7%

---

# Passaggio a Unicode{#switching-to-unicode}

Per un&#39;istanza esistente **prod** in Linux/PostgreSQL, i passaggi per passare a unicode sono i seguenti:

1. Interrompere i processi di scrittura nel database:

   ```
   su - neolane
   nlserver shutdown
   ```

1. Eseguire il dump del database:

   ```
   su - postgres
   pg_dump mydatabase > mydatabase.sql
   ```

1. Crea un database Unicode:

   ```
   createdb -E UNICODE mydatabase_unicode
   ```

1. Ripristina il database:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Aggiorna l&#39;opzione che indica che il database è Unicode:

   ```
   psql mydatabase_unicode
   update XtkOption set sStringValue = 'u'||sStringValue where sName='XtkDatabaseId' and sStringValue not like 'u%';
   ```

1. Sui server di tracciamento:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Aggiungi il carattere **u** davanti al valore relativo all&#39;identificatore del database (**databaseId**):

   ```
   <web>
    <redirection databaseId="u7F0000010554364C" trackingPassword="myPassword="/>
   </web>
   ```

1. Nei server che chiamano il database:

   ```
   su - neolane
   cd nl6/conf
   vi config-prod.xml
   ```

   Modificare il riferimento al database:

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

1. Confermare l&#39;interruttore. A questo scopo, connettiti tramite la console Adobe Campaign e:

   * verificare che i dati siano visualizzati correttamente, in particolare i caratteri accentuati:
   * avvia una consegna e controlla che il recupero del tracciamento funzioni.
