---
product: campaign
title: Configurazione del server Campaign
description: Configurazione del server Campaign
feature: Installation, Instance Settings
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 1be1528d657537786c430ea9c8bdb3aad58ba20d
workflow-type: tm+mt
source-wordcount: '1569'
ht-degree: 1%

---

# Guida introduttiva alla configurazione del server Campaign{#gs-campaign-server-config}



Questo capitolo descrive le configurazioni lato server che possono essere eseguite in base alle tue esigenze e alle specificità dell’ambiente.

## Restrizioni

Queste procedure sono limitate alle **distribuzioni on-premise**/**ibride** e richiedono le autorizzazioni di amministrazione.

Per le distribuzioni di **hosted**, le impostazioni lato server possono essere configurate solo per Adobe. Tuttavia, alcune impostazioni possono essere configurate all&#39;interno di [Pannello di controllo Campaign Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it), ad esempio la gestione del elenco Consentiti IP o le autorizzazioni URL. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=it).

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Documentazione del Pannello di controllo](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it)
* [Modelli di hosting](../../installation/using/hosting-models.md)
* [Matrice di funzionalità Campaign Classic on-premise e in hosting](../../installation/using/capability-matrix.md)

## File di configurazione

I file di configurazione di Campaign Classic sono archiviati nella cartella **conf** della cartella di installazione di Adobe Campaign. La configurazione è suddivisa in due file:

* **serverConf.xml**: configurazione generale per tutte le istanze. Questo file combina i parametri tecnici del server Adobe Campaign, che sono condivisi da tutte le istanze. La descrizione di alcuni di questi parametri è riportata di seguito. I diversi nodi e parametri ed elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (dove **istanza** è il nome dell&#39;istanza): configurazione specifica dell&#39;istanza. Se condividi il server tra più istanze, immetti i parametri specifici di ciascuna istanza nel relativo file.

## Ambito di configurazione

Configura o adatta il server Campaign in base alle tue esigenze e configurazione. Puoi eseguire le seguenti azioni:

* Proteggi [Identificatore interno](#internal-identifier)
* Abilita [processi di Campaign](#enabling-processes)
* Configura [autorizzazioni URL](url-permissions.md)
* Definisci [Aree di protezione](security-zones.md)
* Configura [impostazioni Tomcat](configure-tomcat.md)
* Personalizza [Parametri di consegna](configure-delivery-settings.md)
* Definisci [Sicurezza pagine dinamiche e inoltri](#dynamic-page-security-and-relays)
* Limita l&#39;elenco di [Comandi esterni consentiti](#restricting-authorized-external-commands)
* Configura [Tracciamento ridondante](#redundant-tracking)
* Gestisci [Affinità elevata disponibilità e flusso di lavoro](#high-availability-workflows-and-affinities)
* Configura gestione file - [Ulteriori informazioni](file-res-management.md)
   * Limita il formato dei file di caricamento
   * Abilitare l’accesso alle risorse pubbliche
   * Configura connessione proxy
* [Riavvio automatico del processo](#automatic-process-restart)


## Identificatore interno {#internal-identifier}

L&#39;identificatore **internal** è un account di accesso tecnico da utilizzare per l&#39;installazione, l&#39;amministrazione e la manutenzione. Questo accesso non è associato a un’istanza.

Gli operatori connessi tramite questo accesso disporranno di tutti i diritti su tutte le istanze. Questo login non avrà una password nel caso di una nuova installazione. È necessario definire manualmente questa password.

Usa il comando seguente:

```sql
nlserver config -internalpassword
```

Vengono quindi visualizzate le seguenti informazioni. Immettere e confermare la password:

```sql
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Abilita processi {#enabling-processes}

I processi Adobe Campaign sul server sono abilitati (e disabilitati) tramite i file **config-default.xml** e **`config-<instance>.xml`**.

Per applicare le modifiche a questi file, se il servizio Adobe Campaign è avviato, è necessario eseguire il comando **nlserver config -reload**.

Esistono due tipi di processi: a più istanze e a istanza singola.

* **multi-instance**: viene avviato un singolo processo per tutte le istanze. Questo è il caso dei processi **web**, **syslogd** e **trackinglogd**.

  L&#39;abilitazione può essere configurata dal file **config-default.xml**.

  Dichiarazione di un server Adobe Campaign per accedere alle console client e per il reindirizzamento (tracciamento):

  ```
  vi nl6/conf/config-default.xml
  <web args="-tomcat" autoStart="true"/>  
  <!-- to start if the machine is also a redirection server -->  
  <trackinglogd autoStart="true"/>
  ```

  In questo esempio, il file viene modificato utilizzando un comando **vi** in Linux. Può essere modificato con qualsiasi editor **.txt** o **.xml**.

* **mono-instance**: viene avviato un processo per ogni istanza (moduli: **mta**, **wfserver**, **inMail**, **sms** e **stat**).

  L’abilitazione può essere configurata utilizzando il file di configurazione dell’istanza:

  ```
  config-<instance>.xml
  ```

  Dichiarazione di un server per la consegna, esecuzione di istanze del flusso di lavoro e recupero della posta non recapitata:

  ```
  <mta autoStart="true" statServerAddress="localhost"/>
  <wfserver autoStart="true"/>  
  <inMail autoStart="true"/>
  <stat autoStart="true"/>
  ```

**Archiviazione dati di Campaign**

È possibile configurare la directory di archiviazione (**var** directory) dei dati di Adobe Campaign (registri, download, reindirizzamenti, ecc.). A tale scopo, utilizzare la variabile di sistema **XTK_VAR_DIR**:

* In Windows, indicare il valore seguente nella variabile di sistema **XTK_VAR_DIR**

  ```
  D:\log\AdobeCampaign
  ```

* In Linux, vai al file **customer.sh** e indica: **esporta XTK_VAR_DIR=/app/log/AdobeCampaign**.

  Per ulteriori informazioni, consulta [Personalizzare i parametri](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Sicurezza delle pagine dinamiche e inoltri {#dynamic-page-security-and-relays}

Per impostazione predefinita, tutte le pagine dinamiche sono automaticamente correlate al server Tomcat **local** del computer in cui è stato avviato il modulo Web. Questa configurazione viene immessa nella sezione **`<url>`** della configurazione dell&#39;inoltro query per il file **ServerConf.xml**.

È possibile inoltrare l&#39;esecuzione della pagina dinamica su un server **remoto** se il modulo Web non è attivato nel computer. A tale scopo, è necessario sostituire **localhost** con il nome del computer remoto per JSP e JSSP, applicazioni Web, report e stringhe.

Per ulteriori informazioni sui vari parametri disponibili, fare riferimento al file di configurazione **serverConf.xml**.

Per le pagine JSP, la configurazione predefinita è:

```
<url relayHost="true" relayPath="true" targetUrl="http://localhost:8080" urlPath="*.jsp"/>
```

Adobe Campaign utilizza le seguenti pagine JSP:

* /nl/jsp/**soaprouter.jsp**: connessioni alla console client e ai servizi Web (API SOAP),
* /nl/jsp/**m.jsp**: pagine mirror,
* /nl/jsp/**logon.jsp**: accesso basato sul Web ai report e alla distribuzione della console client,
* /nl/jsp/**s.jsp**: utilizzo di marketing virale (sponsorizzazione e social network).

I JSSP utilizzati per il canale app mobile sono i seguenti:

* nms/mobile/1/registerIOS.jssp
* nms/mobile/1/registerAndroid.jssp

**Esempio:**

È possibile impedire le connessioni dei computer client dall&#39;esterno. Per eseguire questa operazione, è sufficiente limitare l&#39;esecuzione di **soaprouter.jsp** e autorizzare solo l&#39;esecuzione di pagine mirror, collegamenti virali, moduli Web e risorse pubbliche.

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

In questo esempio, il valore **`<IP_addresses>`** coincide con l&#39;elenco di indirizzi IP (separati da virgole) autorizzati a utilizzare il modulo di inoltro per questa maschera.

>[!NOTE]
>
>I valori devono essere adattati in base alla configurazione e ai vincoli di rete, soprattutto se sono state sviluppate configurazioni specifiche per l’installazione.

### Gestire le intestazioni HTTP {#managing-http-headers}

Per impostazione predefinita, non tutte le intestazioni HTTP vengono inoltrate. Puoi aggiungere intestazioni specifiche nelle risposte inviate dall’inoltro. Per eseguire questa operazione:

1. Vai al file **serverConf.xml**.
1. Nel nodo **`<relay>`**, passa all&#39;elenco delle intestazioni HTTP inoltrate.
1. Aggiungi un elemento **`<responseheader>`** con i seguenti attributi:

   * **name**: nome intestazione
   * **valore**: nome valore.

   Ad esempio:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Limita comandi esterni autorizzati {#restricting-authorized-external-commands}

A partire dalla build 8780, gli amministratori tecnici possono limitare l’elenco dei comandi esterni autorizzati che possono essere utilizzati in Adobe Campaign.

A tale scopo, è necessario creare un file di testo con l&#39;elenco dei comandi che si desidera impedire l&#39;utilizzo, ad esempio:

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

Nel nodo **exec** del file di configurazione del server, è necessario fare riferimento al file creato in precedenza nell&#39;attributo **blacklistFile**.

**Solo per Linux**: nel file di configurazione del server è consigliabile specificare un utente dedicato all&#39;esecuzione di comandi esterni per migliorare la configurazione della sicurezza. Questo utente è impostato nel nodo **exec** del file di configurazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

>[!NOTE]
>
>Se non viene specificato alcun utente, tutti i comandi vengono eseguiti nel contesto utente dell’istanza di Adobe Campaign. L’utente deve essere diverso dall’utente che esegue Adobe Campaign.

Ad esempio:

```
<serverConf>
 <exec user="theUnixUser" blacklistFile="/pathtothefile/blacklist"/>
</serverConf>
```

Questo utente deve essere aggiunto all’elenco degli utenti dell’operatore Adobe Campaign &quot;neolane&quot;.

>[!IMPORTANT]
>
>Non utilizzare un sudo personalizzato. Sul sistema deve essere installato un sudo standard.


## Tracciamento ridondante {#redundant-tracking}

Quando si utilizzano più server per il reindirizzamento, questi devono essere in grado di comunicare tra loro tramite chiamate SOAP per condividere le informazioni dagli URL da reindirizzare. Al momento dell’avvio della consegna, è possibile che non tutti i server di reindirizzamento siano disponibili; pertanto, potrebbero non disporre dello stesso livello di informazioni.

>[!NOTE]
>
>Quando si utilizza l&#39;architettura standard o enterprise, il server applicazioni principale deve essere autorizzato a caricare le informazioni di tracciamento su ciascun computer.

Gli URL dei server ridondanti devono essere specificati nella configurazione di reindirizzamento tramite il file **serverConf.xml**.

**Esempio:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

La proprietà **enableIf** è facoltativa (vuota per impostazione predefinita) e consente di abilitare la connessione solo se il risultato è vero. Questo consente di ottenere una configurazione identica su tutti i server di reindirizzamento.

Per ottenere il nome host del computer, eseguire il comando seguente: **hostname -s**.



## Flussi di lavoro e affinità ad alta disponibilità {#high-availability-workflows-and-affinities}

È possibile configurare diversi server di workflow (wfserver) e distribuirli su due o più computer. Se scegli questo tipo di architettura, configura la modalità di connessione dei load balancer in base all’accesso ad Adobe Campaign.

Per l&#39;accesso dal Web, selezionare la modalità **load balancer** per limitare i tempi di connessione.

Se accedi tramite la console Adobe Campaign, scegli la modalità **hash** o **ip fisso**. In questo modo è possibile mantenere la connessione tra il client avanzato e il server e impedire, ad esempio, l&#39;interruzione di una sessione utente durante un&#39;operazione di importazione o esportazione.

Puoi scegliere di forzare l’esecuzione di un flusso di lavoro o di un’attività del flusso di lavoro su un determinato computer. A questo scopo, devi definire una o più affinità per il flusso di lavoro o l’attività interessata.

1. Creare le affinità del flusso di lavoro o dell&#39;attività immettendole nel campo **[!UICONTROL Affinity]**.

   È possibile scegliere qualsiasi nome di affinità, ma assicurarsi di non utilizzare spazi o segni di punteggiatura. Se si utilizzano server diversi, specificare nomi diversi.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   L’elenco a discesa contiene le affinità precedentemente utilizzate. Viene completato nel tempo con i diversi valori immessi.

1. Aprire il file **nl6/conf/config-`<instance>.xml`**.
1. Modificare la riga corrispondente al modulo **[!UICONTROL wfserver]** come segue:

   ```
   <wfserver autoStart="true" affinity="XXX,"/>
   ```

   Se definisci più affinità, queste devono essere separate da virgole senza spazi:

   ```
   <wfserver autoStart="true" affinity="XXX,YYY,"/>
   ```

   La virgola che segue il nome dell’affinità è necessaria per l’esecuzione di flussi di lavoro per i quali non è definita alcuna affinità.

   Se desideri eseguire solo i flussi di lavoro per i quali è definita un’affinità, non aggiungere una virgola alla fine dell’elenco delle affinità. Ad esempio, modificare la riga come segue:

   ```
   <wfserver autoStart="true" affinity="XXX"/>
   ```

## Riavvio automatico {#automatic-process-restart}

Per impostazione predefinita, i diversi processi di Adobe Campaign vengono riavviati automaticamente ogni giorno alle 6 (ora del server).

Tuttavia, puoi modificare questa configurazione.

A tale scopo, passare al file **serverConf.xml**, che si trova nell&#39;archivio **conf** dell&#39;installazione.

Ogni processo configurato in questo file ha un attributo **processRestartTime**. Puoi modificare il valore di questo attributo per adattare il tempo di riavvio di ciascun processo in base alle tue esigenze.

>[!IMPORTANT]
>
>Non eliminare questo attributo. È necessario riavviare tutti i processi ogni giorno.
