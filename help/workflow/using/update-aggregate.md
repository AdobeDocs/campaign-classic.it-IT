---
solution: Campaign Classic
product: campaign
title: Aggiorna aggregato
description: Ulteriori informazioni sull'attività del flusso di lavoro Aggiorna aggregazione
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---


# Aggiorna aggregato{#update-aggregate}

Gli aggregati sono definiti a livello di cubo ai fini del reporting. Quando si configura un&#39;aggregazione è disponibile una scheda **[!UICONTROL Workflow]**.

Per ulteriori informazioni sui cubi e sull&#39;utilizzo degli aggregati in  Adobe Campaign, fare riferimento alla sezione dedicata [](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates).

L&#39;attività **[!UICONTROL Update aggregate]** consente di selezionare la modalità di aggiornamento da applicare: pieno o parziale.

Per impostazione predefinita, durante ogni calcolo viene eseguito un aggiornamento completo. Per abilitare un aggiornamento parziale, selezionate l&#39;opzione pertinente e definite le condizioni di aggiornamento.

![](assets/s_advuser_cube_agregate_05.png)

**Buona pratica**: un&#39; **[!UICONTROL Scheduler]** attività può essere utilizzata per specificare la frequenza degli aggiornamenti di calcolo.

![](assets/s_advuser_cube_agregate_04.png)

