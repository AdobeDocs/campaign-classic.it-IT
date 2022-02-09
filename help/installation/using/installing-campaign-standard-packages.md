---
product: campaign
title: Installazione dei pacchetti integrati di Campaign Classic
description: Scopri come installare i pacchetti incorporati di Campaign
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 6%

---

# Installazione dei pacchetti integrati di Campaign Classic{#installing-campaign-standard-packages}

![](../../assets/v7-only.svg)

## Informazioni sui pacchetti incorporati {#campaign-standard-packages}

I pacchetti incorporati contengono un set di funzioni che possono essere installate in base alle tue esigenze e a seconda del contratto. Di seguito è riportato l’elenco completo dei pacchetti incorporati di Campaign.

>[!CAUTION]
>
>È possibile installare solo i pacchetti corrispondenti alle opzioni indicate nel contratto di licenza.
>
>L&#39;installazione di un nuovo pacchetto può avere un impatto su tutta la piattaforma: deve essere testato e convalidato prima della distribuzione finale.
>
>Una volta installato un pacchetto, non è possibile disinstallarlo.
>
>In qualità di cliente ospitato o ibrido, contatta l’Adobe per far sì che sia implementato un nuovo pacchetto integrato.

Per installare un pacchetto incorporato:

1. Accedi alla procedura guidata di importazione del pacchetto da **[!UICONTROL Tools > Advanced > Import package]** nella console client di Adobe Campaign.
1. Seleziona **[!UICONTROL Install a standard package]**.
1. Nell&#39;elenco dei pacchetti, seleziona i pacchetti da installare.
   >[!NOTE]
   >
   >Quando un pacchetto è disabilitato, significa che è già installato o che non è compatibile con la tua istanza. La compatibilità è descritta nella tabella seguente.
1. Fai clic su **[!UICONTROL Next]**, quindi **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto.

   Una volta installati i pacchetti, la barra di avanzamento mostra **100%** e puoi visualizzare il seguente messaggio nei log di installazione: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** la finestra di installazione.

I pacchetti sono ora installati.

### Elenco dei pacchetti predefiniti {#list-of-standard-packages}

Nella tabella seguente sono elencati tutti i pacchetti incorporati di Campaign.

<table> 
 <thead> 
  <tr> 
   <th> Pacchetto </th> 
   <th> Descrizione </th> 
   <th> Tipo di istanza </th>
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> Consegna<br /> </td> 
   <td> Monitora le consegne e gli eventuali problemi riscontrati durante l’invio dei messaggi. <a href="../../delivery/using/about-delivery-monitoring.md">Ulteriori informazioni</a><br /> </td> 
   <td> Tutto</td> 
  </tr> 
  <tr> 
   <td> Campagne di marketing (Campaign)<br /> </td> 
   <td> Definisce, ottimizza, esegue e analizza campagne di comunicazione e marketing. <a href="../../campaign/using/designing-marketing-campaigns.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Risorse di marketing (MRM)<br /> </td> 
   <td> Controlla le azioni di marketing in modalità collaborativa fornendo la gestione e il tracciamento delle attività, dei budget e delle risorse di marketing. <a href="../../mrm/using/about-marketing-resource-management.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Motore di offerta (interazione)<br /> </td> 
   <td> Risponde in tempo reale durante un'interazione con un determinato contatto (un cliente o un target) rendendolo una o più offerte adattate.  Facoltativo. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Controllo del motore di offerta con istanza di esecuzione. Facoltativo.<br /> </td> 
   <td> Pacchetto da installare sull’istanza di controllo per il motore di offerta (interazione). <a href="../../interaction/using/distributed-architectures.md#packages-configuration">Ulteriori informazioni</a> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Motore di offerta per le istanze di esecuzione. Facoltativo.<br /> </td> 
   <td> Pacchetto da installare sulle istanze di esecuzione per il motore di offerta (interazione). <a href="../../interaction/using/distributed-architectures.md">Ulteriori informazioni</a> </td> 
   <td> Mid, Execution <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Social network (Social Marketing) <br /> </td> 
   <td> Sincronizza Adobe Campaign con Twitter e Facebook. <a href="../../social/using/about-social-marketing.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto</td> 
  </tr> 
  <tr> 
   <td> Controllo dei messaggi transazionali (Centro messaggi - Controllo)<br /> </td> 
   <td> Gestisce i messaggi di attivazione generati dagli eventi attivati dai sistemi informativi. Facoltativo. <a href="../../message-center/using/about-transactional-messaging.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Esecuzione di messaggi transazionali (Centro messaggi - Esecuzione) <br /> </td> 
   <td> Garantisce una maggiore disponibilità e una migliore gestione del carico. Facoltativo. <a href="../../message-center/using/about-transactional-messaging.md">Ulteriori informazioni</a><br /> </td> 
   <td> Esecuzione<br /> </td>
  </tr> 
  <tr> 
   <td> Canale LINE<br /> </td> 
   <td> Invia consegne utilizzando il canale LINE con Adobe Campaign. Facoltativo. Messaggi transazionali (pacchetto del Centro messaggi) obbligatori. <a href="../../delivery/using/line-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Canale Direct Mail<br /> </td> 
   <td> Invia consegne utilizzando il canale direct mailing con Adobe Campaign. Facoltativo. <a href="../../delivery/using/about-direct-mail-channel.md">Ulteriori informazioni</a><br /> </td> 
   <td> Tutto<br /> </td>
  </tr> 
  <tr> 
   <td> Canale mobile (SMS) <br /> </td> 
   <td> Invia consegne utilizzando il canale Mobile/SMS con Adobe Campaign. Facoltativo. <a href="../../delivery/using/sms-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
   <tr> 
   <td> Canale telefonico<br /> </td> 
   <td> Invia consegne utilizzando il canale telefonico con Adobe Campaign. Utilizzato per call center. Facoltativo. <a href="../../delivery/using/communication-channels.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Canale app mobile<br /> </td> 
   <td> Utilizza la piattaforma Adobe Campaign per inviare notifiche personalizzate ai terminali iOS e Android tramite app. Facoltativo. <a href="../../delivery/using/about-mobile-app-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestione dei contenuti<br /> </td> 
   <td> Crea newsletter o siti web ricorrenti e quindi convalida e pubblica i messaggi. <a href="../../delivery/using/about-content-management.md">Ulteriori informazioni</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Sondaggi online (Gestore dei sondaggi)<br /> </td> 
   <td> Crea e gestisce moduli online per aggiungere o modificare le informazioni sul profilo, per effettuare l’abbonamento, per annullare l’iscrizione o per creare un modulo di partecipazione al concorso. Facoltativo. <a href="../../surveys/using/about-surveys.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Analisi di marketing<br /> </td> 
   <td> Consente di analizzare e misurare i dati, calcolare le statistiche, semplificare e ottimizzare la creazione e il calcolo dei rapporti. Inoltre, puoi creare rapporti e creare popolazioni target. Facoltativo. <a href="../../reporting/using/about-cubes.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestione della risposta<br /> </td> 
   <td> Misura il successo e la redditività delle campagne di marketing o delle proposte di offerta per tutti i canali di comunicazione.  Facoltativo. <a href="../../response/using/about-response-manager.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Accesso a dati esterni (Federated Data Access)<br /> </td> 
   <td> Fornisce l’opzione Federated Data Access (FDA) per elaborare le informazioni memorizzate in uno o più database esterni in modo da poter accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.  Facoltativo. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Ottimizzazione di Campaign<br /> </td> 
   <td> Controlla, filtra e controlla l’invio delle consegne in modo che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali. Facoltativo. <a href="../../campaign-opt/using/about-campaign-typologies.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitoraggio del recapito messaggi (recapito messaggi e-mail)<br /> </td> 
   <td> Misura il successo delle campagne che raggiungono la casella in entrata dei destinatari senza rimbalzare o essere contrassegnate come spam. Facoltativo. <a href="../../delivery/using/about-deliverability.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto </td> 
  </tr> 
  <tr> 
   <td> Gestione coupon<br /> </td> 
   <td> Crea un set di coupon da aggiungere alle prossime offerte di marketing. Facoltativo. <a href="../../delivery/using/personalized-coupons.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Rendering della casella in entrata (IR)<br /> </td> 
   <td> Consente di visualizzare in anteprima il messaggio inviato nei diversi contesti in cui potrebbe essere ricevuto e di verificare la compatibilità nei principali desktop e applicazioni. Facoltativo. <a href="../../delivery/using/inbox-rendering.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing centrale/locale (Marketing distribuito)<br /> </td> 
   <td> Implementa campagne di cooperazione tra enti centrali (sedi centrali, dipartimenti di marketing, ecc.) e gli enti locali (punti vendita, agenzie regionali, ecc.). Facoltativo. <a href="../../distributed/using/about-distributed-marketing.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Connettori di gestione delle relazioni con i clienti<br /> </td> 
   <td> Fornisce diversi connettori di gestione delle relazioni con i clienti per collegare la tua piattaforma Adobe Campaign ai tuoi sistemi di terze parti.  <a href="../../platform/using/crm-connectors.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Connettori di Web Analytics<br /> </td> 
   <td> Consente ad Adobe Campaign e Adobe Analytics di interagire attraverso il pacchetto dei connettori di Web Analytics. Non compatibile con i messaggi transazionali (pacchetto del Centro messaggi). <a href="../../platform/using/adobe-analytics-connector.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Integrazione AEM<br /> </td> 
   <td> Consente di gestire il contenuto delle consegne e-mail e i moduli direttamente in Adobe Experience Manager, per sfruttare AEM funzionalità di modifica dei contenuti e le capacità di consegna di Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integrazione di tipi di pubblico condivisi di Adobe Experience Cloud<br /> </td> 
   <td> Consente di scambiare e condividere audience/segmenti con le soluzioni e i servizi di base di Adobe Experience Cloud. Richiede IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integrazione con Adobe Experience Cloud<br /> </td> 
   <td> Consente di importare ed esportare tipi di pubblico/segmenti da diverse soluzioni Adobe Experience Cloud in Adobe Campaign. Facoltativo. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Ulteriori informazioni</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Regolamento sulla protezione dei dati sulla privacy<br /> </td> 
   <td> Contiene funzionalità aggiuntive utili per la conformità in materia di privacy in Campaign Classic. <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto</td> 
  </tr> 
  <tr> 
   <td> Trasferisci a mid-Sourcing <br /> </td> 
   <td> Dettagli sull'installazione e la configurazione di un server di mid-sourcing, nonché la distribuzione di un'istanza che consente a terze parti di inviare messaggi in modalità di mid-sourcing. Facoltativo. <a href="../../installation/using/mid-sourcing-server.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Piattaforma di mid-sourcing<br /> </td> 
   <td> Questa configurazione è una soluzione intermedia ottimale tra una configurazione in hosting (ASP) e l’internalizzazione. I componenti di esecuzione rivolti all’esterno vengono eseguiti su un server "mid-sourcing" ospitato in Adobe Campaign. Facoltativo. <a href="../../installation/using/mid-sourcing-server.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Mid-sourcing </td> 
  </tr> 
  <tr> 
   <td> Supporto AMP<br /> </td> 
   <td> Consente di utilizzare il nuovo AMP interattivo per il formato e-mail e inviare e-mail dinamiche. Facoltativo. <a href="../../delivery/using/defining-interactive-content.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto </td> 
  </tr> 
  <tr> 
   <td> ACS Connector<br /> </td> 
   <td> Consente di collegare Adobe Campaign v7 e Adobe Campaign Standard. Si tratta di una funzione integrata in Campaign v7 che replica automaticamente i dati in Campaign Standard, unendo il meglio di entrambe le applicazioni. Facoltativo. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Pacchetto Message Center {#message-center-package}

Devi installare i canali di consegna (e-mail, canale mobile, canale app mobile, LINE, ecc.) prima di installare i messaggi transazionali (pacchetto del centro messaggi). Se hai avviato un progetto del Centro messaggi per e-mail e successivamente devi aggiungere un nuovo canale, segui questi passaggi:

1. Installa il nuovo canale, ad esempio il **Canale mobile**, utilizzando la procedura guidata di importazione del pacchetto ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importa il file ( **[!UICONTROL Tools > Advanced > Import package > File]**) e seleziona:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. In **[!UICONTROL XML data content to import]**, mantieni solo il modello di consegna del Centro messaggi corrispondente al canale correlato. Ad esempio, se hai aggiunto il **Canale mobile**, mantieni solo **entità** corrispondente al **[!UICONTROL Mobile transactional message]** Modello (smsTriggerMessage). Se hai aggiunto il **Canale app mobile**, mantieni solo **Messaggio sulle transazioni iOS** modelli (iosTriggerMessage) e **Messaggio sulle transazioni Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)


### [!DNL LINE] configurazione del canale{#line-package}

Per impostare [!DNL LINE] canale, devi prima installare il [!DNL LINE] pacchetto.

Nel contesto di una configurazione di mid-sourcing, è necessario:

* Installa il [!DNL LINE] pacchetto sia sull&#39;istanza Marketing che MID

* Imposta la [!DNL LINE] account esterno nell’istanza mkt per puntare all’istanza mid modificando la modalità di consegna. [Ulteriori informazioni](../../delivery/using/line-channel.md#configure-line-external)

* Imposta la [!DNL LINE] credenziali nell’account esterno nell’istanza MID.

>[!CAUTION]
>
>Modelli di consegna del Centro messaggi per [!DNL LINE] il canale non sarà disponibile se i pacchetti del Centro messaggi sono installati prima [!DNL LINE].