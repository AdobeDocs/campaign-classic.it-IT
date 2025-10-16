---
product: campaign
title: Installare i pacchetti incorporati di Campaign Classic
description: Scopri come installare i pacchetti incorporati di Campaign
feature: Installation, Application Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
exl-id: 2bc077c4-ed65-4157-bfc9-df5d0442f476
source-git-commit: 0507e0372a81351adc145dafdd3cbe5d5422dc00
workflow-type: tm+mt
source-wordcount: '1271'
ht-degree: 3%

---

# Installare i pacchetti incorporati di Campaign Classic{#installing-campaign-standard-packages}



## Informazioni sui pacchetti incorporati {#campaign-standard-packages}

I pacchetti incorporati contengono una serie di funzioni che possono essere installate in base alle tue esigenze e a seconda del contratto. L’elenco completo dei pacchetti integrati di Campaign è disponibile di seguito.

>[!CAUTION]
>
>È possibile installare solo i pacchetti corrispondenti alle opzioni indicate nel contratto di licenza.
>
>L’installazione di un nuovo pacchetto può influire su tutta la piattaforma: deve essere testato e convalidato prima della distribuzione finale.
>
>Una volta installato un pacchetto, non è possibile disinstallarlo.
>
>In qualità di cliente in hosting o ibrido, contatta Adobe per distribuire un nuovo pacchetto integrato.

Per installare un pacchetto integrato:

1. Accedere all&#39;Assistente all&#39;importazione del pacchetto da **[!UICONTROL Tools > Advanced > Import package]** nella console client di Adobe Campaign.
1. Seleziona **[!UICONTROL Install a standard package]**.
1. Nell&#39;elenco dei pacchetti, selezionare i pacchetti da installare.
   >[!NOTE]
   >
   >Quando un pacchetto è disattivato, significa che è già installato o non è compatibile con l’istanza. La compatibilità è illustrata nella tabella seguente.
1. Fare clic su **[!UICONTROL Next]**, quindi su **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto.

   Una volta installati i pacchetti, la barra di avanzamento mostra **100%** ed è possibile visualizzare il seguente messaggio nei registri di installazione: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** la finestra di installazione.

I pacchetti ora sono installati.

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
   <td> Monitora le consegne e gli eventuali problemi rilevati durante l’invio dei messaggi. <a href="../../delivery/using/about-delivery-monitoring.md">Ulteriori informazioni</a><br /> </td> 
   <td> Tutti</td> 
  </tr> 
  <tr> 
   <td> Campagne di marketing (Campaign)<br /> </td> 
   <td> Definisce, ottimizza, esegue e analizza campagne di comunicazione e marketing. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/campaigns/campaigns.html" target="_blank">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Risorse di marketing (MRM)<br /> </td> 
   <td> Controlla le azioni di marketing in modalità collaborativa fornendo la gestione e il tracciamento delle attività, dei budget e delle risorse di marketing. <a href="https://experienceleague.adobe.com/docs/campaign/automation/mrm/about-marketing-resource-management.html?lang=it" target="_blank">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Motore di offerta (interazione)<br /> </td> 
   <td> Risponde in tempo reale durante un’interazione con un determinato contatto (un cliente o un target) rendendolo una o più offerte adattate.  Facoltativo. <a href="../../interaction/using/interaction-and-offer-management.md#packages-configuration">Ulteriori informazioni</a> <br /> </td> 
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
   <td> Mid, Esecuzione <br /> </td>  
  </tr> 
  <!--tr> 
   <td> Lead Management (Leads) (deprecated)<br /> </td> 
   <td> Simplifies the process of building and maintaining the entire leads management life cycle. <br /> </td> 
   <td> Yes<br /> </td> 
   <td> Optional, <a href="https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html">Learn More</a> </td> 
  </tr--> 
  <tr> 
   <td> Social network (Social marketing) <br /> </td> 
   <td> Sincronizza Adobe Campaign con X (precedentemente noto come Twitter) e Facebook. <a href="../../social/using/about-social-marketing.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutti</td> 
  </tr> 
  <tr> 
   <td> Controllo dei messaggi transazionali (Centro messaggi - Controllo)<br /> </td> 
   <td> Gestisce i messaggi di attivazione generati da eventi attivati dai sistemi di informazione. Facoltativo. <a href="../../message-center/using/about-transactional-messaging.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Esecuzione dei messaggi transazionali (Centro messaggi - Esecuzione) <br /> </td> 
   <td> Garantisce una maggiore disponibilità e una migliore gestione del carico. Facoltativo. <a href="../../message-center/using/about-transactional-messaging.md">Ulteriori informazioni</a><br /> </td> 
   <td> Esecuzione<br /> </td>
  </tr> 
  <tr> 
   <td> Canale LINE<br /> </td> 
   <td> Invia consegne utilizzando il canale LINE con Adobe Campaign. Facoltativo. La messaggistica transazionale (pacchetto del centro messaggi) è obbligatoria. <a href="../../delivery/using/line-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Canale direct mailing<br /> </td> 
   <td> Invia consegne utilizzando il canale di direct mailing con Adobe Campaign. Facoltativo. <a href="../../delivery/using/about-direct-mail-channel.md">Ulteriori informazioni</a><br /> </td> 
   <td> Tutto<br /> </td>
  </tr> 
  <tr> 
   <td> Canale mobile (SMS) <br /> </td> 
   <td> Invia consegne utilizzando il canale Mobile/SMS con Adobe Campaign. Facoltativo. <a href="../../delivery/using/sms-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
   <tr> 
   <td> Canale telefonico<br /> </td> 
   <td> Invia consegne utilizzando il canale telefonico con Adobe Campaign. Utilizzato per il call center. Facoltativo. <a href="../../delivery/using/communication-channels.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Canale app mobile<br /> </td> 
   <td> Utilizza la piattaforma Adobe Campaign per inviare notifiche personalizzate ai terminali di iOS e Android tramite app. Facoltativo. <a href="../../delivery/using/about-mobile-app-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestione contenuti<br /> </td> 
   <td> Crea newsletter o siti Web ricorrenti, quindi convalida e pubblica i messaggi. <a href="../../delivery/using/about-content-management.md">Ulteriori informazioni</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Sondaggi online (Gestione sondaggi)<br /> </td> 
   <td> Crea e gestisce moduli online per aggiungere o modificare le informazioni del profilo, per effettuare l’abbonamento, per annullare l’abbonamento o un modulo per partecipare a un concorso. Facoltativo. <a href="../../surveys/using/about-surveys.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Consente di analizzare e misurare i dati, calcolare le statistiche, semplificare e ottimizzare la creazione e il calcolo dei rapporti. Inoltre, puoi creare rapporti e creare popolazioni target. Facoltativo. <a href="../../reporting/using/ac-cubes.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestione risposte<br /> </td> 
   <td> Misura il successo e la redditività delle campagne di marketing o delle proposte di offerte per tutti i canali di comunicazione.  Facoltativo. <a href="../../response/using/about-response-manager.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Accesso ai dati esterni (Federated Data Access)<br /> </td> 
   <td> Fornisce l’opzione Federated Data Access (FDA) per elaborare le informazioni memorizzate in uno o più database esterni in modo da poter accedere ai dati esterni senza modificare la struttura dei dati di Adobe Campaign.  Facoltativo. <a href="https://experienceleague.adobe.com/docs/campaign/automation/workflows/advanced-management/accessing-an-external-database-fda.html" target="_blank">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Ottimizzazione campagna<br /> </td> 
   <td> Controlla, filtra e monitora l’invio delle consegne in modo che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in linea con le politiche di comunicazione aziendali. Facoltativo. <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-optimization/campaign-typologies.html?lang=it" target="_blank">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitoraggio del recapito messaggi (recapito messaggi e-mail)<br /> </td> 
   <td> Misura il successo delle campagne che raggiungono la casella in entrata dei destinatari senza rimbalzare o essere contrassegnate come spam. Facoltativo. <a href="../../delivery/using/about-deliverability.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutti </td> 
  </tr> 
  <tr> 
   <td> Gestione coupon<br /> </td> 
   <td> Crea un set di coupon da aggiungere alle prossime offerte di marketing. Facoltativo. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalized-coupons.html" target="_blank">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Rendering casella in entrata (IR)<br /> </td> 
   <td> Consente di visualizzare in anteprima il messaggio inviato nei diversi contesti in cui può essere ricevuto e di verificare la compatibilità nei desktop e nelle applicazioni principali. Facoltativo. <a href="../../delivery/using/inbox-rendering.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing centrale/locale (Marketing distribuito)<br /> </td> 
   <td> Implementa campagne di cooperazione tra enti centrali (sedi centrali, dipartimenti di marketing, ecc.) ed enti locali (punti vendita, agenzie regionali, ecc.). Facoltativo. <a href="https://experienceleague.adobe.com/docs/campaign/automation/distributed-marketing/about-distributed-marketing.html?lang=it" target="_blank">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Connettori di gestione delle relazioni con i clienti<br /> </td> 
   <td> Fornisce vari connettori di gestione delle relazioni con i clienti per collegare la piattaforma Adobe Campaign ai sistemi di terze parti.  <a href="../../platform/using/crm-connectors.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Connettori di analisi web<br /> </td> 
   <td> Consente ad Adobe Campaign e Adobe Analytics di interagire attraverso il pacchetto Connettori di analisi web. Non compatibile con la messaggistica transazionale (pacchetto del centro messaggi). <a href="../../integrations/using/gs-aa.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Integrazione AEM<br /> </td> 
   <td> Consente di gestire il contenuto delle consegne e-mail e dei moduli direttamente in Adobe Experience Manager per sfruttare le funzionalità di modifica dei contenuti di AEM e le capacità di consegna di Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integrazione dei tipi di pubblico condivisi di Adobe Experience Cloud<br /> </td> 
   <td> Consente di scambiare e condividere tipi di pubblico/segmenti con soluzioni e app Adobe Experience Cloud. Richiede IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integrazione con Adobe Experience Cloud<br /> </td> 
   <td> Consente di importare ed esportare tipi di pubblico/segmenti da diverse soluzioni Adobe Experience Cloud in Adobe Campaign. Facoltativo. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Ulteriori informazioni</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Regolamento sulla protezione dei dati sulla privacy<br /> </td> 
   <td> Contiene funzionalità aggiuntive per facilitare la conformità in materia di privacy in Campaign Classic. <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutti</td> 
  </tr> 
  <tr> 
   <td> Trasferisci a mid-sourcing <br /> </td> 
   <td> Descrive l’installazione e la configurazione di un server di mid-sourcing, nonché la distribuzione di un’istanza che consente a terze parti di inviare messaggi in modalità mid-sourcing. Facoltativo. <a href="../../installation/using/mid-sourcing-server.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Piattaforma mid-sourcing<br /> </td> 
   <td> Questa configurazione rappresenta una soluzione intermedia ottimale tra una configurazione ASP (Hosted Configuration) e l’internalizzazione. I componenti di esecuzione rivolti all’esterno vengono eseguiti su un server di "mid-sourcing" ospitato in Adobe Campaign. Facoltativo. <a href="../../installation/using/mid-sourcing-server.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Mid-sourcing </td> 
  </tr> 
  <tr> 
   <td> Supporto AMP<br /> </td> 
   <td> Consente di utilizzare il nuovo AMP interattivo per il formato e-mail e di inviare e-mail dinamiche. Facoltativo. <a href="https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html" target="_blank">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutti </td> 
  </tr> 
  <tr> 
   <td> Connettore ACS (obsoleto)<br /> </td> 
   <td> Collega Adobe Campaign v7 e Adobe Campaign Standard. Si tratta di una funzione integrata di Campaign v7 che replica automaticamente i dati in Campaign Standard, unendo il meglio di entrambe le applicazioni. Facoltativo.<br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Pacchetto Centro messaggi {#message-center-package}

È necessario installare i canali di consegna (e-mail, canale mobile, canale app mobile, LINE, ecc.) prima di installare la messaggistica transazionale (pacchetto del centro messaggi). Se hai avviato un progetto di Centro messaggi di sola posta elettronica e in seguito devi aggiungere un nuovo canale, devi seguire questi passaggi:

1. Installa il nuovo canale, ad esempio il **canale mobile**, utilizzando l&#39;Assistente all&#39;importazione del pacchetto ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importare il file ( **[!UICONTROL Tools > Advanced > Import package > File]**) e selezionare:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. In **[!UICONTROL XML data content to import]**, mantieni solo il modello di consegna del Centro messaggi corrispondente al canale correlato. Ad esempio, se hai aggiunto il **Canale mobile**, mantieni solo l&#39;elemento **entità** corrispondente al modello **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Se hai aggiunto il **canale app mobile**, mantieni solo i **modelli di messaggi transazionali di iOS** (iosTriggerMessage) e **messaggi transazionali di Android** (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)


### Configurazione canale [!DNL LINE]{#line-package}

Per configurare il canale [!DNL LINE], è necessario prima installare il pacchetto [!DNL LINE].

Nel contesto di una configurazione di mid-sourcing, devi:

* Installa il pacchetto [!DNL LINE] sia sull&#39;istanza Marketing che su quella MID

* Imposta l&#39;account esterno [!DNL LINE] nell&#39;istanza di marketing in modo che punti all&#39;istanza mid modificando la modalità di consegna. [Ulteriori informazioni](../../delivery/using/line-channel.md#configure-line-external)

* Imposta le credenziali [!DNL LINE] nell&#39;account esterno nell&#39;istanza MID.

>[!CAUTION]
>
>I modelli di recapito del Centro messaggi per il canale [!DNL LINE] non saranno disponibili se i pacchetti del Centro messaggi sono installati prima di [!DNL LINE].