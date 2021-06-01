---
product: campaign
title: Attività External signal
description: Ulteriori informazioni sull’attività del flusso di lavoro del segnale esterno
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# External signal{#external-signal}

L’attività **External signal** ti consente di attivare l’esecuzione di un set di attività in un flusso di lavoro per una pianificazione.

Quando un&#39;attività &quot;External signal&quot; viene attivata, viene messa in pausa indefinitamente o fino alla fine del periodo di tempo specificato. La sua transizione è attivata dalla chiamata SOAP **PostEvent(sessionToken, workflowId, attività, transizione, parametri, complete).** Il  **[!UICONTROL complete]** parametro consente di completare l’attività, pertanto non reagisce alle chiamate successive.

Fare riferimento alla documentazione online relativa alle chiamate SOAP per ulteriori informazioni sulla funzione PostEvent.

Puoi configurare questa attività per definire gli eventi se non viene ricevuto alcun segnale. A questo scopo, modifica l’attività e fai clic sulla scheda **[!UICONTROL Expiration]** . Fai clic sul pulsante **[!UICONTROL Insert]** per creare e configurare un evento.

![](assets/edit_signal.png)

La configurazione delle scadenze è descritta in [Scadenze](../../workflow/using/defining-approvals.md).

Il campo **Ritardo** consente di specificare un ritardo di scadenza nelle unità scelte. Vedere [Wait](../../workflow/using/wait.md) .

Ogni riga rappresenta un tipo di scadenza e coincide con una transizione.

![](assets/external_sign_diag.png)
