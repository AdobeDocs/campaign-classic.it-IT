---
product: campaign
title: SMS in entrata
description: Ulteriori informazioni sull’attività del flusso di lavoro SMS in entrata
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Channels Activity
exl-id: 94a9d50b-4ead-4815-8d12-942fa78b4e8a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 4%

---

# SMS in entrata{#inbound-sms}



La **SMS in entrata** activity ti consente di scaricare ed elaborare messaggi di testo da un account esterno.

## Properties {#properties}

![](assets/sms_rec_edit.png)

La prima scheda della **SMS in entrata** activity ti consente di immettere i parametri di indirizzamento per i messaggi SMS e lo script da eseguire alla ricezione di ogni messaggio. La seconda scheda ti consente di assegnare una pianificazione all’attività e la terza definisce le condizioni di scadenza dell’attività.

1. **[!UICONTROL SMS routing]**: Seleziona l’account esterno da utilizzare per il recupero SMS. Gli account esterni sono configurati tramite il **[!UICONTROL Administration > Platform > External accounts]** nodo dell&#39;albero.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

La **[!UICONTROL Script]**, **[!UICONTROL Schedule]** e **[!UICONTROL Expiry]** le schede sono descritte in [E-mail in entrata](inbound-emails.md).
