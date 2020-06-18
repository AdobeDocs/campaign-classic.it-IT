---
title: Importazioni ed esportazioni generiche
seo-title: Importazioni ed esportazioni generiche
description: Importazioni ed esportazioni generiche
seo-description: null
page-status-flag: never-activated
uuid: e98753bb-1f14-4ec7-aa3b-d5e4f1ebaef7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: a21576c7-e94c-4fe1-9e31-d89116e427f6
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---


# Importazioni ed esportazioni generiche{#generic-imports-and-exports}

 Adobe Campaign offre un modulo di esportazione dei dati che semplifica l&#39;estrazione di un elenco di clienti o potenziali (ad esempio, dopo un&#39;operazione di targeting) che diventeranno quindi parte di una popolazione target.

 Adobe Campaign offre anche un modulo di importazione che consente di fornire al database i dati provenienti da file esterni.

>[!NOTE]
>
>Le esportazioni e le importazioni sono configurate in modelli dedicati eseguiti tramite flussi di lavoro tramite **[!UICONTROL Import]** e **[!UICONTROL Export]** attività. Possono essere ripetuti automaticamente in base a un programma, ad esempio per automatizzare lo scambio di dati tra diversi sistemi informativi. Se necessario, potete creare un&#39;importazione o un&#39;esportazione occasionale tramite il **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** nodo della struttura ad Adobe Campaign .

È possibile:

* Create un modello di importazione o esportazione e configuratelo (vedete di seguito).
* Creare un&#39;importazione o un&#39;esportazione: fare riferimento a [Esportazione di dati](../../platform/using/exporting-data.md) o [Importazione di dati](../../platform/using/importing-data.md).
* Avviate l&#39;importazione o l&#39;esportazione e monitorate l&#39;esecuzione. fare riferimento al tracciamento [](#execution-tracking)dell&#39;esecuzione.

>[!CAUTION]
>
>L&#39;importazione dei dati in Campaign deve essere eseguita tramite flussi di lavoro per garantire la coerenza dei dati e migliorare l&#39;efficienza. Per ulteriori informazioni, consultare le sezioni [Importazione di dati](../../workflow/using/importing-data.md), [Importazione di best practice](../../workflow/using/importing-data.md#best-practices-when-importing-data) e [Importazione di modelli di esempio](../../workflow/using/importing-data.md#setting-up-a-recurring-import) .

## Creating a job template {#creating-a-job-template}

I modelli di importazione ed esportazione sono memorizzati nella **[!UICONTROL Resources > Templates > Job templates]** directory della struttura  Adobi Campaign.

![](assets/s_ncs_user_export_wizard_template.png)

Per impostazione predefinita, in questa directory sono presenti tre modelli di importazione e uno di esportazione. Non devono essere modificati. Potete duplicarli per creare modelli personalizzati o creare un nuovo modello tramite il **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** menu.

![](assets/s_ncs_user_export_wizard_template_create.png)

La procedura per la creazione di un modello di processo viene presentata in [Esportazione guidata](../../platform/using/exporting-data.md#export-wizard) e [Importazione guidata](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>Il modello nativo **[!UICONTROL Import block list]** è già configurato per importare un elenco di indirizzi e-mail aggiunti all&#39;elenco dei blocchi.
> 
>I modelli **[!UICONTROL New text import]** e **[!UICONTROL New text export]** consentono di configurare un’importazione o un’esportazione da zero.

## Creazione di una nuova importazione/esportazione {#creating-a-new-import-export}

Una volta configurato il modello, le operazioni di importazione ed esportazione possono essere avviate in diversi contesti  Adobe Campaign.

Tutte queste opzioni consentono di aprire la procedura guidata di [importazione](../../platform/using/importing-data.md) o [esportazione](../../platform/using/exporting-data.md#export-wizard) .

* Nella **[!UICONTROL Profiles and targets]** sezione dell’area di lavoro  Adobe Campaign, fate clic sul **[!UICONTROL Jobs]** collegamento: viene visualizzato l’elenco delle importazioni e delle esportazioni esistenti.

   Fate clic sul **[!UICONTROL Create]** pulsante e selezionate il tipo di processo da eseguire.

   ![](assets/s_ncs_user_import_from_home.png)

* Potete inoltre avviare importazioni ed esportazioni dalla sezione Supervisione dell’area di lavoro: due collegamenti dedicati consentono di avviare direttamente l’importazione o l’esportazione.

   ![](assets/s_ncs_user_import_from_production.png)

* Importazioni ed esportazioni possono essere avviate anche dall&#39;esploratore di Adobi Campaign .

   Per esportare/importare dati, fare clic sul **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** nodo, quindi sull&#39; **[!UICONTROL New]** icona, quindi selezionare **[!UICONTROL Export]** o **[!UICONTROL Import]**. Viene aperta la procedura guidata appropriata.

   ![](assets/s_ncs_user_export_wizard_launch_from_menu.png)

## Tracciamento esecuzione {#execution-tracking}

Potete visualizzare il tracciamento dell&#39;esecuzione nella sezione superiore di questo editor. È possibile chiudere la procedura guidata di esportazione e visualizzare l’esecuzione del processo mediante l’elenco dei processi di importazione/esportazione.

![](assets/s_ncs_user_export_list_and_details.png)

* La **[!UICONTROL Log]** scheda consente di visualizzare i messaggi di registro relativi all&#39;esecuzione.
* La **[!UICONTROL Rejects]** scheda contiene i record rifiutati. Vedere [Comportamento in caso di errore](../../platform/using/importing-data.md#behavior-in-the-event-of-an-error).

>[!NOTE]
>
>Gli stati dei processi di importazione/esportazione vengono visualizzati negli stati dei [processi](../../platform/using/importing-data.md#job-statuses).

