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
source-git-commit: 757e3a5395f24e0bdd04737aba0458881e4ea780
workflow-type: tm+mt
source-wordcount: '47'
ht-degree: 14%

---

# Comportamento JSP{#jsp-behavior}



Se alcuni processi di **jsp** non vengono eseguiti correttamente, è necessario forzarne la ricompilazione.

A questo scopo, immetti i seguenti comandi:

```
nlserver stop web
cd nl6/tomcat-X
rm -r work/
nlserver start web
```

I processi **jsp** vengono rigenerati alla successiva connessione.
