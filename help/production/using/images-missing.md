---
product: campaign
title: Immagini mancanti
description: Immagini mancanti
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 5%

---

# Immagini mancanti{#images-missing}



Nella versione 17.9, sono stati spostati diversi file (in particolare icone).

Per i clienti in hosting, non vi è alcun impatto. Per le installazioni on-premise, leggere quanto segue.

**Utenti Apache:**

Non ha alcun impatto per gli utenti Apache che utilizzano l&#39;**apache_neolane.conf** fornito.

**Utenti IIS:**

Per gli utenti IIS (su Windows), dopo l’aggiornamento della build nella console mancheranno diverse icone. Sono necessari ulteriori passaggi per l’aggiornamento di IIS:

1. Dopo l&#39;aggiornamento della build, fare doppio clic su **iis_neolane_setup.vbs** che si trova nella directory di installazione di Campaign. Il percorso predefinito è C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Riavvia il sito IIS che è stato aggiornato dal passaggio precedente.
