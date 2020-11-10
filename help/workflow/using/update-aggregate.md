---
title: Aggiorna aggregato
description: Ulteriori informazioni sull'attività del flusso di lavoro Aggiorna aggregazione
page-status-flag: never-activated
uuid: 34ae42e1-da34-43be-b219-0b3b872177b3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 031f8d5d-940c-4a4c-97e7-ad4ef61983c1
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '96'
ht-degree: 4%

---


# Aggiorna aggregato{#update-aggregate}

Gli aggregati sono definiti a livello di cubo ai fini del reporting. Quando si configura un aggregato è disponibile una **[!UICONTROL Workflow]** scheda.

Per ulteriori informazioni sui cubi e sull&#39;utilizzo degli aggregati in  Adobe Campaign, consultare la [sezione](../../reporting/using/concepts-and-methodology.md#calculating-and-using-aggregates)dedicata.

L&#39; **[!UICONTROL Update aggregate]** attività consente di selezionare la modalità di aggiornamento da applicare: pieno o parziale.

Per impostazione predefinita, durante ogni calcolo viene eseguito un aggiornamento completo. Per abilitare un aggiornamento parziale, selezionate l&#39;opzione pertinente e definite le condizioni di aggiornamento.

![](assets/s_advuser_cube_agregate_05.png)

**Buona pratica**: un&#39; **[!UICONTROL Scheduler]** attività può essere utilizzata per specificare la frequenza degli aggiornamenti di calcolo.

![](assets/s_advuser_cube_agregate_04.png)

