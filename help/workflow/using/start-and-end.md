---
solution: Campaign Classic
product: campaign
title: Start ed End
description: Ulteriori informazioni sulle attività di avvio e fine del flusso di lavoro
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%

---


# Start ed End{#start-and-end}

Le attività **[!UICONTROL Start]** e **[!UICONTROL End]** consentono di contrassegnare graficamente l’inizio e la fine di un flusso di lavoro. Queste attività non hanno alcun impatto funzionale e sono pertanto facoltative.

* **[!UICONTROL Start]**

   L&#39;esecuzione di un flusso di lavoro inizia con attività senza transizioni in entrata e attività di tipo Start.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   Potete configurare l&#39; **[!UICONTROL End]** attività per interrompere tutte le attività in corso. A questo scopo, fate doppio clic sull&#39;attività per visualizzarne le proprietà, quindi selezionate l&#39;opzione appropriata.

   ![](assets/s_user_segmentation_end.png)

   I dati nella tabella di lavoro vengono eliminati automaticamente quando l&#39;attività finale è abilitata. Se ciò non è necessario e per evitare carichi non necessari, potete scegliere di disabilitare la transizione all&#39;ultimo output dell&#39;attività. Ad esempio, in corrispondenza di un output di consegna, se non è pianificato alcun processo, deselezionate l&#39;opzione appropriata come illustrato di seguito:

   ![](assets/s_advuser_delivery_option_no_output.png)

