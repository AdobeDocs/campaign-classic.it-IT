---
product: campaign
title: Comportamento JSP
description: Comportamento JSP
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 858d00d0-7c65-43be-8bae-f0f945f71f1a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '36'
ht-degree: 16%

---

# Comportamento JSP{#jsp-behavior}

![](../../assets/v7-only.svg)

Se **jsp** i processi non vengono eseguiti correttamente, è necessario forzarli a ricompilarli.

A questo scopo, immetti i seguenti comandi:

```
nlserver stop web
cd nl6/tomcat-8
rm -r work/
nlserver start web
```

La **jsp** i processi verranno rigenerati al successivo collegamento.
