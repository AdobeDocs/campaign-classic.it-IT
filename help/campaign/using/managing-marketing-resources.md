---
title: Gestione delle risorse di marketing
seo-title: Gestione delle risorse di marketing
description: Gestione delle risorse di marketing
seo-description: null
page-status-flag: never-activated
uuid: 35333bcb-0749-45b1-98ab-d5de6d91861c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 069dbc6b-4019-4d66-85a8-0e4de6b66f18
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 1%

---


# Gestione delle risorse di marketing{#managing-marketing-resources}

 Adobe Campaign consente di gestire e monitorare le risorse di marketing coinvolte nel ciclo di vita della campagna. Queste risorse di marketing possono essere una brochure, un aiuto visivo o qualsiasi altro mezzo di comunicazione che coinvolga più operatori.

Per ogni risorsa di marketing gestita tramite  Adobe Campaign, puoi monitorarne lo stato e la cronologia in qualsiasi momento e visualizzare la versione corrente.

## Aggiunta di una risorsa di marketing {#adding-a-marketing-resource}

Le risorse di marketing sono accessibili tramite l&#39;universo Campagne.

Per aggiungere una risorsa, fate clic sul **[!UICONTROL Create]** pulsante .

![](assets/s_ncs_user_mkg_resource_add.png)

Per rendere disponibile una risorsa sul server Adobe Campaign , è necessario aggiungere la risorsa desiderata trascinandola nell’area centrale dell’editor. Puoi anche fare clic sul **[!UICONTROL Upload file to server...]** collegamento.

![](assets/s_ncs_user_mkg_resource_file.png)

Un messaggio di conferma consente di avviare il caricamento.

Al termine del caricamento, la risorsa viene aggiunta all’elenco delle risorse disponibili. È accessibile  operatori Adobe Campaign. Possono visualizzarlo (tramite la **[!UICONTROL Preview]** scheda), copiarlo per modificarlo o aggiornare il file sul server (utilizzando la **[!UICONTROL Edit]** scheda).

![](assets/s_ncs_user_mkg_resource_extract.png)

Fare clic sulla **[!UICONTROL General]** scheda per selezionare gli operatori o i gruppi di operatori responsabili del monitoraggio, del tracciamento e dell&#39;approvazione di questa risorsa. La selezione del revisore viene eseguita tramite il **[!UICONTROL Advanced parameters]** collegamento.

* L&#39;operatore a cui è assegnata la risorsa è responsabile del tracciamento.
* L&#39;operatore di approvazione è responsabile dell&#39;approvazione della risorsa di marketing. All&#39;avvio del processo di convalida delle risorse verrà inviata una notifica.

   Se non è selezionato alcun revisore, la risorsa sarà **[!UICONTROL cannot be]** soggetta all&#39;approvazione.

* Se necessario, potete anche specificare un lettore di prova.

È possibile specificare una data di disponibilità (indicativa) per la risorsa. Oltre tale data, verrà visualizzata con **[!UICONTROL Late]** stato.

## Lavoro collaborativo sulle risorse {#collaborative-work-on-resources}

Puoi modificare e aggiornare una risorsa di marketing e, se necessario, informarne altri operatori Adobe Campaign . Puoi:

* Scaricate la risorsa localmente per modificarla.
* Aggiornare il file sul server e renderlo accessibile ad altri operatori.
* Bloccare una risorsa per impedirne la modifica da parte di altri operatori.

>[!NOTE]
>
>La **[!UICONTROL History]** scheda contiene il registro di download e aggiornamento della risorsa. Il **[!UICONTROL Details]** pulsante consente di visualizzare la versione selezionata:

### Blocco/sblocco di una risorsa {#locking-unlocking-a-resource}

Una volta create, le risorse sono disponibili nel dashboard delle risorse di marketing e gli operatori possono modificarle.

Quando un operatore desidera lavorare su una risorsa, è preferibile bloccarla prima dell&#39;avvio del lavoro, per impedire ad altri operatori di modificarla allo stesso tempo. La risorsa viene quindi riservata; rimane accessibile, ma non può essere pubblicato o aggiornato sul server da un altro operatore.

Un messaggio speciale notifica agli operatori che tentano di accedervi:

![](assets/s_ncs_user_mkg_resource_locked.png)

La **[!UICONTROL Tracking]** scheda indica il nome dell&#39;operatore che ha bloccato la risorsa e la data di aggiornamento pianificata.

![](assets/s_ncs_user_mkg_resource_locked_date.png)

Per bloccare una risorsa, è necessario fare clic sulla risorsa seguita dal **[!UICONTROL Lock]** pulsante nel dashboard della risorsa.

![](assets/s_ncs_user_mkg_resource_lock.png)

È possibile indicare la data di restituzione pianificata nella **[!UICONTROL Tracking]** scheda della risorsa.

![](assets/s_ncs_user_mkg_resource_lock_date.png)

Queste informazioni consentono di informare  altri operatori Adobe Campaign della data in cui la risorsa verrà sbloccata.

Una volta aggiornata, la risorsa viene sbloccata automaticamente e resa nuovamente disponibile a tutti gli operatori.

Se necessario, potete anche sbloccarlo manualmente dal dashboard.

>[!NOTE]
>
>Solo l&#39;operatore che ha bloccato la risorsa e gli operatori con diritti di amministratore sono autorizzati a sbloccare una risorsa.

### Forum di discussione {#discussion-forums}

Per ogni risorsa, la **[!UICONTROL Forum]** scheda consente ai partecipanti di scambiare informazioni.

[I forum](../../campaign/using/discussion-forums.md) di discussione spiegano come funzionano i forum di discussione in  Adobe Campaign.

## Ciclo di vita di una risorsa di marketing {#life-cycle-of-a-marketing-resource}

Quando viene creata la risorsa,  gli operatori Adobe Campaign vengono nominati per progettare, verificare, approvare e pubblicare la risorsa. È possibile determinare la durata di queste campagne.

La **[!UICONTROL Tracking]** scheda consente di monitorare le azioni eseguite sulla risorsa: approvazioni, rifiuti di approvazione, commenti correlati o pubblicazioni.

Nella **[!UICONTROL History]** scheda vengono visualizzati i trasferimenti di file eseguiti per la risorsa.

### Processo di approvazione {#approval-process}

La data di disponibilità prevista viene visualizzata nei dettagli della risorsa, se specificata nella **[!UICONTROL Tracking]** scheda. Una volta raggiunta tale data, è possibile eseguire il processo di approvazione utilizzando il **[!UICONTROL Submit for approval]** pulsante nel dashboard delle risorse. Lo stato della risorsa diventa **[!UICONTROL Approval in progress]**.

Una risorsa può essere approvata tramite il **[!UICONTROL Approve resource]** pulsante del dashboard.

![](assets/s_ncs_user_task_valid_date.png)

Gli operatori autorizzati possono quindi accettare o rifiutare l&#39;approvazione. Questa azione è possibile: tramite il messaggio e-mail inviato (facendo clic sul collegamento nel messaggio di notifica) o tramite la console (facendo clic sul pulsante **[!UICONTROL Approve]** ).

La finestra di approvazione consente di inserire un commento.

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

La **[!UICONTROL Tracking]** scheda consente a tutti gli operatori di tenere traccia delle varie fasi del processo di approvazione.

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>Oltre al revisore specificato per ogni risorsa di marketing, gli operatori con diritti di amministratore e il gestore risorse sono autorizzati ad approvare una risorsa di marketing.

### Publishing a resource {#publishing-a-resource}

Una volta approvata, la risorsa marketing deve essere pubblicata. Il processo di pubblicazione deve essere soggetto a un&#39;implementazione specifica in base ai requisiti aziendali. Ciò significa che le risorse possono essere pubblicate su una rete extranet o su qualsiasi altro server, che informazioni specifiche possono essere inviate a un provider di servizi esterno, ecc.

Per pubblicare una risorsa, fai clic sul **[!UICONTROL Publish]** pulsante nella zona di modifica del dashboard delle risorse di marketing.

![](assets/s_ncs_user_mkg_resource_available.png)

Potete inoltre automatizzare la pubblicazione di una risorsa tramite un flusso di lavoro.

Pubblicare una risorsa significa renderla disponibile per l’uso (ad esempio, tramite un’altra attività). La pubblicazione varia a seconda della natura della risorsa: per un volantino, pubblicare può significare inviare il file a una stampante, per un&#39;agenzia Web, può significare pubblicarlo su un sito Web, ecc.

Affinché  Adobe Campaign possa pubblicare, è necessario creare un flusso di lavoro adeguato e collegarlo alla risorsa. A questo scopo, aprite la **[!UICONTROL Advanced settings]** casella della risorsa, quindi selezionate il flusso di lavoro desiderato nel **[!UICONTROL Post-processing]** campo.

![](assets/mrm_asset_postprocessing_workflow.png)

Il flusso di lavoro verrà eseguito:

* Quando il revisore fa clic sul **[!UICONTROL Publish resource]** collegamento (o, se non è stato definito alcun revisore, la persona responsabile della risorsa).
* Se la risorsa viene gestita tramite un&#39;attività di creazione delle risorse di marketing, verrà eseguita quando l&#39;attività è impostata su **[!UICONTROL Finished]**, purché la **[!UICONTROL Publish the marketing resource]** casella sia selezionata nell&#39;attività (fare riferimento all&#39;attività [di creazione delle risorse di](../../campaign/using/creating-and-managing-tasks.md#marketing-resource-creation-task)marketing)

Se un flusso di lavoro non viene avviato immediatamente (se ad esempio il flusso di lavoro viene interrotto), lo stato della risorsa cambia in **[!UICONTROL Pending publication]**. Una volta avviato il flusso di lavoro, lo stato della risorsa cambia in **[!UICONTROL Published]**. Questo stato non tiene conto di eventuali errori nel processo di pubblicazione. Controllate lo stato del flusso di lavoro per verificare che sia stato eseguito correttamente.

## Collegamento di una risorsa a una campagna {#linking-a-resource-to-a-campaign}

### Riferimento a una risorsa di marketing {#referencing-a-marketing-resource}

Le risorse di marketing possono essere associate alle campagne, a condizione che questa funzione sia stata selezionata nel modello di campagna.

>[!NOTE]
>
>Per informazioni dettagliate su come creare e configurare i modelli delle campagne, consultate i modelli [delle](../../campaign/using/marketing-campaign-templates.md#campaign-templates)campagne.

Fate clic sulla **[!UICONTROL Documents > Resources]** scheda nel dashboard della campagna, quindi fate clic **[!UICONTROL Add]** per selezionare la risorsa in questione.

![](assets/s_ncs_user_mkg_resource_ref.png)

Potete filtrare le risorse per stato, natura o tipo oppure applicare un filtro personalizzato.

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

Fai clic **[!UICONTROL OK]** per aggiungere la risorsa all&#39;elenco delle risorse di marketing a cui viene fatto riferimento per questa campagna.

Il **[!UICONTROL Details]** pulsante consente di modificarlo e visualizzarlo.

Le risorse aggiunte vengono visualizzate nel dashboard. È inoltre possibile modificarli.

### Aggiunta di una risorsa di marketing a un profilo di consegna {#adding-a-marketing-resource-to-a-delivery-outline}

Le risorse di marketing possono essere associate alle consegne tramite i contorni di consegna.

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>Per ulteriori informazioni sui contorni di consegna, vedere [Associazione e strutturazione delle risorse collegate tramite un profilo](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)di consegna.

## Gestione delle scorte {#stock-management}

Puoi associare una risorsa di marketing a una o più scorte per gestire le forniture e visualizzare un avviso sul dashboard in caso di scorte insufficienti.

>[!NOTE]
>
>Per ulteriori informazioni sulla gestione delle azioni in  Adobe Campaign, fare riferimento a Gestione delle [scorte](../../campaign/using/providers--stocks-and-budgets.md#stock-management).

Per associare una risorsa di marketing a una risorsa, modificate la mappa di magazzino e modificate o create una risorsa. Aggiungi una linea di azioni e seleziona la risorsa di marketing corrispondente.

![](assets/s_ncs_user_task_in_a_stock.png)

Se necessario, è possibile modificare la risorsa selezionata tramite l’ **[!UICONTROL Edit the link]** icona (lente di ingrandimento) a destra della risorsa, una volta selezionata.

Specificate la risorsa iniziale e la risorsa di avviso, quindi salvate.

La risorsa è indicata nei dettagli della risorsa.

![](assets/s_ncs_user_task_with_a_stock.png)

Se lo stock è insufficiente, agli operatori interessati viene inviato un avviso.

## Funzioni avanzate {#advanced-functions}

Il dashboard delle risorse di marketing consente di eseguire i tipi di operazioni consueti: aggiungere, modificare, bloccare/sbloccare, approvare, pubblicare. Puoi creare altri tipi di risorse di marketing e accedere a funzionalità avanzate tramite la struttura  Adobe Campaign. A questo scopo, fate clic **[!UICONTROL Explorer]** nella home page di  Adobe Campaign.

Per impostazione predefinita, le risorse di marketing sono memorizzate nel **[!UICONTROL MRM > Marketing resources]** nodo della struttura.

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

Da questa visualizzazione potete aggiungere le seguenti risorse:

* File
* HTML
* Testo
* URL

