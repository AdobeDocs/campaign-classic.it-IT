---
product: campaign
title: Aggiornamenti dei dati
description: Aggiornamenti dei dati
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 2%

---

# Attività Update data{#updating-data}

![](../../assets/common.svg)

I dati collegati al profilo di un destinatario possono essere aggiornati manualmente o automaticamente.

## Imposta un aggiornamento automatico {#setting-up-an-automatic-update}

Un aggiornamento automatico può essere configurato tramite un flusso di lavoro. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/update-data.md).

## Eseguire un aggiornamento di massa {#performing-a-mass-update}

Per eseguire aggiornamenti manuali, fai clic con il pulsante destro del mouse sui destinatari selezionati per utilizzare il menu di scelta rapida **[!UICONTROL Actions]** o utilizza l&#39;icona **[!UICONTROL Actions]**.

![](assets/s_ncs_user_action_icon.png)

Esistono due tipi di aggiornamenti: aggiornamento di massa per un set di destinatari e unione dei dati tra due profili. Per ogni azione, una procedura guidata consente di configurare l’aggiornamento.

### Aggiornamento di massa {#mass-update}

Per l&#39;aggiornamento di massa, utilizzare **[!UICONTROL Action > Mass update of selected lines...]**. La procedura guidata consente di configurare ed eseguire l’aggiornamento.

Il primo passaggio della procedura guidata consiste nel specificare i campi da aggiornare.

Nella sezione a sinistra della procedura guidata viene visualizzato l’elenco dei campi disponibili. Utilizza il campo **[!UICONTROL Find]** per eseguire una ricerca in questi campi. Premere il tasto **Enter** per sfogliare l&#39;elenco. I nomi dei campi corrispondenti alla voce vengono visualizzati in grassetto, come illustrato di seguito.

Fai doppio clic sui campi da aggiornare per visualizzarli nella sezione a destra della procedura guidata.

![](assets/s_ncs_user_update_wizard01_1.png)

In caso di errore, utilizza il pulsante **[!UICONTROL Delete]** per eliminare un campo dall’elenco dei campi da aggiornare.

Seleziona o immetti i valori da applicare ai profili da aggiornare.

![](assets/s_ncs_user_update_wizard01_12.png)

Puoi fare clic su **[!UICONTROL Distribution of values]** per visualizzare la distribuzione dei valori del campo selezionato per i destinatari presenti nella cartella corrente (non solo per i destinatari interessati dall’aggiornamento).

![](assets/s_ncs_user_update_wizard01_2.png)

È possibile definire filtri per visualizzare la distribuzione dei valori in questa finestra o modificare la cartella corrente per visualizzare la distribuzione dei valori in un&#39;altra cartella. Si tratta di azioni di sola lettura; non influiscono sulla configurazione dell’aggiornamento in fase di definizione.

![](assets/s_ncs_user_update_wizard01_3.png)

Chiudi questa finestra e fai clic su **[!UICONTROL Next]** per visualizzare il secondo passaggio della procedura guidata di aggiornamento. In questo passaggio, puoi avviare l&#39;aggiornamento facendo clic su **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

Le informazioni relative all’esecuzione dell’aggiornamento vengono visualizzate nella sezione superiore della procedura guidata.

Il **[!UICONTROL Stop]** consente di annullare l&#39;aggiornamento, ma alcuni record potrebbero essere stati aggiornati e l&#39;arresto del processo non annullerà questi aggiornamenti. La barra di avanzamento mostra lo stato di avanzamento dell’operazione.

### Unisci dati {#merge-data}

Seleziona **[!UICONTROL Merge selected lines...]** per avviare l’unione di due profili destinatario. I profili da unire devono essere selezionati prima di selezionare l’opzione . L&#39;unione viene configurata e avviata utilizzando una procedura guidata.

La procedura guidata visualizza i valori da recuperare per ogni campo completato in uno o più dei profili di origine. Se uno o più campi dei profili da unire hanno valori diversi, vengono visualizzati nella sezione **[!UICONTROL List of conflicts]** . Puoi quindi selezionare il profilo predefinito utilizzando i pulsanti di scelta sotto l’elenco, come nell’esempio seguente:

![](assets/s_ncs_user_merge_wizard01_1.png)

Fai clic su **[!UICONTROL Compute]** per visualizzare il risultato desiderato.

![](assets/s_ncs_user_merge_wizard01_2.png)

Controllare le colonne **[!UICONTROL Result]** di entrambe le sezioni della finestra e fare clic su **[!UICONTROL Finish]** per eseguire l&#39;unione.

## Esportare i dati {#exporting-data}

È possibile esportare il contenuto di un elenco. Per configurare ed eseguire l’esportazione:

1. Selezionare i record da esportare.
1. Fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. Quindi seleziona i dati da estrarre. Per impostazione predefinita, tutte le colonne visualizzate vengono aggiunte alle colonne di output.

   ![](assets/s_ncs_user_export_list_start.png)

   Per ulteriori informazioni su come configurare la procedura guidata di esportazione, consulta [questa sezione](../../platform/using/executing-export-jobs.md).

## Iscriviti a un servizio {#subscribing-to-a-service}

Nella maggior parte dei casi, i destinatari si abbonano a una newsletter tramite una pagina di destinazione dedicata, come spiegato in [questa sezione](../../delivery/using/managing-subscriptions.md). Tuttavia, i profili dei destinatari filtrati possono essere abbonati manualmente a un servizio (newsletter o servizio virtuale). Per eseguire questa operazione:

1. Seleziona i destinatari che desideri sottoscrivere e fai clic con il pulsante destro del mouse su di essi.
1. Seleziona **[!UICONTROL Actions > Subscribe selection to a service]**.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Seleziona il servizio desiderato e fai clic su **[!UICONTROL Next]**:

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >Questo editor consente di creare un nuovo servizio: fare clic sul pulsante **[!UICONTROL Create]** .

1. Puoi **[!UICONTROL Send a confirmation message]** ai destinatari. Il contenuto di questo messaggio può essere configurato nello scenario di abbonamento collegato al servizio selezionato.
1. Fai clic sul pulsante **[!UICONTROL Start]** per eseguire il processo di abbonamento.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

La sezione superiore della finestra consente di monitorare il processo di esecuzione. Il pulsante **[!UICONTROL Stop]** ti consente di interrompere il processo. Tuttavia, i destinatari già elaborati verranno sottoscritti.

Deselezionando l’opzione **[!UICONTROL Do not keep a trace of this job in the database]**, puoi selezionare (o creare) la cartella di esecuzione in cui verranno memorizzate le informazioni sul processo.

Per verificare il processo, vai alla scheda **[!UICONTROL Subscriptions]** sui profili dei destinatari interessati dall’operazione o alla scheda **[!UICONTROL Subscriptions]** accessibile tramite il nodo **[!UICONTROL Profiles and Targets > Services and Subscriptions]** .

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione e la configurazione di servizi di informazione, consulta [questa pagina](../../delivery/using/managing-subscriptions.md).
