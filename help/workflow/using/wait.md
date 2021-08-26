---
product: campaign
title: Attività Wait
description: Ulteriori informazioni sull’attività del flusso di lavoro Wait
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# Attività Wait{#wait}

![](../../assets/common.svg)

Un&#39;attività **Wait** attiva la relativa transizione dopo un ritardo di tempo compreso tra alcuni secondi e diversi mesi. Un’attività di attesa non blocca l’esecuzione di altre attività; il flusso di lavoro può eseguire attività in parallelo mentre questa attività è in sospeso.

Puoi immettere l’etichetta e attendere il tempo di attesa utilizzando l’editor, come nell’esempio seguente:

![](assets/edit_wait.png)

Nel campo **[!UICONTROL Duration]**, il valore può essere espresso nell&#39;unità scelta: (secondo le impostazioni regionali dell&#39;operatore):

* Se le impostazioni internazionali non sono specificate: **s** per secondi, **m** per minuti, **h** per ore, **d** per giorni, **y** per anni. Al momento dell’approvazione, il valore viene automaticamente convertito nell’unità più leggibile.

   L&#39;unità predefinita è il giorno (**d**).

* Se, ad esempio, le impostazioni regionali sono impostate su &quot;Français&quot;: **s** per secondi, **mn** per minuti, **h** per ore, **j** per giorni, **m** per mesi, **a** per anni. Al momento dell&#39;approvazione, il valore viene automaticamente convertito nell&#39;unità più leggibile, come nell&#39;esempio precedente **90s** è stato convertito in **1mn 30s**.

   L&#39;unità predefinita è il giorno (**d**).
