---
product: campaign
title: Distribuzione di un’istanza
description: Ulteriori informazioni sulla procedura guidata di implementazione di Campaign
feature: Installation, Instance Settings, Deployment
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 8b07447c-9a86-4b56-8d29-e0b01357a6ec
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '3388'
ht-degree: 1%

---

# Distribuzione di un’istanza{#deploying-an-instance}

>[!NOTE]
>
>Le configurazioni lato server possono essere eseguite solo da Adobe per le distribuzioni in hosting da Adobe. Per ulteriori informazioni sulle diverse implementazioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o a [questa pagina](../../installation/using/capability-matrix.md).

## Distribuzione guidata {#deployment-wizard}

Adobe Campaign fornisce un assistente grafico, disponibile nella console client di Adobe Campaign, per definire i parametri dell’istanza a cui stai per connetterti.

Per avviare la procedura guidata di distribuzione, selezionare **Strumenti > Avanzate > Procedura guidata di distribuzione**.

![](assets/s_ncs_install_deployment_wiz_01.png)

I passaggi di configurazione sono i seguenti:

1. [Parametri generali](#general-parameters)
1. [Parametri del canale e-mail](#email-channel-parameters)
1. [Gestione delle e-mail non recapitate](#managing-bounced-emails)
1. [Configurazione del tracciamento](#tracking-configuration)
1. [Parametri del canale mobile](#mobile-channel-parameters)
1. [Impostazioni regionali](#regional-settings)
1. [Accesso da Internet](#access-from-the-internet)
1. [Gestione delle risorse pubbliche](#managing-public-resources)
1. [Eliminazione dei dati](#purging-data)

## Parametri generali {#general-parameters}

Il primo passaggio della procedura guidata di distribuzione consente di immettere informazioni generali sull’istanza.

![](assets/s_ncs_install_deployment_wiz_02.png)

### Informazioni generali {#general-information}

La sezione inferiore della finestra consente di selezionare le opzioni da attivare.

* **[!UICONTROL Customer identifier used in billing]** : può essere il nome dell’istanza e il numero di versione.
* **[!UICONTROL Common name of the customer]** : immetti una stringa di caratteri con il nome dell’azienda. Queste informazioni possono essere utilizzate nei collegamenti di annullamento dell’abbonamento.
* **[!UICONTROL Namespace]** : inserisci un identificatore breve in minuscolo. Lo scopo è distinguere tra la configurazione specifica e la configurazione di fabbrica in caso di aggiornamento. Lo spazio dei nomi predefinito è **cus** - per il cliente.

### Opzioni tecniche {#technical-options}

La sezione inferiore della finestra consente di selezionare le opzioni da attivare.

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Email channel]** : per attivare la consegna e-mail. Fai riferimento a [Parametri del canale e-mail](#email-channel-parameters).
* **[!UICONTROL Tracking]** : per abilitare il tracciamento della popolazione target (aperture e clic). Fai riferimento a [Configurazione del tracciamento](#tracking-configuration).
* **[!UICONTROL Managing bounced emails]** : per definire l’account POP utilizzato per raccogliere le e-mail in arrivo. Fai riferimento a [Gestione delle e-mail non recapitate](#managing-bounced-emails).
* **[!UICONTROL LDAP integration]** : per configurare l’autenticazione utente tramite una directory LDAP. Fai riferimento a [Connessione tramite LDAP](../../installation/using/connecting-through-ldap.md).

## Parametri del canale e-mail {#email-channel-parameters}

Il passaggio seguente ti consente di definire le informazioni da visualizzare nelle intestazioni dei messaggi.

Questi parametri possono essere sovraccaricati nei modelli di consegna e singolarmente per ogni consegna (se gli utenti dispongono dei diritti richiesti).

### Parametri per e-mail consegnate {#parameters-for-delivered-emails}

![](assets/s_ncs_install_deployment_wiz_04.png)

Indicare i seguenti parametri:

* **[!UICONTROL Sender name]** : immetti il nome del mittente.
* **[!UICONTROL Sender address]** : immetti l’indirizzo e-mail del mittente. Quando si inviano e-mail da Adobe Campaign, il **Indirizzo mittente** la cassetta postale non è monitorata e gli utenti marketing non possono accedere a questa cassetta postale. Inoltre, Adobe Campaign non offre la possibilità di rispondere automaticamente o inoltrare automaticamente le e-mail ricevute in questa casella di posta. Ulteriori informazioni sulle best practice per la consegna dei messaggi [in questa documentazione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/ac-starting-new-platform.html){_blank}.

* **[!UICONTROL Reply address text]** : immetti il nome utilizzato quando il destinatario fa clic su **[!UICONTROL Reply]** pulsante.
* **[!UICONTROL Reply address]** : immetti l’indirizzo e-mail da utilizzare quando il destinatario fa clic su **[!UICONTROL Reply]** nel software client di posta elettronica. Scopo della **Indirizzo di risposta** è il momento in cui desideri che il destinatario risponda a un indirizzo diverso da **Indirizzo mittente**.  Questo indirizzo deve essere un indirizzo e-mail valido, collegato a una cassetta postale monitorata e ospitato dal cliente.  Potrebbe trattarsi di una casella di posta di supporto, ad esempio, `customer-care@customer.com`: in cui le e-mail vengono lette e a cui viene data risposta.

* **[!UICONTROL Error address]** : immetti l’indirizzo e-mail dei messaggi con errori. Si tratta dell’indirizzo tecnico utilizzato per gestire le e-mail non recapitate, incluse quelle ricevute dal server Adobe Campaign a causa di indirizzi di destinazione inesistenti. Questo indirizzo deve essere un indirizzo e-mail valido, collegato a una cassetta postale monitorata e ospitato dal cliente. Potrebbe trattarsi di una cassetta postale di mancato recapito, ad esempio: `errors@customer.com`. Questo indirizzo può essere modificato per una consegna o nei modelli di consegna, dal **SMTP** scheda delle proprietà del modello di consegna/consegna. [Ulteriori informazioni](../../delivery/using/email-parameters.md#managing-bounce-emails-managing-bounce-emails).


Inoltre, puoi specificare **maschere** autorizzato per l’indirizzo del mittente e l’indirizzo di errore. Se necessario, queste maschere possono essere separate da virgole. Questa configurazione è facoltativa. Quando vengono immessi i campi, Adobe Campaign controlla al momento della consegna (durante l’analisi, se l’indirizzo non include alcuna variabile) che gli indirizzi siano validi. Questa modalità operativa assicura che non vengano utilizzati indirizzi che potrebbero attivare problemi di consegna. Gli indirizzi di consegna devono essere configurati sul server di consegna.

>[!NOTE]
>
>* Queste impostazioni vengono salvate nelle opzioni della piattaforma Campaign. [Ulteriori informazioni](../../installation/using/configuring-campaign-options.md).
> 
>* Per le configurazioni con più marchi, puoi adattare l’indirizzo Error e ignorare questa configurazione dall’account esterno di indirizzamento e-mail. [Ulteriori informazioni](../../installation/using/external-accounts.md#email-routing-external-account).
>


### Caratteri autorizzati negli indirizzi {#characters-authorized-in-addresses}

<!--This window enables you to define, for all email campaigns, the delivery and address-quality management options.-->

Nel database di Adobe Campaign, tutti gli indirizzi e-mail devono essere creati come segue: `x@y.z`. Il **x**, **y** e **z** i caratteri non possono essere vuoti e non possono includere caratteri non autorizzati.

Qui puoi definire i caratteri autorizzati (&#39;criteri dati&#39;) nel campo e-mail del database. I caratteri non inclusi nell&#39;elenco saranno vietati e pertanto rifiutati quando si immettono informazioni nel database tramite l&#39;interfaccia, tramite un modulo Web e si importano dati.

Sono disponibili due elenchi: **Solo europeo** o **Solo Stati Uniti**. Se necessario, è possibile aggiungere altri caratteri.

### Parametri di consegna {#delivery-parameters}

Il **Parametri avanzati...** Il collegamento ti consente di accedere alle opzioni di consegna, ai parametri collegati ai nuovi tentativi e alle quarantene.

![](assets/s_ncs_install_deployment_wiz_05.png)

Questa finestra ti consente di definire, per tutte le campagne e-mail, le opzioni di gestione per la consegna e la qualità degli indirizzi.

Sono disponibili le seguenti opzioni:

* **[!UICONTROL Delivery duration of messages]** : oltre questo limite di tempo, la consegna viene interrotta (per impostazione predefinita, 5 giorni).
* **[!UICONTROL Online resources validity duration]** : momento in cui vengono conservate le informazioni provenienti dal profilo del destinatario per generare pagine mirror.
* **[!UICONTROL Exclude recipients who no longer wish to be contacted]** : quando questa opzione è selezionata, al momento della inserisce nell&#39;elenco Bloccati i destinatari non verranno contattati.
* **[!UICONTROL Automatically ignore doubles]** : quando questa opzione è selezionata, la consegna non viene effettuata su indirizzi duplicati.

>[!NOTE]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), il **[!UICONTROL Delivery duration of the messages]** verrà utilizzato solo se impostato su **3,5 giorni o meno**. Se definisci un valore superiore a 3,5 giorni, questo non verrà preso in considerazione.

### Parametri per riprovare {#retry-parameters}

Le informazioni sui recuperi sono fornite nella **Periodi di recupero** e **Numero di recuperi** campi: quando un destinatario non è raggiungibile, ad esempio se la casella in entrata è piena, per impostazione predefinita il programma tenterà di contattarlo 5 volte, con un intervallo di un’ora tra ogni tentativo (durante il tempo di consegna massimo). Questi valori possono essere modificati in base alle tue esigenze.

>[!NOTE]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), i parametri per i nuovi tentativi di Campaign non vengono più utilizzati. I nuovi tentativi di mancato recapito non permanenti e il periodo di tempo che intercorre tra di essi sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte di mancato recapito provenienti dal dominio e-mail del messaggio.

### Parametri di quarantena {#quarantine-parameters}

Le opzioni di configurazione per le quarantene sono le seguenti:

* **[!UICONTROL Duration between two significant errors]** : inserisci un valore (&quot;1d&quot; per impostazione predefinita: 1 giorno) per definire il tempo che l’applicazione attende prima di incrementare il contatore degli errori in caso di errore,
* **[!UICONTROL Maximum number of errors before quarantine]** : una volta raggiunto questo valore, l’indirizzo e-mail viene messo in quarantena (per impostazione predefinita &quot;5&quot;: l’indirizzo verrà messo in quarantena al sesto errore). Ciò significa che il contatto sarà automaticamente escluso dalle consegne successive.

## Gestione delle e-mail non recapitate {#managing-bounced-emails}

La posta non recapitata è estremamente importante per qualificare gli errori di consegna. Questi errori vengono categorizzati in NP@I una volta che le regole ne hanno determinato la causa.

Questo passaggio è disponibile solo se **Canale e-mail** e **E-mail non recapitate** le opzioni di gestione vengono selezionate nella prima fase della procedura guidata di distribuzione. Fai riferimento a [Parametri generali](#general-parameters).

Questa fase ti consente di definire le impostazioni per la gestione dei messaggi non recapitati.

![](assets/s_ncs_install_deployment_wiz_06.png)

### Account POP utilizzato per recuperare le e-mail in arrivo {#pop-account-used-to-retrieve-incoming-mails}

Indica i parametri per la connessione all’account per il recupero delle e-mail in arrivo.

* **[!UICONTROL Label]** : nome che include tutti i parametri indicati di seguito,
* **[!UICONTROL Server]** : server utilizzato per recuperare la posta non recapitata (posta in arrivo),
* **[!UICONTROL Security]** : se necessario, seleziona **[!UICONTROL SSL]** dall’elenco a discesa,
* **[!UICONTROL Port]** : porta del server (generalmente 110),
* **[!UICONTROL Account]** : nome dell’account utilizzato per la posta non recapitata,
* **[!UICONTROL Password]** : password associata all’account.

Una volta specificate le impostazioni POP, fare clic su **Test** per verificare che siano corretti.

### E-mail non recapitate non elaborate {#unprocessed-bounce-mails}

I mancati recapiti vengono gestiti automaticamente da Adobe Campaign, applicando le regole elencate nella **Administration > Campaign Management > Non deliverables Management > Qualificazione del registro di consegna** nodo. Per ulteriori informazioni, consulta [Gestione posta non recapitata](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management).

I mancati recapiti non elaborati non vengono visualizzati nell’interfaccia di Adobe Campaign. Vengono eliminati automaticamente a meno che non vengano trasferiti a una cassetta postale di terze parti utilizzando i campi seguenti:

* **[!UICONTROL Forwarding address]** : compila questo campo per trasferire a un indirizzo di terze parti tutti i messaggi di errore (elaborati o non elaborati ) raccolti dalla piattaforma Adobe Campaign.
* **[!UICONTROL Address for errors]** : compila questo campo per trasferire a un indirizzo di terze parti solo i messaggi di errore che il processo inMail non è stato in grado di qualificare.
* **[!UICONTROL SMTP server]** : server utilizzato per inviare le e-mail non recapitate non elaborate.

>[!IMPORTANT]
>
>Per inoltrare e-mail non recapitate non elaborate, l’Adobe consiglia di compilare solo il campo **[!UICONTROL Address for errors]** campo. Tuttavia, assicurati che l’indirizzo utilizzato sia controllato regolarmente, in quanto ciò potrebbe comportare un carico pesante sul server di posta. Per ulteriori informazioni, contatta il responsabile del tuo account.

## Configurazione del tracciamento {#tracking-configuration}

Il passaggio successivo consente di configurare il tracciamento per l’istanza. L’istanza deve essere dichiarata e registrata con i server di tracciamento.

Questo passaggio è disponibile solo quando **Canale e-mail** e **Tracciamento** le opzioni sono selezionate nella prima pagina della procedura guidata di distribuzione. Fai riferimento a [Parametri generali](#general-parameters).

Per informazioni più dettagliate sul tracciamento web (modalità di tracciamento, creazione e inserimento di tag...), consulta [questo documento](../../configuration/using/about-web-tracking.md).

### Principio di funzionamento {#operating-principle}

Quando attivi il tracciamento su un’istanza, gli URL nelle consegne vengono modificati durante l’invio per abilitare il tracciamento.

* Le informazioni sugli URL esterni (protetti o meno) immesse in questa pagina della procedura guidata di distribuzione vengono utilizzate per generare il nuovo URL. Oltre a queste informazioni, il collegamento modificato contiene: gli identificatori della consegna, il destinatario e l’URL.

  Le informazioni di tracciamento vengono raccolte da Adobe Campaign sui server di tracciamento per arricchire i profili dei destinatari e i dati collegati alla consegna ( **[!UICONTROL Tracking]** schede).

  Le informazioni sugli URL interni vengono utilizzate solo dal server applicazioni Adobe Campaign per contattare il server o i server di tracciamento.

  Per ulteriori informazioni, consulta [Server di tracciamento](#tracking-server).

* Una volta configurati gli URL, devi abilitare il tracciamento. A questo scopo, l’istanza deve essere registrata sui server di tracciamento.

  Per ulteriori informazioni, consulta [Salvataggio del tracciamento](#saving-tracking).

### Server di tracciamento {#tracking-server}

![](assets/s_ncs_install_deployment_wiz_08.png)

Per garantire l’efficienza del tracciamento in questa istanza, è necessario visualizzare le seguenti informazioni:
<!--With Mid-sourcing architecture, you can externalize tracking management. To do this:-->

* **[!UICONTROL External URL]** e/o **[!UICONTROL Secure external URL]** : immetti l’URL di reindirizzamento da utilizzare nell’e-mail da inviare.
* **[!UICONTROL Internal URL(s)]** : URL utilizzati solo dal server Adobe Campaign per contattare i server di tracciamento e raccogliere i registri e caricare gli URL. Non è necessario associarlo all’istanza.

  Se non specifichi un URL, per impostazione predefinita verrà utilizzato l’URL di tracciamento.

Con l’architettura mid-sourcing, puoi esternalizzare la gestione del tracciamento. Per eseguire questa operazione:

1. Seleziona l’opzione **[!UICONTROL Externalize tracking management]** : consente di utilizzare un server di mid-sourcing come server di tracciamento.
1. Popolare il **[!UICONTROL External account]** e **[!UICONTROL Instance name]** per connettersi al server di mid-sourcing.

   Per ulteriori informazioni, consulta [Server di mid-sourcing](../../installation/using/mid-sourcing-server.md).

1. Fai clic su **[!UICONTROL Enable the tracking instance]** per approvare la connessione al server.

   ![](assets/s_ncs_install_deployment_wiz_18.png)

### Salvataggio del tracciamento {#saving-tracking}

Una volta inseriti gli URL, devi registrare il server di tracciamento.

Fai clic sul collegamento **Registrazione sui server di tracciamento** quindi selezionare una delle opzioni disponibili.

![](assets/s_ncs_install_deployment_wiz_09.png)

Esistono tre possibili tipi di architettura per l’implementazione del tracciamento:

1. **Aggiunta del supporto per il tracciamento in un’istanza esistente**

   Questa scelta si applica se l’istanza è già stata creata per altre esigenze (server MTA, ecc.) su server che verranno utilizzati come server di tracciamento.

   ![](assets/s_ncs_install_deployment_wiz_11.png)

   Immetti la password per **interno** account sui server di reindirizzamento per configurare l’istanza di tracciamento.

   >[!NOTE]
   >
   >Se vengono utilizzati più server di tracciamento, devono tutti utilizzare lo stesso nome e la stessa password.

   Specifica il nome dell’istanza e la password.

1. **Crea una nuova istanza dedicata al tracciamento**

   Questa opzione è utile quando le istanze di tracciamento sono riservate per il tracciamento e non hanno altri moduli applicativi.

   ![](assets/s_ncs_install_deployment_wiz_10.png)

   Immetti la password per **interno** account sui server di reindirizzamento per configurare l’istanza di tracciamento.

   >[!NOTE]
   >
   >Se sono configurati più server di tracciamento, devono tutti utilizzare la stessa password.

   Specifica il nome dell’istanza, la password ed eventuali maschere DNS associate, ad esempio **[!UICONTROL Campaign*]**.

1. **Convalida un’istanza di tracciamento già preconfigurata per te**

   Questa opzione viene utilizzata quando non si dispone della password per **interno** account; in questo caso, un account di tracciamento è preconfigurato per te sui server di tracciamento. Immetti la password dell&#39;account di tracciamento dei server di reindirizzamento per convalidare l&#39;istanza di tracciamento.

   ![](assets/s_ncs_install_deployment_wiz_17.png)

   Specifica il nome dell’istanza da convalidare.

Clic **Approva** per avviare la registrazione con il server di tracciamento.

Nella finestra precedente, un messaggio conferma la registrazione a livello del server di tracciamento:

![](assets/s_ncs_install_deployment_wiz_tracking_ok.png)

Parametri collegati alle ricerche URL **non deve essere modificato** per un&#39;installazione standard. Per tutti gli altri parametri, contatta l’Adobe.

## Parametri del canale mobile {#mobile-channel-parameters}

Il passaggio successivo consente di definire le impostazioni predefinite per le consegne ai dispositivi mobili (SMS e Push WAP).

>[!NOTE]
>
>Il canale mobile è facoltativo: questa fase viene visualizzata solo se è stato acquistato. Controlla il contratto di licenza.

![](assets/s_ncs_install_deployment_wiz_12.png)

### Account predefinito per la consegna SMS {#default-account-for-sms-delivery}

Immettere le seguenti informazioni:

* **[!UICONTROL Label]** : immetti un nome per questo account SMS/Wap Push. Ad esempio, è possibile utilizzare il nome del router.
* Per **[!UICONTROL Server]**, **[!UICONTROL Port]**, **[!UICONTROL Account]**, **[!UICONTROL Password]**, **[!UICONTROL Connector]**, **[!UICONTROL Send Endpoint]**, **[!UICONTROL Reception Endpoint]**, **[!UICONTROL Notification Endpoint]** campi: contatta il provider di servizi per ottenere le impostazioni richieste.

### Parametri degli SMS inviati {#parameters-of-sms-sent}

In **Priorità** Elenco a discesa: seleziona &quot;Normal&quot; (Normale), &quot;High&quot; (Alta) o &quot;Urgent&quot; (Urgente) per applicarlo ai messaggi da inviare.

### Parametri avanzati {#advanced-parameters}

Il **Parametri avanzati...** consente di accedere alle opzioni di nuovo tentativo e quarantena.

![](assets/s_ncs_install_deployment_wiz_13.png)

Le informazioni sui nuovi tentativi sono disponibili nel **Periodo di nuovi tentativi** e **Numero di nuovi tentativi** campi: quando un dispositivo mobile non è raggiungibile, per impostazione predefinita il programma riprova 5 volte a intervalli di almeno 15 minuti (per il periodo di consegna massimo). Questi valori possono essere adattati in base alle tue esigenze.

Le opzioni di configurazione per le quarantene sono le seguenti:

* **[!UICONTROL Time between two significant errors]** : immetti un valore predefinito (per impostazione predefinita &quot;1d&quot;: giorno) per definire il tempo che l’applicazione attende prima di incrementare il contatore degli errori in caso di errore.
* **[!UICONTROL Maximum number of errors before quarantine]** : una volta raggiunto questo valore, il numero di cellulare viene messo in quarantena (per impostazione predefinita &quot;5&quot;: il numero viene messo in quarantena al sesto errore). Ciò significa che il contatto verrà automaticamente escluso dalle consegne future.

## Impostazioni regionali {#regional-settings}

Questa fase ti consente di includere le preferenze dei criteri per i dati.

![](assets/s_ncs_install_deployment_wiz_14.png)

* **[!UICONTROL Consider all phone numbers as international ones]** : quando questa opzione è selezionata, l’applicazione applica il formato internazionale ai numeri di telefono (il prefisso del paese è quindi obbligatorio perché il numero di cifre non verrà controllato prima di applicare la formattazione). Se questa opzione non è selezionata, il numero di telefono internazionale deve essere preceduto da &quot;+&quot; o &quot;00&quot;.
* **[!UICONTROL Store all phone numbers using the international format]** : questa opzione riguarda solo **residenti nazionali** numeri di telefono importati o modificati. Definire se si desidera utilizzare un formato nazionale (ad esempio 425 555 0150) o internazionale (ad esempio +1 425 555 0150)

## Accesso da Internet {#access-from-the-internet}

>[!IMPORTANT]
>
>Per motivi di privacy, consigliamo di utilizzare HTTPS per tutte le risorse esterne.

Questo passaggio ti consente di definire gli URL di accesso per le pagine Adobe Campaign esposte su Internet.

È inoltre necessario indicare qui le opzioni di pubblicazione collegate ai moduli Web.

![](assets/s_ncs_install_deployment_wiz_15.png)

### Server esposti sul Web {#servers-exposed-on-the-web}

Utilizzare questa pagina per popolare gli URL del server per:

1. Accedi al server applicazioni esposto su Internet: moduli di abbonamento/annullamento dell’abbonamento, extranet, ecc.
1. Accedi al server applicazioni per le risorse non esposte sul web: moduli, Intranet, pagine di conferma.
1. Accedi alle pagine mirror delle consegne.

   Una pagina speculare è una pagina dinamica che visualizza il contenuto dell’e-mail. È accessibile tramite un collegamento inserito nel messaggio inviato al destinatario e può contenere elementi personalizzati. La pagina speculare offre al destinatario la possibilità di leggere il messaggio in un browser Internet invece che nel software e-mail, indipendentemente dal formato di consegna (testo o HTML). Tuttavia, le pagine mirror vengono generate per una determinata consegna solo se è stato definito il contenuto HTML richiesto.

Adobe Campaign consente di distinguere questi tre URL per distribuire il carico su più piattaforme.


>[!NOTE]
>
>* Queste impostazioni vengono salvate nelle opzioni della piattaforma Campaign. [Ulteriori informazioni](../../installation/using/configuring-campaign-options.md).
>* Per le configurazioni con più marchi, puoi adattare l’URL della pagina mirror e ignorare questa configurazione dall’account esterno di indirizzamento e-mail. [Ulteriori informazioni](../../installation/using/configuring-campaign-options.md).


## Gestione delle risorse pubbliche {#managing-public-resources}

>[!IMPORTANT]
>
>Per motivi di privacy, consigliamo di utilizzare HTTPS per tutte le risorse esterne.

Per essere viste dall’esterno, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server accessibile dall’esterno. Possono quindi essere disponibili per destinatari o operatori esterni.

![](assets/s_ncs_install_deployment_wiz_img_uploading.png)

Per questo passaggio, è necessario immettere:

1. Il nuovo URL della risorsa pubblica. Per ulteriori informazioni, consulta [URL risorse pubbliche](#public-resources-url) sezione.
1. La modalità di rilevamento delle immagini in una consegna. Per ulteriori informazioni, consulta [Rilevamento immagine della consegna](#delivery-image-detection) sezione.
1. Opzioni di pubblicazione. Per ulteriori informazioni, consulta [Modalità di pubblicazione](#publication-modes) sezione.

Le risorse pubbliche sono accessibili tramite **Amministrazione > Risorse > Online > Risorse pubbliche** della struttura Adobe Campaign. Vengono raccolti in una libreria e possono essere inclusi nelle e-mail, ma anche utilizzati in campagne o attività e nella gestione dei contenuti.

![](assets/install_pub_resources_view.png)

### URL risorse pubbliche {#public-resources-url}

Il primo campo consente di specificare l’inizio dell’URL utilizzato per le risorse caricate. Una volta caricate, le risorse sono accessibili tramite questo nuovo URL.

In una consegna, puoi utilizzare le immagini memorizzate nella libreria di risorse pubblica o qualsiasi altra immagine o immagine locale memorizzata su un server.

* Per le immagini delle e-mail, **https://** server **/res/img** URL.

  Questo valore può essere sovrascritto per ogni consegna.

* Per le risorse pubbliche, l’URL **https://** server **/res/** istanza ****dove **istanza**è il nome dell’istanza di tracciamento.

### Rilevamento immagine della consegna {#delivery-image-detection}

In una consegna, puoi utilizzare le immagini memorizzate nella libreria di risorse pubblica o qualsiasi altra immagine o immagine locale memorizzata su un server.

Il campo **Maschere URL** consente di specificare l’elenco delle maschere URL da ignorare durante il caricamento automatico delle immagini. Se ad esempio si utilizzano immagini memorizzate in un sito accessibile dall&#39;esterno, in particolare in un sito Internet, è possibile immettere l&#39;URL del sito in questo campo.

![](assets/s_ncs_install_deployment_wiz_img_mask.png)

Puoi specificare più maschere URL utilizzando una virgola per separarle.

* Per informazioni sull’utilizzo e la gestione delle immagini nelle e-mail, consulta [questa sezione](../../delivery/using/defining-the-email-content.md#adding-images).
* Nella procedura guidata di consegna, le immagini chiamate da questi URL avranno lo stato &quot;Ignorato&quot;.

### Modalità di pubblicazione {#publication-modes}

La sezione inferiore della procedura guidata consente di selezionare le opzioni di pubblicazione delle risorse pubbliche e delle immagini.

Sono disponibili le seguenti modalità di pubblicazione:

* Server di tracciamento

  Le risorse verranno copiate automaticamente sui diversi server di tracciamento. Sono configurati nel passaggio [Configurazione del tracciamento](#tracking-configuration).

* Altri server Adobe Campaign

  Puoi utilizzare uno o più altri server Adobe Campaign in cui copiare le risorse.

  Lato server, per utilizzare un server Adobe Campaign dedicato, devi creare una nuova istanza con il seguente comando:

  ```
  nlserver config -addtrackinginstance:<trackingA>/<trackingA*>
  ```

  Immettere quindi la password.

  I parametri dei server dedicati sono riportati nella **[!UICONTROL Media URL(s)]**, **[!UICONTROL Password]** e **[!UICONTROL Instance name]** campi.

  ![](assets/s_ncs_install_images_upload_b.png)

* Script di pubblicazione manuale (solo per risorse pubbliche)

  ![](assets/s_ncs_install_images_upload_c.png)

  Puoi pubblicare le immagini utilizzando uno script:

   * Devi creare questo script: il suo contenuto dipende dalla configurazione.
   * Lo script verrà richiamato dal comando seguente:

     ```
     [INSTALL]/copyToFrontal.vbs "$(XTK_INSTALL_DIR)\var\<instance>\upload\" "img1,img2,img3"
     ```

     dove `[INSTALL]` è il percorso di accesso alla cartella di installazione di Adobe Campaign.

   * In Unix, assicurati che lo script sia eseguibile.

Per le immagini, è necessario copiarle dalla cartella &quot;images&quot; specificata tramite **NmsDelivery_ImageSubDirectory** su uno o più server frontali. Questi server memorizzeranno le immagini per renderle accessibili tramite il nuovo URL configurato.

In caso di pubblicazione su un server Adobe Campaign senza uno script di pubblicazione manuale, per impostazione predefinita, le immagini di una consegna vengono memorizzate in `$(XTK_INSTALL_DIR)/var/res/img/ directory`. L’URL corrispondente è il seguente: **`https://server/res/img`**.

`XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)`. L’URL corrispondente è il seguente: **`https://server/res/instance`** dove istanza è il nome dell’istanza di tracciamento.

>[!NOTE]
>
>È possibile modificare la directory di archiviazione delle risorse pubbliche. Per ulteriori informazioni, consulta [Gestione delle risorse pubbliche](#managing-public-resources).

### Sincronizzazione delle risorse pubbliche {#synchronizing-public-resources}

Questa funzionalità consente di **sincronizzare le risorse pubbliche** su più server di riserva.

Se una risorsa pubblica non è presente nel server di tracciamento o se la risorsa restituisce un errore 404, il server di tracciamento tenterà di trovare la risorsa in uno dei server di riserva.

La dichiarazione e la configurazione dei server di riserva devono essere eseguite nel **serverConf.xml** file. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questo [sezione](../../installation/using/the-server-configuration-file.md).

**Dichiarazione**

```
<redirection>
<spareServer enabledIf="" id="" url=""/>
</redirection>
```

**Configurazione**

Per ogni risorsa pubblica che deve essere sincronizzata, devi aggiungere un attributo di stato al `<url>` elemento nel `<relay>` parte:

L’attributo di stato può corrispondere a uno dei tre valori seguenti:

* spare: la risorsa pubblica è sincronizzata

* normale: comportamento esistente (senza sincronizzazione)

* blacklist: se restituisce un errore 404, l’URL viene aggiunto al inserisco nell&#39;elenco Bloccati di. La durata (in secondi) dell’URL nel inserisco nell&#39;elenco Bloccati di è definita da un **timeout** attributo il cui valore predefinito è 60s.

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

## Eliminazione dei dati {#purging-data}

L’ultima fase della procedura guidata di distribuzione consente di configurare la rimozione automatica dei dati obsoleti. I valori sono espressi in giorni.

![](assets/s_ncs_install_deployment_wiz_16.png)

I dati vengono eliminati automaticamente tramite il flusso di lavoro di pulizia del database. Per ulteriori informazioni su come configurare e utilizzare questo flusso di lavoro e dettagli sugli elementi eliminati, consulta questa [documento](../../production/using/database-cleanup-workflow.md).
