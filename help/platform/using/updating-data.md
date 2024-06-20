---
product: campaign
title: Aggiornamento dei dati
description: Aggiornamento dei dati
feature: Data Management
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: 8aceafa362b80f6e34edfd91a71551a58501a3d0
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 1%

---

# Aggiornare i dati{#updating-data}

>[!NOTE]
>
>Questa pagina si applica solo agli operatori che si connettono a Campaign con autenticazione nativa.

I dati collegati al profilo di un destinatario possono essere aggiornati manualmente o automaticamente.

## Impostare un aggiornamento automatico {#setting-up-an-automatic-update}

Un aggiornamento automatico può essere configurato tramite un flusso di lavoro. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/update-data.md).

## Eseguire un aggiornamento di massa {#performing-a-mass-update}

Per eseguire aggiornamenti manuali, fai clic con il pulsante destro del mouse sui destinatari selezionati per utilizzare **[!UICONTROL Actions]** menu di scelta rapida o utilizzare **[!UICONTROL Actions]** icona.

![](assets/s_ncs_user_action_icon.png)

Esistono due tipi di aggiornamenti: aggiornamento di massa per un set di destinatari e unione di dati tra due profili. Per ogni azione, una procedura guidata consente di configurare l’aggiornamento.

### Aggiornamento di massa {#mass-update}

Per l&#39;aggiornamento di massa, utilizzare **[!UICONTROL Action > Mass update of selected lines...]**. La procedura guidata consente di configurare ed eseguire l’aggiornamento.

Il primo passaggio della procedura guidata consiste nel specificare i campi da aggiornare.

Nella sezione a sinistra della procedura guidata viene visualizzato l&#39;elenco dei campi disponibili. Utilizza il **[!UICONTROL Find]** per eseguire una ricerca di questi campi. Premere il tasto **Invio** per sfogliare l&#39;elenco. I nomi dei campi corrispondenti alla voce vengono visualizzati in grassetto, come illustrato di seguito.

Fare doppio clic sui campi da aggiornare per visualizzarli nella sezione a destra della procedura guidata.

![](assets/s_ncs_user_update_wizard01_1.png)

In caso di errore, utilizza **[!UICONTROL Delete]** per eliminare un campo dall&#39;elenco dei campi da aggiornare.

Seleziona o immetti i valori da applicare ai profili da aggiornare.

![](assets/s_ncs_user_update_wizard01_12.png)

Puoi fare clic su **[!UICONTROL Distribution of values]** per visualizzare la distribuzione dei valori del campo selezionato per i destinatari presenti nella cartella corrente (non solo per i destinatari interessati dall&#39;aggiornamento).

![](assets/s_ncs_user_update_wizard01_2.png)

È possibile definire filtri per visualizzare la distribuzione dei valori in questa finestra o modificare la cartella corrente per visualizzare la distribuzione dei valori in un&#39;altra cartella. Si tratta di azioni di sola lettura che non influiscono sulla configurazione dell’aggiornamento da definire.

![](assets/s_ncs_user_update_wizard01_3.png)

Chiudi questa finestra e fai clic su **[!UICONTROL Next]** per visualizzare il secondo passaggio della procedura guidata di aggiornamento. In questo passaggio, puoi avviare l’aggiornamento facendo clic su **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

Le informazioni relative all’esecuzione degli aggiornamenti vengono visualizzate nella sezione superiore della procedura guidata.

Il **[!UICONTROL Stop]** consente di annullare l&#39;aggiornamento, ma alcuni record potrebbero essere stati aggiornati e l&#39;arresto del processo non annullerà questi aggiornamenti. La barra di avanzamento mostra lo stato di avanzamento dell’operazione.

### Unisci dati {#merge-data}

Seleziona **[!UICONTROL Merge selected lines...]** per avviare l’unione di due profili di destinatari. Prima di selezionare l’opzione, è necessario selezionare i profili da unire. L’unione viene configurata e avviata tramite una procedura guidata.

La procedura guidata visualizza i valori da recuperare per ogni campo completato in uno dei profili sorgente. Se uno o più campi nei profili da unire hanno valori diversi, vengono visualizzati nel **[!UICONTROL List of conflicts]** sezione. È quindi possibile selezionare il profilo predefinito utilizzando i pulsanti di scelta sotto l&#39;elenco, come nell&#39;esempio seguente:

![](assets/s_ncs_user_merge_wizard01_1.png)

Clic **[!UICONTROL Compute]** per visualizzare il risultato desiderato.

![](assets/s_ncs_user_merge_wizard01_2.png)

Controlla la **[!UICONTROL Result]** colonne di entrambe le sezioni della finestra e fare clic su **[!UICONTROL Finish]** per eseguire l&#39;unione.

## Esporta dati {#exporting-data}

È possibile esportare il contenuto di un elenco. Per configurare ed eseguire l&#39;esportazione:

1. Selezionare i record da esportare.
1. Fai clic con il pulsante destro del mouse e seleziona (Copia negli Appunti) **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. Quindi seleziona i dati da estrarre. Per impostazione predefinita, tutte le colonne visualizzate vengono aggiunte alle colonne di output.

   ![](assets/s_ncs_user_export_list_start.png)

   Per ulteriori informazioni su come configurare l’esportazione guidata, consulta [questa sezione](../../platform/using/executing-export-jobs.md).

## Abbonati a un servizio {#subscribing-to-a-service}

Nella maggior parte dei casi, i destinatari si abbonano a una newsletter tramite una pagina di destinazione dedicata, come spiegato in [questa sezione](../../delivery/using/managing-subscriptions.md). Tuttavia, i profili dei destinatari filtrati possono essere abbonati a un servizio (newsletter o servizio virale) manualmente. Per eseguire questa operazione:

1. Seleziona i destinatari da abbonare e fai clic con il pulsante destro del mouse.
1. Seleziona **[!UICONTROL Actions > Subscribe selection to a service]**.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Seleziona il servizio desiderato e fai clic su **[!UICONTROL Next]**:

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >Questo editor consente di creare un nuovo servizio: fai clic su **[!UICONTROL Create]** pulsante.

1. È possibile **[!UICONTROL Send a confirmation message]** ai destinatari. Il contenuto di questo messaggio può essere configurato nello scenario di abbonamento collegato al servizio selezionato.
1. Fai clic su **[!UICONTROL Start]** per eseguire il processo di sottoscrizione.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

La sezione superiore della finestra consente di monitorare il processo di esecuzione. Il **[!UICONTROL Stop]** consente di interrompere il processo. Tuttavia, i destinatari già elaborati verranno iscritti.

Se deselezioni la **[!UICONTROL Do not keep a trace of this job in the database]** , è possibile selezionare (o creare) la cartella di esecuzione in cui verranno memorizzate le informazioni sul processo.

Per controllare il processo, vai al **[!UICONTROL Subscriptions]** sui profili dei destinatari interessati da questa operazione, oppure **[!UICONTROL Subscriptions]** accessibile tramite il **[!UICONTROL Profiles and Targets > Services and Subscriptions]** nodo.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione e la configurazione dei servizi di informazione, consulta [questa pagina](../../delivery/using/managing-subscriptions.md).
