---
product: campaign
title: Immagini mancanti
description: Immagini mancanti
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

---

# Immagini mancanti{#images-missing}

![](../../assets/v7-only.svg)

Nella versione 17.9 sono stati spostati diversi file (in particolare icone).

Per i clienti in hosting, non vi è alcun impatto. Per le installazioni on-premise, leggi quanto segue.

**Utenti Apache:**

Gli utenti Apache non hanno alcun impatto se utilizzano il **apache_neolane.conf**.

**Utenti IIS:**

Per gli utenti IIS (su Windows), dopo l&#39;aggiornamento della build nella console appariranno diverse icone mancanti. Sono necessari ulteriori passaggi di aggiornamento IIS:

1. Dopo l’aggiornamento della build, fai doppio clic su **iis_neolane_setup.vbs** si trova nella directory di installazione di Campaign. Il percorso predefinito è C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Riavvia il sito IIS aggiornato dal passaggio precedente.
