---
solution: Campaign Classic
product: campaign
title: Aggiornamenti dei dati
description: Aggiornamenti dei dati
audience: platform
content-type: reference
topic-tags: profile-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 2%

---


# Aggiornamenti dei dati{#updating-data}

I dati collegati al profilo di un destinatario possono essere aggiornati manualmente o automaticamente.

## Impostazione di un aggiornamento automatico {#setting-up-an-automatic-update}

Un aggiornamento automatico può essere configurato tramite un flusso di lavoro. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../workflow/using/update-data.md).

## Esecuzione di un aggiornamento di massa {#performing-a-mass-update}

Per eseguire aggiornamenti manuali, fare clic con il pulsante destro del mouse sui destinatari selezionati per utilizzare il menu di **[!UICONTROL Actions]** scelta rapida, oppure utilizzare l&#39; **[!UICONTROL Actions]** icona.

![](assets/s_ncs_user_action_icon.png)

Esistono due tipi di aggiornamenti: aggiornamento di massa per un set di destinatari e unione dei dati tra due profili. Per ogni azione, una procedura guidata consente di configurare l’aggiornamento.

### Aggiornamento di massa {#mass-update}

Per l&#39;aggiornamento di massa, utilizzare **[!UICONTROL Action > Mass update of selected lines...]**. La procedura guidata consente di configurare ed eseguire l&#39;aggiornamento.

Il primo passaggio della procedura guidata consiste nel specificare i campi da aggiornare.

Nella sezione a sinistra della procedura guidata viene visualizzato l’elenco dei campi disponibili. Utilizzare il **[!UICONTROL Find]** campo per eseguire una ricerca in questi campi. Premere il tasto **Invio** per scorrere l&#39;elenco. I nomi dei campi corrispondenti alla voce vengono visualizzati in grassetto, come illustrato di seguito.

Fare doppio clic sui campi da aggiornare per visualizzarli nella sezione destra della procedura guidata.

![](assets/s_ncs_user_update_wizard01_1.png)

In caso di errore, utilizzare il **[!UICONTROL Delete]** pulsante per eliminare un campo dall&#39;elenco dei campi da aggiornare.

Selezionate o immettete i valori da applicare ai profili da aggiornare.

![](assets/s_ncs_user_update_wizard01_12.png)

Potete fare clic **[!UICONTROL Distribution of values]** per visualizzare la distribuzione dei valori del campo selezionato per i destinatari presenti nella cartella corrente (non solo per i destinatari interessati dall&#39;aggiornamento).

![](assets/s_ncs_user_update_wizard01_2.png)

È possibile definire filtri per visualizzare la distribuzione dei valori in questa finestra o modificare la cartella corrente per visualizzare la distribuzione dei valori in un&#39;altra cartella. Si tratta di azioni di sola lettura; non influiscono sulla configurazione dell’aggiornamento in fase di definizione.

![](assets/s_ncs_user_update_wizard01_3.png)

Chiudi questa finestra e fai clic **[!UICONTROL Next]** per visualizzare il secondo passaggio della procedura guidata di aggiornamento. In questo passaggio, puoi avviare l&#39;aggiornamento facendo clic su **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

Le informazioni relative all&#39;esecuzione dell&#39;aggiornamento sono visualizzate nella sezione superiore della procedura guidata.

Consente di **[!UICONTROL Stop]** annullare l&#39;aggiornamento, ma alcuni record potrebbero essere stati aggiornati e l&#39;arresto del processo non annullerà questi aggiornamenti. La barra di avanzamento mostra l’avanzamento dell’operazione.

### Unisci dati {#merge-data}

Seleziona **[!UICONTROL Merge selected lines...]** per avviare l&#39;unione di due profili di destinatari. I profili da unire devono essere selezionati prima di selezionare l&#39;opzione. L&#39;unione viene configurata e avviata utilizzando una procedura guidata.

La procedura guidata visualizza i valori da recuperare per ogni campo completato in uno o più dei profili di origine. Se uno o più campi nei profili da unire hanno valori diversi, vengono visualizzati nella **[!UICONTROL List of conflicts]** sezione. È quindi possibile selezionare il profilo predefinito utilizzando i pulsanti di scelta sotto l&#39;elenco, come nell&#39;esempio seguente:

![](assets/s_ncs_user_merge_wizard01_1.png)

Fate clic **[!UICONTROL Compute]** per visualizzare il risultato della scelta.

![](assets/s_ncs_user_merge_wizard01_2.png)

Controllare le **[!UICONTROL Result]** colonne di entrambe le sezioni della finestra e fare clic **[!UICONTROL Finish]** per eseguire l&#39;unione.

## Esportazione di dati {#exporting-data}

È possibile esportare il contenuto di un elenco. Per configurare ed eseguire l&#39;esportazione:

1. Selezionare i record da esportare.
1. Fare clic con il pulsante destro del mouse e selezionare **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. Quindi selezionate i dati da estrarre. Per impostazione predefinita, tutte le colonne visualizzate vengono aggiunte alle colonne di output.

   ![](assets/s_ncs_user_export_list_start.png)

   Per ulteriori informazioni su come configurare la procedura guidata di esportazione, vedere [Esportazione guidata](../../platform/using/exporting-data.md#export-wizard).

## Iscrizione a un servizio {#subscribing-to-a-service}

Nella maggior parte dei casi, i destinatari si iscrivono a una newsletter tramite una pagina di destinazione dedicata, come illustrato in [questa sezione](../../delivery/using/managing-subscriptions.md). Tuttavia, i profili dei destinatari filtrati possono essere sottoscritti manualmente a un servizio (Newsletter o Viral service). Per eseguire questa operazione:

1. Selezionate i destinatari che desiderate sottoscrivere e fate clic con il pulsante destro del mouse.
1. Seleziona **[!UICONTROL Actions > Subscribe selection to a service]**.

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. Selezionate il servizio desiderato e fate clic su **[!UICONTROL Next]**:

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >Questo editor consente di creare un nuovo servizio: fare clic sul **[!UICONTROL Create]** pulsante.

1. È possibile **[!UICONTROL Send a confirmation message]** indirizzare i destinatari. Il contenuto di questo messaggio può essere configurato nello scenario di iscrizione collegato al servizio selezionato.
1. Fate clic sul **[!UICONTROL Start]** pulsante per eseguire il processo di iscrizione.

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

La sezione superiore della finestra consente di monitorare il processo di esecuzione. Il **[!UICONTROL Stop]** pulsante consente di interrompere il processo. Tuttavia, i destinatari già elaborati verranno sottoscritti.

Se deselezionate l’ **[!UICONTROL Do not keep a trace of this job in the database]** opzione, potete selezionare (o creare) la cartella di esecuzione in cui verranno memorizzate le informazioni su questo processo.

Per controllare il processo, passare alla **[!UICONTROL Subscriptions]** scheda sui profili dei destinatari interessati dall&#39;operazione oppure alla **[!UICONTROL Subscriptions]** scheda a cui si accede tramite il **[!UICONTROL Profiles and Targets > Services and Subscriptions]** nodo.

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>Per ulteriori informazioni sulla creazione e la configurazione dei servizi di informazione, consultate [questa pagina](../../delivery/using/managing-subscriptions.md).

