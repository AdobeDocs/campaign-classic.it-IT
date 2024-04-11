---
product: campaign
title: Audit trail
description: Scopri come monitorare l’istanza con Campaign Audit trail
feature: Audit Trail, Monitoring, Workflows
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 2%

---

# Audit trail{#audit-trail}



In Adobe Campaign, il **[!UICONTROL Audit trail]** consente di accedere alla cronologia completa delle modifiche apportate all’interno dell’istanza.

**[!UICONTROL Audit trail]** acquisisce in tempo reale un elenco completo delle azioni e degli eventi che si verificano all’interno dell’istanza di Adobe Campaign. Include una modalità autonoma di accedere alla cronologia dei dati per poter rispondere a domande quali: cosa è successo ai flussi di lavoro e chi li ha aggiornati per ultimo o cosa hanno fatto gli utenti nell’istanza.

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

  Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta [sezione dedicata](../../workflow/using/monitoring-workflow-execution.md).

* **Opzione audit trail**: controlla le attività e le ultime modifiche apportate alle opzioni.

  Per ulteriori informazioni sulle opzioni, consulta questa [pagina](../../installation/using/configuring-campaign-options.md).

## Accesso a Audit trail {#accessing-audit-trail}

Per accedere al di **[!UICONTROL Audit trail]** :

1. Accedere a **[!UICONTROL Explorer]** della tua istanza.
1. Sotto **[!UICONTROL Administration]** menu, seleziona **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. Il **[!UICONTROL Audit trail]** viene visualizzata la finestra con l&#39;elenco delle entità. Adobe Campaign controllerà le azioni di creazione, modifica ed eliminazione per flussi di lavoro, opzioni e schemi.

   Selezionate una delle entità per ulteriori informazioni sulle ultime modifiche.

   ![](assets/audit_trail_2.png)

1. Il **[!UICONTROL Audit entity]** La finestra fornisce informazioni più dettagliate sull’entità scelta, ad esempio:

   * **[!UICONTROL Type]** : flusso di lavoro, opzioni o schemi.
   * **[!UICONTROL Entity]** : nome interno delle attività.
   * **[!UICONTROL Modified by]** : nome utente dell’ultima persona che ha modificato questa entità.
   * **[!UICONTROL Action]** : ultima azione eseguita sull’entità, Creata, Modificata o Eliminata.
   * **[!UICONTROL Modification date]** : data dell’ultima azione eseguita su questa entità.

   Il blocco di codice fornisce ulteriori informazioni su ciò che è stato modificato esattamente nell’entità.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Per impostazione predefinita, il periodo di conservazione è impostato su 180 giorni per **[!UICONTROL Audit logs]** . Per ulteriori informazioni su come modificare il periodo di conservazione, consulta [pagina](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Attiva/disattiva Audit trail {#enable-disable-audit-trail}

L’audit trail può essere facilmente attivato o disattivato per un’attività specifica se, ad esempio, si desidera risparmiare spazio nel database.

Per eseguire questa operazione:

1. Accedere a **[!UICONTROL Explorer]** della tua istanza.
1. Sotto **[!UICONTROL Administration]** menu, seleziona **[!UICONTROL Platform]** allora **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Selezionate una delle seguenti opzioni a seconda dell&#39;entità da attivare/disattivare:

   * Per il flusso di lavoro: **[!UICONTROL XtkAudit_Workflows]**
   * Per gli schemi: **[!UICONTROL XtkAudit_DataSchema]**
   * Per le opzioni: **[!UICONTROL XtkAudit_Option]**
   * Per ogni entità: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Modificare il **[!UICONTROL Value]** a 1 se si desidera abilitare l’entità o a 0 se si desidera disabilitarla.

   ![](assets/audit_trail_6.png)

1. Clic **[!UICONTROL Save]** .
