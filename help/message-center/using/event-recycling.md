---
title: Riciclaggio degli eventi
seo-title: Riciclaggio degli eventi
description: Riciclaggio degli eventi
seo-description: null
page-status-flag: never-activated
uuid: 55624a41-65a1-4759-8087-6e5d2c5c5b62
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: 568a9dec-5818-4666-b858-aa41fe827b92
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Riciclaggio degli eventi{#event-recycling}

Se la consegna di un messaggio su un canale specifico ha esito negativo, Adobe Campaign può inviare nuovamente il messaggio utilizzando un canale diverso. Ad esempio, se una consegna sul canale SMS ha esito negativo, il messaggio viene inviato utilizzando il canale e-mail.

A questo scopo, dovete configurare un flusso di lavoro che ricrea tutti gli eventi con lo stato di errore **** di consegna e assegna loro un canale diverso.

>[!CAUTION]
>
>Questo passaggio può essere eseguito solo utilizzando un flusso di lavoro ed è quindi riservato agli utenti esperti. Per ulteriori informazioni, contattate il responsabile commerciale di Adobe.

