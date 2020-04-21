---
title: Distribuzione tramite e-mail
seo-title: Distribuzione tramite e-mail
description: Distribuzione tramite e-mail
seo-description: null
page-status-flag: never-activated
uuid: 983aec6b-60f6-4c9b-a75a-1693958626c2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: 86c18986-1f65-40ff-80dc-1fbff37f406d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 631e29bd6e59b8ae46084dee3a1d470916a2032b

---


# Configurazioni e-mail tecniche{#email-deliverability}

## Panoramica {#overview}

La sezione seguente fornisce una panoramica della configurazione necessaria per controllare l&#39;output delle istanze di Adobe Campaign quando si distribuiscono le e-mail.

>[!NOTE]
>
>Alcune configurazioni possono essere eseguite solo da Adobe per le distribuzioni ospitate da Adobe, ad esempio per accedere ai file di configurazione del server e dell&#39;istanza. Per ulteriori informazioni sulle diverse distribuzioni, consultate la sezione Modelli [di](../../installation/using/hosting-models.md) hosting o [questo articolo](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

Per ulteriori informazioni sui concetti e sulle best practice relativi alla recapito, consulta questa [sezione](../../delivery/using/about-deliverability.md).

Tutte le raccomandazioni tecniche relative all&#39;invio e alla ricezione efficiente di e-mail da parte di una piattaforma Adobe Campaign sono disponibili in questa [sezione](../../delivery/using/technical-recommendations.md).

## Principio di funzionamento {#operating-principle}

È possibile controllare l&#39;output di una o più istanze di Adobe Campaign per limitare il numero di e-mail inviate a seconda di un dominio. Ad esempio, potete limitare l&#39;output a 20.000 all&#39;ora per gli indirizzi **yahoo.com** , mentre configurate 100.000 messaggi all&#39;ora per tutti gli altri domini.

L&#39;output dei messaggi deve essere controllato per ogni indirizzo IP utilizzato dai server di consegna (**mta**). Diversi **dati** suddivisi su più computer e appartenenti a diverse istanze di Adobe Campaign possono condividere lo stesso indirizzo IP per la consegna delle e-mail: è necessario impostare un processo per coordinare l&#39;uso di questi indirizzi IP.

Questo è ciò che il modulo **stat** fa: inoltra tutte le richieste di connessione e i messaggi da inviare ai server di posta elettronica per un insieme di indirizzi IP. Il server delle statistiche tiene traccia delle consegne e può abilitare o disabilitare l&#39;invio in base alle quote impostate.

![](assets/s_ncs_install_mta.png)

* Il server delle statistiche (**stat**) è collegato a una base Adobe Campaign per caricare la configurazione.
* I server di distribuzione (**mta**) utilizzano un UDP per contattare un server di statistiche che non appartiene sempre alla propria istanza.

### Server di distribuzione {#delivery-servers}

Il modulo **mta** distribuisce i messaggi ai suoi moduli figlio **principale** . Ogni **nodo secondario** prepara i messaggi prima di richiedere un&#39;autorizzazione al server delle statistiche e inviarli.

La procedura è la seguente:

1. Il **tag** seleziona i messaggi idonei e assegna loro un **elemento secondario** principale disponibile.
1. Il **nodo secondario** carica tutte le informazioni necessarie per la creazione del messaggio (contenuto, elementi di personalizzazione, allegati, immagini, ecc.) e inoltra il messaggio all&#39; **e-mail Traffic Shaper**.
1. Non appena lo shaper del traffico e-mail riceve l&#39;autorizzazione del server di statistiche (stato **smtp**), il messaggio viene inviato al destinatario.

![](assets/s_ncs_install_email_traffic_shaper.png)

### Statistiche e limitazioni del server e-mail {#email-server-statistics-and-limitations}

Il server di statistiche mantiene le seguenti statistiche per ogni server di posta elettronica che riceve i messaggi:

* numero di connessioni point-in-time aperte,
* Numero di messaggi inviati nell&#39;ultima ora,
* Frequenza delle connessioni riuscite/rifiutate,
* Frequenza delle connessioni a server non raggiungibili.

Allo stesso tempo, il modulo carica un elenco di limitazioni per alcuni server e-mail:

* Numero massimo di connessioni simultanee,
* Numero massimo di messaggi all&#39;ora,
* Numero massimo di messaggi per connessione.

### Gestione degli indirizzi IP {#managing-ip-addresses}

Il server di statistiche può combinare più istanze o più computer con lo stesso indirizzo IP pubblico. Non è quindi collegato a un’istanza specifica, ma deve contattare un’istanza per recuperare le limitazioni per dominio.

Le statistiche di consegna sono conservate per ciascun MX di destinazione e per ciascun IP di origine. Ad esempio, se il dominio di destinazione ha 5 MX e la piattaforma può utilizzare 3 indirizzi IP diversi, il server può gestire fino a 15 serie di indicatori per questo dominio.

L&#39;indirizzo IP di origine corrisponde all&#39;indirizzo IP pubblico, ovvero all&#39;indirizzo visualizzato dal server e-mail remoto. Questo indirizzo IP può essere diverso dall&#39;indirizzo della macchina che ospita il **mta**, se è fornito un router NAT. Per questo motivo il server di statistiche utilizza un identificatore che corrisponde all’IP pubblico (**publicId**). L&#39;associazione tra l&#39;indirizzo locale e questo identificatore viene dichiarata nel file di configurazione **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

## Controllo output di consegna {#delivery-output-controlling}

Per inviare messaggi ai server e-mail, il componente **E-mail Traffic Shaper** richiede una connessione dal server di statistiche. Una volta accettata la richiesta, la connessione viene aperta.

Prima di inviare i messaggi, il modulo richiede i &#39;token&#39; dal server. Si tratta in genere di insiemi di almeno 10 token che riducono il numero di query al server.

Il server salva tutte le statistiche relative alle connessioni e alle consegne. In caso di riavvio, le informazioni vengono temporaneamente perse: ogni client conserva una copia locale delle statistiche di invio e le restituisce regolarmente al server (ogni 2 minuti). Il server può quindi riaggregare i dati.

Nelle sezioni seguenti viene descritta l’elaborazione di un messaggio da parte del componente **Email Traffic Shaper** (Condivisione traffico e-mail).

### Invio di messaggi {#message-delivery}

Quando un messaggio viene inviato, sono disponibili 3 risultati:

1. **Successo**: il messaggio è stato inviato correttamente. Il messaggio viene aggiornato.
1. **Messaggio non riuscito**: il server contattato ha rifiutato il messaggio per il destinatario scelto. Questo risultato corrisponde ai codici restituiti da 550 a 599, ma è possibile definire eccezioni.
1. **Sessione non riuscita** (per 5.11 verso l&#39;alto): se la **mta** riceve una risposta per questo messaggio, il messaggio viene abbandonato (fare riferimento a [Messaggio di abbandono](#message-abandonment)). Il messaggio viene inviato a un altro percorso o impostato su in sospeso se non sono disponibili altri percorsi (fare riferimento a [Messaggio in sospeso](#message-pending)).

   >[!NOTE]
   >
   >Un **percorso** è una connessione tra l&#39; **oggetto** di Adobe Campaign e l&#39; **elemento** di destinazione. Il **tag** di Adobe Campaign può scegliere tra diversi IP iniziali e diversi IP di dominio di destinazione.

### Abbandono dei messaggi {#message-abandonment}

I messaggi abbandonati vengono restituiti al **tag** e non vengono più gestiti dal **master**.

Il **MTA** decide la procedura per questo messaggio (recupero, abbandono, quarantena, ecc.) in base al codice di risposta e alle regole.

### Messaggio in sospeso {#message-pending}

Quando arriva nella coda attiva, un messaggio viene chiuso e non sono disponibili percorsi.

Un percorso è generalmente contrassegnato come non disponibile per un periodo di tempo variabile dopo un errore di connessione. Il periodo di indisponibilità dipende dalla frequenza e dall&#39;età degli errori.

## Configurazione del server di statistiche {#statistics-server-configuration}

Il server di statistiche può essere utilizzato da più istanze: deve essere configurato in modo indipendente dalle istanze che lo utilizzeranno.

Per iniziare, definisci il database di Adobe Campaign che ospiterà la configurazione.

### Avvia configurazione {#start-configuration}

Per impostazione predefinita, il modulo **stat** è avviato per ogni istanza. Quando le istanze vengono mutualizzate sullo stesso computer, o quando le istanze condividono lo stesso indirizzo IP, viene utilizzato un singolo server di statistiche: gli altri devono essere disabilitati.

### Definizione della porta del server {#definition-of-the-server-port}

Per impostazione predefinita, il server delle statistiche ascolta la porta 7777. Questa porta può essere modificata nel file **serverConf.xml** . Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).

```
<stat port="1234"/>
```

## Configurazione MX {#mx-configuration}

### Informazioni sulle regole MX {#about-mx-rules}

Le regole MX (Mail eXchanger) sono regole che gestiscono la comunicazione tra un server di invio e un server di ricezione.

>[!IMPORTANT]
>
>Per le installazioni ospitate o ibride, se avete effettuato l’aggiornamento all’MTA avanzato, le regole di **[!UICONTROL MX management]** consegna effettiva non vengono più utilizzate. L&#39;MTA avanzata utilizza le proprie regole MX che le consentono di personalizzare il throughput in base al dominio in base alla reputazione storica dell&#39;e-mail e al feedback in tempo reale proveniente dai domini in cui invii le e-mail.
>
>Per ulteriori informazioni sull&#39;MTA avanzata di Adobe Campaign, consulta questo [documento](https://helpx.adobe.com/campaign/kb/acc-campaign-enhanced-mta.html).

Queste regole vengono ricaricate automaticamente ogni mattina alle 6 del mattino (ora del server) per fornire regolarmente l&#39;istanza del client.

A seconda delle capacità materiali e della politica interna, un ISP accetta un numero predefinito di connessioni e messaggi all&#39;ora. Queste variabili possono essere modificate automaticamente dal sistema ISP a seconda della reputazione dell&#39;IP e del dominio di invio. Attraverso la sua piattaforma di recapito, Adobe Campaign gestisce più di 150 regole specifiche dall&#39;ISP e, inoltre, una regola generica per altri domini.

Il numero massimo di connessioni non dipende esclusivamente dal numero di indirizzi IP pubblici utilizzati dall&#39;MTA.

Ad esempio, se sono state consentite 5 connessioni nelle regole MX e avete configurato 2 IP pubblici, potreste pensare che non sia possibile avere più di 10 connessioni contemporaneamente aperte a questo dominio. Questo non è vero, infatti il numero massimo di connessioni si riferisce a un percorso e un percorso che è una combinazione di uno dei nostri IP pubblici MTA e un IP pubblico dell&#39;MTA del cliente.

Nell&#39;esempio seguente, l&#39;utente ha due indirizzi IP pubblici configurati e il dominio è yahoo.com.

```
user:~ user$ host -t mx yahoo.com
                yahoo.com mail is handled by 1 mta5.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta6.am0.yahoodns.net.
                yahoo.com mail is handled by 1 mta7.am0.yahoodns.net.
```

I record MX per yahoo.com ci dicono che yahoo.com ha 3 Mail Exchangers. Per collegare lo scambiatore di posta peer, l&#39;MTA richiederà l&#39;indirizzo IP del computer dal DNS.

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

Per questo record, l&#39;utente può contattare 8 indirizzi IP peer. Poiché ha 2 indirizzi IP pubblici questo gli dà 8 * 2 = 16 combinazioni per raggiungere i server di posta yahoo.com. Ciascuna di queste combinazioni è denominata percorso.

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

4 di questi 8 indirizzi IP sono già utilizzati in mta5 (98.136.216.26, 98.138.112.38, 63.250.192.46 e 98.136.217.203). Questo record consente all&#39;utente di utilizzare 4 nuovi indirizzi IP. Il terzo record MX farà lo stesso.

In totale, abbiamo 16 indirizzi IP remoti. In combinazione con i nostri 2 IP pubblici locali abbiamo 32 percorsi per raggiungere i server di posta yahoo.com.

>[!NOTE]
>
>Se 2 record MX fanno riferimento allo stesso indirizzo IP, questo verrà conteggiato come un percorso e non come due.

Di seguito sono riportati alcuni esempi di utilizzo delle regole MX:

![](assets/s_ncs_examples_mx_rules.png)

Nell&#39;esempio seguente, l&#39;utente ha un limite di 10.000 messaggi all&#39;ora per un determinato dominio, ma la capacità effettiva MTA è superiore a tale limite.

In questo caso, il traffico è diviso in 12 periodi di 5 minuti per ogni ora, e il limite reale è di 833 messaggi per periodo.

Questi messaggi verranno inviati il più rapidamente possibile.

![](assets/s_ncs_traffic_shaping.png)

### Configurazione della gestione MX {#configuring-mx-management}

Le regole da rispettare per MX sono definite nel **[!UICONTROL MX management]** documento del **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nodo della struttura.

Se il **[!UICONTROL MX management]** documento non esiste nel nodo, è possibile crearlo manualmente. Per eseguire questa operazione:

1. Create un nuovo set di regole per la posta elettronica.
1. Scegliere la **[!UICONTROL MX management]** modalità.

   ![](assets/s_ncs_install_mx_mgt_rule.png)

1. Immettere **defaultMXRules** nel **[!UICONTROL Internal name]** campo.

Per tenere conto delle modifiche, è necessario riavviare il server delle statistiche.

Per ricaricare la configurazione senza riavviare il server di statistiche, utilizzare il seguente comando sul computer che ospita il server: `nlserver stat -reload`

>[!NOTE]
>
>Questa riga di comando è preferibile al riavvio del **server**. Impedisce la perdita delle statistiche raccolte prima del riavvio ed evita picchi d&#39;uso che possono andare contro le quote definite nelle regole MX.

### Configurazione delle regole MX {#configuring-mx-rules}

Il **[!UICONTROL MX management]** documento elenca tutti i domini collegati a una regola MX.

Queste regole vengono applicate in sequenza: viene applicata la prima regola la cui maschera MX è compatibile con l&#39;MX di destinazione.

I seguenti parametri disponibili per ciascuna regola sono:

* **[!UICONTROL MX mask]**: dominio a cui viene applicata la regola. Ogni regola definisce una maschera di indirizzo per l&#39;MX. È pertanto ammissibile qualsiasi MX il cui nome corrisponda a questa maschera. La maschera può contenere &quot;*&quot; e &quot;?&quot; caratteri generici.

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

   In questo caso verrà utilizzata la regola MX `*.google.com` . Come potete vedere, la maschera della regola MX non corrisponde necessariamente al dominio presente nella posta. Le regole MX applicate agli indirizzi e-mail di gmail.com saranno quelli con la maschera `*.google.com`.

* **[!UICONTROL Range of identifiers]**: questa opzione consente di indicare gli intervalli di identificatori (publicID) per i quali si applica la regola. Potete specificare:

   * Numero: la regola verrà applicata solo a publicId,
   * Un intervallo di numeri (**numero1-numero2**): la regola verrà applicata a tutti gli publicID tra questi due numeri.
   >[!NOTE]
   >
   >Se il campo è vuoto, la regola si applica a tutti gli identificatori.

   Un ID pubblico è un identificatore interno di un IP pubblico utilizzato da uno o più MTA. Tali ID sono definiti nei server MTA nel file **config-instance.xml** .

   ![](assets/s_ncs_install_mta_ips.png)

* **[!UICONTROL Shared]**: definisce l&#39;ambito delle proprietà per questa regola MX. Se questa opzione è selezionata, tutti i parametri vengono condivisi su tutti gli IP disponibili nell&#39;istanza. Se questa opzione è deselezionata, le regole MX sono definite per ogni IP. Il numero massimo di messaggi viene moltiplicato per il numero di IP disponibili.
* **[!UICONTROL Maximum number of connections]**: numero massimo di connessioni simultanee al dominio del mittente.
* **[!UICONTROL Maximum number of messages]**: numero massimo di messaggi che possono essere inviati su una connessione. Quando i messaggi superano questo numero, la connessione viene chiusa e ne viene aperta una nuova.
* **[!UICONTROL Messages per hour]**: numero massimo di messaggi che possono essere inviati nel dominio del mittente in un&#39;ora.
* **[!UICONTROL Connection time out]**: soglia di tempo per la connessione a un dominio.

   >[!NOTE]
   >
   >Windows può emettere un **timeout** prima di questa soglia, che dipende dalla versione di Windows in uso.

* **[!UICONTROL Timeout Data]**: tempo massimo di attesa dopo l&#39;invio del contenuto del messaggio (sezione DATI del protocollo SMTP).
* **[!UICONTROL Timeout]**: tempo di attesa massimo per altri scambi con il server SMTP.
* **[!UICONTROL TLS]**: Il protocollo TLS, che consente di cifrare le consegne e-mail, può essere attivato in modo selettivo. Per ogni maschera MX sono disponibili le seguenti opzioni:

   * **[!UICONTROL Default configuration]**: Si tratta della configurazione generale specificata nel file di configurazione serverConf.xml applicato.

      >[!CAUTION]
      >
      >Non è consigliabile modificare la configurazione predefinita.

   * **[!UICONTROL Disabled]** : I messaggi vengono inviati sistematicamente senza crittografia.
   * **[!UICONTROL Opportunistic]** : La consegna dei messaggi è crittografata se il server di ricezione (SMTP) è in grado di generare il protocollo TLS.

Esempio di configurazione:

![](assets/s_ncs_install_mx_mgt_rule_details.png)

### Gestione dei formati e-mail {#managing-email-formats}

È possibile definire il formato dei messaggi inviati, in modo che il contenuto visualizzato si adatti automaticamente in base al dominio dell&#39;indirizzo di ciascun destinatario.

A tale scopo, passare al **[!UICONTROL Management of email formats]** documento, che si trova in **[!UICONTROL Administration]** > **[!UICONTROL Campaign management]** > **[!UICONTROL Non deliverables management]** > **[!UICONTROL Mail rule sets]**.

Questo documento contiene un elenco di tutti i domini predefiniti che corrispondono ai formati giapponesi gestiti da Adobe Campaign. Per ulteriori informazioni, consultare [questo documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

![](assets/mail_rule_sets.png)

Il parametro struttura **** MIME (Multipurpose Internet Mail Extensions) consente di definire la struttura del messaggio che verrà inviata ai diversi client di posta elettronica. Sono disponibili tre opzioni:

* **Multipart**: Il messaggio viene inviato in formato testo o HTML. Se il formato HTML non è accettato, il messaggio potrà comunque essere visualizzato in formato testo.

   Per impostazione predefinita, la struttura multiparte è **multiparte/alternativa**, ma diventa automaticamente **multiparte/correlata** quando un’immagine viene aggiunta al messaggio. Per impostazione predefinita, alcuni fornitori prevedono il formato **multiparte/correlato** . Anche se non è collegata alcuna immagine, l&#39; **[!UICONTROL Force multipart/related]** opzione impone tale formato.

* **HTML**: Viene inviato un messaggio solo HTML. Se il formato HTML non è accettato, il messaggio non verrà visualizzato.
* **Testo**: Viene inviato un messaggio in formato solo testo. I messaggi in formato testo hanno dimensioni molto ridotte.

Se l’ **[!UICONTROL Image inclusion]** opzione è attivata, queste vengono visualizzate direttamente nel corpo del messaggio e-mail. Le immagini verranno caricate e i collegamenti URL verranno sostituiti dal relativo contenuto.

Questa opzione è utilizzata in particolare dal mercato giapponese per **Deco-mail**, **Decore Mail** o **Decoration Mail**. Per ulteriori informazioni, consultare [questo documento](../../delivery/using/defining-the-email-content.md#sending-emails-on-japanese-mobiles).

>[!CAUTION]
>
>L’inserimento di immagini in un messaggio e-mail ne aumenta notevolmente le dimensioni.

## Configurazione server di consegna {#delivery-server-configuration}

### Blocca sincronizzazione {#clock-synchronization}

Gli orologi di tutti i server che compongono la piattaforma Adobe Campaign (incluso il database) devono essere sincronizzati e i loro sistemi devono essere impostati sullo stesso fuso orario.

### Coordinate del server di statistiche {#coordinates-of-the-statistics-server}

L&#39;indirizzo del server di statistiche deve essere fornito nel **tag**.

La proprietà **statServerAddress** dell&#39;elemento **mta** della configurazione consente di specificare l&#39;indirizzo e il numero della porta da utilizzare.

```
<mta statServerAddress="emailStatServer:7777">
   [...]
 </mta>
```

Per utilizzare il server di statistiche sullo stesso computer, è necessario immettere almeno il nome del computer con il valore **localhost** :

```
 <mta statServerAddress="localhost">
```

>[!CAUTION]
>
>Se questo campo non viene popolato, il **tag** non verrà avviato.

### Elenco di indirizzi IP da utilizzare {#list-of-ip-addresses-to-use}

La configurazione relativa alla gestione del traffico si trova nell&#39;elemento **mta/child/smtp** del file di configurazione.

Per ogni elemento **IPAffinity** , è necessario dichiarare gli indirizzi IP che possono essere utilizzati per il computer.

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
* **heloHost**: questo identificatore rappresenta l&#39;indirizzo IP come verrà visualizzato dal server SMTP.

* **publicId**: questa informazione è utile quando un indirizzo IP è condiviso da diversi **mtas** di Adobe Campaign dietro a un router NAT. Il server delle statistiche utilizza questo identificatore per memorizzare le statistiche di connessione e invio tra il punto iniziale e il server di destinazione.
* **peso**: consente di definire la frequenza relativa di utilizzo dell’indirizzo. Per impostazione predefinita, tutti gli indirizzi hanno uno spessore pari a 1.

>[!NOTE]
>
>Nel file serverConf.xml, è necessario verificare che un IP corrisponda a un singolo helohost con un identificatore univoco (public_id). Non può essere mappato su più host, il che potrebbe causare problemi di limitazione delle consegne.

Nell&#39;esempio precedente, con condizioni normali, gli indirizzi saranno distribuiti come segue:

    * &quot;1&quot;: 5 / (5+5+1) = 45%
    * &quot;2&quot;: 5 / (5+5+1) = 45%
    * &quot;3&quot;: 1 / (5+5+1) = 10%

Se, ad esempio, il primo indirizzo non può essere utilizzato per un dato MX, i messaggi verranno inviati come segue:

    * &quot;2&quot;: 5 / (5+1) = 83%
    * &quot;3&quot;: 1 / (5+1) = 17%

* **includeDomains**: consente di riservare questo indirizzo IP alle e-mail appartenenti a un dominio specifico. Si tratta di un elenco di maschere che possono contenere uno o più caratteri jolly (&#39;*&#39;). Se l&#39;attributo non è specificato, tutti i domini possono utilizzare questo indirizzo IP.

   Esempio: **includeDomains=&quot;wanadoo.com,arancione.com,yahoo.*&quot;**

* **excludeDomains**: esclude un elenco di domini per questo indirizzo IP. Questo filtro viene applicato dopo il filtro **includeDomains** .

   ![](assets/s_ncs_install_mta_ips.png)

## Ottimizzazione dell&#39;invio tramite e-mail {#email-sending-optimization}

L&#39;architettura interna dell&#39; **applicazione** Adobe Campaign ha un impatto sulla configurazione per ottimizzare la distribuzione delle e-mail. Di seguito sono riportati alcuni suggerimenti per migliorare le consegne.

### Regolare il parametro maxWaitingMessages {#adjust-the-maxwaitingmessages-parameter}

Il parametro **maxWaitingMessages** indica il numero massimo di messaggi preparati in anticipo dal **nodo secondario**. I messaggi vengono eliminati da questo elenco solo dopo che sono stati inviati o abbandonati.

Questo parametro è molto importante e particolarmente critico se i messaggi non sono ordinati per dominio.

Una volta raggiunta la soglia **maxWorkingSetMb** (256), il server di consegna interrompe l&#39;invio dei messaggi. Le prestazioni diminuiranno in modo significativo finché il **figlio** principale non ricomincia. Per ovviare a questo problema, potete aumentare la soglia del parametro **maxWorkingSetMb** oppure diminuire la soglia del parametro **maxWaitingMessages** .

Il parametro **maxWorkingSetMb** viene calcolato empiricamente moltiplicando il numero massimo di messaggi per la dimensione media del messaggio e moltiplicando il risultato per 2,5. Ad esempio, se un messaggio ha una dimensione media di 50 kB e il parametro **maxWaitingMessages** è uguale a 1.000, la memoria utilizzata sarà media di 125 MB.

### Regola il numero di elementi secondari {#adjust-the-number-of-mtachild}

Il numero di figli non deve superare il numero di processori nella macchina (circa 1000 sessioni). Si consiglia di non superare gli 8 **elementi figlio**. Potreste quindi aumentare il numero di messaggi per **figlio** (**maxMsgPerChild**) per ottenere una durata di vita sufficiente.
