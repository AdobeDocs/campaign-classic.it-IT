---
solution: Campaign Classic
product: campaign
title: Aggiornamento della console
description: Aggiornamento della console
audience: production
content-type: reference
topic-tags: troubleshooting
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '55'
ht-degree: 10%

---


# Aggiornamento della console{#console-update}

Se avete selezionato l&#39;opzione **[!UICONTROL Do not request console update]** e desiderate riattivare la richiesta di aggiornamento, eseguite la procedura seguente:

1. Aprire l&#39;editor del database del Registro di sistema utilizzando il comando **regedit** nel menu di Windows **[!UICONTROL Start > Execute]**.

   ![](assets/ncs_console_update_1.png)

1. Nella struttura ad albero, visualizzare le opzioni del nodo **[!UICONTROL HKEY_CURRENT_USERSoftwareneolaneNL_6nlclient]**.
1. Eliminate la voce **[!UICONTROL confAdvisedUpgrade]** e chiudete l&#39;editor del Registro di sistema.

   ![](assets/ncs_console_update_2.png)

