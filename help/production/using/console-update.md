---
product: campaign
title: Aggiornamento della console
description: Aggiornamento della console
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
TQID: https://experienceleague.adobe.com/oNVXa9DaMu-b-GpfxT-Z0jFbWEd-MnsSzu8Jdb0S0Fw
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2:
  - id: c1579802-ddd4-4214-8a91-97b2066abe11
feature_v2: []
subfeature_v2:
  - id: c03a11ff-bdf9-4e5b-b279-f468b4293464
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 55
ht-degree: 10%

---

# Aggiornamento della console{#console-update}



Se è stata selezionata l&#39;opzione **[!UICONTROL Do not request console update]** e si desidera riattivare la richiesta di aggiornamento, attenersi alla procedura seguente:

1. Aprire l&#39;editor del database del Registro di sistema utilizzando il comando **regedit** nel menu di Windows **[!UICONTROL Start > Execute]**.

   ![](assets/ncs_console_update_1.png)

1. Nella struttura, visualizzare le opzioni del nodo **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Eliminare la voce **[!UICONTROL confAdvisedUpgrade]** e chiudere l&#39;editor del Registro di sistema.

   ![](assets/ncs_console_update_2.png)
