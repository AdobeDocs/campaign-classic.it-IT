---
product: campaign
title: Immagini mancanti
description: Immagini mancanti
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
TQID: https://experienceleague.adobe.com/GDlcjvzSGP70FlVGHmnhJHsqC3SFG5Y-kQOohR00j8c
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 111
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
