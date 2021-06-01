---
product: campaign
title: Audit trail
description: Audit trail
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 8508d879-fb38-4b1f-9f55-0341bb8d0c67
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---

# Audit trail{#audit-trail}

In Adobe Campaign, la sezione **[!UICONTROL Audit trail]** ti consente di accedere alla cronologia completa delle modifiche apportate all’interno dell’istanza.

**[!UICONTROL Audit trail]** acquisisce in tempo reale un elenco completo delle azioni e degli eventi che si verificano all’interno della tua istanza Adobe Campaign. Include un modo self-service per accedere alla cronologia dei dati e rispondere a domande quali: cosa è successo ai flussi di lavoro e chi li ha aggiornati per ultimo o cosa hanno fatto i tuoi utenti nell’istanza.

>[!NOTE]
>
>Adobe Campaign non controlla le modifiche apportate ai diritti utente, ai modelli, alla personalizzazione o alle campagne.\
>L’audit trail può essere gestito solo dagli amministratori dell’istanza.

Audit Trail è costituito da tre componenti:

* **Audit trail** dello schema: Controlla le attività e le ultime modifiche apportate agli schemi.

   Per ulteriori informazioni sugli schemi, consulta questa [pagina](../../configuration/using/data-schemas.md).

* **Audit trail** del flusso di lavoro: Controlla le attività e le ultime modifiche apportate ai flussi di lavoro e, inoltre, lo stato dei flussi di lavoro, come:

   * Inizio
   * Pausa
   * Interruzione
   * Riavvio
   * Pulizia uguale alla cronologia di eliminazione dell&#39;azione
   * Simula ciò che è uguale all&#39;azione Inizio in modalità di simulazione
   * Riattivazione uguale all&#39;azione Esegui subito le attività in sospeso
   * Arresto totale

   Per ulteriori informazioni sui flussi di lavoro, consulta questa [pagina](../../workflow/using/about-workflows.md).

   Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta la sezione [dedicata](../../workflow/using/monitoring-workflow-execution.md).

* **Percorso di controllo** opzione: Controlla le attività e le ultime modifiche apportate alle opzioni.

   Per ulteriori informazioni sulle opzioni, consulta questa [pagina](../../installation/using/configuring-campaign-options.md).

## Accesso a Audit trail {#accessing-audit-trail}

Per accedere al **[!UICONTROL Audit trail]** dell’istanza :

1. Accedi al menu **[!UICONTROL Explorer]** della tua istanza.
1. Nel menu **[!UICONTROL Administration]** , seleziona **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. Viene visualizzata la finestra **[!UICONTROL Audit trail]** con l’elenco delle entità. Adobe Campaign controllerà le azioni di creazione, modifica ed eliminazione per flussi di lavoro, opzioni e schemi.

   Seleziona una delle entità per ulteriori informazioni sulle ultime modifiche.

   ![](assets/audit_trail_2.png)

1. La finestra **[!UICONTROL Audit entity]** fornisce informazioni più dettagliate sull’entità selezionata, ad esempio:

   * **[!UICONTROL Type]** : Flusso di lavoro, opzioni o schemi.
   * **[!UICONTROL Entity]** : Nome interno delle attività.
   * **[!UICONTROL Modified by]** : Nome utente dell’ultima persona che ha modificato l’entità.
   * **[!UICONTROL Action]** : Ultima azione eseguita su questa entità, Creata, Modificata o Eliminata.
   * **[!UICONTROL Modification date]** : Data dell’ultima azione eseguita su questa entità.

   Il blocco di codice fornisce ulteriori informazioni sulle modifiche apportate esattamente nell’entità.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Per impostazione predefinita, il periodo di conservazione è impostato su 180 giorni per **[!UICONTROL Audit logs]** . Per ulteriori informazioni su come modificare il periodo di conservazione, consulta questa [pagina](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Attiva/disattiva traccia di audit {#enable-disable-audit-trail}

L&#39;audit trail può essere facilmente attivato o disattivato per una specifica attività se, ad esempio, si desidera risparmiare spazio sul database.

Per eseguire questa operazione:

1. Accedi al menu **[!UICONTROL Explorer]** della tua istanza.
1. Nel menu **[!UICONTROL Administration]** , seleziona **[!UICONTROL Platform]** , quindi **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Seleziona una delle seguenti opzioni a seconda dell’entità da attivare/disattivare:

   * Per Flusso di lavoro: **[!UICONTROL XtkAudit_Workflows]**
   * Per gli schemi: **[!UICONTROL XtkAudit_DataSchema]**
   * Per le opzioni: **[!UICONTROL XtkAudit_Option]**
   * Per ogni entità: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Cambia l’ **[!UICONTROL Value]** in 1 se desideri abilitare l’entità o in 0 se desideri disattivarla.

   ![](assets/audit_trail_6.png)

1. Fai clic su **[!UICONTROL Save]** .
