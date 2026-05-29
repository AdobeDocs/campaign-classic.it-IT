---
product: campaign
title: Attendere
description: Ulteriori informazioni sull’attività del flusso di lavoro Attendi
feature: Workflows
hide: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
TQID: https://experienceleague.adobe.com/sQ3GwMFQnhy6eOmFSfMUwT8Z3UE0p4cHLAjr8CjS2FM
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: []
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
  - id: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 192
ht-degree: 1%

---

# Attendere{#wait}



Un&#39;attività **Wait** attiva la relativa transizione dopo un ritardo di tempo compreso tra alcuni secondi e diversi mesi. Un’attività in attesa non blocca l’esecuzione di altre attività; il flusso di lavoro può eseguire le attività in parallelo mentre questa attività è in sospeso.

Puoi immettere l’etichetta e il tempo di attesa utilizzando l’editor, come nell’esempio seguente:

![](assets/edit_wait.png)

Nel campo **[!UICONTROL Duration]**, il valore può essere espresso nell&#39;unità scelta: (in base alle impostazioni internazionali dell&#39;operatore):

* Se le impostazioni internazionali non sono specificate: **s** per secondi, **m** per minuti, **h** per ore, **d** per giorni, **y** per anni. Al momento dell’omologazione, il valore viene automaticamente convertito nell’unità più leggibile.

  L&#39;unità predefinita è il giorno (**d**).

* Se, ad esempio, le impostazioni internazionali sono impostate su &quot;Français&quot;: **s** per secondi, **mn** per minuti, **h** per ore, **j** per giorni, **m** per mesi, **a** per anni. Al momento dell&#39;approvazione, il valore viene automaticamente convertito nell&#39;unità più leggibile, come nell&#39;esempio precedente **90s** è stato convertito in **1mn 30s**.

  L&#39;unità predefinita è il giorno (**d**).
