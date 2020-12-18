---
solution: Campaign Classic
product: campaign
title: AND-join
description: AND-join
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 6%

---


# AND-join{#and-join}

Un join attiva la propria transizione in uscita solo quando vengono attivate tutte le transizioni in entrata, ossia quando tutte le attività precedenti sono terminate. Questo consente di verificare che alcune attività siano state completate prima di continuare a eseguire il flusso di lavoro.

Ad esempio, potete utilizzare un&#39;attività AND-join nel contesto della creazione di contenuto e dell&#39;automazione dell&#39;invio di contenuti, per fare in modo che una consegna venga avviata solo una volta completate le fasi di query di destinazione e di aggiornamento dei contenuti. Un caso d&#39;uso dedicato è disponibile in [questa sezione](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)

![](assets/and-join-usage.png)

La popolazione inviata in uscita dell&#39;attività è determinata scegliendo un set principale tra le transizioni in entrata nell&#39;attività.

La transizione in uscita può contenere solo una delle popolazioni di transizione in entrata. Se l&#39;attività non è configurata, la transizione in uscita selezionerà in modo casuale una delle popolazioni in entrata.

>[!CAUTION]
>
>Nel caso di attività di tipo **AND-join**, le variabili dell&#39;evento vengono unite ma se una stessa variabile viene definita due volte, si verifica un conflitto e il valore rimane indeterminato. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/javascript-scripts-and-templates.md#event-variables).
