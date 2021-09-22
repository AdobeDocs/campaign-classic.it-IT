---
product: campaign
title: Configurazione di SpamAssassin
description: Configurazione di SpamAssassin
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 2%

---

# Configurazione di SpamAssassin{#configuring-spamassassin}

![](../../assets/v7-only.svg)

>[!NOTE]
>
>Alcune configurazioni possono essere eseguite solo per Adobe per le distribuzioni ospitate da Adobe. Ad esempio, per accedere ai file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle diverse distribuzioni, consulta la sezione [Modelli di hosting](../../installation/using/hosting-models.md) o [questa pagina](../../installation/using/capability-matrix.md).

## Panoramica {#overview}

SpamAssassin è un software progettato per filtrare le e-mail indesiderate. Insieme a questo software, Adobe Campaign può assegnare un punteggio alle e-mail e determinare se è probabile che un messaggio venga considerato indesiderabile prima dell’avvio della consegna. A questo scopo, SpamAssassin deve essere installato e configurato sui server applicazioni di Adobe Campaign e richiede un certo numero di moduli Perl aggiuntivi per funzionare.

La distribuzione e l&#39;integrazione di SpamAssassin come descritto in questo capitolo si basano sull&#39;installazione software predefinita, così come le regole di filtraggio e punteggio, che sono quelle fornite da SpamAssassin senza alcuna modifica o ottimizzazione. L’attribuzione del punteggio e la qualificazione dei messaggi si basano esclusivamente sulla configurazione delle opzioni SpamAssassin e sulle regole di filtro. Gli amministratori di rete sono responsabili dell&#39;adattamento alle esigenze aziendali.

>[!IMPORTANT]
>
>La qualifica delle e-mail come indesiderabile da SpamAssassin si basa interamente su regole di filtraggio e punteggio.
>
>Queste regole devono quindi essere aggiornate almeno una volta al giorno affinché l’installazione di SpamAssassin e la sua integrazione in Adobe Campaign siano pienamente funzionanti e garantiscano la pertinenza dei punteggi assegnati alle consegne prima dell’invio.
>
>Questo aggiornamento è responsabilità dell&#39;amministratore del server che ospita SpamAssassin.

L’utilizzo di SpamAssassin in Adobe Campaign fornisce un’indicazione sul possibile comportamento dei server di posta che utilizzano SpamAssassin quando ricevono e-mail inviate da Adobe Campaign. Tuttavia, è possibile che i server di posta di provider di Internet o server di posta online considerino ancora indesiderabili i messaggi inviati da Adobe Campaign.

La distribuzione di SpamAssassin e dei suoi moduli in Perl richiede l&#39;utilizzo di server applicativi Adobe Campaign dotati di accesso a Internet tramite una connessione HTTP (flusso TCP/80).

## Installazione su un computer Windows {#installing-on-a-windows-machine}

Per installare e configurare SpamAssassin su Windows per abilitare l’integrazione con Adobe Campaign, esegui i seguenti passaggi:

1. Installa SpamAssassin
1. Integrare SpamAssassin in Adobe Campaign

### Installazione di SpamAssassin {#installing-spamassassin}

1. Connettiti al [portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) utilizzando le tue credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it?lang=en).
1. Scarica il file **Neolane Spam Assassin (Installazione di Windows) (2.0)** (neolane_spamassassin.2.0.zip).
1. Copia questo file sul server Adobe Campaign, quindi decomprimi il file.

   >[!NOTE]
   >
   >È possibile decomprimere il file ovunque si desideri, purché il percorso sia costituito da uno dei seguenti caratteri di espressione regolare: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Il percorso di installazione non deve contenere spazi bianchi.

1. Vai al file in cui hai decompresso il file, quindi fai doppio clic sul file **run_me.bat** per avviare lo script di installazione.

   Se viene visualizzata una shell di Windows e continua a essere visualizzata per alcuni secondi, attendi che l&#39;installazione e l&#39;aggiornamento siano completati, quindi fai clic su **Invio**.

   Se la shell di Windows non viene visualizzata o non viene visualizzata prima della scomparsa immediata, segui questi passaggi, fai doppio clic sul file **portatileShell.bat** per visualizzare una shell di Windows e controlla che il percorso della shell corrisponda alla cartella in cui è stato decompresso il file **spamassassin.zip**. In caso contrario, accedervi utilizzando il comando **cd**.

   Inserisci **run_me.bat**, quindi fai clic su **Invio** per avviare il processo di installazione e aggiornamento. L&#39;operazione restituisce uno dei seguenti valori per indicare il risultato dell&#39;aggiornamento.

   * **0**: è stato eseguito un aggiornamento.
   * **1**: Nessun nuovo aggiornamento disponibile.
   * **2**: nessun nuovo aggiornamento disponibile.
   * **3**: aggiornamento non riuscito durante la verifica precedente.
   * **4** o più: si è verificato un errore.

1. Per verificare che l&#39;installazione di SpamAssassin sia stata completata, utilizza il test GTUBE (Generic Test for Unsollecited Bulk Email) utilizzando la seguente procedura:

   1. Crea un file di testo e salvalo in **C:\TestSpamMail.txt**.
   1. Inserisci il seguente contenuto nel file :

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

   1. Fai doppio clic sul file **portatileShell.bat** per visualizzare una shell di Windows e quindi avvia il seguente comando (o &quot;`<root>`&quot; designa la cartella creata quando decomprimi il file **spamassassin.zip**):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Il contenuto di questa e-mail di test attiva un punteggio di 1.000 punti per SpamAssassin. Ciò significa che è stato rilevato come indesiderabile e che l&#39;installazione ha avuto successo ed è completamente funzionale.

### Integrazione di SpamAssassin in Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Modifica il file **`[INSTALL]/conf/serverConf.xml`**. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questa [sezione](../../installation/using/the-server-configuration-file.md).
1. Modifica il valore dell&#39;attributo **spamCheck** degli elementi **command** nel nodo **Web**. A questo scopo, esegui il seguente comando:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Tutti i percorsi devono essere assoluti.

   Arresta e avvia il servizio **[!UICONTROL Adobe Campaign]** .

1. Per verificare l’integrazione di SpamAssassin in Adobe Campaign utilizza un test GTBUE (Test generico per e-mail in blocco non richieste):

   Fare doppio clic sul file **portableshell.bat**. Questo attiva la visualizzazione di una shell di Windows. Esegui quindi il seguente comando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Il contenuto di questa e-mail di test attiva 1.000 punti assegnati da SpamAssassin. Ciò significa che è stata rilevata come indesiderabile e che l’integrazione in Adobe Campaign ha avuto successo ed è completamente funzionale.

1. Aggiorna le regole di filtro e punteggio di SpamAssassin

   Per un aggiornamento iniziale delle regole di filtraggio e punteggio, avvia **portatileShell.bat** ed esegui il seguente comando:

   ```
   sa-update --no-gpg
   ```

   Per eseguire un aggiornamento automatico delle regole di filtro e punteggio, utilizzare lo stesso comando in un&#39;attività di sistema pianificata:

   ```
   sa-update --no-gpg
   ```

## Installazione su un computer Linux {#installing-on-a-linux-machine}

### Passaggi di installazione in Debian {#installation-steps-in-debian}

* Se necessario, installare Perl e SpamAssassin utilizzando il seguente comando:

   ```
   apt-get install spamassassin libxml-writer-perl
   ```

* Nel file **serverConf.xml** (disponibile in `/usr/local/[INSTALL]/nl6/conf/`), modifica la riga **spamCheck** come segue:

   ```
   <spamCheck command="perl
   /usr/local/[NSTALL]/nl6/bin/spamcheck.pl"/>
   ```

### Passaggi per l’installazione in RHEL/CentOS {#installation-steps-in-rhel-centos}

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

### Aggiornamento delle regole del filtro {#updating-filter-rules}

Le regole del filtro possono essere aggiornate automaticamente utilizzando lo strumento **sa-update** . Per ulteriori informazioni, consulta il sito web ufficiale SpamAssassin [https://spamassassin.apache.org/](https://spamassassin.apache.org/) .

In Debian, gli aggiornamenti avvengono automaticamente ogni giorno.

Se non è così (ad esempio quando Debian viene installato manualmente), crea uno script per automatizzare gli aggiornamenti delle regole.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Inserisci questo script in **crontab** utilizzando il seguente comando:

```
crontab-e
```

### Ottimizzazione delle prestazioni {#performance-optimization}

Per migliorare le prestazioni in Linux, modifica il file **/etc/spamassassin/local.cf** e aggiungi la seguente riga alla fine del file:

```
dns_available no
```
