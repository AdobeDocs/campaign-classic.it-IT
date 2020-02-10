---
title: Inizio e fine
seo-title: Inizio e fine
description: Inizio e fine
seo-description: null
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# Inizio e fine{#start-and-end}

Le attività **[!UICONTROL Start]** e **[!UICONTROL End]** consentono di contrassegnare graficamente l’inizio e la fine di un flusso di lavoro. Queste attività non hanno alcun impatto funzionale e sono pertanto facoltative.

* **[!UICONTROL Start]**

   L&#39;esecuzione di un flusso di lavoro inizia con attività senza transizioni in entrata e attività di tipo Start.

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   Potete configurare l&#39; **[!UICONTROL End]** attività per interrompere tutte le attività in corso. A questo scopo, fate doppio clic sull&#39;attività per visualizzarne le proprietà, quindi selezionate l&#39;opzione appropriata.

   ![](assets/s_user_segmentation_end.png)

   I dati nella tabella di lavoro vengono eliminati automaticamente quando l&#39;attività finale è abilitata. Se ciò non è necessario e per evitare carichi non necessari, potete scegliere di disabilitare la transizione all&#39;ultimo output dell&#39;attività. Ad esempio, in corrispondenza di un output di consegna, se non è pianificato alcun processo, deselezionate l&#39;opzione appropriata come illustrato di seguito:

   ![](assets/s_advuser_delivery_option_no_output.png)

