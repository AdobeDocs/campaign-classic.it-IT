---
product: campaign
title: Modifica di uno schema
description: Ulteriori informazioni sull’attività del flusso di lavoro Modifica schema
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: d26966a8-b5db-4fa4-85ec-7ebd770c4ef3
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---

# Modifica di uno schema{#edit-schema}

![](../../assets/common.svg)

I dati possono essere trasformati, normalizzati e, se necessario, arricchiti nel flusso di lavoro utilizzando **[!UICONTROL Edit schema]** attività. Viene generalmente utilizzato per normalizzare la struttura dei dati: è possibile rinominare le colonne di output o modificarne il contenuto, ad esempio calcolando i valori medi di un campo o di un aggregato.

Questa attività non modifica i dati nella tabella di lavoro, modifica solo il relativo schema, ovvero la visualizzazione logica dei dati.

![](assets/wf_manipulation_box.png)

È inoltre possibile creare join con altre tabelle di lavoro tramite **[!UICONTROL Links]** scheda .

![](assets/wf_manipulation_box_link_tab.png)

La sezione inferiore consente di configurare l’elenco delle condizioni di unione, ovvero i criteri utilizzati per riconciliare i dati delle due tabelle.
