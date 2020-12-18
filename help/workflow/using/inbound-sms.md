---
solution: Campaign Classic
product: campaign
title: SMS in entrata
description: Ulteriori informazioni sull'attività del flusso di lavoro SMS in entrata
audience: workflow
content-type: reference
topic-tags: event-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 4%

---


# SMS in entrata{#inbound-sms}

L&#39;attività **Inbound SMS** consente di scaricare ed elaborare messaggi di testo da un account esterno.

## Properties {#properties}

![](assets/sms_rec_edit.png)

La prima scheda dell&#39;attività **Inbound SMS** consente di inserire i parametri di routing per i messaggi SMS e di inserire lo script da eseguire alla ricezione di ogni messaggio. La seconda scheda consente di assegnare una pianificazione all&#39;attività, mentre la terza scheda definisce le condizioni di scadenza dell&#39;attività.

1. **[!UICONTROL SMS routing]**: Selezionare l&#39;account esterno da utilizzare per il recupero SMS. Gli account esterni sono configurati tramite il nodo **[!UICONTROL Administration > Platform > External accounts]** della struttura.
1. **[!UICONTROL Script]**
1. **[!UICONTROL Schedule]**

   ![](assets/sms_rec_edit_2.png)

1. **[!UICONTROL Expiration]**

Le schede **[!UICONTROL Script]**, **[!UICONTROL Schedule]** e **[!UICONTROL Expiry]** sono descritte in [Inbound Emails](../../workflow/using/inbound-emails.md).
