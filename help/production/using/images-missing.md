---
title: Immagini mancanti
seo-title: Immagini mancanti
description: Immagini mancanti
seo-description: null
page-status-flag: never-activated
uuid: 0dc73ea0-70bc-476d-bdff-2e62d6929f21
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: e001db7a-7c53-477e-a534-ce4d83d68559
translation-type: tm+mt
source-git-commit: d509dc584cd4ae17c6dda85c09fceee8c6162dba
workflow-type: tm+mt
source-wordcount: '114'
ht-degree: 7%

---


# Immagini mancanti{#images-missing}

Nella versione 17.9 sono stati spostati diversi file (in particolare icone).

Per i clienti ospitati, non vi è alcun impatto. Per le installazioni locali, leggete quanto segue.

**Utenti Apache:**

Gli utenti Apache non hanno alcun impatto se utilizzano il file **apache_neolane.conf fornito**

**Utenti IIS:**

Per gli utenti IIS (in Windows), dopo l&#39;aggiornamento della build nella console appariranno diverse icone mancanti. Sono necessari ulteriori passaggi di aggiornamento IIS:

1. Dopo l&#39;aggiornamento della build, fai doppio clic su **iis_neolane_setup.vbs** presente nella directory di installazione di Campaign. Il percorso predefinito è C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Riavviate il sito IIS aggiornato dal passaggio precedente.

