---
product: campaign
title: Modifica struttura di navigazione di Campaign Explorer
description: Modifica struttura di navigazione di Campaign Explorer
feature: Application Settings
role: Developer
exl-id: 204d4a24-267c-4976-90d9-7bf5bee8d116
source-git-commit: 9f5205ced6b8d81639d4d0cb6a76905a753cddac
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# Modifica struttura di navigazione di Campaign Explorer{#edition}

La schermata per la creazione e la configurazione dei documenti di configurazione della gerarchia di navigazione è accessibile tramite il nodo **[!UICONTROL Administration > Configuration > Navigation hierarchies]**:

![](assets/d_ncs_integration_navigation_arbo.png)

La configurazione della gerarchia di navigazione è suddivisa in diversi documenti XML. Funziona in base a un principio simile all’estensione dello schema: tutti i documenti vengono uniti per generare un singolo documento contenente l’intera configurazione. Questo documento non può essere modificato e viene visualizzato tramite la scheda &quot;Anteprima&quot;.

Il campo di modifica fornisce il contenuto del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Il controllo di modifica &quot;Nome&quot; consente di immettere la chiave del documento costituita dal nome e dallo spazio dei nomi. Gli attributi &quot;name&quot; e &quot;namespace&quot; dell&#39;elemento **`<navtree>`** vengono aggiornati automaticamente nel campo di modifica XML dello schema.

L&#39;anteprima genera automaticamente il documento unito contenente la configurazione completa:

![](assets/d_ncs_integration_navigation_preview.png)
