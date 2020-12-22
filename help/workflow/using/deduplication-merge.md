---
title: Utilizzo della funzionalità Unisci dell'attività Deduplicazione
description: Scopri come utilizzare la funzionalità Unisci dell'attività Deduplicazione
page-status-flag: never-activated
uuid: 8887574e-447b-48a5-afc6-95783ffa7fb3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4113c3fe-a279-4fe1-be89-ea43c96edc34
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 32a14eb99847dc04a582623204bc856c29fa4359
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 4%

---


# Utilizzo della funzionalità Unisci dell&#39;attività Deduplicazione {#deduplication-merge}

## Informazioni sul caso di utilizzo {#about-this-use-case}

Questo esempio descrive come utilizzare la funzionalità **[!UICONTROL Merge]** nell&#39;attività **[!UICONTROL Deduplication]**.

Per ulteriori informazioni su questa funzionalità, consultare [questa sezione](../../workflow/using/deduplication.md#merging-fields-into-single-record).

L&#39;attività **[!UICONTROL Deduplication]** viene utilizzata per rimuovere righe duplicate da un set di dati. In questo caso d’uso, i dati riportati di seguito vengono duplicati in base al campo E-mail.

| Data ultima modifica | Nome | Cognome | E-mail | Cellulare | Telefono |
|-----|------------|-----------|-------|--------------|------|
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 03/10/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Con la funzionalità **[!UICONTROL Merge]** dell&#39;attività di deduplicazione, puoi configurare un set di regole per la deduplicazione per definire un gruppo di campi da unire in un singolo record di dati risultante. Ad esempio, con un set di record duplicati, potete scegliere di mantenere il numero di telefono più vecchio o il nome più recente.

## Attivazione della funzionalità Unisci {#activating-merge}


Per abilitare la funzionalità di unione, è innanzitutto necessario configurare l&#39;attività **[!UICONTROL Deduplication]**. Per farlo, esegui questi passaggi:

1. Aprite l&#39;attività, quindi fate clic sul collegamento **[Modifica configurazione]**.

1. Selezionare il campo di riconciliazione da utilizzare per la deduplicazione, quindi fare clic su **[!UICONTROL Next]**. In questo esempio, vogliamo deduplicare in base al campo e-mail.

   ![](assets/uc_merge_edit.png)

1. Fare clic sul collegamento **[!UICONTROL Advanced parameters]**, quindi attivare le opzioni **[!UICONTROL Merge records]** e **[!UICONTROL Use several record merging criteria]**.

   ![](assets/uc_merge_advanced_parameters.png)

1. La scheda **[!UICONTROL Merge]** viene aggiunta alla schermata di configurazione **[!UICONTROL Deduplication]**. Questa scheda consente di specificare i dati da unire durante l&#39;esecuzione della deduplicazione.

## Configurazione dei campi da unire {#configuring-rules}

Di seguito sono riportate le regole che si desidera utilizzare per unire i dati in un singolo record:

* Mantenere il nome più recente (campi nome e cognome),
* Mantenere il cellulare più recente,
* Mantenere il numero di telefono più vecchio,
* Tutti i campi di un gruppo devono essere non-null per essere idonei per il record finale.

Per configurare queste regole, attenetevi alla procedura seguente:

1. Aprite la scheda **[!UICONTROL Merge]**, quindi fate clic sul pulsante **[!UICONTROL Add]**.

   ![](assets/uc_merge_add.png)

1. Specificare l&#39;identificatore e l&#39;etichetta del gruppo di campi da unire.

   ![](assets/uc_merge_identifier.png)

1. Indicare le condizioni per la selezione dei record da prendere in considerazione.

   ![](assets/uc_merge_filter.png)

1. Ordinare in base all&#39;ultima data di modifica per selezionare il nome più recente.

   ![](assets/uc_merge_sort.png)

1. Selezionare i campi da unire. In questo esempio, vogliamo mantenere i campi nome e cognome.

   ![](assets/uc_merge_keep.png)

1. I campi vengono aggiunti al set di dati da unire e un nuovo elemento viene aggiunto allo schema del flusso di lavoro.

   Ripetete questi passaggi per configurare i campi telefono e telefono cellulare.

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## Risultati {#results}

Dopo la configurazione di queste regole, i dati seguenti vengono ricevuti alla fine dell&#39;attività **[!UICONTROL Deduplication]**.

| Data modifica | Nome | Cognome | E-mail | Cellulare | Telefono |
-----|------------|-----------|-------|--------------|------|
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 03/10/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Il risultato viene unito dai tre record in base alle regole configurate in precedenza. Dopo il confronto, si conclude che vengono utilizzati il nome e il telefono cellulare più recenti, insieme al numero di telefono originale.

| Nome | Cognome | E-mail | Cellulare | Telefono |
|------------|-----------|-------|--------------|------|
| Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> Il nome che è stato unito è &quot;Bobby&quot;, perché abbiamo configurato una regola &quot;Nome&quot; composta sia dal nome che dal cognome.
>
>Di conseguenza, non è stato possibile prendere in considerazione &quot;Bob&quot; (il nome più recente) perché il campo del cognome associato era vuoto. La combinazione più recente di nomi e cognomi è stata unita nel record finale.
