---
product: campaign
title: Struttura di uno schema di dati
description: Struttura di uno schema di dati
feature: Custom Resources
role: Developer
exl-id: 86036f2f-ec7c-413e-b1e1-10a71a06cd6d
TQID: 'https://experienceleague.adobe.com/bp-x2YrBY5WzNVTXJjpzdZgG45vNPPG9-z339I9U5Lw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
subfeature_v2:
  - id: a2002dba-5e37-4dff-8e04-1cc3ec73558c
    internal-label: Custom resources
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 10%
---
# Struttura di uno schema di dati{#structure-of-a-data-schema}

La struttura di uno schema di dati viene visualizzata sotto forma di struttura ad albero. Per visualizzarlo graficamente nella console client di Adobe Campaign, seleziona lo schema di destinazione e fai clic sulla scheda secondaria **[!UICONTROL Structure]**.

![](assets/d_ncs_integration_schema_arbo.png)

Come standard, i campi vengono visualizzati per primi (Attivo, Attivato, ecc.) e in ordine alfabetico. Gli elementi strutturanti sono i seguenti (Indirizzo postale, Posizione) e infine i collegamenti (Informazioni e-mail, Cartella, ecc.).

Le chiavi primarie sono identificate da una chiave rossa e le chiavi esterne da una chiave gialla.

I collegamenti sono distinti graficamente a seconda che appartengano o meno alla tabella. Vengono visualizzati per primi quelli che iniziano dalla tabella, ovvero quelli che hanno la chiave esterna nella tabella (Informazioni e-mail, Cartella, Paese). Collegamenti di raccolta &quot;Inverti&quot; (abbonamento, ordini, ecc.) vengono visualizzati alla fine.
