---
title: Approvazione di campagne di marketing
seo-title: Approvazione di campagne di marketing
description: Approvazione di campagne di marketing
seo-description: null
page-status-flag: never-activated
uuid: 842b501f-7d65-4450-b7ab-aff3942fb96f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: orchestrate-campaigns
discoiquuid: 8d076211-10a6-4a98-b0d2-29dad154158c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---

# Approvazione di campagne di marketing {#approving-marketing-campaigns}

## Processo di approvazione {#approval-process}

Ogni fase della consegna può essere sottoposta ad approvazione per garantire il pieno monitoraggio e controllo dei vari processi della campagna: targeting, contenuto, budget, estrazione e invio di una prova.

>[!NOTE]
>
>È necessario verificare che i revisori dispongano dei diritti appropriati per l&#39;approvazione. Verificate inoltre che la relativa area di protezione sia definita correttamente.

Le e-mail di notifica vengono inviate agli operatori Adobe Campaign che sono stati designati per i revisori per informarli di una richiesta di approvazione.

La procedura di approvazione è presentata in [Controllo e approvazione delle consegne](#checking-and-approving-deliveries).

>[!NOTE]
>
>Solo il proprietario della consegna può avviare una consegna. Affinché un altro operatore (o gruppo di operatori) possa avviare una consegna, è necessario aggiungerlo come revisori nel **[!UICONTROL Delivery start:]** campo.\
>Consultare anche [Selezione di revisori](#selecting-reviewers).

### Principio di funzionamento {#operating-principle-}

Ad esempio, l&#39;e-mail standard per l&#39;approvazione del budget sarà la seguente:

![](assets/s_user_validation_link_in_mail.png)

Gli operatori del revisore possono quindi scegliere se approvare o meno il passaggio in questione.

![](assets/s_user_validation_page_confirm.png)

Una volta che l&#39;operatore approva la scelta, l&#39;approvazione o il rifiuto del processo viene inoltrato al dashboard di distribuzione.

![](assets/s_user_validation_link_in_op_board.png)

Le informazioni sono disponibili anche nei registri di approvazione della campagna (accessibile tramite la **[!UICONTROL Edit > Tracking > Approvals]** scheda):

![](assets/s_user_validation_log_in_op_edit_tab.png)

Tali notifiche vengono inviate agli operatori interessati a ogni processo per il quale è stata abilitata l&#39;approvazione.

Le approvazioni possono essere abilitate per il modello di campagna, per ogni campagna singolarmente o per una consegna.

Tutti i processi che richiedono l’approvazione sono selezionati nel modello della campagna ( **[!UICONTROL Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** scheda), così come gli operatori che hanno il compito dell’approvazione (riceveranno le notifiche, a meno che questa opzione non sia abilitata). Per ulteriori informazioni, consulta [Approvare i processi](#approving-processes).

Queste impostazioni possono essere sostituite per ogni campagna creata utilizzando questo modello e singolarmente per ogni distribuzione della campagna: fare clic sul **[!UICONTROL Properties]** pulsante, quindi sulla **[!UICONTROL Approvals]** scheda.

Nell&#39;esempio seguente, il contenuto di distribuzione non richiederà approvazioni:

![](assets/s_user_validation_select_process_from_del.png)

### Selezione di revisori {#selecting-reviewers}

Per ciascun tipo di omologazione, gli operatori o i gruppi di operatori incaricati dell&#39;omologazione sono selezionati dall&#39;elenco a discesa nella consegna. È possibile aggiungere altri operatori tramite il **[!UICONTROL Edit...]** collegamento. Questa finestra consente inoltre di modificare la scadenza dell’approvazione.

![](assets/s_user_validation_add_operator.png)

Se non viene specificato alcun revisore, il manager della campagna sarà responsabile dell&#39;approvazione e riceverà le notifiche. Il manager della campagna è specificato nella **[!UICONTROL Edit > Properties]** scheda della campagna:

![](assets/s_user_op_manager_field.png)

>[!NOTE]
>
>Anche tutti gli altri operatori Adobe Campaign con **[!UICONTROL Administrator]** diritti possono approvare i processi, ma non riceveranno notifiche.\
>Per impostazione predefinita, il manager campagna non può eseguire l&#39;approvazione o avviare le consegne se gli operatori di approvazione sono stati definiti. Potete modificare questo comportamento e autorizzare il manager campagna ad approvare/avviare le consegne creando l&#39;opzione **NmsCampaign_Activate_OwnerConfirm** con **1** come valore.

### Modalità di approvazione {#approval-modes}

#### Approvazione tramite il dashboard {#approval-via-the-dashboard}

Per approvare un processo tramite la console o l’interfaccia Web, fate clic sul collegamento appropriato nel dashboard della campagna. I processi possono essere approvati anche tramite il tracciamento della distribuzione o tramite il dashboard di distribuzione.

![](assets/s_user_validation_from_console.png)

Controllare le informazioni da approvare, scegliere se accettare o rifiutare l&#39;approvazione e, se necessario, immettere un commento. Fate clic **[!UICONTROL Ok]** per salvare.

>[!NOTE]
>
>Se un processo è già stato approvato da un altro operatore, il collegamento di approvazione non è disponibile.

#### Approvazione tramite messaggi di notifica {#approval-via-notification-messages}

Fate clic sul collegamento disponibile nel messaggio di notifica (consultate [Notifiche](#notifications)). Ti verrà chiesto di identificarti, come mostrato di seguito:

![](assets/s_user_validation__log_in.png)

Selezionate **[!UICONTROL Accept]** o **[!UICONTROL Reject]** immettete un commento, se necessario.

![](assets/s_user_validation_save_target_validation.png)

Clic **[!UICONTROL Validate]**.

>[!NOTE]
>
>Se durante il processo sono stati generati avvisi, nella notifica viene visualizzato un avviso.

#### Tracciamento approvazione {#approval-tracking}

Le informazioni sono disponibili in diversi punti:

* Nel registro di approvazione della campagna, **[!UICONTROL Approvals]** sottoscheda della **[!UICONTROL Edit > Tracking]** scheda:

   ![](assets/s_user_validation_log_from_op.png)

* Nel registro di distribuzione della campagna, **[!UICONTROL Deliveries]** scheda secondaria della **[!UICONTROL Edit > Tracking]** scheda:

   ![](assets/s_user_validation_log_from_delivery_list.png)

* Lo stato di approvazione per ogni consegna può essere visualizzato facendo clic sull&#39; **[!UICONTROL Hide/show log]** opzione della **[!UICONTROL Summary]** scheda.

   ![](assets/s_user_validation_log_delivery.png)

* Queste informazioni sono accessibili anche tramite la **[!UICONTROL Tracking > Approvals]** scheda di ogni consegna:

   ![](assets/s_user_validation_log_from_exe_tab.png)

>[!NOTE]
>
>Una volta che un operatore ha approvato o rifiutato un lavoro, gli altri operatori di revisione non possono più agire in seguito all&#39;approvazione.

#### Approvazione automatica e manuale {#automatic-and-manual-approval}

Durante la creazione di un flusso di lavoro di targeting, se l&#39;approvazione è automatica (modalità predefinita), Adobe Campaign visualizza il collegamento di approvazione o invia una notifica non appena è richiesta l&#39;approvazione.

Per scegliere la modalità di approvazione (manuale o automatica), fate clic sulla **[!UICONTROL Edit > Properties]** scheda della campagna o del modello di campagna, quindi fate clic **[!UICONTROL Advanced campaign settings...]** e infine sulla **[!UICONTROL Approvals]** scheda.

![](assets/s_user_validation_select_mode.png)

>[!NOTE]
>
>La modalità di approvazione selezionata verrà applicata a tutte le consegne della campagna.

Quando viene creato un flusso di lavoro di targeting, l&#39;approvazione manuale consente di evitare la creazione di collegamenti di approvazione o l&#39;invio automatico di notifiche. Il dashboard della campagna offre quindi un **[!UICONTROL Submit targeting for approval]** collegamento per avviare manualmente il processo di approvazione.

Un messaggio di conferma consente di autorizzare le approvazioni per i processi selezionati per la consegna.

I pulsanti di approvazione vengono quindi visualizzati nel dashboard della campagna (per questa consegna), nel dashboard di distribuzione e nel tracciamento della consegna. Se le notifiche sono abilitate, saranno inviate in parallelo.

Questo metodo di abilitazione delle approvazioni consente di utilizzare il targeting senza inviare notifiche push ai revisori.

### Notifications {#notifications}

Le notifiche sono messaggi e-mail specifici inviati ai revisori per informarli che un processo è in attesa di approvazione. Quando l&#39;operatore fa clic sul collegamento nel messaggio, viene visualizzata una pagina di autenticazione e, dopo l&#39;accesso, l&#39;operatore può visualizzare le informazioni e approvare o rifiutare il processo. È inoltre possibile inserire un commento nella finestra di approvazione.

Il contenuto delle e-mail di notifica può essere personalizzato. Consultate Contenuto [delle](#notification-content)notifiche.

#### Attivazione/Disattivazione delle notifiche {#enabling-disabling-notification}

Per impostazione predefinita, i messaggi di notifica vengono inviati se l’approvazione del processo correlato è abilitata nel modello di campagna, nella campagna o nella consegna. Le notifiche possono tuttavia essere disattivate per autorizzare solo le approvazioni dalla console.

A questo scopo, modificate la finestra di approvazione del modello campagna o campagna ( **[!UICONTROL Edit > Properties]** > **[!UICONTROL Advanced campaign settings...]** > **[!UICONTROL Approvals]** scheda) e selezionate **[!UICONTROL Do not enable notification sending]**.

![](assets/s_user_validation_notif_desactivate.png)

#### Contenuto notifica {#notification-content}

Il contenuto delle notifiche è definito in un modello specifico: **[!UICONTROL Notification of validations for the marketing campaign]**. Questo modello viene salvato nella **[!UICONTROL Administration > Campaign management > Technical delivery templates]** cartella della struttura di Adobe Campaign.

## Controllo e approvazione delle consegne {#checking-and-approving-deliveries}

Adobe Campaign consente di impostare i processi di approvazione per le fasi principali della campagna di marketing in modalità collaborativa.

Per le consegne per corrispondenza diretta, gli operatori di Adobe Campaign possono visualizzare il file di estrazione prima dell&#39;invio al router, e se necessario possono modificare il formato e riavviare l&#39;estrazione. Consultate [Approvazione di un file](#approving-an-extraction-file)di estrazione.

Per ogni campagna potete approvare target di consegna, contenuto (consultate [Approvazione di contenuti](#approving-content)) e costi. Gli operatori Adobe Campaign incaricati dell&#39;approvazione possono ricevere notifiche via e-mail e accettare o rifiutare l&#39;approvazione dalla console o tramite una connessione Web. Consultate [Approvare i processi](#approving-processes).

Una volta completate queste fasi di convalida, la consegna può essere avviata. Vedere [Avvio di una consegna](../../campaign/using/marketing-campaign-deliveries.md#starting-a-delivery).

>[!NOTE]
>
>Per ulteriori informazioni sulle modalità di approvazione e il tracciamento, consulta Processo [di](#approval-process)approvazione.

### Approvazione dei processi {#approving-processes}

Le fasi che richiedono l’approvazione vengono visualizzate nel dashboard della campagna (tramite la console dell’interfaccia Web). Vengono inoltre visualizzati nella tabella di tracciamento della consegna e nel dashboard di consegna.

A questo punto, lo stato della campagna è **[!UICONTROL To validate]**.

>[!NOTE]
>
>* Per selezionare i processi che saranno soggetti all&#39;approvazione, modificate il modello della campagna. Per ulteriori informazioni, consulta Modelli [per](../../campaign/using/marketing-campaign-templates.md#campaign-templates)campagne.
   >
   >
* Consultare anche la sezione relativa al processo di [approvazione](#approval-process).



![](assets/s_ncs_user_edit_del_to_validate.png)

>[!NOTE]
>
>In un flusso di lavoro di targeting, se si verifica un errore collegato a un problema di configurazione durante la preparazione dei messaggi, il **[!UICONTROL Restart message preparation]** collegamento viene visualizzato nel dashboard. Correggete l&#39;errore e fate clic su questo collegamento per riavviare la preparazione dei messaggi evitando la fase di targeting.

![](assets/s_user_validation_relaunch_message_preparation.png)

Per ogni consegna nella campagna, potete approvare i seguenti processi:

* **Targeting, contenuti e budget**

   Quando **[!UICONTROL Enable target approval]**, **[!UICONTROL Enable content approval]** o **[!UICONTROL Enable budget approval]** le opzioni sono selezionate nella finestra delle impostazioni di approvazione del processo, i collegamenti pertinenti vengono visualizzati nel dashboard della campagna per le consegne interessate.

   >[!NOTE]
   >
   >L&#39;approvazione del budget è disponibile solo se l&#39;approvazione del targeting è abilitata nella finestra delle impostazioni di approvazione. Il collegamento per l&#39;approvazione del budget viene visualizzato solo dopo l&#39;analisi della destinazione. Inoltre, questo collegamento viene visualizzato insieme al collegamento per l&#39;approvazione della destinazione.

   Se le opzioni **[!UICONTROL Assign content editing]** o **[!UICONTROL External content approval]** sono selezionate nella finestra delle impostazioni di approvazione, nel dashboard vengono visualizzati i **[!UICONTROL Available content]** collegamenti e **[!UICONTROL External content approval]** .

   L&#39;approvazione del contenuto consente di accedere alle prove di stampa inviate.

* **Approvazione estrazione (consegna diretta per posta)**

   Se **[!UICONTROL Enable extraction approval]** è selezionato nella finestra delle impostazioni di approvazione, il file estratto deve essere approvato prima che il router possa essere informato.

   Un **[!UICONTROL Approve content]** collegamento è disponibile nel dashboard della campagna come mostrato di seguito:

   ![](assets/s_ncs_user_edit_file_valid.png)

   I file di estrazione possono essere visualizzati in anteprima tramite la casella di approvazione, quindi accettati o rifiutati.

   ![](assets/s_ncs_user_edit_file_valid_preview_file.png)

   >[!NOTE]
   >
   >L’anteprima del file di estrazione riguarda solo un esempio di dati. L&#39;intero file di output non viene caricato.

* **Approvazione delle consegne associate**

   L&#39; **[!UICONTROL Enable individual approval of each associated delivery]** opzione viene utilizzata per una consegna principale associata alle consegne secondarie. Per impostazione predefinita, questa opzione non è selezionata in modo che sia possibile eseguire un&#39;approvazione globale della consegna principale. Se questa opzione è selezionata, ogni consegna deve essere approvata singolarmente.

   ![](assets/s_ncs_user_task_valid_associate.png)

#### Selezione dei processi da approvare {#choosing-the-processes-to-be-approved}

Le fasi di approvazione sono definite con il modello associato alla campagna. Devi selezionare gli elementi da approvare dal modello e specificare gli operatori Adobe Campaign che saranno responsabili di queste approvazioni. Per ulteriori informazioni, consulta Modelli [per](../../campaign/using/marketing-campaign-templates.md#campaign-templates)campagne.

>[!NOTE]
>
>La configurazione di approvazione per il modello di campagna o campagna verrà applicata a tutte le consegne future collegate a questa campagna. Eventuali modifiche alla configurazione non verranno applicate alle consegne precedenti.

Queste informazioni possono essere sostituite per ogni campagna e consegna.

Per una campagna, fare clic sulla **[!UICONTROL Edit > Properties]** scheda, quindi sul **[!UICONTROL Advanced campaign settings...]** collegamento e infine sulla **[!UICONTROL Approvals]** sottoscheda per accedere alla pagina di configurazione delle approvazioni.

Puoi selezionare e deselezionare i processi per approvare e nominare gli operatori Adobe Campaign incaricati dell&#39;approvazione. Può trattarsi di singoli operatori, di un gruppo di operatori o di un elenco di operatori.

Per selezionare un elenco di operatori, fare clic sul **[!UICONTROL Edit...]** collegamento a destra del campo a destra del primo revisore e aggiungere tutti gli operatori necessari, come illustrato di seguito:

![](assets/s_user_validation_add_operator.png)

>[!NOTE]
>
>* Se viene definito un elenco di revisori, un processo viene approvato non appena un revisore lo accetta. Il collegamento di approvazione non viene più visualizzato nel dashboard. Quando l&#39;invio di notifiche è abilitato, se un altro revisore fa clic sul collegamento di approvazione nel messaggio di notifica, viene loro notificato che un altro operatore ha già approvato il processo.
>* Potete definire una pianificazione di approvazione per la campagna nella sezione inferiore della finestra di modifica del revisore. Per impostazione predefinita, i revisori dispongono di tre giorni a partire dalla data di invio per approvare un processo. È possibile configurare un promemoria che viene inviato automaticamente agli operatori interessati prima del termine di approvazione.
>* Potete aggiungere promemoria da questa sezione.
>



![](assets/s_ncs_user_edit_op_valid_calendar.png)

Per ogni consegna, fate clic sul **[!UICONTROL Audit]** pulsante e sulla **[!UICONTROL Approvals]** scheda per visualizzare e modificare le date di approvazione e i promemoria automatici.

![](assets/s_ncs_user_edit_del_valid.png)

>[!NOTE]
>
>Questa scheda è disponibile dopo l’avvio del processo di approvazione del contenuto.

### Approvazione del contenuto {#approving-content}

>[!CAUTION]
>
>Per approvare un contenuto, è obbligatorio eseguire un ciclo di prova. Le prove consentono di approvare la visualizzazione di informazioni, i dati di personalizzazione e verificare che i collegamenti funzionino. Per ulteriori informazioni sulla creazione di una prova e sul suo ciclo di vita, consulta la sezione [Invio di messaggi](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof) .
>
>Le funzionalità di approvazione dei contenuti descritte di seguito sono progettate per essere aggiunte alla consegna della prova.

È possibile configurare un ciclo di approvazione dei contenuti. A questo scopo, selezionate l’ **[!UICONTROL Enable content approval]** opzione nella finestra delle impostazioni di approvazione. Le fasi principali del ciclo di approvazione dei contenuti sono:

1. Dopo aver creato una nuova distribuzione, il manager campagna fa clic sul **[!UICONTROL Submit content]** collegamento nel dashboard della campagna per avviare il ciclo di approvazione dei contenuti.

   ![](assets/s_ncs_user_validation_submit_content_validation.png)

   >[!NOTE]
   >
   >Se nella finestra delle impostazioni di approvazione sono state selezionate le opzioni **[!UICONTROL Enable the sending of proofs]** (per le consegne e-mail) o **[!UICONTROL Enable the sending and approval of proofs]** (per le consegne per corrispondenza diretta), le prove verranno inviate automaticamente.

1. Un messaggio e-mail di notifica viene inviato alla persona responsabile del contenuto, che può scegliere se approvarlo o meno:

   * tramite il messaggio e-mail di notifica:

      ![](assets/s_ncs_user_del_content_valid_bat_notif.png)

      >[!NOTE]
      >
      >Il messaggio e-mail di notifica contiene un collegamento alle prove di prova già inviate ed eventualmente un rendering del messaggio per i vari webmail, se l&#39;opzione **Consegna** è abilitata per questa istanza.

   * tramite la console o l’interfaccia Web, il tracciamento della distribuzione, il dashboard di distribuzione o il dashboard della campagna:

      ![](assets/s_ncs_user_validation_content_bat_op.png)

      >[!NOTE]
      >
      >Questa dashboard della campagna consente di visualizzare l&#39;elenco delle prove che sono state inviate facendo clic sul **[!UICONTROL Inbox rendering...]** collegamento. Per visualizzarne il contenuto, fate clic sull’ **[!UICONTROL Detail]** icona a destra dell’elenco.

      ![](assets/s_ncs_user_validation_content_BAT_details.png)

1. Viene inviato un messaggio e-mail di notifica alla persona responsabile della campagna in cui viene indicato se il contenuto è stato approvato o meno.

   >[!NOTE]
   >
   >Il responsabile della campagna può riavviare il ciclo di approvazione dei contenuti in qualsiasi momento. A questo scopo, fate clic sul collegamento sulla **[!UICONTROL Content status]** linea del dashboard della campagna (a livello di consegna), quindi fate clic **[!UICONTROL Reset content approval to submit it again]**.

   ![](assets/s_user_validation_relaunch_content_validation.png)

#### Assegnazione della modifica del contenuto {#assign-content-editing}

Questa opzione consente di definire un utente responsabile della modifica del contenuto, ad esempio un webmaster. Se l’ **[!UICONTROL Assign content editing]** opzione è selezionata nella finestra delle impostazioni di approvazione, vengono aggiunti diversi passaggi di approvazione tra la creazione della consegna e la consegna dell’e-mail di notifica alla persona responsabile del contenuto:

1. Dopo aver creato una nuova consegna, la persona responsabile della campagna fa clic sul **[!UICONTROL Submit content editing]** collegamento nel dashboard della campagna per avviare il ciclo di modifica dei contenuti.

   ![](assets/s_ncs_user_validation_submit_content_edition.png)

1. Il responsabile della modifica dei contenuti riceverà un messaggio e-mail in cui informa che il contenuto è disponibile.

   ![](assets/s_ncs_user_validation_submit_content_notif.png)

1. Possono quindi accedere alla console, aprire la distribuzione e modificarla utilizzando una procedura guidata semplificata per modificare l’oggetto, il contenuto HTML e di testo e inviare le prove di stampa.

   ![](assets/s_user_validation_content_edition.png)

   >[!NOTE]
   >
   >Se nella finestra delle impostazioni di approvazione sono state selezionate le opzioni **[!UICONTROL Enable the sending of proofs]** (per le consegne e-mail) o **[!UICONTROL Enable the sending and approval of proofs]** (per le consegne per corrispondenza diretta), le prove verranno inviate automaticamente.

1. Una volta che il responsabile della modifica dei contenuti ha terminato di apportare modifiche ai contenuti da distribuire, può rendere disponibili i contenuti.

   A tal fine, possono:

   * fai clic sul **[!UICONTROL Available content]** collegamento tramite la console di Adobe Campaign.

      ![](assets/s_ncs_user_validation_submit_content_available.png)

   * fai clic sul collegamento nel messaggio di notifica, quindi approva la disponibilità del contenuto.

      ![](assets/s_ncs_user_validation_submit_content_available2.png)

      L&#39;operatore può aggiungere un commento prima di inviare il contenuto alla persona responsabile della campagna.

      ![](assets/s_ncs_user_validation_submit_content_available3.png)

      Il messaggio di notifica consente al revisore di approvare o rifiutare il contenuto.

      ![](assets/s_ncs_user_validation_submit_content_available4.png)

#### Approvazione di contenuti esterni {#external-content-approval}

Questa opzione consente di definire un operatore esterno incaricato di approvare il rendering della distribuzione, ad esempio la coerenza della comunicazione del marchio, le tariffe ecc. Quando l&#39; **[!UICONTROL External content approval]** opzione è selezionata nella finestra delle impostazioni di approvazione, vengono aggiunti diversi passaggi di approvazione tra l&#39;approvazione del contenuto e la consegna della notifica alla persona responsabile della campagna:

1. Il manager del contenuto esterno riceve un messaggio e-mail di notifica in cui informa che il contenuto è stato approvato e richiede l’approvazione esterna.
1. Il messaggio e-mail di notifica contiene collegamenti alle prove di stampa inviate, che consentono di visualizzare il rendering della consegna, e un pulsante per approvare o rifiutare il contenuto della consegna.

   >[!NOTE]
   >
   >Questi collegamenti sono disponibili solo se sono state inviate una o più prove di stampa. In caso contrario, il rendering della distribuzione è disponibile solo tramite la console o l&#39;interfaccia Web.

   ![](assets/s_user_validation_external_content.png)

### Approvazione di un file di estrazione {#approving-an-extraction-file}

Per le consegne offline, Adobe Campaign genera un file di estrazione che, a seconda della configurazione, viene inviato al router. Il relativo contenuto dipende dal modello di esportazione utilizzato.

Quando il contenuto, il targeting e il budget sono stati approvati, la distribuzione diventa **[!UICONTROL Extraction pending]** finché non viene avviato il flusso di lavoro di estrazione per le campagne.

![](assets/s_ncs_user_waiting_file_extraction.png)

Alla data della richiesta di estrazione, il file di estrazione viene creato e lo stato di consegna cambia in **[!UICONTROL File to approve]**.

![](assets/s_ncs_user_file_extract_to_valid.png)

Potete visualizzare il contenuto del file estratto (facendo clic sul suo nome), approvarlo o, se necessario, modificarne il formato e riavviare l&#39;estrazione utilizzando i collegamenti nel dashboard.

Una volta che il file è stato approvato, è possibile inviare l&#39;e-mail di notifica al router. Per ulteriori informazioni, vedere [Avvio della distribuzione](../../campaign/using/marketing-campaign-deliveries.md#starting-an-offline-delivery)offline.
