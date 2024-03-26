---
product: campaign
title: Passaggio a Unicode
description: Passaggio a Unicode
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 5%

---

# Passaggio a Unicode{#switching-to-unicode}



Per un esistente **prod** in Linux/PostgreSQL, i passaggi per passare a unicode sono i seguenti:

1. Interrompere la scrittura dei processi nel database:

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

1. Ripristina il database:

   ```
   psql mydatabase_unicode < mydatabase.sql
   ```

1. Aggiornare l&#39;opzione che indica che il database è Unicode:

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

   Aggiungi il **u** davanti al valore relativo all&#39;identificatore del database (**databaseId**):

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

1. Riavviare tutti i computer:

   ```
   /etc/init.d/apache stop
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   /etc/init.d/apache start
   ```

1. Confermare il pulsante. A questo scopo, effettua la connessione tramite la console Adobe Campaign e:

   * verifica che i dati siano visualizzati correttamente, in particolare i caratteri accentuati:
   * avvia una consegna e verifica che il recupero del tracciamento funzioni.
