---
title: Distribuzione di un'istanza
seo-title: Distribuzione di un'istanza
description: Distribuzione di un'istanza
seo-description: null
page-status-flag: never-activated
uuid: 5694b07a-6c1c-45a3-8a22-fd9da163c28c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 71fc8bfc-40e0-4592-a540-bd6807ded3a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a2cb740fe9b71435f602b738bd270fd3a0954901

---


# Distribuzione di un&#39;istanza{#deploying-an-instance}

>[!NOTE]
>
>Le configurazioni lato server possono essere eseguite da Adobe solo per le distribuzioni ospitate da Adobe. Per ulteriori informazioni sulle diverse distribuzioni, consultate la sezione Modelli [di](../../installation/using/hosting-models.md) hosting o [questo articolo](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Procedura guidata di distribuzione {#deployment-wizard}

Una procedura guidata grafica, disponibile nella console client di Adobe Campaign, consente di definire i parametri dell&#39;istanza a cui ci si desidera connettere.

Per avviare la procedura guidata di distribuzione, selezionare **Strumenti > Avanzate > Implementazione guidata**.

![](assets/s_ncs_install_deployment_wiz_01.png)

I passaggi di configurazione sono i seguenti:

1. [Parametri generali](#general-parameters)
1. [Parametri canale e-mail](#email-channel-parameters)
1. [Gestione delle e-mail rimbalzate](#managing-bounced-emails)
1. [Monitoraggio della configurazione](#tracking-configuration)
1. [Parametri del canale mobile](#mobile-channel-parameters)
1. [Impostazioni internazionali](#regional-settings)
1. [Accesso da Internet](#access-from-the-internet)
1. [Gestione delle risorse pubbliche](#managing-public-resources)
1. [Rimozione dei dati](#purging-data)

## Parametri generali {#general-parameters}

Il primo passaggio della procedura guidata di distribuzione consente di inserire informazioni generali sull’istanza.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Informazioni generali {#general-information}

La sezione inferiore della finestra consente di selezionare le opzioni da attivare.

* **[!UICONTROL Customer identifier used in billing]** : può essere il nome dell&#39;istanza e il numero di versione.
* **[!UICONTROL Common name of the customer]** : Immettere una stringa di caratteri con il nome della società. Queste informazioni possono essere utilizzate nei collegamenti di annullamento dell&#39;iscrizione.
* **[!UICONTROL Namespace]** : Inserite un identificatore breve in caratteri minuscoli. L&#39;obiettivo è quello di distinguere tra la configurazione specifica e la configurazione di fabbrica in caso di aggiornamento. Lo spazio dei nomi predefinito è **incentrato** - per il cliente.

### Opzioni tecniche {#technical-options}

La sezione inferiore della finestra consente di selezionare le opzioni da attivare.

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Email channel]** : per attivare la consegna tramite e-mail. Fate riferimento ai parametri [del canale](#email-channel-parameters)e-mail.
* **[!UICONTROL Tracking]** : Per abilitare il tracciamento della popolazione di destinazione (aperture e clic). Fare riferimento alla configurazione [](#tracking-configuration)Tracciamento.
* **[!UICONTROL Managing bounced emails]** : Per definire l&#39;account POP utilizzato per recuperare la posta elettronica in arrivo. Fate riferimento a [Gestione delle e-mail](#managing-bounced-emails)rimbalzate.
* **[!UICONTROL LDAP integration]** : Per configurare l’autenticazione utente tramite una directory LDAP. Fate riferimento a [Connessione mediante LDAP](../../installation/using/connecting-through-ldap.md).

## Parametri canale e-mail {#email-channel-parameters}

Il passaggio seguente consente di definire le informazioni da visualizzare nelle intestazioni dei messaggi.

Questi parametri possono essere sovraccaricati nei modelli di consegna e singolarmente per ogni consegna (se gli utenti dispongono dei diritti richiesti).

### Parametri per le e-mail consegnate {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indicate i seguenti parametri:

* **[!UICONTROL Sender name]** : Nome del mittente,
* **[!UICONTROL Sender address]** : L&#39;indirizzo del mittente,
* **[!UICONTROL Reply address text]** : Nome personalizzabile che verrà utilizzato quando il destinatario fa clic sul **[!UICONTROL Reply]** pulsante nel software client di posta elettronica,
* **[!UICONTROL Reply address]** : L&#39;indirizzo e-mail da utilizzare quando il destinatario fa clic sul **[!UICONTROL Reply]** pulsante nel software client di posta elettronica,
* **[!UICONTROL Error address]** : Indirizzo e-mail dei messaggi con errori. Si tratta dell&#39;indirizzo tecnico utilizzato per gestire i messaggi di rimbalzo, compresi i messaggi e-mail ricevuti dal server Adobe Campaign a causa di indirizzi di destinazione inesistenti.

Inoltre, potete specificare le **maschere** autorizzate per l&#39;indirizzo del mittente e l&#39;indirizzo di errore. Se necessario, queste maschere possono essere separate utilizzando una virgola. Questa configurazione è facoltativa. Quando vengono immessi dei campi, Adobe Campaign verifica al momento della consegna (durante l&#39;analisi, se l&#39;indirizzo non include variabili) che gli indirizzi siano validi. Questa modalità operativa assicura che non vengano utilizzati indirizzi che possano causare problemi di consegna. Gli indirizzi di consegna devono essere configurati sul server di consegna.

### Caratteri autorizzati negli indirizzi {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

Nel database di Adobe Campaign, tutti gli indirizzi e-mail devono essere creati come segue: `x@y.z`. I caratteri **x**, **y** e **z** non devono essere vuoti e non devono includere caratteri non autorizzati.

È possibile definire qui i caratteri autorizzati (&#39;criteri dati&#39;) nel campo e-mail del database. I caratteri non inclusi nell&#39;elenco saranno vietati e quindi rifiutati quando si immettono informazioni nel database tramite l&#39;interfaccia, tramite un modulo Web e si importano anche dati.

Sono disponibili due elenchi: **Solo** europea o solo **** USA. Se necessario, è possibile aggiungere altri caratteri.

### Parametri di consegna {#delivery-parameters}

Parametri **avanzati...** collegamento consente di accedere alle opzioni di consegna, ai parametri collegati a tentativi e quarantena.

![](assets/s_ncs_install_deployment_wiz_05.png)

Questa finestra consente di definire, per tutte le campagne e-mail, le opzioni di gestione della qualità dell&#39;indirizzo e della consegna.

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Delivery duration of messages]** : Oltre tale limite, la consegna è interrotta (per impostazione predefinita, 5 giorni),
* **[!UICONTROL Online resources validity duration]** : Tempo di conservazione delle informazioni del profilo destinatario per generare pagine mirror,
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Quando questa opzione è selezionata, i destinatari inseriti nella blacklist non verranno contattati,
* **[!UICONTROL Automatically ignore doubles]** : Quando questa opzione è selezionata, la consegna non verrà effettuata a indirizzi duplicati.

### Parametri del tentativo {#retry-parameters}

Le informazioni sui recuperi sono fornite nei campi **Recupero** e **Numero di recuperi** : quando un destinatario non è raggiungibile, ad esempio se la propria inbox è piena, per impostazione predefinita il programma tenta di contattarli 5 volte, con un intervallo di un&#39;ora tra ogni tentativo (durante il tempo di consegna massimo). Questi valori possono essere modificati in base alle vostre esigenze.

### Parametri di quarantena {#quarantine-parameters}

Le opzioni di configurazione per le quarantena sono le seguenti:

* **[!UICONTROL Duration between two significant errors]** : immettere un valore (&quot;1d&quot; per impostazione predefinita: 1 giorno) per definire l&#39;ora in cui l&#39;applicazione attende prima di incrementare il contatore di errori in caso di errore,
* **[!UICONTROL Maximum number of errors before quarantine]** : una volta raggiunto questo valore, l&#39;indirizzo e-mail viene messo in quarantena (per impostazione predefinita, &quot;5&quot;: l&#39;indirizzo verrà messo in quarantena al sesto errore). Ciò significa che il contatto sarà automaticamente escluso dalle consegne successive.

## Gestione delle e-mail rimbalzate {#managing-bounced-emails}

Bounce mail è estremamente importante per qualificare gli errori di consegna. Questi errori vengono classificati nella NP@I dopo che le regole ne hanno determinato la causa.

Questo passaggio è disponibile solo se nel primo passaggio della procedura guidata di distribuzione sono selezionate le opzioni di gestione della posta **e del canale** e-mail e **** rimbalzo. Fare riferimento ai parametri [](#general-parameters)generali.

Questa fase consente di definire le impostazioni per la gestione dei messaggi di rimbalzo.

![](assets/s_ncs_install_deployment_wiz_06.png)

### Account POP utilizzato per recuperare le e-mail in arrivo {#pop-account-used-to-retrieve-incoming-mails}

Indicate i parametri per la connessione all&#39;account per il recupero delle e-mail in arrivo.

* **[!UICONTROL Label]** : Nome che include tutti i parametri indicati di seguito,
* **[!UICONTROL Server]** : Server utilizzato per recuperare la posta indesiderata (posta in arrivo),
* **[!UICONTROL Security]** : Se necessario, selezionate **[!UICONTROL SSL]** dall&#39;elenco a discesa,
* **[!UICONTROL Port]** : porta del server (generalmente 110),
* **[!UICONTROL Account]** : Nome dell’account utilizzato per la posta indesiderata,
* **[!UICONTROL Password]** : Password associata all&#39;account.

Una volta specificate le impostazioni POP, fate clic su **Test** per verificare che siano corrette.

### Messaggi di rimbalzo non elaborati {#unprocessed-bounce-mails}

Gli avvisi vengono gestiti automaticamente da Adobe Campaign applicando le regole elencate nel nodo **Amministrazione > Gestione campagna > Gestione non risultati finali > Qualifica** del registro di consegna. Per ulteriori informazioni, consultare Gestione [della posta](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)rimbalzata.

I rimbalzi non elaborati non vengono visualizzati nell&#39;interfaccia di Adobe Campaign. Vengono eliminati automaticamente a meno che non vengano trasferiti a una cassetta postale di terze parti utilizzando i seguenti campi:

* **[!UICONTROL Forwarding address]** : Compila questo campo per trasferire a un indirizzo di terze parti tutti i messaggi di errore (elaborati o non elaborati) raccolti dalla piattaforma Adobe Campaign.
* **[!UICONTROL Address for errors]** : Compila questo campo per trasferire a un indirizzo di terze parti solo i messaggi di errore che il processo inMail non è stato in grado di soddisfare le condizioni richieste.
* **[!UICONTROL SMTP server]** : Server utilizzato per inviare le e-mail di rimbalzo non elaborate.

>[!CAUTION]
>
>Per inoltrare e-mail di rimbalzo non elaborate, Adobe consiglia di compilare solo il **[!UICONTROL Address for errors]** campo. Tuttavia, assicurarsi che l&#39;indirizzo utilizzato sia controllato regolarmente, in quanto ciò potrebbe mettere un carico pesante sul server di posta. Per ulteriori informazioni, contattate il vostro responsabile commerciale.

## Monitoraggio della configurazione {#tracking-configuration}

Il passaggio successivo consente di configurare il tracciamento per l’istanza. L’istanza deve essere dichiarata e registrata con i server di tracciamento.

Questo passaggio è disponibile solo quando le opzioni Canale **e-** mail e **Tracciamento** sono selezionate nella prima pagina della procedura guidata di distribuzione. Fare riferimento ai parametri [](#general-parameters)generali.

Per informazioni più dettagliate sul tracciamento Web (modalità di tracciamento, creazione e inserimento di tag...), consultate [questo documento](../../configuration/using/about-web-tracking.md).

### Principio di funzionamento {#operating-principle}

Quando si attiva il tracciamento su un&#39;istanza, gli URL nelle consegne vengono modificati durante l&#39;invio per abilitare il tracciamento.

* Le informazioni sugli URL esterni (protetti o meno) immesse in questa pagina della procedura guidata di distribuzione vengono utilizzate per creare il nuovo URL. Oltre a queste informazioni, il collegamento modificato contiene: gli identificatori della consegna, il destinatario e l’URL.

   Le informazioni di tracciamento vengono raccolte da Adobe Campaign sui server di tracciamento per arricchire i profili dei destinatari e i dati collegati alla consegna ( **[!UICONTROL Tracking]** schede).

   Le informazioni sugli URL interni vengono utilizzate solo dal server dell’applicazione Adobe Campaign per contattare i server di tracciamento.

   Per ulteriori informazioni, vedere [Server](#tracking-server)di tracciamento.

* Una volta configurati gli URL, è necessario abilitare il tracciamento. A questo scopo, l’istanza deve essere registrata sui server di tracciamento.

   Per ulteriori informazioni, consulta [Salvataggio del tracciamento](#saving-tracking).

### Server di tracciamento {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Per garantire l&#39;efficienza del tracciamento su questo caso, devono essere visualizzate le seguenti informazioni:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** e/o **[!UICONTROL Secure external URL]** : Immettete l’URL di reindirizzamento da utilizzare nell’e-mail da inviare.
* **[!UICONTROL Internal URL(s)]** : URL utilizzati solo dal server Adobe Campaign per contattare i server di tracciamento per raccogliere i registri e caricare gli URL. Non è necessario associarlo all&#39;istanza.

   Se non specificate un URL, per impostazione predefinita verrà utilizzato l’URL di tracciamento.

Con l&#39;architettura mid-sourcing, puoi esternalizzare la gestione del tracciamento. Per eseguire questa operazione:

1. Selezionate l’opzione **[!UICONTROL Externalize tracking management]** : questo consente di utilizzare un server di mid-sourcing come server di tracciamento.
1. Compilare i campi **[!UICONTROL External account]** e **[!UICONTROL Instance name]** per collegarsi al server di mid-sourcing.

   Per ulteriori informazioni, fare riferimento al server [](../../installation/using/mid-sourcing-server.md)mid-sourcing.

1. Fare clic sul **[!UICONTROL Enable the tracking instance]** pulsante per approvare la connessione al server.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Salvataggio del tracciamento {#saving-tracking}

Dopo aver popolato gli URL, è necessario registrare il server di tracciamento.

Fai clic sul collegamento **Registrazione sui server di tracciamento** e seleziona una delle opzioni disponibili.

![](assets/s_ncs_install_deployment_wiz_09.png)

Esistono tre possibili tipi di architettura per implementare il tracciamento:

1. **Aggiunta del supporto per il tracciamento in un’istanza esistente**

   Questa scelta si applica se l’istanza è già stata creata per altre esigenze (server MTA, ecc.) sui server che verranno utilizzati come server di monitoraggio.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Per configurare l’istanza di tracciamento, immettete la password per l’account **interno** nei server di reindirizzamento.

   >[!NOTE]
   >
   >Se vengono utilizzati più server di tracciamento, devono utilizzare tutti lo stesso nome e la stessa password.

   Specificate il nome dell&#39;istanza e la password.

1. **Creare una nuova istanza dedicata al tracciamento**

   Questa opzione è utile quando le istanze di tracciamento sono riservate al tracciamento e non dispongono di altri moduli applicativi.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Per configurare l’istanza di tracciamento, immettete la password per l’account **interno** nei server di reindirizzamento.

   >[!NOTE]
   >
   >Se sono configurati più server di tracciamento, questi devono utilizzare la stessa password.

   Specificate il nome dell&#39;istanza, la password e tutte le maschere DNS associate, ad esempio **[!UICONTROL Campaign*]**.

1. **Convalida di un’istanza di tracciamento già preconfigurata**

   Questa opzione viene utilizzata quando non si dispone della password per l&#39;account **interno** ; In questo caso, un account di tracciamento è preconfigurato nei server di tracciamento. Immettere la password dell&#39;account di tracciamento dei server di reindirizzamento per convalidare l&#39;istanza di tracciamento.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Specificate il nome dell’istanza da convalidare.

Fate clic su **Approva** per avviare il processo di registrazione con il server di tracciamento.

Nella finestra precedente, un messaggio conferma la registrazione a livello di server di tracciamento:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

I parametri collegati alle ricerche URL non **devono essere modificati** per un&#39;installazione standard. Per tutti gli altri parametri, contattate Adobe.

## Parametri del canale mobile {#mobile-channel-parameters}

Il passaggio successivo ti consente di definire le impostazioni predefinite per le consegne a dispositivi mobili (SMS e WAP Push).

>[!NOTE]
>
>Il canale mobile è opzionale: questa fase verrà visualizzata solo se è stata acquistata. Controllare il contratto di licenza.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Account predefinito per la consegna SMS {#default-account-for-sms-delivery}

Inserite le seguenti informazioni:

* **[!UICONTROL Label]** : Immettete un nome per questo account push SMS/Wap. Ad esempio, è possibile utilizzare il nome del router.
* Per i **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]** campi: Contattate il fornitore del servizio per conoscere le impostazioni richieste.

### Parametri di SMS inviati {#parameters-of-sms-sent}

Nell&#39;elenco a discesa **Priorità** : Selezionare &quot;Normal&quot;, &quot;High&quot; o &quot;Urgente&quot; per applicarlo ai messaggi da inviare.

### Parametri avanzati {#advanced-parameters}

Parametri **avanzati...** il collegamento consente di accedere alle opzioni relative a tentativi e quarantena.

![](assets/s_ncs_install_deployment_wiz_13.png)

Le informazioni sui tentativi sono disponibili nei campi **Periodo di tentativi** e **Numero di tentativi** : Quando un dispositivo mobile non è raggiungibile, per impostazione predefinita il programma riproverà 5 volte a intervalli di almeno 15 minuti (per il periodo di consegna massimo). Questi valori possono essere adattati alle vostre esigenze.

Le opzioni di configurazione per le quarantena sono le seguenti:

* **[!UICONTROL Time between two significant errors]** : Immettete un valore predefinito (per impostazione predefinita &quot;1d&quot;: day) per definire l&#39;ora in cui l&#39;applicazione attende prima di incrementare il contatore di errori per un errore.
* **[!UICONTROL Maximum number of errors before quarantine]** : Una volta raggiunto questo valore, il numero di cellulare viene messo in quarantena (per impostazione predefinita, &quot;5&quot;: il numero verrà messo in quarantena al sesto errore). Ciò significa che il contatto verrà automaticamente escluso dalle consegne future.

## Impostazioni internazionali {#regional-settings}

Questa fase consente di includere le preferenze per i criteri dei dati.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Quando questa opzione è selezionata, l&#39;applicazione applica il formato internazionale ai numeri di telefono (il prefisso del paese è quindi obbligatorio perché il numero di cifre non sarà controllato prima di applicare la formattazione). Se questa opzione non è selezionata, è necessario preassegnare il numero di telefono internazionale con &quot;+&quot; o &quot;00&quot;.
* **[!UICONTROL Store all phone numbers using the international format]** : Questa opzione riguarda solo i numeri di telefono **domestici** importati o modificati. Specificate se desiderate utilizzare un formato domestico (ad esempio 425 555 0150) o internazionale (ad esempio +1 425 555 0150)

## Accesso da Internet {#access-from-the-internet}

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

Questo passaggio consente di definire gli URL di accesso per le pagine Adobe Campaign esposte su Internet.

È inoltre necessario indicare qui le opzioni di pubblicazione collegate ai moduli Web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Server esposti sul Web {#servers-exposed-on-the-web}

Utilizzare questa pagina per compilare gli URL del server in modo che:

1. Accedere al server applicazioni esposto su Internet: moduli di iscrizione/annullamento dell&#39;iscrizione, Extranet, ecc.
1. Accedete al server applicazione per le risorse non esposte sul Web: moduli, Intranet, pagine di conferma.
1. Consente di accedere alle pagine mirror delle consegne.

   Una pagina mirror è una pagina dinamica che visualizza il contenuto dell&#39;e-mail. È accessibile tramite un collegamento inserito nel messaggio inviato al destinatario e può contenere elementi personalizzati. La pagina mirror dà al destinatario la possibilità di leggere il messaggio in un browser Internet invece del software e-mail, indipendentemente dal formato di consegna (testo o HTML). Tuttavia, le pagine mirror vengono generate per una determinata consegna solo se è stato definito il contenuto HTML richiesto.

Adobe Campaign consente di distinguere questi tre URL per estendere il carico su più piattaforme.

## Gestione delle risorse pubbliche {#managing-public-resources}

>[!CAUTION]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

Per essere visualizzate dall&#39;esterno, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server esterno accessibile. Possono quindi essere disponibili a destinatari o operatori esterni.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Per questo passaggio, dovete immettere:

1. Il nuovo URL della risorsa pubblica. Per ulteriori informazioni, consultate la sezione URL [risorse](#public-resources-url) pubbliche.
1. Modalità di rilevamento delle immagini in una distribuzione. Per ulteriori informazioni, consulta la sezione Rilevamento [immagini](#delivery-image-detection) consegna.
1. Opzioni di pubblicazione. Per ulteriori informazioni, consulta la sezione Modalità [di](#publication-modes) pubblicazione.

Le risorse pubbliche sono accessibili tramite il nodo **Amministrazione > Risorse > Online > Risorse** pubbliche della struttura di Adobe Campaign. Vengono raccolti in una libreria e possono essere inclusi nelle e-mail, ma anche utilizzati in campagne o attività e nella gestione dei contenuti.

![](assets/install_pub_resources_view.png)

### URL risorse pubbliche {#public-resources-url}

Il primo campo consente di specificare l’inizio dell’URL utilizzato per le risorse una volta caricato il file. Quando vengono caricate, le risorse sono accessibili tramite questo nuovo URL.

In una distribuzione, potete utilizzare le immagini memorizzate nella libreria delle risorse pubbliche o in qualsiasi altra immagine o immagine locale memorizzata in un server.

* Per le immagini e-mail, l’URL **https://** server **/res/img** .

   Questo valore può essere ignorato per ogni consegna.

* Per le risorse pubbliche, l’URL **https://** server **/res/** instance ****in cui **instance**è il nome dell’istanza di tracciamento.

### Rilevamento delle immagini di distribuzione {#delivery-image-detection}

In una distribuzione, potete utilizzare le immagini memorizzate nella libreria delle risorse pubbliche o in qualsiasi altra immagine o immagine locale memorizzata in un server.

Le maschere **** URL dei campi consentono di specificare l’elenco di maschere URL da ignorare durante il caricamento automatico delle immagini. Ad esempio, se utilizzate immagini memorizzate in un sito accessibile dall’esterno, in particolare su un sito Internet, potete inserire l’URL del sito in questo campo.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Potete specificare più maschere URL utilizzando una virgola per separarle.

* Per informazioni sull&#39;utilizzo e la gestione delle immagini nelle e-mail, consultare [questa sezione](../../delivery/using/defining-the-email-content.md#adding-images).
* Nella procedura guidata di consegna, le immagini richiamate da questi URL avranno lo stato &quot;Ignorato&quot;.

### Modalità di pubblicazione {#publication-modes}

La sezione inferiore della procedura guidata consente di selezionare le opzioni di pubblicazione delle risorse pubbliche e delle immagini. Queste opzioni sono disponibili anche per i moduli Web e i sondaggi.

Sono disponibili le seguenti modalità di pubblicazione:

* Server di monitoraggio

   Le risorse verranno automaticamente copiate sui diversi server di tracciamento. Sono configurati nella configurazione [step](#tracking-configuration)Tracking.

* Altri server Adobe Campaign

   Puoi utilizzare uno o più altri server Adobe Campaign in cui copieranno le risorse.

   Sul lato server, per utilizzare un server Adobe Campaign dedicato, devi creare una nuova istanza con il seguente comando:

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   Quindi immettete la password.

   I parametri dei server dedicati sono indicati nei **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** e **[!UICONTROL Instance name]** campi.

   ![](assets/s_ncs_install_images_upload_b.png)

* Script di pubblicazione manuale (solo per risorse pubbliche)

   ![](assets/s_ncs_install_images_upload_c.png)

   È possibile pubblicare le immagini utilizzando uno script:

   * È necessario creare questo script: I contenuti dipendono dalla configurazione.
   * Lo script verrà chiamato dal comando seguente:

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      dove `[INSTALL]` è il percorso di accesso alla cartella di installazione di Adobe Campaign.

   * In Unix, verificare che lo script sia eseguibile.

Per le immagini, devono essere copiate dalla cartella &quot;immagini&quot; specificata tramite l&#39;opzione **NmsDelivery_ImageSubDirectory** su uno o più server frontali. Tali server memorizzeranno le immagini per renderle accessibili tramite il nuovo URL configurato.

In caso di pubblicazione su un server Adobe Campaign senza uno script di pubblicazione manuale, per impostazione predefinita le immagini di una distribuzione vengono memorizzate nel `$(XTK_INSTALL_DIR)/var/res/img/ directory`. L’URL corrispondente è il seguente: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. L’URL corrispondente è il seguente: **`https://server/res/instance`** dove instance è il nome dell’istanza di tracciamento.

>[!NOTE]
>
>È possibile modificare la directory di memorizzazione delle risorse pubbliche. Per ulteriori informazioni, vedere [Gestione delle risorse](#managing-public-resources)pubbliche.

### Sincronizzazione delle risorse pubbliche {#synchronizing-public-resources}

Questa funzionalità consente di **sincronizzare le risorse** pubbliche su più server di riserva.

Se una risorsa pubblica non è presente sul server di tracciamento o se la risorsa restituisce un errore 404, il server di tracciamento tenterà di trovare la risorsa su uno dei server di riserva.

La dichiarazione e la configurazione dei server di riserva devono essere eseguite nel file **serverConf.xml** del server di Marketing. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

**Dichiarazione**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configurazione**

Per ogni risorsa pubblica che deve essere sincronizzata, è necessario aggiungere un attributo di stato all&#39; `<url>` elemento nella `<relay>` parte:

L&#39;attributo status può essere uno dei tre valori seguenti:

* di riserva: La risorsa pubblica è sincronizzata

* normal: Comportamento esistente (senza sincronizzazione)

* blacklist: L’URL viene inserito in blacklist se restituisce un errore 404. La durata (in secondi) dell&#39;elenco di blacklist è definita da un attributo di **timeout** il cui valore predefinito è 60 s.

La configurazione out-of-the-box della sincronizzazione è:

```
(extracted from the serverConf.xml file)

<redirection P3PCompactPolicy="CAO DSP COR CURa DEVa TAIa OUR BUS IND UNI COM NAV"
databaseId="" defLogCount="30" expirationURL="" maxJobsInCache="100"
startRedirection="true" startRedirectionInModule="true" trackWebVisitors="false" trackingPassword="">
<spareServer enabledIf="" id="1" url=""/>
</redirection>

....


<relay debugRelay="false" forbiddenCharsInAuthority="?#.@/:" forbiddenCharsInPath="?#/"
           modDir="index.html" startRelay="false" startRelayInModule="true" timeout="60">
   <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/view/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jsp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*.jssp"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/webApp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/report/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="/jssp/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/strings/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/interaction/*"/>
      <url IPMask="" deny="" hostMask="" relayHost="true" relayPath="true" status="normal" targetUrl="https://localhost:8080" timeout="" urlPath="/barcode/*"/>

      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/favicon.*"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.html"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.png"/>
      <url IPMask="" deny="" hostMask="" relayHost="false" relayPath="false" status="spare" targetUrl="" timeout="" urlPath="/*.jpg"/>

 </relay>
```

## Rimozione dei dati {#purging-data}

L’ultima fase della procedura guidata di distribuzione consente di configurare la rimozione automatica dei dati obsoleti. I valori sono espressi in giorni.

![](assets/s_ncs_install_deployment_wiz_16.png)

I dati vengono eliminati automaticamente tramite il flusso di lavoro di pulizia del database. Per ulteriori informazioni su come configurare e utilizzare questo flusso di lavoro e sui dettagli degli elementi eliminati, consulta questo [documento](../../production/using/database-cleanup-workflow.md).
