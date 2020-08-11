---
title: Configurazione del server Campaign
seo-title: Configurazione del server Campaign
description: Configurazione del server Campaign
seo-description: null
page-status-flag: never-activated
uuid: be21ae4b-ca2a-4952-b256-cd8dc51309cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 1a94c94e-ab6b-45c2-a0f3-6adeec7e2d2d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc54cef4c44be4c694e062f56685dbb09d2fcf8e
workflow-type: tm+mt
source-wordcount: '3593'
ht-degree: 3%

---


# Configurazione del server Campaign{#configuring-campaign-server}

La sezione seguente descrive le configurazioni lato server che possono essere eseguite in base alle esigenze e alle specifiche dell&#39;ambiente.

>[!IMPORTANT]
>
>Queste configurazioni devono essere eseguite dagli amministratori e solo per i modelli di hosting **locali** .
>
>Per le distribuzioni **ospitate** , le impostazioni lato server possono essere configurate solo  Adobe. Tuttavia, alcune impostazioni possono essere configurate all&#39;interno del Pannello di controllo Campaign (ad esempio, gestione di elenchi consentiti  IP o autorizzazioni URL).

Per ulteriori informazioni, consultare le sezioni seguenti:

* [Documentazione del Pannello di controllo Campaign](https://docs.adobe.com/content/help/it-IT/control-panel/using/control-panel-home.html)
* [Modelli di hosting](../../installation/using/hosting-models.md)
* [Matrice di funzionalità Campaign Classic locale e ospitata](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)
* [Procedura](../../installation/using/about-hybrid-and-hosted-models.md) di configurazione per modelli ibridi ed ospitati )

I file di configurazione Campaign Classic sono memorizzati nella cartella **conf** della cartella di installazione Adobe Campaign . La configurazione è suddivisa in due file:

* **serverConf.xml**: configurazione generale per tutte le istanze. Questo file combina i parametri tecnici del server Adobe Campaign : vengono condivisi da tutte le istanze. La descrizione di alcuni di questi parametri è dettagliata di seguito. I diversi nodi e parametri ed elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (dove **instance** è il nome dell’istanza): specifica configurazione dell&#39;istanza. Se condividete il server tra più istanze, inserite i parametri specifici per ciascuna istanza nel relativo file.

## Definizione delle aree di protezione {#defining-security-zones}

### Informazioni sulle aree di protezione {#about-security-zones}

Ogni operatore deve essere collegato a una zona per accedere a un&#39;istanza e l&#39;IP dell&#39;operatore deve essere incluso negli indirizzi o nei set di indirizzi definiti nella zona di sicurezza. La configurazione dell&#39;area di protezione viene eseguita nel file di configurazione del server Adobe Campaign .

Gli operatori sono collegati a una zona di protezione dal relativo profilo nella console ( **[!UICONTROL Administration > Access management > Operators]** nodo). Scopri come collegare le aree agli operatori della campagna in [questa sezione](#linking-a-security-zone-to-an-operator).

### Creazione di aree di protezione {#creating-security-zones}

Una zona è definita da:

* uno o più intervalli di indirizzi IP (IPv4 e IPv6)
* un nome tecnico collegato a ciascun intervallo di indirizzi IP

Le aree di sicurezza sono interbloccate, il che significa che la definizione di una nuova zona all&#39;interno di un&#39;altra area riduce il numero di operatori che possono accedervi aumentando al contempo i diritti assegnati a ciascun operatore.

Le aree devono essere definite durante la configurazione del server, nel file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Ogni area definisce i diritti, ad esempio:

* Connessione HTTP anziché HTTPS
* Visualizzazione degli errori (errori Java, JavaScript, C++, ecc.)
* Report e anteprima webApp
* Autenticazione tramite login/password
* Modalità di connessione non sicura

>[!NOTE]
>
>**Ogni operatore deve essere collegato a una zona**. Se l&#39;indirizzo IP dell&#39;operatore appartiene all&#39;intervallo definito dalla zona, l&#39;operatore può accedere all&#39;istanza.\
>L&#39;indirizzo IP dell&#39;operatore può essere definito in più zone. In questo caso, l&#39;operatore riceve l&#39; **insieme** di diritti disponibili per ogni area.

Il file **serverConf.xml** out-of-the-box include tre aree: **public, VPN e LAN**.

>[!NOTE]
>
>**La configurazione out-of-the-box è sicura**. Tuttavia, prima di eseguire la migrazione da una versione precedente di  Adobe Campaign, potrebbe essere necessario ridurre temporaneamente la sicurezza per migrare e approvare le nuove regole.

Esempio di come definire una zona nel file **serverConf.xml** :

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" name="public">
<subNetwork label="All addresses" mask="*" name="all"/>

<securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)"
              name="vpn" showErrors="true">

  <securityZone allowDebug="true" allowEmptyPassword="true" allowHTTP="true"
                allowUserPassword="false" label="Private Network (LAN)" name="lan"
                sessionTokenOnly="true" showErrors="true">
    <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
    <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
    <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
    <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
    <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
    <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  </securityZone>

</securityZone>
</securityZone>
```

Tutti i diritti che definiscono una zona sono i seguenti:

* **allowDebug**: consente l&#39;esecuzione di un&#39;app Web in modalità &quot;debug&quot;
* **allowEmptyPassword**: autorizza una connessione a un&#39;istanza senza una password
* **allowHTTP**: è possibile creare una sessione senza utilizzare il protocollo HTTPS
* **allowUserPassword**: il token di sessione può avere il seguente modulo &quot;`<login>/<password>`&quot;
* **sessionTokenOnly**: il token di protezione non è richiesto nell&#39;URL di connessione
* **showErrors**: gli errori sul lato server vengono inoltrati e visualizzati

>[!IMPORTANT]
>
>Nella definizione di un&#39;area, ogni attributo con il valore **true** riduce la protezione.

Quando si utilizza Centro messaggi, se sono presenti più istanze di esecuzione, è necessario creare un&#39;area di protezione aggiuntiva con l&#39;attributo **sessionTokenOnly** definito come **true**, in cui devono essere aggiunti solo gli indirizzi IP necessari. Per ulteriori informazioni sulla configurazione delle istanze, consultare [questo documento](../../message-center/using/creating-a-shared-connection.md).

### Best practice per le zone di sicurezza {#best-practices-for-security-zones}

Nella definizione della zona di sicurezza del **piano** , è possibile aggiungere una maschera di indirizzo IP che definisca l&#39;accesso tecnico. Questo componente aggiuntivo consente l&#39;accesso a tutte le istanze ospitate sul server.

```
<securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true"
                    allowUserPassword="false" label="Private Network (LAN)" name="lan"
                    sessionTokenOnly="true" showErrors="true">
        <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1"/>
        <subNetwork label="Lan 2" mask="172.16.0.0/12" name="lan2"/>
        <subNetwork label="Lan 3" mask="10.0.0.0/8" name="lan3"/>
        <subNetwork label="Localhost" mask="127.0.0.1/16" name="locahost"/>
        <subNetwork label="Lan (IPv6)" mask="fc00::/7" name="lan6"/>
        <subNetwork label="Localhost (IPv6)" mask="::1/128" name="localhost6"/>
  
        <!-- Customer internal IPs -->
        <subNetwork id="internalNetwork" mask="a.b.c.d/xx"/>

      </securityZone>
```

È consigliabile definire gli intervalli di indirizzi IP direttamente nel file di configurazione dedicato all&#39;istanza per gli operatori che accedono solo a un&#39;istanza specifica.

Nel **`config-<instance>.xml`** file:

```
  <securityZone name="public">
   ...
    <securityZone name="vpn">
      <subNetwork id="cus1" mask="a.b.c.d/xx"/>
```

### Reti secondarie e proxy in una zona di sicurezza {#sub-networks-and-proxies-in-a-security-zone}

Il parametro **proxy** può essere utilizzato in un elemento **subNetwork** per specificare l&#39;uso del proxy in una zona di sicurezza.

Quando si fa riferimento a un proxy e una connessione entra tramite questo proxy (visibile tramite l&#39;intestazione HTTP X-Forwarded-For), la zona verificata è quella dei client del proxy e non quella del proxy.

>[!IMPORTANT]
>
>Se un proxy è configurato e può essere ignorato (o se non esiste), l&#39;indirizzo IP che verrà testato sarà in grado di essere falsificato.
>
>Inoltre, i relè ora vengono generati come proxy. È quindi possibile aggiungere l&#39;indirizzo IP 127.0.0.1 all&#39;elenco dei proxy nella configurazione della zona di sicurezza.
>
>Ad esempio: &quot; `<subnetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" proxy="127.0.0.1,10.100.2.135" />`&quot;.

Possono verificarsi diversi casi:

* Nella zona di protezione viene fatto riferimento direttamente a una sub-rete e non è configurato alcun proxy: gli utenti della rete secondaria possono connettersi direttamente al server Adobe Campaign .

   ![](assets/8101_proxy1.png)

* È specificato un proxy per una rete secondaria nella zona di sicurezza: gli utenti di questa sub-rete possono accedere al server Adobe Campaign  tramite questo proxy.

   ![](assets/8101_proxy2.png)

* Un proxy è incluso in una rete secondaria della zona di sicurezza: gli utenti che hanno accesso tramite questo proxy, indipendentemente dalla loro origine, possono accedere al server Adobe Campaign .

   ![](assets/8101_proxy3.png)

Gli indirizzi IP dei proxy che possono accedere al server Adobe Campaign  devono essere inseriti sia nella **`<subnetwork>`** relativa rete secondaria che nella sottorete di primo livello **`<subnetwork name="all"/>`**. Ad esempio, qui per un proxy il cui indirizzo IP è 10.131.146.102:

```
<securityZone allowDebug="false" allowHTTP="false" label="Public Network" 
                      name="public">
    <subNetwork label="All addresses" mask="*" name="all"
                      proxy="10.131.146.102,127.0.0.1, ::1"/>

    <securityZone allowDebug="true" allowHTTP="false" label="Private Network (VPN)" 
                      name="vpn" showErrors="true">
        <securityZone allowDebug="true" allowEmptyPassword="false" allowHTTP="true" 
                      allowUserPassword="false" label="Private Network (LAN)" 
                      name="lan" sessionTokenOnly="true" showErrors="true">
            <subNetwork label="Lan proxy" mask="10.131.193.182" name="lan3" 
                      proxy="10.131.146.102,127.0.0.1, ::1"/>
            <subNetwork label="Lan 1" mask="192.168.0.0/16" name="lan1" 
                      proxy="127.0.0.1, ::1"/>

        </securityZone>
    </securityZone>
</securityZone>
```

### Collegamento di un’area di sicurezza a un operatore {#linking-a-security-zone-to-an-operator}

Una volta definite le zone, ogni operatore deve essere collegato a uno di essi per poter accedere a un&#39;istanza e l&#39;indirizzo IP dell&#39;operatore deve essere incluso negli indirizzi o nell&#39;intervallo di indirizzi a cui si fa riferimento nella zona.

La configurazione tecnica delle zone viene eseguita nel file di configurazione del server Campaign: **serverConf.xml**.

Prima di questo, è necessario iniziare configurando l&#39; **[!UICONTROL Security zone]** enumerazione out-of-the-box per collegare un&#39;etichetta al nome interno della zona definita nel file **serverConf.xml** .

Questa configurazione viene effettuata in Campaign Explorer:

1. Fare clic sul **[!UICONTROL Administration > Platform > Enumerations]** nodo.
1. Selezionare l&#39;enumerazione del **[!UICONTROL Security zone (securityZone)]** sistema.

   ![](assets/enum_securityzone.png)

1. Per ogni area di protezione definita nel file di configurazione del server, fare clic sul **[!UICONTROL Add]** pulsante.
1. Nel **[!UICONTROL Internal name]** campo, immettere il nome della zona definita nel file **serverConf.xml** . Corrisponde all&#39;attributo **@name** dell&#39; `<securityzone>` elemento. Immettere l&#39;etichetta collegata al nome interno nel campo **** Etichetta.

   ![](assets/enum_addsecurityvalue.png)

1. Fate clic su OK e salvate le modifiche.

Una volta definite le zone e configurata l&#39; **[!UICONTROL Security zone]** enumerazione, è necessario collegare ogni operatore a un&#39;area di protezione:

1. Fare clic sul **[!UICONTROL Administration > Access management > Operators]** nodo.
1. Selezionare l&#39;operatore a cui si desidera collegare un&#39;area di protezione e fare clic sulla **[!UICONTROL Edit]** scheda.
1. Vai alla **[!UICONTROL Access rights]** scheda e fai clic sul **[!UICONTROL Edit access parameters...]** collegamento.

   ![](assets/zone_operator.png)

1. Selezionare una zona dall&#39;elenco a **[!UICONTROL Authorized connection zone]** discesa

   ![](assets/zone_operator_selection.png)

1. Fate clic su **[!UICONTROL OK]** e salvate le modifiche per applicare le modifiche.

## Configurazione di Tomcat {#configuring-tomcat}

### Porta predefinita per Tomcat {#default-port-for-tomcat}

Quando la porta di ascolto 8080 del server Tomcat è già occupata con un&#39;altra applicazione necessaria per la configurazione, è necessario sostituire la porta 8080 con una gratuita (ad esempio 8090). Per modificarlo, modificate il file **server.xml** salvato nella directory **/tomcat-7/conf** della cartella di installazione di Adobe Campaign .

Quindi modificate la porta delle pagine dei relè JSP. A questo scopo, modificate il file **serverConf.xml** salvato nella directory **/conf** della directory di installazione di Adobe Campaign . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

```
<serverConf>
   ...
   <web controlPort="8005" httpPort="8090"...
   <url ... targetUrl="http://localhost:8090"...
```

### Mapping di una cartella in Tomcat {#mapping-a-folder-in-tomcat}

Per definire le impostazioni specifiche per il cliente, potete creare un file **user_contexts.xml** nella cartella **/tomcat-7/conf** , che contiene anche il file **contexts.xml** .

Questo file conterrà il seguente tipo di informazioni:

```
 <Context path='/foo' docBase='../customers/foo'   crossContext='true' debug='0' reloadable='true' trusted='false'/>
```

Se necessario, questa operazione può essere riprodotta sul lato server.

## Personalizzazione dei parametri di consegna {#personalizing-delivery-parameters}

I parametri di consegna sono definiti nel file di configurazione **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

La configurazione e i comandi generali del server sono descritti in dettaglio nella configurazione [del server](../../installation/using/campaign-server-configuration.md)Campaign.

Potete anche eseguire le seguenti configurazioni in base alle vostre esigenze e impostazioni.

### Relè SMTP {#smtp-relay}

Il modulo MTA agisce come agente nativo di trasferimento della posta per la trasmissione SMTP (porta 25).

È tuttavia possibile sostituirlo con un server di inoltro se richiesto dal criterio di protezione. In tal caso, il throughput globale sarà quello relay (a condizione che il throughput del server relay sia inferiore a quello dell&#39;Adobe Campaign ).

In questo caso, questi parametri vengono impostati configurando il server SMTP nella **`<relay>`** sezione. È necessario specificare l&#39;indirizzo IP (o l&#39;host) del server SMTP utilizzato per trasferire la posta e la porta associata (per impostazione predefinita, 25).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Questa modalità operativa comporta gravi limitazioni per le consegne, in quanto può ridurre notevolmente il throughput a causa delle prestazioni intrinseche del server relay (latenza, banner...). Inoltre, la capacità di qualificare gli errori di consegna sincroni (rilevati analizzando il traffico SMTP) sarà limitata e l&#39;invio non sarà possibile se il server relay non è disponibile.

### Processi figlio MTA {#mta-child-processes}

È possibile controllare la popolazione di processi secondari (maxSpareServers per impostazione predefinita 2) al fine di ottimizzare le prestazioni di trasmissione in base alla potenza della CPU dei server e alle risorse di rete disponibili. Questa configurazione deve essere realizzata nella **`<master>`** sezione della configurazione MTA su ogni singolo computer.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Consultare anche Ottimizzazione [dell’invio per](../../installation/using/email-deliverability.md#email-sending-optimization)e-mail.

### Gestione del traffico SMTP in uscita con affinità {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configurazione di affinità deve essere coerente da un server all&#39;altro. È consigliabile contattare  Adobe per la configurazione dell&#39;affinità, in quanto le modifiche alla configurazione dovrebbero essere replicate su tutti i server applicazioni che eseguono l&#39;MTA.

È possibile migliorare il traffico SMTP in uscita tramite affinità con indirizzi IP.

A questo scopo, eseguire i seguenti passaggi:

1. Immettete le affinità nella **`<ipaffinity>`** sezione del file **serverConf.xml** .

   Un&#39;affinità può avere diversi nomi diversi: per separarli, utilizzare il **;** carattere.

   Esempio:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Per visualizzare i parametri pertinenti, fare riferimento al file **serverConf.xml** .

1. Per abilitare la selezione di affinità negli elenchi a discesa, è necessario aggiungere i nomi di affinità nell&#39;enumerazione **IPAffinity** .

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Le enumerazioni sono dettagliate in [questo documento](../../platform/using/managing-enumerations.md).

   Potete quindi selezionare l&#39;affinità da utilizzare, come illustrato di seguito per le tipologie:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Puoi anche fare riferimento alla configurazione [del server di](../../installation/using/email-deliverability.md#delivery-server-configuration)consegna.

## Autorizzazioni URL {#url-permissions}

L’elenco predefinito di URL che possono essere richiamati tramite codici JavaScript (flussi di lavoro, ecc.) dalle istanze Campaign Classic è limitato. Si tratta di URL che consentono il corretto funzionamento delle istanze.

Per impostazione predefinita, le istanze non possono connettersi a URL esterni. Tuttavia, è possibile aggiungere alcuni URL esterni all’elenco degli URL autorizzati, in modo che l’istanza possa connettersi a tali URL. Questo consente di connettere le istanze Campaign a sistemi esterni, ad esempio server SFTP o siti Web, per abilitare il trasferimento di file e/o dati.

Una volta aggiunto l’URL, viene inserito un suo riferimento nel file di configurazione dell’istanza (serverConf.xml).

I metodi utilizzati per gestire le autorizzazioni URL dipendono dal modello di hosting:

* **Ibrido** o **locale**: aggiungete gli URL da consentire nel file **** serverConf.xml. Informazioni dettagliate sono disponibili nella sezione seguente.
* **Ospitato**: aggiungete gli URL per consentire l’accesso tramite l’ **Pannello di controllo Campaign**. Per ulteriori informazioni, consulta la [documentazione dedicata](https://docs.adobe.com/content/help/en/control-panel/using/instances-settings/url-permissions.html).

Con i modelli di hosting **ibridi** e **locali** , l&#39;amministratore deve fare riferimento a un nuovo **urlPermission** nel file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Esistono tre modalità di protezione della connessione:

* **Blocco**: tutti gli URL che non appartengono al elenco consentiti  sono bloccati, con un messaggio di errore. Questa è la modalità predefinita dopo un post aggiornamento.
* **Autorizzazione**: tutti gli URL che non appartengono al elenco consentiti  sono consentiti.
* **Avviso**: tutti gli URL che non appartengono al elenco consentiti  sono consentiti, ma l&#39;interprete JS invia un avviso in modo che l&#39;amministratore possa raccogliere tali URL. Questa modalità aggiunge i messaggi di avviso JST-310027.

```
<urlPermission action="warn" debugTrace="true">
  <url dnsSuffix="abc.company1.com" urlRegEx=".*" />
  <url dnsSuffix="def.partnerA_company1.com" urlRegEx=".*" />
  <url dnsSuffix="xyz.partnerB_company1.com" urlRegEx=".*" />
</urlPermission>
```

>[!IMPORTANT]
>
>Per impostazione predefinita, il client dei nuovi clienti utilizza la modalità **di** blocco. Se devono consentire un nuovo URL, devono contattare l’amministratore per aggiungerlo al elenco consentiti .
>
>I clienti esistenti che provengono da una migrazione possono utilizzare la modalità **di** avviso per un certo periodo di tempo. Nel frattempo, devono analizzare il traffico in uscita prima di autorizzare gli URL. Una volta definito l’elenco degli URL autorizzati, questi devono contattare l’amministratore per aggiungere gli URL al elenco consentiti  e attivare la modalità **di** blocco.

## Sicurezza e relè delle pagine dinamiche {#dynamic-page-security-and-relays}

Per impostazione predefinita, tutte le pagine dinamiche sono automaticamente correlate al server Tomcat **locale** del computer il cui modulo Web è stato avviato. Questa configurazione viene immessa nella **`<url>`** sezione della configurazione relay della query per il file **ServerConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Per trasmettere l&#39;esecuzione della pagina dinamica su un server **remoto** ; se il modulo Web non è attivato sul computer. A tal fine, è necessario sostituire il **localhost** con il nome del computer remoto per JSP e JSSP, applicazioni Web, rapporti e stringhe.

Per ulteriori informazioni sui vari parametri disponibili, fare riferimento al file di configurazione **serverConf.xml** .

Per le pagine JSP, la configurazione predefinita è:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

 Adobe Campaign utilizza le seguenti pagine JSP:

* /nl/jsp/**soaprouter.jsp**: connessioni console client e servizi Web (API SOAP),
* /nl/jsp/**m.jsp**: pagine mirror,
* /nl/jsp/**access.jsp**: accesso basato su Web ai rapporti e alla distribuzione della console client,
* /nl/jsp/**s.jsp** : Utilizzo del marketing virale (sponsorizzazione e social network).

Gli JSSP utilizzati per il canale app mobile sono i seguenti:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Esempio:**

È possibile impedire le connessioni dei computer client dall&#39;esterno. A tal fine, è sufficiente limitare l&#39;esecuzione di **soaprouter.jsp** e autorizzare solo l&#39;esecuzione di pagine mirror, link virali, moduli Web e risorse pubbliche.

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

In questo esempio, il **`<IP_addresses>`** valore coincide con l&#39;elenco di indirizzi IP (separati da virgole) autorizzati a utilizzare il modulo relè per questa maschera.

>[!NOTE]
>
>I valori devono essere adattati in base alla configurazione e ai vincoli di rete, specialmente se sono state sviluppate configurazioni specifiche per l&#39;installazione.

## Limitazione dei comandi esterni autorizzati {#restricting-authorized-external-commands}

>[!NOTE]
>
>La seguente configurazione è necessaria solo per le installazioni aziendali interne.

Dalla build 8780, gli amministratori tecnici possono limitare l&#39;elenco dei comandi esterni autorizzati utilizzabili in  Adobe Campaign.

A tal fine, è necessario creare un file di testo con l&#39;elenco dei comandi che si desidera impedire l&#39;utilizzo, ad esempio:

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

Nel nodo **exec** del file di configurazione del server, è necessario fare riferimento al file creato in precedenza nell&#39;attributo **blocklistFile** .

**Solo** per Linux: nel file di configurazione del server, si consiglia di specificare un utente dedicato all&#39;esecuzione di comandi esterni per migliorare la configurazione di protezione. Questo utente è impostato nel nodo **exec** del file di configurazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Se non viene specificato alcun utente, tutti i comandi vengono eseguiti nel contesto utente dell&#39;istanza Adobe Campaign . L&#39;utente deve essere diverso dall&#39;utente che esegue  Adobe Campaign.

Ad esempio:

```
<serverConf>
 <exec user="theUnixUser" blocklistFile="/pathtothefile/blocklist"/>
</serverConf>
```

Questo utente deve essere aggiunto all&#39;elenco secondario dell&#39;operatore &quot;neolane&quot;  Adobe Campaign.

>[!IMPORTANT]
>
>Non utilizzare un sudo personalizzato. Nel sistema deve essere installato un sudo standard.

## Gestione delle intestazioni HTTP {#managing-http-headers}

Per impostazione predefinita, tutte le intestazioni HTTP non vengono trasmesse. È possibile aggiungere intestazioni specifiche nelle risposte inviate per inoltro. Per eseguire questa operazione:

1. Andate al file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).
1. Nel **`<relay>`** nodo, passare all&#39;elenco delle intestazioni HTTP inoltrate.
1. Aggiungete un **`<responseheader>`** elemento con i seguenti attributi:

   * **name**: nome intestazione
   * **value**: value name.

   Ad esempio:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Tracciamento ridondante {#redundant-tracking}

Quando più server vengono utilizzati per il reindirizzamento, devono essere in grado di comunicare tra loro tramite chiamate SOAP per condividere informazioni dagli URL da reindirizzare. al momento dell&#39;avvio della consegna, è possibile che non tutti i server di reindirizzamento siano disponibili; pertanto potrebbero non avere lo stesso livello di informazioni.

>[!NOTE]
>
>Quando si utilizza l&#39;architettura standard o aziendale, il server applicazione principale deve essere autorizzato a caricare le informazioni di tracciamento su ogni computer.

Gli URL dei server ridondanti devono essere specificati nella configurazione di reindirizzamento tramite il file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

**Esempio:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

La proprietà **enableIf** è facoltativa (vuota per impostazione predefinita) e consente di abilitare la connessione solo se il risultato è vero; Questo consente di ottenere una configurazione identica su tutti i server di reindirizzamento.

Per ottenere il nome host del computer, eseguire il comando seguente: **hostname -s**.

## Gestione delle risorse pubbliche {#managing-public-resources}

Le risorse pubbliche sono presentate in [Gestione delle risorse](../../installation/using/deploying-an-instance.md#managing-public-resources)pubbliche.

Sono memorizzati nella directory **/var/res/instance** della directory di installazione di Adobe Campaign .

L’URL corrispondente è: **http://server/res/instance** dove **istanza** è il nome dell’istanza di tracciamento.

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

In questo caso, il nuovo URL per le risorse pubbliche fornito nella parte superiore della finestra della procedura guidata di distribuzione dovrebbe puntare a questa cartella.

## Flussi di lavoro e affinità ad alta disponibilità {#high-availability-workflows-and-affinities}

Potete configurare diversi server di workflow (wfserver) e distribuirli su due o più computer. Se scegliete questo tipo di architettura, configurate la modalità di connessione dei bilanciatori di carico in base all&#39;accesso  Adobe Campaign.

Per accedere dal Web, selezionate la modalità di bilanciamento del **carico** per limitare i tempi di connessione.

Se accedete tramite la console  Adobe Campaign, scegliete **hash** o **ip** . Questo consente di mantenere la connessione tra il client avanzato e il server e impedire che una sessione utente venga interrotta durante un&#39;operazione di importazione o esportazione, ad esempio.

Potete scegliere di imporre l&#39;esecuzione di un flusso di lavoro o di un&#39;attività di workflow su un computer specifico. A tal fine, è necessario definire una o più affinità per il flusso di lavoro o l&#39;attività interessati.

1. Create le affinità del flusso di lavoro o dell&#39;attività immettendole nel **[!UICONTROL Affinity]** campo.

   Potete scegliere liberamente i nomi di affinità. Tuttavia, accertarsi di non utilizzare spazi o segni di punteggiatura. Se utilizzate server diversi, specificate nomi diversi.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   L&#39;elenco a discesa contiene le affinità precedentemente utilizzate. Viene completato nel tempo con i diversi valori inseriti.

1. Aprite il file **nl6/conf/config-`<instance>.xml`**.
1. Modificate la linea che corrisponde al **[!UICONTROL wfserver]** modulo come segue:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Se si definiscono più affinità, queste devono essere separate da virgole senza spazi:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   La virgola che segue il nome dell&#39;affinità è necessaria per l&#39;esecuzione di flussi di lavoro per i quali non è definita alcuna affinità.

   Se desiderate eseguire solo flussi di lavoro per i quali è definita un&#39;affinità, non aggiungete una virgola alla fine dell&#39;elenco delle affinità. Ad esempio, modificare la linea come segue:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Riavvio automatico del processo {#automatic-process-restart}

Per impostazione predefinita, i diversi processi  Adobe Campaign si riavviano automaticamente alle 6 del mattino (ora del server) ogni giorno.

Tuttavia, potete modificare questa configurazione.

A questo scopo, andate al file **serverConf.xml** , che si trova nell&#39;archivio **conf** dell&#39;installazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Ogni processo configurato in questo file ha un attributo **processRestartTime** . Potete modificare il valore di questo attributo per adattare il tempo di riavvio di ogni processo in base alle vostre esigenze.

>[!IMPORTANT]
>
>Non eliminare questo attributo. Tutti i processi devono essere riavviati ogni giorno.

## Limitazione dei file caricati {#limiting-uploadable-files}

Un nuovo attributo **uploadAllowList** consente di limitare i tipi di file disponibili per il caricamento sul server Adobe Campaign .

Questo attributo è disponibile nell&#39;elemento **dataStore** del file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

Il valore predefinito di questo attributo è **.+** e consente di caricare qualsiasi tipo di file.

Per limitare i possibili formati, è necessario sostituire il valore dell&#39;attributo con un&#39;espressione regolare Java valida. È possibile immettere diversi valori separandoli con una virgola.

Ad esempio: **uploadAllowList=&quot;.*.png,.*.jpg&quot;** consente di caricare i formati PNG e JPG sul server. Non verranno accettati altri formati.

>[!IMPORTANT]
>
>In Internet Explorer, il percorso completo del file deve essere verificato dall&#39;espressione regolare.

## Configurazione connessione proxy {#proxy-connection-configuration}

Se devi collegare il server Campaign all&#39;esterno tramite un proxy (ad esempio, utilizzando un&#39;attività del flusso di lavoro di trasferimento file), devi configurare la sezione proxyConfig del serverConf tramite un comando. Sono possibili le seguenti connessioni proxy: HTTP, HTTPS, FTP, SFTP. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>A partire dalla versione 20.2, i parametri del protocollo HTTP e HTTPS non sono più disponibili. Le seguenti informazioni fanno ancora riferimento a questi parametri, poiché rimangono disponibili per le build precedenti, incluso 9032.
>
>I proxy SOCKS non sono supportati.

Usa il comando seguente:

```
nlserver config -setproxy:[protocol]/[serverIP]:[port]/[login][:‘https’|'http’]
```

i parametri del protocollo possono essere &quot;http&quot;, &quot;https&quot; o &quot;ftp&quot;.

Se imposti FTP sulla stessa porta del traffico HTTP/HTTPS, puoi usare quanto segue:

```
nlserver config -setproxy:http/198.51.100.0:8080/user
```

Le opzioni &quot;http&quot; e &quot;https&quot; vengono utilizzate solo quando il parametro del protocollo è &quot;ftp&quot; e indicano se il tunneling sulla porta specificata verrà eseguito attraverso HTTPS o attraverso HTTP.

Se utilizzate porte diverse per il traffico FTP/SFTP e HTTP/HTTPS attraverso il server proxy, dovete impostare il parametro del protocollo ‘ftp’.


Ad esempio:

```
nlserver config -setproxy:ftp/198.51.100.0:8080/user:’http’
```

Quindi immettete la password.

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

Se disponete di connessioni interne che dovrebbero passare attraverso il proxy, aggiungetele nel parametro override.

Se desiderate disattivare temporaneamente la connessione proxy, impostate il parametro enabled su &quot;false&quot; o &quot;0&quot;.
