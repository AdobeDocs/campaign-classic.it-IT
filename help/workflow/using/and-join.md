---
product: campaign
title: Attività AND-join
description: Attività AND-join
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 8b6d5c03-e104-4cf0-82ab-a08467e3e478
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 5%

---

# Attività AND-join{#and-join}

![](../../assets/common.svg)

Un join attiva la relativa transizione in uscita solo quando vengono attivate tutte le transizioni in entrata, ad esempio al termine di tutte le attività precedenti. Questo ti consente di verificare che alcune attività siano state completate prima di continuare a eseguire il flusso di lavoro.

Ad esempio, puoi utilizzare un’attività AND-join nel contesto dell’automazione della creazione e dell’invio dei contenuti, per assicurarti che una consegna venga avviata solo una volta completati i passaggi di query di destinazione e aggiornamenti dei contenuti. Un caso d&#39;uso dedicato è disponibile in [questa sezione](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

>[!NOTE]
>
>Tieni presente che le transizioni in entrata configurate con diverse dimensioni di targeting non possono essere unite utilizzando un’attività **[!UICONTROL AND-join]** .

La popolazione in uscita inviata dell’attività è determinata scegliendo un set principale tra le transizioni in entrata nell’attività.

La transizione in uscita può contenere solo una delle popolazioni di transizione in entrata. Se l’attività non è configurata, la transizione in uscita selezionerà in modo casuale una delle popolazioni in entrata.

>[!CAUTION]
>
>Nel caso di attività di tipo **AND-join**, le variabili dell&#39;evento vengono unite ma se una stessa variabile viene definita due volte, si verifica un conflitto e il valore rimane indeterminato. Per ulteriori informazioni al riguardo, consulta [questa sezione](javascript-scripts-and-templates.md#event-variables).
