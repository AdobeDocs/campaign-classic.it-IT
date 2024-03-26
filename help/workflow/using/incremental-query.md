---
product: campaign
title: Query incrementale
description: Ulteriori informazioni sull’attività del flusso di lavoro Incremental query
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: abc08232-1a92-41e8-90f1-02e0a673539b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 5%

---

# Query incrementale{#incremental-query}



Una query incrementale consente di selezionare periodicamente un target in base a un criterio, escludendo le persone già interessate da questo criterio.

La popolazione già sottoposta a targeting viene memorizzata per istanza di flusso di lavoro e per attività, ovvero due flussi di lavoro avviati dallo stesso modello non condividono lo stesso registro. D’altra parte, due attività basate sulla stessa query incrementale per la stessa istanza di flusso di lavoro utilizzeranno lo stesso registro.

La query viene definita nello stesso modo delle query standard, ma la sua esecuzione è pianificata.

**Argomenti correlati:**

* [Caso d’uso: aggiornamento dell’elenco trimestrale tramite una query incrementale](quarterly-list-update.md)
* [Creazione di una query](query.md#creating-a-query)

>[!CAUTION]
>
>Se il risultato di una query incrementale è uguale a **0** durante una delle esecuzioni, il flusso di lavoro viene sospeso fino alla successiva esecuzione programmata della query. Le transizioni e le attività che seguono la query incrementale non vengono quindi elaborate prima dell’esecuzione successiva.

Per eseguire questa operazione:

1. In **[!UICONTROL Scheduling & History]** , seleziona la scheda **[!UICONTROL Schedule execution]** opzione. L&#39;attività rimane attiva dopo la creazione e verrà attivata solo nei momenti specificati dalla pianificazione per l&#39;esecuzione della query. Tuttavia, se l’opzione è disabilitata, la query viene eseguita immediatamente **e in un colpo solo**.
1. Fai clic sul pulsante **[!UICONTROL Change]**.

   In **[!UICONTROL Schedule editing wizard]** è possibile configurare il tipo di frequenza, la ricorrenza degli eventi e il periodo di validità degli eventi.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Clic **[!UICONTROL Finish]** per salvare la pianificazione.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. La sezione inferiore della sezione **[!UICONTROL Scheduling & History]** Questa scheda ti consente di selezionare il numero di giorni da considerare nella cronologia.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

     I destinatari già oggetto di targeting possono essere registrati per un numero massimo di giorni dal giorno in cui sono stati oggetto di targeting. Se questo valore è zero, i destinatari non vengono mai eliminati dal registro.

   * **[!UICONTROL Keep history when starting]**

     Questa opzione consente di non eliminare il registro quando l’attività è abilitata.

   * **[!UICONTROL SQL table name]**

     Questo parametro consente di sovraccaricare la tabella SQL predefinita contenente i dati della cronologia.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo set di tre valori identifica la popolazione target della query. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificativi target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.
