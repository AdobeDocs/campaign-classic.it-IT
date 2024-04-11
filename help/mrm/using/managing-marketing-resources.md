---
product: campaign
title: Gestire le risorse di marketing
description: Scopri come gestire le risorse di marketing
feature: Resource Management
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: f661e1d1-de2f-4c6a-bbff-e3ffcd1831f0
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1386'
ht-degree: 1%

---

# Gestire le risorse di marketing{#managing-marketing-resources}



Adobe Campaign consente di gestire e tenere traccia delle risorse di marketing coinvolte nel ciclo di vita della campagna. Queste risorse di marketing possono essere costituite da un opuscolo, un aiuto visivo o qualsiasi altro mezzo di comunicazione che coinvolga più operatori.

Per ogni risorsa marketing gestita tramite Adobe Campaign, puoi tracciarne lo stato e la cronologia in qualsiasi momento e visualizzare la versione corrente.

## Aggiunta di una risorsa marketing {#adding-a-marketing-resource}

Le risorse di marketing sono accessibili tramite **[!UICONTROL Campaigns]** scheda.

Per aggiungere una risorsa, fai clic su **[!UICONTROL Create]** pulsante.

![](assets/s_ncs_user_mkg_resource_add.png)

Per rendere disponibile una risorsa sul server Adobe Campaign, devi aggiungere la risorsa desiderata trascinandola e rilasciandola nell’area centrale dell’editor. Puoi anche fare clic sul pulsante **[!UICONTROL Upload file to server...]** collegamento.

![](assets/s_ncs_user_mkg_resource_file.png)

Un messaggio di conferma ti consente di avviare il caricamento.

Al termine del caricamento, la risorsa viene aggiunta all’elenco delle risorse disponibili. È accessibile agli operatori di Adobe Campaign. È possibile visualizzarlo (tramite il **[!UICONTROL Preview]** ), creare una copia per modificarlo o aggiornare il file sul server (utilizzando **[!UICONTROL Edit]** ).

![](assets/s_ncs_user_mkg_resource_extract.png)

Fai clic su **[!UICONTROL General]** per selezionare gli operatori o i gruppi di operatori incaricati del monitoraggio, del tracciamento e dell’approvazione di questa risorsa. La selezione del revisore viene eseguita tramite **[!UICONTROL Advanced parameters]** collegamento.

* L’operatore a cui è assegnata la risorsa è responsabile del tracciamento.
* L’operatore di approvazione è responsabile dell’approvazione della risorsa di marketing. Verranno avvisati all’avvio del processo di convalida delle risorse.

  Se non è selezionato alcun revisore, la risorsa **[!UICONTROL cannot be]** soggetto ad approvazione.

* Se necessario, è anche possibile specificare un correttore di bozze.

Puoi specificare una data di disponibilità (indicativa) per la risorsa. Oltre questa data, verrà visualizzato con **[!UICONTROL Late]** stato.

## Lavoro collaborativo sulle risorse {#collaborative-work-on-resources}

Puoi modificare e aggiornare una risorsa di marketing e, se necessario, informarne altri operatori Adobe Campaign. Puoi eseguire le seguenti azioni:

* Scarica la risorsa localmente per modificarla.
* Aggiornare il file sul server e renderlo accessibile ad altri operatori.
* Blocca una risorsa per impedirne la modifica da parte di altri operatori.

>[!NOTE]
>
>Il **[!UICONTROL History]** contiene il registro di download e aggiornamento della risorsa. Il **[!UICONTROL Details]** consente di visualizzare la versione selezionata.

### Blocco/sblocco di una risorsa {#locking-unlocking-a-resource}

Una volta create, le risorse sono disponibili nel dashboard delle risorse di marketing e gli operatori possono modificarle.

Quando un operatore desidera lavorare su una risorsa, è preferibile bloccarla prima di iniziare il lavoro, per evitare che altri operatori la modifichino contemporaneamente. La risorsa viene quindi riservata e rimane accessibile, ma non può essere pubblicata o aggiornata sul server da un altro operatore.

Un messaggio speciale avvisa gli operatori che tentano di accedervi:

![](assets/s_ncs_user_mkg_resource_locked.png)

Il **[!UICONTROL Tracking]** indica il nome dell’operatore che ha bloccato la risorsa e la data di aggiornamento pianificata.

![](assets/s_ncs_user_mkg_resource_locked_date.png)

Per bloccare una risorsa, fai clic sulla risorsa seguita dalla **[!UICONTROL Lock]** nel dashboard delle risorse.

![](assets/s_ncs_user_mkg_resource_lock.png)

È possibile indicare la data di reso pianificata nel **[!UICONTROL Tracking]** della risorsa.

![](assets/s_ncs_user_mkg_resource_lock_date.png)

Queste informazioni ti consentono di informare altri operatori Adobe Campaign della data in cui la risorsa verrà sbloccata.

Una volta aggiornata, la risorsa viene automaticamente sbloccata e resa nuovamente disponibile a tutti gli operatori.

Se necessario, è anche possibile sbloccarla manualmente dal dashboard.

>[!NOTE]
>
>Solo l&#39;operatore che ha bloccato la risorsa e gli operatori con diritti di amministratore sono autorizzati a sbloccare una risorsa.

### Forum di discussione {#discussion-forums}

Per ogni risorsa, il **[!UICONTROL Forum]** Questa scheda consente ai partecipanti di scambiarsi informazioni.

[Forum di discussione](../../mrm/using/discussion-forums.md) spiega come funzionano i forum di discussione in Adobe Campaign.

## Ciclo di vita di una risorsa di marketing {#life-cycle-of-a-marketing-resource}

Al momento della creazione della risorsa, gli operatori Adobe Campaign sono incaricati di progettarla, correggerla, approvarla e pubblicarla. È possibile determinare una durata per queste campagne.

Il **[!UICONTROL Tracking]** Questa scheda ti consente di monitorare tutte le azioni eseguite sulla risorsa: approvazioni, rifiuti di approvazione, commenti correlati o pubblicazioni.

Il **[!UICONTROL History]** Questa scheda mostra i trasferimenti di file effettuati per questa risorsa.

### Processo di approvazione {#approval-process}

La data di disponibilità prevista viene visualizzata nei dettagli della risorsa, se è stata specificata in **[!UICONTROL Tracking]** scheda. Una volta raggiunta tale data, puoi eseguire il processo di approvazione utilizzando **[!UICONTROL Submit for approval]** nel dashboard delle risorse. Lo stato della risorsa diventa **[!UICONTROL Approval in progress]**.

Una risorsa può essere approvata tramite **[!UICONTROL Approve resource]** sulla dashboard.

![](assets/s_ncs_user_task_valid_date.png)

Gli operatori autorizzati possono quindi accettare o rifiutare l’approvazione. Questa azione è possibile tramite il messaggio e-mail inviato (facendo clic sul collegamento nel messaggio di notifica) o tramite la console (facendo clic sul pulsante **[!UICONTROL Approve]** ).

La finestra di approvazione consente di inserire un commento.

![](assets/s_ncs_user_mkg_resource_valid_ok.png)

Il **[!UICONTROL Tracking]** consente a tutti gli operatori di tenere traccia delle varie fasi del processo di approvazione.

![](assets/s_ncs_user_mkg_resource_log.png)

>[!NOTE]
>
>Oltre al revisore specificato per ogni risorsa di marketing, gli operatori con diritti di amministratore e il responsabile risorse sono autorizzati ad approvare una risorsa di marketing.

### Pubblicazione di una risorsa {#publishing-a-resource}

Una volta approvata, la risorsa marketing deve essere pubblicata. Il processo di pubblicazione deve essere soggetto a un&#39;implementazione specifica in base ai requisiti aziendali. Ciò significa che le risorse possono essere pubblicate su una extranet o su qualsiasi altro server, che è possibile inviare informazioni specifiche a un fornitore di servizi esterno e così via.

Per pubblicare una risorsa, fai clic su **[!UICONTROL Publish]** nell’area di modifica del dashboard delle risorse di marketing.

![](assets/s_ncs_user_mkg_resource_available.png)

Puoi anche automatizzare la pubblicazione di una risorsa tramite un flusso di lavoro.

Pubblicare una risorsa significa renderla disponibile per l’uso (ad esempio, da un’altra attività). La pubblicazione varia a seconda della natura della risorsa: per un volantino, la pubblicazione può significare l&#39;invio del file a una stampante, per un&#39;agenzia web, può significare la pubblicazione su un sito web, ecc.

Per pubblicare Adobe Campaign, devi creare un flusso di lavoro adeguato e collegarlo alla risorsa. Per eseguire questa operazione, apri la **[!UICONTROL Advanced settings]** della risorsa, quindi seleziona il flusso di lavoro desiderato nella sezione **[!UICONTROL Post-processing]** campo.

![](assets/mrm_asset_postprocessing_workflow.png)

Il flusso di lavoro verrà eseguito:

* Quando il revisore fa clic su **[!UICONTROL Publish resource]** (o, se non è stato definito alcun revisore, la persona responsabile della risorsa).
* Se la risorsa viene gestita tramite un’attività di creazione di risorse di marketing, verrà eseguita quando l’attività è impostata su **[!UICONTROL Finished]**, purché **[!UICONTROL Publish the marketing resource]** è selezionata nell&#39;attività (fare riferimento a [Attività di creazione risorse marketing](../../mrm/using/creating-and-managing-tasks.md#marketing-resource-creation-task))

Se un flusso di lavoro non viene avviato immediatamente (ad esempio se viene interrotto), lo stato della risorsa cambia in **[!UICONTROL Pending publication]**. Una volta avviato il flusso di lavoro, lo stato della risorsa cambia in **[!UICONTROL Published]**. Questo stato non tiene conto di possibili errori nel processo di pubblicazione. Controlla lo stato del flusso di lavoro per assicurarti che sia eseguito correttamente.

## Collegamento di una risorsa a una campagna {#linking-a-resource-to-a-campaign}

### Riferimento a una risorsa marketing {#referencing-a-marketing-resource}

Le risorse di marketing possono essere associate alle campagne, purché questa funzione sia stata selezionata nel modello della campagna.

>[!NOTE]
>
>Per informazioni dettagliate su come creare e configurare modelli di campagna, consulta [Modelli di campagna](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Fai clic su **[!UICONTROL Documents > Resources]** nel dashboard della campagna, quindi fai clic su **[!UICONTROL Add]** per selezionare la risorsa in questione.

![](assets/s_ncs_user_mkg_resource_ref.png)

Puoi filtrare le risorse per stato, natura o tipo, oppure applicare un filtro personalizzato.

![](assets/s_ncs_user_mkg_resource_ref_filter.png)

Clic **[!UICONTROL OK]** per aggiungere la risorsa all’elenco delle risorse di marketing a cui si fa riferimento per questa campagna.

Il **[!UICONTROL Details]** consente di modificarlo e visualizzarlo.

Le risorse aggiunte vengono visualizzate nel dashboard. Possono anche essere modificati qui.

### Aggiunta di una risorsa marketing a una struttura di consegna {#adding-a-marketing-resource-to-a-delivery-outline}

Le risorse di marketing possono essere associate alle consegne tramite i profili di consegna.

![](assets/s_ncs_user_mkg_resource_in_compo.png)

>[!NOTE]
>
>Per ulteriori informazioni sui profili di consegna, consulta [Associazione e strutturazione delle risorse collegate tramite una struttura di consegna](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline).

## Gestione delle scorte {#stock-management}

È possibile associare una risorsa marketing a uno o più titoli per gestire le forniture e visualizzare un avviso nel dashboard in caso di scorte insufficienti.

>[!NOTE]
>
>Per ulteriori informazioni sulla gestione delle scorte in Adobe Campaign, consulta [Gestione delle scorte](../../campaign/using/providers-stocks-and-budgets.md#stock-management).

Per associare una risorsa marketing a un magazzino, modificare la mappa del magazzino e modificare o creare un magazzino. Aggiungere una linea magazzino e selezionare la risorsa marketing corrispondente.

![](assets/s_ncs_user_task_in_a_stock.png)

Se necessario, puoi modificare la risorsa selezionata tramite **[!UICONTROL Edit the link]** (lente di ingrandimento) situata a destra della risorsa dopo averla selezionata.

Specificare il materiale iniziale e il materiale di allerta, quindi salvare.

Le scorte sono indicate nei dettagli della risorsa.

![](assets/s_ncs_user_task_with_a_stock.png)

Quando le scorte sono insufficienti, viene inviato un avviso agli operatori interessati.

## Funzioni avanzate {#advanced-functions}

La dashboard delle risorse di marketing consente di eseguire i tipi di operazioni abituali: aggiungi, modifica, blocca/sblocca, approva, pubblica. Puoi creare altri tipi di risorse di marketing e accedere a funzionalità avanzate tramite la struttura Adobe Campaign. A questo scopo, fai clic su **[!UICONTROL Explorer]** nella home page di Adobe Campaign.

Per impostazione predefinita, le risorse di marketing sono memorizzate in **[!UICONTROL MRM > Marketing resources]** dell&#39;albero.

![](assets/s_ncs_user_mkg_resource_create_from_list.png)

Da questa vista puoi aggiungere le seguenti risorse:

* File
* HTML
* Testo
* URL
