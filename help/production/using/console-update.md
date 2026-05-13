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
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
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
