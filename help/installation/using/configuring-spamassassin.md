---
title: Configurazione di SpamAssassin
seo-title: Configurazione di SpamAssassin
description: Configurazione di SpamAssassin
seo-description: null
page-status-flag: never-activated
uuid: 327548c0-d621-4417-9fc9-b0bf30251dc0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: aa37bdc6-0f85-4eca-859f-e8b15083cfb5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: edb99a13d8b2f39f991e8ceb6718291d92504242

---


# Configurazione di SpamAssassin{#configuring-spamassassin}

>[!NOTE]
>
>Alcune configurazioni possono essere eseguite solo da Adobe per le distribuzioni ospitate da Adobe. Ad esempio, per accedere ai file di configurazione del server e dell&#39;istanza. Per ulteriori informazioni sulle diverse distribuzioni, consultate la sezione Modelli [di](../../installation/using/hosting-models.md) hosting o [questo articolo](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html).

## Panoramica {#overview}

SpamAssassin è un software progettato per filtrare le e-mail indesiderate. Insieme a questo software, Adobe Campaign può assegnare un punteggio alle e-mail e stabilire se è probabile che un messaggio venga considerato indesiderabile prima dell&#39;avvio della consegna. A tal fine, SpamAssassin deve essere installato e configurato sui server applicazioni di Adobe Campaign e richiede il funzionamento di un certo numero di moduli Perl aggiuntivi.

L&#39;implementazione e l&#39;integrazione di SpamAssassin come descritto in questo capitolo si basano sull&#39;installazione software predefinita, così come le regole di filtraggio e punteggio, che sono quelle fornite da SpamAssassin senza alcuna modifica o ottimizzazione. L&#39;attribuzione del punteggio e la qualifica del messaggio si basano esclusivamente sulla configurazione delle opzioni SpamAssassin e sulle regole di filtraggio. Gli amministratori di rete sono responsabili dell&#39;adattamento alle esigenze aziendali.

>[!CAUTION]
>
>La qualifica delle e-mail come indesiderabili da SpamAssassin si basa interamente su regole di filtraggio e punteggio.
>
>Queste regole devono pertanto essere aggiornate almeno una volta al giorno affinché l&#39;installazione di SpamAssassin e la sua integrazione in Adobe Campaign siano completamente funzionanti e per garantire la pertinenza dei punteggi assegnati alle consegne prima dell&#39;invio.
>
>Questo aggiornamento è responsabilità dell&#39;amministratore del server che ospita SpamAssassin.

L&#39;utilizzo di SpamAssassin in Adobe Campaign fornisce un&#39;indicazione sul possibile comportamento dei server di posta che utilizzano SpamAssassin quando ricevono e-mail inviate da Adobe Campaign. Tuttavia, è possibile che i server di posta dei provider di Internet o dei server di posta elettronica online considerino ancora indesiderabili i messaggi inviati da Adobe Campaign.

La distribuzione di SpamAssassin e dei suoi moduli in Perl richiede l&#39;utilizzo di server applicazioni Adobe Campaign dotati di accesso a Internet tramite una connessione HTTP (flusso TCP/80).

## Installazione su un computer Windows {#installing-on-a-windows-machine}

Per installare e configurare SpamAssassin in Windows per abilitare l&#39;integrazione con Adobe Campaign, effettua i seguenti passaggi:

1. Installazione di SpamAssassin
1. Integrare SpamAssassin in Adobe Campaign

### Installazione di SpamAssassin {#installing-spamassassin}

1. Effettuate la connessione al portale [](http://support.neolane.net) Extranet utilizzando le credenziali utente.
1. Andate al centro **** Download, quindi individuate la sezione **Strumenti** nella pagina.
1. Scaricate il file **Spam Assassin (Installazione di Windows) (1.0)** .
1. Copiate questo file nel server Adobe Campaign, quindi decomprimetelo.

   >[!NOTE]
   >
   >È possibile decomprimere il file ovunque si desideri, purché il percorso sia composto dai seguenti caratteri di espressione regolare: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Il percorso di installazione non deve contenere spazi bianchi.

1. Passate al file in cui avete decompresso il file, quindi fate doppio clic sul file **run_me.bat** per avviare lo script di installazione.

   Se viene visualizzata una shell di Windows e continua a essere visualizzata per alcuni secondi, attendere il completamento dell&#39;installazione e dell&#39;aggiornamento, quindi fare clic su **Invio**.

   Se Windows Shell non viene visualizzato o non viene visualizzato prima della scomparsa immediata, procedere come segue: fare doppio clic sul file **portableShell.bat** per visualizzare una shell di Windows e verificare che il percorso Shell corrisponda alla cartella in cui è stato decompresso il file **spamassassin.zip** . In caso contrario, accedete utilizzando il comando **cd** .

   Immettere **run_me.bat** , quindi fare clic su **Enter** per avviare il processo di installazione e aggiornamento. L&#39;operazione restituisce uno dei seguenti valori per indicare il risultato dell&#39;aggiornamento.

   * **0**: è stato effettuato un aggiornamento.
   * **1**: Nessun nuovo aggiornamento disponibile.
   * **2**: nessun nuovo aggiornamento disponibile.
   * **3**: aggiornamento non riuscito durante la verifica preliminare.
   * **4** o più: si è verificato un errore.

1. Per verificare che l&#39;installazione SpamAssassin sia stata eseguita correttamente, utilizzare il test GTUBE (Generic Test for Unsolicited Bulk Email) utilizzando la seguente procedura:

   1. Create un file di testo e salvatelo in **C:\TestSpamMail.txt**.
   1. Inserire il contenuto seguente nel file:

      ```
      Subject: Test Spam Mail (GTUBE)
      Message-ID: <1010101@example.net>
      Date: MM-DD-YY
      From: Sender <sender@example.net>
      To: Recipient <recipient@example.net>
      Precedence: junk
      MIME-Version: 1.0
      Content-Type: text/plain; charset=us-ascii
      Content-Transfer-Encoding: 7bit
      
      XJS*C4JDBQADN1.NSBN3*2IDNEN*GTUBE-STANDARD-ANTI-UBE-TEST-EMAIL*C.34X
      ```

   1. Fare doppio clic sul file **portatileShell.bat** per visualizzare una shell di Windows, quindi avviare il seguente comando (o &quot;`<root>`&quot; indica la cartella creata quando si decomprime il file **spamassassin.zip** ):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Il contenuto di questa e-mail di test attiva un punteggio di 1.000 punti per SpamAssassin. Ciò significa che è stato rilevato come indesiderabile e che l&#39;installazione ha avuto successo ed è completamente funzionante.

### Integrazione di SpamAssassin in Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Modificate il **`[INSTALL]/conf/serverConf.xml`** file. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).
1. Modificate il valore dell&#39;attributo **spamCheck** degli elementi **command** nel nodo **Web** . A questo scopo, eseguite il comando seguente:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Tutti i percorsi devono essere assoluti.

   Arrestate e avviate il **[!UICONTROL Adobe Campaign]** servizio.

1. Per verificare l’integrazione di SpamAssassin in Adobe Campaign, utilizza un test GTBUE (Test generico per e-mail di massa non richieste):

   Fare doppio clic sul file **portableshell.bat** . Questo attiva la visualizzazione di una shell di Windows. Quindi eseguite il comando seguente:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Il contenuto di questa e-mail di test attiva 1.000 punti assegnati da SpamAssassin. Ciò significa che è stato rilevato come indesiderabile e che l&#39;integrazione in Adobe Campaign è stata un successo ed è completamente funzionale.

1. Aggiorna regole di filtraggio e valutazione SpamAssassin

   Per un aggiornamento iniziale delle regole di filtraggio e punteggio, avviate **portabilitàShell.bat** ed eseguite il comando seguente:

   ```
   sa-update --no-gpg
   ```

   Per eseguire un aggiornamento automatico delle regole di filtraggio e punteggio, utilizzare lo stesso comando in un&#39;attività di sistema pianificata:

   ```
   sa-update --no-gpg
   ```

## Installazione su un computer Linux {#installing-on-a-linux-machine}

### Procedura di installazione in Debian {#installation-steps-in-debian}

* Se necessario, installa Perl e SpamAssassin utilizzando il seguente comando:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* Nel file **serverConf.xml** (disponibile in `/usr/local/[INSTALL]/nl6/conf/`), modificate la riga **spamCheck** come segue:

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Procedura di installazione in RHEL/CentOS {#installation-steps-in-rhel-centos}

Se necessario, installare Perl e recuperare i pacchetti utilizzando CPAN:

```
cpan Digest::SHA1
cpan HTML::Parser
cpan Net::DNS
cpan Mail::SPF 
cpan XML::LibXML
cpan XML::Writer
cpan Mail::SpamAssassin
```

### Aggiornamento delle regole filtro {#updating-filter-rules}

Le regole del filtro possono essere aggiornate automaticamente utilizzando lo strumento **sa-update** . Per ulteriori informazioni, consultare il sito ufficiale SpamAssassin [http://spamassassin.apache.org/](http://spamassassin.apache.org/) .

In Debian, gli aggiornamenti avvengono automaticamente ogni giorno.

In caso contrario (ad esempio, quando Debian viene installato manualmente), create uno script per automatizzare gli aggiornamenti delle regole.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Inserire questo script in **crontab** utilizzando il comando seguente:

```
crontab-e
```

### Ottimizzazione delle prestazioni {#performance-optimization}

Per migliorare le prestazioni in Linux, modificate il file **/etc/spamassassin/local.cf** e aggiungete la seguente riga alla fine del file:

```
dns_available no
```

