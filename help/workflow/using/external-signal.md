---
title: Segnale esterno
seo-title: Segnale esterno
description: Segnale esterno
seo-description: null
page-status-flag: never-activated
uuid: dbe6624a-70cf-4ac4-adfd-bc72db9bb3f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 3739593f-056c-4165-87ef-63c812bd3c43
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b369a17fabc55607fc6751e7909e1a1cb3cd4201
workflow-type: tm+mt
source-wordcount: '164'
ht-degree: 4%

---


# Segnale esterno{#external-signal}

L&#39;attività **Segnale** esterno consente di attivare l&#39;esecuzione di un insieme di attività in un flusso di lavoro per una pianificazione.

Quando un&#39;attività &quot;Segnale esterno&quot; viene attivata, viene messa in pausa indefinitamente o fino alla fine del periodo di tempo specificato. La sua transizione è attivata dalla chiamata SOAP **PostEvent(sessionToken, workflowId, attività, transizione, parametri, complete).** Il **[!UICONTROL complete]** parametro consente di completare l’attività, pertanto non reagisce alle chiamate successive.

Per ulteriori informazioni sulla funzione PostEvent, fare riferimento alla documentazione online relativa alle chiamate SOAP.

Puoi configurare questa attività per definire gli eventi in caso di mancata ricezione di segnali. A questo scopo, modificate l&#39;attività e fate clic sulla **[!UICONTROL Expiration]** scheda. Fate clic sul **[!UICONTROL Insert]** pulsante per creare e configurare un evento.

![](assets/edit_signal.png)

La configurazione delle scadenze è dettagliata in [Scadenze](../../workflow/using/defining-approvals.md).

Il campo **Ritardo** consente di specificare un ritardo di scadenza nelle unità di scelta. Vedi [Aspetta](../../workflow/using/wait.md).

Ogni riga rappresenta un tipo di scadenza e coincide con una transizione.

![](assets/external_sign_diag.png)

