---
solution: Campaign Classic
product: campaign
title: Configurazione del server Campaign
description: Configurazione del server Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
translation-type: tm+mt
source-git-commit: 0c83c989c7e3718a989a4943f5cde7ad4717fddc
workflow-type: tm+mt
source-wordcount: '2810'
ht-degree: 6%

---

# Configurazione del server Campaign{#configuring-campaign-server}

La sezione seguente descrive le configurazioni lato server che possono essere eseguite in base alle tue esigenze e alle specificità dell’ambiente.

Queste configurazioni devono essere eseguite dagli amministratori e solo per i modelli di hosting **On-Premise** .

Per le distribuzioni **in hosting**, le impostazioni lato server possono essere configurate solo per Adobe. Tuttavia, alcune impostazioni possono essere configurate all&#39;interno del Pannello di controllo Campaign (ad esempio, gestione degli inserire nell&#39;elenco Consentiti IP o autorizzazioni URL).

>[!NOTE]
>
>Il Pannello di controllo Campaign è accessibile a tutti gli utenti amministratori. I passaggi per concedere all’amministratore l’accesso a un utente sono descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).
>
>Tieni presente che l’istanza deve essere ospitata su AWS e aggiornata con la build [Gold Standard](../../rn/using/gs-overview.md) più recente o con la build [GA più recente (21.1)](../../rn/using/latest-release.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Per verificare se l&#39;istanza è ospitata su AWS, segui i passaggi descritti in [questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

Per ulteriori informazioni, consulta queste sezioni:

* [Documentazione del Pannello di controllo Campaign](https://docs.adobe.com/content/help/it-IT/control-panel/using/control-panel-home.html)
* [Modelli di hosting](../../installation/using/hosting-models.md)
* [Matrice di funzionalità Campaign Classic on-premise e in hosting](../../installation/using/capability-matrix.md)
* [Passaggi per la configurazione dei modelli ibridi ed in hosting](../../installation/using/hosting-models.md)

I file di configurazione di Campaign Classic sono memorizzati nella cartella **conf** della cartella di installazione di Adobe Campaign. La configurazione viene suddivisa in due file:

* **serverConf.xml**: configurazione generale per tutte le istanze. Questo file combina i parametri tecnici del server Adobe Campaign: sono condivisi da tutte le istanze. La descrizione di alcuni di questi parametri è illustrata di seguito. I diversi nodi e parametri ed elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml**  (dove  **** istanza è il nome dell&#39;istanza): configurazione specifica dell’istanza. Se condividi il server tra più istanze, inserisci i parametri specifici di ciascuna istanza nel relativo file.

## Configurazione di Tomcat {#configuring-tomcat}

### Porta predefinita per Tomcat {#default-port-for-tomcat}

Quando la porta di ascolto 8080 del server Tomcat è già occupata con un&#39;altra applicazione necessaria per la configurazione, è necessario sostituire la porta 8080 con una gratuita (ad esempio 8090). Per modificarlo, modifica il file **server.xml** salvato nella directory **/tomcat-8/conf** della cartella di installazione di Adobe Campaign.

Quindi modifica la porta delle pagine relay JSP. A questo scopo, modifica il file **serverConf.xml** salvato nella directory **/conf** della directory di installazione di Adobe Campaign. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Mappatura di una cartella in Tomcat {#mapping-a-folder-in-tomcat}

Per definire le impostazioni specifiche del cliente, è possibile creare un file **user_contexts.xml** nella cartella **/tomcat-8/conf**, che contiene anche il file **contexts.xml**.

Questo file conterrà il seguente tipo di informazioni:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessario, questa operazione può essere riprodotta sul lato server.

## Personalizzazione dei parametri di consegna {#personalizing-delivery-parameters}

I parametri di consegna sono definiti nel file di configurazione **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

La configurazione e i comandi generali del server sono descritti in [Configurazione del server Campaign](../../installation/using/campaign-server-configuration.md).

Puoi anche eseguire le seguenti configurazioni in base alle tue esigenze e impostazioni.

### relè SMTP {#smtp-relay}

Il modulo MTA agisce come agente nativo di trasferimento della posta per la trasmissione SMTP (porta 25).

È tuttavia possibile sostituirlo con un server relay se richiesto dal criterio di sicurezza. In tal caso, il throughput globale sarà quello relay (purché il throughput del server relay sia inferiore a quello di Adobe Campaign).

In questo caso, questi parametri vengono impostati configurando il server SMTP nella sezione **`<relay>`** . È necessario specificare l’indirizzo IP (o l’host) del server SMTP utilizzato per trasferire la posta e la relativa porta associata (25 per impostazione predefinita).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Questa modalità operativa implica gravi limitazioni delle consegne, in quanto può ridurre notevolmente il throughput a causa delle prestazioni intrinseche del server relay (latenza, larghezza di banda...). Inoltre, la capacità di qualificare gli errori di consegna sincroni (rilevati analizzando il traffico SMTP) sarà limitata e l’invio non sarà possibile se il server relay non è disponibile.

### Processi figlio MTA {#mta-child-processes}

È possibile controllare la popolazione dei processi figlio (maxSpareServers per impostazione predefinita 2) al fine di ottimizzare le prestazioni di trasmissione in base alla potenza della CPU dei server e alle risorse di rete disponibili. Questa configurazione deve essere effettuata nella sezione **`<master>`** della configurazione MTA su ogni singolo computer.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Consulta anche [Ottimizzazione dell&#39;invio di e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

### Gestione del traffico SMTP in uscita con affinità {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configurazione dell&#39;affinità deve essere coerente da un server all&#39;altro. È consigliabile contattare l’Adobe per la configurazione dell’affinità, in quanto le modifiche di configurazione devono essere replicate su tutti i server applicativi che eseguono l’MTA.

Puoi migliorare il traffico SMTP in uscita tramite affinità con indirizzi IP.

A questo scopo, esegui i seguenti passaggi:

1. Immetti le affinità nella sezione **`<ipaffinity>`** del file **serverConf.xml**.

   Un&#39;affinità può avere diversi nomi diversi: per separarli, utilizzare il carattere **;**.

   Esempio:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Per visualizzare i parametri rilevanti, fai riferimento al file **serverConf.xml** .

1. Per abilitare la selezione di affinità negli elenchi a discesa, devi aggiungere i nomi di affinità nell&#39;enumerazione **IPAffinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Le enumerazioni sono descritte in [questo documento](../../platform/using/managing-enumerations.md).

   Puoi quindi selezionare l’affinità da utilizzare, come mostrato di seguito per le tipologie:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Puoi anche fare riferimento a [Configurazione del server di consegna](../../installation/using/email-deliverability.md#delivery-server-configuration).

## Autorizzazioni URL {#url-permissions}

L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) dalle istanze Campaign Classic è limitato. Si tratta di URL che consentono il corretto funzionamento delle istanze.

Per impostazione predefinita, le istanze non possono connettersi a URL esterni. Tuttavia, è possibile aggiungere alcuni URL esterni all’elenco degli URL autorizzati, in modo che l’istanza possa connettersi ad essi. Questo consente di connettere le istanze Campaign a sistemi esterni, ad esempio server SFTP o siti Web, per abilitare il trasferimento di file e/o dati.

Una volta aggiunto l’URL, viene inserito un suo riferimento nel file di configurazione dell’istanza (serverConf.xml).

Il modo in cui puoi gestire le autorizzazioni URL dipende dal modello di hosting:

* **** Hybridor  **on-premise**: aggiungi gli URL da consentire nel file  **serverConf.xml**. Informazioni dettagliate sono disponibili nella sezione seguente.
* **Ospitato**: aggiungi gli URL da consentire tramite il  **Pannello di controllo Campaign**. Per ulteriori informazioni, consulta la [documentazione dedicata](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html).

   >[!NOTE]
   >
   >Il Pannello di controllo Campaign è accessibile a tutti gli utenti amministratori. I passaggi per concedere all’amministratore l’accesso a un utente sono descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=en#discover-control-panel).
   >
   >Tieni presente che l’istanza deve essere ospitata su AWS e aggiornata con la build [Gold Standard](../../rn/using/gs-overview.md) più recente. Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version). Per verificare se l&#39;istanza è ospitata su AWS, segui i passaggi descritti in [questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).

Con i modelli di hosting **Hybrid** e **On-Premise**, l&#39;amministratore deve fare riferimento a un nuovo **urlPermission** nel file **serverConf.xml**. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Esistono tre modalità di protezione della connessione:

* **Blocco**: tutti gli URL che non appartengono all&#39;inserire nell&#39;elenco Consentiti vengono bloccati, con un messaggio di errore. Questa è la modalità predefinita dopo un aggiornamento successivo.
* **Permissivo**: tutti gli URL che non appartengono all’inserire nell&#39;elenco Consentiti sono consentiti.
* **Avviso**: tutti gli URL che non appartengono all’inserire nell&#39;elenco Consentiti sono consentiti, ma l’interprete JS emette un avviso in modo che l’amministratore possa raccoglierli. Questa modalità aggiunge messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Per impostazione predefinita, il client dei nuovi clienti utilizza la modalità di blocco **a1/>.** Se devono consentire l’accesso a un nuovo URL, devono contattare il proprio amministratore per aggiungerlo all’inserire nell&#39;elenco Consentiti.
>
>I clienti esistenti provenienti da una migrazione possono utilizzare per un po’ la modalità di avviso **a1/> .** Nel frattempo, devono analizzare il traffico in uscita prima di autorizzare gli URL. Una volta definito l’elenco degli URL autorizzati, è necessario contattare il proprio amministratore per aggiungere gli URL all’inserire nell&#39;elenco Consentiti e attivare la **modalità di blocco**.

## Sicurezza delle pagine dinamiche e relè {#dynamic-page-security-and-relays}

Per impostazione predefinita, tutte le pagine dinamiche sono automaticamente correlate al server **locale** Tomcat del computer di cui è stato avviato il modulo Web. Questa configurazione viene immessa nella sezione **`<url>`** della configurazione del relay query per il file **ServerConf.xml**. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Per inoltrare l&#39;esecuzione della pagina dinamica su un server **remoto**; se il modulo Web non è attivato nel computer. A questo scopo, è necessario sostituire **localhost** con il nome del computer remoto per JSP e JSSP, applicazioni Web, rapporti e stringhe.

Per ulteriori informazioni sui vari parametri disponibili, consulta il file di configurazione **serverConf.xml** .

Per le pagine JSP, la configurazione predefinita è:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign utilizza le seguenti pagine JSP:

* /nl/jsp/**soaprouter.jsp**: connessioni a console client e servizi Web (API SOAP),
* /nl/jsp/**m.jsp**: pagine mirror,
* /nl/jsp/**logon.jsp**: accesso basato sul web ai rapporti e alla distribuzione della console client,
* /nl/jsp/**s.jsp** : Utilizzo del marketing virale (sponsorizzazione e social network).

I JSSP utilizzati per il canale app mobile sono i seguenti:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Esempio:**

È possibile impedire le connessioni dei computer client dall&#39;esterno. A tal fine, limita l&#39;esecuzione di **soaprouter.jsp** e autorizza solo l&#39;esecuzione di pagine mirror, collegamenti virali, moduli web e risorse pubbliche.

I parametri sono i seguenti:

```
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask="<IP_addresses>" deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/> 
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="m.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="s.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true" relayPath="true" targetUrl="http://localhost:8080" timeout="" urlPath="webForm.jsp"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/webApp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/jssp/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/strings/pub*"/>
<url IPMask=""               deny=""     hostMask="" relayHost="true"  relayPath="true"  targetUrl="http://localhost:8080" timeout="" urlPath="/interaction/pub*"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jsp"/>
<url IPMask=""               deny="true" hostMask="" relayHost="false" relayPath="false" targetUrl="http://localhost:8080" timeout="" urlPath="*.jssp"/>
```

In questo esempio, il valore **`<IP_addresses>`** coincide con l’elenco di indirizzi IP (separati da virgole) autorizzati a utilizzare il modulo relay per questa maschera.

>[!NOTE]
>
>I valori devono essere adattati in base alla configurazione e ai vincoli di rete, specialmente se sono state sviluppate configurazioni specifiche per l&#39;installazione.

## Limitazione dei comandi esterni autorizzati {#restricting-authorized-external-commands}

>[!NOTE]
>
>La configurazione seguente è necessaria solo per le installazioni on-premise.

Dalla build 8780, gli amministratori tecnici possono limitare l’elenco dei comandi esterni autorizzati che possono essere utilizzati in Adobe Campaign.

A questo scopo, è necessario creare un file di testo con l&#39;elenco dei comandi che si desidera impedire di utilizzare, ad esempio:

```
ln
dd
openssl
curl
wget
python
python3
perl
ruby
sh
```

>[!IMPORTANT]
>
>Questo elenco non è esaustivo.

Nel nodo **exec** del file di configurazione del server, è necessario fare riferimento al file creato in precedenza nell&#39;attributo **blacklistFile** .

**Solo** per Linux: nel file di configurazione del server, si consiglia di specificare un utente dedicato all&#39;esecuzione di comandi esterni per migliorare la configurazione di sicurezza. Questo utente è impostato nel nodo **exec** del file di configurazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Se non viene specificato alcun utente, tutti i comandi vengono eseguiti nel contesto utente dell’istanza di Adobe Campaign. L’utente deve essere diverso dall’utente che esegue Adobe Campaign.

Ad esempio:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Questo utente deve essere aggiunto all’elenco secondario dell’operatore Adobe Campaign &quot;neolane&quot;.

>[!IMPORTANT]
>
>Non utilizzare uno sudo personalizzato. Sul sistema deve essere installato uno sudo standard.

## Gestione delle intestazioni HTTP {#managing-http-headers}

Per impostazione predefinita, tutte le intestazioni HTTP non vengono trasmesse. È possibile aggiungere intestazioni specifiche nelle risposte inviate tramite relay. Per eseguire questa operazione:

1. Vai al file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).
1. Nel nodo **`<relay>`**, vai all&#39;elenco delle intestazioni HTTP inoltrate.
1. Aggiungi un elemento **`<responseheader>`** con i seguenti attributi:

   * **nome**: nome intestazione
   * **valore**: nome del valore.

   Ad esempio:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Tracciamento ridondante {#redundant-tracking}

Quando per il reindirizzamento vengono utilizzati più server, questi devono essere in grado di comunicare tra loro tramite chiamate SOAP per condividere informazioni dagli URL da reindirizzare. Al momento dell&#39;avvio della consegna, è possibile che non tutti i server di reindirizzamento siano disponibili; pertanto potrebbero non avere lo stesso livello di informazioni.

>[!NOTE]
>
>Quando si utilizza l&#39;architettura standard o Enterprise, il server applicazioni principale deve essere autorizzato a caricare le informazioni di tracciamento su ogni computer.

Gli URL dei server ridondanti devono essere specificati nella configurazione di reindirizzamento tramite il file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

**Esempio:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

La proprietà **enableIf** è facoltativa (vuota per impostazione predefinita) e consente di abilitare la connessione solo se il risultato è vero; Ciò ti consente di ottenere una configurazione identica su tutti i server di reindirizzamento.

Per ottenere il nome host del computer, eseguire il comando seguente: **hostname -s**.

## Gestione delle risorse pubbliche {#managing-public-resources}

Le risorse pubbliche sono presentate in [Gestione delle risorse pubbliche](../../installation/using/deploying-an-instance.md#managing-public-resources).

Sono memorizzati nella directory **/var/res/instance** della directory di installazione di Adobe Campaign.

L’URL corrispondente è: **http://server/res/instance** dove **instance** è il nome dell&#39;istanza di tracciamento.

È possibile specificare un&#39;altra directory aggiungendo un nodo al file **conf-`<instance>`.xml** per configurare la memorizzazione sul server. Questo significa aggiungere le seguenti righe:

```
<serverconf>
  <shared>
    <dataStore hosts="media*" lang="fra">
      <virtualDir name="images" path="/var/www/images"/>
     <virtualDir name="publicFileRes" path="$(XTK_INSTALL_DIR)/var/res/$(INSTANCE_NAME)/"/>
    </dataStore>
  </shared>
</serverconf>
```

In questo caso, il nuovo URL per le risorse pubbliche indicato nella parte superiore della finestra della procedura guidata di distribuzione deve puntare a questa cartella.

## Flussi di lavoro e affinità ad alta disponibilità {#high-availability-workflows-and-affinities}

È possibile configurare diversi server del flusso di lavoro (wfserver) e distribuirli su due o più computer. Se scegli questo tipo di architettura, configura la modalità di connessione dei load balancer in base all’accesso Adobe Campaign.

Per l&#39;accesso dal web, seleziona la modalità **load balancer** per limitare i tempi di connessione.

Se accedi tramite la console Adobe Campaign, scegli la modalità **hash** o **ip fisso** . Ciò consente di mantenere la connessione tra il client avanzato e il server e di impedire l’interruzione di una sessione utente durante un’operazione di importazione o esportazione, ad esempio.

Puoi scegliere di forzare l’esecuzione di un flusso di lavoro o di un’attività del flusso di lavoro su un determinato computer. A questo scopo, devi definire una o più affinità per il flusso di lavoro o l’attività interessata.

1. Crea le affinità del flusso di lavoro o dell’attività inserendole nel campo **[!UICONTROL Affinity]** .

   Puoi scegliere liberamente i nomi di affinità. Tuttavia, assicurarsi di non utilizzare spazi o segni di punteggiatura. Se si utilizzano server diversi, specificare nomi diversi.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   L&#39;elenco a discesa contiene affinità precedentemente utilizzate. Viene completato nel tempo con i diversi valori immessi.

1. Apri il file **nl6/conf/config-`<instance>.xml`** .
1. Modifica la linea che corrisponde al modulo **[!UICONTROL wfserver]** come segue:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Se definisci diverse affinità, queste devono essere separate da virgole senza spazi:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   La virgola che segue il nome dell’affinità è necessaria per l’esecuzione dei flussi di lavoro per i quali non è definita alcuna affinità.

   Se desideri eseguire solo flussi di lavoro per i quali è definita un’affinità, non aggiungere una virgola alla fine dell’elenco delle affinità. Ad esempio, modificare la linea come segue:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Riavvio automatico del processo {#automatic-process-restart}

Per impostazione predefinita, i diversi processi di Adobe Campaign vengono riavviati automaticamente alle 6 del mattino (ora del server) ogni giorno.

Tuttavia, puoi modificare questa configurazione.

A questo scopo, accedi al file **serverConf.xml**, che si trova nel **repository** dell&#39;installazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Ogni processo configurato in questo file ha un attributo **processRestartTime** . Puoi modificare il valore di questo attributo per adattare il tempo di riavvio di ogni processo in base alle tue esigenze.

>[!IMPORTANT]
>
>Non eliminare questo attributo. Tutti i processi devono essere riavviati ogni giorno.

## Limitazione dei file caricabili {#limiting-uploadable-files}

Un nuovo attributo **uploadWhiteList** consente di limitare i tipi di file disponibili per il caricamento sul server Adobe Campaign.

Questo attributo è disponibile all&#39;interno dell&#39;elemento **dataStore** del file **serverConf.xml**. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Il valore predefinito di questo attributo è **.+** e consente di caricare qualsiasi tipo di file.

Per limitare i formati possibili, devi sostituire il valore dell&#39;attributo con un&#39;espressione regolare java valida. È possibile immettere diversi valori separandoli con una virgola.

Ad esempio: **uploadWhiteList=&quot;.*.png,.*.jpg&quot;** consente di caricare i formati PNG e JPG sul server. Non verranno accettati altri formati.

>[!IMPORTANT]
>
>In Internet Explorer, il percorso completo del file deve essere verificato dall&#39;espressione regolare.

## Configurazione della connessione proxy {#proxy-connection-configuration}

Puoi collegare il server Campaign a un sistema esterno tramite un proxy, ad esempio utilizzando un’attività del flusso di lavoro **Trasferimento file**. A questo scopo, devi configurare la sezione **proxyConfig** del file **serverConf.xml** tramite un comando specifico. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Sono possibili le seguenti connessioni proxy: HTTP, HTTPS, FTP, SFTP. A partire dalla versione 20.2 di Campaign, i parametri del protocollo HTTP e HTTPS sono **non più disponibili**. Tali parametri sono ancora indicati di seguito in quanto rimangono disponibili nelle build precedenti, tra cui 9032.

>[!CAUTION]
>
>È supportata solo la modalità di autenticazione di base. Autenticazione NTLM non supportata.
>
>I proxy SOCKS non sono supportati.


È possibile utilizzare il comando seguente:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

i parametri del protocollo possono essere &quot;http&quot;, &quot;https&quot; o &quot;ftp&quot;.

Se imposti FTP sulla stessa porta del traffico HTTP/HTTPS, puoi utilizzare quanto segue:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Le opzioni &quot;http&quot; e &quot;https&quot; vengono utilizzate solo quando il parametro del protocollo è &quot;ftp&quot; e indicano se il tunneling sulla porta specificata verrà eseguito su HTTPS o su HTTP.

Se utilizzi porte diverse per il traffico FTP/SFTP e HTTP/HTTPS sul server proxy, devi impostare il parametro del protocollo &quot;ftp&quot;.


Ad esempio:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Quindi inserisci la password.

Le connessioni HTTP sono definite nel parametro proxyHTTP:

```
<proxyConfig enabled=“1” override=“localhost*” useSingleProxy=“0”>
<proxyHTTP address=“198.51.100.0" login=“user” password=“*******” port=“8080”/>
</proxyConfig>
```

Le connessioni HTTPS sono definite nel parametro proxyHTTPS:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyHTTPS address=“198.51.100.0” login=“user” password=“******” port=“8080"/>
</proxyConfig>
```

Le connessioni FTP/FTPS sono definite nel parametro proxyFTP:

```
<proxyConfig enabled=“1" override=“localhost*” useSingleProxy=“0">
<proxyFTP address=“198.51.100.0” login=“user” password=“******” port=“5555" https=”true”/>
</proxyConfig>
```

Se si utilizza lo stesso proxy per diversi tipi di connessione, verrà definito solo il proxyHTTP con useSingleProxy impostato su &quot;1&quot; o &quot;true&quot;.

Se disponi di connessioni interne che devono passare attraverso il proxy, aggiungili nel parametro override.

Se desideri disattivare temporaneamente la connessione proxy, imposta il parametro abilitato su &quot;false&quot; o &quot;0&quot;.
