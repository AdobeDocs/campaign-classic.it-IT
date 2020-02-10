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
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Importazioni ed esportazioni generiche{#generic-imports-and-exports}

Adobe Campaign offre un modulo di esportazione dei dati che semplifica l&#39;estrazione di un elenco di clienti o potenziali (ad esempio, dopo un&#39;operazione di targeting) che diventeranno quindi parte di una popolazione target.

Adobe Campaign offre anche un modulo di importazione che consente di fornire al database i dati provenienti da file esterni.

>[!NOTE]
>
>Le esportazioni e le importazioni sono configurate in modelli dedicati eseguiti tramite flussi di lavoro tramite **[!UICONTROL Import]** e **[!UICONTROL Export]** attività. Possono essere ripetuti automaticamente in base a un programma, ad esempio per automatizzare lo scambio di dati tra diversi sistemi informativi. Se necessario, puoi creare un&#39;importazione o un&#39;esportazione occasionale tramite il **[!UICONTROL Profiles and Targets > Jobs > Generic imports and exports]** nodo della struttura di Adobe Campaign.

È possibile:

* Create un modello di importazione o esportazione e configuratelo (vedete di seguito).
* Creare un&#39;importazione o un&#39;esportazione: fare riferimento a [Esportazione di dati](../../platform/using/exporting-data.md) o [Importazione di dati](../../platform/using/importing-data.md).
* Avviate l&#39;importazione o l&#39;esportazione e monitorate l&#39;esecuzione. fare riferimento al tracciamento [](#execution-tracking)dell&#39;esecuzione.

>[!CAUTION]
>
>L&#39;importazione dei dati in Campaign deve essere eseguita tramite flussi di lavoro per garantire la coerenza dei dati e migliorare l&#39;efficienza. Per ulteriori informazioni, consultare le sezioni [Importazione di dati](../../workflow/using/importing-data.md), [Best practice](../../workflow/using/importing-data.md#best-practices-when-importing-data) e [Importazione di modelli di esempio](../../workflow/using/importing-data.md#setting-up-a-recurring-import) .

## Creating a job template {#creating-a-job-template}

I modelli di importazione ed esportazione sono memorizzati nella **[!UICONTROL Resources > Templates > Job templates]** directory della struttura di Adobe Campaign.

![](assets/s_ncs_user_export_wizard_template.png)

Per impostazione predefinita, in questa directory sono presenti tre modelli di importazione e uno di esportazione. Non devono essere modificati. Potete duplicarli per creare modelli personalizzati o creare un nuovo modello tramite il **[!UICONTROL New > Import template]** / **[!UICONTROL Export template]** menu.

![](assets/s_ncs_user_export_wizard_template_create.png)

La procedura per la creazione di un modello di processo viene presentata in [Esportazione guidata](../../platform/using/exporting-data.md#export-wizard) e [Importazione guidata](../../platform/using/importing-data.md#import-wizard).

>[!NOTE]
>
>Il modello nativo **[!UICONTROL Import blacklist]** è già configurato per importare un elenco di indirizzi e-mail in lista nera.
> 
>I modelli **[!UICONTROL New text import]** e **[!UICONTROL New text export]** consentono di configurare un’importazione o un’esportazione da zero.

## Creazione di una nuova importazione/esportazione {#creating-a-new-import-export}

Una volta configurato il modello, le operazioni di importazione ed esportazione possono essere avviate in diversi contesti in Adobe Campaign.

Tutte queste opzioni consentono di aprire la procedura guidata di [importazione](../../platform/using/importing-data.md) o [esportazione](../../platform/using/exporting-data.md#export-wizard) .

* Nella **[!UICONTROL Profiles and targets]** sezione dell&#39;area di lavoro di Adobe Campaign, fai clic sul **[!UICONTROL Jobs]** collegamento: viene visualizzato l’elenco delle importazioni e delle esportazioni esistenti.

   Fate clic sul **[!UICONTROL Create]** pulsante e selezionate il tipo di processo da eseguire.

   ![](assets/s_ncs_user_import_from_home.png)

* Potete inoltre avviare importazioni ed esportazioni dalla sezione Supervisione dell’area di lavoro: due collegamenti dedicati consentono di avviare direttamente l’importazione o l’esportazione.

   ![](assets/s_ncs_user_import_from_production.png)

* Importazioni ed esportazioni possono essere avviate anche da Adobe Campaign Explorer.

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

