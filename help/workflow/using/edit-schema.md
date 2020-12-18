---
solution: Campaign Classic
product: campaign
title: Modifica schema
description: Ulteriori informazioni sull'attività del flusso di lavoro Modifica schema
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---


# Modifica schema{#edit-schema}

I dati possono essere trasformati, normalizzati e, se necessario, arricchiti nel flusso di lavoro utilizzando l&#39;attività **[!UICONTROL Edit schema]**. Viene generalmente utilizzato per normalizzare la struttura dei dati: è possibile rinominare le colonne di output o modificarne il contenuto, calcolando ad esempio i valori medi di un campo o di un aggregato.

Questa attività non modifica i dati nella tabella di lavoro, modifica solo il relativo schema, ovvero la visualizzazione logica dei dati.

![](assets/wf_manipulation_box.png)

È inoltre possibile creare join con altre tabelle di lavoro, tramite la scheda **[!UICONTROL Links]**.

![](assets/wf_manipulation_box_link_tab.png)

La sezione inferiore consente di configurare l&#39;elenco delle condizioni di unione, ossia i criteri utilizzati per riconciliare i dati delle due tabelle.
