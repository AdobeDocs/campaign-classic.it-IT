---
title: Installazione dei pacchetti standard di Campaign Classic
seo-title: Installazione dei pacchetti standard di Campaign Classic
description: Installazione dei pacchetti standard di Campaign Classic
seo-description: null
page-status-flag: never-activated
uuid: 1cba9487-52fc-442f-ae99-f8a2c157f25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: dd8f9adf-208c-42d9-b1a7-bfc8a690687e
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 6%

---


# Installing Campaign Classic built-in packages{#installing-campaign-standard-packages}

## Informazioni sui pacchetti incorporati {#campaign-standard-packages}

I pacchetti incorporati contengono un set di funzioni che possono essere installate in base alle esigenze e a seconda del contratto. L&#39;elenco completo dei pacchetti predefiniti per Campaign è disponibile di seguito.

>[!CAUTION]
>
>È possibile installare solo pacchetti corrispondenti alle opzioni indicate nel contratto di licenza.
>
>L&#39;installazione di un nuovo pacchetto può avere un impatto su tutta la vostra piattaforma: deve essere testato e convalidato prima della distribuzione finale.
>
>Una volta installato un pacchetto, non potete disinstallarlo.

Per installare un pacchetto predefinito:

1. Accedete alla procedura guidata di importazione dei pacchetti **[!UICONTROL Tools > Advanced > Package import...]** nella console client Adobe Campaign .
1. Seleziona **[!UICONTROL Install a standard package]**.
1. Nell&#39;elenco dei pacchetti, verificate i pacchetti da installare.
   >[!NOTE]
   >
   >Quando un pacchetto è disattivato, significa che è già installato o che non è compatibile con l&#39;istanza. La compatibilità è illustrata nella tabella seguente.
1. Fate clic **[!UICONTROL Next]**, quindi **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto.

   Una volta installati i pacchetti, la barra di avanzamento mostra il **100%** ed è possibile visualizzare il seguente messaggio nei registri di installazione: **[!UICONTROL Installation of packages successful]**.

1. **[!UICONTROL Close]** la finestra di installazione.

I pacchetti ora sono installati.

### Elenco dei pacchetti out-of-the-box {#list-of-standard-packages}

Nella tabella seguente sono elencati tutti i pacchetti standard con la relativa descrizione, il tipo di istanza su cui possono essere installati (Marketing, Mid, ecc.) e informazioni aggiuntive.

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
   <td> Controlla le consegne e eventuali problemi riscontrati durante l'invio dei messaggi. <a href="../../delivery/using/monitoring-a-delivery.md">Ulteriori informazioni</a><br /> </td> 
   <td> Tutto</td> 
  </tr> 
  <tr> 
   <td> Campagne di marketing (Campaign)<br /> </td> 
   <td> Definisce, ottimizza, esegue e analizza campagne di comunicazione e marketing. <a href="../../campaign/using/designing-marketing-campaigns.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing</td>
  </tr> 
  <tr> 
   <td> Marketing resources (MRM)<br /> </td> 
   <td> Controlla le azioni di marketing in modalità collaborativa fornendo la gestione e il tracciamento di attività, budget e risorse di marketing. <a href="../../campaign/using/about-marketing-resource-management.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Motore di offerta (interazione)<br /> </td> 
   <td> Risponde in tempo reale durante un'interazione con un dato contatto (un cliente o un target), rendendogli una o più offerte adattate.  Facoltativo. <a href="../../interaction/using/interaction-and-offer-management.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Controllo del motore di offerta con istanza di esecuzione. Facoltativo.<br /> </td> 
   <td> </td> 
   <td> Marketing<br /> </td>  
  </tr> 
  <tr> 
   <td> Motore di offerta per le istanze di esecuzione. Facoltativo.<br /> </td> 
   <td> </td> 
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
   <td> Sincronizza  Adobe Campaign con Twitter e Facebook. <a href="../../social/using/about-social-marketing.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto</td> 
  </tr> 
  <tr> 
   <td> Controllo messaggi transazionali (Centro messaggi - Controllo)<br /> </td> 
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
   <td> Invia le consegne utilizzando il canale LINE con  Adobe Campaign. Facoltativo. Messaggi transazionali (pacchetto del centro messaggi) obbligatori. <a href="../../delivery/using/line-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Canale Direct Mail<br /> </td> 
   <td> Invia le consegne utilizzando il canale di posta diretta con  Adobe Campaign. Facoltativo. <a href="../../delivery/using/about-direct-mail-channel.md">Ulteriori informazioni</a><br /> </td> 
   <td> Tutto<br /> </td>
  </tr> 
  <tr> 
   <td> Canale mobile (SMS) <br /> </td> 
   <td> Invia le consegne utilizzando il canale Mobile/SMS con  Adobe Campaign. Facoltativo. <a href="../../delivery/using/sms-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Canale app mobile<br /> </td> 
   <td> Utilizza la piattaforma Adobe Campaign  per inviare notifiche personalizzate ai terminali iOS e Android tramite app. Facoltativo. <a href="../../delivery/using/about-mobile-app-channel.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Content Manager<br /> </td> 
   <td> Crea newsletter o siti Web periodici, quindi convalida e pubblicazione dei messaggi. <a href="../../delivery/using/about-content-management.md">Ulteriori informazioni</a> <br /> </td> 
   <td> </td>
  </tr> 
  <tr> 
   <td> Indagini online (responsabile sondaggio)<br /> </td> 
   <td> Crea e gestisce moduli online per aggiungere o modificare informazioni sul profilo, per iscriversi, per annullare la sottoscrizione o per un modulo di partecipazione al concorso. Facoltativo. <a href="../../web/using/about-surveys.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing Analytics<br /> </td> 
   <td> Consente di analizzare e misurare i dati, calcolare le statistiche, semplificare e ottimizzare la creazione e il calcolo dei rapporti. Inoltre, potete creare rapporti e creare popolazioni target. Facoltativo. <a href="../../reporting/using/about-cubes.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Gestione della risposta<br /> </td> 
   <td> Misura il successo e la redditività delle campagne di marketing o delle proposte di offerta per tutti i canali di comunicazione.  Facoltativo. <a href="../../campaign/using/about-response-manager.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Accesso ai dati esterni (accesso ai dati federati)<br /> </td> 
   <td> Fornisce l'opzione Federated Data Access (FDA) per elaborare le informazioni memorizzate in uno o più database esterni in modo da poter accedere ai dati esterni senza modificare la struttura  dati Adobe Campaign.  Facoltativo. <a href="../../workflow/using/accessing-an-external-database--fda-.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto<br /> </td> 
  </tr> 
  <tr> 
   <td> Ottimizzazione di Campaign<br /> </td> 
   <td> Controlla, filtra e controlla l'invio di messaggi in modo che i messaggi inviati soddisfino al meglio le esigenze e le aspettative dei clienti, in conformità con le politiche di comunicazione aziendali. Facoltativo. <a href="../../campaign/using/about-campaign-typologies.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Monitoraggio della realizzabilità (recapito e-mail)<br /> </td> 
   <td> Misura il successo delle campagne che raggiungono la inbox dei destinatari senza rimbalzare o essere contrassegnate come spam. Facoltativo. <a href="../../delivery/using/about-deliverability.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto </td> 
  </tr> 
  <tr> 
   <td> Gestione coupon<br /> </td> 
   <td> Crea un set di buoni da aggiungere alle prossime offerte di marketing. Facoltativo. <a href="../../delivery/using/personalized-coupons.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Rendering inbox (IR)<br /> </td> 
   <td> Consente di visualizzare l'anteprima del messaggio inviato nei diversi contesti in cui potrebbe essere ricevuto e di verificare la compatibilità nei principali desktop e applicazioni. Facoltativo. <a href="../../delivery/using/inbox-rendering.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Marketing centrale/locale (Distributed Marketing)<br /> </td> 
   <td> Implementa campagne di cooperazione tra enti centrali (sedi centrali, dipartimenti marketing, ecc.) ed enti locali (punti di vendita, agenzie regionali, ecc.). Facoltativo. <a href="../../campaign/using/about-distributed-marketing.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> CRM connectors<br /> </td> 
   <td> Fornisce diversi connettori CRM per collegare la tua piattaforma Adobe Campaign  ai tuoi sistemi di terze parti.  <a href="../../platform/using/crm-connectors.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Connettori per analisi Web<br /> </td> 
   <td> Consente  Adobe Campaign e  Adobe Analytics di interagire attraverso il pacchetto di connettori di analisi Web. Non compatibile con i messaggi transazionali (pacchetto del centro messaggi). <a href="../../platform/using/adobe-analytics-data-connector.md">Ulteriori informazioni</a><br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Integrazione AEM<br /> </td> 
   <td> Consente di gestire il contenuto delle comunicazioni e-mail e dei moduli direttamente in Adobe Experience Manager, per poter usufruire AEM funzionalità di modifica dei contenuti e  capacità di consegna Adobe Campaign. <a href="../../integrations/using/about-adobe-experience-manager.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Integrazione dell'audience condivisa Adobe Marketing Cloud<br /> </td> 
   <td> Consente di scambiare e condividere audience/segmenti con le soluzioni Adobe Experience Cloud e i servizi di base. Richiede IMS. <a href="../../integrations/using/sharing-audiences-with-adobe-experience-cloud.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing<br /> </td> 
  </tr> 
  <tr> 
   <td> Integrazione con Adobe Marketing Cloud<br /> </td> 
   <td> Consente di importare ed esportare audience/segmenti da diverse soluzioni Adobe Marketing Cloud in  Adobe Campaign. Facoltativo. <a href="../../integrations/using/configuring-ims.md#installing-the-package">Ulteriori informazioni</a> </td> 
   <td> Marketing</td> 
  </tr> 
  <tr> 
   <td> Regolamento sulla protezione dei dati sulla privacy<br /> </td> 
   <td> Contiene funzionalità aggiuntive per agevolare la conformità alla privacy in Campaign Classic. <a href="https://helpx.adobe.com/it/campaign/kb/acc-privacy.html">Ulteriori informazioni</a> <br /> </td> 
   <td> Tutto</td> 
  </tr> 
  <tr> 
   <td> Transfer to Mid-Sourcing <br /> </td> 
   <td> Consente di specificare l'installazione e la configurazione di un server mid-sourcing, nonché la distribuzione di un'istanza che consente a terzi di inviare messaggi in modalità mid-sourcing. Facoltativo. <a href="../../installation/using/mid-sourcing-server.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
  <tr> 
   <td> Piattaforma di mid-sourcing<br /> </td> 
   <td> Questa configurazione è una soluzione intermedia ottimale tra una configurazione in hosting (ASP) e l'internalizzazione. I componenti di esecuzione rivolti all’esterno vengono eseguiti su un server di "mid-sourcing" ospitato  Adobe Campaign. Facoltativo. <a href="../../installation/using/mid-sourcing-server.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Media-sourcing </td> 
  </tr> 
  <tr> 
   <td> Connettore ACS<br /> </td> 
   <td> Ponti  Adobe Campaign v7 e  Adobe Campaign Standard. Si tratta di una funzione integrata in Campaign v7 che replica automaticamente i dati ai Campaign Standard, unendo il meglio di entrambe le applicazioni. Facoltativo. <a href="../../integrations/using/acs-connector-principles-and-data-cycle.md">Ulteriori informazioni</a> <br /> </td> 
   <td> Marketing </td> 
  </tr> 
 </tbody> 
</table>

### Pacchetto Message Center {#message-center-package}

Devi installare canali di distribuzione (E-mail, Canale mobile, Canale app mobile, ecc.) prima di installare i messaggi transazionali (pacchetto del centro messaggi). Se hai avviato un progetto di Centro messaggi e-mail e devi successivamente aggiungere un nuovo canale, devi seguire la procedura seguente:

1. Installate il nuovo canale, ad esempio il canale **** Mobile, utilizzando la procedura guidata di importazione del pacchetto ( **[!UICONTROL Tools > Advanced > Import package > Adobe Campaign package]**).
1. Importa il file ( **[!UICONTROL Tools > Advanced > Import package > File]**), quindi seleziona:

   ```
   \datakit\nms\[Your language]\package\messageCenter.xml
   ```

1. In **[!UICONTROL XML data content to import]**, mantenere solo il modello di consegna del Centro messaggi corrispondente al canale correlato. Ad esempio, se hai aggiunto il canale **** Mobile, tieni solo l’elemento **entità** corrispondente al modello **[!UICONTROL Mobile transactional message]** (smsTriggerMessage). Se hai aggiunto **Mobile App Channel**, mantieni solo i modelli di messaggi **transazionali** iOS (iosTriggerMessage) e i messaggi **transazionali** Android (androidTriggerMessage).

   ![](assets/messagecenter_install_channel.png)

>[!CAUTION]
>
>I modelli di consegna del Centro messaggi per LINE non saranno disponibili se i pacchetti del Centro messaggi sono installati prima di LINE

