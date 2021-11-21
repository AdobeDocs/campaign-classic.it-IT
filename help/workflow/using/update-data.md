---
product: campaign
title: Attività Update data
description: Ulteriori informazioni sull’attività del flusso di lavoro Update data
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 9f5735d2-73b8-469f-bc10-482c99cdd4a1
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 2%

---

# Attività Update data{#update-data}

![](../../assets/common.svg)

Un **Update data** L’attività -type esegue un aggiornamento di massa dei campi nel database.

## Tipo di operazione {#operation-type}

La **[!UICONTROL Operation type]** consente di scegliere il processo da eseguire sui dati del database:

* **[!UICONTROL Insert or update]**: aggiungi dati o aggiornali se sono già stati aggiunti.
* **[!UICONTROL Insert]**: aggiungi solo dati.
* **[!UICONTROL Update]**: aggiorna solo i dati.
* **[!UICONTROL Update and merge collections]**: aggiorna i dati e scegli un record principale, quindi collega gli elementi collegati ai duplicati in questo record principale. I duplicati possono quindi essere eliminati senza creare elementi orfani collegati.
* **[!UICONTROL Delete]**: elimina i dati.

![](assets/s_advuser_update_data_1.png)

La **[!UICONTROL Batch size]** consente di selezionare il numero di elementi di transizione in entrata da aggiornare. Ad esempio, se dici 500, i primi 500 record trattati verranno aggiornati.

## Identificazione del record {#record-identification}

Specifica come identificare i record nel database:

* Se le voci di dati si riferiscono a una dimensione di targeting esistente, seleziona la **[!UICONTROL By directly using the targeting dimension]** e selezionala nel **[!UICONTROL Updated dimension]** campo .

   Puoi visualizzare i campi per la dimensione selezionata utilizzando **[!UICONTROL Edit this link]** pulsante lente di ingrandimento.

* In caso contrario, specifica uno o più collegamenti che consentano l’identificazione dei dati nel database o l’uso diretto delle chiavi di riconciliazione.

![](assets/s_advuser_update_data_2.png)

## Selezione dei campi da aggiornare {#selecting-the-fields-to-be-updated}

Utilizza la **[!UICONTROL Automatically associate fields with the same name]** affinché Adobe Campaign identifichi automaticamente i campi da aggiornare.

![](assets/s_advuser_update_data_3b.png)

È inoltre possibile utilizzare **[!UICONTROL Insert]** per selezionare manualmente i campi del database da aggiornare.

![](assets/s_advuser_update_data_3.png)

Seleziona tutti i campi da aggiornare e, se necessario, aggiungi condizioni in base a quale deve essere eseguito l’aggiornamento. A questo scopo, utilizza la colonna **[!UICONTROL Taken into account if]**. Le condizioni sono applicate una dopo l&#39;altra e in linea con l&#39;ordine nell&#39;elenco. Utilizza le frecce a destra per cambiare l’ordine degli aggiornamenti.

È possibile utilizzare più volte lo stesso campo di destinazione.

All&#39;interno di un **[!UICONTROL Insert or update]** Puoi selezionare la campagna da applicare, singolarmente o per ogni campo. A questo scopo, seleziona il valore desiderato nel **[!UICONTROL Operation]** colonna.

![](assets/s_advuser_update_data_5.png)

La **[!UICONTROL modifiedDate]**, **[!UICONTROL modifiedBy]**, **[!UICONTROL createdDate]** e **[!UICONTROL createdBy]** i campi vengono aggiornati automaticamente durante gli aggiornamenti dei dati, a meno che la relativa modalità di gestione non sia configurata specificatamente nella tabella di aggiornamento dei campi.

L&#39;aggiornamento del record viene eseguito solo per i record contenenti almeno una differenza. Se i valori sono uguali, non viene eseguito alcun aggiornamento.

La **[!UICONTROL Advanced parameters]** link ti consente di specificare opzioni aggiuntive per gestire l’aggiornamento dei dati e la gestione dei duplicati. Puoi anche:

* **[!UICONTROL Disable automatic key management]**.
* **[!UICONTROL Disable audit]**.
* **[!UICONTROL Empty the destination value if the source value is empty (NULL)]**. Questa opzione è selezionata automaticamente per impostazione predefinita.
* **[!UICONTROL Update all columns with matching names]**.
* Specifica le condizioni che considerano gli elementi di origine che utilizzano un&#39;espressione nel **[!UICONTROL Enabled if]** campo .
* Specifica le condizioni che considerano i duplicati utilizzando un’espressione. Se controlli la **[!UICONTROL Ignore records which concern the same target]** , verrà considerata solo la prima delle espressioni dell’elenco.

**[!UICONTROL Generate an outbound transition]**

Crea una transizione in uscita che verrà attivata al termine dell’esecuzione. L’aggiornamento di solito segnala la fine di un flusso di lavoro di targeting e pertanto l’opzione non viene attivata per impostazione predefinita.

**[!UICONTROL Generate an outbound transition for the rejects]**

Crea una transizione in uscita contenente record che non sono stati elaborati correttamente dopo l’aggiornamento (ad esempio, se è presente un duplicato). L’aggiornamento in genere segna la fine di un flusso di lavoro di targeting e pertanto l’opzione non è attivata per impostazione predefinita.

## Aggiornamento e unione delle raccolte {#updating-and-merging-collections}

L’aggiornamento dei dati e l’unione delle raccolte consente di aggiornare i dati contenuti in un record utilizzando i dati di uno o più record secondari, allo scopo di conservarne uno solo se lo desideri. Questi aggiornamenti sono gestiti da un set di regole.

>[!NOTE]
>
>Questa opzione consente inoltre di elaborare i riferimenti ai record secondari dalle tabelle di lavoro del flusso di lavoro (targetWorkflow), dalle consegne (targetDelivery) e dagli elenchi (targetList). Se necessario, questi collegamenti vengono visualizzati nell’elenco in cui si selezionano campi e raccolte.

1. Seleziona la **[!UICONTROL Update and merge collections]** funzionamento.

   ![](assets/update_and_merge_collections1.png)

1. Seleziona l’ordine di priorità per i collegamenti. Ciò ti consente di identificare il record principale. I collegamenti disponibili variano a seconda della transizione in entrata.

   ![](assets/update_and_merge_collections2.png)

1. Selezionare le raccolte da spostare al record principale e i campi da aggiornare.

   Immettere le regole che si applicano a questi record secondari una o più volte identificati. A questo scopo, puoi utilizzare il Generatore di espressioni. Per ulteriori informazioni, consulta questa [sezione](../../platform/using/defining-filter-conditions.md#building-expressions). Ad esempio, specificando che si tratta del valore aggiornato più di recente tra tutti i diversi record che devono essere conservati.

   Quindi inserisci le condizioni da prendere in considerazione per la regola.

   Infine, specifica il tipo di aggiornamento da eseguire. Ad esempio, puoi scegliere di eliminare i record secondari dopo l’aggiornamento dei dati.

   Ad esempio, puoi configurare l’unione di raccolte contenenti dati eterogenei, ad esempio l’elenco delle sottoscrizioni per un destinatario. Utilizzando le regole, puoi anche creare nuove storie di abbonamento da sottoscrizioni di record secondari o persino spostare l’elenco di sottoscrizioni da un record secondario a un record principale.

1. Specificare l&#39;ordine di elaborazione dei record secondari selezionando **[!UICONTROL Advanced parameters]** > **[!UICONTROL Duplicates]**.

   ![](assets/update_and_merge_collections3.png)

I dati per i record secondari sono associati al record principale se sono applicabili le regole definite. A seconda del tipo di aggiornamento selezionato, i record secondari possono essere eliminati.

## Esempio: Aggiornare i dati dopo un arricchimento {#example--update-data-following-an-enrichment}

La [Passaggio 2: Scrittura di dati arricchiti nella tabella &quot;Acquisti&quot;](creating-a-summary-list.md#step-2--writing-enriched-data-to-the--purchases--table) sezione del caso d’uso che descrive la creazione di un elenco di ricap offre un esempio di aggiornamento dei dati dopo un’attività di arricchimento.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.
