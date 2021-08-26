---
product: campaign
title: Gestione dei flussi di lavoro
description: Gestione dei flussi di lavoro
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---

# Gestione dei flussi di lavoro{#managing-workflows}

![](../../assets/v7-only.svg)

Per impostazione predefinita, i nuovi flussi di lavoro si basano su un modello di flusso di lavoro preconfigurato e basato su una tabella dei destinatari (nms:recipient). Affinché siano basati automaticamente sulla tabella personalizzata dei destinatari a cui si fa riferimento nell&#39;opzione **Nms_DefaultRcpSchema** (consulta la sezione [Configurazione dell&#39;interfaccia](../../configuration/using/configuring-the-interface.md) ), è necessario creare un nuovo modello di flusso di lavoro.

Crea un nuovo modello tramite il nodo **[!UICONTROL Resources > Templates > Workflow templates]** . Nelle proprietà del modello, le dimensioni fornite corrispondono alla tabella dei destinatari esterni.

Basando i nuovi flussi di lavoro su un modello creato di recente, la tabella personalizzata verrà selezionata per impostazione predefinita per le dimensioni di targeting e filtro globali del flusso di lavoro.

Tutte le attività utilizzate nel flusso di lavoro utilizzeranno quindi la tabella personalizzata senza bisogno di alcuna configurazione manuale aggiuntiva.

Per ulteriori informazioni sui flussi di lavoro, consulta [questa sezione](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
