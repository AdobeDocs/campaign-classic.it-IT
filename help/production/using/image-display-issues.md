---
solution: Campaign Classic
product: campaign
title: Problemi relativi alla visualizzazione delle immagini
description: Problemi relativi alla visualizzazione delle immagini
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 50f95d7156e7104d90fa7a31eea30711b9c11bbf
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 6%

---


# Problemi relativi alla visualizzazione delle immagini{#image-display-issues}

Se si verificano dei problemi di visualizzazione delle immagini in un messaggio inviato, i motivi possono essere collegati a una posizione non corretta:

* Le posizioni potrebbero non corrispondere, oppure le immagini potrebbero non essere state correttamente inviate al server di tracciamento duplicato: controllate la configurazione.
* Le immagini potrebbero non risiedere nella cartella delle risorse pubbliche nell&#39;istanza di marketing: caricate le immagini nella cartella delle risorse per risolvere il problema.
* Se lavori in un&#39;architettura mid-sourcing: quando vengono inviate prove di stampa, le immagini controllate vengono caricate senza errori (le informazioni vengono visualizzate nei registri di analisi).

Come risolvere i problemi:

1. Inviate una prova che mostrerà le immagini.
1. Convalida la configurazione delle risorse nell&#39;impostazione dell&#39;istanza corretta.
1. Controllate la cartella delle risorse pubbliche o, se non si trova nella cartella delle risorse pubbliche, la cartella a cui viene fatto riferimento nella consegna.
