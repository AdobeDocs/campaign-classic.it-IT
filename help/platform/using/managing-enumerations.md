---
product: campaign
title: Gestione delle enumerazioni
description: Gestione delle enumerazioni
feature: Data Management
badge: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 2ece058d-b493-4fea-b3db-322cf7ea7f4f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '882'
ht-degree: 0%

---

# Gestire le enumerazioni{#managing-enumerations}



Un&#39;enumerazione (nota anche come &#39;elenco dettagliato&#39;) è un elenco di valori suggeriti dal sistema per compilare alcuni campi. Le enumerazioni consentono di standardizzare i valori di questi campi e di semplificare l&#39;immissione di dati o l&#39;utilizzo all&#39;interno di query.

L&#39;elenco di valori viene visualizzato come elenco a discesa dal quale è possibile selezionare il valore da immettere nel campo. L’elenco a discesa consente inoltre l’input predittivo, in cui l’operatore immette le prime lettere e l’applicazione compila il resto.

Alcuni campi della console sono stati definiti con questo tipo di enumerazioni. Le enumerazioni sono denominate &quot;open&quot; se è possibile aggiungere valori tramite input diretto nel campo corrispondente.

## Accesso ai valori {#access-to-values}

I valori per questo tipo di campo sono definiti e l’amministrazione complessiva di questi campi (aggiunta/eliminazione di un valore) viene eseguita tramite **[!UICONTROL Administration > Platform > Enumerations]** dell&#39;albero.

![](assets/s_ncs_user_itemized_list_node.png)

* La sezione superiore offre un elenco di campi per i quali è stato definito un elenco dettagliato.
* Nella sezione inferiore sono elencati i valori proposti. Questi valori verranno ripetuti negli editor che utilizzano questo campo.

  ![](assets/s_ncs_user_itemized_list_values.png)

  Per creare un nuovo valore di enumerazione, fai clic su **[!UICONTROL Add]**.

  ![](assets/s_ncs_user_itemized_list.png)

  Se il **[!UICONTROL Open]** è selezionata, l’utente può aggiungere un nuovo valore di elenco dettagliato direttamente nel campo corrispondente. Un messaggio di conferma ti consente di creare questo valore.

  ![](assets/s_ncs_user_itemized_list_new_value.png)

* Se il **[!UICONTROL Closed]** è selezionata, gli utenti non potranno creare nuovi valori, ma potranno semplicemente scegliere tra quelli disponibili.

## Standardizzare i dati {#standardizing-data}

### Informazioni sulla pulizia degli alias {#about-alias-cleansing}

Nei campi elenco dettagliati è possibile immettere valori diversi da quelli di enumerazione. Questi possono essere memorizzati così come sono o essere puliti.

>[!CAUTION]
>
>La pulizia dei dati è un processo critico che influisce sui dati presenti nel database. Adobe Campaign esegue aggiornamenti di massa dei dati, che potrebbero causare l’eliminazione di alcuni valori. Questa operazione è pertanto riservata agli utenti esperti.

Il valore immesso è quindi:

* Sono stati aggiunti ai valori dell’elenco dettagliati: in questo caso, il **[!UICONTROL Open]** deve essere selezionata,
* o automaticamente sostituito dal relativo alias corrispondente: in questo caso, il caso deve essere definito nel **[!UICONTROL Alias]** scheda dell’elenco dettagliato,
* o viene memorizzato nell’elenco degli alias: gli verrà successivamente assegnato un alias.

  >[!NOTE]
  >
  >Se devi utilizzare le funzionalità di pulizia dei dati, seleziona la **[!UICONTROL Alias cleansing]** nell&#39;elenco dettagliato.

### Utilizzo degli alias {#using-aliases}

Opzione **[!UICONTROL Alias cleansing]** consente di utilizzare alias per l&#39;elenco dettagliato selezionato. Quando questa opzione è selezionata, il **[!UICONTROL Alias]** nella parte inferiore della finestra.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Creare un alias {#creating-an-alias}

Per creare un alias, fare clic su **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Immettere l&#39;alias che si desidera convertire e il valore da applicare e fare clic su **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Controlla i parametri prima di confermare questa operazione.

>[!CAUTION]
>
>Una volta confermata questa fase, i valori precedentemente immessi potrebbero non essere recuperati: sono stati sostituiti.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

Pertanto, quando un utente immette il valore **NEILSEN** in un campo &quot;azienda&quot; (nella console Adobe Campaign o in un modulo), verrà automaticamente sostituito dal valore **NIELSEN Ltd.**. La sostituzione del valore viene eseguita da **Pulizia alias** flusso di lavoro. Fai riferimento a [Esegui pulizia dati](#running-data-cleansing).

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Conversione di valori in alias {#converting-values-into-aliases}

Per convertire un valore di enumerazione in un alias, fare clic con il pulsante destro del mouse nell&#39;elenco di valori e scegliere **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Scegliere i valori da convertire e fare clic su **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Clic **[!UICONTROL Start]** per eseguire la conversione.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

Al termine dell’esecuzione, l’alias viene aggiunto all’elenco degli alias.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Recuperare gli hit alias {#retrieving-alias-hits}

I valori immessi dagli utenti possono essere convertiti in alias. In effetti, quando l’utente immette un valore non incluso nell’elenco dettagliato, il valore viene memorizzato in **[!UICONTROL Alias]** scheda.

Il **Pulizia alias** il flusso di lavoro tecnico recupera questi valori ogni notte per aggiornare l’elenco dettagliato. Fai riferimento a [Esegui pulizia dati](#running-data-cleansing)

Se necessario, il **[!UICONTROL Hits]** può visualizzare il numero di volte in cui questo valore è stato immesso. Il calcolo di questo valore può richiedere tempo e memoria. Per ulteriori informazioni, consulta [Calcola occorrenze voce](#calculating-entry-occurrences).

### Esegui pulizia dati {#running-data-cleansing}

La pulizia dei dati viene eseguita da **[!UICONTROL Alias cleansing]** flusso di lavoro tecnico. Le configurazioni definite per le enumerazioni vengono applicate durante l’esecuzione. Fai riferimento a [Flusso di lavoro di pulizia degli alias](#alias-cleansing-workflow).

La pulizia può essere attivata tramite **[!UICONTROL Cleanse values...]** collegamento.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

Il **[!UICONTROL Advanced parameters...]** Questo collegamento ti consente di impostare la data a partire dalla quale i valori raccolti vengono presi in considerazione.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Fai clic su **[!UICONTROL Start]** per eseguire la pulizia dei dati.

#### Calcola occorrenze voce {#calculating-entry-occurrences}

Il **[!UICONTROL Alias]** scheda secondaria di un elenco dettagliato può visualizzare il numero di occorrenze di un alias tra tutti i valori immessi. Queste informazioni sono una stima e verranno visualizzate nel **[!UICONTROL Hits]** colonna.

>[!CAUTION]
>
>Il calcolo delle occorrenze della voce alias può richiedere molto tempo. Per questo motivo è necessario prestare attenzione quando si utilizza questa funzione.

Puoi eseguire il calcolo degli hit manualmente tramite **[!UICONTROL Cleanse values...]** collegamento. A questo scopo, fai clic su **[!UICONTROL Advanced parameters...]** e seleziona le opzioni desiderate.

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: questo ti consente di aggiornare gli hit che sono già stati calcolati, in base alla data immessa.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: consente di eseguire calcoli sull’intera piattaforma Adobe Campaign.

Puoi anche creare un flusso di lavoro dedicato per consentire l’esecuzione automatica del calcolo per un determinato periodo, ad esempio una volta alla settimana.

A questo scopo, crea una copia di **[!UICONTROL Alias cleansing]** , modificare la pianificazione e utilizzare le impostazioni seguenti nel **[!UICONTROL Enumeration value cleansing]** attività:

* **-updateHits** per aggiornare il numero di hit alias,
* **-updateHits:completo** per ricalcolare tutti gli hit alias.

#### Flusso di lavoro di pulizia degli alias {#alias-cleansing-workflow}

Il **Pulizia alias** il flusso di lavoro esegue la pulizia dei valori delle enumerazioni. Per impostazione predefinita, viene eseguito su base giornaliera.

È accessibile tramite **[!UICONTROL Administration > Production > Technical workflows]** nodo.

![](assets/s_ncs_user_itemized_list_alias_wf.png)
