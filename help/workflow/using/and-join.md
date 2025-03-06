---
product: campaign
title: AND-join
description: AND-join
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 14%

---

# AND-join{#and-join}



Un join attiva la relativa transizione in uscita solo quando vengono attivate tutte le transizioni in entrata, ovvero quando tutte le attività precedenti sono state completate. Questo consente di verificare che alcune attività siano state completate prima di continuare a eseguire il flusso di lavoro.

Ad esempio, puoi utilizzare un’attività AND-join nel contesto della creazione di contenuti e dell’automazione dell’invio della consegna, per assicurarti che una consegna venga avviata solo una volta completati i passaggi di query di destinazione e aggiornamenti dei contenuti. Un caso d&#39;uso dedicato è disponibile in [questa sezione](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>Le transizioni in entrata configurate con dimensioni di targeting diverse non possono essere unite insieme utilizzando un&#39;attività **[!UICONTROL AND-join]**.

La popolazione in uscita inviata dell’attività è determinata scegliendo un set principale tra le transizioni in entrata nell’attività.

La transizione in uscita può contenere solo una delle popolazioni di transizione in entrata. Se l’attività non è configurata, la transizione in uscita selezionerà in modo casuale una delle popolazioni in entrata.

>[!CAUTION]
>
>Nel caso di attività di tipo **AND-join**, le variabili evento vengono unite ma se viene definita due volte la stessa variabile, si verifica un conflitto e il valore rimane indeterminato. Per ulteriori informazioni al riguardo, consulta [questa sezione](javascript-scripts-and-templates.md#event-variables).
