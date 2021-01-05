---
solution: Campaign Classic
product: campaign
title: Immagini mancanti
description: Immagini mancanti
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---


# Immagini mancanti{#images-missing}

Nella versione 17.9 sono stati spostati diversi file (in particolare icone).

Per i clienti ospitati, non vi è alcun impatto. Per le installazioni locali, leggete quanto segue.

**Utenti Apache:**

Gli utenti Apache non hanno alcun impatto se utilizzano il **apache_neolane.conf** fornito.

**Utenti IIS:**

Per gli utenti IIS (in Windows), dopo l&#39;aggiornamento della build nella console appariranno diverse icone mancanti. Sono necessari ulteriori passaggi di aggiornamento IIS:

1. Dopo l&#39;aggiornamento della build, fai doppio clic su **iis_neolane_setup.vbs** nella directory di installazione della campagna. Il percorso predefinito è C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Riavviate il sito IIS aggiornato dal passaggio precedente.
