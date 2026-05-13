---
product: campaign
title: Modifica di uno schema
description: Ulteriori informazioni sull’attività Modifica flusso di lavoro dello schema
feature: Workflows, Targeting Activity
hide: true
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
TQID: https://experienceleague.adobe.com/cxBDJJXifg7C4vtB5MPBYSluRpgnbsBkDiuSsnIHDYo
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 115
ht-degree: 3%

---

# Modifica di uno schema{#edit-schema}



I dati possono essere trasformati, normalizzati e, se necessario, arricchiti nel flusso di lavoro utilizzando l&#39;attività **[!UICONTROL Edit schema]**. Viene generalmente utilizzato per normalizzare la struttura dei dati: è possibile rinominare le colonne di output o modificarne il contenuto, ad esempio calcolando i valori medi di un campo o di un aggregato.

Questa attività non modifica i dati nella tabella di lavoro, ma solo il relativo schema, ovvero la vista logica dei dati.

![](assets/wf_manipulation_box.png)

È inoltre possibile creare join con altre tabelle di lavoro tramite la scheda **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

La sezione inferiore consente di configurare l’elenco delle condizioni di join, ovvero i criteri utilizzati per riconciliare i dati delle due tabelle.
