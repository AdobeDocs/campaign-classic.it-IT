---
title: Configurazione e invio della consegna
seo-title: Configurazione e invio della consegna
description: Configurazione e invio della consegna
seo-description: null
page-status-flag: never-activated
uuid: 8bf70ea4-5f28-4d85-b5ce-0bd3ed3eea55
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: df29492f-ed73-4ab8-b075-e76b3b9ebce3
translation-type: tm+mt
source-git-commit: b447e316bed8e0e87d608679c147e6bd7b0815eb
workflow-type: tm+mt
source-wordcount: '1526'
ht-degree: 5%

---


# Configurazione e invio della consegna {#configuring-and-sending-the-delivery}

>[!NOTE]
>
>Solo il proprietario della consegna può avviare una consegna. Affinché un altro operatore (o gruppo di operatori) possa avviare una consegna, è necessario aggiungerlo come revisori nel **[!UICONTROL Delivery start:]** campo.
>
>Per ulteriori informazioni, consulta [questa sezione](../../campaign/using/marketing-campaign-approval.md#selecting-reviewers) .

## Consegna di parametri aggiuntivi {#delivery-additiona-parameters}

Prima di inviare la consegna, potete definire i parametri di invio nelle proprietà di consegna, tramite la **[!UICONTROL Delivery]** scheda.

![](assets/s_ncs_user_wizard_delivery.png)

* **[!UICONTROL Delivery priority]**: Questa opzione consente di influenzare l&#39;ordine di invio delle consegne definendone il livello di priorità (normale, alto o basso). Questo consente di assegnare priorità all&#39;ordine per determinate consegne più urgenti rispetto ad altre.

* **[!UICONTROL Message batch quantity]**: Questa opzione consente di definire il numero di messaggi raggruppati nello stesso pacchetto di consegna XML. Se il parametro è impostato su 0, i messaggi vengono raggruppati automaticamente. La dimensione del pacchetto è definita dal calcolo `<delivery size>/1024`, con un minimo di 8 messaggi e un massimo di 256 messaggi per pacchetto.

   >[!CAUTION]
   >
   >Quando la consegna viene duplicata, il parametro viene reimpostato.

* **[!UICONTROL Send using multiple waves]**: Per ulteriori informazioni, vedere [Invio tramite più onde](#sending-using-multiple-waves).

* **[!UICONTROL Test SMTP delivery]**: Questa opzione consente di verificare l&#39;invio di una consegna tramite SMTP. La consegna viene elaborata fino alla connessione al server SMTP, ma non viene inviata.

   >[!NOTE]
   >
   >L&#39;utilizzo di questa opzione non è consigliato durante l&#39;installazione tramite mid-sourcing per non chiamare i dati.
   >
   >Per ulteriori informazioni sulla configurazione di un server SMTP, consultare [questa sezione](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).

* **[!UICONTROL Email BCC]**: Questa opzione consente di memorizzare le e-mail in un sistema esterno tramite CCN semplicemente aggiungendo un indirizzo e-mail CCN alla destinazione del messaggio. For more on this, refer [to this section](../../delivery/using/sending-messages.md#archiving-emails).

Una volta che la consegna è configurata e pronta per l&#39;invio, accertatevi di aver eseguito l&#39;analisi [](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)Consegna. Al termine, fai clic **[!UICONTROL Confirm delivery]** per avviare la distribuzione dei messaggi.

![](assets/s_ncs_user_email_del_send.png)

Potete quindi chiudere la procedura guidata di consegna e monitorare l&#39;esecuzione della consegna dalla **[!UICONTROL Delivery]** scheda, accessibile tramite i dettagli della consegna o tramite l&#39;elenco delle consegne.

Dopo aver inviato i messaggi, puoi monitorare e tenere traccia delle consegne. Per ulteriori informazioni, consulta queste sezioni:

* [Monitoraggio di una consegna](../../delivery/using/monitoring-a-delivery.md)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Informazioni sul tracking dei messaggi](../../delivery/using/about-message-tracking.md)

## Pianificazione dell&#39;invio della consegna {#scheduling-the-delivery-sending}

Puoi posticipare la consegna dei messaggi per pianificare la consegna o per gestire la pressione di vendita ed evitare di sollecitare eccessivamente una popolazione.

1. Fate clic sul **[!UICONTROL Send]** pulsante e selezionate l’ **[!UICONTROL Postpone delivery]** opzione.

1. Specifica una data iniziale nel **[!UICONTROL Contact date]** campo.

![](assets/dlv_email_del_plan.png)

1. Potete quindi avviare l&#39;analisi della consegna, quindi confermare l&#39;invio. Tuttavia, l&#39;invio della consegna non inizia fino alla data indicata nel **[!UICONTROL Contact date]** campo.

>[!CAUTION]
>
>Una volta avviata l&#39;analisi, la data di contatto definita è fissa. Se modificate questa data, dovrete riavviare l&#39;analisi in modo da tener conto delle modifiche apportate.

![](assets/s_ncs_user_email_del_start_delayed.png)

Nell&#39;elenco di consegna, la consegna verrà visualizzata con **[!UICONTROL Pending]** stato.

![](assets/s_ncs_user_email_del_waiting.png)

La pianificazione può essere configurata anche a monte tramite il **[!UICONTROL Scheduling]** pulsante di consegna.

![](assets/s_ncs_user_email_del_save_in_calendar_ico.png)

Consente di posticipare la consegna a una data successiva o di salvarla nel calendario provvisorio.

* L&#39; **[!UICONTROL Schedule delivery (no automatic execution)]** opzione consente di pianificare un&#39;analisi provvisoria della consegna.

   Quando questa configurazione viene salvata, la consegna diventa **[!UICONTROL Targeting pending]** stato. L&#39;analisi verrà avviata alla data specificata.

* L&#39; **[!UICONTROL Schedule delivery (automatic execution on planned date)]** opzione consente di specificare la data di consegna.

   Fai clic su **[!UICONTROL Send]** e seleziona **[!UICONTROL Postpone delivery]** quindi avvia l&#39;analisi e conferma la consegna. Al termine dell&#39;analisi, la destinazione di consegna è pronta e i messaggi verranno inviati automaticamente alla data specificata.

Le date e le ore sono espresse nel fuso orario dell&#39;operatore corrente. L&#39;elenco a **[!UICONTROL Time zone]** discesa situato sotto il campo di immissione della data di contatto consente di convertire automaticamente la data e l&#39;ora inserite nel fuso orario selezionato.

Ad esempio, se pianificate una consegna da eseguire automaticamente alle 8 ora di Londra, l&#39;ora viene automaticamente convertita nel fuso orario selezionato:

![](assets/s_ncs_user_email_del_plan_calendar_timezone.png)

## Invio con più onde {#sending-using-multiple-waves}

Per bilanciare il carico, è possibile suddividere le consegne in più batch. Configurare il numero di batch e la loro proporzione rispetto all&#39;intera consegna.

>[!NOTE]
>
>È possibile definire solo la dimensione e il ritardo tra due onde consecutive. Impossibile configurare i criteri di selezione dei destinatari per ogni onda.

1. Aprite la finestra delle proprietà di consegna e fate clic sulla **[!UICONTROL Delivery]** scheda.
1. Selezionate l’ **[!UICONTROL Send using multiple waves]** opzione e fate clic sul **[!UICONTROL Define waves...]** collegamento.

   ![](assets/s_ncs_user_wizard_waves.png)

1. Per configurare le onde, potete:

   * Definite la dimensione per ogni onda. Ad esempio, se si immette **[!UICONTROL 30%]** nel campo corrispondente, ogni onda rappresenterà il 30% dei messaggi inclusi nella consegna, ad eccezione dell&#39;ultima, che rappresenterà il 10% dei messaggi.

      Nel **[!UICONTROL Period]** campo, specificate il ritardo tra l&#39;inizio di due onde consecutive. Ad esempio, se immettete **[!UICONTROL 2d]**, la prima ondata inizierà immediatamente, la seconda ondata inizierà tra due giorni, la terza ondata tra quattro giorni e così via.

      ![](assets/s_ncs_user_wizard_waves_create_size.png)

   * Definire un calendario per l&#39;invio di ogni onda.

      Nella **[!UICONTROL Start]** colonna, specificate il ritardo tra l&#39;inizio di due onde consecutive. Nella **[!UICONTROL Size]** colonna, immettere un numero fisso o una percentuale.

      Nell&#39;esempio seguente, la prima ondata rappresenta il 25% del numero totale di messaggi inclusi nella consegna e verrà avviata immediatamente. Le due onde successive completano la consegna e sono impostate per iniziare a intervalli di sei ore.

      ![](assets/s_ncs_user_wizard_waves_create.png)
   Una regola di tipologia specifica **[!UICONTROL Wave scheduling check]** assicura che l&#39;ultima onda sia pianificata prima del limite di validità della consegna. Le tipologie di campagna e le relative regole, configurate nella **[!UICONTROL Typology]** scheda delle proprietà di consegna, sono presentate nel processo di [convalida con tipologie](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

   >[!CAUTION]
   >
   >Assicurarsi che le ultime onde non superino il termine di consegna, definito nella **[!UICONTROL Validity]** scheda. In caso contrario, alcuni messaggi potrebbero non essere inviati.
   >
   >È inoltre necessario concedere tempo sufficiente per i tentativi di configurazione delle ultime onde. Vedi [questa sezione](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).

1. Per monitorare le tue invii, vai ai registri di consegna. Consulta [questa pagina](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history).

   Puoi vedere le consegne che erano già state inviate nelle onde elaborate (**[!UICONTROL Sent]** stato) e le consegne da inviare nelle onde rimanenti (**[!UICONTROL Pending]** stato).

I due esempi seguenti sono i casi d’uso più comuni per l’utilizzo di più onde.

* **Durante il processo di rampa**

   Quando le e-mail vengono inviate utilizzando una nuova piattaforma, i provider di servizi Internet (ISP) sono sospetti rispetto agli indirizzi IP non riconosciuti. Se grandi quantità di e-mail vengono inviate improvvisamente, gli ISP spesso le contrassegnano come spam.

   Per evitare di essere contrassegnati come spam, potete aumentare progressivamente il volume inviato utilizzando le onde. Questo dovrebbe garantire uno sviluppo uniforme della fase di avvio e consentire di ridurre il tasso complessivo di indirizzi non validi.

   A tal fine, utilizzate l&#39; **[!UICONTROL Schedule waves according to a calendar]** opzione. Ad esempio, impostate la prima ondata su 10%, la seconda su 15% e così via.

   ![](assets/s_ncs_user_wizard_waves_ramp-up.png)

* **Campagne che coinvolgono un call center**

   Quando gestite una campagna di fedeltà telefonica, la vostra organizzazione ha una capacità limitata di elaborare il numero di chiamate per contattare gli abbonati.

   Utilizzando le onde, puoi limitare il numero di messaggi a 20 al giorno, ossia la capacità di elaborazione giornaliera di un call center.

   To do this, select the **[!UICONTROL Schedule multiple waves of the same size]** option. Immettete **[!UICONTROL 20]** le dimensioni dell’onda e **[!UICONTROL 1d]** nel **[!UICONTROL Period]** campo.

   ![](assets/s_ncs_user_wizard_waves_call_center.png)

## Configurazione dei tentativi {#configuring-retries}

I messaggi temporaneamente non inviati a causa di un errore **soft** o **Ignorato** sono soggetti a un nuovo tentativo automatico. I tipi di errore di consegna e i motivi sono illustrati in questa [sezione](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

La sezione centrale della **[!UICONTROL Delivery]** scheda relativa ai parametri di consegna indica quanti tentativi devono essere eseguiti il giorno successivo alla consegna e il ritardo minimo tra i tentativi.

![](assets/s_ncs_user_wizard_retry_param.png)

Per impostazione predefinita, per il primo giorno della consegna sono pianificati cinque tentativi, con un intervallo minimo di un&#39;ora ripartito nelle 24 ore del giorno. Un nuovo tentativo al giorno viene programmato dopo e fino alla scadenza della consegna, definita nella **[!UICONTROL Validity]** scheda (vedere [Definizione del periodo](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)di validità).

>[!NOTE]
>
>Per le installazioni ospitate o ibride, se avete effettuato l&#39;aggiornamento all&#39;MTA avanzato, le impostazioni dei tentativi nella distribuzione non vengono più utilizzate da Campaign. I tentativi di rimbalzo contenuti e il tempo che intercorre tra di essi sono determinati dall’MTA avanzata in base al tipo e alla gravità delle risposte di rimbalzo provenienti dal dominio e-mail del messaggio.
>
>Tutti gli impatti sono descritti nel documento [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/it/campaign/kb/acc-campaign-enhanced-mta.html) .


## Definizione del periodo di validità {#defining-validity-period}

Una volta avviata la consegna, i messaggi (e tutti i tentativi) possono essere inviati fino alla scadenza della consegna. Questo è indicato nelle proprietà di consegna, tramite la **[!UICONTROL Validity]** scheda.

![](assets/s_ncs_user_email_del_valid_period.png)

* Il **[!UICONTROL Delivery duration]** campo consente di specificare il limite per i tentativi di consegna globali. Ciò significa che  Adobe Campaign invia i messaggi a partire dalla data di inizio e che, per i messaggi che restituiscono solo un errore, vengono eseguiti tentativi regolari configurabili fino al raggiungimento del limite di validità.

   Potete anche scegliere di specificare le date. A tale scopo, selezionare **[!UICONTROL Explicitly set validity dates]**. In questo caso, le date limite di consegna e validità consentono anche di specificare l&#39;ora. L&#39;ora corrente è utilizzata per impostazione predefinita, ma è possibile modificarla direttamente nel campo di input.

* **Limite di validità delle risorse**: Il **[!UICONTROL Validity limit]** campo viene utilizzato per le risorse caricate, principalmente per la pagina mirror e le immagini. Le risorse presenti in questa pagina sono valide per un periodo di tempo limitato (per risparmiare spazio su disco).

   I valori in questo campo possono essere espressi nelle unità elencate in [questa sezione](../../platform/using/adobe-campaign-workspace.md#default-units).

>[!NOTE]
>
>Per le installazioni ospitate o ibride, se avete effettuato l&#39;aggiornamento all&#39;MTA avanzato, l&#39; **[!UICONTROL Delivery duration]** impostazione nelle consegne della campagna verrà utilizzata solo se impostata su **3,5** giorni o meno. Se definisci un valore superiore a 3,5 giorni, questo non verrà preso in considerazione.
>
>Tutti gli impatti sono descritti nel documento [Adobe Campaign Enhanced MTA](https://helpx.adobe.com/it/campaign/kb/acc-campaign-enhanced-mta.html) .
