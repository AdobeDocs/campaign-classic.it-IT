---
title: Utilizzare la funzionalità di unione dell’attività Deduplication
description: Scopri come utilizzare la funzionalità di unione dell’attività Deduplication
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management
exl-id: a6b10585-7bf9-4fef-b886-db081b6d3acc
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 8%

---

# Utilizzare la funzionalità di unione dell’attività Deduplication {#deduplication-merge}



## Informazioni su questo caso d’uso {#about-this-use-case}

Questo caso d&#39;uso descrive come utilizzare **[!UICONTROL Merge]** nella **[!UICONTROL Deduplication]** attività.

Per ulteriori informazioni su questa funzionalità, consulta [questa sezione](deduplication.md#merging-fields-into-single-record).

La **[!UICONTROL Deduplication]** viene utilizzata per rimuovere righe duplicate da un set di dati. In questo caso d’uso, i dati mostrati di seguito vengono duplicati in base al campo E-mail .

| Data ultima modifica | Nome | Cognome | E-mail | Telefono cellulare | Telefono |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Con le attività di deduplicazione **[!UICONTROL Merge]** funzionalità, puoi configurare un set di regole per la deduplicazione per definire un gruppo di campi da unire in un singolo record di dati risultante. Ad esempio, con un set di record duplicati, puoi scegliere di mantenere il numero di telefono più vecchio o il nome più recente.

## Attivazione della funzionalità di unione {#activating-merge}


Per abilitare la funzionalità di unione, è innanzitutto necessario configurare la **[!UICONTROL Deduplication]** attività. Per farlo, esegui questi passaggi:

1. Apri l’attività, quindi fai clic sul pulsante **[Modifica configurazione]** link.

1. Seleziona il campo di riconciliazione da utilizzare per la deduplicazione, quindi fai clic su **[!UICONTROL Next]**. In questo esempio, vogliamo deduplicare in base al campo e-mail.

   ![](assets/uc_merge_edit.png)

1. Fai clic sul pulsante **[!UICONTROL Advanced parameters]** , quindi attiva il **[!UICONTROL Merge records]** e **[!UICONTROL Use several record merging criteria]** opzioni.

   ![](assets/uc_merge_advanced_parameters.png)

1. La **[!UICONTROL Merge]** viene aggiunta alla scheda **[!UICONTROL Deduplication]** schermata di configurazione. Questa scheda consente di specificare i dati da unire durante l’esecuzione della deduplicazione.

## Configurazione dei campi da unire {#configuring-rules}

Di seguito sono riportate le regole che si desidera utilizzare per unire i dati in un singolo record:

* Mantenere il nome più recente (campi nome e cognome),
* Mantenere il cellulare più recente,
* Mantenere il numero di telefono più vecchio,
* Tutti i campi di un gruppo devono essere non-null per essere idonei al record finale.

Per configurare queste regole, effettua le seguenti operazioni:

1. Apri **[!UICONTROL Merge]** , quindi fai clic sul pulsante **[!UICONTROL Add]** pulsante .

   ![](assets/uc_merge_add.png)

1. Specifica l’identificatore e l’etichetta del gruppo di campi da unire.

   ![](assets/uc_merge_identifier.png)

1. Indicare le condizioni per la selezione dei record da prendere in considerazione.

   ![](assets/uc_merge_filter.png)

1. Ordina in base all’ultima data di modifica per selezionare il nome più recente.

   ![](assets/uc_merge_sort.png)

1. Selezionare i campi da unire. In questo esempio, vogliamo mantenere i campi nome e cognome.

   ![](assets/uc_merge_keep.png)

1. I campi vengono aggiunti al set di dati da unire e un nuovo elemento viene aggiunto allo schema del flusso di lavoro.

   Ripetere questi passaggi per configurare i campi del telefono cellulare e del telefono.

   ![](assets/dedup8.png)

   ![](assets/dedup9.png)

## Risultati {#results}

Dopo aver configurato queste regole, i seguenti dati vengono ricevuti alla fine del **[!UICONTROL Deduplication]** attività.

| Data di modifica | Nome | Cognome | E-mail | Telefono cellulare | Telefono |
|-----|------------|-----------|-------|--------------|------|
| 5/19/2020 | Robert | Tisner | bob@mycompany.com | 444-444-444 | 777-777-7777 |
| 7/22/2020 | Bobby | Tisner | bob@mycompany.com |  | 777-777-7777 |
| 10/03/2020 | Bob |  | bob@mycompany.com |  | 888-888-8888 |

Il risultato viene unito dai tre record in base alle regole configurate in precedenza. Dopo il confronto, si conclude che sono utilizzati il nome e il telefono cellulare più recenti, insieme al numero di telefono originale.

| Nome | Cognome | E-mail | Telefono cellulare | Telefono |
|------------|-----------|-------|--------------|------|
| Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

>[!NOTE]
>
> Il nome che è stato unito è &quot;Bobby&quot;, perché abbiamo configurato una regola &quot;Nome&quot; composta sia dal nome che dal cognome.
>
>Di conseguenza, non è stato possibile prendere in considerazione &quot;Bob&quot; (il nome più recente) perché il campo del cognome associato era vuoto. La combinazione più recente di nomi e cognomi è stata unita nel record finale.
