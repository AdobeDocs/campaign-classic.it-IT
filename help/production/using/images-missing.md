---
product: campaign
title: Immagini mancanti
description: Immagini mancanti
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 6ccda57d-f7a3-4501-b2f4-59fcb05f9013
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 5%

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
