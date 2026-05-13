---
product: campaign
title: Gestione dei flussi di lavoro
description: Gestione dei flussi di lavoro
feature: Workflows, Configuration
role: Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 617b0050-6b04-4c68-9f63-511baae99f41
TQID: https://experienceleague.adobe.com/dpHtLw4PYGg35t-ihmw9LGUSbjgeNloUhGXp9KPJaRU
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 142
ht-degree: 4%

---

# Gestione dei flussi di lavoro{#managing-workflows}



Per impostazione predefinita, i nuovi flussi di lavoro si basano su un modello di flusso di lavoro preconfigurato e basato su una tabella dei destinatari (nms:recipient). Per basarli automaticamente sulla tabella personalizzata dei destinatari a cui si fa riferimento nell&#39;opzione **Nms_DefaultRcpSchema** (vedere la [sezione Configurazione dell&#39;interfaccia](../../configuration/using/configuring-the-interface.md)), è necessario creare un nuovo modello di flusso di lavoro.

Crea un nuovo modello tramite il nodo **[!UICONTROL Resources > Templates > Workflow templates]**. Nelle proprietà del modello, le dimensioni fornite corrispondono alla tabella dei destinatari esterni.

Basando i nuovi flussi di lavoro su un modello creato di recente, la tabella personalizzata verrà selezionata per impostazione predefinita per le dimensioni di targeting e filtro globali del flusso di lavoro.

Tutte le attività utilizzate nel flusso di lavoro utilizzeranno quindi la tabella personalizzata senza richiedere alcuna configurazione manuale aggiuntiva.

Per ulteriori informazioni sui flussi di lavoro, consulta [questa sezione](../../workflow/using/about-workflows.md).

![](assets/cfg_external_table_workflow.png)
