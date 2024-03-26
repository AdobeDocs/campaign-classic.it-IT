---
product: campaign
title: Immagini mancanti
description: Immagini mancanti
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 11%

---

# Immagini mancanti{#images-missing}



Nella versione 17.9, sono stati spostati diversi file (in particolare icone).

Per i clienti in hosting, non vi è alcun impatto. Per le installazioni on-premise, leggere quanto segue.

**Utenti Apache:**

Non c’è alcun impatto per gli utenti Apache se utilizzano il fornito **apache_neolane.conf**.

**Utenti IIS:**

Per gli utenti IIS (su Windows), dopo l’aggiornamento della build nella console mancheranno diverse icone. Sono necessari ulteriori passaggi per l’aggiornamento di IIS:

1. Dopo l’aggiornamento della build, fai doppio clic su **iis_neolane_setup.vbs** si trova nella directory di installazione di Campaign. Il percorso predefinito è C:\Program Files (x86)\Adobe\Adobe Campaign v7\conf
1. Riavvia il sito IIS che è stato aggiornato dal passaggio precedente.
