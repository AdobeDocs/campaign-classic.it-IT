---
product: campaign
title: Segnale esterno
description: Ulteriori informazioni sull’attività del flusso di lavoro External signal
feature: Workflows
hide: true
exl-id: da84d3ff-1e64-45ef-bef0-da4a24d93461
TQID: 'https://experienceleague.adobe.com/2fWd7-VtAc2x-MQm-o5rpGmDsrn6rszSfZxjVDzleTw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: ee25c34b-ea50-427b-9369-ba0a160f7d70
    internal-label: HeatMap
  - id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22f
    internal-label: Execution activities
  - id: d1110311-2ca4-442b-be37-088a6db845ee
    internal-label: Data Management activities
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
source-git-commit: 3e213ecc670d5a3cb8299c092ccbb5303858327d
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 2%
---
# Segnale esterno{#external-signal}



L&#39;attività **External signal** consente di attivare l&#39;esecuzione di un set di attività in un flusso di lavoro a una pianificazione.

Quando viene attivata, l&#39;attività &#39;External signal&#39; viene sospesa indefinitamente o fino alla fine del periodo di tempo specificato. La relativa transizione è attivata dalla chiamata SOAP **PostEvent(sessionToken, workflowId, activity, transition, parameters, complete).** Il parametro **[!UICONTROL complete]** consente di completare l&#39;attività, pertanto non reagirà alle chiamate successive.

Per ulteriori informazioni sulla funzione PostEvent, consulta la documentazione online relativa alle chiamate di SOAP.

Puoi configurare questa attività per definire gli eventi se non viene ricevuto alcun segnale. A tale scopo, modificare l&#39;attività e fare clic sulla scheda **[!UICONTROL Expiration]**. Fare clic sul pulsante **[!UICONTROL Insert]** per creare e configurare un evento.

![](assets/edit_signal.png)

La configurazione delle scadenze è descritta in [Scadenze](defining-approvals.md).

Il campo **Ritardo** consente di specificare un ritardo di scadenza nelle unità scelte. Vedi [Attendi](wait.md).

Ogni riga rappresenta un tipo di scadenza e coincide con una transizione.

![](assets/external_sign_diag.png)
