---
product: campaign
title: Comportamento JSP
description: Comportamento JSP
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# Comportamento JSP{#jsp-behavior}

Se alcuni processi **jsp** non vengono eseguiti correttamente, è necessario forzarli a ricompilarli.

A questo scopo, immetti i seguenti comandi:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

I processi **jsp** vengono rigenerati alla successiva connessione.
