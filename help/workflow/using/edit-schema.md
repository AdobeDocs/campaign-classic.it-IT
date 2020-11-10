---
title: Modifica schema
description: Ulteriori informazioni sull'attività del flusso di lavoro Modifica schema
page-status-flag: never-activated
uuid: abd77902-98b7-4ab7-a240-dd6b3bb247bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 733576d2-505f-4598-89eb-a10e7331bf7e
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 3%

---


# Modifica schema{#edit-schema}

I dati possono essere trasformati, normalizzati e, se necessario, arricchiti nel flusso di lavoro tramite l&#39; **[!UICONTROL Edit schema]** attività. Viene generalmente utilizzato per normalizzare la struttura dei dati: è possibile rinominare le colonne di output o modificarne il contenuto, calcolando ad esempio i valori medi di un campo o di un aggregato.

Questa attività non modifica i dati nella tabella di lavoro, modifica solo il relativo schema, ovvero la visualizzazione logica dei dati.

![](assets/wf_manipulation_box.png)

È inoltre possibile creare join con altre tabelle di lavoro tramite la **[!UICONTROL Links]** scheda.

![](assets/wf_manipulation_box_link_tab.png)

La sezione inferiore consente di configurare l&#39;elenco delle condizioni di unione, ossia i criteri utilizzati per riconciliare i dati delle due tabelle.
