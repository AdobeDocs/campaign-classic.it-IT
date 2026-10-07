---
product: campaign
title: Gestione dei flussi di lavoro
description: Gestione dei flussi di lavoro
feature: Workflows, Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: 'https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%
---
# Gestione dei flussi di lavoro{#managing-workflows}



Per impostazione predefinita, i nuovi flussi di lavoro si basano su un modello di flusso di lavoro preconfigurato e basato su una tabella dei destinatari (nms:recipient). Per basarli automaticamente sulla tabella personalizzata dei destinatari a cui si fa riferimento nell&#39;opzione **Nms_DefaultRcpSchema** (vedere la [sezione Configurazione dell&#39;interfaccia](../../configuration/using/configuring-the-interface.md)), è necessario creare un nuovo modello di flusso di lavoro.

Crea un nuovo modello tramite il nodo **[!UICONTROL Resources > Templates > Workflow templates]**. Nelle proprietà del modello, le dimensioni fornite corrispondono alla tabella dei destinatari esterni.

Basando i nuovi flussi di lavoro su un modello creato di recente, la tabella personalizzata verrà selezionata per impostazione predefinita per le dimensioni di targeting e filtro globali del flusso di lavoro.

Tutte le attività utilizzate nel flusso di lavoro utilizzeranno quindi la tabella personalizzata senza richiedere alcuna configurazione manuale aggiuntiva.

Per ulteriori informazioni sui flussi di lavoro, consulta [questa sezione](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
