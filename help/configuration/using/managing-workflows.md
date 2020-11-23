---
solution: Campaign Classic
product: campaign
title: Gestione dei flussi di lavoro
description: Gestione dei flussi di lavoro
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '134'
ht-degree: 4%

---


# Gestione dei flussi di lavoro{#managing-workflows}

Per impostazione predefinita, i nuovi flussi di lavoro si basano su un modello di flusso di lavoro preconfigurato e basato su una tabella del destinatario (nms:destinatario). Affinché siano basati automaticamente sulla tabella personalizzata dei destinatari a cui viene fatto riferimento nell&#39;opzione **Nms_DefaultRcpSchema** (vedere [Configurazione della sezione dell&#39;interfaccia](../../configuration/using/configuring-the-interface.md) ), è necessario creare un nuovo modello di flusso di lavoro.

Crea un nuovo modello tramite il **[!UICONTROL Resources > Templates > Workflow templates]** nodo. Nelle proprietà del modello, le dimensioni fornite corrispondono alla tabella dei destinatari esterni.

Basando i nuovi flussi di lavoro su un modello creato di recente, la tabella personalizzata verrà selezionata per impostazione predefinita per le dimensioni globali di targeting e filtro del flusso di lavoro.

Tutte le attività utilizzate nel flusso di lavoro utilizzeranno quindi la tabella personalizzata senza bisogno di ulteriori configurazioni manuali.

For more information on workflows, refer to [this section](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)

