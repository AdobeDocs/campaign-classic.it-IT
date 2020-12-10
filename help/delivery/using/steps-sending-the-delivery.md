---
solution: Campaign Classic
product: campaign
title: Configurazione e invio della consegna
description: Configurazione e invio della consegna
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '1521'
ht-degree: 5%

---


# Configurazione e invio della consegna {#configuring-and-sending-the-delivery}

>[!NOTE]
>
>Solo il proprietario della consegna può avviare una consegna. Affinché un altro operatore (o gruppo di operatori) possa avviare una consegna, è necessario aggiungerlo come revisori nel campo **[!UICONTROL Delivery start:]**.
>
>Per ulteriori informazioni, fare riferimento a [questa sezione](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers).

## Consegna parametri aggiuntivi {#delivery-additiona-parameters}

Prima di inviare la consegna, è possibile definire i parametri di invio nelle proprietà di consegna, tramite la scheda **[!UICONTROL Delivery]**.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: Questa opzione consente di influenzare l&#39;ordine di invio delle consegne definendone il livello di priorità (normale, alto o basso). Questo consente di assegnare priorità all&#39;ordine per determinate consegne più urgenti rispetto ad altre.

* **[!UICONTROL Message batch quantity]**: Questa opzione consente di definire il numero di messaggi raggruppati nello stesso pacchetto di consegna XML. Se il parametro è impostato su 0, i messaggi vengono raggruppati automaticamente. La dimensione del pacchetto è definita dal calcolo `<delivery size>/1024`, con un minimo di 8 e un massimo di 256 messaggi per pacchetto.

   >[!CAUTION]
   >
   >Quando la consegna viene duplicata, il parametro viene reimpostato.

* **[!UICONTROL Send using multiple waves]**: Per ulteriori informazioni, vedere  [Invio tramite più onde](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: Questa opzione consente di verificare l&#39;invio di una consegna tramite SMTP. La consegna viene elaborata fino alla connessione al server SMTP, ma non viene inviata.

   >[!NOTE]
   >
   >L&#39;utilizzo di questa opzione non è consigliato durante l&#39;installazione tramite mid-sourcing per non chiamare i dati.
   >
   >Per ulteriori informazioni sulla configurazione di un server SMTP, vedere [in questa sezione](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* **[!UICONTROL Email BCC]**: Questa opzione consente di memorizzare le e-mail in un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN alla destinazione del messaggio. Per ulteriori informazioni, consultare [la sezione](../../delivery/using/sending-messages.md#archiving-emails).

Una volta che la consegna è configurata e pronta per l&#39;invio, accertati di aver eseguito l&#39; [Analisi consegna](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery). Al termine, fare clic su **[!UICONTROL Confirm delivery]** per avviare la distribuzione dei messaggi.

![](assets/s_ncs_user_email_del_send.png)

Potete quindi chiudere la procedura guidata di consegna e monitorare l&#39;esecuzione della consegna dalla scheda **[!UICONTROL Delivery]**, accessibile tramite i dettagli della consegna o tramite l&#39;elenco delle consegne.

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [Monitoraggio di una consegna](../../delivery/using/about-delivery-monitoring.md)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Informazioni sul tracking dei messaggi](../../delivery/using/about-message-tracking.md)

## Pianificazione dell&#39;invio {#scheduling-the-delivery-sending}

Puoi posticipare la consegna dei messaggi per pianificare la consegna o per gestire la pressione di vendita ed evitare di sollecitare eccessivamente una popolazione.

1. Fare clic sul pulsante **[!UICONTROL Send]** e selezionare l&#39;opzione **[!UICONTROL Postpone delivery]**.

1. Specificate una data di inizio nel campo **[!UICONTROL Contact date]**.

![](assets/dlv_email_del_plan.png)

1. Potete quindi avviare l&#39;analisi della consegna, quindi confermare l&#39;invio. Tuttavia, l&#39;invio della consegna non inizia fino alla data indicata nel campo **[!UICONTROL Contact date]**.

>[!CAUTION]
>
>Una volta avviata l&#39;analisi, la data di contatto definita è fissa. Se modificate questa data, dovrete riavviare l&#39;analisi in modo da tener conto delle modifiche apportate.

![](assets/s_ncs_user_email_del_start_delayed.png)

Nell&#39;elenco di consegna, la consegna verrà visualizzata con lo stato **[!UICONTROL Pending]**.

![](assets/s_ncs_user_email_del_waiting.png)

La pianificazione può essere configurata anche a monte tramite il pulsante **[!UICONTROL Scheduling]** della consegna.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Consente di posticipare la consegna a una data successiva o di salvarla nel calendario provvisorio.

* L&#39;opzione **[!UICONTROL Schedule delivery (no automatic execution)]** consente di pianificare un&#39;analisi provvisoria della consegna.

   Quando questa configurazione viene salvata, lo stato di consegna cambia in **[!UICONTROL Targeting pending]**. L&#39;analisi verrà avviata alla data specificata.

* L&#39;opzione **[!UICONTROL Schedule delivery (automatic execution on planned date)]** consente di specificare la data di consegna.

   Fare clic su **[!UICONTROL Send]**, selezionare **[!UICONTROL Postpone delivery]**, quindi avviare l&#39;analisi e confermare la consegna. Al termine dell&#39;analisi, la destinazione di consegna è pronta e i messaggi verranno inviati automaticamente alla data specificata.

Le date e le ore sono espresse nel fuso orario dell&#39;operatore corrente. L&#39;elenco a discesa **[!UICONTROL Time zone]** situato sotto il campo di immissione della data di contatto consente di convertire automaticamente la data e l&#39;ora inserite nel fuso orario selezionato.

Ad esempio, se pianificate una consegna da eseguire automaticamente alle 8 ora di Londra, l&#39;ora viene automaticamente convertita nel fuso orario selezionato:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Invio tramite più onde {#sending-using-multiple-waves}

Per bilanciare il carico, è possibile suddividere le consegne in più batch. Configurare il numero di batch e la loro proporzione rispetto all&#39;intera consegna.

>[!NOTE]
>
>È possibile definire solo la dimensione e il ritardo tra due onde consecutive. Impossibile configurare i criteri di selezione dei destinatari per ogni onda.

1. Aprite la finestra delle proprietà di consegna e fate clic sulla scheda **[!UICONTROL Delivery]**.
1. Selezionare l&#39;opzione **[!UICONTROL Send using multiple waves]** e fare clic sul collegamento **[!UICONTROL Define waves...]**.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Per configurare le onde, potete:

   * Definite la dimensione per ogni onda. Ad esempio, se immetti **[!UICONTROL 30%]** nel campo corrispondente, ogni onda rappresenterà il 30% dei messaggi inclusi nella consegna, ad eccezione dell&#39;ultima, che rappresenterà il 10% dei messaggi.

      Nel campo **[!UICONTROL Period]**, specificate il ritardo tra l&#39;inizio di due onde consecutive. Ad esempio, se immettete **[!UICONTROL 2d]**, la prima ondata inizierà immediatamente, la seconda ondata inizierà tra due giorni, la terza ondata tra quattro giorni e così via.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definire un calendario per l&#39;invio di ogni onda.

      Nella colonna **[!UICONTROL Start]**, specificate il ritardo tra l&#39;inizio di due onde consecutive. Nella colonna **[!UICONTROL Size]**, immettere un numero fisso o una percentuale.

      Nell&#39;esempio seguente, la prima ondata rappresenta il 25% del numero totale di messaggi inclusi nella consegna e verrà avviata immediatamente. Le due onde successive completano la consegna e sono impostate per iniziare a intervalli di sei ore.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   Una regola di tipologia specifica, **[!UICONTROL Wave scheduling check]**, garantisce che l&#39;ultima onda sia pianificata prima del limite di validità della consegna. Le tipologie di campagna e le relative regole, configurate nella scheda **[!UICONTROL Typology]** delle proprietà di consegna, sono presentate in [Processo di convalida con tipologie](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!CAUTION]
   >
   >Assicurarsi che le ultime onde non superino il termine di consegna, definito nella scheda **[!UICONTROL Validity]**. In caso contrario, alcuni messaggi potrebbero non essere inviati.
   >
   >È inoltre necessario concedere tempo sufficiente per i tentativi di configurazione delle ultime onde. Vedi [questa sezione](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).

1. Per monitorare le tue invii, vai ai registri di consegna. Consulta [questa pagina](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).

   Potete visualizzare le consegne che erano già state inviate nelle onde elaborate (**[!UICONTROL Sent]** stato) e le consegne da inviare nelle onde rimanenti (**[!UICONTROL Pending]** stato).

I due esempi seguenti sono i casi d’uso più comuni per l’utilizzo di più onde.

* **Durante il processo di rampa**

   Quando le e-mail vengono inviate utilizzando una nuova piattaforma, i provider di servizi Internet (ISP) sono sospetti rispetto agli indirizzi IP non riconosciuti. Se grandi quantità di e-mail vengono inviate improvvisamente, gli ISP spesso le contrassegnano come spam.

   Per evitare di essere contrassegnati come spam, potete aumentare progressivamente il volume inviato utilizzando le onde. Questo dovrebbe garantire uno sviluppo uniforme della fase di avvio e consentire di ridurre il tasso complessivo di indirizzi non validi.

   A tale scopo, utilizzare l&#39;opzione **[!UICONTROL Schedule waves according to a calendar]**. Ad esempio, impostate la prima ondata su 10%, la seconda su 15% e così via.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagne che coinvolgono un call center**

   Quando gestite una campagna di fedeltà telefonica, la vostra organizzazione ha una capacità limitata di elaborare il numero di chiamate per contattare gli abbonati.

   Utilizzando le onde, puoi limitare il numero di messaggi a 20 al giorno, ossia la capacità di elaborazione giornaliera di un call center.

   A questo scopo, selezionare l&#39;opzione **[!UICONTROL Schedule multiple waves of the same size]**. Immettere **[!UICONTROL 20]** come dimensione dell&#39;onda e **[!UICONTROL 1d]** nel campo **[!UICONTROL Period]**.

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Configurazione dei tentativi {#configuring-retries}

I messaggi temporaneamente non inviati a causa di un errore **Soft** o **Ignorato** sono soggetti a un nuovo tentativo automatico. I tipi di errore di consegna e i motivi sono presentati in questa sezione [](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

La sezione centrale della scheda **[!UICONTROL Delivery]** per i parametri di consegna indica quanti tentativi devono essere eseguiti il giorno successivo alla consegna e il ritardo minimo tra i tentativi.

![](assets/s_ncs_user_wizard_retry_param.png)

Per impostazione predefinita, per il primo giorno della consegna sono pianificati cinque tentativi, con un intervallo minimo di un&#39;ora ripartito nelle 24 ore del giorno. Un nuovo tentativo al giorno viene programmato dopo e fino al termine di consegna, definito nella scheda **[!UICONTROL Validity]** (vedere [Definizione del periodo di validità](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)).

>[!NOTE]
>
>Per le installazioni ospitate o ibride, se avete effettuato l&#39;aggiornamento all&#39;MTA avanzato, le impostazioni dei tentativi nella distribuzione non vengono più utilizzate da Campaign. I tentativi di rimbalzo contenuti e il tempo che intercorre tra di essi sono determinati dall’MTA avanzata in base al tipo e alla gravità delle risposte di rimbalzo provenienti dal dominio e-mail del messaggio.
>
>Tutti gli impatti sono descritti nel documento [ Adobe Campaign Enhanced MTA](https://helpx.adobe.com/it/campaign/kb/acc-campaign-enhanced-mta.html).


## Definizione del periodo di validità {#defining-validity-period}

Una volta avviata la consegna, i messaggi (e tutti i tentativi) possono essere inviati fino alla scadenza della consegna. Questo è indicato nelle proprietà di consegna, tramite la scheda **[!UICONTROL Validity]**.

![](assets/s_ncs_user_email_del_valid_period.png)

* Il campo **[!UICONTROL Delivery duration]** consente di specificare il limite per i tentativi di consegna globali. Ciò significa che  Adobe Campaign invia i messaggi a partire dalla data di inizio e che, per i messaggi che restituiscono solo un errore, vengono eseguiti tentativi regolari configurabili fino al raggiungimento del limite di validità.

   Potete anche scegliere di specificare le date. A questo scopo, selezionare **[!UICONTROL Explicitly set validity dates]**. In questo caso, le date limite di consegna e validità consentono anche di specificare l&#39;ora. L&#39;ora corrente è utilizzata per impostazione predefinita, ma è possibile modificarla direttamente nel campo di input.

* **Limite di validità delle risorse**: Il  **[!UICONTROL Validity limit]** campo viene utilizzato per le risorse caricate, principalmente per la pagina mirror e le immagini. Le risorse presenti in questa pagina sono valide per un periodo di tempo limitato (per risparmiare spazio su disco).

   I valori in questo campo possono essere espressi nelle unità elencate in [questa sezione](../../platform/using/adobe-campaign-workspace.md#default-units).

>[!NOTE]
>
>Per le installazioni ospitate o ibride, se avete effettuato l&#39;aggiornamento all&#39;MTA avanzato, l&#39;impostazione **[!UICONTROL Delivery duration]** nelle consegne della campagna sarà utilizzata solo se impostata su **3.5** giorni o meno. Se definisci un valore superiore a 3,5 giorni, questo non verrà preso in considerazione.
>
>Tutti gli impatti sono descritti nel documento [ Adobe Campaign Enhanced MTA](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html).
