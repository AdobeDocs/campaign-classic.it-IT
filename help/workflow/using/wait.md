---
solution: Campaign Classic
product: campaign
title: Wait
description: Ulteriori informazioni sull'attività del flusso di lavoro di attesa
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---


# Wait{#wait}

Un&#39;attività **Wait** attiva la transizione dopo un ritardo di tempo compreso tra alcuni secondi e diversi mesi. Un&#39;attività di attesa non blocca l&#39;esecuzione di altre attività; il flusso di lavoro può eseguire attività in parallelo mentre l&#39;attività è in sospeso.

Potete immettere l&#39;etichetta e il tempo di attesa utilizzando l&#39;editor, come nell&#39;esempio seguente:

![](assets/edit_wait.png)

Nel **[!UICONTROL Duration]** campo, il valore può essere espresso nell&#39;unità di scelta: (in base alle impostazioni regionali dell&#39;operatore):

* Se le impostazioni internazionali non sono specificate: **s** per secondi, **m** per minuti, **h** per ore, **d** per giorni, **y** per anni. Al momento dell&#39;approvazione, il valore viene automaticamente convertito nell&#39;unità più leggibile.

   L&#39;unità predefinita è il giorno (**d**).

* Se, ad esempio, le impostazioni regionali sono impostate su &quot;Français&quot;: **s** per secondi, **mn** per minuti, **h** per ore, **j** per giorni, **m** per mesi, **** un&#39;ora per anni. Al momento dell&#39;approvazione, il valore viene automaticamente convertito nell&#39;unità più leggibile, come nell&#39;esempio sopra **90** è stato convertito in **1mn 30**.

   L&#39;unità predefinita è il giorno (**d**).

