---
product: campaign
title: Aggiornamento della console
description: Aggiornamento della console
feature: Monitoring, Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 3a127bbe-9abb-4b5b-bd7e-e1ea550929ba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 20%

---

# Aggiornamento della console{#console-update}



Se hai selezionato **[!UICONTROL Do not request console update]** e si desidera riattivare la richiesta di aggiornamento, attenersi alla seguente procedura:

1. Aprire l&#39;editor del database del Registro di sistema utilizzando **regedit** comando in Windows **[!UICONTROL Start > Execute]** menu.

   ![](assets/ncs_console_update_1.png)

1. Nella struttura, visualizza le opzioni della **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nodo.
1. Elimina **[!UICONTROL confAdvisedUpgrade]** e chiudi l’editor del Registro di sistema.

   ![](assets/ncs_console_update_2.png)
