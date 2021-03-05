---
solution: Campaign Classic
product: campaign
title: Pubblico di destinazione della campagna di marketing
description: Scopri come definire il pubblico delle campagne di marketing
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '1485'
ht-degree: 2%

---


# Selezionare il pubblico delle campagne {#marketing-campaign-deliveries}

In una campagna di marketing, per ogni consegna, puoi definire:

* Il pubblico - Ulteriori informazioni in [Creazione del pubblico in un flusso di lavoro](#building-the-main-target-in-a-workflow) e [Selezione della popolazione target](#selecting-the-target-population).
* Un gruppo di controllo - Ulteriori informazioni in [questa sezione](#defining-a-control-group).
* Indirizzi di seed - Ulteriori informazioni in [questa sezione](../../delivery/using/about-seed-addresses.md).

Alcune di queste informazioni possono essere ereditate dal [modello di campagna](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

Per generare la destinazione di consegna, puoi definire i criteri di filtro per i destinatari nel database. Questa modalità di selezione dei destinatari è presentata in [questa sezione](../../delivery/using/steps-defining-the-target-population.md).

## Invia a un gruppo

È possibile importare una popolazione in un elenco, quindi eseguire il targeting di tale elenco nelle consegne. Per farlo, segui la procedura indicata di seguito:

1. Modifica la consegna interessata e fai clic sul collegamento **[!UICONTROL To]** per modificare la popolazione target.

1. Nella scheda **[!UICONTROL Main target]** , seleziona l’opzione **[!UICONTROL Defined via the database]** e fai clic su **[!UICONTROL Add]** per selezionare i destinatari.

![](assets/s_user_target_group_add.png)

1. Scegli **[!UICONTROL A list of recipients]** e fai clic su **[!UICONTROL Next]** per selezionarlo.

![](assets/s_user_target_group_next.png)

## Creare il pubblico in un flusso di lavoro della campagna {#building-the-main-target-in-a-workflow}

Il target principale di una consegna può essere definito anche nel flusso di lavoro della campagna: questo ambiente grafico consente di creare un target utilizzando query, test e operatori: unione, deduplicazione, condivisione, ecc.

>[!IMPORTANT]
>
>Non devi aggiungere più di 28 flussi di lavoro in una campagna. Superato questo limite, nell’interfaccia non sono visibili flussi di lavoro aggiuntivi e possono generare errori.

### Crea il flusso di lavoro {#creating-a-targeting-workflow}

Il targeting può essere creato tramite una combinazione di condizioni di filtro in una sequenza grafica in un flusso di lavoro. Puoi creare popolazioni e sottopopolazioni che saranno oggetto di targeting in base alle tue esigenze. Per visualizzare l’editor del flusso di lavoro, fai clic sulla scheda **[!UICONTROL Targeting and workflows]** nel dashboard della campagna.

![](assets/s_ncs_user_edit_op_wf_link.png)

La popolazione target viene estratta dal database di Adobe Campaign tramite una o più query inserite in un flusso di lavoro. Per informazioni su come generare una query, consulta [questa sezione](../../workflow/using/query.md).

Puoi avviare query e condividere popolazioni tramite caselle quali Unione, Intersezione, Condivisione, Esclusione, ecc.

Selezionare gli oggetti dagli elenchi a sinistra dell’area di lavoro e collegarli per creare la destinazione.

![](assets/s_ncs_user_edit_op_wf_tab_a.png)

Nel diagramma, collega le query di targeting e pianificazione necessarie per la costruzione del target nel diagramma. Puoi eseguire il targeting mentre la costruzione è in corso, al fine di controllare la popolazione estratta dal database.

>[!NOTE]
>
>Esempi e procedure per la definizione delle query sono descritti in [questa sezione](../../workflow/using/query.md).

La sezione a sinistra dell’editor contiene una libreria di oggetti grafici che rappresentano le attività. La prima scheda contiene le attività di targeting e la seconda scheda contiene le attività di controllo del flusso, che vengono utilizzate occasionalmente per coordinare le attività di targeting.

Le funzioni di esecuzione e formattazione del flusso di lavoro di targeting sono accessibili tramite la barra degli strumenti dell’editor di diagrammi.

![](assets/s_user_campaign_segmentation05.png)

>[!NOTE]
>
>Le attività disponibili per creare il diagramma, nonché tutte le funzioni di visualizzazione e layout sono descritte in dettaglio nella guida [Automazione con flussi di lavoro](../../workflow/using/architecture.md) .

Puoi creare diversi flussi di lavoro di targeting per una singola campagna. Per aggiungere un flusso di lavoro:

1. Vai alla sezione in alto a sinistra della zona di creazione del flusso di lavoro, fai clic con il pulsante destro del mouse e seleziona **[!UICONTROL Add]**. Puoi inoltre utilizzare il pulsante **[!UICONTROL New]** situato sopra questa zona.

   ![](assets/s_ncs_user_add_a_wf.png)

1. Seleziona il modello **[!UICONTROL New workflow]** e denomina questo flusso di lavoro.
1. Fai clic su **[!UICONTROL OK]** per confermare la creazione del flusso di lavoro, quindi crea il diagramma per questo flusso di lavoro.

### Esegui il flusso di lavoro {#executing-a-workflow}

I flussi di lavoro di targeting possono essere avviati manualmente tramite il pulsante **[!UICONTROL Start]** nella barra degli strumenti, purché si disponga dei diritti appropriati.

Il targeting può essere programmato per l’esecuzione automatica in base a una pianificazione (pianificazione) o a un evento (segnale esterno, importazione di file, ecc.).

Le azioni relative all’esecuzione del flusso di lavoro di targeting (avvio, arresto, pausa, ecc.) sono processi **asincroni**: il comando viene salvato e avrà effetto non appena il server sarà disponibile per applicarlo.

Le icone della barra degli strumenti consentono di intervenire sull’esecuzione del flusso di lavoro di targeting.

* Avvia o riavvia

   * L’icona **[!UICONTROL Start]** ti consente di avviare il flusso di lavoro di targeting. Quando fai clic su questa icona, vengono attivate tutte le attività senza una transizione di input (eccetto i ponticelli di fine).

      ![](assets/s_user_segmentation_start.png)

      Il server prende in considerazione la richiesta, come mostrato dal suo stato:

      ![](assets/s_user_segmentation_start_status.png)

      Lo stato del processo cambia in **[!UICONTROL Started]**.

   * Puoi riavviare il flusso di lavoro di targeting tramite l’icona appropriata della barra degli strumenti. Questo comando può essere utile se l’icona **[!UICONTROL Start]** non è disponibile, ad esempio quando è in corso l’arresto del flusso di lavoro di targeting. In questo caso, fai clic sull&#39;icona **[!UICONTROL Restart]** per anticipare il riavvio. Il server prende in considerazione la richiesta, come mostra il suo stato:

      ![](assets/s_user_segmentation_restart_status.png)

      Il processo quindi immette lo stato **[!UICONTROL Started]** .

* Interrompi o interrompi

   * Le icone della barra degli strumenti consentono di interrompere o sospendere un flusso di lavoro di targeting in corso.

      Quando si fa clic su **[!UICONTROL Pause]**, le operazioni in corso **[!UICONTROL are not]** sono in pausa, ma nessun&#39;altra attività viene avviata fino al prossimo riavvio.

      ![](assets/s_user_segmentation_pause.png)

      Il server prende in considerazione il comando, come mostra il relativo stato:

      ![](assets/s_user_segmentation_pause_status.png)

      Puoi anche mettere in pausa automaticamente un flusso di lavoro di targeting quando l’esecuzione raggiunge una particolare attività. A questo scopo, fai clic con il pulsante destro del mouse sull’attività da cui deve essere messo in pausa il flusso di lavoro di targeting e seleziona **[!UICONTROL Enable but do not execute]**.

      ![](assets/s_user_segmentation_donotexecute.png)

      Questa configurazione viene visualizzata da un’icona speciale.

      ![](assets/s_user_segmentation_pause_activity.png)

      >[!NOTE]
      >
      >Questa opzione è utile durante la progettazione avanzata della campagna di targeting e le fasi di test.

      Fai clic su **[!UICONTROL Start]** per riprendere l’esecuzione.

   * Fai clic sull’icona **[!UICONTROL Stop]** per interrompere l’esecuzione in corso.

      ![](assets/s_user_segmentation_stop.png)

      Il server prende in considerazione il comando, come mostra il relativo stato:

      ![](assets/s_user_segmentation_stop_status.png)
   Puoi anche interrompere automaticamente un flusso di lavoro di targeting quando l’esecuzione raggiunge un’attività . A questo scopo, fai clic con il pulsante destro del mouse sull’attività da cui verrà interrotto il flusso di lavoro di targeting e seleziona **[!UICONTROL Do not activate]**.

   ![](assets/s_user_segmentation_donotactivate.png)

   ![](assets/s_user_segmentation_unactivation.png)

   Questa configurazione viene visualizzata da un’icona speciale.

   >[!NOTE]
   >
   >Questa opzione è utile durante la progettazione avanzata della campagna di targeting e le fasi di test.

* Interruzione incondizionata

   In Esplora risorse, seleziona **[!UICONTROL Administration > Production > Object created automatically > Campaign workflows]** per accedere e intervenire su ogni flusso di lavoro della campagna.

   Per interrompere il flusso di lavoro in modo incondizionato, fai clic sull’icona **[!UICONTROL Actions]** e seleziona **[!UICONTROL Unconditional]** interrompi. Questa azione interrompe il flusso di lavoro della campagna.

   ![](assets/s_user_segmentation_stop_unconditional.png)

## Aggiungi un gruppo di controllo {#defining-a-control-group}

Un gruppo di controllo è una popolazione che non riceverà la consegna; viene utilizzato per monitorare il comportamento dopo la consegna e l’impatto della campagna effettuando un confronto con il comportamento della popolazione target, che ha ricevuto la consegna.

Il gruppo di controllo può essere estratto dal target principale e/o provenire da un gruppo o query specifico.

### Attiva il gruppo di controllo per una campagna {#activating-the-control-group-for-a-campaign}

È possibile definire un gruppo di controllo a livello di campagna, nel qual caso il gruppo di controllo verrà applicato a ogni consegna della campagna interessata.

1. Modifica la campagna in questione e fai clic sulla scheda **[!UICONTROL Edit]** .
1. Fai clic su **[!UICONTROL Advanced campaign settings]**.

   ![](assets/s_ncs_user_edit_op_target.png)

1. Selezionare l&#39;opzione **[!UICONTROL Enable and edit control group configuration]**.
1. Fare clic su **[!UICONTROL Edit...]** per configurare il gruppo di controllo.

   ![](assets/s_ncs_user_edit_op_general_tab_exe_target.png)

La procedura di configurazione è presentata in [Estrazione del gruppo di controllo dalla destinazione principale](#extracting-the-control-group-from-the-main-target) e [Aggiunta di un gruppo di controllo](#adding-a-population).

### Attiva il gruppo di controllo per una consegna {#activating-the-control-group-for-a-delivery}

È possibile definire un gruppo di controllo a livello di consegna, nel qual caso il gruppo di controllo verrà applicato a ogni consegna della campagna interessata.

Per impostazione predefinita, la configurazione del gruppo di controllo definita a livello di campagna si applica a ogni consegna della campagna. È tuttavia possibile adattare il gruppo di controllo per una singola consegna.

>[!NOTE]
>
>Se hai definito un gruppo di controllo per una campagna e lo configuri anche per una consegna collegata a questa campagna, verrà applicato solo il gruppo di controllo definito per la consegna.

1. Modifica la consegna in questione, quindi fai clic sul collegamento **[!UICONTROL To]** nella sezione **[!UICONTROL Email parameters]** .

   ![](assets/s_ncs_user_edit_op_target_del.png)

1. Fare clic sulla scheda **[!UICONTROL Control group]**, quindi selezionare **[!UICONTROL Enable and edit control group configuration]**.
1. Fare clic su **[!UICONTROL Edit...]** per configurare il gruppo di controllo.

La procedura di configurazione è presentata in [Estrazione del gruppo di controllo dalla destinazione principale](#extracting-the-control-group-from-the-main-target) e [Aggiunta di un gruppo di controllo](#adding-a-population).

### Estrai il gruppo di controllo dalla destinazione principale {#extracting-the-control-group-from-the-main-target}

Puoi estrarre i destinatari dal target principale della consegna. In questo caso, i destinatari verranno presi dal target delle azioni di consegna interessate da questa configurazione. Questa estrazione può essere casuale o essere il risultato dell’ordinamento dei destinatari.

![](assets/s_ncs_user_extract_from_target_population.png)

Per estrarre un gruppo di controllo, abilitare il gruppo di controllo per la campagna o la consegna e selezionare una delle opzioni seguenti: **[!UICONTROL Activate random sampling]** o **[!UICONTROL Keep only the first records after sorting]**.

* **[!UICONTROL Activate random sampling]** : questa opzione applica il campionamento casuale ai destinatari nella popolazione target. Se poi imposti la soglia su 100, il gruppo di controllo sarà composto da 100 destinatari selezionati in modo casuale dalla popolazione target. Il campionamento casuale dipende dal motore del database.
* **[!UICONTROL Keep only the first records after sorting]** : questa opzione consente di definire un limite basato su uno o più criteri di ordinamento. Se si seleziona il campo **[!UICONTROL Age]** come criterio di ordinamento e quindi si definisce 100 come soglia, il gruppo di controllo sarà composto dai 100 destinatari più giovani. Ad esempio, potrebbe essere interessante definire un gruppo di controllo che includa i destinatari che effettuano pochi acquisti o i destinatari che effettuano acquisti frequenti e confrontare il loro comportamento con quello dei destinatari contattati.

Fai clic su **[!UICONTROL Next]** per definire l’ordinamento (se necessario) e seleziona la modalità di limitazione del destinatario.

![](assets/s_ncs_user_edit_op_target_param.png)

Questa configurazione equivale a un’attività di condivisione nel flusso di lavoro, che consente di suddividere il target in sottoinsiemi. Il gruppo di controllo è uno di questi sottoinsiemi. Per ulteriori informazioni, consulta [questa sezione](../../workflow/using/architecture.md) .

### Utilizza una nuova popolazione come gruppo di controllo {#adding-a-population}

È possibile definire una nuova popolazione da utilizzare come gruppo di controllo. Questa popolazione può provenire da un gruppo di destinatari o puoi crearla tramite una query specifica.

![](assets/s_ncs_user_add_to_target_population.png)

>[!NOTE]
>
>L’editor delle query di Adobe Campaign è presentato in [questa sezione](../../workflow/using/query.md).


#### Video tutorial {#create-email-video}

In questo video viene illustrato come creare una campagna e un messaggio e-mail in Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/25604?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).