---
solution: Campaign Classic
product: campaign
title: Riciclaggio degli eventi
description: Riciclaggio degli eventi
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---


# Riciclaggio eventi{#event-recycling}

Se la consegna di un messaggio su un canale specifico ha esito negativo,  Adobe Campaign può inviare nuovamente il messaggio utilizzando un canale diverso. Ad esempio, se una consegna sul canale SMS ha esito negativo, il messaggio viene inviato utilizzando il canale e-mail.

A tal fine, è necessario configurare un flusso di lavoro che ricrea tutti gli eventi con lo stato **Errore di consegna** e assegna loro un canale diverso.

>[!CAUTION]
>
>Questo passaggio può essere eseguito solo utilizzando un flusso di lavoro ed è quindi riservato agli utenti esperti. Per maggiori informazioni, contattare  responsabile commerciale di Adobe.

