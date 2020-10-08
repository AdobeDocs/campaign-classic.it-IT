---
title: Gestione delle enumerazioni
seo-title: Gestione delle enumerazioni
description: Gestione delle enumerazioni
seo-description: null
page-status-flag: never-activated
uuid: 23ad4cae-237f-48e5-b111-cfe88cf0b864
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 7674c856-2b64-4a85-9ffa-3e14a142028e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 0%

---


# Gestione delle enumerazioni{#managing-enumerations}

## Informazioni sulle enumerazioni {#about-enumerations}

Un&#39;enumerazione (nota anche come &#39;elenco dettagliato&#39;) è un elenco di valori suggeriti dal sistema per compilare alcuni campi. Le enumerazioni consentono di standardizzare i valori di questi campi e aiutano nell&#39;immissione o nell&#39;uso dei dati all&#39;interno delle query.

L&#39;elenco di valori viene visualizzato come elenco a discesa dal quale è possibile selezionare il valore da immettere nel campo. L&#39;elenco a discesa consente inoltre l&#39;input predittivo, in cui l&#39;operatore immette le prime lettere, e l&#39;applicazione completa il resto.

Alcuni dei campi della console sono stati definiti con questo tipo di enumerazioni. Le enumerazioni sono denominate &quot;open&quot; se è possibile aggiungere valori mediante immissione diretta nel campo corrispondente.

## Accesso ai valori {#access-to-values}

I valori per questo tipo di campo sono definiti e l&#39;amministrazione generale di questi campi (aggiunta o eliminazione di un valore) viene eseguita tramite il **[!UICONTROL Administration > Platform > Enumerations]** nodo della struttura.

![](assets/s_ncs_user_itemized_list_node.png)

* Nella sezione superiore è disponibile un elenco di campi per i quali è stato definito un elenco dettagliato.
* Nella sezione inferiore sono elencati i valori proposti. Questi valori verranno ripetuti negli editor che utilizzano questo campo.

   ![](assets/s_ncs_user_itemized_list_values.png)

   Per creare un nuovo valore di enumerazione, fare clic su **[!UICONTROL Add]**.

   ![](assets/s_ncs_user_itemized_list.png)

   Se l&#39; **[!UICONTROL Open]** opzione è selezionata, l&#39;utente può aggiungere un nuovo valore elenco dettagliato direttamente nel campo corrispondente. Un messaggio di conferma consente di creare questo valore.

   ![](assets/s_ncs_user_itemized_list_new_value.png)

* Se l’ **[!UICONTROL Closed]** opzione è selezionata, gli utenti non saranno in grado di creare nuovi valori, ma semplicemente di scegliere tra i valori disponibili.

## Standardizzazione dei dati {#standardizing-data}

### Informazioni sulla pulizia degli alias {#about-alias-cleansing}

Nei campi elenco dettagliati è possibile immettere valori diversi dai valori di enumerazione. Possono essere memorizzati così come sono o essere puliti.

>[!CAUTION]
>
>La pulizia dei dati è un processo critico che interessa i dati presenti nel database.  Adobe Campaign esegue aggiornamenti di massa dei dati, che potrebbero causare l&#39;eliminazione di alcuni valori. Questa operazione è pertanto riservata agli utenti esperti.

Il valore immesso può essere:

* Aggiunto ai valori elenco dettagliati: in questo caso, l&#39; **[!UICONTROL Open]** opzione deve essere selezionata,
* o sostituito automaticamente dal relativo alias corrispondente: In questo caso, questo caso deve essere definito nella **[!UICONTROL Alias]** scheda dell&#39;elenco degli elementi,
* o è memorizzato nell&#39;elenco degli alias: un alias verrà assegnato successivamente.

   >[!NOTE]
   >
   >Se è necessario utilizzare le funzionalità di pulizia dei dati, selezionare l&#39; **[!UICONTROL Alias cleansing]** opzione nell&#39;elenco dettagliato.

### Utilizzo degli alias {#using-aliases}

Questa opzione **[!UICONTROL Alias cleansing]** consente di utilizzare gli alias per l&#39;elenco di elementi selezionato. Quando questa opzione è selezionata, la **[!UICONTROL Alias]** scheda viene visualizzata nella parte inferiore della finestra.

![](assets/s_ncs_user_itemized_list_alias_option.png)

#### Creazione di un alias {#creating-an-alias}

Per creare un alias, fare clic su **[!UICONTROL Add]**.

![](assets/s_ncs_user_itemized_list_alias_create.png)

Inserite l’alias da convertire e il valore da applicare e fate clic su **[!UICONTROL Ok]**.

![](assets/s_ncs_user_itemized_list_alias_create_2.png)

Controllare i parametri prima di confermare l&#39;operazione.

>[!CAUTION]
>
>Una volta confermata questa fase, i valori precedentemente inseriti non possono essere recuperati: sono stati sostituiti.

![](assets/s_ncs_user_itemized_list_alias_create_3.png)

Pertanto, quando un utente immette il valore **NEILSEN** in un campo &quot;società&quot; (nella console Adobe Campaign  o in un modulo), verrà automaticamente sostituito dal valore **NIELSEN Ltd**. La sostituzione del valore viene eseguita dal flusso di lavoro di pulizia **degli** alias. Fare riferimento a [Esecuzione della pulizia](#running-data-cleansing)dei dati.

![](assets/s_ncs_user_itemized_list_alias_use.png)

#### Conversione di valori in alias {#converting-values-into-aliases}

Per convertire un valore di enumerazione in un alias, fare clic con il pulsante destro del mouse nell&#39;elenco dei valori e scegliere **[!UICONTROL Convert values into aliases...]**.

![](assets/s_ncs_user_itemized_list_alias_detail.png)

Scegliete i valori da convertire e fate clic su **[!UICONTROL Next]**.

![](assets/s_ncs_user_itemized_list_alias_transform.png)

Fare clic **[!UICONTROL Start]** per eseguire la conversione.

![](assets/s_ncs_user_itemized_list_alias_detail1.png)

Una volta completata l&#39;esecuzione, l&#39;alias viene aggiunto all&#39;elenco degli alias.

![](assets/s_ncs_user_itemized_list_alias_detail2.png)

#### Recupero degli hit di alias {#retrieving-alias-hits}

I valori immessi dagli utenti possono essere convertiti in alias. In effetti, quando l&#39;utente immette un valore che non è incluso nell&#39;elenco dettagliato, il valore viene memorizzato nella **[!UICONTROL Alias]** scheda.

Il flusso di lavoro tecnico **di pulizia** alias recupera questi valori ogni notte per aggiornare l&#39;elenco dettagliato. Fare riferimento a [Esecuzione della pulizia dei dati](#running-data-cleansing)

Se necessario, la **[!UICONTROL Hits]** colonna può visualizzare il numero di volte in cui è stato immesso questo valore. Il calcolo di questo valore può richiedere tempo e memoria. Per ulteriori informazioni, vedere [Calcolo delle occorrenze](#calculating-entry-occurrences)delle voci.

### Esecuzione della pulizia dei dati {#running-data-cleansing}

La pulizia dei dati viene eseguita dal flusso di lavoro **[!UICONTROL Alias cleansing]** tecnico. Le configurazioni definite per le enumerazioni vengono applicate durante l&#39;esecuzione. Fare riferimento al flusso di lavoro [di pulizia](#alias-cleansing-workflow)degli alias.

La pulizia può essere attivata tramite il **[!UICONTROL Cleanse values...]** collegamento.

![](assets/s_ncs_user_itemized_list_alias_start_normalize.png)

Il **[!UICONTROL Advanced parameters...]** collegamento consente di impostare la data a partire dalla quale vengono presi in considerazione i valori raccolti.

![](assets/s_ncs_user_itemized_list_alias_normalize.png)

Fare clic sul **[!UICONTROL Start]** pulsante per eseguire la pulizia dei dati.

#### Calcolo delle occorrenze delle voci {#calculating-entry-occurrences}

La **[!UICONTROL Alias]** sottoscheda di un elenco dettagliato può visualizzare il numero di occorrenze di un alias tra tutti i valori immessi. Queste informazioni sono una stima e verranno visualizzate nella **[!UICONTROL Hits]** colonna.

>[!CAUTION]
>
>Il calcolo delle occorrenze delle voci di alias può richiedere molto tempo. È per questo che occorre prestare attenzione quando si utilizza questa funzione.

Puoi eseguire il calcolo degli hit manualmente tramite il **[!UICONTROL Cleanse values...]** collegamento. A questo scopo, fate clic sul **[!UICONTROL Advanced parameters...]** collegamento e selezionate le opzioni desiderate.

![](assets/s_ncs_user_itemized_list_alias_hits.png)

* **[!UICONTROL Update the number of alias hits]**: questo consente di aggiornare gli hit già calcolati, in base alla data immessa.
* **[!UICONTROL Recalculate the number of alias hits from the start]**: consente di eseguire il calcolo sull&#39;intera piattaforma  Adobe Campaign.

È inoltre possibile creare un flusso di lavoro dedicato per consentire l&#39;esecuzione automatica del calcolo per un determinato periodo, ad esempio una volta alla settimana.

A questo scopo, create una copia del **[!UICONTROL Alias cleansing]** flusso di lavoro, modificate l&#39;utilità di pianificazione e utilizzate le seguenti impostazioni nell&#39; **[!UICONTROL Enumeration value cleansing]** attività:

* **-updateHits** per aggiornare il numero di hit di alias,
* **-updateHits:full** per ricalcolare tutti gli hit di alias.

#### Flusso di lavoro di pulizia alias {#alias-cleansing-workflow}

Il flusso di lavoro di pulizia **degli** alias esegue la pulizia dei valori delle enumerazioni. Per impostazione predefinita, viene eseguito su base giornaliera.

È accessibile tramite il **[!UICONTROL Administration > Production > Technical workflows]** nodo.

![](assets/s_ncs_user_itemized_list_alias_wf.png)

