---
title: Esecuzione di un flusso di lavoro
seo-title: Esecuzione di un flusso di lavoro
description: Esecuzione di un flusso di lavoro
seo-description: null
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# Esecuzione di un flusso di lavoro{#executing-a-workflow}

Le linee guida per la risoluzione dei problemi relativi all&#39;esecuzione dei flussi di lavoro sono disponibili in [questa sezione](../../production/using/workflow-execution.md).

## Avvio di un flusso di lavoro {#starting-a-workflow}

Un flusso di lavoro viene sempre avviato manualmente. All&#39;avvio, tuttavia, può rimanere inattivo a seconda delle informazioni specificate tramite un pianificatore (vedere [Pianificazione](../../workflow/using/scheduler.md)) o la pianificazione delle attività.

Azioni relative all&#39;esecuzione del flusso di lavoro di targeting (avvio, arresto, pausa, ecc.) sono processi **asincroni** : l&#39;ordine viene registrato e sarà effettivo non appena il server sarà disponibile ad applicarlo.

La barra degli strumenti consente di avviare e tenere traccia dell’esecuzione del flusso di lavoro.

L&#39;elenco delle opzioni disponibili nel **[!UICONTROL Actions]** menu e il menu di scelta rapida sono descritti di seguito.

### Azioni, barra degli strumenti {#actions-toolbar}

I pulsanti della barra degli strumenti sono descritti in questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow). Il **[!UICONTROL Actions]** pulsante consente di accedere a opzioni di esecuzione aggiuntive per agire su flussi di lavoro selezionati. Potete inoltre utilizzare il **[!UICONTROL File > Actions]** menu oppure fare clic con il pulsante destro del mouse su un flusso di lavoro e selezionare **[!UICONTROL Actions]**.

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   Questa azione consente di avviare l’esecuzione di un flusso di lavoro: un flusso di lavoro **Completato**, **In corso di modifica** o in **pausa** , cambia lo stato in **Avviato**. Il motore del flusso di lavoro gestisce quindi l&#39;esecuzione del flusso di lavoro. Se il flusso di lavoro è stato messo in pausa, viene ripreso, altrimenti il flusso di lavoro viene avviato dall&#39;inizio e le attività iniziali vengono attivate.

   Avvio è un processo asincrono: La richiesta viene salvata ed elaborata il prima possibile da un server del flusso di lavoro.

* **[!UICONTROL Pause]**

   Questa azione imposta lo stato del flusso di lavoro su **Pausa**. Nessuna attività viene attivata fino alla ripresa del flusso di lavoro; tuttavia, le operazioni in corso non vengono messe in pausa.

* **[!UICONTROL Stop]**

   Questa azione interrompe l&#39;esecuzione di un flusso di lavoro in corso. Lo stato dell’istanza è impostato su **Completato**. Se possibile, le operazioni in corso vengono interrotte. Le importazioni e le query SQL vengono annullate immediatamente.

   L&#39;arresto è un processo asincrono. La richiesta è registrata, quindi il server del flusso di lavoro o i server annullano le operazioni in corso. L’arresto di un’istanza del flusso di lavoro può richiedere del tempo, soprattutto se il flusso di lavoro è in esecuzione su più server, ciascuno dei quali deve assumersi il controllo per annullare le attività in corso.

* **[!UICONTROL Restart]**

   Questa azione si arresta e quindi riavvia il flusso di lavoro. Nella maggior parte dei casi, il riavvio è più rapido. È inoltre utile automatizzare il riavvio quando l&#39;arresto richiede un certo tempo: perché il comando &#39;Stop&#39; non è disponibile quando il flusso di lavoro viene interrotto.

   Le **[!UICONTROL Start / Pause / Stop / Restart]** azioni sono disponibili anche tramite le icone di esecuzione nella barra degli strumenti. For more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   Questa azione consente di eliminare la cronologia del flusso di lavoro. Per ulteriori informazioni, fare riferimento a [Rimozione dei registri](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs).

* **[!UICONTROL Start in simulation mode]**

   Questa opzione consente di avviare il flusso di lavoro in modalità di simulazione anziché in modalità reale. Questo significa che quando si attiva questa modalità, vengono eseguite solo le attività che non hanno alcun impatto sul database o sul file system (ad es. **[!UICONTROL Query]**, **[!UICONTROL Union]**, **[!UICONTROL Intersection]**, ecc.). Attività che hanno un impatto (ad es. **[!UICONTROL Export]**, **[!UICONTROL Import]**, ecc.) e quelli successivi (nello stesso ramo) non sono eseguiti.

* **[!UICONTROL Execute pending tasks now]**

   Questa azione consente di avviare tutte le attività in sospeso il prima possibile. Per avviare un&#39;attività specifica, fare clic con il pulsante destro del mouse sulla relativa attività e selezionare **[!UICONTROL Execute pending task(s) now]**.

* **[!UICONTROL Unconditional stop]**

   Questa opzione modifica lo stato del flusso di lavoro in **[!UICONTROL Finished]**. Questa azione deve essere utilizzata come ultima risorsa solo se il normale processo di arresto ha esito negativo dopo diversi minuti. Utilizzate l&#39;interruzione non condizionale solo se siete sicuri che non siano in corso processi di workflow effettivi.

   >[!CAUTION]
   >
   >Questa opzione è riservata agli utenti esperti.

* **[!UICONTROL Save as template]**

   Questa azione crea un nuovo modello di flusso di lavoro basato sul flusso di lavoro selezionato. È necessario specificare la cartella in cui verrà salvato (nel **[!UICONTROL Folder]** campo).

   Le opzioni **[!UICONTROL Mass update of selected lines]** e **[!UICONTROL Merge selected lines]** sono opzioni di piattaforma generiche disponibili in tutti i **[!UICONTROL Actions]** menu. For more on this, refer to this [section](../../platform/using/updating-data.md).

### Menu di scelta rapida {#right-click-menu}

Quando sono selezionate una o più attività del flusso di lavoro, potete fare clic con il pulsante destro del mouse per agire sulla selezione.

![](assets/contextual_menu.png)

Nel menu di scelta rapida sono disponibili le seguenti opzioni:

**[!UICONTROL Open]**: questa opzione consente di accedere alle proprietà dell&#39;attività.

**[!UICONTROL Display logs:]** questa opzione consente di visualizzare il registro dell&#39;esecuzione delle attività per l&#39;attività selezionata. Fare riferimento a [Visualizzazione dei registri](../../workflow/using/monitoring-workflow-execution.md#displaying-logs).

**[!UICONTROL Execute pending task(s) now:]** questa azione consente di avviare al più presto le attività in sospeso.

**[!UICONTROL Workflow restart from a task:]** questa opzione consente di riavviare il flusso di lavoro utilizzando i risultati precedentemente memorizzati per questa attività.

**[!UICONTROL Cut/Copy/Paste/Delete:]** queste opzioni consentono di tagliare, copiare, incollare ed eliminare le attività.

**[!UICONTROL Copy as bitmap:]** questa opzione consente di visualizzare uno screenshot di tutte le attività.

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** queste opzioni sono disponibili anche nella **[!UICONTROL Advanced]** scheda delle proprietà dell&#39;attività. Sono descritti in [Execution](../../workflow/using/advanced-parameters.md#execution).

**[!UICONTROL Save / Cancel:]** consente di salvare o annullare le modifiche apportate a un flusso di lavoro.

>[!NOTE]
>
>Potete selezionare un gruppo di attività e applicare uno di questi comandi.

Anche in questa [sezione](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)viene illustrato il menu di scelta rapida.

## Ciclo di vita del flusso di lavoro {#workflow-life-cycle}

Il ciclo di workflow presenta tre fasi principali.

* **In corso di modifica**

   Questa è la fase di progettazione iniziale: Quando viene creato un nuovo flusso di lavoro, il suo stato è &#39;In corso di modifica&#39;. Il flusso di lavoro non è ancora gestito dal server e può essere modificato senza rischi.

* **Avviato**

   Una volta completata la fase di progettazione iniziale, il flusso di lavoro può essere avviato. In questa fase, l&#39;istanza viene gestita dal server e le singole attività vengono eseguite. Il flusso di lavoro può comunque essere modificato con alcune precauzioni.

* **Completato**

   Un flusso di lavoro è &quot;Completato&quot; quando non sono più presenti attività in corso o quando un operatore ha esplicitamente arrestato l&#39;istanza.

Ad esempio, le attività **Inizio** e **Consegna** sono descritte mentre l&#39;attività **Approvazione** lampeggia nel flusso di lavoro seguente.

![](assets/new-workflow-6.png)

Ciò significa che le prime due attività sono state eseguite correttamente e che l&#39;approvazione è in corso, ovvero è stata creata ma non ancora completata.

I caratteri **574 -Ok** visualizzati sopra la transizione dopo l&#39;attività **Consegna** indicano che la preparazione della consegna ha interessato 574 destinatari e che l&#39;operazione è stata completata correttamente. Queste informazioni, che vengono aggiunte alle transizioni quando vengono eseguite, vengono calcolate dalle attività che elaborano i dati.

Il flusso di lavoro viene avviato e è in attesa che un operatore appartenente al gruppo specificato nell&#39;attività di **approvazione** prenda una decisione. Gli operatori appartenenti al gruppo e che dispongono di un indirizzo e-mail o di un numero di telefono cellulare ricevono una notifica.

La gestione degli operatori è descritta in questa [sezione](../../platform/using/access-management.md).

Per ulteriori informazioni su come monitorare i flussi di lavoro, consulta [questa sezione](../../workflow/using/monitoring-workflow-execution.md).

## Ciclo di vita dei dati {#data-life-cycle}

### Tabella lavoro {#work-table}

Nei flussi di lavoro, i dati trasportati da un&#39;attività all&#39;altra vengono memorizzati in una tabella di lavoro temporanea.

Questi dati possono essere visualizzati e analizzati facendo clic con il pulsante destro del mouse sulla transizione appropriata.

![](assets/wf-right-click-analyze.png)

A questo scopo, selezionate il menu appropriato:

* Visualizzazione della destinazione

   Questo menu visualizza i dati disponibili sulla popolazione di destinazione e la struttura della tabella di lavoro (**[!UICONTROL Schema]** scheda).

   ![](assets/wf-right-click-display.png)

   Per ulteriori informazioni, vedere [Tabelle di lavoro e schema](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema)del flusso di lavoro.

* Analisi della destinazione

   Questo menu consente di accedere alla procedura guidata di analisi descrittiva che consente di generare statistiche e rapporti sui dati della transizione.

   For more on this, refer to this [section](../../reporting/using/using-the-descriptive-analysis-wizard.md).

I dati di destinazione vengono eliminati durante l&#39;esecuzione del flusso di lavoro. È accessibile solo l&#39;ultima tabella di lavoro. È possibile configurare il flusso di lavoro in modo che tutte le tabelle di lavoro rimangano accessibili: selezionate l’ **[!UICONTROL Keep the result of interim populations between two executions]** opzione nelle proprietà del flusso di lavoro.

Tuttavia, si consiglia di evitare di attivare questa opzione in caso di quantità significative di dati.

![](assets/wf-purge-data-option.png)

### Dati di destinazione {#target-data}

I dati memorizzati nella tabella di lavoro del flusso di lavoro sono accessibili nei campi di personalizzazione.

Questo consente di utilizzare i dati raccolti tramite un elenco o in base alle risposte a un sondaggio in una consegna. A questo scopo, utilizzare la sintassi seguente:

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** Gli elementi di personalizzazione di tipo (targetData) non sono disponibili per i flussi di lavoro di targeting. La destinazione di consegna deve essere integrata nel flusso di lavoro e specificata nella transizione in entrata della consegna.

Se desiderate creare delle prove di consegna, il target di prova deve essere costruito in base alla **[!UICONTROL Address substitution]** modalità in modo da poter inserire i dati di personalizzazione. For more on this, refer to this [section](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

Nell&#39;esempio seguente, raccoglieremo un elenco di informazioni sui clienti da utilizzare in un&#39;e-mail personalizzata.

Effettuate le seguenti operazioni:

1. Create un flusso di lavoro per raccogliere le informazioni, riconciliatelo con i dati già presenti nel database, quindi avviate una consegna.

   ![](assets/wf-targetdata-sample-1.png)

   Nel nostro esempio, il contenuto del file è il seguente:

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   Per caricare il file, procedere come segue:

   ![](assets/wf-targetdata-sample-2.png)

1. Configura l&#39;attività del **[!UICONTROL Enrichment]** tipo per riconciliare i dati raccolti con quelli già presenti nel database Adobe Campaign.

   Qui, la chiave di riconciliazione è il numero di conto:

   ![](assets/wf-targetdata-sample-3.png)

1. Quindi configurate i **[!UICONTROL Delivery]** seguenti parametri: viene creato in base a un modello e i destinatari sono specificati dalla transizione in entrata.

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >Per personalizzare la consegna possono essere utilizzati solo i dati contenuti nella transizione. **i campi di personalizzazione del tipo targetData** sono disponibili solo per la popolazione in entrata dell&#39; **[!UICONTROL Delivery]** attività.

1. Nel modello di consegna, utilizzate i campi raccolti nel flusso di lavoro.

   A tal fine, inserire **[!UICONTROL Target extension]** campi di personalizzazione di tipo.

   ![](assets/wf-targetdata-sample-5.png)

   Qui, vogliamo inserire il genere musicale e il tipo di supporto preferiti del cliente (CD o DVD) come indicato nel file raccolto dal flusso di lavoro.

   Inoltre, aggiungeremo un coupon per i titolari di carte fedeltà, ossia i destinatari per i quali il valore &quot;Carta&quot; è uguale a 1.

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** I dati di tipo (targetData) vengono inseriti nelle consegne utilizzando le stesse caratteristiche di tutti i campi di personalizzazione. Possono essere utilizzati anche nell&#39;oggetto, nelle etichette di collegamento o nei link stessi.

   I messaggi indirizzati ai destinatari raccolti conterranno i seguenti dati:

   ![](assets/wf-targetdata-sample-7.png)

## Definizione delle approvazioni {#defining-approvals}

Le approvazioni consentono agli operatori di prendere decisioni su un flusso di lavoro o di confermarne l&#39;esecuzione continua.

Un messaggio viene inviato a un gruppo di operatori e il flusso di lavoro attende una risposta prima della ripresa. Il flusso di lavoro non viene interrotto e altre operazioni possono essere eseguite. Ad esempio, potrebbero essere presenti più approvazioni simultanee in sospeso.

Un&#39;approvazione può contenere più opzioni che l&#39;operatore può scegliere. Tuttavia, è possibile limitare il numero di scelte a uno per inviare un&#39;attività da eseguire a un operatore, ad esempio per eseguire il targeting. L&#39;operatore può quindi rispondere una volta eseguita l&#39;attività (il processo riprende). L&#39;esempio seguente illustra questi tipi di approvazione:

![](assets/validation-1.png)

Nelle operazioni, tutte le fasi che richiedono l&#39;approvazione si basano sullo stesso principio.

![](assets/validation-1-in-op.png)

Gli esempi di approvazione sono disponibili in questa [sezione](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries).

Un operatore può rispondere in uno dei due modi seguenti: convalida mediante la pagina Web collegata nel messaggio e-mail o tramite la console.

>[!NOTE]
>
>Una volta salvata la risposta, la risposta potrebbe non essere modificata.

### Invio di e-mail {#sending-emails}

È possibile ricevere un messaggio di approvazione contenente un collegamento a una pagina Web tramite la quale è possibile rispondere. Affinché l&#39;operatore di destinazione riceva un&#39;e-mail di approvazione, l&#39;indirizzo e-mail dell&#39;operatore deve essere completo. In caso contrario, l&#39;operatore deve utilizzare la console per rispondere

La gestione degli operatori è descritta in questa [sezione](../../platform/using/access-management.md).

Le e-mail di approvazione vengono inviate in modo continuo. Il modello di consegna predefinito è **[!UICONTROL notifyAssignee]**: Viene salvata nella **[!UICONTROL Administration > Campaign management > Technical delivery templates]** cartella. Questo scenario può essere personalizzato ed è anche consigliato di creare una copia e modificare i modelli per ogni attività.

Le consegne create tramite questo modello vengono memorizzate nella **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** cartella.

### Approvazione tramite console {#approval-via-the-console}

Nelle operazioni, gli elementi da approvare vengono visualizzati nel dashboard della campagna.

Per i flussi di lavoro tecnici, è possibile accedere alle attività che l&#39;utente può approvare dalla struttura ad albero della **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** cartella.

![](assets/validation-node.png)

### Gruppi {#groups}

Un&#39;approvazione è assegnata a un gruppo di operatori, un singolo operatore o un insieme di operatori selezionati tramite una condizione di filtraggio.

1. Per la forma di approvazione più semplice, l&#39;attività è terminata non appena l&#39;operatore risponde. Tutti gli altri operatori che cercano di rispondere riceveranno una notifica che qualcuno l&#39;ha già fatto.
1. Per approvazioni multiple, fare riferimento a [Approvazione](#multiple-approval)multipla.

I gruppi di operatori per le approvazioni devono essere designati come ruoli o funzioni anziché come individui denominati. Ad esempio, un gruppo &quot;Budget campagna&quot; è preferibile a &quot;Gruppo Harry&quot;. Consigliamo di avere almeno due persone in un gruppo che possano approvare un compito. In questo modo, se uno è assente, l&#39;altro può rispondere.

### Scadenza {#expirations}

Le scadenze sono transizioni specifiche utilizzate in diversi tipi di attività, in particolare nelle approvazioni. Una scadenza può essere utilizzata per attivare un’azione dopo un determinato lasso di tempo in assenza di una risposta o per proseguire il flusso di lavoro (e assegnare un’approvazione a un altro gruppo, ad esempio).

La seconda scheda nelle proprietà di approvazione dell&#39;attività consente di definire una o più scadenze. In realtà, potete definire più tipi di scadenza.

![](assets/expiration.png)

Per aggiungere una nuova scadenza, fate clic su **[!UICONTROL Add]**. A ciascuna scadenza creata viene aggiunta una transizione. È possibile:

* modificare i parametri tipici direttamente facendo clic su una cella nell&#39;elenco (o premendo F2),
* oppure modificare l&#39;espressione facendo clic sul **[!UICONTROL Detail...]** pulsante.

>[!NOTE]
>
>Non è necessario specificare un ordine per le scadenze in quanto elaborate in ordine cronologico.

L&#39; **[!UICONTROL Do not terminate the task]** opzione lascia attiva l&#39;approvazione quando il ritardo viene superato. Questa modalità consente di gestire i promemoria lasciando attiva l’approvazione: gli operatori possono ancora rispondere. Questa opzione è disabilitata per impostazione predefinita, pertanto l&#39;attività viene considerata terminata alla scadenza e gli operatori potrebbero non rispondere più.

Potete creare quattro tipi di scadenza:

* **Ritardo dopo l’inizio** dell’attività: La scadenza viene calcolata aggiungendo un periodo di tempo specificato alla data in cui viene attivata l’approvazione.
* **Ritardo dopo una data** specificata: La scadenza viene calcolata aggiungendo un periodo di tempo alla data specificata.
* **Ritardo prima di una data** specificata: La scadenza viene calcolata sottraendo un periodo di tempo da una data specificata.
* **Scadenza calcolata dallo script**: La scadenza viene calcolata utilizzando JavaScript.

   L’esempio seguente calcola una scadenza 24 ore prima della data di inizio di una consegna (identificata da **vars.deliveryId**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

### Approvazione multipla {#multiple-approval}

L&#39;approvazione multipla è un meccanismo che consente a tutti gli operatori di approvazione di rispondere. Per ogni risposta viene attivata una transizione.

L&#39;approvazione multipla è utile per i meccanismi di votazione o indagine. Potete contare le risposte ed elaborarne il risultato dopo un determinato periodo aggiungendo una scadenza.

### Diritti richiesti {#required-rights}

Gli operatori di un gruppo devono avere almeno i seguenti diritti per poter rispondere a una richiesta di approvazione:

* Autorizzazioni di scrittura per il flusso di lavoro.
* Autorizzazioni di lettura e scrittura per la cartella contenente le attività da approvare.

Il gruppo Esecuzione flusso di lavoro dispone di tali diritti. Un operatore aggiunto a questo gruppo ha i diritti per rispondere a una richiesta di approvazione.

## Architettura {#architecture}

I flussi di lavoro vengono gestiti da un modulo specifico. Questo modulo può essere avviato su più server per condividere il carico di elaborazione.

![](assets/architecture.png)

* Il processo &#39;Workflow Instance Runner&#39; (runwf) esegue tutte le attività di una determinata istanza del flusso di lavoro. Quando non ci sono attività da eseguire per il momento, diventa &quot;passivo&quot;, cioè salva il suo stato nel database, quindi si arresta.
* Il modulo &#39;Workflow Server&#39; (wfserver) controlla le istanze correnti del flusso di lavoro. In presenza di un&#39;attività da eseguire, questo modulo crea un processo per attivare (o riattivare) l&#39;istanza corrispondente.

Quando un operatore esegue un&#39;azione su un flusso di lavoro (avvio, arresto, pausa, ecc.), l&#39;azione non viene eseguita direttamente dal modulo &#39;nlserver&#39;, ma viene invece inserita in una coda per essere elaborata dal modulo del flusso di lavoro.
