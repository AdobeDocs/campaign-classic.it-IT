---
solution: Campaign Classic
product: campaign
title: Prerequisiti per la migrazione ad Adobe Campaign 7
description: Prerequisiti per la migrazione ad Adobe Campaign 7
audience: migration
content-type: reference
topic-tags: migrating-to-adobe-campaign-7
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '80'
ht-degree: 22%

---


# Prerequisiti per la migrazione ad Adobe Campaign 7{#prerequisites-for-migration-to-adobe-campaign}

Prima di eseguire qualsiasi migrazione, consultare le sezioni [Prima di avviare la migrazione](../../migration/using/before-starting-migration.md) e [Configurazione della piattaforma](../../migration/using/configuring-your-platform.md).

Durante la migrazione dalla v6.02 a  Adobe Campaign v7, alcuni file consegnati in precedenza non vengono consegnati.

Se viene visualizzato un errore client, dovete aggiornare i dashboard con il nuovo codice Adobe Campaign v7  oppure copiare manualmente i file seguenti dall’istanza v6.02 all’istanza v7:

```
v6.02 files and spaces:
/usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
/usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
v6.1 files and spaces:
/usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
/usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
```
