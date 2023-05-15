---
product: campaign
title: Gestione dei flussi di lavoro
description: Gestione dei flussi di lavoro
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---

# Gestione dei flussi di lavoro{#managing-workflows}



Per impostazione predefinita, i nuovi flussi di lavoro si basano su un modello di flusso di lavoro preconfigurato e basato su una tabella dei destinatari (nms:recipient). Affinché siano basati automaticamente sulla tabella personalizzata dei destinatari a cui si fa riferimento nel **Nms_DefaultRcpSchema** (vedi [Configurazione dell’interfaccia](../../configuration/using/configuring-the-interface.md) (sezione ), devi creare un nuovo modello di flusso di lavoro.

Crea un nuovo modello tramite **[!UICONTROL Resources > Templates > Workflow templates]** nodo. Nelle proprietà del modello, le dimensioni fornite corrispondono alla tabella dei destinatari esterni.

Basando i nuovi flussi di lavoro su un modello creato di recente, la tabella personalizzata verrà selezionata per impostazione predefinita per le dimensioni di targeting e filtro globali del flusso di lavoro.

Tutte le attività utilizzate nel flusso di lavoro utilizzeranno quindi la tabella personalizzata senza bisogno di alcuna configurazione manuale aggiuntiva.

Per ulteriori informazioni sui flussi di lavoro, consulta [questa sezione](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
