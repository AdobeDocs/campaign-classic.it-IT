---
product: campaign
title: Modifica
description: Editio
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---


# Modifica albero di navigazione di Campaign Explorer{#edition}

![](../../assets/v7-only.svg)

La schermata per la creazione e la configurazione dei documenti di configurazione della gerarchia di navigazione è accessibile tramite **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nodo:

![](assets/d_ncs_integration_navigation_arbo.png)

La configurazione della gerarchia di navigazione è divisa su più documenti XML. Opera su un principio simile all&#39;estensione dello schema: tutti i documenti vengono uniti per generare un singolo documento contenente l’intera configurazione. Questo documento non può essere modificato e viene visualizzato tramite la scheda &quot;Anteprima&quot;.

Il campo di modifica fornisce il contenuto del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Il controllo di modifica &quot;Nome&quot; consente di inserire la chiave del documento costituita dal nome e dallo spazio dei nomi. Gli attributi &quot;name&quot; e &quot;namespace&quot; del **`<navtree>`** vengono aggiornati automaticamente nel campo di modifica XML dello schema.

L’anteprima genera automaticamente il documento unito contenente la configurazione completa:

![](assets/d_ncs_integration_navigation_preview.png)
