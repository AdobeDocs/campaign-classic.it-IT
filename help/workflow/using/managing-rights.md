---
solution: Campaign Classic
product: campaign
title: Gestione delle autorizzazioni
description: Gestione delle autorizzazioni
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 1%

---


# Gestione delle autorizzazioni{#managing-rights}

Se non si tratta di amministratori,  operatori Adobe Campaign devono disporre dei diritti di accesso per creare, eseguire o modificare i flussi di lavoro.

In generale, gli operatori che agiscono sui flussi di lavoro devono accedere ai file contenenti i dati utilizzati durante le varie attività (destinatari, elenco destinatari, iscrizioni, consegne, ecc.) ed eventualmente ai relativi file secondari.

Devono inoltre essere mappati sui diritti denominati che coincidono con le azioni eseguite dai flussi di lavoro che avranno effetto (importazione dei destinatari, accesso ai file, fusione, esecuzione di script SQL, ecc.).

Per ulteriori informazioni sulla gestione di operatori e autorizzazioni, consultare la sezione [](../../platform/using/access-management.md).

## Gruppi di operatori {#operator-groups}

I seguenti gruppi di operatori sono associati al flusso di lavoro:

* Il gruppo **[!UICONTROL Workflow execution]** consente di controllare l&#39;esecuzione e l&#39;approvazione dei flussi di lavoro di targeting: il FLUSSO di lavoro denominato right è mappato agli operatori di questo gruppo. È richiesto per tutte le azioni sui flussi di lavoro, oltre ai diritti di accesso ai file di dati. Per impostazione predefinita, il gruppo **[!UICONTROL Workflow execution]** dispone dell&#39;accesso in sola lettura ai file di flusso di lavoro di targeting standard e ai modelli di flusso di lavoro. Gli operatori di questo gruppo dispongono inoltre dell&#39;accesso in lettura e scrittura al file di approvazione in sospeso.
* Il gruppo **[!UICONTROL Workflow supervisors]** consente agli operatori di gestire le approvazioni dei flussi di lavoro.
* Il gruppo **[!UICONTROL Operation Managers]** per accedere ai flussi di lavoro delle campagne.

## Diritti denominati {#named-rights}

Solo il FLUSSO di lavoro denominato right è specifico dei flussi di lavoro: consente di creare, avviare e interrompere flussi di lavoro. I diritti di lettura nel file del flusso di lavoro sono necessari per l&#39;applicazione del diritto denominato. Per i flussi di lavoro di targeting, è necessario leggere il file **[!UICONTROL Profiles and Targets]**.

## Account di esecuzione del flusso di lavoro {#workflow-execution-account}

Potete configurare l&#39;account di esecuzione da utilizzare a livello di modello di workflow. L&#39;account di esecuzione consente di mappare direttamente le autorizzazioni al flusso di lavoro, indipendentemente dall&#39;operatore Adobe Campaign  che avvia l&#39;esecuzione. Per impostazione predefinita, ogni flusso di lavoro viene eseguito con i diritti dell&#39;operatore che l&#39;ha avviato.

Per mappare un account di esecuzione a un flusso di lavoro, andate all&#39;elenco dei modelli di workflow e fate clic con il pulsante destro del mouse sul modello collegato al flusso di lavoro. Scegliere **[!UICONTROL Action > Change execution account...]**, quindi selezionare l&#39;account da utilizzare.
