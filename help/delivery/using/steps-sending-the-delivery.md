---
solution: Campaign Classic
product: campaign
title: Configurazione e invio della consegna
description: Configurazione e invio della consegna
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 5%

---

# Configurazione e invio della consegna {#configuring-and-sending-the-delivery}

>[!NOTE]
>
>Solo il proprietario della consegna può avviare una consegna. Affinché un altro operatore (o gruppo di operatori) sia in grado di avviare una consegna, devi aggiungerli come revisori nel campo **[!UICONTROL Delivery start:]** . Per ulteriori informazioni, consulta [questa sezione](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Parametri aggiuntivi di consegna {#delivery-additiona-parameters}

Prima di inviare la consegna, puoi definire i parametri di invio nelle proprietà di consegna tramite la scheda **[!UICONTROL Delivery]** .

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: Questa opzione ti consente di influenzare l’ordine di invio delle consegne definendone il livello di priorità (normale, alto o basso). Questo ti consente di assegnare priorità all’ordine per consegne specifiche e più urgenti rispetto ad altre.

* **[!UICONTROL Message batch quantity]**: Questa opzione ti consente di definire il numero di messaggi raggruppati all’interno dello stesso pacchetto di consegna XML. Se il parametro è impostato su 0, i messaggi vengono raggruppati automaticamente. La dimensione del pacchetto è definita dal calcolo `<delivery size>/1024`, con un minimo di 8 e un massimo di 256 messaggi per pacchetto.

   >[!IMPORTANT]
   >
   >Quando la consegna viene duplicata, il parametro viene reimpostato.

* **[!UICONTROL Send using multiple waves]**: Per ulteriori informazioni, consulta  [Invio utilizzando più ondate](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: Questa opzione consente di verificare l’invio di una consegna tramite SMTP. La consegna viene elaborata fino alla connessione al server SMTP, ma non viene inviata.

   >[!NOTE]
   >
   >L’utilizzo di questa opzione non è consigliato quando si installa utilizzando mid-sourcing per non chiamare mta. Per ulteriori informazioni sulla configurazione di un server SMTP, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#delivery-settings).

* **[!UICONTROL Email BCC]**: Questa opzione ti consente di archiviare le e-mail su un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN al target del messaggio. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/sending-messages.md#archiving-emails).

## Conferma della consegna {#confirming-delivery}

Una volta configurata la consegna e pronta per l’invio, assicurati di aver eseguito l’analisi della consegna.

A questo scopo, fai clic su **[!UICONTROL Send]**, seleziona l’azione desiderata e fai clic su **[!UICONTROL Analyze]**. Per ulteriori informazioni, consulta [Avvio dell&#39;analisi](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Al termine, fai clic su **[!UICONTROL Confirm delivery]** per avviare la consegna dei messaggi.

Puoi quindi chiudere la procedura guidata di consegna e monitorare l’esecuzione della consegna dalla scheda **[!UICONTROL Delivery]** , accessibile tramite i dettagli di questa consegna o tramite l’elenco delle consegne.

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [Monitoraggio di una consegna](../../delivery/using/about-delivery-monitoring.md)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Informazioni sul tracking dei messaggi](../../delivery/using/about-message-tracking.md)

## Pianificazione dell’invio della consegna {#scheduling-the-delivery-sending}

Puoi posticipare la consegna dei messaggi per pianificare la consegna o per gestire la pressione di vendita ed evitare di sollecitare eccessivamente una popolazione.

1. Fare clic sul pulsante **[!UICONTROL Send]** e selezionare l&#39;opzione **[!UICONTROL Postpone delivery]**.

1. Specifica una data di inizio nel campo **[!UICONTROL Contact date]** .

![](assets/dlv_email_del_plan.png)

1. Puoi quindi avviare l’analisi della consegna, quindi confermare l’invio della consegna. Tuttavia, l’invio della consegna avrà inizio solo alla data indicata nel campo **[!UICONTROL Contact date]** .

>[!IMPORTANT]
>
>Una volta avviata l’analisi, la data di contatto definita viene corretta. Se modifichi questa data, dovrai riavviare l’analisi in modo che le modifiche vengano prese in considerazione.

![](assets/s_ncs_user_email_del_start_delayed.png)

Nell’elenco delle consegne, la consegna verrà visualizzata con lo stato **[!UICONTROL Pending]** .

![](assets/s_ncs_user_email_del_waiting.png)

La pianificazione può essere configurata a monte anche tramite il pulsante **[!UICONTROL Scheduling]** della consegna.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Ti consente di rinviare la consegna a una data successiva o di salvarla nel calendario provvisorio.

* L’opzione **[!UICONTROL Schedule delivery (no automatic execution)]** ti consente di pianificare un’analisi provvisoria della consegna.

   Quando questa configurazione viene salvata, lo stato della consegna diventa **[!UICONTROL Targeting pending]** . L’analisi verrà avviata alla data specificata.

* L’opzione **[!UICONTROL Schedule delivery (automatic execution on planned date)]** ti consente di specificare la data di consegna.

   Fai clic su **[!UICONTROL Send]** e seleziona **[!UICONTROL Postpone delivery]**, quindi avvia l’analisi e conferma la consegna. Al termine dell’analisi, il target di consegna è pronto e i messaggi verranno inviati automaticamente alla data specificata.

Le date e gli orari sono espressi nel fuso orario dell’operatore corrente. L’elenco a discesa **[!UICONTROL Time zone]** situato sotto il campo di immissione della data di contatto consente di convertire automaticamente la data e l’ora inserite nel fuso orario selezionato.

Ad esempio, se pianifichi l’esecuzione automatica di una consegna alle 8 ora di Londra, l’ora viene automaticamente convertita nel fuso orario selezionato:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Invio tramite più ondate {#sending-using-multiple-waves}

Per bilanciare il carico, puoi dividere le consegne in più batch. Configura il numero di batch e la loro proporzione rispetto all’intera consegna.

>[!NOTE]
>
>È possibile definire solo le dimensioni e il ritardo tra due onde consecutive. Impossibile configurare i criteri di selezione dei destinatari per ogni ondata.

1. Apri la finestra delle proprietà di consegna e fai clic sulla scheda **[!UICONTROL Delivery]** .
1. Seleziona l’opzione **[!UICONTROL Send using multiple waves]** e fai clic sul collegamento **[!UICONTROL Define waves...]** .

   ![](assets/s_ncs_user_wizard_waves.png)

1. Per configurare le onde, puoi effettuare le seguenti operazioni:

   * Definisci le dimensioni per ogni onda. Ad esempio, se immetti **[!UICONTROL 30%]** nel campo corrispondente, ogni ondata rappresenterà il 30% dei messaggi inclusi nella consegna, tranne l’ultima, che rappresenterà il 10% dei messaggi.

      Nel campo **[!UICONTROL Period]** , specifica il ritardo tra l’inizio di due onde consecutive. Ad esempio, se immetti **[!UICONTROL 2d]**, la prima ondata verrà avviata immediatamente, la seconda partirà tra due giorni, la terza ondata tra quattro giorni e così via.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definisci un calendario per l’invio di ogni ondata.

      Nella colonna **[!UICONTROL Start]** specificare il ritardo tra l&#39;inizio di due onde consecutive. Nella colonna **[!UICONTROL Size]** immettere un numero fisso o una percentuale.

      Nell’esempio seguente, la prima ondata rappresenta il 25% del numero totale di messaggi inclusi nella consegna e inizierà immediatamente. Le due ondate successive completano la consegna e sono impostate per iniziare a intervalli di sei ore.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   Una regola di tipologia specifica, **[!UICONTROL Wave scheduling check]**, assicura che l’ultima ondata sia pianificata prima del limite di validità della consegna. Le tipologie di campagna e le relative regole, configurate nella scheda **[!UICONTROL Typology]** delle proprietà di consegna, sono presentate in [Processo di convalida con tipologie](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Assicurati che le ultime ondate non superino la scadenza di consegna, definita nella scheda **[!UICONTROL Validity]** . In caso contrario, alcuni messaggi potrebbero non essere inviati.
   >
   >È inoltre necessario disporre di tempo sufficiente per i nuovi tentativi durante la configurazione delle ultime ondate. Vedi [questa sezione](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).

1. Per monitorare gli invii, passa ai registri di consegna. Consulta [questa pagina](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

   Puoi visualizzare le consegne già inviate nelle ondate elaborate (**[!UICONTROL Sent]** stato) e le consegne da inviare nelle onde rimanenti (**[!UICONTROL Pending]** stato ).

I due esempi seguenti sono i casi d’uso più comuni per l’utilizzo di più ondate.

* **Durante il processo di espansione**

   Quando le e-mail vengono inviate utilizzando una nuova piattaforma, i provider di servizi Internet (ISP) sono sospetti riguardo agli indirizzi IP non riconosciuti. Se grandi volumi di e-mail vengono improvvisamente inviati, gli ISP spesso li contrassegnano come spam.

   Per evitare di essere contrassegnati come spam, è possibile aumentare progressivamente il volume inviato utilizzando le onde. Questo dovrebbe garantire uno sviluppo fluido della fase di avvio e consentire di ridurre il tasso complessivo di indirizzi non validi.

   A tale scopo, utilizza l’opzione **[!UICONTROL Schedule waves according to a calendar]** . Ad esempio, impostate la prima ondata su 10%, la seconda su 15% e così via.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagne che coinvolgono un call center**

   Quando gestisci una campagna di fidelizzazione telefonica, la tua organizzazione ha una capacità limitata di elaborare il numero di chiamate per contattare gli abbonati.

   Utilizzando le ondate, puoi limitare il numero di messaggi a 20 al giorno, corrispondente alla capacità di elaborazione giornaliera di un call center.

   A questo scopo, seleziona l’opzione **[!UICONTROL Schedule multiple waves of the same size]** . Immetti **[!UICONTROL 20]** come dimensione dell&#39;onda e **[!UICONTROL 1d]** nel campo **[!UICONTROL Period]** .

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Configurazione dei nuovi tentativi {#configuring-retries}

I messaggi temporaneamente non consegnati a causa di un errore **Soft** o **Ignored** sono soggetti a un nuovo tentativo automatico. I tipi e i motivi di errori di consegna sono descritti in questa sezione [sezione](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento all’ [MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), le impostazioni dei nuovi tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito e il periodo di tempo che li separa sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte non recapitate provenienti dal dominio e-mail del messaggio.

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA di Campaign legacy, la sezione centrale della scheda **[!UICONTROL Delivery]** per i parametri di consegna indica quanti tentativi devono essere eseguiti il giorno successivo alla consegna e il ritardo minimo tra nuovi tentativi.

![](assets/s_ncs_user_wizard_retry_param.png)

Per impostazione predefinita, sono pianificati cinque nuovi tentativi per il primo giorno della consegna con un intervallo minimo di un’ora suddiviso nelle 24 ore del giorno. Un nuovo tentativo al giorno viene programmato dopo e fino alla scadenza della consegna, definita nella scheda **[!UICONTROL Validity]** (consulta [Definizione del periodo di validità](#defining-validity-period)).

## Definizione del periodo di validità {#defining-validity-period}

Quando la consegna è stata avviata, i messaggi (ed eventuali tentativi) possono essere inviati fino alla scadenza della consegna. Questo è indicato nelle proprietà di consegna tramite la scheda **[!UICONTROL Validity]** .

![](assets/s_ncs_user_email_del_valid_period.png)

* Il campo **[!UICONTROL Delivery duration]** ti consente di immettere il limite per i tentativi di consegna globali. Questo significa che Adobe Campaign invia i messaggi a partire dalla data di inizio e quindi, per i messaggi che restituiscono un errore, vengono eseguiti tentativi regolari e configurabili fino al raggiungimento del limite di validità.

   Puoi anche scegliere di specificare le date. A questo scopo, seleziona **[!UICONTROL Explicitly set validity dates]**. In questo caso, le date del limite di consegna e validità ti consentono anche di specificare l’ora. L’ora corrente viene utilizzata per impostazione predefinita, ma puoi modificarla direttamente nel campo di input.

   >[!IMPORTANT]
   >
   >Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento all’ [MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), l’impostazione **[!UICONTROL Delivery duration]** nelle consegne e-mail di Campaign verrà utilizzata solo se è impostata su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni, questo non verrà preso in considerazione.

* **Limite di validità delle risorse**: Il  **[!UICONTROL Validity limit]** campo viene utilizzato per le risorse caricate, principalmente per la pagina speculare e per le immagini. Le risorse presenti in questa pagina sono valide per un periodo di tempo limitato (per risparmiare spazio su disco).

   I valori in questo campo possono essere espressi nelle unità elencate in [questa sezione](../../platform/using/adobe-campaign-workspace.md#default-units).
