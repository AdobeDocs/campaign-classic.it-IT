---
solution: Campaign Classic
product: campaign
title: Approvazione di campagne di marketing
description: Scopri come gestire le approvazioni delle campagne di marketing
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
translation-type: tm+mt
source-git-commit: 67364f80ddc51d4792e73bbf39d388bdf4297005
workflow-type: tm+mt
source-wordcount: '2434'
ht-degree: 0%

---


# Imposta e gestisci il processo di approvazione {#approving-marketing-campaigns}

Ogni fase della consegna può essere soggetta ad approvazione per garantire il pieno monitoraggio e controllo dei vari processi della campagna: targeting, contenuto, budget, estrazione e invio di una bozza.

I messaggi di notifica vengono inviati agli operatori di Adobe Campaign che sono revisori designati per informarli di una richiesta di approvazione. Verifica che i revisori dispongano delle **autorizzazioni appropriate** per l&#39;approvazione e che la relativa area di sicurezza sia definita correttamente. [Ulteriori informazioni](#selecting-reviewers).

La procedura di approvazione è presentata in [questa sezione](#checking-and-approving-deliveries).

>[!NOTE]
>
>Solo il proprietario della consegna può avviare una consegna. Affinché un altro operatore (o gruppo di operatori) sia in grado di avviare una consegna, devi aggiungerli come revisori nel campo **[!UICONTROL Delivery start:]** .\
>[Ulteriori informazioni](#selecting-reviewers).

## Principio di funzionamento {#operating-principle-}

Ad esempio, il messaggio standard per l&#39;approvazione del budget è il seguente:

![](assets/s_user_validation_link_in_mail.png)

Gli operatori del revisore possono quindi scegliere se approvare o meno il budget.

![](assets/s_user_validation_page_confirm.png)

Una volta convalidata l’operatore, l’approvazione o il rifiuto del processo viene inoltrato al dashboard di consegna.

![](assets/s_user_validation_link_in_op_board.png)

Le informazioni sono disponibili anche nei registri di approvazione della campagna.Tali registri sono accessibili tramite la scheda **[!UICONTROL Edit > Tracking > Approvals]** .

![](assets/s_user_validation_log_in_op_edit_tab.png)

Tali notifiche vengono inviate agli operatori interessati a ciascun processo per il quale è stata abilitata l’approvazione.

Le approvazioni possono essere abilitate per il modello di campagna, per ogni campagna singolarmente o per una consegna.

Tutti i processi che richiedono l’approvazione vengono selezionati nel modello della campagna ( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** scheda ), così come gli operatori incaricati dell’approvazione (riceveranno notifiche, a meno che questa opzione non sia abilitata). Per ulteriori informazioni al riguardo, consulta [questa sezione](#approving-processes).

Queste impostazioni possono essere sostituite per ogni campagna creata utilizzando questo modello e singolarmente per ogni consegna della campagna: fare clic sul pulsante **[!UICONTROL Properties]**, quindi sulla scheda **[!UICONTROL Approvals]**.

Nell’esempio seguente, il contenuto di consegna non richiederà approvazioni:

![](assets/s_user_validation_select_process_from_del.png)

## Seleziona revisori {#selecting-reviewers}

Per ciascun tipo di omologazione, gli operatori o i gruppi di operatori incaricati dell’omologazione sono selezionati dall’elenco a discesa nella consegna. Puoi aggiungere altri operatori utilizzando il collegamento **[!UICONTROL Edit...]** . Questa finestra consente inoltre di modificare la scadenza dell&#39;approvazione.

![](assets/s_user_validation_add_operator.png)

Se non viene specificato alcun revisore, il responsabile della campagna sarà responsabile dell’approvazione e riceverà le notifiche. Il manager della campagna è specificato nella scheda **[!UICONTROL Edit > Properties]** della campagna:

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>Anche tutti gli altri operatori di Adobe Campaign con diritti **[!UICONTROL Administrator]** possono approvare i lavori, ma non riceveranno notifiche.\
>Per impostazione predefinita, il gestore della campagna non può eseguire l’approvazione o avviare le consegne se sono stati definiti operatori di approvazione. Puoi modificare questo comportamento e autorizzare il gestore campagne ad approvare/avviare le consegne creando l’opzione **NmsCampaign_Activate_OwnerConfirmation** con **1** come valore.

## Modalità di approvazione {#approval-modes}

### Approvazione tramite il dashboard {#approval-via-the-dashboard}

Per approvare un processo tramite la console o l’interfaccia Web, fai clic sul collegamento appropriato nel dashboard della campagna. I processi possono essere approvati anche tramite il tracciamento della consegna o tramite il dashboard di consegna.

![](assets/s_user_validation_from_console.png)

Controllare le informazioni da approvare, scegliere se accettare o rifiutare l&#39;approvazione e, se necessario, inserire un commento. Fai clic su **[!UICONTROL Ok]** per salvare.

>[!NOTE]
>
>Se un processo è già stato approvato da un altro operatore, il collegamento di approvazione non è disponibile.

### Approvazione tramite messaggi di notifica {#approval-via-notification-messages}

Fai clic sul collegamento disponibile nel messaggio di notifica (vedi [Notifiche](#notifications)). Devi effettuare l’accesso, come illustrato di seguito:

![](assets/s_user_validation__log_in.png)

Seleziona **[!UICONTROL Accept]** o **[!UICONTROL Reject]** e immetti un commento, se necessario.

![](assets/s_user_validation_save_target_validation.png)

Fai clic su **[!UICONTROL Validate]**.

>[!NOTE]
>
>Se durante il processo sono stati generati avvisi, nella notifica viene visualizzato un avviso.

### Tracking di approvazione {#approval-tracking}

Le informazioni sono disponibili in diversi punti:

* Nel registro di approvazione della campagna, **[!UICONTROL Approvals]** scheda secondaria della scheda **[!UICONTROL Edit > Tracking]** :

   ![](assets/s_user_validation_log_from_op.png)

* Nel registro di consegna della campagna, **[!UICONTROL Deliveries]** scheda secondaria della scheda **[!UICONTROL Edit > Tracking]** :

   ![](assets/s_user_validation_log_from_delivery_list.png)

* Per visualizzare lo stato di approvazione per ogni consegna, fai clic sull’opzione **[!UICONTROL Hide/show log]** della scheda **[!UICONTROL Summary]** .

   ![](assets/s_user_validation_log_delivery.png)

* Queste informazioni sono accessibili anche tramite la scheda **[!UICONTROL Tracking > Approvals]** di ogni consegna:

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>Una volta che un operatore ha approvato o rifiutato un lavoro, gli altri operatori di revisione non possono più agire in base all&#39;approvazione.

### Approvazione automatica e manuale {#automatic-and-manual-approval}

Quando crei un flusso di lavoro di targeting, se l’approvazione è automatica (modalità predefinita), Adobe Campaign visualizza il collegamento di approvazione o invia una notifica non appena è richiesta un’approvazione.

Per scegliere la modalità di approvazione (manuale o automatica), fai clic sulla scheda **[!UICONTROL Edit > Properties]** della campagna o del modello della campagna, quindi fai clic su **[!UICONTROL Advanced campaign settings...]** e infine sulla scheda **[!UICONTROL Approvals]** .

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>La modalità di approvazione selezionata verrà applicata a tutte le consegne della campagna.

Quando viene generato un flusso di lavoro di targeting, l’approvazione manuale consente di evitare la creazione di collegamenti di approvazione o l’invio automatico di notifiche. Il dashboard della campagna offre quindi un collegamento **[!UICONTROL Submit targeting for approval]** per avviare manualmente il processo di approvazione.

Un messaggio di conferma ti consente di autorizzare le approvazioni sui processi selezionati per questa consegna.

I pulsanti di approvazione vengono quindi visualizzati sul dashboard della campagna (per questa consegna), sul dashboard di consegna e nel tracciamento della consegna. Se le notifiche sono abilitate, verranno inviate in parallelo.

Questo metodo di abilitazione delle approvazioni consente di utilizzare il targeting senza inviare notifiche spurie ai revisori.

## Notifiche {#notifications}

Le notifiche sono messaggi e-mail specifici inviati ai revisori per informarli che un processo è in attesa di approvazione. Quando l’operatore fa clic sul collegamento nel messaggio, viene visualizzata una pagina di autenticazione e, dopo l’accesso, l’operatore può visualizzare le informazioni e approvare o rifiutare il processo. È inoltre possibile inserire un commento nella finestra di approvazione.

Il contenuto delle e-mail di notifica può essere personalizzato. Consulta [Contenuto della notifica](#notification-content).

### Attiva/Disattiva notifica {#enabling-disabling-notification}

Per impostazione predefinita, i messaggi di notifica vengono inviati se l’approvazione del processo correlato è abilitata nel modello di campagna, nella campagna o nella consegna. Tuttavia, le notifiche possono essere disattivate per autorizzare solo le approvazioni dalla console.

A questo scopo, modifica la finestra di approvazione del modello di campagna o campagna ( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** scheda ) e seleziona **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

### Contenuto della notifica {#notification-content}

Il contenuto delle notifiche è definito in un modello specifico: **[!UICONTROL Notification of validations for the marketing campaign]**. Questo modello viene salvato nella cartella **[!UICONTROL Administration > Campaign management > Technical delivery templates]** della struttura di Adobe Campaign.

## Rivedi e approva le consegne {#checking-and-approving-deliveries}

Adobe Campaign ti consente di impostare processi di approvazione per le fasi principali della campagna di marketing in modalità collaborativa.

Per le consegne di direct mailing, gli operatori di Adobe Campaign possono visualizzare il file di estrazione prima che venga inviato al router e, se necessario, possono modificare il formato e riavviare l’estrazione. Consulta [Approvare un file di estrazione](#approving-an-extraction-file).

Per ogni campagna puoi approvare il target di consegna, il contenuto (consulta [Approva contenuto](#approving-content)) e i costi. Gli operatori di Adobe Campaign incaricati dell’approvazione possono ricevere una notifica tramite e-mail e accettare o rifiutare l’approvazione dalla console o tramite una connessione web. Consulta [Passaggi per approvare una consegna](#approving-processes).

Una volta completate queste fasi di convalida, è possibile avviare la consegna. [Ulteriori informazioni](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery).

### Passaggi per approvare una consegna {#approving-processes}

Le fasi che richiedono l’approvazione vengono visualizzate nel dashboard della campagna (tramite la console dell’interfaccia web). Vengono inoltre visualizzati nella tabella di tracciamento della consegna e nel dashboard di consegna.

A questo punto, lo stato della campagna è **[!UICONTROL To validate]**.

>[!NOTE]
>
>Per selezionare i processi che richiedono un’approvazione, modifica il modello della campagna. Per ulteriori informazioni, consulta [Modelli di campagna](../../campaign/using/marketing-campaign-templates.md#campaign-templates).


![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>In un flusso di lavoro di targeting, se si verifica un errore collegato a un problema di configurazione durante la preparazione dei messaggi, il collegamento **[!UICONTROL Restart message preparation]** viene visualizzato sul dashboard. Correggi l’errore e fai clic su questo collegamento per riavviare la preparazione dei messaggi ignorando la fase di targeting.

![](assets/s_user_validation_relaunch_message_preparation.png)

Per ogni consegna nella campagna, puoi approvare i seguenti processi:

* **Targeting, contenuto e budget**

   Quando le opzioni **[!UICONTROL Enable target approval]**, **[!UICONTROL Enable content approval]** o **[!UICONTROL Enable budget approval]** sono selezionate nella finestra delle impostazioni di approvazione dei processi, i collegamenti pertinenti vengono visualizzati nel dashboard della campagna per le consegne interessate.

   >[!NOTE]
   >
   >L&#39;approvazione del budget è disponibile solo se l&#39;approvazione del targeting è abilitata nella finestra delle impostazioni di approvazione. Il collegamento per l&#39;approvazione del budget viene visualizzato solo dopo l&#39;analisi del target. Inoltre, questo collegamento viene visualizzato insieme al collegamento per l’approvazione di destinazione.

   Se le opzioni **[!UICONTROL Assign content editing]** o **[!UICONTROL External content approval]** sono selezionate nella finestra delle impostazioni di approvazione, il dashboard mostrerà i collegamenti **[!UICONTROL Available content]** e **[!UICONTROL External content approval]**.

   L’approvazione del contenuto ti consente di accedere alle bozze inviate.

* **Approvazione estrazione (consegna direct mailing)**

   Quando **[!UICONTROL Enable extraction approval]** è selezionato nella finestra delle impostazioni di approvazione, il file estratto deve essere approvato prima che il router possa essere notificato.

   Un collegamento **[!UICONTROL Approve content]** è disponibile nel dashboard della campagna come mostrato di seguito:

   ![](assets/s_ncs_user_edit_file_valid.png)

   I file di estrazione possono essere visualizzati in anteprima tramite la casella di approvazione e quindi accettati o rifiutati.

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >L’anteprima del file di estrazione riguarda solo un campione di dati. L&#39;intero file di output non viene caricato.

* **Approvazione delle consegne associate**

   L’opzione **[!UICONTROL Enable individual approval of each associated delivery]** viene utilizzata per una consegna principale associata alle consegne secondarie. Per impostazione predefinita, questa opzione non è selezionata in modo da poter eseguire un&#39;approvazione globale della consegna principale. Se questa opzione è selezionata, ogni consegna deve essere approvata singolarmente.

   ![](assets/s_ncs_user_task_valid_associate.png)

### Seleziona processi approvati {#choosing-the-processes-to-be-approved}

Le fasi di approvazione sono definite con il modello associato alla campagna. Devi selezionare gli elementi da approvare dal modello e specificare gli operatori Adobe Campaign responsabili per queste approvazioni. Per ulteriori informazioni sui modelli delle campagne, consulta [questa sezione](../../campaign/using/marketing-campaign-templates.md#campaign-templates).

>[!NOTE]
>
>La configurazione di approvazione per la campagna (o modello di campagna) si applica a tutte le consegne future collegate a questa campagna. Eventuali modifiche di configurazione non verranno applicate alle consegne precedenti.

Queste informazioni possono essere ignorate per ogni campagna e consegna.

Per una campagna, fai clic sulla scheda **[!UICONTROL Edit > Properties]** , quindi sul collegamento **[!UICONTROL Advanced campaign settings...]** e infine sulla sottoscheda **[!UICONTROL Approvals]** per accedere alla pagina di configurazione delle approvazioni.

Puoi selezionare e deselezionare i processi per approvare e nominare gli operatori Adobe Campaign incaricati dell’approvazione. Possono essere singoli operatori, un gruppo di operatori o un elenco di operatori.

Per selezionare un elenco di operatori, fai clic sul collegamento **[!UICONTROL Edit...]** a destra del campo che designa il primo revisore e aggiungi tutti gli operatori necessari, come illustrato di seguito:

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Se viene definito un elenco di revisori, un processo viene approvato quando un revisore lo accetta. Il collegamento di approvazione pertinente non viene quindi più offerto nel dashboard. Quando l’invio di notifiche è abilitato, se un altro revisore fa clic sul collegamento di approvazione nel messaggio di notifica, viene informato che un altro operatore ha già approvato il processo.
>* È possibile definire una pianificazione di approvazione per la campagna nella sezione inferiore della finestra di modifica del revisore. Per impostazione predefinita, i revisori dispongono di tre giorni a partire dalla data di invio per approvare un processo. È possibile configurare un promemoria che viene inviato automaticamente agli operatori interessati prima del termine di approvazione.
>* Puoi aggiungere promemoria da questa sezione.

>



![](assets/s_ncs_user_edit_op_valid_calendar.png)

Per ogni consegna, fai clic sul pulsante **[!UICONTROL Audit]** e sulla scheda **[!UICONTROL Approvals]** per visualizzare e modificare le date di approvazione e i promemoria automatici.

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Questa scheda è disponibile dopo l’avvio del processo di approvazione del contenuto.

### Approvare un contenuto {#approving-content}

>[!CAUTION]
>
>Per approvare un contenuto, è obbligatorio un ciclo di prova. Le bozze consentono di approvare la visualizzazione di informazioni, dati di personalizzazione e verificare che i collegamenti funzionino. Scopri come creare una bozza in [questa sezione](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).
>
>Le funzionalità di approvazione dei contenuti descritte di seguito si riferiscono alla consegna delle prove.

È possibile configurare un ciclo di approvazione dei contenuti. A questo scopo, seleziona l’opzione **[!UICONTROL Enable content approval]** nella finestra delle impostazioni di approvazione. Le fasi principali del ciclo di approvazione dei contenuti sono:

1. Dopo aver creato una nuova consegna, il manager della campagna fa clic sul collegamento **[!UICONTROL Submit content]** nel dashboard della campagna per avviare il ciclo di approvazione dei contenuti.

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Se le opzioni **[!UICONTROL Enable the sending of proofs]** (per le consegne e-mail) o **[!UICONTROL Enable the sending and approval of proofs]** (per le consegne direct mail) sono state selezionate nella finestra delle impostazioni di approvazione, le bozze vengono inviate automaticamente.

1. Viene inviata un’e-mail di notifica alla persona responsabile del contenuto, che può scegliere se approvarla o meno:

   * tramite e-mail di notifica:

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >L’e-mail di notifica contiene un collegamento alle bozze già inviate e, possibilmente, a un rendering del messaggio per le varie e-mail web se l’opzione **Consegna** è abilitata per questa istanza.

   * tramite la console o l’interfaccia web, il tracciamento della consegna, il dashboard di consegna o il dashboard della campagna:

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >Questo dashboard della campagna consente di visualizzare l’elenco delle bozze inviate, facendo clic sul collegamento **[!UICONTROL Inbox rendering...]** . Per visualizzarne il contenuto, fai clic sull’icona **[!UICONTROL Detail]** a destra dell’elenco.

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. Viene inviata un’e-mail di notifica alla persona responsabile della campagna per informarla dell’approvazione o meno del contenuto.

   >[!NOTE]
   >
   >Il responsabile della campagna può riavviare il ciclo di approvazione dei contenuti in qualsiasi momento. A questo scopo, fai clic sul collegamento sulla riga **[!UICONTROL Content status]** del dashboard della campagna (a livello di consegna), quindi fai clic su **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### Assegnare la modifica dei contenuti {#assign-content-editing}

Questa opzione ti consente di definire un utente responsabile della modifica dei contenuti, ad esempio un webmaster. Se l’opzione **[!UICONTROL Assign content editing]** è selezionata nella finestra delle impostazioni di approvazione, vengono aggiunti diversi passaggi di approvazione tra la creazione della consegna e la consegna dell’e-mail di notifica alla persona responsabile del contenuto:

1. Dopo aver creato una nuova consegna, la persona responsabile della campagna fa clic sul collegamento **[!UICONTROL Submit content editing]** nel dashboard della campagna per avviare il ciclo di modifica dei contenuti.

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. Il responsabile della modifica dei contenuti riceverà un’e-mail in cui informa che il contenuto è disponibile.

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. Possono quindi accedere alla console, aprire la consegna e modificarla utilizzando una procedura guidata semplificata per modificare l’oggetto, il contenuto HTML e di testo e inviare bozze.

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Se le opzioni **[!UICONTROL Enable the sending of proofs]** (per le consegne e-mail) o **[!UICONTROL Enable the sending and approval of proofs]** (per le consegne direct mail) sono state selezionate nella finestra delle impostazioni di approvazione, le bozze vengono inviate automaticamente.

1. Una volta che il responsabile della modifica dei contenuti ha terminato di apportare modifiche al contenuto della consegna, può rendere disponibile il contenuto.

   A questo scopo, possono:

   * fai clic sul collegamento **[!UICONTROL Available content]** tramite la console Adobe Campaign.

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * fai clic sul collegamento nel messaggio di notifica, quindi approva la disponibilità del contenuto.

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      L’operatore può aggiungere un commento prima di inviare il contenuto alla persona responsabile della campagna.

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      Il messaggio di notifica consente al revisore di approvare o rifiutare il contenuto.

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### Approvazione dei contenuti esterni {#external-content-approval}

Questa opzione ti consente di definire un operatore esterno incaricato di approvare il rendering della consegna, ad esempio la coerenza della comunicazione del brand, i tassi, ecc. Quando l’opzione **[!UICONTROL External content approval]** è selezionata nella finestra delle impostazioni di approvazione, vengono aggiunti diversi passaggi di approvazione tra l’approvazione del contenuto e la consegna della notifica alla persona responsabile della campagna:

1. Il gestore dei contenuti esterni riceve un messaggio e-mail di notifica in cui viene indicato che il contenuto è stato approvato e richiede l’approvazione esterna.
1. L’e-mail di notifica contiene collegamenti alle bozze inviate, che consentono di visualizzare il rendering della consegna, e un pulsante per approvare o rifiutare il contenuto della consegna.

   >[!NOTE]
   >
   >Questi collegamenti sono disponibili solo se sono state inviate una o più bozze. In caso contrario, il rendering della consegna è disponibile solo tramite la console o l’interfaccia web.

   ![](assets/s_user_validation_external_content.png)

### Approva un file di estrazione {#approving-an-extraction-file}

Per le consegne offline, Adobe Campaign genera un file di estrazione che, a seconda della configurazione, viene inviato al router. Il relativo contenuto dipende dal modello di esportazione utilizzato.

Una volta approvati il contenuto, il targeting e il budget, la consegna cambia in **[!UICONTROL Extraction pending]** fino a quando non viene avviato il flusso di lavoro di estrazione per le campagne.

![](assets/s_ncs_user_waiting_file_extraction.png)

Alla data della richiesta di estrazione, il file di estrazione viene creato e lo stato di consegna cambia in **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

Puoi visualizzare il contenuto del file estratto (facendo clic sul suo nome), approvarlo o, se necessario, modificarne il formato e riavviare l’estrazione utilizzando i collegamenti presenti nel dashboard.

Una volta approvato il file, è possibile inviare l&#39;e-mail di notifica al router. Per ulteriori informazioni, consulta [Avviare una consegna offline](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery).
