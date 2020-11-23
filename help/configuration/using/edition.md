---
solution: Campaign Classic
product: campaign
title: Modifica
description: Modifica
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 2%

---


# Modifica{#edition}

La schermata per la creazione e la configurazione dei documenti di configurazione della gerarchia di navigazione è accessibile tramite il **[!UICONTROL Administration > Configuration > Navigation hierarchies]** nodo:

![](assets/d_ncs_integration_navigation_arbo.png)

La configurazione della gerarchia di navigazione è suddivisa in più documenti XML. Opera in base a un principio simile all&#39;estensione dello schema: tutti i documenti vengono uniti per generare un singolo documento contenente l’intera configurazione. Questo documento non può essere modificato e viene visualizzato tramite la scheda &quot;Anteprima&quot;.

Il campo di modifica fornisce il contenuto del documento XML:

![](assets/d_ncs_integration_navigation_edit.png)

>[!NOTE]
>
>Il controllo di modifica &quot;Name&quot; consente di immettere la chiave del documento costituita dal nome e dallo spazio dei nomi. Gli attributi &quot;name&quot; e &quot;namespace&quot; dell&#39; **`<navtree>`** elemento vengono aggiornati automaticamente nel campo di modifica XML dello schema.

L&#39;anteprima genera automaticamente il documento unito contenente la configurazione completa:

![](assets/d_ncs_integration_navigation_preview.png)

