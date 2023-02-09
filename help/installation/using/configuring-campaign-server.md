---
product: campaign
title: Configurazione del server Campaign
description: Configurazione del server Campaign
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 46c8ed46-0947-47fb-abda-6541b12b6f0c
source-git-commit: 294309239bc476669e9e017c27bd1b51a0bdaf8c
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# Guida introduttiva alla configurazione del server Campaign{#gs-campaign-server-config}

![](../../assets/v7-only.svg)

Questo capitolo descrive le configurazioni lato server che possono essere eseguite in base alle esigenze e alle specificità dell’ambiente.

## Restrizioni

Tali procedure sono limitate a **on-premise**/**ibrido** implementazioni e richiedono le autorizzazioni di amministrazione.

Per **ospitato** le implementazioni e le impostazioni lato server possono essere configurate solo per Adobe. Tuttavia, alcune impostazioni possono essere configurate in [Pannello di controllo Campaign campagna](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it), ad esempio gestione inserire nell&#39;elenco Consentiti IP o autorizzazioni URL. [Ulteriori informazioni](https://experienceleague.adobe.com/docs/control-panel/using/instances-settings/ip-allow-listing-instance-access.html?lang=it).

Per ulteriori informazioni, consulta queste sezioni:

* [Documentazione del Pannello di controllo](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=it)
* [Modelli di hosting](../../installation/using/hosting-models.md)
* [Matrice di funzionalità Campaign Classic on-premise e in hosting](../../installation/using/capability-matrix.md)

## File di configurazione

I file di configurazione di Campaign Classic sono memorizzati nel **conf** della cartella di installazione di Adobe Campaign. La configurazione viene suddivisa in due file:

* **serverConf.xml**: configurazione generale per tutte le istanze. Questo file combina i parametri tecnici del server Adobe Campaign: sono condivisi da tutte le istanze. La descrizione di alcuni di questi parametri è illustrata di seguito. I diversi nodi e parametri ed elencati in questo [sezione](../../installation/using/the-server-configuration-file.md).
* **config-`<instance>`.xml** (4) **istanza** è il nome dell&#39;istanza): configurazione specifica dell’istanza. Se condividi il server tra più istanze, inserisci i parametri specifici di ciascuna istanza nel relativo file.

## Ambito di configurazione

Configura o adatta il server Campaign in base alle tue esigenze e alla tua configurazione. È possibile eseguire le seguenti operazioni:

* Proteggere [Identificatore interno](#internal-identifier)
* Abilita [Processi campagna](#enabling-processes)
* Configura [Autorizzazioni URL](url-permissions.md)
* Definisci [Zone di sicurezza](security-zones.md)
* Configura [Impostazioni Tomcat](configure-tomcat.md)
* Personalizza [Parametri di consegna](configure-delivery-settings.md)
* Definisci [Sicurezza e relè delle pagine dinamiche](#dynamic-page-security-and-relays)
* Limita l&#39;elenco di [Comandi esterni consentiti](#restricting-authorized-external-commands)
* Configurazione [Tracciamento ridondante](#redundant-tracking)
* Gestisci [Elevata disponibilità e affinità dei flussi di lavoro](#high-availability-workflows-and-affinities)
* Configurare la gestione dei file - [Ulteriori informazioni](file-res-management.md)
   * Limitare il formato dei file di caricamento
   * Abilitare l’accesso alle risorse pubbliche
   * Configurare la connessione proxy
* [Riavvio automatico del processo](#automatic-process-restart)


## Identificatore interno {#internal-identifier}

La **interno** identifier è un login tecnico da utilizzare a fini di installazione, amministrazione e manutenzione. Questo accesso non è associato a un&#39;istanza.

Gli operatori connessi che utilizzano questo accesso disporranno di tutti i diritti su tutte le istanze. Questo accesso non avrà una password nel caso di una nuova installazione. È necessario definire manualmente questa password.

Usa il comando seguente:

```
nlserver config -internalpassword
```

Vengono quindi visualizzate le seguenti informazioni. Immetti e conferma la password:

```
17:33:57 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
Enter the current password.
Password:
Enter the new password.
Password: XXXX
Confirmation: XXXX
17:34:02 >   Password successfully changed for account 'internal' (authentication mode 'nl')
```

## Abilitare i processi {#enabling-processes}

I processi Adobe Campaign sul server sono attivati (e disabilitati) tramite il **config-default.xml** e **`config-<instance>.xml`** file.

Per applicare le modifiche a questi file, se il servizio Adobe Campaign viene avviato, è necessario eseguire il **nlserver config -reload** comando.

Esistono due tipi di processi: istanza multipla e singola.

* **a più istanze**: viene avviato un singolo processo per tutte le istanze. Ciò vale per **web**, **syslogd** e **trackinglogd** processi.

   L’abilitazione può essere configurata dal **config-default.xml** file.

   Dichiarazione di un server Adobe Campaign per accedere alle console client e per il reindirizzamento (tracciamento):

   ```
   vi nl6/conf/config-default.xml
   <web args="-tomcat" autoStart="true"/>  
   <!-- to start if the machine is also a redirection server -->  
   <trackinglogd autoStart="true"/>
   ```

   In questo esempio, il file viene modificato utilizzando un **vi** in Linux. Può essere modificato utilizzando **.txt** o **.xml** editor.

* **mono-istanza**: viene avviato un processo per ogni istanza (moduli: **mta**, **wfserver**, **inMail**, **sms** e **stat**).

   L’abilitazione può essere configurata utilizzando il file di configurazione dell’istanza:

   ```
   config-<instance>.xml
   ```

   Dichiarazione di un server per la consegna, esecuzione delle istanze del flusso di lavoro e recupero della posta non recapitata:

   ```
   <mta autoStart="true" statServerAddress="localhost"/>
   <wfserver autoStart="true"/>  
   <inMail autoStart="true"/>
   <stat autoStart="true"/>
   ```

**Archiviazione dati di Campaign**

Puoi configurare la directory di archiviazione (**var** ) dei dati di Adobe Campaign (registri, download, reindirizzamenti, ecc.). Per eseguire questa operazione, utilizza la variabile **XTK_VAR_DIR** variabile di sistema:

* In Windows, indica il seguente valore nel **XTK_VAR_DIR** variabile di sistema

   ```
   D:\log\AdobeCampaign
   ```

* In Linux, vai al **customer.sh** e indicare: **esporta XTK_VAR_DIR=/app/log/AdobeCampaign**.

   Per ulteriori informazioni, consulta [Personalizzare i parametri](../../installation/using/installing-packages-with-linux.md#personalizing-parameters).


## Sicurezza e relè delle pagine dinamiche {#dynamic-page-security-and-relays}

Per impostazione predefinita, tutte le pagine dinamiche sono automaticamente correlate alla **locale** Server Tomcat del computer il cui modulo Web è stato avviato. Questa configurazione viene immessa nel **`<url>`** sezione della configurazione del relay query per **ServerConf.xml** file.

È possibile inoltrare l’esecuzione della pagina dinamica su un **remoto** server; se il modulo Web non è attivato nel computer. A questo scopo, devi sostituire il **localhost** con il nome del computer remoto per JSP e JSSP, applicazioni Web, report e stringhe.

Per ulteriori informazioni sui vari parametri disponibili, consulta la **serverConf.xml** file di configurazione.

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

È possibile impedire le connessioni dei computer client dall&#39;esterno. Per fare questo, è sufficiente limitare l&#39;esecuzione di **soaprouter.jsp** e autorizzare solo l&#39;esecuzione di pagine mirror, link virali, moduli web e risorse pubbliche.

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

In questo esempio, la **`<IP_addresses>`** il valore coincide con l’elenco degli indirizzi IP (separati da virgole) autorizzati a utilizzare il modulo relay per questa maschera.

>[!NOTE]
>
>I valori devono essere adattati in base alla configurazione e ai vincoli di rete, specialmente se sono state sviluppate configurazioni specifiche per l&#39;installazione.

### Gestire le intestazioni HTTP {#managing-http-headers}

Per impostazione predefinita, tutte le intestazioni HTTP non vengono trasmesse. È possibile aggiungere intestazioni specifiche nelle risposte inviate tramite relay. Per eseguire questa operazione:

1. Vai a **serverConf.xml** file.
1. In **`<relay>`** vai all&#39;elenco delle intestazioni HTTP inoltrate.
1. Aggiungi un **`<responseheader>`** con i seguenti attributi:

   * **name**: nome intestazione
   * **value**: nome del valore.

   Ad esempio:

   ```
   <responseHeader name="Strict-Transport-Security" value="max-age=16070400; includeSubDomains"/>
   ```

## Limitare i comandi esterni autorizzati {#restricting-authorized-external-commands}

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

In **exec** nodo del file di configurazione del server, è necessario fare riferimento al file creato in precedenza nel **blacklistFile** attributo.

**Solo per Linux**: nel file di configurazione del server, si consiglia di specificare un utente dedicato all&#39;esecuzione di comandi esterni per migliorare la configurazione di sicurezza. Questo utente è impostato nella **exec** nodo del file di configurazione. Tutti i parametri disponibili nel **serverConf.xml** sono elencati in [sezione](../../installation/using/the-server-configuration-file.md).

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


## Tracciamento ridondante {#redundant-tracking}

Quando per il reindirizzamento vengono utilizzati più server, questi devono essere in grado di comunicare tra loro tramite chiamate SOAP per condividere informazioni dagli URL da reindirizzare. Al momento dell&#39;avvio della consegna, è possibile che non tutti i server di reindirizzamento siano disponibili; pertanto potrebbero non avere lo stesso livello di informazioni.

>[!NOTE]
>
>Quando si utilizza l&#39;architettura standard o Enterprise, il server applicazioni principale deve essere autorizzato a caricare le informazioni di tracciamento su ogni computer.

Gli URL dei server ridondanti devono essere specificati nella configurazione di reindirizzamento tramite il **serverConf.xml** file.

**Esempio:**

```
<spareserver enabledIf="$(hostname)!='front_srv1'" id="1" url="http://front_srv1:8080" />
<spareserver enabledIf="$(hostname)!='front_srv2'" id="2" url="http://front_srv2:8080" />
```

La **enableIf** è facoltativo (vuoto per impostazione predefinita) e consente di abilitare la connessione solo se il risultato è vero. Ciò ti consente di ottenere una configurazione identica su tutti i server di reindirizzamento.

Per ottenere il nome host del computer, eseguire il comando seguente: **hostname -s**.



## Flussi di lavoro e affinità ad alta disponibilità {#high-availability-workflows-and-affinities}

È possibile configurare diversi server del flusso di lavoro (wfserver) e distribuirli su due o più computer. Se scegli questo tipo di architettura, configura la modalità di connessione dei load balancer in base all’accesso Adobe Campaign.

Per accedere dal web, seleziona la **load balancer** per limitare i tempi di connessione.

Se accedi tramite la console Adobe Campaign, scegli **hash** o **ip fisso** modalità. Ciò consente di mantenere la connessione tra il client avanzato e il server e di impedire l’interruzione di una sessione utente durante un’operazione di importazione o esportazione, ad esempio.

Puoi scegliere di forzare l’esecuzione di un flusso di lavoro o di un’attività del flusso di lavoro su un determinato computer. A questo scopo, devi definire una o più affinità per il flusso di lavoro o l’attività interessata.

1. Crea le affinità del flusso di lavoro o dell’attività inserendole nel **[!UICONTROL Affinity]** campo .

   Puoi scegliere qualsiasi nome di affinità, ma assicurati di non utilizzare spazi o segni di punteggiatura. Se si utilizzano server diversi, specificare nomi diversi.

   ![](assets/s_ncs_install_server_wf_affinity01.png)

   ![](assets/s_ncs_install_server_wf_affinity02.png)

   L&#39;elenco a discesa contiene affinità precedentemente utilizzate. Viene completato nel tempo con i diversi valori immessi.

1. Apri **nl6/conf/config-`<instance>.xml`** file.
1. Modifica la linea che corrisponde alla **[!UICONTROL wfserver]** modulo come segue:

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

## Riavvio automatico {#automatic-process-restart}

Per impostazione predefinita, i diversi processi di Adobe Campaign vengono riavviati automaticamente alle 6 del mattino (ora del server) ogni giorno.

Tuttavia, puoi modificare questa configurazione.

Per eseguire questa operazione, vai alla pagina **serverConf.xml** nel file **conf** archivio dell&#39;installazione.

Ogni processo configurato in questo file ha un **processRestartTime** attributo. Puoi modificare il valore di questo attributo per adattare il tempo di riavvio di ogni processo in base alle tue esigenze.

>[!IMPORTANT]
>
>Non eliminare questo attributo. Tutti i processi devono essere riavviati ogni giorno.
