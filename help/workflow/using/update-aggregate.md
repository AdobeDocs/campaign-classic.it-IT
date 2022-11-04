---
product: campaign
title: Aggregato di aggiornamento
description: Ulteriori informazioni sull’attività del flusso di lavoro aggregato Aggiorna
feature: Workflows
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
source-git-commit: 1635366b9e1302acd3d8997312bf07d5c1a68982
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 3%

---

# Aggregato di aggiornamento{#update-aggregate}

![](../../assets/v7-only.svg)

Gli aggregati sono definiti a livello di cubo a scopo di reporting. A **[!UICONTROL Workflow]** è disponibile durante la configurazione di un aggregato.

Gli aggregati sono utili per la manipolazione di grandi volumi di dati. Vengono aggiornati automaticamente in base alle impostazioni definite nella casella del flusso di lavoro dedicata, per integrare i dati raccolti più di recente negli indicatori

Gli aggregati sono definiti nella scheda pertinente di ciascun cubo.

![](assets/s_advuser_cube_agregate_01.png)


La **[!UICONTROL Update aggregate]** activity ti consente di selezionare la modalità di aggiornamento da applicare: completo o parziale.

Per impostazione predefinita, durante ogni calcolo viene eseguito un aggiornamento completo. Per abilitare un aggiornamento parziale, seleziona l’opzione pertinente e definisci le condizioni di aggiornamento.

![](assets/s_advuser_cube_agregate_05.png)

**Buone pratiche**: a **[!UICONTROL Scheduler]** l’attività può essere utilizzata per specificare la frequenza degli aggiornamenti di calcolo.

![](assets/s_advuser_cube_agregate_04.png)
