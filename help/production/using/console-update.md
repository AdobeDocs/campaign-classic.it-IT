---
product: campaign
title: Aggiornamento della console
description: Aggiornamento della console
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Aggiornamento della console{#console-update}

![](../../assets/v7-only.svg)

Se hai selezionato l&#39;opzione **[!UICONTROL Do not request console update]** e desideri riattivare la richiesta di aggiornamento, applica la procedura seguente:

1. Aprire l&#39;editor del database del Registro di sistema utilizzando il comando **regedit** nel menu Windows **[!UICONTROL Start > Execute]**.

   ![](assets/ncs_console_update_1.png)

1. Nella struttura ad albero, visualizzare le opzioni del nodo **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Elimina la voce **[!UICONTROL confAdvisedUpgrade]** e chiudi l&#39;editor del Registro di sistema.

   ![](assets/ncs_console_update_2.png)
