---
product: campaign
title: SMS in entrata
description: Ulteriori informazioni sull’attività del flusso di lavoro SMS in entrata
audience: workflow
content-type: reference
topic-tags: event-activities
exl-id: 94a9d50b-4ead-4815-8d12-942fa78b4e8a
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 4%

---

# SMS in entrata{#inbound-sms}

L’attività **Inbound SMS** ti consente di scaricare ed elaborare messaggi di testo da un account esterno.

## Properties {#properties}

![](assets/sms_rec_edit.png)

La prima scheda dell’attività **Inbound SMS** ti consente di inserire i parametri di indirizzamento per i messaggi SMS e di immettere lo script da eseguire al momento della ricezione di ciascun messaggio. La seconda scheda ti consente di assegnare una pianificazione all’attività e la terza definisce le condizioni di scadenza dell’attività.

1. **[!UICONTROL SMS routing]**: Seleziona l’account esterno da utilizzare per il recupero SMS. Gli account esterni sono configurati tramite il nodo **[!UICONTROL Administration > Platform > External accounts]** della struttura.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

Le schede **[!UICONTROL Script]**, **[!UICONTROL Schedule]** e **[!UICONTROL Expiry]** sono descritte dettagliatamente in [E-mail in entrata](../../workflow/using/inbound-emails.md).
