---
product: campaign
title: Configurazione tecnica delle e-mail
description: Scopri come configurare Campaign per controllare l’output delle istanze durante la consegna delle e-mail
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '3023'
ht-degree: 0%

---

# Configurazioni tecniche delle e-mail{#email-deliverability}



## Panoramica {#overview}

La sezione seguente fornisce una panoramica della configurazione necessaria per controllare l’output delle istanze di Adobe Campaign durante la distribuzione delle e-mail.

>[!NOTE]
>
>Alcune configurazioni possono essere eseguite solo da Adobe per le distribuzioni ospitate da Adobe, ad esempio per accedere ai file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle diverse implementazioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o a [questa pagina](../../installation/using/capability-matrix.md).

Per ulteriori informazioni sui concetti e le best practice relativi al recapito messaggi con Adobe Campaign, consulta questa [sezione](../../delivery/using/about-deliverability.md).

Per informazioni più approfondite sulla consegna dei messaggi, comprese tutte le raccomandazioni tecniche relative all’invio e alla ricezione efficienti delle e-mail da parte di una piattaforma di Adobe, consulta [Guida alle procedure consigliate per la consegna dei messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

## Principio di funzionamento {#operating-principle}

È possibile controllare l’output di una o più istanze di Adobe Campaign per limitare il numero di e-mail inviate a seconda di un dominio. Ad esempio, puoi limitare l’output a 20.000 all’ora per **yahoo.com** , configurando 100.000 messaggi all&#39;ora per tutti gli altri domini.

L’output del messaggio deve essere controllato per ogni indirizzo IP utilizzato dai server di consegna (**mta**). Diversi **mta** suddiviso su più computer e appartenente a varie istanze di Adobe Campaign, può condividere lo stesso indirizzo IP per la consegna delle e-mail: è necessario impostare un processo per coordinare l’utilizzo di questi indirizzi IP.

Questo è ciò che **stat** modulo: inoltra tutte le richieste di connessione e i messaggi da inviare ai server di posta per un set di indirizzi IP. Il server delle statistiche tiene traccia delle consegne e può abilitare o disabilitare l&#39;invio in base alle quote impostate.

![](assets/s_ncs_install_mta.png)

* Server delle statistiche (**stat**) è collegato a una base Adobe Campaign per caricarne la configurazione.
* I server di consegna (**mta**) utilizzare un UDP per contattare un server di statistiche che non appartiene sempre alla propria istanza.

### Server di consegna {#delivery-servers}

Il **mta** il modulo distribuisce i messaggi al relativo **mtachild** moduli secondari. Ogni **mtachild** prepara i messaggi prima di richiedere un&#39;autorizzazione al server di statistiche e di inviarli.

I passaggi sono i seguenti:

1. Il **mta** seleziona i messaggi idonei e assegna loro un **mtachild**.
1. Il **mtachild** carica tutte le informazioni necessarie per la creazione del messaggio (contenuto, elementi di personalizzazione, allegati, immagini, ecc.) e inoltra il messaggio al **E-mail Traffic Shaper**.
1. Non appena lo shaper del traffico e-mail riceve l&#39;autorizzazione del server delle statistiche (**stat smtp**), il messaggio viene inviato al destinatario.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Statistiche e limitazioni del server e-mail {#email-server-statistics-and-limitations}

Il server delle statistiche gestisce le seguenti statistiche per ogni server e-mail che riceve messaggi:

* Numero di connessioni point-in-time aperte,
* Numero di messaggi inviati nell’ultima ora,
* Numero di connessioni riuscite/rifiutate,
* Frequenza di connessioni a server non raggiungibili.

Allo stesso tempo, il modulo carica un elenco di limitazioni per alcuni server e-mail:

* numero massimo di connessioni simultanee,
* Numero massimo di messaggi all’ora
* Numero massimo di messaggi per connessione.

### Gestione degli indirizzi IP {#managing-ip-addresses}

Il server delle statistiche può combinare più istanze o computer con lo stesso indirizzo IP pubblico. Non è quindi collegato a un’istanza specifica, ma deve contattare un’istanza per recuperare le limitazioni per dominio.

Le statistiche di consegna vengono conservate per ogni MX di destinazione e per ogni IP di origine. Ad esempio, se il dominio di destinazione ha 5 MX e la piattaforma può utilizzare 3 indirizzi IP diversi, il server può gestire fino a 15 serie di indicatori per questo dominio.

L’indirizzo IP di origine corrisponde all’indirizzo IP pubblico, ovvero all’indirizzo visualizzato dal server e-mail remoto. Questo indirizzo IP può essere diverso dall&#39;indirizzo del computer che ospita **mta**, se viene fornito un router NAT. Per questo motivo il server delle statistiche utilizza un identificatore che corrisponde all&#39;IP pubblico (**publicId**). L&#39;associazione tra l&#39;indirizzo locale e questo identificatore è dichiarata nel **serverConf.xml** file di configurazione. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questo [sezione](../../installation/using/the-server-configuration-file.md).

## Controllo dell’output di consegna {#delivery-output-controlling}

Per inviare messaggi ai server di posta elettronica, **E-mail Traffic Shaper** il componente richiede una connessione dal server di statistiche. Una volta accettata la richiesta, la connessione viene aperta.

Prima di inviare messaggi, il modulo richiede &quot;token&quot; dal server. Si tratta in genere di set di almeno 10 token, che riducono il numero di query per il server.

Il server salva tutte le statistiche relative a connessioni e consegne. In caso di riavvio, le informazioni vengono temporaneamente perse: ogni client mantiene una copia locale delle proprie statistiche di invio e le restituisce al server regolarmente (ogni 2 minuti). Il server può quindi riaggregare i dati.

Nelle sezioni seguenti viene descritta l’elaborazione di un messaggio da parte di **E-mail Traffic Shaper** componente.

### Consegna dei messaggi {#message-delivery}

Quando viene inviato un messaggio, i possibili risultati sono 3:

1. **Completato**: il messaggio è stato inviato correttamente. Il messaggio viene aggiornato.
1. **Messaggio non riuscito**: il server contattato ha rifiutato il messaggio per il destinatario scelto. Questo risultato corrisponde ai codici restituiti da 550 a 599, ma è possibile definire le eccezioni.
1. **Sessione non riuscita** (per 5.11 verso l&#39;alto): se il **mta** riceve una risposta per questo messaggio, il messaggio viene abbandonato (fare riferimento a [Abbandono del messaggio](#message-abandonment)). Il messaggio viene inviato a un altro percorso o impostato su In sospeso se non sono disponibili altri percorsi (fare riferimento a [Messaggio in attesa](#message-pending)).

   >[!NOTE]
   >
   >A **percorso** è una connessione tra Adobe Campaign **mta** e il target **mta**. Adobe Campaign **mta** può scegliere tra diversi IP iniziali e diversi IP del dominio di destinazione.

### Abbandono del messaggio {#message-abandonment}

I messaggi abbandonati vengono restituiti al **mta** e non sono più gestiti dal **mtachild**.

Il **mta** decide la procedura per questo messaggio (recupero, abbandono, quarantena, ecc.) a seconda del codice di risposta e delle regole.

### Messaggio in attesa {#message-pending}

Un messaggio viene aperto quando arriva nella coda attiva e non sono disponibili percorsi.

Un percorso è generalmente contrassegnato come non disponibile per un periodo di tempo variabile dopo un errore di connessione. Il periodo di indisponibilità dipende dalla frequenza e dall’età degli errori.

## Configurazione del server di statistiche {#statistics-server-configuration}

Il server delle statistiche può essere utilizzato da diverse istanze: deve essere configurato indipendentemente dalle istanze che lo utilizzeranno.

Inizia definendo il database di Adobe Campaign che ospiterà la configurazione.

### Avvia configurazione {#start-configuration}

Per impostazione predefinita, il **stat** viene avviato per ogni istanza. Quando le istanze sono messe in pool sullo stesso computer o quando condividono lo stesso indirizzo IP, viene utilizzato un unico server di statistiche: le altre devono essere disabilitate.

### Definizione della porta del server {#definition-of-the-server-port}

Per impostazione predefinita, il server delle statistiche è in ascolto sulla porta 7777. Questa porta può essere modificata in **serverConf.xml** file. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questo [sezione](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## Configurazione MX {#mx-configuration}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), il **[!UICONTROL MX management]** le regole di velocità effettiva di consegna non vengono più utilizzate. L’MTA avanzato utilizza le proprie regole MX, che gli consentono di personalizzare la velocità effettiva per dominio in base alla reputazione cronologica dell’e-mail e al feedback in tempo reale proveniente dai domini in cui invii le e-mail.

### Informazioni sulle regole MX {#about-mx-rules}

>[!NOTE]
>
>Questa sezione e le sezioni seguenti si applicano solo alle installazioni on-premise e alle installazioni in hosting/ibride che utilizzano l’MTA di Campaign legacy.

Le regole MX (Mail eXchanger) sono le regole che gestiscono la comunicazione tra un server di invio e un server ricevente.

Queste regole vengono ricaricate automaticamente ogni mattina alle 6 (ora del server) per fornire regolarmente l’istanza del client.

A seconda delle capacità materiali e della politica interna, un ISP accetterà un numero predefinito di connessioni e messaggi all&#39;ora. Queste variabili possono essere modificate automaticamente dal sistema ISP a seconda della reputazione dell’IP e del dominio di invio. Tramite la sua piattaforma di recapito messaggi, Adobe Campaign gestisce più di 150 regole specifiche da parte dell’ISP e, inoltre, una regola generica per altri domini.

Il numero massimo di connessioni non dipende esclusivamente dal numero di indirizzi IP pubblici utilizzati dall’MTA.

Ad esempio, se hai consentito 5 connessioni nelle regole MX e hai configurato 2 IP pubblici, potresti pensare che non puoi avere più di 10 connessioni aperte contemporaneamente a questo dominio. Questo non è vero, infatti il numero massimo di connessioni si riferisce a un percorso e a un percorso che è una combinazione di uno dei nostri IP pubblici MTA e un IP pubblico dell’MTA del client.

Nell’esempio seguente, l’utente ha configurato due indirizzi IP pubblici e il dominio è yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

I record MX per yahoo.com ci dicono che yahoo.com ha 3 Mail Exchanger. Per connettere Peer Mail Exchanger, l’MTA richiederà il suo indirizzo IP al DNS.

```
user:~ user$ host -t a mta5.am0.yahoodns.net
                mta5.am0.yahoodns.net has address 98.136.216.26
                mta5.am0.yahoodns.net has address 98.136.217.202
                mta5.am0.yahoodns.net has address 98.138.112.38
                mta5.am0.yahoodns.net has address 66.196.118.37
                mta5.am0.yahoodns.net has address 63.250.192.46
                mta5.am0.yahoodns.net has address 66.196.118.240
                mta5.am0.yahoodns.net has address 98.136.217.203
                mta5.am0.yahoodns.net has address 98.138.112.35
```

Per questo record, l’utente può contattare 8 indirizzi IP peer. Poiché l’utente dispone di 2 indirizzi IP pubblici, ciò fornisce loro 8 * 2 = 16 combinazioni per raggiungere i server di posta yahoo.com. Ognuna di queste combinazioni è denominata percorso.

Il secondo record MX viene visualizzato come:

```
user:~ user$ host -t a mta6.am0.yahoodns.net
                mta6.am0.yahoodns.net has address 98.138.112.38
                mta6.am0.yahoodns.net has address 98.136.216.26
                mta6.am0.yahoodns.net has address 63.250.192.46
                mta6.am0.yahoodns.net has address 66.196.118.35
                mta6.am0.yahoodns.net has address 98.136.217.203
                mta6.am0.yahoodns.net has address 98.138.112.32
                mta6.am0.yahoodns.net has address 98.138.112.37
                mta6.am0.yahoodns.net has address 66.196.118.33
```

4 di questi 8 indirizzi IP sono già utilizzati in mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 e 98.136.217.203). Questo record consente all’utente di utilizzare 4 nuovi indirizzi IP. Il terzo record MX farà lo stesso.

In totale, abbiamo 16 indirizzi IP remoti. In combinazione con i nostri 2 IP pubblici locali abbiamo 32 percorsi per raggiungere i server di posta yahoo.com.

>[!NOTE]
>
>Se 2 record MX fanno riferimento allo stesso indirizzo IP, questo verrà conteggiato come un percorso e non come due.

Di seguito sono riportati alcuni esempi di utilizzo delle regole MX:

![](assets/s_ncs_examples_mx_rules.png)

Nell’esempio seguente, l’utente ha un limite di 10.000 messaggi all’ora per un determinato dominio, ma la capacità di throughput MTA è superiore a questo limite.

In questo caso, il traffico viene diviso in 12 periodi di 5 minuti per ogni ora e il limite effettivo è di 833 messaggi per periodo.

Questi messaggi verranno recapitati il più rapidamente possibile.

![](assets/s_ncs_traffic_shaping.png)

### Configurazione della gestione MX {#configuring-mx-management}

Le norme da rispettare per MX sono definite nella **[!UICONTROL MX management]** documento del **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** dell&#39;albero.

Se il **[!UICONTROL MX management]** il documento non esiste nel nodo, è possibile crearlo manualmente. Per eseguire questa operazione:

1. Crea un nuovo set di regole di posta.
1. Scegli la **[!UICONTROL MX management]** modalità.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Invio **defaultMXRules** nel **[!UICONTROL Internal name]** campo.

Per tenere conto delle modifiche, è necessario riavviare il server delle statistiche.

Per ricaricare la configurazione senza riavviare il server delle statistiche, utilizzare il comando seguente nel computer che ospita il server: `nlserver stat -reload`

>[!NOTE]
>
>Questa riga di comando è da preferirsi a **riavvio nlserver**. Impedisce la perdita delle statistiche raccolte prima del riavvio ed evita picchi di utilizzo che possono andare contro le quote definite nelle regole MX.

### Configurazione delle regole MX {#configuring-mx-rules}

Il **[!UICONTROL MX management]** nel documento sono elencati tutti i domini collegati a una regola MX.

Queste regole vengono applicate in sequenza: viene applicata la prima regola la cui maschera MX è compatibile con la MX di destinazione.

I seguenti parametri disponibili per ciascuna regola sono:

* **[!UICONTROL MX mask]**: dominio a cui viene applicata la regola. Ogni regola definisce una maschera di indirizzo per l’MX. Qualsiasi MX il cui nome corrisponde a questa maschera è quindi idoneo. La maschera può contenere &quot;&#42;&quot; e &quot;?&quot; caratteri generici.

   Ad esempio, i seguenti indirizzi:

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   sono compatibili con le seguenti maschere:

   * &#42;.yahoo.com
   * ?.mx.yahoo.com

   Ad esempio, per l’indirizzo e-mail foobar@gmail.com, il dominio è gmail.com e il record MX è:

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   In questo caso, la regola MX `*.google.com` verrà utilizzato. Come puoi vedere, la maschera della regola MX non corrisponde necessariamente al dominio nell’e-mail. Le regole MX applicate per gli indirizzi e-mail gmail.com saranno quelle con la maschera `*.google.com`.

* **[!UICONTROL Range of identifiers]**: questa opzione ti consente di indicare gli intervalli di identificatori (publicID) per i quali si applica la regola. Puoi specificare:

   * Un numero: la regola si applicherà solo a questo publicId,
   * Un intervallo di numeri (**number1-number2**): la regola si applica a tutti gli id pubblici compresi tra questi due numeri.

   >[!NOTE]
   >
   >Se il campo è vuoto, la regola si applica a tutti gli identificatori.

   Un ID pubblico è un identificatore interno di un IP pubblico utilizzato da uno o più MTA. Questi ID sono definiti nei server MTA di **config-instance.xml** file.

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: definisce l’ambito delle proprietà per questa regola MX. Se questa opzione è selezionata, tutti i parametri vengono condivisi su tutti gli IP disponibili nell’istanza. Se questa opzione è deselezionata, le regole MX vengono definite per ogni IP. Il numero massimo di messaggi viene moltiplicato per il numero di IP disponibili.
* **[!UICONTROL Maximum number of connections]**: numero massimo di connessioni simultanee al dominio del mittente.
* **[!UICONTROL Maximum number of messages]**: numero massimo di messaggi che possono essere inviati in una connessione. Quando i messaggi superano questo numero, la connessione viene chiusa e ne viene aperta una nuova.
* **[!UICONTROL Messages per hour]**: numero massimo di messaggi che possono essere inviati in un’ora al dominio del mittente.
* **[!UICONTROL Connection time out]**: soglia di tempo per la connessione a un dominio.

   >[!NOTE]
   >
   >Windows può emettere un **timeout** prima di questa soglia, che dipende dalla versione di Windows in uso.

* **[!UICONTROL Timeout Data]**: tempo di attesa massimo dopo l’invio del contenuto del messaggio (sezione DATA del protocollo SMTP).
* **[!UICONTROL Timeout]**: tempo massimo di attesa per altri scambi con il server SMTP.
* **[!UICONTROL TLS]**: il protocollo TLS, che consente di crittografare le consegne e-mail, può essere abilitato selettivamente. Per ogni maschera MX sono disponibili le seguenti opzioni:

   * **[!UICONTROL Default configuration]**: si tratta della configurazione generale specificata nel file di configurazione serverConf.xml applicato.

      >[!IMPORTANT]
      >
      >Non è consigliabile modificare la configurazione predefinita.

   * **[!UICONTROL Disabled]** : i messaggi vengono inviati sistematicamente senza crittografia.
   * **[!UICONTROL Opportunistic]** : la consegna dei messaggi è crittografata se il server ricevente (SMTP) può generare il protocollo TLS.

Esempio di configurazione:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Per ulteriori informazioni sull’utilizzo dei server MX con Adobe Campaign, consulta [questa sezione](../../installation/using/using-mx-servers.md).

### Gestione dei formati e-mail {#managing-email-formats}

Puoi definire il formato dei messaggi inviati, in modo che il contenuto visualizzato si adatti automaticamente in base al dominio dell’indirizzo di ciascun destinatario.

Per eseguire questa operazione, passare al **[!UICONTROL Management of email formats]** documento, che si trova in **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Questo documento contiene un elenco di tutti i domini predefiniti che corrispondono ai formati giapponesi gestiti da Adobe Campaign. Per ulteriori informazioni, consulta [questo documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

Il **Struttura MIME** (Multipurpose Internet Mail Extensions) consente di definire la struttura dei messaggi che verranno inviati ai diversi client di posta. Sono disponibili tre opzioni:

* **Multipart**: il messaggio viene inviato in formato testo o HTML. Se il formato HTML non viene accettato, il messaggio potrà comunque essere visualizzato in formato testo.

   Per impostazione predefinita, la struttura multipart è **multipart/alternative**, ma diventa automaticamente **multipart/related** quando un’immagine viene aggiunta al messaggio. Alcuni provider si aspettano che **multipart/related** per impostazione predefinita, il **[!UICONTROL Force multipart/related]** impone questo formato anche se non è allegata alcuna immagine.

* **HTML**: viene inviato un messaggio solo HTML. Se il formato HTML non è accettato, il messaggio non viene visualizzato.
* **Testo**: viene inviato un messaggio in formato di solo testo. Il vantaggio dei messaggi in formato testo è la loro dimensione molto ridotta.

Se il **[!UICONTROL Image inclusion]** è abilitata, vengono visualizzate direttamente nel corpo dell’e-mail. Le immagini vengono quindi caricate e i collegamenti URL sostituiti dal relativo contenuto.

Questa opzione è particolarmente utilizzata dal mercato giapponese per **Deco-mail**, **Decore Mail** o **Decoration Mail**. Per ulteriori informazioni, consulta [questo documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>L’inserimento di immagini in un’e-mail ne aumenta considerevolmente le dimensioni.

## Configurazione del server di consegna {#delivery-server-configuration}

### Sincronizzazione orologio {#clock-synchronization}

Gli orologi di tutti i server che compongono la piattaforma Adobe Campaign (incluso il database) devono essere sincronizzati e i relativi sistemi impostati sullo stesso fuso orario.

### Coordinate del server delle statistiche {#coordinates-of-the-statistics-server}

L&#39;indirizzo del server delle statistiche deve essere fornito nel **mta**.

Il **statServerAddress** proprietà del **mta** dell&#39;elemento di configurazione consente di specificare l&#39;indirizzo e il numero della porta da utilizzare.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Per utilizzare il server delle statistiche sullo stesso computer, è necessario immettere almeno il nome del computer con **localhost** valore:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Se questo campo non è compilato, il **mta** non inizierà.

### Elenco di indirizzi IP da utilizzare {#list-of-ip-addresses-to-use}

La configurazione relativa alla gestione del traffico si trova in **mta/child/smtp** del file di configurazione.

Per ogni **IPAfinity** , è necessario dichiarare gli indirizzi IP che possono essere utilizzati per il computer.

Esempio:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

I parametri sono i seguenti:

* **indirizzo**: questo è l’indirizzo IP del computer host MTA da utilizzare.
* **heloHost**: questo identificatore rappresenta l’indirizzo IP così come verrà visualizzato dal server SMTP.

* **publicId**: queste informazioni sono utili quando un indirizzo IP viene condiviso da più Adobe Campaign **mta** dietro un router NAT. Il server delle statistiche utilizza questo identificatore per memorizzare la connessione e inviare statistiche tra questo punto iniziale e il server di destinazione.
* **peso**: ti consente di definire la frequenza relativa di utilizzo dell’indirizzo. Per impostazione predefinita, tutti gli indirizzi hanno un peso uguale a 1.

>[!NOTE]
>
>Nel file serverConf.xml, devi verificare che un IP corrisponda a un singolo helohost con un identificatore univoco (public_id). Non può essere mappato su più helohost, il che potrebbe causare problemi di limitazione della consegna.

Nell’esempio precedente, in condizioni normali, gli indirizzi verranno distribuiti come segue:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Se, ad esempio, il primo indirizzo non può essere utilizzato per un determinato MX, i messaggi verranno inviati come segue:

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**: consente di riservare questo indirizzo IP per le e-mail appartenenti a un dominio specifico. Elenco di maschere che possono contenere uno o più caratteri jolly (&#39;&#42;&#39;). Se l’attributo non è specificato, tutti i domini possono utilizzare questo indirizzo IP.

   Esempio: **includeDomains=&quot;wanadoo.com,orange.com,yahoo.&#42;&quot;**

* **excludeDomains**: esclude un elenco di domini per questo indirizzo IP. Questo filtro viene applicato dopo il **includeDomains** filtro.

   ![](assets/s_ncs_install_mta_ips.png)

## Ottimizzazione dell’invio di e-mail {#email-sending-optimization}

Architettura interna di Adobe Campaign **mta** ha un impatto sulla configurazione per l’ottimizzazione della consegna e-mail. Di seguito sono riportati alcuni suggerimenti per migliorare le consegne.

### Regolare il parametro maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter}

Il **maxWaitingMessages** Il parametro indica il numero massimo di messaggi preparati in anticipo da **mtachild**. I messaggi vengono eliminati dall&#39;elenco solo dopo essere stati inviati o abbandonati.

Questo parametro è molto importante e particolarmente critico se i messaggi non sono ordinati per dominio.

Una volta **maxWorkingSetMb** (256) quando viene raggiunta la soglia, il server di consegna interrompe l’invio dei messaggi. Le prestazioni diminuiranno in modo significativo fino a quando **mtachild** riavvia. Per evitare questo problema, puoi aumentare la soglia del **maxWorkingSetMb** o diminuire la soglia del **maxWaitingMessages** parametro.

Il **maxWorkingSetMb** Il parametro viene calcolato empiricamente moltiplicando il numero massimo di messaggi per la dimensione media e moltiplicando il risultato per 2,5. Ad esempio, se un messaggio ha una dimensione media di 50 KB e **maxWaitingMessages** è uguale a 1.000, la memoria utilizzata è in media di 125 MB.

### Regola il numero di matchild {#adjust-the-number-of-mtachild}

Il numero di figli non deve superare il numero di processori presenti nella macchina (circa 1000 sessioni). Si consiglia di non superare gli 8 **mtachild**. Puoi quindi aumentare il numero di messaggi per **secondario** (**maxMsgPerChild**) per ottenere una durata di vita sufficiente.
