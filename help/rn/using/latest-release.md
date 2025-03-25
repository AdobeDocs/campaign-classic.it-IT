---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: 631188b5974eaa4cd1bf667c5df9f2ff0f983cf0
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 27%

---

# Ultima versione {#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign Classic v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.4.2 - Build 9390 {#release-7-4-2}

[!BADGE Disponibilità limitata]{type=Informative url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità limitata"}

_sabato 21 marzo 2025_

>[!AVAILABILITY]
>
>Questa versione è in **Disponibilità limitata** (LA). È limitato solo agli utenti di Hosted/Managed Services. Questa versione sarà presto disponibile per i clienti ibridi e on-premise.

<!--
### Compatibility updates {#comp-7-4-2}

This release comes with the following compatibility updates:

* JQuery library update: fixes multiple UI issues (reports, web apps)
* PostgreSQL 15 and 16

-->

### Miglioramenti di sicurezza {#security-7-4-2}

Questa versione include diverse correzioni di sicurezza.

La connessione con le soluzioni e le app Adobe tramite l&#39;account esterno **[!UICONTROL Adobe Experience Cloud]** è stata aggiornata per rafforzare la sicurezza.

### Correzioni {#release-7-4-2-fixes}

Questa versione include le seguenti correzioni principali:

* Connessione TLS/SMPP: sono stati risolti dei problemi di stabilità SMPP

* Correzioni di BigQuery Google:

   * Sono state corrette le regressioni sui tipi di dati BOOLEAN
   * Sono stati risolti dei problemi relativi alle impostazioni proxy.
   * Sono state corrette le regressioni sui tipi di dati DATETIME
   * Stabilità del carico di massa fisso
   * Sono stati migliorati i test interni sulle versioni ODBC
   * È stato risolto un problema relativo ai caratteri speciali nella stringa di connessione
   * Timeout predefinito rimosso (5 min) nelle query BigQuery Google

* Mail Transfer Agent (MTA): risolto elemento secondario MTA orfano bloccato nello stato **[!UICONTROL Start pending]**.

In questa versione sono stati risolti anche i seguenti problemi:

NEO-47269, NEO-59059, NEO-62455, NEO-65774, NEO-66462, NEO-66989, NEO-77898, NEO-78843, NEO-79373, NEO-79598, NEO-80145, NEO-80245, NEO-80434, NEO-80683, NEO-81222, NEO-81433, NEO-81864, NEO-82351, NEO-82781, NEO-82838 82923 83252 83809 83826 84024 84553 85150, NEO-, NEO-, NEO-, NEO-, NEO-, NEO-, NEO-, NEO-

