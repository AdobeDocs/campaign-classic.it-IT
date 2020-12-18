---
solution: Campaign Classic
product: campaign
title: Gestione delle risorse di marketing
description: Gestione delle risorse di marketing
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1384'
ht-degree: 1%

---


# Gestione delle risorse di marketing{#managing-marketing-resources}

 Adobe Campaign consente di gestire e monitorare le risorse di marketing coinvolte nel ciclo di vita della campagna. Queste risorse di marketing possono essere una brochure, un aiuto visivo o qualsiasi altro mezzo di comunicazione che coinvolga più operatori.

Per ogni risorsa di marketing gestita tramite  Adobe Campaign, puoi monitorarne lo stato e la cronologia in qualsiasi momento e visualizzare la versione corrente.

## Aggiunta di una risorsa di marketing {#adding-a-marketing-resource}

Le risorse di marketing sono accessibili tramite l&#39;universo Campagne.

Per aggiungere una risorsa, fate clic sul pulsante **[!UICONTROL Create]**.

![](assets/s_ncs_user_mkg_resource_add.png)

Per rendere disponibile una risorsa sul server Adobe Campaign , è necessario aggiungere la risorsa desiderata trascinandola nell’area centrale dell’editor. È inoltre possibile fare clic sul collegamento **[!UICONTROL Upload file to server...]**.

![](assets/s_ncs_user_mkg_resource_file.png)

Un messaggio di conferma consente di avviare il caricamento.

Al termine del caricamento, la risorsa viene aggiunta all’elenco delle risorse disponibili. È accessibile  operatori Adobe Campaign. Possono visualizzare il file (tramite la scheda **[!UICONTROL Preview]**), fare una copia per modificarlo o aggiornare il file sul server (utilizzando la scheda **[!UICONTROL Edit]**).

![](assets/s_ncs_user_mkg_resource_extract.png)

Fare clic sulla scheda **[!UICONTROL General]** per selezionare gli operatori o i gruppi di operatori responsabili del monitoraggio, del tracciamento e dell&#39;approvazione di questa risorsa. La selezione del revisore viene eseguita tramite il collegamento **[!UICONTROL Advanced parameters]**.

* L&#39;operatore a cui è assegnata la risorsa è responsabile del tracciamento.
* L&#39;operatore di approvazione è responsabile dell&#39;approvazione della risorsa di marketing. All&#39;avvio del processo di convalida delle risorse verrà inviata una notifica.

   Se non è selezionato alcun revisore, la risorsa **[!UICONTROL cannot be]** è soggetta all&#39;approvazione.

* Se necessario, potete anche specificare un lettore di prova.

È possibile specificare una data di disponibilità (indicativa) per la risorsa. Oltre tale data, verrà visualizzato con lo stato **[!UICONTROL Late]**.

## Lavoro collaborativo sulle risorse {#collaborative-work-on-resources}

Puoi modificare e aggiornare una risorsa di marketing e, se necessario, informarne altri operatori Adobe Campaign . Puoi:

* Scaricate la risorsa localmente per modificarla.
* Aggiornare il file sul server e renderlo accessibile ad altri operatori.
* Bloccare una risorsa per impedirne la modifica da parte di altri operatori.

>[!NOTE]
>
>La scheda **[!UICONTROL History]** contiene il registro di download e aggiornamento della risorsa. Il pulsante **[!UICONTROL Details]** consente di visualizzare la versione selezionata:

### Blocco/sblocco di una risorsa {#locking-unlocking-a-resource}

Una volta create, le risorse sono disponibili nel dashboard delle risorse di marketing e gli operatori possono modificarle.

Quando un operatore desidera lavorare su una risorsa, è preferibile bloccarla prima dell&#39;avvio del lavoro, per impedire ad altri operatori di modificarla allo stesso tempo. La risorsa viene quindi riservata; rimane accessibile, ma non può essere pubblicato o aggiornato sul server da un altro operatore.

Un messaggio speciale notifica agli operatori che tentano di accedervi:

![](assets/s_ncs_user_mkg_resource_locked.png)

La scheda **[!UICONTROL Tracking]** indica il nome dell&#39;operatore che ha bloccato la risorsa e la data di aggiornamento pianificata.

![](assets/s_ncs_user_mkg_resource_locked_date.png)

Per bloccare una risorsa, è necessario fare clic sulla risorsa seguita dal pulsante **[!UICONTROL Lock]** nel dashboard della risorsa.

![](assets/s_ncs_user_mkg_resource_lock.png)

È possibile indicare la data di restituzione pianificata nella scheda **[!UICONTROL Tracking]** della risorsa.

![](assets/s_ncs_user_mkg_resource_lock_date.png)

Queste informazioni consentono di informare  altri operatori Adobe Campaign della data in cui la risorsa verrà sbloccata.

Una volta aggiornata, la risorsa viene sbloccata automaticamente e resa nuovamente disponibile a tutti gli operatori.

Se necessario, potete anche sbloccarlo manualmente dal dashboard.

>[!NOTE]
>
>Solo l&#39;operatore che ha bloccato la risorsa e gli operatori con diritti di amministratore sono autorizzati a sbloccare una risorsa.

### Forum di discussione {#discussion-forums}

Per ogni risorsa, la scheda **[!UICONTROL Forum]** consente ai partecipanti di scambiare informazioni.

[Nei ](../../campaign/using/discussion-forums.md) forum di discussione viene illustrato come i forum di discussione funzionano in  Adobe Campaign.

## Ciclo di vita di una risorsa di marketing {#life-cycle-of-a-marketing-resource}

Quando viene creata la risorsa,  gli operatori Adobe Campaign vengono nominati per progettare, verificare, approvare e pubblicare la risorsa. È possibile determinare la durata di queste campagne.

La scheda **[!UICONTROL Tracking]** consente di monitorare tutte le azioni eseguite sulla risorsa: approvazioni, rifiuti di approvazione, commenti correlati o pubblicazioni.

Nella scheda **[!UICONTROL History]** sono visualizzati i trasferimenti di file eseguiti per questa risorsa.

### Processo di approvazione {#approval-process}

La data di disponibilità prevista viene visualizzata nei dettagli della risorsa, se specificata nella scheda **[!UICONTROL Tracking]**. Una volta raggiunta tale data, è possibile eseguire il processo di approvazione utilizzando il pulsante **[!UICONTROL Submit for approval]** nel dashboard delle risorse. Lo stato della risorsa diventa quindi **[!UICONTROL Approval in progress]**.

Una risorsa può essere approvata mediante il pulsante **[!UICONTROL Approve resource]** nel dashboard.

![](assets/s_ncs_user_task_valid_date.png)

Gli operatori autorizzati possono quindi accettare o rifiutare l&#39;approvazione. Questa azione è possibile: tramite il messaggio e-mail inviato (facendo clic sul collegamento nel messaggio di notifica) o tramite la console (facendo clic sul pulsante **[!UICONTROL Approve]** ).

La finestra di approvazione consente di inserire un commento.

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

La scheda **[!UICONTROL Tracking]** consente a tutti gli operatori di tenere traccia delle varie fasi del processo di approvazione.

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>Oltre al revisore specificato per ogni risorsa di marketing, gli operatori con diritti di amministratore e il gestore risorse sono autorizzati ad approvare una risorsa di marketing.

### Pubblicazione di una risorsa {#publishing-a-resource}

Una volta approvata, la risorsa marketing deve essere pubblicata. Il processo di pubblicazione deve essere soggetto a un&#39;implementazione specifica in base ai requisiti aziendali. Ciò significa che le risorse possono essere pubblicate su una rete extranet o su qualsiasi altro server, che informazioni specifiche possono essere inviate a un provider di servizi esterno, ecc.

Per pubblicare una risorsa, fate clic sul pulsante **[!UICONTROL Publish]** nella zona di modifica del dashboard delle risorse di marketing.

![](assets/s_ncs_user_mkg_resource_available.png)

Potete inoltre automatizzare la pubblicazione di una risorsa tramite un flusso di lavoro.

Pubblicare una risorsa significa renderla disponibile per l’uso (ad esempio, tramite un’altra attività). La pubblicazione varia a seconda della natura della risorsa: per un volantino, pubblicare può significare inviare il file a una stampante, per un&#39;agenzia Web, può significare pubblicarlo su un sito Web, ecc.

Affinché  Adobe Campaign possa pubblicare, è necessario creare un flusso di lavoro adeguato e collegarlo alla risorsa. A questo scopo, aprite la casella **[!UICONTROL Advanced settings]** della risorsa, quindi selezionate il flusso di lavoro desiderato nel campo **[!UICONTROL Post-processing]**.

![](assets/mrm_asset_postprocessing_workflow.png)

Il flusso di lavoro verrà eseguito:

* Quando il revisore fa clic sul collegamento **[!UICONTROL Publish resource]** (o, se non è stato definito alcun revisore, sulla persona responsabile della risorsa).
* Se la risorsa viene gestita tramite un&#39;attività di creazione delle risorse di marketing, verrà eseguita quando l&#39;attività è impostata su **[!UICONTROL Finished]**, purché la casella **[!UICONTROL Publish the marketing resource]** sia selezionata nell&#39;attività (fare riferimento a [Attività di creazione delle risorse di marketing](../../campaign/using/creating-and-managing-tasks.md#marketing-resource-creation-task))

Se un flusso di lavoro non viene avviato immediatamente (se ad esempio il flusso di lavoro viene interrotto), lo stato della risorsa cambia in **[!UICONTROL Pending publication]**. Una volta avviato il flusso di lavoro, lo stato della risorsa cambia in **[!UICONTROL Published]**. Questo stato non tiene conto di eventuali errori nel processo di pubblicazione. Controllate lo stato del flusso di lavoro per verificare che sia stato eseguito correttamente.

## Collegamento di una risorsa a una campagna {#linking-a-resource-to-a-campaign}

### Riferimento a una risorsa di marketing {#referencing-a-marketing-resource}

Le risorse di marketing possono essere associate alle campagne, a condizione che questa funzione sia stata selezionata nel modello di campagna.

>[!NOTE]
>
>Per informazioni dettagliate su come creare e configurare i modelli delle campagne, fare riferimento a [Modelli delle campagne](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Fate clic sulla scheda **[!UICONTROL Documents > Resources]** nel dashboard della campagna, quindi fate clic su **[!UICONTROL Add]** per selezionare la risorsa in questione.

![](assets/s_ncs_user_mkg_resource_ref.png)

Potete filtrare le risorse per stato, natura o tipo oppure applicare un filtro personalizzato.

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

Fate clic su **[!UICONTROL OK]** per aggiungere la risorsa all&#39;elenco delle risorse di marketing a cui viene fatto riferimento per questa campagna.

Il pulsante **[!UICONTROL Details]** consente di modificarlo e visualizzarlo.

Le risorse aggiunte vengono visualizzate nel dashboard. È inoltre possibile modificarli.

### Aggiunta di una risorsa di marketing a una struttura di consegna {#adding-a-marketing-resource-to-a-delivery-outline}

Le risorse di marketing possono essere associate alle consegne tramite i contorni di consegna.

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>Per ulteriori informazioni sui contorni di consegna, fare riferimento a [Associazione e strutturazione delle risorse collegate tramite un profilo di consegna](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## Gestione delle scorte {#stock-management}

Puoi associare una risorsa di marketing a una o più scorte per gestire le forniture e visualizzare un avviso sul dashboard in caso di scorte insufficienti.

>[!NOTE]
>
>Per ulteriori informazioni sulla gestione delle scorte in  Adobe Campaign, fare riferimento a [Gestione delle scorte](../../campaign/using/providers--stocks-and-budgets.md#stock-management).

Per associare una risorsa di marketing a una risorsa, modificate la mappa di magazzino e modificate o create una risorsa. Aggiungi una linea di azioni e seleziona la risorsa di marketing corrispondente.

![](assets/s_ncs_user_task_in_a_stock.png)

Se necessario, è possibile modificare la risorsa selezionata tramite l&#39;icona **[!UICONTROL Edit the link]** (lente di ingrandimento) situata a destra della risorsa una volta selezionata.

Specificate la risorsa iniziale e la risorsa di avviso, quindi salvate.

La risorsa è indicata nei dettagli della risorsa.

![](assets/s_ncs_user_task_with_a_stock.png)

Se lo stock è insufficiente, agli operatori interessati viene inviato un avviso.

## Funzioni avanzate {#advanced-functions}

Il dashboard delle risorse di marketing consente di eseguire i tipi di operazioni consueti: aggiungere, modificare, bloccare/sbloccare, approvare, pubblicare. Puoi creare altri tipi di risorse di marketing e accedere a funzionalità avanzate tramite la struttura  Adobe Campaign. A tale scopo, fare clic su **[!UICONTROL Explorer]** nella home page di  Adobe Campaign.

Per impostazione predefinita, le risorse di marketing sono memorizzate nel nodo **[!UICONTROL MRM > Marketing resources]** della struttura.

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

Da questa visualizzazione potete aggiungere le seguenti risorse:

* File
* HTML
* Testo
* URL

