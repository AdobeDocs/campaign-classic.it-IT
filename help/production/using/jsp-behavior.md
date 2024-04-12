---
product: campaign
title: Comportamento JSP
description: Comportamento JSP
feature: Monitoring
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 14%

---

# Comportamento JSP{#jsp-behavior}



Se certi **jsp** i processi non vengono eseguiti correttamente, è necessario forzarne la ricompilazione.

A questo scopo, immetti i seguenti comandi:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

Il **jsp** i processi vengono rigenerati alla successiva connessione.
