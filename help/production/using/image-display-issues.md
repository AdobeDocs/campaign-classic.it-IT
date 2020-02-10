---
title: Problemi di visualizzazione delle immagini
seo-title: Problemi di visualizzazione delle immagini
description: Problemi di visualizzazione delle immagini
seo-description: null
page-status-flag: never-activated
uuid: 8fc51459-ee46-4c05-8011-f0651e6b451b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: dfccfe8c-b826-4648-9a0b-23d7e6a4808a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Problemi di visualizzazione delle immagini{#image-display-issues}

Se si verificano dei problemi di visualizzazione delle immagini in un messaggio inviato, i motivi possono essere collegati a una posizione non corretta:

* le posizioni potrebbero non corrispondere o le immagini potrebbero non essere state correttamente inviate al server di tracciamento duplicato: controllate la configurazione.
* le immagini potrebbero non risiedere nella cartella delle risorse pubbliche nell&#39;istanza di marketing: caricate le immagini nella cartella delle risorse per risolvere il problema.
* se lavorate in un&#39;architettura mid-sourcing: quando vengono inviate prove di stampa, le immagini controllate vengono caricate senza errori (le informazioni vengono visualizzate nei registri di analisi).

Come risolvere i problemi:

1. Inviate una prova che mostrerà le immagini.
1. Convalida la configurazione delle risorse nell&#39;impostazione dell&#39;istanza corretta.
1. Controllate la cartella delle risorse pubbliche oppure, se non si trova nella cartella delle risorse pubbliche, la cartella a cui viene fatto riferimento nel recapito.

