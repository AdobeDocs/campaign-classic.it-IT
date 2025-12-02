---
product: campaign
title: Struttura di uno schema di dati
description: Struttura di uno schema di dati
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# Struttura di uno schema di dati{#structure-of-a-data-schema}

La struttura di uno schema di dati viene visualizzata sotto forma di struttura ad albero. Per visualizzarlo graficamente nella console client di Adobe Campaign, seleziona lo schema di destinazione e fai clic sulla scheda secondaria **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Come standard, i campi vengono visualizzati per primi (Attivo, Attivato, ecc.) e in ordine alfabetico. Gli elementi strutturanti sono i seguenti (Indirizzo postale, Posizione) e infine i collegamenti (Informazioni e-mail, Cartella, ecc.).

Le chiavi primarie sono identificate da una chiave rossa e le chiavi esterne da una chiave gialla.

I collegamenti sono distinti graficamente a seconda che appartengano o meno alla tabella. Vengono visualizzati per primi quelli che iniziano dalla tabella, ovvero quelli che hanno la chiave esterna nella tabella (Informazioni e-mail, Cartella, Paese). Alla fine vengono visualizzati i collegamenti di raccolta &quot;Inverso&quot; (Abbonamento, Ordini, ecc.).
