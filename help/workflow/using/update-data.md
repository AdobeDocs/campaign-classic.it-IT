---
solution: Campaign Classic
product: campaign
title: Update data
description: Ulteriori informazioni sull'attività del flusso di lavoro Aggiorna dati
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---


# Update data{#update-data}

Un&#39;attività di tipo **Update data** esegue un aggiornamento di massa dei campi nel database.

## Tipo di operazione {#operation-type}

Il campo **[!UICONTROL Operation type]** consente di scegliere il processo da eseguire sui dati del database:

* **[!UICONTROL Insert or update]**: aggiungere dati o aggiornarli se sono già stati aggiunti.
* **[!UICONTROL Insert]**: aggiungi solo dati.
* **[!UICONTROL Update]**: aggiorna solo i dati.
* **[!UICONTROL Update and merge collections]**: aggiorna i dati e scegli un record principale, quindi collega gli elementi collegati ai duplicati in questo record primario. I duplicati possono quindi essere eliminati senza creare elementi associati orfani.
* **[!UICONTROL Delete]**: elimina i dati.

![](assets/s_advuser_update_data_1.png)

Il campo **[!UICONTROL Batch size]** consente di selezionare il numero di elementi di transizione in entrata da aggiornare. Ad esempio, se specifichi 500, i primi 500 record trattati verranno aggiornati.

## Identificazione del record {#record-identification}

Specificare come identificare i record nel database:

* Se le voci di dati si riferiscono a una dimensione di targeting esistente, selezionare l&#39;opzione **[!UICONTROL By directly using the targeting dimension]** e selezionarla nel campo **[!UICONTROL Updated dimension]**.

   È possibile visualizzare i campi per la dimensione selezionata utilizzando il pulsante lente di ingrandimento **[!UICONTROL Edit this link]**.

* In caso contrario, specificare uno o più collegamenti che consentano l&#39;identificazione dei dati nel database o l&#39;uso diretto delle chiavi di riconciliazione.

![](assets/s_advuser_update_data_2.png)

## Selezione dei campi da aggiornare {#selecting-the-fields-to-be-updated}

Utilizzate l&#39;opzione **[!UICONTROL Automatically associate fields with the same name]** per  Adobe Campaign per identificare automaticamente i campi da aggiornare.

![](assets/s_advuser_update_data_3b.png)

È inoltre possibile utilizzare l&#39;icona **[!UICONTROL Insert]** per selezionare manualmente i campi del database da aggiornare.

![](assets/s_advuser_update_data_3.png)

Selezionate tutti i campi da aggiornare e, se necessario, aggiungete le condizioni in base alle quali eseguire l&#39;aggiornamento. A questo scopo, utilizza la colonna **[!UICONTROL Taken into account if]**. Le condizioni vengono applicate una dopo l&#39;altra e in conformità con l&#39;ordine nell&#39;elenco. Utilizzate le frecce a destra per cambiare l&#39;ordine degli aggiornamenti.

È possibile utilizzare lo stesso campo di destinazione più volte.

All&#39;interno di un&#39;operazione **[!UICONTROL Insert or update]**, potete selezionare la campagna da applicare, singolarmente o per ciascun campo. A questo scopo, selezionate il valore desiderato nella colonna **[!UICONTROL Operation]**.

![](assets/s_advuser_update_data_5.png)

I campi **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** e **[!UICONTROL createdBy]** vengono aggiornati automaticamente durante gli aggiornamenti dei dati, a meno che la relativa modalità di gestione non sia configurata specificatamente nella tabella di aggiornamento del campo.

L&#39;aggiornamento dei record viene eseguito solo per i record contenenti almeno una differenza. Se i valori sono identici, non viene eseguito alcun aggiornamento.

Il collegamento **[!UICONTROL Advanced parameters]** consente di specificare opzioni aggiuntive per l&#39;aggiornamento dei dati e la gestione dei duplicati. È inoltre possibile:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Questa opzione è selezionata automaticamente per impostazione predefinita.
* **[!UICONTROL Update all columns with matching names]**.
* Specificate le condizioni che considerano gli elementi di origine mediante un&#39;espressione nel campo **[!UICONTROL Enabled if]**.
* Specificare le condizioni che considerano i duplicati utilizzando un&#39;espressione. Se si seleziona l&#39;opzione **[!UICONTROL Ignore records which concern the same target]**, verrà considerato solo il primo nell&#39;elenco di espressioni.

**[!UICONTROL Generate an outbound transition]**

Crea una transizione in uscita che verrà attivata al termine dell&#39;esecuzione. In genere, l&#39;aggiornamento indica la fine di un flusso di lavoro di targeting, pertanto l&#39;opzione non è attivata per impostazione predefinita.

**[!UICONTROL Generate an outbound transition for the rejects]**

Crea una transizione in uscita contenente record che non sono stati elaborati correttamente dopo l&#39;aggiornamento (ad esempio, se è presente un duplicato). L&#39;aggiornamento in genere segna la fine di un flusso di lavoro di targeting e di conseguenza l&#39;opzione non è attivata per impostazione predefinita.

## Aggiornamento e unione delle raccolte {#updating-and-merging-collections}

L&#39;aggiornamento dei dati e l&#39;unione delle raccolte consente di aggiornare i dati contenuti in un record utilizzando i dati di uno o più record secondari, allo scopo di mantenerne uno solo se lo si desidera. Questi aggiornamenti sono gestiti da un set di regole.

>[!NOTE]
>
>Questa opzione consente inoltre di elaborare riferimenti a record secondari da tabelle di lavoro del flusso di lavoro (targetWorkflow), consegne (targetDelivery) ed elenchi (targetList). Se necessario, questi collegamenti vengono visualizzati nell&#39;elenco in cui si selezionano campi e raccolte.

1. Selezionare l&#39;operazione **[!UICONTROL Update and merge collections]**.

   ![](assets/update_and_merge_collections1.png)

1. Selezionare l&#39;ordine di priorità per i collegamenti. Questo consente di identificare il record principale. I collegamenti disponibili variano a seconda della transizione in entrata.

   ![](assets/update_and_merge_collections2.png)

1. Selezionate le raccolte da spostare al record principale e i campi da aggiornare.

   Immettere le regole che si applicano a questi record secondari una o più volte identificati. A questo scopo, potete utilizzare il generatore di espressioni. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/defining-filter-conditions.md#building-expressions). Ad esempio, specificando che si tratta del valore aggiornato più recente tra tutti i diversi record da conservare.

   Quindi immettete le condizioni da prendere in considerazione per la regola.

   Infine, specificate il tipo di aggiornamento da eseguire. Ad esempio, è possibile scegliere di eliminare i record secondari dopo l&#39;aggiornamento dei dati.

   Ad esempio, potete configurare l&#39;unione di raccolte contenenti dati eterogenei, come l&#39;elenco di sottoscrizioni per un destinatario. Utilizzando le regole, puoi anche creare nuove storie di iscrizione dalle sottoscrizioni di record secondari, oppure spostare l&#39;elenco di sottoscrizioni da un record secondario a un record primario.

1. Specificare l&#39;ordine in cui si desidera elaborare i record secondari, selezionando **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

I dati per i record secondari sono associati al record principale se sono applicabili le regole definite. In base al tipo di aggiornamento selezionato, i record secondari possono essere eliminati.

## Esempio: Aggiornamento dei dati in seguito a un arricchimento {#example--update-data-following-an-enrichment}

Il [passo 2: La scrittura di dati arricchiti nella sezione &quot;Acquisti&quot; della tabella](../../workflow/using/creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) del caso d&#39;uso che descrive in dettaglio la creazione di un elenco di ricap offre un esempio di aggiornamento dei dati dopo un&#39;attività di arricchimento.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.
