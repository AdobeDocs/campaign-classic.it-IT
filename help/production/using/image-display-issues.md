---
product: campaign
title: Problemi relativi alla visualizzazione delle immagini
description: Problemi relativi alla visualizzazione delle immagini
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 62fa491e-3e83-422b-bcde-2bae2c1b676e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---

# Problemi relativi alla visualizzazione delle immagini{#image-display-issues}

![](../../assets/v7-only.svg)

Se riscontri problemi di visualizzazione delle immagini in un messaggio inviato, i motivi potrebbero essere collegati a una posizione errata:

* Le posizioni potrebbero non corrispondere o le immagini potrebbero non essere state inviate correttamente al server di tracciamento duplicato: controlla la configurazione.
* Le immagini potrebbero non trovarsi nella cartella delle risorse pubbliche nell’istanza di marketing: carica le immagini nella cartella delle risorse per risolvere il problema.
* Se lavori in un’architettura di mid-sourcing: verifica che le immagini vengano caricate senza errori quando vengono inviate le bozze (le informazioni vengono visualizzate nei registri di analisi).

Come risolvere i problemi:

1. Invia una prova che mostri le immagini.
1. Convalida la configurazione delle risorse nella configurazione dell’istanza corretta.
1. Controlla la cartella delle risorse pubbliche o, se non si trova nella cartella delle risorse pubbliche, la cartella a cui si fa riferimento nella consegna.
