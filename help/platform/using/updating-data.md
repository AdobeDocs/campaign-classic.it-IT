---
product: campaign
title: Aggiornamento dei dati
description: Aggiornamento dei dati
feature: Data Management
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---

# Aggiornare i dati{#updating-data}

>[!NOTE]
>
>Questa pagina si applica solo agli operatori che si connettono a Campaign con autenticazione nativa.

I dati collegati al profilo di un destinatario possono essere aggiornati manualmente o automaticamente.

## Impostare un aggiornamento automatico {#setting-up-an-automatic-update}

Un aggiornamento automatico può essere configurato tramite un flusso di lavoro. Per ulteriori informazioni, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/targeting-activities/update-data.html?lang=it){target="_blank"}.

## Eseguire un aggiornamento di massa {#performing-a-mass-update}

Per eseguire gli aggiornamenti manuali, fare clic con il pulsante destro del mouse sui destinatari selezionati per utilizzare il menu di scelta rapida **[!UICONTROL Actions]** oppure utilizzare l&#39;icona **[!UICONTROL Actions]**.

![](assets/s_ncs_user_action_icon.png)

Esistono due tipi di aggiornamenti: aggiornamento di massa per un set di destinatari e unione di dati tra due profili. Per ogni azione, un assistente ti consente di configurare l’aggiornamento.

### Aggiornamento di massa {#mass-update}

Per l&#39;aggiornamento di massa, utilizzare **[!UICONTROL Action > Mass update of selected lines...]**. L’assistente ti aiuta a configurare ed eseguire l’aggiornamento.

Il primo passaggio dell’assistente consiste nel specificare i campi da aggiornare.

Nella sezione a sinistra dell&#39;assistente viene visualizzato l&#39;elenco dei campi disponibili. Utilizza il campo **[!UICONTROL Find]** per eseguire una ricerca di questi campi. Premere il tasto **Invio** per sfogliare l&#39;elenco. I nomi dei campi corrispondenti alla voce vengono visualizzati in grassetto, come illustrato di seguito.

Fare doppio clic sui campi da aggiornare per visualizzarli nella sezione destra dell&#39;assistente.

![](assets/s_ncs_user_update_wizard01_1.png)

In caso di errore, utilizzare il pulsante **[!UICONTROL Delete]** per eliminare un campo dall&#39;elenco dei campi da aggiornare.

Seleziona o immetti i valori da applicare ai profili da aggiornare.

![](assets/s_ncs_user_update_wizard01_12.png)

È possibile fare clic su **[!UICONTROL Distribution of values]** per visualizzare la distribuzione dei valori del campo selezionato per i destinatari presenti nella cartella corrente (non solo per i destinatari interessati dall&#39;aggiornamento).

![](assets/s_ncs_user_update_wizard01_2.png)

È possibile definire filtri per visualizzare la distribuzione dei valori in questa finestra o modificare la cartella corrente per visualizzare la distribuzione dei valori in un&#39;altra cartella. Si tratta di azioni di sola lettura che non influiscono sulla configurazione dell’aggiornamento da definire.

![](assets/s_ncs_user_update_wizard01_3.png)

Chiudere la finestra e fare clic su **[!UICONTROL Next]** per visualizzare il secondo passaggio dell&#39;Assistente all&#39;aggiornamento. In questo passaggio è possibile avviare l&#39;aggiornamento facendo clic su **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

Le informazioni relative all’esecuzione degli aggiornamenti vengono visualizzate nella sezione superiore dell’assistente.

**[!UICONTROL Stop]** consente di annullare l&#39;aggiornamento, ma alcuni record potrebbero essere stati aggiornati e l&#39;arresto del processo non annullerà questi aggiornamenti. La barra di avanzamento mostra lo stato di avanzamento dell’operazione.

### Unisci dati {#merge-data}

Selezionare **[!UICONTROL Merge selected lines...]** per avviare l&#39;unione di due profili di destinatari. Prima di selezionare l’opzione, è necessario selezionare i profili da unire. L’unione viene configurata e avviata tramite un assistente.

L’assistente visualizza i valori da recuperare per ogni campo completato in uno dei profili sorgente. Se uno o più campi nei profili da unire hanno valori diversi, vengono visualizzati nella sezione **[!UICONTROL List of conflicts]**. È quindi possibile selezionare il profilo predefinito utilizzando i pulsanti di scelta sotto l&#39;elenco, come nell&#39;esempio seguente:

![](assets/s_ncs_user_merge_wizard01_1.png)

Fare clic su **[!UICONTROL Compute]** per visualizzare il risultato desiderato.

![](assets/s_ncs_user_merge_wizard01_2.png)

Controllare le colonne **[!UICONTROL Result]** di entrambe le sezioni della finestra e fare clic su **[!UICONTROL Finish]** per eseguire l&#39;unione.

## Esporta dati {#exporting-data}

È possibile esportare il contenuto di un elenco. Per configurare ed eseguire l&#39;esportazione:

1. Selezionare i record da esportare.
1. Fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. Quindi seleziona i dati da estrarre. Per impostazione predefinita, tutte le colonne visualizzate vengono aggiunte alle colonne di output.

   ![](assets/s_ncs_user_export_list_start.png)

   Per ulteriori informazioni su come configurare l&#39;Assistente all&#39;esportazione, consultare [questa sezione](../../platform/using/executing-export-jobs.md).

## Abbonati a un servizio {#subscribing-to-a-service}

Nella maggior parte dei casi, i destinatari si abbonano a una newsletter tramite una pagina di destinazione dedicata, come spiegato in [questa sezione](../../delivery/using/managing-subscriptions.md). Tuttavia, i profili dei destinatari filtrati possono essere abbonati a un servizio (newsletter o servizio virale) manualmente. Per eseguire questa operazione:

1. Seleziona i destinatari da abbonare e fai clic con il pulsante destro del mouse.
1. Seleziona **[!UICONTROL Actions > Subscribe selection to a service]**.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Selezionare il servizio desiderato e fare clic su **[!UICONTROL Next]**:

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >Questo editor consente di creare un nuovo servizio: fare clic sul pulsante **[!UICONTROL Create]**.

1. È possibile **[!UICONTROL Send a confirmation message]** ai destinatari. Il contenuto di questo messaggio può essere configurato nello scenario di abbonamento collegato al servizio selezionato.
1. Fare clic sul pulsante **[!UICONTROL Start]** per eseguire il processo di sottoscrizione.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

La sezione superiore della finestra consente di monitorare il processo di esecuzione. Il pulsante **[!UICONTROL Stop]** consente di arrestare il processo. Tuttavia, i destinatari già elaborati verranno iscritti.

Se si deseleziona l&#39;opzione **[!UICONTROL Do not keep a trace of this job in the database]**, è possibile selezionare o creare la cartella di esecuzione in cui verranno memorizzate le informazioni sul processo.

Per verificare il processo, passare alla scheda **[!UICONTROL Subscriptions]** dei profili dei destinatari interessati da questa operazione oppure alla scheda **[!UICONTROL Subscriptions]** accessibile tramite il nodo **[!UICONTROL Profiles and Targets > Services and Subscriptions]**.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione e la configurazione di Information Services, consulta [questa pagina](../../delivery/using/managing-subscriptions.md).
