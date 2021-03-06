---
product: campaign
title: Gestione delle enumerazioni
description: Gestione delle enumerazioni
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 2ece058d-b493-4fea-b3db-322cf7ea7f4f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---

# Gestire le enumerazioni{#managing-enumerations}

![](../../assets/common.svg)

Un&#39;enumerazione (nota anche come &quot;elenco dettagliato&quot;) è un elenco di valori suggeriti dal sistema per compilare alcuni campi. Le enumerazioni ti consentono di standardizzare i valori di questi campi e di utilizzare i dati immessi o utilizzati all’interno delle query.

L’elenco dei valori viene visualizzato come elenco a discesa dal quale è possibile selezionare il valore da immettere nel campo. L’elenco a discesa abilita anche l’input predittivo, in cui l’operatore immette le prime lettere, e l’applicazione compila il resto.

Alcuni dei campi della console sono stati definiti con questo tipo di enumerazioni. Le enumerazioni sono denominate &quot;open&quot; se è possibile aggiungere valori mediante input diretto nel campo corrispondente.

## Accesso ai valori {#access-to-values}

I valori per questo tipo di campo sono definiti e l’amministrazione complessiva di questi campi (aggiunta/eliminazione di un valore) viene eseguita tramite la **[!UICONTROL Administration > Platform > Enumerations]** nodo dell&#39;albero.

![](assets/s_ncs_user_itemized_list_node.png)

* Nella sezione superiore è disponibile un elenco di campi per i quali è stato definito un elenco dettagliato.
* Nella sezione inferiore sono elencati i valori proposti. Questi valori verranno ripetuti negli editor che utilizzano questo campo.

   ![](assets/s_ncs_user_itemized_list_values.png)

   Per creare un nuovo valore di enumerazione, fai clic su **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_itemized_list.png)

   Se la **[!UICONTROL Open]** se è selezionata, l’utente può aggiungere un nuovo valore di elenco con elementi direttamente nel campo corrispondente. Un messaggio di conferma ti consente di creare questo valore.

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* Se la **[!UICONTROL Closed]** è selezionata l’opzione , gli utenti non saranno in grado di creare nuovi valori, ma semplicemente di scegliere tra i valori disponibili.

## Standardizzazione dei dati {#standardizing-data}

### Informazioni sulla pulizia degli alias {#about-alias-cleansing}

Nei campi elenco dettagliati è possibile immettere valori diversi dai valori di enumerazione. Questi possono essere conservati come sono o essere puliti.

>[!CAUTION]
>
>La pulizia dei dati è un processo critico che influisce sui dati presenti nel database. Adobe Campaign esegue aggiornamenti di massa dei dati, che possono causare l’eliminazione di alcuni valori. Questa operazione è pertanto riservata agli utenti esperti.

Il valore immesso può quindi essere:

* Aggiunto ai valori elenco dettagliati: in questo caso **[!UICONTROL Open]** deve essere selezionata,
* o automaticamente sostituito dal relativo alias corrispondente: In questo caso, questo caso deve essere definito nella **[!UICONTROL Alias]** scheda dell’elenco dettagliato,
* o è memorizzato nell&#39;elenco degli alias: un alias da assegnare successivamente.

   >[!NOTE]
   >
   >Se devi utilizzare le funzionalità di pulizia dei dati, seleziona la **[!UICONTROL Alias cleansing]** nell’elenco dettagliato.

### Utilizzo degli alias {#using-aliases}

Opzione **[!UICONTROL Alias cleansing]** consente di utilizzare gli alias per l’elenco di elementi selezionato. Quando questa opzione è selezionata, la **[!UICONTROL Alias]** viene visualizzata nella parte inferiore della finestra.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Creare un alias {#creating-an-alias}

Per creare un alias, fai clic su **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Inserisci l’alias da convertire e il valore da applicare e fai clic su **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Controlla i parametri prima di confermare questa operazione.

>[!CAUTION]
>
>Una volta confermata questa fase, i valori precedentemente inseriti potrebbero non essere recuperati: sono stati sostituiti.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

Pertanto, quando un utente immette il valore **NEILSEN** in un campo &quot;azienda&quot; (nella console Adobe Campaign o in un modulo), viene automaticamente sostituito dal valore **NIELSEN Ltd**. La sostituzione del valore viene eseguita dal **Pulizia degli alias** workflow. Fai riferimento a [Eseguire la pulizia dei dati](#running-data-cleansing).

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Conversione dei valori in alias {#converting-values-into-aliases}

Per convertire un valore di enumerazione in un alias, fare clic con il pulsante destro del mouse nell&#39;elenco dei valori e scegliere **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Scegli i valori da convertire e fai clic su **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Fai clic su **[!UICONTROL Start]** per eseguire la conversione.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

Una volta completata l’esecuzione, l’alias viene aggiunto all’elenco degli alias.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Recupera hit alias {#retrieving-alias-hits}

I valori immessi dagli utenti possono essere convertiti in alias. In effetti, quando l’utente immette un valore che non è incluso nell’elenco dettagliato, il valore viene memorizzato nella variabile **[!UICONTROL Alias]** scheda .

La **Pulizia degli alias** il flusso di lavoro tecnico recupera questi valori ogni notte per aggiornare l’elenco dettagliato. Fai riferimento a [Eseguire la pulizia dei dati](#running-data-cleansing)

Se necessario, il **[!UICONTROL Hits]** può visualizzare il numero di volte in cui è stato immesso questo valore. Il calcolo di questo valore può richiedere tempo e memoria. Per ulteriori informazioni, consulta [Calcola occorrenze di immissione](#calculating-entry-occurrences).

### Eseguire la pulizia dei dati {#running-data-cleansing}

La pulizia dei dati viene eseguita dal **[!UICONTROL Alias cleansing]** flusso di lavoro tecnico. Le configurazioni definite per le enumerazioni vengono applicate durante l&#39;esecuzione. Fai riferimento a [Flusso di lavoro di pulizia degli alias](#alias-cleansing-workflow).

La pulizia può essere attivata tramite il **[!UICONTROL Cleanse values...]** link.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

La **[!UICONTROL Advanced parameters...]** link ti consente di impostare la data a partire dalla quale vengono presi in considerazione i valori raccolti.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Fai clic sul pulsante **[!UICONTROL Start]** pulsante per eseguire la pulizia dei dati.

#### Calcola occorrenze di immissione {#calculating-entry-occurrences}

La **[!UICONTROL Alias]** la sottoscheda di un elenco dettagliato può visualizzare il numero di occorrenze di un alias tra tutti i valori immessi. Queste informazioni sono una stima e verranno visualizzate nella **[!UICONTROL Hits]** colonna.

>[!CAUTION]
>
>Il calcolo delle occorrenze delle voci di alias può richiedere molto tempo. Per questo motivo occorre prestare attenzione quando si utilizza questa funzione.

Puoi eseguire manualmente il calcolo degli hit tramite **[!UICONTROL Cleanse values...]** link. A questo scopo, fai clic sul pulsante **[!UICONTROL Advanced parameters...]** e seleziona le opzioni desiderate.

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: questo consente di aggiornare gli hit già calcolati in base alla data immessa.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: consente di eseguire il calcolo sull’intera piattaforma Adobe Campaign.

È inoltre possibile creare un flusso di lavoro dedicato affinché il calcolo venga eseguito automaticamente per un determinato periodo, ad esempio una volta alla settimana.

A questo scopo, crea una copia del **[!UICONTROL Alias cleansing]** , modifica la pianificazione e utilizza le seguenti impostazioni nel **[!UICONTROL Enumeration value cleansing]** attività:

* **-updateHits** per aggiornare il numero di hit di alias,
* **-updateHits:full** per ricalcolare tutti gli hit di alias.

#### Flusso di lavoro di pulizia degli alias {#alias-cleansing-workflow}

La **Pulizia degli alias** workflow esegue la pulizia dei valori delle enumerazioni. Per impostazione predefinita viene eseguito su base giornaliera.

È accessibile tramite il **[!UICONTROL Administration > Production > Technical workflows]** nodo.

![](assets/s_ncs_user_itemized_list_alias_wf.png)
