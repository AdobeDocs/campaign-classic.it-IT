---
product: campaign
title: Prerequisiti per la migrazione ad Adobe Campaign 7
description: Prerequisiti per la migrazione ad Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
exl-id: 747d8a2c-b13a-4852-a9b5-0d37b236a36f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---

# Prerequisiti per la migrazione ad Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

![](../../assets/v7-only.svg)

Prima di eseguire qualsiasi migrazione, consulta la [Prima di avviare la migrazione](../../migration/using/before-starting-migration.md) e [Configurazione della piattaforma](../../migration/using/configuring-your-platform.md) sezioni.

Durante la migrazione dalla versione v6.02 ad Adobe Campaign v7, alcuni file consegnati in precedenza non vengono consegnati.

Se viene visualizzato un errore client, è necessario aggiornare le dashboard con il nuovo codice Adobe Campaign v7 oppure copiare manualmente i seguenti file dall&#39;istanza v6.02 all&#39;istanza v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
