---
product: campaign
title: Configurare e inviare la consegna
description: Scopri come configurare e inviare la consegna
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Channel Configuration
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1502'
ht-degree: 11%

---

# Configurare e inviare la consegna {#configuring-and-sending-the-delivery}



## Autorizzazioni{#delivery-permissions}

Solo il proprietario della consegna può avviare una consegna. Affinché altri operatori (o gruppi di operatori) possano avviare una consegna, aggiungili come revisori nel **[!UICONTROL Delivery start:]** campo . [Ulteriori informazioni](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Parametri aggiuntivi di consegna {#delivery-additiona-parameters}

Prima di inviare la consegna, puoi definire i parametri di invio nelle proprietà di consegna tramite la **[!UICONTROL Delivery]** scheda .

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: utilizza questa opzione per modificare l’ordine di invio delle consegne impostandone il livello di priorità: normale, alta o bassa.

* **[!UICONTROL Message batch quantity]**: utilizza questa opzione per definire il numero di messaggi raggruppati all’interno dello stesso pacchetto di consegna XML. Se il parametro è impostato su 0, i messaggi vengono raggruppati automaticamente. La dimensione del pacchetto è definita dal calcolo `<delivery size>/1024`, con un minimo di 8 messaggi e un massimo di 256 messaggi per pacchetto.

   >[!IMPORTANT]
   >
   >Quando la consegna viene creata duplicando una consegna esistente, questo parametro viene reimpostato.

* **[!UICONTROL Send using multiple waves]**: utilizza questa opzione per inviare i messaggi in batch anziché a tutto il pubblico contemporaneamente. [Ulteriori informazioni](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: utilizza questa opzione per testare l’invio tramite SMTP. La consegna viene elaborata fino alla connessione al server SMTP, ma non viene inviata: per ogni destinatario della consegna, Campaign si connette al server del provider SMTP, esegue il comando SMTP RCPT TO e chiude la connessione prima del comando SMTP DATA.

   >[!NOTE]
   >
   >* Questa opzione non deve essere impostata in mid-sourcing.
   >
   >* Ulteriori informazioni sulla configurazione del server SMTP, in [questa sezione](../../installation/using/configure-delivery-settings.md).


* **[!UICONTROL Email BCC]**: utilizza questa opzione per memorizzare le e-mail su un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN al target del messaggio. [Ulteriori informazioni](sending-messages.md#archiving-emails).

## Conferma consegna {#confirming-delivery}

Quando la consegna è configurata e pronta per l’invio, esegui l’analisi della consegna.

A questo scopo, fai clic su **[!UICONTROL Send]**, seleziona l’azione desiderata e fai clic su **[!UICONTROL Analyze]**. [Ulteriori informazioni](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Al termine, fai clic su **[!UICONTROL Confirm delivery]** per avviare la consegna dei messaggi.

Puoi quindi chiudere la procedura guidata di consegna e tenere traccia dell’esecuzione della consegna dal **[!UICONTROL Delivery]** , accessibile tramite i dettagli di questa consegna o tramite l’elenco delle consegne.

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [Monitorare una consegna](about-delivery-monitoring.md)
* [Errori di consegna](understanding-delivery-failures.md)
* [Informazioni sul tracciamento dei messaggi](about-message-tracking.md)

## Pianificare l’invio della consegna {#scheduling-the-delivery-sending}

Puoi posticipare l’invio del messaggio pianificando la consegna.

1. Fai clic sul pulsante **[!UICONTROL Send]** e seleziona il pulsante **[!UICONTROL Postpone delivery]** opzione .

1. Specifica una data di inizio nel **[!UICONTROL Contact date]** campo .

![](assets/dlv_email_del_plan.png)

1. Puoi quindi avviare l’analisi della consegna, quindi confermare l’invio della consegna. Tuttavia, l’invio della consegna inizia solo la data indicata nella **[!UICONTROL Contact date]** campo .

>[!IMPORTANT]
>
>Una volta avviata l’analisi, la data di contatto definita viene corretta. Se modifichi questa data, devi riavviare l’analisi in modo che le modifiche vengano prese in considerazione.

![](assets/s_ncs_user_email_del_start_delayed.png)

Nell’elenco delle consegne, la consegna verrà visualizzata con **[!UICONTROL Pending]** stato.

![](assets/s_ncs_user_email_del_waiting.png)

La programmazione può essere configurata a monte tramite **[!UICONTROL Scheduling]** pulsante della consegna.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Ti consente di rinviare la consegna a una data successiva o di salvarla nel calendario provvisorio.

* La **[!UICONTROL Schedule delivery (no automatic execution)]** consente di pianificare un’analisi provvisoria della consegna.

   Quando questa configurazione viene salvata, la consegna viene modificata in **[!UICONTROL Targeting pending]** stato. L’analisi verrà avviata alla data specificata.

* La **[!UICONTROL Schedule delivery (automatic execution on planned date)]** consente di specificare la data di consegna.

   Fai clic su **[!UICONTROL Send]** e seleziona **[!UICONTROL Postpone delivery]** quindi avvia l’analisi e conferma la consegna. Al termine dell’analisi, il target di consegna è pronto e i messaggi verranno inviati automaticamente alla data specificata.

Le date e gli orari sono espressi nel fuso orario dell’operatore corrente. La **[!UICONTROL Time zone]** l’elenco a discesa situato sotto il campo di immissione della data di contatto consente di convertire automaticamente la data e l’ora inserite nel fuso orario selezionato.

Ad esempio, se pianifichi l’esecuzione automatica di una consegna alle 8 ora di Londra, l’ora viene automaticamente convertita nel fuso orario selezionato:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Invia in più scaglioni {#sending-using-multiple-waves}

Per bilanciare il carico, puoi dividere le consegne in più batch. Configura il numero di batch e la loro proporzione rispetto all’intera consegna.

>[!NOTE]
>
>È possibile definire solo le dimensioni e il ritardo tra due onde consecutive. Impossibile configurare i criteri di selezione dei destinatari per ogni ondata.

1. Apri la finestra delle proprietà di consegna e fai clic sul pulsante **[!UICONTROL Delivery]** scheda .
1. Seleziona la **[!UICONTROL Send using multiple waves]** e fai clic su **[!UICONTROL Define waves...]** link.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Per configurare le onde, puoi effettuare le seguenti operazioni:

   * Definisci le dimensioni per ogni onda. Ad esempio, se immetti **[!UICONTROL 30%]** nel campo corrispondente, ogni ondata rappresenta il 30% dei messaggi inclusi nella consegna, tranne l’ultima, che rappresenterà il 10% dei messaggi.

      In **[!UICONTROL Period]** campo , specificare il ritardo tra l&#39;inizio di due onde consecutive. Ad esempio, se immetti **[!UICONTROL 2d]** La prima onda inizierà immediatamente, la seconda inizierà tra due giorni, la terza in quattro giorni e così via.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definisci un calendario per l’invio di ogni ondata.

      In **[!UICONTROL Start]** specificare il ritardo tra l&#39;inizio di due onde consecutive. In **[!UICONTROL Size]** immettere un numero fisso o una percentuale.

      Nell’esempio seguente, la prima ondata rappresenta il 25% del numero totale di messaggi inclusi nella consegna e inizierà immediatamente. Le due ondate successive completano la consegna e sono impostate per iniziare a intervalli di sei ore.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   Una regola di tipologia specifica, **[!UICONTROL Wave scheduling check]**, assicura che l’ultima ondata sia pianificata prima del limite di validità della consegna. Le tipologie di campagna e le relative regole, configurate nel **[!UICONTROL Typology]** scheda delle proprietà di consegna, sono presentate in [Processo di convalida con tipologie](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Assicurati che le ultime ondate non superino il termine di consegna, definito in **[!UICONTROL Validity]** scheda . In caso contrario, alcuni messaggi potrebbero non essere inviati.
   >
   >È inoltre necessario disporre di tempo sufficiente per i nuovi tentativi durante la configurazione delle ultime ondate. Vedi [questa sezione](steps-sending-the-delivery.md#configuring-retries).

1. Per monitorare gli invii, passa ai registri di consegna. Consulta [questa pagina](delivery-dashboard.md#delivery-logs-and-history).

   Puoi vedere le consegne che erano già state inviate nelle ondate elaborate (**[!UICONTROL Sent]** stato) e le consegne da inviare nelle onde rimanenti (**[!UICONTROL Pending]** status).

I due esempi seguenti sono i casi d’uso più comuni per l’utilizzo di più ondate.

* **Durante il processo di espansione**

   Quando le e-mail vengono inviate utilizzando una nuova piattaforma, i provider di servizi Internet (ISP) sono sospetti riguardo agli indirizzi IP non riconosciuti. Se grandi volumi di e-mail vengono improvvisamente inviati, gli ISP spesso li contrassegnano come spam.

   Per evitare di essere contrassegnati come spam, è possibile aumentare progressivamente il volume inviato utilizzando le onde. Questo dovrebbe garantire uno sviluppo fluido della fase di avvio e consentire di ridurre il tasso complessivo di indirizzi non validi.

   A tale scopo, utilizza le **[!UICONTROL Schedule waves according to a calendar]** opzione . Ad esempio, impostate la prima ondata su 10%, la seconda su 15% e così via.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagne che coinvolgono un call center**

   Quando gestisci una campagna di fidelizzazione telefonica, la tua organizzazione ha una capacità limitata di elaborare il numero di chiamate per contattare gli abbonati.

   Utilizzando le ondate, puoi limitare il numero di messaggi a 20 al giorno, corrispondente alla capacità di elaborazione giornaliera di un call center.

   A questo scopo, seleziona la **[!UICONTROL Schedule multiple waves of the same size]** opzione . Invio **[!UICONTROL 20]** come le dimensioni dell&#39;onda e **[!UICONTROL 1d]** in **[!UICONTROL Period]** campo .

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Configura nuovi tentativi {#configuring-retries}

Messaggi temporaneamente non consegnati a causa di un **Morbido** o **Ignorato** Gli errori sono soggetti a un nuovo tentativo automatico. I tipi e i motivi di errori di consegna sono descritti in questo [sezione](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), le impostazioni relative ai nuovi tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito e il periodo di tempo che li separa sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte non recapitate provenienti dal dominio e-mail del messaggio.

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign, la sezione centrale della **[!UICONTROL Delivery]** la scheda per i parametri di consegna indica quanti tentativi devono essere eseguiti il giorno successivo alla consegna e il ritardo minimo tra i nuovi tentativi.

![](assets/s_ncs_user_wizard_retry_param.png)

Per impostazione predefinita, sono pianificati cinque nuovi tentativi per il primo giorno della consegna con un intervallo minimo di un’ora suddiviso nelle 24 ore del giorno. Viene programmato un nuovo tentativo al giorno dopo e fino alla scadenza della consegna, definita nella **[!UICONTROL Validity]** scheda . Vedi [Definire il periodo di validità](#defining-validity-period).

## Definire il periodo di validità {#defining-validity-period}

Quando la consegna è stata avviata, i messaggi (ed eventuali tentativi) possono essere inviati fino alla scadenza della consegna. Questo è indicato nelle proprietà di consegna tramite il **[!UICONTROL Validity]** scheda .

![](assets/s_ncs_user_email_del_valid_period.png)

* La **[!UICONTROL Delivery duration]** consente di immettere il limite per i tentativi di consegna globali. Questo significa che Adobe Campaign invia i messaggi a partire dalla data di inizio e quindi, per i messaggi che restituiscono un errore, vengono eseguiti nuovi tentativi regolari e configurabili fino al raggiungimento del limite di validità.

   Puoi anche scegliere di specificare le date. A questo scopo, seleziona **[!UICONTROL Explicitly set validity dates]**. In questo caso, per le date di consegna e del limite validità puoi anche specificare l’ora. Per impostazione predefinita viene utilizzata l’ora corrente, ma puoi modificarla direttamente nel campo di input.

   >[!IMPORTANT]
   >
   >Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), **[!UICONTROL Delivery duration]** l’impostazione nelle consegne e-mail di Campaign viene utilizzata solo se è impostata su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni, questo non verrà preso in considerazione.

* **Limite di validità delle risorse**: La **[!UICONTROL Validity limit]** viene utilizzato per le risorse caricate, principalmente per la pagina speculare e per le immagini. Le risorse presenti in questa pagina sono valide per un periodo di tempo limitato (per risparmiare spazio su disco).

   I valori in questo campo possono essere espressi nelle unità elencate in [questa sezione](../../platform/using/adobe-campaign-workspace.md#default-units).
