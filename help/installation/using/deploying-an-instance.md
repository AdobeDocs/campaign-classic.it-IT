---
product: campaign
title: Distribuzione di un’istanza
description: Ulteriori informazioni sulla procedura guidata di distribuzione di Campaign
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 8b07447c-9a86-4b56-8d29-e0b01357a6ec
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '3058'
ht-degree: 1%

---

# Distribuzione di un’istanza{#deploying-an-instance}

>[!NOTE]
>
>Le configurazioni lato server possono essere eseguite solo per Adobe per le distribuzioni ospitate da Adobe. Per ulteriori informazioni sulle diverse distribuzioni, consulta la sezione [Modelli di hosting](../../installation/using/hosting-models.md) o [questa pagina](../../installation/using/capability-matrix.md).

## Procedura guidata di distribuzione {#deployment-wizard}

Una procedura guidata grafica, disponibile nella console client di Adobe Campaign, consente di definire i parametri dell’istanza a cui desideri connetterti.

Per avviare la procedura guidata di distribuzione, selezionare **Strumenti > Avanzate > Procedura guidata di distribuzione**.

![](assets/s_ncs_install_deployment_wiz_01.png)

I passaggi di configurazione sono i seguenti:

1. [Parametri generali](#general-parameters)
1. [Parametri del canale e-mail](#email-channel-parameters)
1. [Gestione delle e-mail rimbalzate](#managing-bounced-emails)
1. [Configurazione del tracciamento](#tracking-configuration)
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

* **[!UICONTROL Customer identifier used in billing]** : può essere il nome dell’istanza e il numero di versione.
* **[!UICONTROL Common name of the customer]** : Immetti una stringa di caratteri con il nome della tua azienda. Queste informazioni possono essere utilizzate nei collegamenti di annullamento dell’abbonamento.
* **[!UICONTROL Namespace]** : Inserisci un identificatore breve in minuscolo. L&#39;obiettivo è quello di distinguere tra la configurazione specifica e la configurazione di fabbrica in caso di aggiornamento. Lo spazio dei nomi predefinito è **cus** - per il cliente.

### Opzioni tecniche {#technical-options}

La sezione inferiore della finestra consente di selezionare le opzioni da attivare.

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Email channel]** : per attivare la consegna e-mail. Fai riferimento a [Parametri del canale e-mail](#email-channel-parameters).
* **[!UICONTROL Tracking]** : Per abilitare il tracciamento della popolazione target (aperture e clic). Fai riferimento a [Configurazione del tracciamento](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : Per definire l&#39;account POP utilizzato per raccogliere la posta elettronica in arrivo. Consulta [Gestione delle e-mail rimbalzate](#managing-bounced-emails).
* **[!UICONTROL LDAP integration]** : Per configurare l&#39;autenticazione utente tramite una directory LDAP. Fare riferimento a [Connessione tramite LDAP](../../installation/using/connecting-through-ldap.md).

## Parametri del canale e-mail {#email-channel-parameters}

Il passaggio seguente ti consente di definire le informazioni da visualizzare nelle intestazioni dei messaggi.

Questi parametri possono essere sovraccaricati nei modelli di consegna e singolarmente per ogni consegna (se gli utenti dispongono dei diritti richiesti).

### Parametri per le e-mail consegnate {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indica i seguenti parametri:

* **[!UICONTROL Sender name]** : Nome del mittente,
* **[!UICONTROL Sender address]** : l&#39;indirizzo del mittente,
* **[!UICONTROL Reply address text]** : Il nome, personalizzabile, che verrà utilizzato quando il destinatario fa clic sul  **[!UICONTROL Reply]** pulsante nel software client di posta elettronica,
* **[!UICONTROL Reply address]** : Indirizzo e-mail da utilizzare quando il destinatario fa clic sul  **[!UICONTROL Reply]** pulsante nel proprio software client di posta elettronica,
* **[!UICONTROL Error address]** : Indirizzo e-mail dei messaggi con errori. Si tratta dell’indirizzo tecnico utilizzato per gestire la posta non recapitata, incluse le e-mail ricevute dal server Adobe Campaign a causa di indirizzi di destinazione inesistenti.

Inoltre, puoi specificare le **maschere** autorizzate per l&#39;indirizzo del mittente e l&#39;indirizzo di errore. Se necessario, queste maschere possono essere separate utilizzando virgole. Questa configurazione è facoltativa. Quando i campi vengono immessi, Adobe Campaign verifica al momento della consegna (durante l’analisi, se l’indirizzo non include variabili) che gli indirizzi siano validi. Questa modalità operativa assicura che non vengano utilizzati indirizzi che possano causare problemi di consegna. Gli indirizzi di consegna devono essere configurati sul server di consegna.

### Caratteri autorizzati negli indirizzi {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

Nel database Adobe Campaign, tutti gli indirizzi e-mail devono essere creati come segue: `x@y.z`. I caratteri **x**, **y** e **z** non devono essere vuoti e non devono includere caratteri non autorizzati.

È possibile definire qui i caratteri autorizzati (&quot;policy di dati&quot;) nel campo e-mail del database. I caratteri non inclusi nell’elenco saranno vietati e pertanto rifiutati quando si immettono informazioni nel database tramite l’interfaccia, tramite un modulo web e si importano anche dati.

Sono disponibili due elenchi: **Solo europeo** o **Solo Stati Uniti**. Se necessario, è possibile aggiungere altri caratteri.

### Parametri di consegna {#delivery-parameters}

Parametri **avanzati...Il collegamento** ti consente di accedere alle opzioni di consegna, ai parametri collegati a tentativi e quarantena.

![](assets/s_ncs_install_deployment_wiz_05.png)

Questa finestra ti consente di definire, per tutte le campagne e-mail, le opzioni di gestione della qualità della consegna e dell’indirizzo.

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Delivery duration of messages]** : Oltre questo periodo di tempo, la consegna viene interrotta (per impostazione predefinita, 5 giorni),
* **[!UICONTROL Online resources validity duration]** : tempo di conservazione delle informazioni del profilo destinatario al fine di generare pagine mirror,
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : Quando questa opzione è selezionata, elenco Bloccati i destinatari non verranno contattati,
* **[!UICONTROL Automatically ignore doubles]** : Quando questa opzione è selezionata, la consegna non viene eseguita su indirizzi duplicati.

### Parametri del tentativo {#retry-parameters}

Le informazioni sui recuperi sono fornite nei campi **Periodi di recupero** e **Numero di recuperi**: quando un destinatario non è raggiungibile, ad esempio se la casella in entrata è piena, per impostazione predefinita il programma tenta di contattarli 5 volte, con un intervallo di un&#39;ora tra ogni tentativo (durante il tempo massimo di consegna). Questi valori possono essere modificati in base alle tue esigenze.

### Parametri di quarantena {#quarantine-parameters}

Le opzioni di configurazione per le quarantena sono le seguenti:

* **[!UICONTROL Duration between two significant errors]** : inserisci un valore (&quot;1d&quot; per impostazione predefinita: 1 giorno) per definire il tempo che l&#39;applicazione attende prima di incrementare il contatore degli errori in caso di errore,
* **[!UICONTROL Maximum number of errors before quarantine]** : una volta raggiunto questo valore, l’indirizzo e-mail viene messo in quarantena (per impostazione predefinita &quot;5&quot;: l’indirizzo sarà messo in quarantena al sesto errore). Ciò significa che il contatto sarà automaticamente escluso dalle consegne successive.

## Gestione delle e-mail rimbalzate {#managing-bounced-emails}

La posta non recapitata è estremamente importante per qualificare gli errori di consegna. Questi errori vengono classificati in NP@I una volta che le regole hanno determinato la loro causa.

Questo passaggio è disponibile solo se le opzioni di gestione **Canale e-mail** e **Posta non arrivate a destinazione** sono selezionate nel primo passaggio della procedura guidata di distribuzione. Fare riferimento a [Parametri generali](#general-parameters).

Questa fase ti consente di definire le impostazioni per la gestione delle mail non recapitate.

![](assets/s_ncs_install_deployment_wiz_06.png)

### Account POP utilizzato per recuperare le e-mail in arrivo {#pop-account-used-to-retrieve-incoming-mails}

Indica i parametri per la connessione all’account per il recupero delle e-mail in arrivo.

* **[!UICONTROL Label]** : Nome che include tutti i parametri indicati di seguito,
* **[!UICONTROL Server]** : Server utilizzato per recuperare la posta non recapitata (posta in arrivo),
* **[!UICONTROL Security]** : Se necessario, seleziona  **[!UICONTROL SSL]** dall’elenco a discesa,
* **[!UICONTROL Port]** : porta server (generalmente 110),
* **[!UICONTROL Account]** : Nome dell&#39;account utilizzato per la posta non recapitata,
* **[!UICONTROL Password]** : Password associata all&#39;account.

Una volta specificate le impostazioni POP, fare clic su **Test** per assicurarsi che siano corrette.

### Mail non recapitate non elaborate {#unprocessed-bounce-mails}

I rimbalzi vengono gestiti automaticamente da Adobe Campaign, applicando le regole elencate nel nodo **Amministrazione > Gestione campagna > Gestione non consegnabili > Qualificazione del registro di consegna** . Per ulteriori informazioni, consulta [Gestione della posta non recapitata](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

I messaggi non recapitati non elaborati non vengono visualizzati nell’interfaccia di Adobe Campaign. Vengono eliminati automaticamente a meno che non vengano trasferiti a una cassetta postale di terze parti utilizzando i campi seguenti:

* **[!UICONTROL Forwarding address]** : Compila questo campo per trasferire a un indirizzo di terze parti tutti i messaggi di errore (elaborati o non elaborati ) raccolti dalla piattaforma Adobe Campaign.
* **[!UICONTROL Address for errors]** : Compila questo campo per trasferire a un indirizzo di terze parti solo i messaggi di errore che il processo inMail non è stato in grado di qualificare.
* **[!UICONTROL SMTP server]** : Server utilizzato per inviare le e-mail non recapitate non elaborate.

>[!IMPORTANT]
>
>Per inoltrare le e-mail non recapitate non elaborate, l’Adobe consiglia di compilare solo il campo **[!UICONTROL Address for errors]** . Tuttavia, assicurati che l&#39;indirizzo utilizzato sia controllato regolarmente, in quanto ciò potrebbe comportare un carico pesante sul server di posta. Per ulteriori informazioni, contatta il tuo account executive.

## Tracking della configurazione {#tracking-configuration}

Il passaggio successivo ti consente di configurare il tracciamento per l’istanza. L&#39;istanza deve essere dichiarata e registrata con i server di tracciamento.

Questo passaggio è disponibile solo quando le opzioni **Canale e-mail** e **Tracciamento** sono selezionate nella prima pagina della procedura guidata di distribuzione. Fare riferimento a [Parametri generali](#general-parameters).

Per informazioni più dettagliate sul web tracking (modalità di tracciamento, creazione e inserimento di tag...), consulta [questo documento](../../configuration/using/about-web-tracking.md).

### Principio di funzionamento {#operating-principle}

Quando attivi il tracciamento su un’istanza, gli URL nelle consegne vengono modificati durante l’invio per abilitare il tracciamento.

* Per generare il nuovo URL vengono utilizzate le informazioni sugli URL esterni (protetti o meno) immessi in questa pagina della procedura guidata di distribuzione. Oltre a queste informazioni, il collegamento modificato contiene: gli identificatori della consegna, del destinatario e dell’URL.

   Le informazioni di tracciamento vengono raccolte da Adobe Campaign sui server di tracciamento per arricchire i profili dei destinatari e i dati collegati alle schede di consegna ( **[!UICONTROL Tracking]** ).

   Le informazioni sugli URL interni vengono utilizzate solo dal server dell’applicazione Adobe Campaign per contattare il server o i server di tracciamento.

   Per ulteriori informazioni, consulta [Server di tracciamento](#tracking-server).

* Una volta configurati gli URL, devi abilitare il tracciamento. A questo scopo, l’istanza deve essere registrata sui server di tracciamento.

   Per ulteriori informazioni, consulta [Salvataggio del tracciamento](#saving-tracking).

### Server di tracciamento {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Per garantire l’efficienza del tracciamento su questa istanza, devono essere visualizzate le seguenti informazioni:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** e/o  **[!UICONTROL Secure external URL]** : Immetti l’URL di reindirizzamento da utilizzare nell’e-mail da inviare.
* **[!UICONTROL Internal URL(s)]** : URL utilizzati solo dal server Adobe Campaign per contattare i server di tracciamento per raccogliere i registri e caricare gli URL. Non è necessario associarlo all&#39;istanza.

   Se non specifichi un URL, l’URL di tracciamento verrà utilizzato per impostazione predefinita.

Con l&#39;architettura di mid-sourcing puoi esternalizzare la gestione del tracking. Per eseguire questa operazione:

1. Seleziona l’opzione **[!UICONTROL Externalize tracking management]** : questo consente di utilizzare un server di mid-sourcing come server di tracciamento.
1. Compilare i campi **[!UICONTROL External account]** e **[!UICONTROL Instance name]** per connettersi al server di mid-sourcing.

   Per ulteriori informazioni, consulta [Server di mid-sourcing](../../installation/using/mid-sourcing-server.md).

1. Fai clic sul pulsante **[!UICONTROL Enable the tracking instance]** per approvare la connessione al server.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Salvataggio del tracciamento {#saving-tracking}

Una volta compilati gli URL, devi registrare il server di tracciamento.

Fai clic sul collegamento **Registrazione sui server di tracciamento** e seleziona una delle opzioni disponibili.

![](assets/s_ncs_install_deployment_wiz_09.png)

Esistono tre possibili tipi di architettura per implementare il tracciamento:

1. **Aggiungi il supporto per il tracciamento in un&#39;istanza esistente**

   Questa scelta si applica se l’istanza è già stata creata per altre esigenze (server MTA, ecc.) su server che verranno utilizzati come server di tracciamento.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Immetti la password per l&#39;account **interno** sui server di reindirizzamento per configurare l&#39;istanza di tracciamento.

   >[!NOTE]
   >
   >Se vengono utilizzati più server di tracciamento, questi devono utilizzare tutti lo stesso nome e la stessa password.

   Specifica il nome dell&#39;istanza e la password.

1. **Crea una nuova istanza dedicata al tracciamento**

   Questa opzione è utile quando le istanze di tracciamento sono riservate al tracciamento e non hanno altri moduli di applicazione.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Immetti la password per l&#39;account **interno** sui server di reindirizzamento per configurare l&#39;istanza di tracciamento.

   >[!NOTE]
   >
   >Se sono configurati più server di tracciamento, devono tutti utilizzare la stessa password.

   Specifica il nome dell&#39;istanza, la password e le eventuali maschere DNS associate, ad esempio **[!UICONTROL Campaign*]**.

1. **Convalida un’istanza di tracciamento già preconfigurata**

   Questa opzione viene utilizzata quando non si dispone della password per l&#39;account **interno**; In questo caso, un account di tracciamento è preconfigurato per te sui server di tracciamento. Immetti la password dell&#39;account di tracciamento dei server di reindirizzamento per convalidare l&#39;istanza di tracciamento.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Specifica il nome dell’istanza da convalidare.

Fai clic su **Approva** per avviare il processo di registrazione con il server di tracciamento.

Nella finestra precedente, un messaggio conferma la registrazione a livello di server di tracciamento:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

I parametri collegati alle ricerche URL **non devono essere modificati** per un&#39;installazione standard. Per tutti gli altri parametri, contattare l&#39;Adobe.

## Parametri del canale mobile {#mobile-channel-parameters}

Il passaggio successivo ti consente di definire le impostazioni predefinite per le consegne su dispositivi mobili (SMS e push WAP).

>[!NOTE]
>
>Il canale mobile è facoltativo: questa fase verrà visualizzata solo se è stata acquistata. Controlla il contratto di licenza.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Account predefinito per la consegna SMS {#default-account-for-sms-delivery}

Immetti le seguenti informazioni:

* **[!UICONTROL Label]** : Immetti un nome per questo account push SMS/Wap. Ad esempio, è possibile utilizzare il nome del router.
* Per i campi **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]**: Contattare il provider di servizi per le impostazioni richieste.

### Parametri dell’SMS inviato {#parameters-of-sms-sent}

Nell&#39;elenco a discesa **Priorità** : Seleziona &quot;Normale&quot;, &quot;Alto&quot; o &quot;Urgente&quot; per applicarlo ai messaggi da inviare.

### Parametri avanzati {#advanced-parameters}

Parametri **avanzati...Il collegamento** consente di accedere alle opzioni di esecuzione di un nuovo tentativo e quarantena.

![](assets/s_ncs_install_deployment_wiz_13.png)

Le informazioni sui nuovi tentativi sono disponibili nei campi **Periodo di tentativi** e **Numero di tentativi** : Quando un dispositivo mobile non è raggiungibile, per impostazione predefinita, il programma riproverà 5 volte a intervalli di almeno 15 minuti (per il periodo di consegna massimo). Questi valori possono essere adattati alle tue esigenze.

Le opzioni di configurazione per le quarantena sono le seguenti:

* **[!UICONTROL Time between two significant errors]** : Immetti un valore predefinito (per impostazione predefinita &quot;1d&quot;: day) per definire l&#39;ora in cui l&#39;applicazione attende prima di incrementare il contatore degli errori per un errore.
* **[!UICONTROL Maximum number of errors before quarantine]** : Una volta raggiunto questo valore, il numero mobile viene messo in quarantena (per impostazione predefinita &quot;5&quot;: il numero sarà messo in quarantena al sesto errore). Ciò significa che il contatto verrà automaticamente escluso dalle consegne future.

## Impostazioni internazionali {#regional-settings}

Questa fase consente di includere le preferenze dei criteri per i dati.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : Quando questa opzione è selezionata, l&#39;applicazione applica il formato internazionale ai numeri di telefono (il prefisso del paese è quindi obbligatorio perché il numero di cifre non sarà controllato prima di applicare la formattazione). Se questa opzione non è selezionata, è necessario preimpostare personalmente il numero di telefono internazionale con &quot;+&quot; o &quot;00&quot;.
* **[!UICONTROL Store all phone numbers using the international format]** : Questa opzione riguarda solo i numeri di telefono  **** domestici importati o modificati. Definire se si desidera utilizzare un formato nazionale (ad esempio 425 555 0150) o il formato internazionale (ad esempio +1 425 555 0150)

## Accesso da Internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

Questo passaggio ti consente di definire gli URL di accesso per le pagine Adobe Campaign esposte su Internet.

È inoltre necessario indicare qui le opzioni di pubblicazione collegate ai moduli web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Server esposti sul Web {#servers-exposed-on-the-web}

Utilizza questa pagina per compilare gli URL del server in modo che:

1. Accedi al server applicazioni esposto su Internet: moduli di abbonamento/annullamento dell’abbonamento, extranet, ecc.
1. Accedi al server applicazioni per le risorse non esposte sul Web: moduli, Intranet, pagine di conferma.
1. Accedi alle pagine mirror delle consegne.

   Una pagina speculare è una pagina dinamica che visualizza il contenuto dell’e-mail. È accessibile tramite un collegamento inserito nel messaggio inviato al destinatario e può contenere elementi personalizzati. La pagina speculare dà al destinatario la possibilità di leggere il messaggio in un browser Internet invece che nel software di posta elettronica, indipendentemente dal formato di consegna (testo o HTML). Tuttavia, le pagine mirror vengono generate solo per una determinata consegna se è stato definito il contenuto HTML richiesto.

Adobe Campaign consente di differenziare questi tre URL per distribuire il carico su più piattaforme.

## Gestione delle risorse pubbliche {#managing-public-resources}

>[!IMPORTANT]
>
>Per motivi di privacy, si consiglia di utilizzare HTTPS per tutte le risorse esterne.

Per essere visualizzate dall’esterno, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server accessibile esternamente. Possono quindi essere disponibili per i destinatari o gli operatori esterni.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Per questo passaggio, devi immettere:

1. Il nuovo URL della risorsa pubblica. Per ulteriori informazioni consulta la sezione [URL risorse pubbliche](#public-resources-url) .
1. Modalità di rilevamento delle immagini in una consegna. Per ulteriori informazioni, consulta la sezione [Rilevamento immagini di consegna](#delivery-image-detection) .
1. Opzioni di pubblicazione. Per ulteriori informazioni, consulta la sezione [Modalità di pubblicazione](#publication-modes) .

Le risorse pubbliche sono accessibili tramite il nodo **Amministrazione > Risorse > Online > Risorse pubbliche** della struttura di Adobe Campaign. Vengono raccolte in una libreria e possono essere incluse nelle e-mail, ma anche utilizzate in campagne o attività e nella gestione dei contenuti.

![](assets/install_pub_resources_view.png)

### URL risorse pubbliche {#public-resources-url}

Il primo campo consente di specificare l’inizio dell’URL utilizzato per le risorse una volta effettuato il caricamento. Al momento del caricamento, le risorse sono accessibili tramite questo nuovo URL.

In una consegna, puoi utilizzare le immagini memorizzate nella libreria delle risorse pubbliche o in qualsiasi altra immagine o immagine locale memorizzata su un server.

* Per le immagini di posta elettronica, l&#39;URL **https://** server **/res/img**.

   Questo valore può essere ignorato per ogni consegna.

* Per le risorse pubbliche, l&#39;URL **https://** server **/res/** instance ****dove **instance**è il nome dell&#39;istanza di tracciamento.

### Rilevamento delle immagini di consegna {#delivery-image-detection}

In una consegna, puoi utilizzare le immagini memorizzate nella libreria delle risorse pubbliche o in qualsiasi altra immagine o immagine locale memorizzata su un server.

Il campo **Maschere URL** consente di specificare l’elenco di maschere URL da ignorare durante il caricamento automatico delle immagini. Ad esempio, se utilizzi immagini memorizzate in un sito accessibile dall’esterno, in particolare su un sito Internet, puoi immettere l’URL del sito in questo campo.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Potete specificare più maschere URL utilizzando una virgola per separarle.

* Per informazioni sull&#39;utilizzo e la gestione delle immagini nelle e-mail, consulta [questa sezione](../../delivery/using/defining-the-email-content.md#adding-images).
* Nella procedura guidata di consegna, le immagini richiamate da questi URL avranno lo stato &quot;Ignorato&quot;.

### Modalità di pubblicazione {#publication-modes}

La sezione inferiore della procedura guidata consente di selezionare le opzioni di pubblicazione delle risorse pubbliche e delle immagini. Queste opzioni sono disponibili anche per i moduli web e i sondaggi.

Sono disponibili le seguenti modalità di pubblicazione:

* Server/i di tracciamento

   Le risorse verranno copiate automaticamente nei diversi server di tracciamento. Sono configurati nel passaggio [Configurazione di tracciamento](#tracking-configuration).

* Altri server Adobe Campaign

   Puoi utilizzare un altro server Adobe Campaign in cui copiare le risorse.

   Sul lato server, per utilizzare un server Adobe Campaign dedicato, è necessario creare una nuova istanza con il seguente comando:

   ```
   nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
   ```

   Quindi inserisci la password.

   I parametri dei server dedicati sono indicati nei campi **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** e **[!UICONTROL Instance name]** .

   ![](assets/s_ncs_install_images_upload_b.png)

* Script di pubblicazione manuale (solo per risorse pubbliche)

   ![](assets/s_ncs_install_images_upload_c.png)

   È possibile pubblicare le immagini utilizzando uno script:

   * È necessario creare questo script: Il suo contenuto dipende dalla configurazione.
   * Lo script verrà chiamato dal seguente comando:

      ```
      [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
      ```

      dove `[INSTALL]` è il percorso di accesso alla cartella di installazione di Adobe Campaign.

   * In Unix, assicurati che lo script sia eseguibile.

Per le immagini, deve copiarle dalla cartella &quot;immagini&quot; specificata tramite l&#39;opzione **NmsDelivery_ImageSubDirectory** su uno o più server frontali. Questi server memorizzeranno le immagini per renderle accessibili tramite il nuovo URL configurato.

In caso di pubblicazione su un server Adobe Campaign senza uno script di pubblicazione manuale, per impostazione predefinita le immagini di una consegna sono memorizzate in `$(XTK_INSTALL_DIR)/var/res/img/ directory`. L’URL corrispondente è il seguente: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. L’URL corrispondente è il seguente: **`https://server/res/instance`** dove instance è il nome dell&#39;istanza di tracciamento.

>[!NOTE]
>
>È possibile modificare la directory di archiviazione delle risorse pubbliche. Per ulteriori informazioni, consulta [Gestione delle risorse pubbliche](#managing-public-resources).

### Sincronizzazione delle risorse pubbliche {#synchronizing-public-resources}

Questa funzionalità ti consente di **sincronizzare le risorse pubbliche** su più server di riserva.

Se una risorsa pubblica non è presente sul server di tracciamento o se la risorsa restituisce un errore 404, il server di tracciamento cercherà di trovare la risorsa su uno dei server di riserva.

La dichiarazione e la configurazione dei server di riserva devono essere eseguite nel file **serverConf.xml** del server di marketing. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

**Dichiarazione**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configurazione**

Per ogni risorsa pubblica che deve essere sincronizzata, devi aggiungere un attributo di stato all&#39;elemento `<url>` nella parte `<relay>`:

L&#39;attributo di stato può essere uno dei tre valori seguenti:

* di ricambio: La risorsa pubblica è sincronizzata

* normale: Comportamento esistente (senza sincronizzazione)

* lista nera: L’URL viene aggiunto al elenco Bloccati se restituisce un errore 404. La durata (in secondi) dell&#39;URL in fase di elenco Bloccati è definita da un attributo **timeout** il cui valore predefinito è 60 s.

La configurazione predefinita della sincronizzazione è:

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

L’ultima fase della procedura guidata di distribuzione consente di configurare l’eliminazione automatica dei dati obsoleti. I valori sono espressi in giorni.

![](assets/s_ncs_install_deployment_wiz_16.png)

I dati vengono eliminati automaticamente tramite il flusso di lavoro Database cleanup . Per ulteriori informazioni su come configurare e utilizzare questo flusso di lavoro e sui dettagli sugli elementi eliminati, consulta questo [documento](../../production/using/database-cleanup-workflow.md).
