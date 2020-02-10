---
title: Prerequisiti per la migrazione ad Adobe Campaign 7
seo-title: Prerequisiti per la migrazione ad Adobe Campaign 7
description: Prerequisiti per la migrazione ad Adobe Campaign 7
seo-description: null
page-status-flag: never-activated
uuid: 9f4e4cdf-5338-4597-9d9d-5a3bd13033c7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
discoiquuid: a3bbd8cc-97c6-4b08-adbf-76ab77b97262
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: f460c79a763c6a207656c54351a4c685f2a78a03

---


# Prerequisiti per la migrazione ad Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Prima di eseguire qualsiasi migrazione, consulta le sezioni [Prima di avviare la migrazione](../../migration/using/before-starting-migration.md) e [Configurazione della piattaforma](../../migration/using/configuring-your-platform.md) .

Durante la migrazione dalla v6.02 ad Adobe Campaign v7, alcuni file consegnati in precedenza non vengono consegnati.

Se viene visualizzato un errore client, è necessario aggiornare i dashboard con il nuovo codice Adobe Campaign v7 oppure copiare manualmente i file seguenti dall&#39;istanza v6.02 all&#39;istanza v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
