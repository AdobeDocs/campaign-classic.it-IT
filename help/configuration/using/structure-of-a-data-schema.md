---
title: Struttura di uno schema dati
seo-title: Struttura di uno schema dati
description: Struttura di uno schema dati
seo-description: null
page-status-flag: never-activated
uuid: 83e3995d-fa31-4cb5-acf2-83f17329c99c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: a1a39eaa-6d6f-42c5-a36b-bd1cb3a77dcb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Struttura di uno schema dati{#structure-of-a-data-schema}

La struttura di uno schema dati è visualizzata sotto forma di struttura ad albero. Per visualizzarlo graficamente nella console client Adobe Campaign, seleziona lo schema di destinazione e fai clic sulla **[!UICONTROL Structure]** sottoscheda.

![](assets/d_ncs_integration_schema_arbo.png)

Come standard, i campi vengono visualizzati per primi (Attivo, Attivato, ecc.) e in ordine alfabetico. Gli elementi di strutturazione vengono successivi (Indirizzo postale, Posizione) e infine i collegamenti (Informazioni e-mail, Cartella, ecc.).

Le chiavi primarie sono identificate da un tasto rosso, mentre le chiavi esterne sono identificate da un tasto giallo.

I collegamenti sono distinti graficamente a seconda che appartengano o meno alla tabella. Quelli che iniziano dalla tabella, ovvero che hanno la chiave esterna nella tabella, vengono visualizzati per primi (informazioni e-mail, Cartella, Paese). &quot;Inverti&quot; collegamenti della raccolta (Iscrizione, Ordini, ecc.) vengono visualizzati alla fine.
