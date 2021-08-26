---
product: campaign
title: Gestione delle autorizzazioni del flusso di lavoro
description: Scopri come gestire le autorizzazioni del flusso di lavoro
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 88995fb3-d336-4355-acd4-33118dd0e2b0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Gestione delle autorizzazioni del flusso di lavoro{#managing-rights}

![](../../assets/common.svg)

Se non sono amministratori, gli operatori Adobe Campaign devono disporre dei diritti di accesso per creare, eseguire o modificare i flussi di lavoro.

In generale, gli operatori che agiscono sui flussi di lavoro devono accedere ai file contenenti i dati utilizzati durante le varie attività (destinatari, elenco destinatari, abbonamenti, consegne, ecc.) ed eventualmente ai relativi sottofile.

Devono anche essere mappati ai diritti denominati che coincidono con le azioni eseguite dai flussi di lavoro che influiranno (importazione dei destinatari, accesso ai file, fusione, esecuzione degli script SQL, ecc.).

Per ulteriori informazioni sulla gestione di operatori e autorizzazioni, consulta questa [sezione](../../platform/using/access-management.md).

## Gruppi di operatori {#operator-groups-wf}

I seguenti gruppi di operatori sono associati al flusso di lavoro:

* Il gruppo **[!UICONTROL Workflow execution]** ti consente di controllare l’esecuzione e l’approvazione dei flussi di lavoro di targeting: il WORKFLOW denominato right è mappato sugli operatori di questo gruppo. È richiesto per tutte le azioni sui flussi di lavoro, oltre ad accedere ai diritti ai file di dati. Per impostazione predefinita, il gruppo **[!UICONTROL Workflow execution]** ha accesso in sola lettura ai file di flusso di lavoro di targeting standard e ai modelli di flusso di lavoro. Gli operatori di questo gruppo hanno anche accesso in lettura e scrittura al file di approvazione in sospeso.
* Il gruppo **[!UICONTROL Workflow supervisors]** consente agli operatori di gestire le approvazioni del flusso di lavoro.
* Il gruppo **[!UICONTROL Operation Managers]** per accedere ai flussi di lavoro delle campagne.

## Diritti denominati {#named-rights}

Solo il flusso di lavoro denominato a destra è specifico per i flussi di lavoro: consente di creare, avviare e interrompere i flussi di lavoro. I diritti di lettura sul file del flusso di lavoro sono necessari perché sia applicabile il diritto denominato . Per i flussi di lavoro di targeting, è necessaria la lettura a destra del file **[!UICONTROL Profiles and Targets]** .

## Account di esecuzione del flusso di lavoro {#workflow-execution-account}

Puoi configurare l’account di esecuzione da utilizzare a livello di modello di flusso di lavoro. L’account di esecuzione ti consente di mappare direttamente le autorizzazioni al flusso di lavoro, indipendentemente dall’operatore Adobe Campaign che avvia l’esecuzione. Per impostazione predefinita, ogni flusso di lavoro viene eseguito con i diritti dell’operatore che lo ha avviato.

Per mappare un account di esecuzione a un flusso di lavoro, passa all’elenco dei modelli di flusso di lavoro e fai clic con il pulsante destro del mouse sul modello collegato al flusso di lavoro. Scegli **[!UICONTROL Action > Change execution account...]** , quindi seleziona l’account da utilizzare.
