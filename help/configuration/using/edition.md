---
product: campaign
title: Modifica struttura di navigazione di Campaign Explorer
description: Modifica struttura di navigazione di Campaign Explorer
feature: Application Settings
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 5%

---


# Modifica struttura di navigazione di Campaign Explorer{#edition}

La schermata per la creazione e la configurazione dei documenti di configurazione della gerarchia di navigazione è accessibile tramite **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nodo:

![](assets/d_ncs_integration_navigation_arbo.png)

La configurazione della gerarchia di navigazione è suddivisa in diversi documenti XML. Funziona in base a un principio simile all’estensione dello schema: tutti i documenti vengono uniti per generare un singolo documento contenente l’intera configurazione. Questo documento non può essere modificato e viene visualizzato tramite la scheda &quot;Anteprima&quot;.

Il campo di modifica fornisce il contenuto del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Il controllo di modifica &quot;Nome&quot; consente di immettere la chiave del documento costituita dal nome e dallo spazio dei nomi. Gli attributi &quot;name&quot; e &quot;namespace&quot; del **`<navtree>`** vengono aggiornati automaticamente nel campo di modifica XML dello schema.

L&#39;anteprima genera automaticamente il documento unito contenente la configurazione completa:

![](assets/d_ncs_integration_navigation_preview.png)
