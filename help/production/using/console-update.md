---
product: campaign
title: Aggiornamento della console
description: Aggiornamento della console
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
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
