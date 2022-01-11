---
product: campaign
title: Configurazione e-mail tecnica
description: Scopri come configurare Campaign per controllare l’output delle istanze durante la consegna delle e-mail.
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 515adad2-6129-450a-bb9e-fc80127835af
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '3023'
ht-degree: 0%

---

# Configurazioni tecniche delle e-mail{#email-deliverability}

![](../../assets/v7-only.svg)

## Panoramica {#overview}

La sezione seguente fornisce una panoramica della configurazione necessaria per controllare l’output delle istanze Adobe Campaign durante la consegna delle e-mail.

>[!NOTE]
>
>Alcune configurazioni possono essere eseguite solo da Adobe per le distribuzioni ospitate da Adobe, ad esempio per accedere ai file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle diverse implementazioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o [questa pagina](../../installation/using/capability-matrix.md).

Per ulteriori informazioni sui concetti e sulle best practice relativi al recapito messaggi con Adobe Campaign, consulta questo [sezione](../../delivery/using/about-deliverability.md).

Per informazioni più approfondite sul recapito messaggi, incluse tutte le raccomandazioni tecniche relative all’invio e alla ricezione efficienti di e-mail da parte di una piattaforma di Adobe, fai riferimento alla sezione [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=it).

## Principio di funzionamento {#operating-principle}

È possibile controllare l’output di una o più istanze di Adobe Campaign per limitare il numero di e-mail inviate a seconda di un dominio. Ad esempio, puoi limitare l’output a 20.000 all’ora per **yahoo.com** indirizzi durante la configurazione di 100.000 messaggi all’ora per tutti gli altri domini.

L’output del messaggio deve essere controllato per ogni indirizzo IP utilizzato dai server di consegna (**mta**). Diversi **mta** suddivisi su più computer e appartenenti a varie istanze Adobe Campaign possono condividere lo stesso indirizzo IP per la consegna e-mail: è necessario impostare un processo per coordinare l’utilizzo di questi indirizzi IP.

Questo è ciò che **stat** il modulo esegue: inoltra tutte le richieste di connessione e i messaggi da inviare ai server di posta elettronica per un set di indirizzi IP. Il server di statistiche tiene traccia delle consegne e può abilitare o disabilitare l’invio in base a quote impostate.

![](assets/s_ncs_install_mta.png)

* Server delle statistiche (**stat**) è collegata a una base Adobe Campaign per caricare la configurazione.
* I server di consegna (**mta**) utilizzare un UDP per contattare un server di statistiche che non appartiene sempre alla propria istanza.

### Server di distribuzione {#delivery-servers}

La **mta** il modulo distribuisce i messaggi al proprio **madre** moduli figlio. Ogni **madre** prepara i messaggi prima di richiedere un’autorizzazione al server di statistiche e di inviarli.

Le fasi sono le seguenti:

1. La **mta** seleziona i messaggi idonei e assegna loro un **madre**.
1. La **madre** carica tutte le informazioni necessarie per la creazione del messaggio (contenuto, elementi di personalizzazione, allegati, immagini, ecc.) e inoltra il messaggio al **Shaper traffico e-mail**.
1. Non appena lo shaper del traffico e-mail riceve l&#39;autorizzazione del server di statistiche (**smtp stat**), il messaggio viene inviato al destinatario.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Statistiche e limitazioni del server e-mail {#email-server-statistics-and-limitations}

Il server di statistiche mantiene le seguenti statistiche per ogni server di posta elettronica che riceve i messaggi:

* numero di connessioni point-in-time aperte,
* Numero di messaggi inviati nell’ultima ora,
* Frequenza delle connessioni riuscite/rifiutate,
* Frequenza di connessioni a server non raggiungibili.

Allo stesso tempo, il modulo carica un elenco di limitazioni per alcuni server e-mail:

* Numero massimo di connessioni simultanee,
* Numero massimo di messaggi all’ora,
* Numero massimo di messaggi per connessione.

### Gestione degli indirizzi IP {#managing-ip-addresses}

Il server di statistiche può combinare più istanze o più computer con lo stesso indirizzo IP pubblico. Pertanto non è collegato a un’istanza specifica, ma deve contattare un’istanza per recuperare le limitazioni per dominio.

Le statistiche di consegna sono conservate per ciascun MX di destinazione e per ciascun IP di origine. Ad esempio, se il dominio di destinazione ha 5 MX e la piattaforma può utilizzare 3 indirizzi IP diversi, il server può gestire fino a 15 serie di indicatori per questo dominio.

L&#39;indirizzo IP di origine corrisponde all&#39;indirizzo IP pubblico, ovvero l&#39;indirizzo visualizzato dal server di posta elettronica remoto. Questo indirizzo IP può essere diverso dall&#39;indirizzo del computer che ospita il **mta**, se viene fornito un router NAT. Per questo motivo il server di statistiche utilizza un identificatore che corrisponde all’IP pubblico (**publicId**). L&#39;associazione tra l&#39;indirizzo locale e questo identificatore è dichiarata nella **serverConf.xml** file di configurazione. Tutti i parametri disponibili nel **serverConf.xml** sono elencati in [sezione](../../installation/using/the-server-configuration-file.md).

## Controllo dell&#39;output di consegna {#delivery-output-controlling}

Per inviare messaggi ai server e-mail, la **Shaper traffico e-mail** richiede una connessione dal server di statistiche. Una volta accettata la richiesta, la connessione viene aperta.

Prima di inviare i messaggi, il modulo richiede &quot;token&quot; dal server. Si tratta in genere di set di almeno 10 token, che riducono il numero di query al server.

Il server salva tutte le statistiche relative alle connessioni e alle consegne. In caso di riavvio, le informazioni vengono temporaneamente perse: ogni client conserva una copia locale delle statistiche di invio e le restituisce regolarmente al server (ogni 2 minuti). Il server può quindi eseguire nuovamente l&#39;aggregazione dei dati.

Le sezioni seguenti descrivono l’elaborazione di un messaggio da parte della **Shaper traffico e-mail** componente.

### Consegna messaggi {#message-delivery}

Quando un messaggio viene inviato, ci sono 3 risultati possibili:

1. **Completato**: invio del messaggio completato. Il messaggio viene aggiornato.
1. **Messaggio non riuscito**: il server contattato ha rifiutato il messaggio per il destinatario scelto. Questo risultato corrisponde ai codici restituiti da 550 a 599, ma è possibile definire delle eccezioni.
1. **Sessione non riuscita** (per 5.11 verso l&#39;alto): se **mta** riceve una risposta a questo messaggio, il messaggio viene abbandonato (consulta [Abbandono del messaggio](#message-abandonment)). Il messaggio viene inviato a un altro percorso o impostato su in sospeso se non sono disponibili altri percorsi (consulta [Messaggio in sospeso](#message-pending)).

   >[!NOTE]
   >
   >A **path** è una connessione tra Adobe Campaign **mta** e il target **mta**. Adobe Campaign **mta** può scegliere tra diversi IP iniziali e diversi IP di dominio di destinazione.

### Abbandono del messaggio {#message-abandonment}

I messaggi abbandonati vengono restituiti al **mta** e non sono più gestiti dal **madre**.

La **mta** decide la procedura per questo messaggio (recupero, abbandono, quarantena, ecc.) a seconda del codice di risposta e delle regole.

### Messaggio in sospeso {#message-pending}

Viene visualizzato un messaggio quando arriva nella coda attiva e non sono disponibili percorsi.

Un percorso viene generalmente contrassegnato come non disponibile per un periodo di tempo variabile dopo un errore di connessione. Il periodo di indisponibilità dipende dalla frequenza e dall’età degli errori.

## Configurazione del server di statistica {#statistics-server-configuration}

Il server di statistiche può essere utilizzato da diverse istanze: deve essere configurato in modo indipendente dalle istanze che lo utilizzeranno.

Inizia definendo il database Adobe Campaign che ospiterà la configurazione.

### Avvia la configurazione {#start-configuration}

Per impostazione predefinita, la **stat** modulo avviato per ogni istanza. Quando le istanze vengono raggruppate sullo stesso computer o quando le istanze condividono lo stesso indirizzo IP, viene utilizzato un singolo server di statistiche: gli altri devono essere disabilitati.

### Definizione della porta server {#definition-of-the-server-port}

Per impostazione predefinita, il server di statistiche ascolta la porta 7777. Questa porta può essere modificata nel **serverConf.xml** file. Tutti i parametri disponibili nel **serverConf.xml** sono elencati in [sezione](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## Configurazione MX {#mx-configuration}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](../../delivery/using/sending-with-enhanced-mta.md), **[!UICONTROL MX management]** le regole di velocità effettiva di consegna non vengono più utilizzate. L’MTA avanzato utilizza le proprie regole MX che gli consentono di personalizzare il throughput in base al dominio in base alla reputazione cronologica dell’e-mail e al feedback in tempo reale proveniente dai domini in cui invii e-mail.

### Informazioni sulle regole MX {#about-mx-rules}

>[!NOTE]
>
>Questa sezione e le sezioni seguenti si applicano solo alle installazioni on-premise e alle installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign.

Le regole MX (Mail eXchanger) sono regole che gestiscono la comunicazione tra un server di invio e un server di ricezione.

Queste regole vengono ricaricate automaticamente ogni mattina alle 6 del mattino (ora del server) per fornire regolarmente l&#39;istanza del client.

A seconda delle capacità materiali e della politica interna, un ISP accetta un numero predefinito di connessioni e messaggi all&#39;ora. Queste variabili possono essere modificate automaticamente dal sistema ISP a seconda della reputazione dell’IP e del dominio di invio. Attraverso la sua piattaforma di recapito messaggi, Adobe Campaign gestisce più di 150 regole specifiche da parte dell’ISP e, inoltre, una regola generica per altri domini.

Il numero massimo di connessioni non dipende esclusivamente dal numero di indirizzi IP pubblici utilizzati dall’MTA.

Ad esempio, se hai consentito 5 connessioni nelle regole MX e hai configurato 2 IP pubblici, potresti pensare che non puoi avere più di 10 connessioni aperte contemporaneamente a questo dominio. Questo non è vero, infatti il numero massimo di connessioni si riferisce a un percorso e un percorso che è una combinazione di uno dei nostri IP pubblici MTA e un IP pubblico dell’MTA del cliente.

Nell’esempio seguente, l’utente dispone di due indirizzi IP pubblici configurati e il dominio è yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

I record MX per yahoo.com ci dicono che yahoo.com ha 3 Scambiatori di posta. Per collegare lo scambiatore di posta peer, l&#39;MTA richiederà il suo indirizzo IP dal DNS.

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

Per questo record, l’utente può contattare 8 indirizzi IP peer. Poiché l’utente dispone di 2 indirizzi IP pubblici, questo dà loro 8 * 2 = 16 combinazioni per raggiungere i server di posta yahoo.com. Ciascuna di queste combinazioni è denominata percorso.

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

Nell’esempio seguente, l’utente ha un limite di 10.000 messaggi all’ora per un determinato dominio, ma la capacità effettiva MTA è superiore a questo limite.

In questo caso, il traffico viene suddiviso in 12 periodi di 5 minuti per ogni ora e il limite reale è di 833 messaggi per periodo.

Questi messaggi verranno inviati il più rapidamente possibile.

![](assets/s_ncs_traffic_shaping.png)

### Configurazione della gestione MX {#configuring-mx-management}

Le regole da rispettare per MX sono definite nella **[!UICONTROL MX management]** documento **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nodo dell&#39;albero.

Se la **[!UICONTROL MX management]** il documento non esiste nel nodo, è possibile crearlo manualmente. Per eseguire questa operazione:

1. Crea un nuovo set di regole di posta elettronica.
1. Scegli la **[!UICONTROL MX management]** modalità.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Invio **defaultMXRules** in **[!UICONTROL Internal name]** campo .

Per tenere conto delle modifiche, è necessario riavviare il server delle statistiche.

Per ricaricare la configurazione senza riavviare il server di statistiche, utilizzare il seguente comando sul computer che ospita il server: `nlserver stat -reload`

>[!NOTE]
>
>Questa riga di comando è da preferirsi a **riavvio del server**. Impedisce la perdita delle statistiche raccolte prima del riavvio ed evita picchi d&#39;uso che possono andare contro le quote definite nelle regole MX.

### Configurazione delle regole MX {#configuring-mx-rules}

La **[!UICONTROL MX management]** in un documento sono elencati tutti i domini collegati a una regola MX.

Queste regole vengono applicate in sequenza: viene applicata la prima regola la cui maschera MX è compatibile con la MX di destinazione.

I seguenti parametri disponibili per ogni regola sono:

* **[!UICONTROL MX mask]**: dominio in cui viene applicata la regola. Ogni regola definisce una maschera dell&#39;indirizzo per l&#39;MX. Qualsiasi MX il cui nome corrisponde a questa maschera è pertanto idoneo. La maschera può contenere &quot;*&quot; e &quot;?&quot; caratteri generici.

   Ad esempio, i seguenti indirizzi:

   * a.mx.yahoo.com
   * b.mx.yahoo.com
   * c.mx.yahoo.com

   sono compatibili con le seguenti maschere:

   * *.yahoo.com
   * ?.mx.yahoo.com

   Ad esempio, per l’indirizzo e-mail foobar@gmail.com, il dominio è gmail.com e il record MX è:

   ```
   gmail.com mail exchanger = 20 alt2.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 10 alt1.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 40 alt4.gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 5  gmail-smtp-in.l.google.com.
   gmail.com mail exchanger = 30 alt3.gmail-smtp-in.l.google.com.
   ```

   In questo caso, la regola MX `*.google.com` verrà utilizzato. Come puoi vedere, la maschera della regola MX non corrisponde necessariamente al dominio nella posta. Le regole MX applicate per gli indirizzi e-mail gmail.com saranno quelli con la maschera `*.google.com`.

* **[!UICONTROL Range of identifiers]**: questa opzione ti consente di indicare gli intervalli di identificatori (publicID) per i quali si applica la regola. Puoi specificare:

   * Numero: la regola si applica solo a publicId,
   * Un intervallo di numeri (**numero1-numero2**): la regola si applica a tutti gli publicID tra questi due numeri.

   >[!NOTE]
   >
   >Se il campo è vuoto, la regola si applica a tutti gli identificatori.

   Un ID pubblico è un identificatore interno di un IP pubblico utilizzato da uno o più MTA. Questi ID sono definiti nei server MTA nel **config-instance.xml** file.

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: definisce l&#39;ambito delle proprietà per questa regola MX. Quando questa opzione è selezionata, tutti i parametri vengono condivisi su tutti gli IP disponibili nell’istanza. Se questa opzione è deselezionata, le regole MX vengono definite per ogni IP. Il numero massimo di messaggi viene moltiplicato per il numero di IP disponibili.
* **[!UICONTROL Maximum number of connections]**: numero massimo di connessioni simultanee al dominio del mittente.
* **[!UICONTROL Maximum number of messages]**: numero massimo di messaggi che possono essere inviati su una connessione. Quando i messaggi superano questo numero, la connessione viene chiusa e ne viene aperta una nuova.
* **[!UICONTROL Messages per hour]**: numero massimo di messaggi che possono essere inviati nel dominio del mittente in un&#39;ora.
* **[!UICONTROL Connection time out]**: soglia di tempo per la connessione a un dominio.

   >[!NOTE]
   >
   >Windows può emettere un **timeout** prima di questa soglia, che dipende dalla versione di Windows in uso.

* **[!UICONTROL Timeout Data]**: tempo massimo di attesa dopo l’invio del contenuto del messaggio (sezione DATI del protocollo SMTP).
* **[!UICONTROL Timeout]**: tempo massimo di attesa per altri scambi con il server SMTP.
* **[!UICONTROL TLS]**: Il protocollo TLS, che ti consente di crittografare le consegne delle e-mail, può essere abilitato in modo selettivo. Per ogni maschera MX sono disponibili le seguenti opzioni:

   * **[!UICONTROL Default configuration]**: Si tratta della configurazione generale specificata nel file di configurazione serverConf.xml che viene applicata.

      >[!IMPORTANT]
      >
      >Si sconsiglia di modificare la configurazione predefinita.

   * **[!UICONTROL Disabled]** : I messaggi vengono inviati sistematicamente senza cifratura.
   * **[!UICONTROL Opportunistic]** : La consegna del messaggio viene crittografata se il server ricevente (SMTP) può generare il protocollo TLS.

Esempio di configurazione:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

>[!NOTE]
>
>Per ulteriori informazioni sull’utilizzo dei server MX con Adobe Campaign, consulta [questa sezione](../../installation/using/using-mx-servers.md).

### Gestione dei formati e-mail {#managing-email-formats}

Puoi definire il formato dei messaggi inviati, in modo che il contenuto visualizzato si adatti automaticamente in base al dominio dell’indirizzo di ciascun destinatario.

Per eseguire questa operazione, vai alla pagina **[!UICONTROL Management of email formats]** documento, che si trova in **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Questo documento contiene un elenco di tutti i domini predefiniti corrispondenti ai formati giapponesi gestiti da Adobe Campaign. Per ulteriori informazioni, consulta [presente documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

La **Struttura MIME** Il parametro (Multipurpose Internet Mail Extensions) ti consente di definire la struttura del messaggio che verrà inviata ai diversi client di posta elettronica. Sono disponibili tre opzioni:

* **Multipart**: Il messaggio viene inviato in formato testo o HTML. Se il formato HTML non viene accettato, il messaggio potrà comunque essere visualizzato in formato testo.

   Per impostazione predefinita, la struttura multiparte è **multiparte/alternativa**, ma diventa automaticamente **multiparte/correlata** quando viene aggiunta un’immagine al messaggio. Alcuni fornitori si aspettano che **multiparte/correlata** per impostazione predefinita, il **[!UICONTROL Force multipart/related]** questo formato viene imposto anche se non è collegata alcuna immagine.

* **HTML**: Viene inviato un messaggio solo per HTML. Se il formato HTML non viene accettato, il messaggio non verrà visualizzato.
* **Testo**: Viene inviato un messaggio in formato solo testo. Il vantaggio dei messaggi in formato testo è la loro dimensione molto piccola.

Se la **[!UICONTROL Image inclusion]** questa opzione è abilitata e viene visualizzata direttamente nel corpo dell’e-mail. Le immagini verranno quindi caricate e i collegamenti URL saranno sostituiti dal loro contenuto.

Questa opzione è utilizzata in particolare dal mercato giapponese per **Deco-mail**, **Decorare la posta** o **Decoration Mail**. Per ulteriori informazioni, consulta [presente documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!IMPORTANT]
>
>L’inserimento di immagini in un messaggio e-mail ne aumenta notevolmente le dimensioni.

## Configurazione del server di consegna {#delivery-server-configuration}

### Sincronizzazione dell&#39;orologio {#clock-synchronization}

Gli orologi di tutti i server che compongono la piattaforma Adobe Campaign (incluso il database) devono essere sincronizzati e i relativi sistemi devono essere impostati sullo stesso fuso orario.

### Coordinate del server di statistiche {#coordinates-of-the-statistics-server}

L&#39;indirizzo del server di statistiche deve essere fornito nella **mta**.

La **statServerAddress** proprietà **mta** elemento della configurazione consente di specificare l’indirizzo e il numero della porta da utilizzare.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Per utilizzare il server di statistiche sullo stesso computer, è necessario immettere almeno il nome del computer con il **localhost** valore:

```
 <mta statServerAddress="localhost">
```

>[!IMPORTANT]
>
>Se questo campo non viene compilato, la variabile **mta** non inizierà.

### Elenco di indirizzi IP da utilizzare {#list-of-ip-addresses-to-use}

La configurazione relativa alla gestione del traffico si trova nella **mta/child/smtp** elemento del file di configurazione.

Per ogni **IPAffinity** è necessario dichiarare gli indirizzi IP che possono essere utilizzati per il computer.

Esempio:

```
<IPAffinity localDomain="<domain>" name="default">
  <IP address="192.168.0.11" publicId="1" weight="5"/>
  <IP address="192.168.0.12" heloHost="revdns1.campaign.com" publicId="2" weight="5"/>
  <IP address="192.168.0.13" publicId="3" weight="1"/>
</IPAffinity>
```

I parametri sono i seguenti:

* **indirizzo**: si tratta dell&#39;indirizzo IP del computer host MTA da utilizzare.
* **heloHost**: questo identificatore rappresenta l’indirizzo IP visualizzato dal server SMTP.

* **publicId**: queste informazioni sono utili quando un indirizzo IP è condiviso da diversi Adobe Campaign **MTA** dietro un router NAT. Il server di statistiche utilizza questo identificatore per memorizzare le statistiche di connessione e invio tra questo punto iniziale e il server di destinazione.
* **weight**: consente di definire la frequenza relativa di utilizzo dell’indirizzo. Per impostazione predefinita, tutti gli indirizzi hanno un peso uguale a 1.

>[!NOTE]
>
>Nel file serverConf.xml , è necessario verificare che un IP corrisponda a un singolo host con un identificatore univoco (public_id). Non può essere mappato su più host, il che potrebbe causare problemi di limitazione della consegna.

Nell’esempio precedente, in condizioni normali, gli indirizzi saranno distribuiti come segue:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Se, ad esempio, il primo indirizzo non può essere utilizzato per un dato MX, i messaggi verranno inviati come segue:

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**: ti consente di riservare questo indirizzo IP per le e-mail appartenenti a un dominio specifico. Elenco di maschere che possono contenere uno o più caratteri jolly (&#39;*&#39;). Se l&#39;attributo non è specificato, tutti i domini possono utilizzare questo indirizzo IP.

   Esempio: **includeDomains=&quot;wanadoo.com,arancione.com,yahoo.*&quot;**

* **excludeDomains**: esclude un elenco di domini per questo indirizzo IP. Questo filtro viene applicato dopo la **includeDomains** filtro.

   ![](assets/s_ncs_install_mta_ips.png)

## Ottimizzazione dell’invio di e-mail {#email-sending-optimization}

Architettura interna di Adobe Campaign **mta** ha un impatto sulla configurazione per l’ottimizzazione della consegna e-mail. Di seguito sono riportati alcuni suggerimenti su come migliorare le consegne.

### Regolare il parametro maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter}

La **maxWaitingMessages** Il parametro indica il numero massimo di messaggi preparati in anticipo dal **madre**. I messaggi vengono cancellati dall’elenco solo una volta inviati o abbandonati.

Questo parametro è molto importante e particolarmente critico se i messaggi non vengono ordinati per dominio.

Una volta che **maxWorkingSetMb** (256) viene raggiunta la soglia, il server di consegna smette di inviare messaggi. Le prestazioni diminuiranno significativamente fino a quando **madre** si riavvia. Per evitare questo problema, puoi aumentare la soglia di **maxWorkingSetMb** o diminuire la soglia del **maxWaitingMessages** parametro .

La **maxWorkingSetMb** viene calcolato empiricamente moltiplicando il numero massimo di messaggi per la dimensione media del messaggio e moltiplicando il risultato per 2,5. Ad esempio, se un messaggio ha una dimensione media di 50 kB e il valore **maxWaitingMessages** è uguale a 1.000, la memoria utilizzata sarà media di 125 MB.

### Regolare il numero di elementi figlio {#adjust-the-number-of-mtachild}

Il numero di figli non deve superare il numero di processori presenti nella macchina (circa 1000 sessioni). Si consiglia di non superare gli 8 **madre**. È quindi possibile aumentare il numero di messaggi per **bambino** (**maxMsgPerChild**) per ottenere un ciclo di vita sufficiente.
