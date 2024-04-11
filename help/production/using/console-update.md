---
product: campaign
title: Aggiornamento della console
description: Aggiornamento della console
feature: Monitoring, Upgrade
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---

# Aggiornamento della console{#console-update}



Se hai selezionato **[!UICONTROL Do not request console update]** e si desidera riattivare la richiesta di aggiornamento, attenersi alla seguente procedura:

1. Aprire l&#39;editor del database del Registro di sistema utilizzando **regedit** comando in Windows **[!UICONTROL Start > Execute]** menu.

   ![](assets/ncs_console_update_1.png)

1. Nella struttura, visualizza le opzioni della **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nodo.
1. Elimina **[!UICONTROL confAdvisedUpgrade]** e chiudi l’editor del Registro di sistema.

   ![](assets/ncs_console_update_2.png)
