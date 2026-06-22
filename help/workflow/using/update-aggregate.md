---
product: campaign
title: Aggregato di aggiornamento
description: Ulteriori informazioni sull’attività del flusso di lavoro aggregato Aggiornamento
feature: Workflows
hide: true
exl-id: d2b26af0-30a1-4852-acd5-996795f198a1
TQID: https://experienceleague.adobe.com/YnOd1mT0WQqXHVeFUXFoumzDHxSSlKE2tgGSQFrjBzQ
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
feature_v2: []
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: c35995a47788db080636c66827a4bd6dc98806cf
workflow-type: tm+mt
source-wordcount: 123
ht-degree: 3%

---

# Aggregato di aggiornamento{#update-aggregate}



Gli aggregati sono definiti a livello di cubo a scopo di reporting. È disponibile una scheda **[!UICONTROL Workflow]** durante la configurazione di un aggregato.

Gli aggregati sono utili quando si manipolano grandi volumi di dati. Vengono aggiornati automaticamente in base alle impostazioni definite nella casella del flusso di lavoro dedicato, per integrare negli indicatori i dati raccolti più di recente

Gli aggregati vengono definiti nella scheda relativa di ciascun cubo.

![](assets/s_advuser_cube_agregate_01.png)


L&#39;attività **[!UICONTROL Update aggregate]** consente di selezionare la modalità di aggiornamento da applicare: completo o parziale.

Per impostazione predefinita, durante ogni calcolo viene eseguito un aggiornamento completo. Per abilitare un aggiornamento parziale, seleziona l’opzione pertinente e definisci le condizioni di aggiornamento.

![](assets/s_advuser_cube_agregate_05.png)

**Buona pratica**: è possibile utilizzare un&#39;attività **[!UICONTROL Scheduler]** per specificare la frequenza degli aggiornamenti dei calcoli.

![](assets/s_advuser_cube_agregate_04.png)

