---
product: campaign
title: Problemi relativi alla visualizzazione delle immagini
description: Problemi relativi alla visualizzazione delle immagini
feature: Monitoring
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
TQID: https://experienceleague.adobe.com/aBPQb0Yp8o7goe2CS4h6ydnZV5gjPYINHMxGcc-d140
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2: id: c03a11ff-bdf9-4e5b-b279-f468b4293464id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 134
ht-degree: 6%

---

# Problemi relativi alla visualizzazione delle immagini{#image-display-issues}



Se si verificano problemi di visualizzazione delle immagini in un messaggio inviato, i motivi potrebbero essere collegati alla posizione errata:

* Le posizioni potrebbero non corrispondere oppure le immagini potrebbero non essere state inviate correttamente al server di tracciamento duplicato: controlla la configurazione.
* Le immagini potrebbero non trovarsi nella cartella delle risorse pubbliche nell’istanza di marketing: carica le immagini nella cartella delle risorse per risolvere il problema.
* Se utilizzi un’architettura di mid-sourcing: controlla che le immagini vengano caricate senza errori quando vengono inviate le bozze (le informazioni vengono visualizzate nei registri di analisi).

Come risolvere i problemi:

1. Invia una bozza che mostri le immagini.
1. Verifica che la configurazione delle risorse nella configurazione dell’istanza sia corretta.
1. Controlla la cartella delle risorse pubbliche o, se non la cartella delle risorse pubbliche, la cartella a cui si fa riferimento nella consegna.
