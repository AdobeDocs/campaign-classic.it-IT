---
solution: Campaign Classic
product: campaign
title: Importazioni ed esportazioni generiche
description: Importazioni ed esportazioni generiche
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 3%

---


# Importazioni ed esportazioni generiche{#generic-imports-and-exports}

 Adobe Campaign offre un modulo di esportazione dei dati che semplifica l&#39;estrazione di un elenco di clienti o potenziali (ad esempio, dopo un&#39;operazione di targeting) che diventeranno quindi parte di una popolazione target.

 Adobe Campaign offre anche un modulo di importazione che consente di fornire al database i dati provenienti da file esterni.

>[!NOTE]
>
>Le esportazioni e le importazioni sono configurate in modelli dedicati eseguiti tramite flussi di lavoro attraverso le attività **[!UICONTROL Import]** e **[!UICONTROL Export]**. Possono essere ripetuti automaticamente in base a un programma, ad esempio per automatizzare lo scambio di dati tra diversi sistemi informativi. Se necessario, potete creare un&#39;importazione o un&#39;esportazione occasionale tramite il nodo **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** della struttura di Adobe Campaign .

Puoi:

* Create un modello di importazione o esportazione e configuratelo (vedete di seguito).
* Creare un&#39;importazione o un&#39;esportazione: fare riferimento a [Esportazione di dati](../../platform/using/exporting-data.md) o [Importazione di dati](../../platform/using/importing-data.md).
* Avviate l&#39;importazione o l&#39;esportazione e monitorate l&#39;esecuzione. fare riferimento a [Tracciamento esecuzione](#execution-tracking).

>[!CAUTION]
>
>L&#39;importazione dei dati in Campaign deve essere eseguita tramite flussi di lavoro per garantire la coerenza dei dati e migliorare l&#39;efficienza. Per ulteriori informazioni, consultare le sezioni [Importazione di dati](../../workflow/using/importing-data.md), [Importa best practice](../../workflow/using/importing-data.md#best-practices-when-importing-data) e [Importa esempio di modello](../../workflow/using/importing-data.md#setting-up-a-recurring-import).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](../../platform/using/exporting-and-importing-profiles.md#import-profiles-video)

## Creazione di un modello di processo {#creating-a-job-template}

I modelli di importazione ed esportazione sono memorizzati nella directory **[!UICONTROL Resources > Templates > Job templates]** della struttura di Adobe Campaign .

Per impostazione predefinita, in questa directory sono presenti tre modelli di importazione e uno di esportazione. Non devono essere modificati. Potete duplicarli per creare modelli personalizzati o creare un nuovo modello tramite il menu **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]**.

![](assets/s_ncs_user_export_wizard_template_create.png)

La procedura per la creazione di un modello di processo è presentata in [Procedura guidata di esportazione](../../platform/using/exporting-data.md#export-wizard) e [Procedura guidata di importazione](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>Il modello nativo **[!UICONTROL Import denylist]** è già configurato per importare un elenco di indirizzi e-mail che sono stati aggiunti al elenco Bloccati.
> 
>I modelli **[!UICONTROL New text import]** e **[!UICONTROL New text export]** consentono di configurare un&#39;importazione o un&#39;esportazione da zero.

## Creazione di una nuova importazione/esportazione {#creating-a-new-import-export}

Una volta configurato il modello, le operazioni di importazione ed esportazione possono essere avviate in diversi contesti  Adobe Campaign.

Tutte queste opzioni consentono di aprire la procedura guidata [import](../../platform/using/importing-data.md) o [export](../../platform/using/exporting-data.md#export-wizard).

* Nella sezione **[!UICONTROL Profiles and targets]** dell&#39;area di lavoro  Adobe Campaign, fate clic sul collegamento **[!UICONTROL Jobs]**: viene visualizzato l’elenco delle importazioni e delle esportazioni esistenti.

   Fate clic sul pulsante **[!UICONTROL Create]** e selezionate il tipo di processo da eseguire.

   ![](assets/s_ncs_user_import_from_home.png)

* Potete inoltre avviare importazioni ed esportazioni dalla sezione Supervisione dell’area di lavoro: due collegamenti dedicati consentono di avviare direttamente l’importazione o l’esportazione.

   ![](assets/s_ncs_user_import_from_production.png)

* Importazioni ed esportazioni possono essere avviate anche da  Adobe Campaign Explorer.

   Per esportare/importare dati, fare clic sul nodo **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]**, quindi sull&#39;icona **[!UICONTROL New]**, quindi selezionare **[!UICONTROL Export]** o **[!UICONTROL Import]**. Viene aperta la procedura guidata appropriata.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## Tracciamento esecuzione {#execution-tracking}

Potete visualizzare il tracciamento dell&#39;esecuzione nella sezione superiore di questo editor. È possibile chiudere la procedura guidata di esportazione e visualizzare l’esecuzione del processo mediante l’elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* La scheda **[!UICONTROL Log]** consente di esaminare i messaggi di registro relativi all&#39;esecuzione.
* La scheda **[!UICONTROL Rejects]** contiene i record rifiutati. Vedere [Comportamento in caso di errore](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>Gli stati dei processi di importazione/esportazione sono presentati in [stati dei processi](../../platform/using/importing-data.md#job-statuses).

