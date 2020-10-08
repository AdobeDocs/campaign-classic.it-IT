---
title: Aggiornamento della console
seo-title: Aggiornamento della console
description: Aggiornamento della console
seo-description: null
page-status-flag: never-activated
uuid: d2193d4f-b98c-47b1-88f1-7e5ccf4c453c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 9281808b-1c2f-4095-9051-f181f089f205
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '57'
ht-degree: 14%

---


# Aggiornamento della console{#console-update}

Se avete selezionato l’ **[!UICONTROL Do not request console update]** opzione e desiderate riattivare la richiesta di aggiornamento, eseguite la procedura seguente:

1. Aprire l&#39;editor del database del Registro di sistema utilizzando il comando **regedit** nel menu di Windows **[!UICONTROL Start > Execute]** .

   ![](assets/ncs_console_update_1.png)

1. Nella struttura ad albero, visualizzare le opzioni del **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]** nodo.
1. Eliminare la **[!UICONTROL confAdvisedUpgrade]** voce e chiudere l&#39;editor del Registro di sistema.

   ![](assets/ncs_console_update_2.png)

