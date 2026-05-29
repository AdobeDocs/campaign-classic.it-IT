---
product: campaign
title: Passaggio a Unicode
description: Passaggio a Unicode
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: 4cfecf2f-cf98-42c1-b979-cdd26d5de48b
TQID: https://experienceleague.adobe.com/aJOfEU2Pkyc2ekoYnT1duzyjn7XIU--WSHFWrJXwc-0
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 149
ht-degree: 12%

---

# Passaggio a Unicode{#switching-to-unicode}



Per un&#39;istanza **prod** esistente in Linux/PostgreSQL, i passaggi per passare a unicode sono i seguenti:

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
