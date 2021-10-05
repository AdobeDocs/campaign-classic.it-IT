---
product: campaign
title: Aggregato di aggiornamento
description: Ulteriori informazioni sull’attività del flusso di lavoro aggregato Aggiorna
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 4%

---

# Aggregato di aggiornamento{#update-aggregate}

![](../../assets/common.svg)

Gli aggregati sono definiti a livello di cubo a scopo di reporting. Quando configuri un aggregato è disponibile una scheda **[!UICONTROL Workflow]** .

Per ulteriori informazioni sui cubi e sull&#39;utilizzo degli aggregati in Adobe Campaign, consulta la sezione dedicata [sezione](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

L’attività **[!UICONTROL Update aggregate]** ti consente di selezionare la modalità di aggiornamento da applicare: completo o parziale.

Per impostazione predefinita, durante ogni calcolo viene eseguito un aggiornamento completo. Per abilitare un aggiornamento parziale, seleziona l’opzione pertinente e definisci le condizioni di aggiornamento.

![](assets/s_advuser_cube_agregate_05.png)

**Buona pratica**: un’ **[!UICONTROL Scheduler]** attività può essere utilizzata per specificare la frequenza degli aggiornamenti di calcolo.

![](assets/s_advuser_cube_agregate_04.png)
