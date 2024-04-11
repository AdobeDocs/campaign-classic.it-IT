---
product: campaign
title: Configurazione di SpamAssassin
description: Configurazione di SpamAssassin
feature: Installation, Instance Settings
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 1f1004e2-dcd2-4ec5-98ec-720c205646d5
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# Configurazione di SpamAssassin{#configuring-spamassassin}



>[!NOTE]
>
>Alcune configurazioni possono essere eseguite solo da Adobe per le distribuzioni in hosting da Adobe. Ad esempio, per accedere ai file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle diverse implementazioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o a [questa pagina](../../installation/using/capability-matrix.md).

## Panoramica {#overview}

SpamAssassin è un software progettato per filtrare le e-mail indesiderate. Insieme a questo software, Adobe Campaign può assegnare un punteggio alle e-mail e determinare se un messaggio può essere considerato indesiderato prima dell’avvio della consegna. A questo scopo, SpamAssassin deve essere installato e configurato sul server applicazioni di Adobe Campaign e richiede un certo numero di moduli Perl aggiuntivi per funzionare.

La distribuzione e l&#39;integrazione di SpamAssassin come descritto in questo capitolo si basano sull&#39;installazione del software predefinito, così come le regole di filtraggio e punteggio, che sono quelle fornite da SpamAssassin senza alcuna modifica o ottimizzazione. L’attribuzione del punteggio e la qualifica dei messaggi si basano esclusivamente sulla configurazione delle opzioni SpamAssassin e sulle regole di filtro. Gli amministratori di rete hanno la responsabilità di adattarli alle esigenze della propria azienda.

>[!IMPORTANT]
>
>La qualifica delle e-mail come indesiderate da SpamAssassin si basa interamente sulle regole di filtro e di punteggio.
>
>Queste regole devono quindi essere aggiornate almeno una volta al giorno affinché l’installazione di SpamAssassin e la sua integrazione in Adobe Campaign siano completamente funzionali e per garantire la pertinenza dei punteggi assegnati alle consegne prima dell’invio.
>
>Questo aggiornamento è responsabilità dell&#39;amministratore del server che ospita SpamAssassin.

L’utilizzo di SpamAssassin in Adobe Campaign fornisce un’indicazione sul possibile comportamento dei server di posta che utilizzano SpamAssassin quando ricevono e-mail inviate da Adobe Campaign. Tuttavia, è possibile che i server di posta dei provider Internet o dei server di posta online considerino ancora indesiderabili i messaggi inviati da Adobe Campaign.

La distribuzione di SpamAssassin e dei relativi moduli in Perl richiede server applicazioni Adobe Campaign dotati di accesso a Internet tramite una connessione HTTP (flusso TCP/80).

## Installazione in un computer Windows {#installing-on-a-windows-machine}

Per installare e configurare SpamAssassin su Windows per abilitare l’integrazione con Adobe Campaign, attieniti alla seguente procedura:

1. Installare SpamAssassin
1. Integrare SpamAssassin in Adobe Campaign

### Installazione di SpamAssassin {#installing-spamassassin}

1. Connetti a [Portale di distribuzione software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) utilizzando le credenziali utente. Ulteriori informazioni sulla distribuzione di software in [questa pagina](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).
1. Scarica il file **Neolane Spam Assassin (installazione di Windows) (2.0)** file (neolane_spamassassin.2.0.zip).
1. Copia il file sul server Adobe Campaign, quindi decomprimi il file.

   >[!NOTE]
   >
   >Puoi scegliere di decomprimere il file in qualsiasi posizione, purché il percorso sia costituito da uno dei seguenti caratteri di espressione regolare: **`-_A-Za-z\xA0-\xFF0-9\.\%\@\=\+\,\/\\\:.`**. Il percorso di installazione non deve contenere spazi.

1. Vai al file in cui hai decompresso il file, quindi fai doppio clic sul pulsante **run_me.bat** per avviare lo script di installazione.

   Se viene visualizzata una shell di Windows che continua a essere visualizzata per alcuni secondi, attendere il completamento dell&#39;installazione e dell&#39;aggiornamento, quindi fare clic su **Invio**.

   Se la shell di Windows non viene visualizzata o non viene visualizzata prima di scomparire immediatamente, eseguire la procedura seguente, fare doppio clic sulla **portableShell.bat** per visualizzare una shell di Windows e verificare che il percorso della shell corrisponda alla cartella in cui è memorizzato **spamassassin.zip** file decompresso. In caso contrario, accedervi utilizzando il **cd** comando.

   Invio **run_me.bat** quindi fai clic su **Invio** per avviare il processo di installazione e aggiornamento. L’operazione restituisce uno dei seguenti valori per indicare il risultato dell’aggiornamento.

   * **0**: è stato eseguito un aggiornamento.
   * **1**: nessun nuovo aggiornamento disponibile.
   * **2**: nessun nuovo aggiornamento disponibile.
   * **3**: aggiornamento non riuscito durante la verifica precedente.
   * **4** o più: si è verificato un errore.

1. Per verificare che l&#39;installazione di SpamAssassin sia stata completata correttamente, utilizzare il test GTUBE (Generic Test for Unsolicited Bulk Email) utilizzando la procedura seguente:

   1. Creare un file di testo e salvarlo in **C:\TestSpamMail.txt**.
   1. Inserisci il seguente contenuto nel file:

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

   1. Fai doppio clic sul pulsante **portableShell.bat** per visualizzare una shell di Windows, quindi avviare il comando seguente (o &quot;`<root>`&quot; indica la cartella creata durante la decompressione  **spamassassin.zip** file):

      ```
       "<root>\perl\site\bin\spamassassin" "C:\TestSpamMail.txt"
      ```

      Il contenuto di questa e-mail di test attiva un punteggio di 1.000 punti da SpamAssassin. Ciò significa che è stato rilevato come indesiderato e che l&#39;installazione è stata completata correttamente ed è completamente funzionante.

### Integrazione di SpamAssassin in Adobe Campaign {#integrating-spamassassin-into-adobe-campaign}

1. Modifica il **`[INSTALL]/conf/serverConf.xml`** file. Tutti i parametri disponibili in **serverConf.xml** sono elencati in questo [sezione](../../installation/using/the-server-configuration-file.md).
1. Modifica il valore del **spamCheck** elementi&#39; **comando** attributo in **Web** nodo. A tale scopo, eseguire il comando seguente:

   ```
   <spamCheck command='"<absolute path to the folder where you unzipped the zip file>\call_perl_with_args.bat" "<absolute path to nlserver>/spamcheck.pl"'/>
   ```

   >[!NOTE]
   >
   >Tutti i percorsi devono essere assoluti.

   Interrompi e avvia **[!UICONTROL Adobe Campaign]** servizio.

1. Per verificare l’integrazione di SpamAssassin in Adobe Campaign, utilizza un test GTBUE (test generico per e-mail in blocco non richieste):

   Fai doppio clic sul pulsante **portableshell.bat** file. Questa opzione attiva la visualizzazione di una shell di Windows. Quindi esegui il seguente comando:

   ```
   perl "[INSTALL]\bin\spamcheck.pl" "C:\TestSpamMail.txt"
   ```

   Il contenuto di questa e-mail di test attiva 1.000 punti assegnati da SpamAssassin. Ciò significa che è stato rilevato come indesiderato e che l’integrazione in Adobe Campaign è avvenuta con successo ed è completamente funzionale.

1. Aggiornare le regole di filtro e punteggio di SpamAssassin

   Per un aggiornamento iniziale delle regole di filtraggio e punteggio, inizia **portableShell.bat** ed esegui il comando seguente:

   ```
   sa-update --no-gpg
   ```

   Per eseguire un aggiornamento automatico delle regole di filtro e punteggio, utilizzare lo stesso comando in un&#39;attività di sistema pianificata:

   ```
   sa-update --no-gpg
   ```

## Installazione su un computer Linux {#installing-on-a-linux-machine}

### Passaggi per l’installazione in Debian {#installation-steps-in-debian}

* Se necessario, installare Perl e SpamAssassin utilizzando il seguente comando:

  ```
  apt-get install spamassassin libxml-writer-perl
  ```

* In **serverConf.xml** file (disponibile in `/usr/local/[INSTALL]/nl6/conf/`), modifica il **spamCheck** riga come segue:

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

Le regole del filtro possono essere aggiornate automaticamente utilizzando **sa-update** strumento. Consulta il sito ufficiale SpamAssassin [https://spamassassin.apache.org/](https://spamassassin.apache.org/) per ulteriori informazioni.

In Debian, gli aggiornamenti avvengono automaticamente ogni giorno.

In caso contrario (ad esempio quando Debian è installato manualmente), crea uno script per automatizzare gli aggiornamenti delle regole.

```
!/bin/sh
test -x /usr/bin/sa-update || exit 0
/usr/sbin/sa-update && /etc/init.d/spamassassin update
```

Inserisci lo script in **crontab** utilizzando il comando seguente:

```
crontab-e
```

### Ottimizzazione delle prestazioni {#performance-optimization}

Per migliorare le prestazioni in Linux, modificare il **/etc/spamassassin/local.cf** e aggiungi la seguente riga alla fine del file:

```
dns_available no
```
