---
product: campaign
title: Attendi
description: Ulteriori informazioni sull’attività del flusso di lavoro Attendi
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 4%

---

# Attendi{#wait}



A **Wait** l’attività attiva la relativa transizione dopo un ritardo di tempo compreso tra pochi secondi e diversi mesi. Un’attività in attesa non blocca l’esecuzione di altre attività; il flusso di lavoro può eseguire le attività in parallelo mentre questa attività è in sospeso.

Puoi immettere l’etichetta e il tempo di attesa utilizzando l’editor, come nell’esempio seguente:

![](assets/edit_wait.png)

In **[!UICONTROL Duration]** , il valore può essere espresso nell&#39;unità scelta: (in base alle impostazioni internazionali dell&#39;operatore):

* Se non si specificano le impostazioni internazionali: **s** per secondi, **m** per minuti, **h** per ore, **d** per giorni, **y** per anni. Al momento dell’omologazione, il valore viene automaticamente convertito nell’unità più leggibile.

  L&#39;unità predefinita è il giorno (**d**).

* Se, ad esempio, le impostazioni internazionali sono impostate su &quot;Français&quot;: **s** per secondi, **mn** per minuti, **h** per ore, **j** per giorni, **m** per mesi, **a** per anni. Al momento dell’omologazione, il valore viene automaticamente convertito nell’unità più leggibile, come nell’esempio precedente **90s** convertito in **1mn 30s**.

  L&#39;unità predefinita è il giorno (**d**).
