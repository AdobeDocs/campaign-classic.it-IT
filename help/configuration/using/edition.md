---
solution: Campaign Classic
product: campaign
title: Modifica
description: Modifica
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: d6993725ed4060f2affce98c4a8a5211bda03bdf
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 1%

---


# Modifica albero di navigazione di Campaign Explorer{#edition}

La schermata per la creazione e la configurazione dei documenti di configurazione della gerarchia di navigazione è accessibile tramite il nodo **[!UICONTROL Administration > Configuration > Navigation hierarchies]** :

![](assets/d_ncs_integration_navigation_arbo.png)

La configurazione della gerarchia di navigazione è divisa su più documenti XML. Opera su un principio simile all&#39;estensione dello schema: tutti i documenti vengono uniti per generare un singolo documento contenente l’intera configurazione. Questo documento non può essere modificato e viene visualizzato tramite la scheda &quot;Anteprima&quot;.

Il campo di modifica fornisce il contenuto del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Il controllo di modifica &quot;Nome&quot; consente di inserire la chiave del documento costituita dal nome e dallo spazio dei nomi. Gli attributi &quot;name&quot; e &quot;namespace&quot; dell’elemento **`<navtree>`** vengono aggiornati automaticamente nel campo di modifica XML dello schema.

L’anteprima genera automaticamente il documento unito contenente la configurazione completa:

![](assets/d_ncs_integration_navigation_preview.png)

