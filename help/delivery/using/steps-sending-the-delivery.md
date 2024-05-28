---
product: campaign
title: Configurare e inviare la consegna
description: Scopri come configurare e inviare la consegna
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Channel Configuration
role: User
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
source-git-commit: efd333aed2b14667dc95f92341fc16482f0fb6aa
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 11%

---

# Configurare e inviare la consegna {#configuring-and-sending-the-delivery}

## Autorizzazioni{#delivery-permissions}

Solo il proprietario della consegna può avviare una consegna. Per consentire ad altri operatori (o gruppi di operatori) di avviare una consegna, aggiungili come revisori in **[!UICONTROL Delivery start:]** campo. [Ulteriori informazioni](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Parametri aggiuntivi della consegna {#delivery-additiona-parameters}

Prima di inviare la consegna, puoi definirne i parametri nelle relative proprietà tramite **[!UICONTROL Delivery]** scheda.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: utilizza questa opzione per modificare l’ordine di invio delle consegne impostandone il livello di priorità: normale, alto o basso.

* **[!UICONTROL Message batch quantity]**: utilizza questa opzione per definire il numero di messaggi raggruppati nello stesso pacchetto di consegna XML. Se il parametro è impostato su 0, i messaggi vengono raggruppati automaticamente. La dimensione del pacchetto è definita dal calcolo `<delivery size>/1024`, con un minimo di 8 e un massimo di 256 messaggi per pacchetto.

  >[!IMPORTANT]
  >
  >Quando la consegna viene creata duplicandone una esistente, questo parametro viene reimpostato.

* **[!UICONTROL Send using multiple waves]**: utilizza questa opzione per inviare i messaggi in batch anziché all’intero pubblico contemporaneamente. [Ulteriori informazioni](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: utilizza questa opzione per verificare l’invio tramite SMTP. La consegna viene elaborata fino alla connessione al server SMTP, ma non viene inviata: per ogni destinatario della consegna, Campaign si connette al server del provider SMTP, esegue il comando SMTP RCPT TO e chiude la connessione prima del comando SMTP DATA.

  >[!NOTE]
  >
  >* Questa opzione non deve essere impostata nel mid-sourcing.
  >
  >* Ulteriori informazioni sulla configurazione del server SMTP, in [questa sezione](../../installation/using/configure-delivery-settings.md).

* **[!UICONTROL Email BCC]**: utilizza questa opzione per memorizzare le e-mail su un sistema esterno tramite Ccn semplicemente aggiungendo un indirizzo e-mail Ccn alla destinazione del messaggio. [Ulteriori informazioni](sending-messages.md#archiving-emails).

## Conferma consegna {#confirming-delivery}

Quando la consegna è configurata e pronta per essere inviata, esegui l’analisi della consegna.

A questo scopo, fai clic su **[!UICONTROL Send]**, seleziona l’azione desiderata e fai clic su **[!UICONTROL Analyze]**. [Ulteriori informazioni](steps-validating-the-delivery.md#analyzing-the-delivery).

![](assets/s_ncs_user_email_del_send.png)

Al termine, fai clic su **[!UICONTROL Confirm delivery]** per avviare la consegna dei messaggi.

Puoi quindi chiudere la procedura guidata di consegna e tenere traccia dell’esecuzione della consegna dal **[!UICONTROL Delivery]** accessibile tramite i dettagli di questa consegna o tramite l’elenco delle consegne.

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [Monitorare una consegna](about-delivery-monitoring.md)
* [Errori di consegna](understanding-delivery-failures.md)
* [Informazioni sul tracciamento dei messaggi](about-message-tracking.md)

## Pianificare l’invio della consegna {#scheduling-the-delivery-sending}

Puoi posticipare l’invio del messaggio pianificando la consegna.

1. Fai clic su **[!UICONTROL Send]** e selezionare il pulsante **[!UICONTROL Postpone delivery]** opzione.

1. Specifica una data di inizio in **[!UICONTROL Contact date]** campo.

![](assets/dlv_email_del_plan.png)

1. Puoi quindi avviare l’analisi della consegna e confermare l’invio. Tuttavia, l’invio della consegna avrà inizio solo alla data indicata nella **[!UICONTROL Contact date]** campo.

>[!IMPORTANT]
>
>Dopo aver avviato l&#39;analisi, la data di contatto definita viene corretta. Se modifichi questa data, devi riavviare l’analisi in modo da tenere conto delle modifiche apportate.

![](assets/s_ncs_user_email_del_start_delayed.png)

Nell’elenco di consegna, la consegna viene visualizzata con **[!UICONTROL Pending]** stato.

![](assets/s_ncs_user_email_del_waiting.png)

La pianificazione può essere configurata anche a monte tramite il **[!UICONTROL Scheduling]** pulsante della consegna.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Ti consente di posticipare la consegna a una data successiva o di salvarla nel calendario provvisorio.

* Il **[!UICONTROL Schedule delivery (no automatic execution)]** consente di pianificare un’analisi provvisoria della consegna.

  Quando questa configurazione viene salvata, la consegna cambia in **[!UICONTROL Targeting pending]** stato. L’analisi verrà avviata alla data specificata.

* Il **[!UICONTROL Schedule delivery (automatic execution on planned date)]** consente di specificare la data di consegna.

  Clic **[!UICONTROL Send]** e seleziona **[!UICONTROL Postpone delivery]** quindi avvia l’analisi e conferma la consegna. Al termine dell’analisi, il target della consegna è pronto e i messaggi vengono inviati automaticamente alla data specificata.

Le date e le ore sono espresse nel fuso orario dell&#39;operatore corrente. Il **[!UICONTROL Time zone]** l’elenco a discesa che si trova sotto il campo di immissione della data di contatto consente di convertire automaticamente la data e l’ora immesse nel fuso orario selezionato.

Ad esempio, se pianifichi una consegna da eseguire automaticamente alle 8 (ora di Londra), l’ora viene automaticamente convertita nel fuso orario selezionato:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Inviare in più scaglioni {#sending-using-multiple-waves}

Per bilanciare il carico, puoi dividere le consegne in più batch. Configura il numero di batch e la loro proporzione rispetto all’intera consegna.

>[!NOTE]
>
>Puoi definire solo la dimensione e il ritardo tra due scaglioni consecutivi. Non è possibile configurare i criteri di selezione dei destinatari per ogni ondata.

1. Apri la finestra delle proprietà di consegna e fai clic su **[!UICONTROL Delivery]** scheda.
1. Seleziona la **[!UICONTROL Send using multiple waves]** e fare clic sul pulsante **[!UICONTROL Define waves...]** collegamento.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Per configurare le ondate, puoi effettuare le seguenti operazioni:

   * Definite le dimensioni per ogni scaglione. Ad esempio, se si immette **[!UICONTROL 30%]** nel campo corrispondente, ogni ondata rappresenterà il 30% dei messaggi inclusi nella consegna, ad eccezione dell’ultimo, che rappresenterà il 10% dei messaggi.

     In **[!UICONTROL Period]** , specificare il ritardo tra l&#39;inizio di due scaglioni consecutivi. Ad esempio, se si immette **[!UICONTROL 2d]**, la prima ondata comincerà immediatamente, la seconda fra due giorni, la terza fra quattro giorni e così via.

     ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definisci un calendario per l&#39;invio di ogni scaglione.

     In **[!UICONTROL Start]** , specificare il ritardo tra l&#39;inizio di due ondate consecutive. In **[!UICONTROL Size]** , immettere un numero fisso o una percentuale.

     Nell’esempio seguente, la prima ondata rappresenta il 25% del numero totale di messaggi inclusi nella consegna e inizierà immediatamente. Le due fasi successive completano la consegna e sono impostate per iniziare a intervalli di sei ore.

     ![](assets/s_ncs_user_wizard_waves_create.png)

   Una regola di tipologia specifica, **[!UICONTROL Wave scheduling check]**, assicura che l’ultimo scaglione sia pianificato prima del limite di validità della consegna. Le tipologie di campagne e le relative regole, configurate in **[!UICONTROL Typology]** delle proprietà di consegna, sono presentate in [Processo di convalida con tipologie](steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!IMPORTANT]
   >
   >Assicurati che gli ultimi scaglioni non superino la scadenza di consegna, definita nella sezione **[!UICONTROL Validity]** scheda. In caso contrario, alcuni messaggi potrebbero non essere inviati.
   >
   >È inoltre necessario concedere tempo sufficiente per i nuovi tentativi durante la configurazione degli ultimi scaglioni. Consulta [questa sezione](steps-sending-the-delivery.md#configuring-retries).

1. Per monitorare gli invii, passa ai registri di consegna. Consulta [questa pagina](delivery-dashboard.md#delivery-logs-and-history).

   Puoi visualizzare le consegne già inviate negli scaglioni elaborati (**[!UICONTROL Sent]** stato) e le consegne da inviare negli scaglioni rimanenti (**[!UICONTROL Pending]** stato).

I due esempi seguenti sono i casi d’uso più comuni per l’utilizzo di più scaglioni.

* **Durante il processo di incremento**

  Quando le e-mail vengono inviate utilizzando una nuova piattaforma, i provider di servizi Internet (ISP) sospettano che gli indirizzi IP non siano riconosciuti. Se grandi quantità di e-mail vengono inviate improvvisamente, gli ISP spesso le contrassegnano come spam.

  Per evitare di essere contrassegnati come spam, puoi aumentare progressivamente il volume inviato scaglionando. Ciò dovrebbe garantire un regolare sviluppo della fase di avvio e consentirti di ridurre il tasso complessivo di indirizzi non validi.

  A tale scopo, utilizza **[!UICONTROL Schedule waves according to a calendar]** opzione. Ad esempio, imposta la prima ondata su 10%, la seconda su 15% e così via.

  ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagne che coinvolgono un call center**

  Quando gestisci una campagna fedeltà telefonicamente, la tua organizzazione ha una capacità limitata di elaborare il numero di chiamate per contattare gli abbonati.

  Utilizzando le ondate, puoi limitare il numero di messaggi a 20 al giorno, ad esempio, considerando la capacità di elaborazione giornaliera di un call center.

  A questo scopo, seleziona la **[!UICONTROL Schedule multiple waves of the same size]** opzione. Invio **[!UICONTROL 20]** come la dimensione dell&#39;onda e **[!UICONTROL 1d]** nel **[!UICONTROL Period]** campo.

  ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Configurare nuovi tentativi {#configuring-retries}

Messaggi temporaneamente non consegnati a causa di un **Morbido** o **Ignorato** sono soggetti a un nuovo tentativo automatico. I tipi e i motivi degli errori di consegna sono presentati in questo [sezione](understanding-delivery-failures.md#delivery-failure-types-and-reasons).

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), le impostazioni per i nuovi tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito non permanenti e il periodo di tempo che intercorre tra di essi sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte di mancato recapito provenienti dal dominio e-mail del messaggio.

Per le installazioni on-premise e in hosting/ibride utilizzando l’MTA di Campaign legacy, la sezione centrale della sezione **[!UICONTROL Delivery]** La scheda per i parametri di consegna indica quanti tentativi devono essere eseguiti il giorno successivo alla consegna e il ritardo minimo tra un nuovo tentativo e l’altro.

![](assets/s_ncs_user_wizard_retry_param.png)

Per impostazione predefinita, sono pianificati cinque nuovi tentativi per il primo giorno della consegna con un intervallo minimo di un’ora suddiviso nelle 24 ore del giorno. Un nuovo tentativo al giorno viene programmato dopo tale e fino alla scadenza della consegna, definita nella **[!UICONTROL Validity]** scheda. Consulta [Definire il periodo di validità](#defining-validity-period).

## Definire il periodo di validità {#defining-validity-period}

Una volta avviata la consegna, i messaggi (ed eventuali nuovi tentativi) possono essere inviati fino alla scadenza della consegna. Questo è indicato nelle proprietà di consegna tramite **[!UICONTROL Validity]** scheda.

![](assets/s_ncs_user_email_del_valid_period.png)

* Il **[!UICONTROL Delivery duration]** consente di immettere il limite per i nuovi tentativi di consegna globali. Questo significa che Adobe Campaign invia i messaggi a partire dalla data di inizio e quindi, per i messaggi che restituiscono un errore, vengono eseguiti nuovi tentativi regolari e configurabili fino al raggiungimento del limite di validità.

  Puoi anche scegliere di specificare le date. A questo scopo, seleziona **[!UICONTROL Explicitly set validity dates]**. In questo caso, per le date di consegna e del limite validità puoi anche specificare l’ora. Per impostazione predefinita viene utilizzata l’ora corrente, ma puoi modificarla direttamente nel campo di input.

  >[!IMPORTANT]
  >
  >Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), il **[!UICONTROL Delivery duration]** impostazione nelle consegne e-mail di Campaign verrà utilizzata solo se impostata su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni, questo non verrà preso in considerazione.

* **Limite di validità delle risorse**: Il **[!UICONTROL Validity limit]** Questo campo viene utilizzato per le risorse caricate, principalmente per la pagina speculare e per le immagini. Le risorse presenti in questa pagina sono valide per un periodo di tempo limitato (per risparmiare spazio su disco).

  I valori in questo campo possono essere espressi nelle unità elencate in [questa sezione](../../platform/using/adobe-campaign-workspace.md#default-units).
