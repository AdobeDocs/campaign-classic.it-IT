---
title: Aggiornare dati
seo-title: Aggiornare dati
description: Aggiornare dati
seo-description: null
page-status-flag: never-activated
uuid: 5f3ab7c8-175a-4b06-a50c-edc97b226e3c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: c94ce5b7-aa8a-4ea2-845d-68c9c7dc2a7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# Aggiornare dati{#update-data}

Un&#39;attività di tipo **Aggiorna dati** esegue un aggiornamento di massa dei campi nel database.

## Tipo di operazione {#operation-type}

Il **[!UICONTROL Operation type]** campo consente di scegliere il processo da eseguire sui dati del database:

* **[!UICONTROL Insert or update]**: aggiungere dati o aggiornarli se sono già stati aggiunti.
* **[!UICONTROL Insert]**: aggiungi solo dati.
* **[!UICONTROL Update]**: aggiorna solo i dati.
* **[!UICONTROL Update and merge collections]**: aggiornate i dati e scegliete un record &quot;principale&quot;, quindi collegate agli elementi duplicati nel record master. I duplicati possono quindi essere eliminati senza creare elementi associati orfani.
* **[!UICONTROL Delete]**: eliminare i dati.

![](assets/s_advuser_update_data_1.png)

Il **[!UICONTROL Batch size]** campo consente di selezionare il numero di elementi di transizione in entrata da aggiornare. Ad esempio, se specifichi 500, i primi 500 record trattati verranno aggiornati.

## Identificazione record {#record-identification}

Specificare come identificare i record nel database:

* Se le voci di dati si riferiscono a una dimensione di targeting esistente, selezionate l&#39; **[!UICONTROL By directly using the targeting dimension]** opzione e selezionatela nel **[!UICONTROL Updated dimension]** campo.

   È possibile visualizzare i campi per la dimensione selezionata utilizzando il pulsante della lente di **[!UICONTROL Edit this link]** ingrandimento.

* In caso contrario, specificare uno o più collegamenti che consentano l&#39;identificazione dei dati nel database o l&#39;uso diretto delle chiavi di riconciliazione.

![](assets/s_advuser_update_data_2.png)

## Selezione dei campi da aggiornare {#selecting-the-fields-to-be-updated}

Utilizzate l&#39; **[!UICONTROL Automatically associate fields with the same name]** opzione affinché Adobe Campaign identifichi automaticamente i campi da aggiornare.

![](assets/s_advuser_update_data_3b.png)

È inoltre possibile utilizzare l&#39; **[!UICONTROL Insert]** icona per selezionare manualmente i campi del database da aggiornare.

![](assets/s_advuser_update_data_3.png)

Selezionate tutti i campi da aggiornare e, se necessario, aggiungete le condizioni in base alle quali eseguire l&#39;aggiornamento. A questo scopo, utilizzare la **[!UICONTROL Taken into account if]** colonna. Le condizioni vengono applicate una dopo l&#39;altra e in conformità con l&#39;ordine nell&#39;elenco. Utilizzate le frecce a destra per cambiare l&#39;ordine degli aggiornamenti.

È possibile utilizzare lo stesso campo di destinazione più volte.

All&#39;interno di un&#39; **[!UICONTROL Insert or update]** operazione, potete selezionare la campagna da applicare, singolarmente o per ciascun campo. A questo scopo, selezionate il valore desiderato nella **[!UICONTROL Operation]** colonna.

![](assets/s_advuser_update_data_5.png)

I **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]****[!UICONTROL createdDate]** e **[!UICONTROL createdBy]** i campi vengono aggiornati automaticamente durante gli aggiornamenti dei dati, a meno che la relativa modalità di gestione non sia configurata specificatamente nella tabella di aggiornamento dei campi.

L&#39;aggiornamento dei record viene eseguito solo per i record contenenti almeno una differenza. Se i valori sono identici, non viene eseguito alcun aggiornamento.

Il **[!UICONTROL Advanced parameters]** collegamento consente di specificare opzioni aggiuntive per l&#39;aggiornamento dei dati e la gestione dei duplicati. È inoltre possibile:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Questa opzione è selezionata automaticamente per impostazione predefinita.
* **[!UICONTROL Update all columns with matching names]**.
* Specificare le condizioni che considerano gli elementi di origine mediante un&#39;espressione nel **[!UICONTROL Enabled if]** campo.
* Specificare le condizioni che considerano i duplicati utilizzando un&#39;espressione. Se selezionate l&#39; **[!UICONTROL Ignore records which concern the same target]** opzione, verrà considerata solo la prima delle espressioni dell&#39;elenco.

**[!UICONTROL Generate an outbound transition]**

Crea una transizione in uscita che verrà attivata al termine dell&#39;esecuzione. In genere, l&#39;aggiornamento indica la fine di un flusso di lavoro di targeting, pertanto l&#39;opzione non è attivata per impostazione predefinita.

**[!UICONTROL Generate an outbound transition for the rejects]**

Crea una transizione in uscita contenente record che non sono stati elaborati correttamente dopo l&#39;aggiornamento (ad esempio, se è presente un duplicato). L&#39;aggiornamento in genere segna la fine di un flusso di lavoro di targeting e pertanto l&#39;opzione non è attivata per impostazione predefinita.

## Aggiornamento e unione delle raccolte {#updating-and-merging-collections}

L&#39;aggiornamento dei dati e l&#39;unione delle raccolte consente di aggiornare i dati contenuti in un record utilizzando i dati di uno o più record secondari, allo scopo di mantenerne uno solo se lo si desidera. Questi aggiornamenti sono gestiti da un set di regole.

>[!NOTE]
>
>Questa opzione consente inoltre di elaborare riferimenti a record secondari da tabelle di lavoro del flusso di lavoro (targetWorkflow), consegne (targetDelivery) ed elenchi (targetList). Se necessario, questi collegamenti vengono visualizzati nell&#39;elenco in cui si selezionano campi e raccolte.

1. Selezionare l&#39; **[!UICONTROL Update and merge collections]** operazione.

   ![](assets/update_and_merge_collections1.png)

1. Selezionare l&#39;ordine di priorità per i collegamenti. Questo consente di identificare il record principale. I collegamenti disponibili variano a seconda della transizione in entrata.

   ![](assets/update_and_merge_collections2.png)

1. Selezionate le raccolte da spostare al record principale e i campi da aggiornare.

   Immettere le regole che si applicano a questi record secondari una o più volte identificati. A questo scopo, potete utilizzare il generatore di espressioni. For more on this, refer to this [section](../../platform/using/defining-filter-conditions.md#building-expressions). Ad esempio, specificando che si tratta del valore aggiornato più recente tra tutti i diversi record da conservare.

   Quindi immettete le condizioni da prendere in considerazione per la regola.

   Infine, specificate il tipo di aggiornamento da eseguire. Ad esempio, è possibile scegliere di eliminare i record secondari dopo aver aggiornato i dati.

   Ad esempio, potete configurare l&#39;unione di raccolte contenenti dati eterogenei, come l&#39;elenco di sottoscrizioni per un destinatario. Utilizzando le regole, puoi anche creare nuove storie di iscrizione dalle sottoscrizioni di record secondari, oppure spostare l&#39;elenco di sottoscrizioni da un record secondario a un record primario.

1. Specificare l&#39;ordine in cui si desidera elaborare i record secondari, selezionando **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

I dati per i record secondari sono associati al record principale se sono applicabili le regole definite. In base al tipo di aggiornamento selezionato, i record secondari possono essere eliminati.

## Esempio: Aggiornamento dei dati a seguito di un arricchimento {#example--update-data-following-an-enrichment}

Il [passo 2: La scrittura di dati arricchiti nella sezione &quot;Acquisti&quot; della tabella](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) del caso d&#39;uso, in cui i dettagli relativi alla creazione di un elenco di ricap, offre un esempio di aggiornamento dei dati dopo un&#39;attività di arricchimento.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.
