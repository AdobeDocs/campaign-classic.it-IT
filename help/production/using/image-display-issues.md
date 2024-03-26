---
product: campaign
title: Problemi relativi alla visualizzazione delle immagini
description: Problemi relativi alla visualizzazione delle immagini
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 11%

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
