---
solution: Campaign Classic
product: campaign
title: Gestione delle risorse di marketing
description: Gestione delle risorse di marketing
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 278dec636373b5ccd3b631bd29607ebe894d53c3
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 1%

---


# Gestione delle risorse di marketing{#managing-marketing-resources}

Adobe Campaign consente di gestire e monitorare le risorse di marketing coinvolte nel ciclo di vita della campagna. Queste risorse di marketing possono essere un opuscolo, un aiuto visivo o qualsiasi altro mezzo di comunicazione che coinvolga più operatori.

Per ogni risorsa di marketing gestita tramite Adobe Campaign, puoi tenere traccia dello stato e della cronologia in qualsiasi momento e visualizzare la versione corrente.

## Aggiunta di una risorsa di marketing {#adding-a-marketing-resource}

Le risorse di marketing sono accessibili tramite la scheda **[!UICONTROL Campaigns]** .

Per aggiungere una risorsa, fai clic sul pulsante **[!UICONTROL Create]** .

![](assets/s_ncs_user_mkg_resource_add.png)

Per rendere disponibile una risorsa sul server Adobe Campaign, devi aggiungere la risorsa desiderata trascinandola e rilasciandola nell’area centrale dell’editor. Puoi anche fare clic sul collegamento **[!UICONTROL Upload file to server...]** .

![](assets/s_ncs_user_mkg_resource_file.png)

Un messaggio di conferma consente di avviare il caricamento.

Al termine del caricamento, la risorsa viene aggiunta all’elenco delle risorse disponibili. È accessibile agli operatori Adobe Campaign. Possono visualizzarlo (tramite la scheda **[!UICONTROL Preview]** ), creare una copia per modificarlo o aggiornare il file sul server (utilizzando la scheda **[!UICONTROL Edit]** ).

![](assets/s_ncs_user_mkg_resource_extract.png)

Fai clic sulla scheda **[!UICONTROL General]** per selezionare gli operatori o i gruppi di operatori responsabili del monitoraggio, del tracciamento e dell’approvazione di questa risorsa. La selezione del revisore viene eseguita tramite il collegamento **[!UICONTROL Advanced parameters]**.

* L’operatore a cui è assegnata la risorsa è responsabile del suo tracciamento.
* L’operatore che approva è responsabile dell’approvazione della risorsa di marketing. All’avvio del processo di convalida delle risorse, riceveranno una notifica.

   Se non è selezionato alcun revisore, la risorsa **[!UICONTROL cannot be]** sarà soggetta all’approvazione.

* Se necessario, è anche possibile specificare un lettore di bozze.

Puoi specificare una data di disponibilità (indicativa) per la risorsa. Oltre questa data, verrà visualizzato con lo stato **[!UICONTROL Late]** .

## Lavoro di collaborazione sulle risorse {#collaborative-work-on-resources}

Puoi modificare e aggiornare una risorsa di marketing e, se necessario, informarne altri operatori Adobe Campaign. Puoi:

* Scarica la risorsa localmente per modificarla.
* Aggiorna il file sul server e rendilo accessibile ad altri operatori.
* Bloccare una risorsa per impedirne la modifica da parte di altri operatori.

>[!NOTE]
>
>La scheda **[!UICONTROL History]** contiene il registro di download e aggiornamento della risorsa. Il pulsante **[!UICONTROL Details]** ti consente di visualizzare la versione selezionata:

### Blocco/sblocco di una risorsa {#locking-unlocking-a-resource}

Una volta create, le risorse sono disponibili nel dashboard delle risorse di marketing e gli operatori possono modificarle e modificarle.

Quando un operatore desidera lavorare su una risorsa, è preferibile bloccarla prima di avviare il lavoro, per impedire ad altri operatori di modificarla allo stesso tempo. La risorsa viene quindi riservata; rimane accessibile ma non può essere pubblicato o aggiornato sul server da un altro operatore.

Un messaggio speciale notifica gli operatori che tentano di accedervi:

![](assets/s_ncs_user_mkg_resource_locked.png)

La scheda **[!UICONTROL Tracking]** indica il nome dell’operatore che ha bloccato la risorsa e la data di aggiornamento pianificata.

![](assets/s_ncs_user_mkg_resource_locked_date.png)

Per bloccare una risorsa, devi fare clic sulla risorsa seguita dal pulsante **[!UICONTROL Lock]** nel dashboard della risorsa.

![](assets/s_ncs_user_mkg_resource_lock.png)

Puoi indicare la data di ritorno pianificata nella scheda **[!UICONTROL Tracking]** della risorsa.

![](assets/s_ncs_user_mkg_resource_lock_date.png)

Queste informazioni consentono di informare gli altri operatori Adobe Campaign della data in cui la risorsa verrà sbloccata.

Una volta aggiornata la risorsa, questa viene sbloccata automaticamente e resa nuovamente disponibile a tutti gli operatori.

Se necessario, puoi anche sbloccarlo manualmente dal dashboard.

>[!NOTE]
>
>Solo l’operatore che ha bloccato la risorsa e gli operatori con diritti di amministratore sono autorizzati a sbloccare una risorsa.

### Forum di discussione {#discussion-forums}

Per ogni risorsa, la scheda **[!UICONTROL Forum]** consente ai partecipanti di scambiare informazioni.

[I forum di discussione ](../../campaign/using/discussion-forums.md) spiegano come funzionano i forum di discussione in Adobe Campaign.

## Ciclo di vita di una risorsa di marketing {#life-cycle-of-a-marketing-resource}

Quando la risorsa viene creata, gli operatori Adobe Campaign sono nominati per progettare, correggere, approvare e pubblicare la risorsa. È possibile determinare una durata per queste campagne.

La scheda **[!UICONTROL Tracking]** ti consente di monitorare tutte le azioni eseguite sulla risorsa: approvazioni, rifiuti di approvazione, osservazioni correlate o pubblicazioni.

La scheda **[!UICONTROL History]** visualizza i trasferimenti di file effettuati per questa risorsa.

### Processo di approvazione {#approval-process}

La data di disponibilità prevista viene visualizzata nei dettagli della risorsa, se è stata specificata nella scheda **[!UICONTROL Tracking]** . Una volta raggiunta questa data, puoi eseguire il processo di approvazione utilizzando il pulsante **[!UICONTROL Submit for approval]** nel dashboard delle risorse. Lo stato della risorsa diventa **[!UICONTROL Approval in progress]**.

Una risorsa può essere approvata tramite il pulsante **[!UICONTROL Approve resource]** nel dashboard.

![](assets/s_ncs_user_task_valid_date.png)

Gli operatori autorizzati possono quindi accettare o rifiutare l’approvazione. Questa azione è possibile: tramite il messaggio e-mail inviato (facendo clic sul collegamento nel messaggio di notifica) o tramite la console (facendo clic sul pulsante **[!UICONTROL Approve]** ).

La finestra di approvazione consente di inserire un commento.

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

La scheda **[!UICONTROL Tracking]** consente a tutti gli operatori di tenere traccia delle varie fasi del processo di approvazione.

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>Oltre al revisore specificato per ogni risorsa di marketing, gli operatori con diritti di amministratore e il gestore risorse sono autorizzati ad approvare una risorsa di marketing.

### Pubblicazione di una risorsa {#publishing-a-resource}

Una volta approvata, la risorsa marketing deve essere pubblicata. Il processo di pubblicazione deve essere soggetto a un&#39;implementazione specifica in base ai requisiti aziendali. Ciò significa che le risorse possono essere pubblicate su un server extranet o qualsiasi altro server, che informazioni specifiche possono essere inviate a un provider di servizi esterno, ecc.

Per pubblicare una risorsa, fai clic sul pulsante **[!UICONTROL Publish]** nell’area di modifica del dashboard delle risorse di marketing.

![](assets/s_ncs_user_mkg_resource_available.png)

Puoi anche automatizzare la pubblicazione di una risorsa tramite un flusso di lavoro.

La pubblicazione di una risorsa significa renderla disponibile per l’uso (ad esempio da un’altra attività). La pubblicazione in quanto tale varia a seconda della natura della risorsa: per un volantino, pubblicare può significare inviare il file a una stampante, per un&#39;agenzia web, può significare pubblicarlo su un sito web, ecc.

Affinché Adobe Campaign possa pubblicare, devi creare un flusso di lavoro adeguato e collegarlo alla risorsa. A questo scopo, apri la casella **[!UICONTROL Advanced settings]** della risorsa, quindi seleziona il flusso di lavoro desiderato nel campo **[!UICONTROL Post-processing]** .

![](assets/mrm_asset_postprocessing_workflow.png)

Il flusso di lavoro viene eseguito:

* Quando il revisore fa clic sul collegamento **[!UICONTROL Publish resource]** (o, se non è stato definito alcun revisore, la persona responsabile della risorsa).
* Se la risorsa viene gestita tramite un’attività di creazione di risorse di marketing, viene eseguita quando l’attività è impostata su **[!UICONTROL Finished]**, purché la casella **[!UICONTROL Publish the marketing resource]** sia selezionata nell’attività (consulta [Attività di creazione risorse di marketing](../../campaign/using/creating-and-managing-tasks.md#marketing-resource-creation-task))

Se un flusso di lavoro non viene avviato immediatamente (ad esempio se il flusso di lavoro viene interrotto), lo stato della risorsa diventa **[!UICONTROL Pending publication]**. Una volta avviato il flusso di lavoro, lo stato della risorsa diventa **[!UICONTROL Published]**. Questo stato non tiene conto di eventuali errori nel processo di pubblicazione. Controlla lo stato del flusso di lavoro per assicurarti che sia stato eseguito correttamente.

## Collegamento di una risorsa a una campagna {#linking-a-resource-to-a-campaign}

### Riferimento a una risorsa di marketing {#referencing-a-marketing-resource}

Le risorse di marketing possono essere associate alle campagne, purché questa funzione sia stata selezionata nel modello di campagna.

>[!NOTE]
>
>Per informazioni dettagliate su come creare e configurare i modelli di campagna, consulta [Modelli di campagna](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Fai clic sulla scheda **[!UICONTROL Documents > Resources]** nel dashboard della campagna, quindi fai clic su **[!UICONTROL Add]** per selezionare la risorsa in questione.

![](assets/s_ncs_user_mkg_resource_ref.png)

Puoi filtrare le risorse per stato, natura o tipo oppure applicare un filtro personalizzato.

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

Fai clic su **[!UICONTROL OK]** per aggiungere la risorsa all’elenco delle risorse di marketing a cui si fa riferimento per questa campagna.

Il pulsante **[!UICONTROL Details]** consente di modificarlo e visualizzarlo.

Le risorse aggiunte vengono visualizzate nel dashboard. Possono anche essere modificati qui.

### Aggiunta di una risorsa di marketing a una struttura di consegna {#adding-a-marketing-resource-to-a-delivery-outline}

Le risorse di marketing possono essere associate alle consegne tramite i contorni di consegna.

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>Per ulteriori informazioni sui profili di consegna, consulta [Associazione e strutturazione delle risorse collegate tramite una struttura di consegna](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## Gestione delle scorte {#stock-management}

Puoi associare una risorsa di marketing a uno o più stock per gestire gli approvvigionamenti e visualizzare un avviso sul dashboard in caso di stock insufficienti.

>[!NOTE]
>
>Per ulteriori informazioni sulla gestione delle azioni in Adobe Campaign, consulta [Gestione delle azioni](../../campaign/using/providers--stocks-and-budgets.md#stock-management).

Per associare una risorsa di marketing a una risorsa di marketing, modifica la mappa azioni e modifica o crea una risorsa. Aggiungi una linea di magazzino e seleziona la risorsa di marketing corrispondente.

![](assets/s_ncs_user_task_in_a_stock.png)

Se necessario, puoi modificare la risorsa selezionata tramite l’ icona **[!UICONTROL Edit the link]** (lente di ingrandimento) situata a destra della risorsa una volta selezionata.

Specificare la risorsa iniziale e la scorta di avviso, quindi salvare.

La scorta è indicata nei dettagli della risorsa.

![](assets/s_ncs_user_task_with_a_stock.png)

Se lo stock è insufficiente, viene inviata un&#39;avvertenza agli operatori interessati.

## Funzioni avanzate {#advanced-functions}

Il dashboard delle risorse di marketing ti consente di eseguire i tipi di operazioni consueti: aggiungi, modifica, blocca/sblocca, approva, pubblica. Puoi creare altri tipi di risorse di marketing e accedere a funzionalità avanzate tramite la struttura di Adobe Campaign. A questo scopo, fai clic su **[!UICONTROL Explorer]** nella home page di Adobe Campaign.

Per impostazione predefinita, le risorse di marketing sono memorizzate nel nodo **[!UICONTROL MRM > Marketing resources]** della struttura.

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

Da questa visualizzazione puoi aggiungere le seguenti risorse:

* File
* HTML
* Testo
* URL

