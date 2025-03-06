---
product: campaign
title: Segnale esterno
description: Ulteriori informazioni sull’attività del flusso di lavoro External signal
feature: Workflows
hide: true
hidefromtoc: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%

---

# Segnale esterno{#external-signal}



L&#39;attività **External signal** consente di attivare l&#39;esecuzione di un set di attività in un flusso di lavoro a una pianificazione.

Quando viene attivata, l&#39;attività &#39;External signal&#39; viene sospesa indefinitamente o fino alla fine del periodo di tempo specificato. La relativa transizione è attivata dalla chiamata SOAP **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** Il parametro **[!UICONTROL complete]** consente il completamento dell&#39;attività, pertanto non reagirà alle chiamate successive.

Per ulteriori informazioni sulla funzione PostEvent, consulta la documentazione online relativa alle chiamate di SOAP.

Puoi configurare questa attività per definire gli eventi se non viene ricevuto alcun segnale. A tale scopo, modificare l&#39;attività e fare clic sulla scheda **[!UICONTROL Expiration]**. Fare clic sul pulsante **[!UICONTROL Insert]** per creare e configurare un evento.

![](assets/edit_signal.png)

La configurazione delle scadenze è descritta in [Scadenze](defining-approvals.md).

Il campo **Ritardo** consente di specificare un ritardo di scadenza nelle unità scelte. Vedi [Attendi](wait.md).

Ogni riga rappresenta un tipo di scadenza e coincide con una transizione.

![](assets/external_sign_diag.png)
