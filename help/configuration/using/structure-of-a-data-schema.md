---
product: campaign
title: Struttura di uno schema di dati
description: Struttura di uno schema di dati
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---

# Struttura di uno schema di dati{#structure-of-a-data-schema}

La struttura di uno schema di dati viene visualizzata sotto forma di struttura ad albero. Per visualizzarlo graficamente nella console client di Adobe Campaign, seleziona lo schema di destinazione e fai clic su **[!UICONTROL Structure]** scheda secondaria.

![](assets/d_ncs_integration_schema_arbo.png)

Come standard, i campi vengono visualizzati per primi (Attivo, Attivato, ecc.) e in ordine alfabetico. Gli elementi strutturanti sono i seguenti (Indirizzo postale, Posizione) e infine i collegamenti (Informazioni e-mail, Cartella, ecc.).

Le chiavi primarie sono identificate da una chiave rossa e le chiavi esterne da una chiave gialla.

I collegamenti sono distinti graficamente a seconda che appartengano o meno alla tabella. Vengono visualizzati per primi quelli che iniziano dalla tabella, ovvero quelli che hanno la chiave esterna nella tabella (Informazioni e-mail, Cartella, Paese). Collegamenti di raccolta &quot;Inverti&quot; (abbonamento, ordini, ecc.) vengono visualizzati alla fine.
