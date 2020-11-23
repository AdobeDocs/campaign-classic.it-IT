---
solution: Campaign Classic
product: campaign
title: Incremental query
description: Ulteriori informazioni sull'attività del flusso di lavoro query incrementale
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 3%

---


# Incremental query{#incremental-query}

Una query incrementale consente di selezionare periodicamente una destinazione in base a un criterio, escludendo le persone già interessate per questo criterio.

La popolazione già impostata come destinazione viene memorizzata nella memoria per istanza del flusso di lavoro e per attività, ovvero due flussi di lavoro avviati dallo stesso modello non condividono lo stesso registro. D&#39;altro canto, due attività basate sulla stessa query incrementale per la stessa istanza di flusso di lavoro utilizzeranno lo stesso registro.

La query è definita come per le query standard, ma la sua esecuzione è pianificata.

**Argomenti correlati:**

* [Caso di utilizzo: Aggiornamento dell&#39;elenco trimestrale tramite una query incrementale](../../workflow/using/quarterly-list-update.md)
* [Creazione di una query](../../workflow/using/query.md#creating-a-query)

>[!CAUTION]
>
>Se il risultato di una query incrementale è pari a **0** durante una delle sue esecuzioni, il flusso di lavoro viene messo in pausa fino alla successiva esecuzione programmata della query. Le transizioni e le attività che seguono la query incrementale non vengono pertanto elaborate prima dell&#39;esecuzione seguente.

Per eseguire questa operazione:

1. In the **[!UICONTROL Scheduling & History]** tab, select the **[!UICONTROL Schedule execution]** option. L&#39;attività rimane attiva una volta creata e verrà attivata solo nei momenti specificati dalla pianificazione per l&#39;esecuzione della query. Tuttavia, se l&#39;opzione è disabilitata, la query viene eseguita immediatamente **e in una sola volta**.
1. Fai clic sul pulsante **[!UICONTROL Change]**.

   Nella **[!UICONTROL Schedule editing wizard]** finestra potete configurare il tipo di frequenza, ricorrenza evento e periodo di validità dell’evento.

   ![](assets/s_user_segmentation_wizard_11.png)

1. Click **[!UICONTROL Finish]** to save the schedule.

   ![](assets/s_user_segmentation_wizard_valid.png)

1. La sezione inferiore della **[!UICONTROL Scheduling & History]** scheda consente di selezionare il numero di giorni di cui tenere conto nella cronologia.

   ![](assets/edit_request_inc.png)

   * **[!UICONTROL History in days]**

      I destinatari già assegnati al targeting possono essere registrati per un numero massimo di giorni dal giorno in cui sono stati assegnati al targeting. Se questo valore è zero, i destinatari non vengono mai eliminati dal registro.

   * **[!UICONTROL Keep history when starting]**

      Questa opzione consente di non eliminare il registro quando l&#39;attività è abilitata.

   * **[!UICONTROL SQL table name]**

      Questo parametro consente di sovraccaricare la tabella SQL predefinita contenente i dati della cronologia.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica la popolazione oggetto della query. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:destinatario) ed **[!UICONTROL recCount]** è il numero di elementi nella tabella.
