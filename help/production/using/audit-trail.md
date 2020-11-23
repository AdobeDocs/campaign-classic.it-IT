---
solution: Campaign Classic
product: campaign
title: Audit trail
description: Audit trail
audience: production
content-type: reference
topic-tags: production-procedures
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 3%

---


# Audit trail{#audit-trail}

In  Adobe Campaign, **[!UICONTROL Audit trail]** è possibile accedere alla cronologia completa delle modifiche apportate all’interno dell’istanza.

**[!UICONTROL Audit trail]** acquisisce, in tempo reale, un elenco completo delle azioni e degli eventi che si verificano all’interno dell’istanza di Adobe Campaign . Include un modo self-service per accedere alla cronologia dei dati e rispondere a domande come: che cosa è accaduto ai flussi di lavoro e chi li ha aggiornati per ultimo o che cosa hanno fatto gli utenti nell’istanza.

>[!NOTE]
>
> Adobe Campaign non sta verificando le modifiche apportate all&#39;interno di diritti utente, modelli, personalizzazione o campagne.\
>La traccia di controllo può essere gestita solo dagli amministratori dell&#39;istanza.

Audit Trail è costituito da tre componenti:

* **Percorso** di controllo dello schema: Controlla le attività e le ultime modifiche apportate agli schemi.

   For more information on schemas, refer to this [page](../../configuration/using/data-schemas.md).

* **Percorso** controllo flusso di lavoro: Controlla le attività e le ultime modifiche apportate ai flussi di lavoro e, inoltre, lo stato dei flussi di lavoro, come:

   * Inizio
   * Pausa
   * Interruzione
   * Riavvio
   * Pulizia uguale alla cronologia di rimozione azione
   * Simulare un valore uguale all’azione Inizio in modalità di simulazione
   * Riattivazione pari all&#39;azione Esegui le attività in sospeso ora
   * Arresto totale

   For more information on workflows, refer to this [page](../../workflow/using/about-workflows.md).

   Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta la sezione [](../../workflow/using/monitoring-workflow-execution.md)dedicata.

* **Percorso** controllo opzione: Controlla le attività e le ultime modifiche apportate alle opzioni.

   For more information on options, refer to this [page](../../installation/using/configuring-campaign-options.md).

## Accesso alla traccia di controllo {#accessing-audit-trail}

Per accedere all&#39;istanza **[!UICONTROL Audit trail]** :

1. Accedere al **[!UICONTROL Explorer]** menu dell&#39;istanza.
1. Nel **[!UICONTROL Administration]** menu, selezionare **[!UICONTROL Audit]** .

   ![](assets/audit_trail_1.png)

1. Viene visualizzata **[!UICONTROL Audit trail]** la finestra con l&#39;elenco delle entità.  Adobe Campaign controllerà le azioni di creazione, modifica ed eliminazione per flussi di lavoro, opzioni e schemi.

   Selezionate una delle entità per ulteriori informazioni sulle ultime modifiche.

   ![](assets/audit_trail_2.png)

1. La **[!UICONTROL Audit entity]** finestra fornisce informazioni più dettagliate sull&#39;entità scelta, ad esempio:

   * **[!UICONTROL Type]** : Flusso di lavoro, Opzioni o Schemi.
   * **[!UICONTROL Entity]** : Nome interno delle attività.
   * **[!UICONTROL Modified by]** : Nome utente dell&#39;ultima persona che ha modificato l&#39;entità.
   * **[!UICONTROL Action]** : Ultima azione eseguita su questa entità, Creata, Modificata o Eliminata.
   * **[!UICONTROL Modification date]** : Data dell&#39;ultima azione eseguita su questa entità.

   Il blocco di codice fornisce ulteriori informazioni sulle modifiche apportate esattamente nell&#39;entità.

   ![](assets/audit_trail_3.png)

>[!NOTE]
>
>Per impostazione predefinita, il periodo di mantenimento è impostato su 180 giorni per **[!UICONTROL Audit logs]** . Per ulteriori informazioni su come modificare il periodo di mantenimento, fare riferimento a questa [pagina](../../production/using/database-cleanup-workflow.md#deployment-wizard).

## Abilita/disabilita traccia di controllo {#enable-disable-audit-trail}

La traccia di controllo può essere facilmente attivata o disattivata per una specifica attività se, ad esempio, si desidera risparmiare spazio sul database.

Per eseguire questa operazione:

1. Accedere al **[!UICONTROL Explorer]** menu dell&#39;istanza.
1. Nel **[!UICONTROL Administration]** menu, selezionare **[!UICONTROL Platform]** quindi **[!UICONTROL Options]** .

   ![](assets/audit_trail_4.png)

1. Selezionate una delle seguenti opzioni a seconda dell&#39;entità da attivare/disattivare:

   * Per il flusso di lavoro: **[!UICONTROL XtkAudit_Workflows]**
   * Per gli schemi: **[!UICONTROL XtkAudit_DataSchema]**
   * Per le opzioni: **[!UICONTROL XtkAudit_Option]**
   * Per ogni entità: **[!UICONTROL XtkAudit_Enable_All]**

   ![](assets/audit_trail_5.png)

1. Modificate il valore **[!UICONTROL Value]** su 1 se desiderate abilitare l&#39;entità o su 0 se desiderate disattivarla.

   ![](assets/audit_trail_6.png)

1. Fai clic su **[!UICONTROL Save]** .

