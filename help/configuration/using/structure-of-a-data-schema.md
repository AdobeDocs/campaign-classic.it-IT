---
solution: Campaign Classic
product: campaign
title: Struttura di uno schema di dati
description: Struttura di uno schema di dati
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 10%

---


# Struttura di uno schema di dati{#structure-of-a-data-schema}

La struttura di uno schema dati è visualizzata sotto forma di struttura ad albero. Per visualizzarlo graficamente nella console client Adobe Campaign , selezionate lo schema di destinazione e fate clic sulla **[!UICONTROL Structure]** sottoscheda.

![](assets/d_ncs_integration_schema_arbo.png)

Come standard, i campi vengono visualizzati per primi (Attivo, Attivato, ecc.) e in ordine alfabetico. Gli elementi di strutturazione vengono successivi (Indirizzo postale, Posizione) e infine i collegamenti (Informazioni e-mail, Cartella, ecc.).

Le chiavi primarie sono identificate da un tasto rosso, mentre le chiavi esterne sono identificate da un tasto giallo.

I collegamenti sono distinti graficamente a seconda che appartengano o meno alla tabella. Quelli che iniziano dalla tabella, ovvero che hanno la chiave esterna nella tabella, vengono visualizzati per primi (informazioni e-mail, Cartella, Paese). &quot;Inverti&quot; collegamenti della raccolta (Iscrizione, Ordini, ecc.) vengono visualizzati alla fine.
