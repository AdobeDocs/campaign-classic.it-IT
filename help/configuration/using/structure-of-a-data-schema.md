---
product: campaign
title: Struttura di uno schema di dati
description: Struttura di uno schema di dati
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# Struttura di uno schema di dati{#structure-of-a-data-schema}

![](../../assets/v7-only.svg)

La struttura di uno schema dati viene visualizzata sotto forma di struttura ad albero. Per visualizzarlo graficamente nella console client di Adobe Campaign, seleziona lo schema di destinazione e fai clic sul pulsante **[!UICONTROL Structure]** sottoscheda .

![](assets/d_ncs_integration_schema_arbo.png)

Come standard, i campi vengono visualizzati per primi (Attivo, Attivato, ecc.) e in ordine alfabetico. Gli elementi strutturanti vengono avanti (Indirizzo postale, Posizione) e infine i collegamenti (Informazioni e-mail, Cartella, ecc.).

Le chiavi primarie sono identificate da un tasto rosso, mentre le chiavi esterne sono identificate da un tasto giallo.

I collegamenti vengono distinti graficamente a seconda che appartengano o meno alla tabella. Vengono visualizzati per primi quelli che iniziano dalla tabella, ovvero che contengono la chiave esterna nella tabella (Informazioni e-mail, Cartella, Paese). Collegamenti di raccolta &quot;Inverti&quot; (Abbonamento, Ordini, ecc.) sono visualizzate alla fine.
