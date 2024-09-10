---
product: campaign
title: Audit trail
description: Scopri come monitorare l’istanza con Campaign Audit trail
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 2%

---

# Audit trail{#audit-trail}



In Adobe Campaign, **[!UICONTROL Audit trail]** consente di accedere alla cronologia completa delle modifiche apportate all&#39;interno dell&#39;istanza.

**[!UICONTROL Audit trail]** acquisisce in tempo reale un elenco completo delle azioni e degli eventi che si verificano nell&#39;istanza Adobe Campaign. Include una modalità autonoma di accedere alla cronologia dei dati per poter rispondere a domande quali: cosa è successo ai flussi di lavoro e chi li ha aggiornati per ultimo o cosa hanno fatto gli utenti nell’istanza.

>[!NOTE]
>
>Adobe Campaign non controlla le modifiche apportate all’interno di diritti utente, modelli, personalizzazioni o campagne.\
>L’audit trail può essere gestito solo dagli amministratori dell’istanza.

Audit Trail è costituito da tre componenti:

* **Audit trail dello schema**: controlla le attività e le ultime modifiche apportate agli schemi.

  Per ulteriori informazioni sugli schemi, consulta questa [pagina](../../configuration/using/data-schemas.md).

* **Audit trail del flusso di lavoro**: controlla le attività e le ultime modifiche apportate ai flussi di lavoro e, inoltre, lo stato dei flussi di lavoro, ad esempio:

   * Inizio
   * Pausa
   * Interruzione
   * Riavvio
   * Pulizia uguale all’azione Cancella cronologia
   * Simula, che è uguale all’azione Avvia in modalità simulazione
   * Attivazione uguale all&#39;azione Esegui attività in sospeso ora
   * Arresto totale

  Per ulteriori informazioni sui flussi di lavoro, consulta questa [pagina](../../workflow/using/about-workflows.md).

  Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta la [sezione dedicata](../../workflow/using/monitoring-workflow-execution.md).

* **Option audit trail**: controlla le attività e le ultime modifiche apportate alle opzioni.

  Per ulteriori informazioni sulle opzioni, consulta questa [pagina](../../installation/using/configuring-campaign-options.md).

## Accesso a Audit trail {#accessing-audit-trail}

Per accedere a **[!UICONTROL Audit trail]** dell&#39;istanza:

1. Accedi al menu **[!UICONTROL Explorer]** della tua istanza.
1. Nel menu **[!UICONTROL Administration]**, selezionare **[!UICONTROL Audit]**.

   ![](assets/audit_trail_1.png)

1. Viene visualizzata la finestra **[!UICONTROL Audit trail]** con l&#39;elenco delle entità. Adobe Campaign controllerà le azioni di creazione, modifica ed eliminazione per flussi di lavoro, opzioni e schemi.

   Selezionate una delle entità per ulteriori informazioni sulle ultime modifiche.

   ![](assets/audit_trail_2.png)

1. La finestra **[!UICONTROL Audit entity]** fornisce informazioni più dettagliate sull&#39;entità scelta, ad esempio:

   * **[!UICONTROL Type]**: flusso di lavoro, opzioni o schemi.
   * **[!UICONTROL Entity]**: nome interno delle attività.
   * **[!UICONTROL Modified by]**: nome utente dell&#39;ultima persona che ha modificato l&#39;entità.
   * **[!UICONTROL Action]** : ultima azione eseguita sull&#39;entità, Creata, Modificata o Eliminata.
   * **[!UICONTROL Modification date]** : data dell&#39;ultima azione eseguita su questa entità.

   Il blocco di codice fornisce ulteriori informazioni su ciò che è stato modificato esattamente nell’entità.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Per impostazione predefinita, il periodo di conservazione è impostato su 180 giorni per **[!UICONTROL Audit logs]**. Per ulteriori informazioni su come modificare il periodo di conservazione, consulta questa [pagina](../../production/using/database-cleanup-workflow.md#deployment-assistant).

## Attiva/disattiva Audit trail {#enable-disable-audit-trail}

L’audit trail può essere facilmente attivato o disattivato per un’attività specifica se, ad esempio, si desidera risparmiare spazio nel database.

Per eseguire questa operazione:

1. Accedi al menu **[!UICONTROL Explorer]** della tua istanza.
1. Nel menu **[!UICONTROL Administration]**, selezionare **[!UICONTROL Platform]** e quindi **[!UICONTROL Options]**.

   ![](assets/audit_trail_4.png)

1. Selezionate una delle seguenti opzioni a seconda dell&#39;entità da attivare/disattivare:

   * Per il flusso di lavoro: **[!UICONTROL XtkAudit_Workflows]**
   * Per gli schemi: **[!UICONTROL XtkAudit_DataSchema]**
   * Per le opzioni: **[!UICONTROL XtkAudit_Option]**
   * Per ogni entità: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Modificare **[!UICONTROL Value]** in 1 se si desidera abilitare l&#39;entità o in 0 se si desidera disabilitarla.

   ![](assets/audit_trail_6.png)

1. Fare clic su **[!UICONTROL Save]**.
