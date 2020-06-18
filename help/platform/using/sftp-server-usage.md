---
title: Utilizzo del server SFTP
seo-title: Utilizzo del server SFTP
description: Utilizzo del server SFTP
seo-description: null
page-status-flag: never-activated
uuid: 5281058d-91bd-4f98-835d-1d46dc7b8b1f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: f449ccd5-3965-4ab8-b5a9-993f3260aba9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: fecfff477b0750782c87c017a15e306acac4c61d
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 2%

---


# Utilizzo del server SFTP{#sftp-server-usage}

## Best practice per i server SFTP {#sftp-server-best-practices}

Quando gestite file e dati a scopo ETL, questi file vengono memorizzati in un server SFTP ospitato fornito da Adobe. Questo SFTP è progettato per essere uno spazio di archiviazione temporaneo su cui è possibile controllare la conservazione e l&#39;eliminazione dei file.

Se non utilizzato o monitorato correttamente, questo spazio può riempire rapidamente lo spazio fisico disponibile sul server e causare il troncamento dei file nei successivi caricamenti. Una volta saturo lo spazio, la rimozione automatica può attivare e cancellare i file più vecchi dallo storage SFTP.

Per evitare tali problemi, Adobe consiglia di seguire le best practice riportate di seguito.

>[!NOTE]
>
>Se l&#39;istanza è ospitata su AWS, è possibile monitorare l&#39;archiviazione del server SFTP con il Pannello [di](https://docs.adobe.com/content/help/en/control-panel/using/sftp-management/sftp-storage-management.html)controllo di Campaign Classic.
>
>Per verificare se l’istanza è ospitata su AWS, segui i passaggi descritti in [questa sezione](https://docs.adobe.com/content/help/en/control-panel/using/faq.html#ims-org-id) .

* Le dimensioni del server variano a seconda della licenza. In ogni caso, mantenete i dati minimi possibili e mantenete i dati per tutto il tempo necessario (15 giorni è il limite massimo).
* Per evitare la scadenza della password, utilizzare l&#39;autenticazione basata sulle chiavi anziché l&#39;autenticazione tramite password (le password hanno un periodo di validità di 90 giorni). Inoltre, l&#39;autenticazione basata sulle chiavi consente di generare più chiavi, ad esempio per la gestione di più entità. Al contrario, l&#39;autenticazione tramite password richiede la condivisione della password con tutte le entità gestite.

   Il formato chiave supportato è SSH-2 RSA 2048. Le chiavi possono essere generate con strumenti come PyTTY (Windows) o ssh-keygen (Unix). Sarà necessario fornire la chiave pubblica al team di supporto Adobe tramite un ticket [di](https://support.neolane.net) supporto per consentirne il caricamento sul server Campaign.

* Utilizzare i flussi di lavoro per eliminare correttamente i dati (gestire la conservazione dai flussi di lavoro che consumano i dati).
* Utilizzare i batch nei caricamenti SFTP e nei flussi di lavoro.
* Gestire errori/eccezioni.
* Talvolta, effettuate l’accesso a SFTP per verificare direttamente ciò che vi si trova.
* Ricorda che la gestione del disco SFTP è principalmente una tua responsabilità.
* Per impostazione predefinita, tutte le cartelle create sono in modalità di lettura/scrittura solo per l’identificatore. Quando create delle cartelle a cui Campaign deve accedere, accertatevi di configurarle con diritti di lettura/scrittura per l&#39;intero gruppo. In caso contrario, i flussi di lavoro potrebbero non essere in grado di creare/eliminare file in quanto vengono eseguiti con un identificatore diverso all’interno dello stesso gruppo per motivi di sicurezza.
* Gli IP pubblici da cui si sta tentando di avviare la connessione SFTP devono essere aggiunti all&#39;elenco di autorizzazione nell&#39;istanza Campaign. L&#39;aggiunta di indirizzi IP all&#39;elenco di indirizzi consentiti può essere richiesta tramite un ticket [di](https://support.neolane.net)supporto.

>[!CAUTION]
>
>Se utilizzate il vostro server SFTP, accertatevi di seguire il più possibile le raccomandazioni sopra riportate.

## Risoluzione dei problemi del server SFTP {#sftp-server-troubleshooting}

La sezione seguente elenca le informazioni da verificare e fornire al team di assistenza Adobe tramite un ticket [di](https://support.neolane.net) assistenza in caso di problemi di connessione con i server SFTP ospitati da Adobe.

1. Verificare che l&#39;istanza sia in esecuzione. A questo scopo, aprite il browser, quindi effettuate una **[!UICONTROL GET]** chiamata all’endpoint dell’istanza **[!UICONTROL /r/test]** :

   ```
   https://instanceUrl/r/test
   ```

   Se l&#39;istanza è in esecuzione, è necessario ottenere questo tipo di risposta:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   In ogni caso, fornite la risposta del comando nel ticket di supporto.

1. Verificate che la porta in uscita 22 sia aperta sul sito da cui state tentando di avviare la connessione SFTP. A questo scopo, utilizzate il comando seguente:

   ```
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   >[!NOTE]
   >
   >Lo strumento Rete consente di gestire facilmente le connessioni di rete su vari sistemi operativi (vedere [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Se la porta non è aperta, accertatevi di aprire le connessioni in uscita sul vostro lato, quindi riprovate. Se i problemi di connessione persistono, condividete l&#39;output del comando con il team di assistenza Adobe.

1. Verificate che l&#39;IP pubblico da cui state tentando di avviare la connessione SFTP sia quello fornito al supporto Adobe per l&#39;elenco di autorizzazioni.
1. Se utilizzate un&#39;autenticazione basata su password, la password potrebbe essere scaduta (le password hanno un periodo di validità di 90 giorni). È quindi vivamente consigliato l&#39;utilizzo di un&#39;autenticazione basata sulle chiavi (consultate Best practice [per il server](#sftp-server-best-practices)SFTP).
1. Se utilizzate un&#39;autenticazione basata su chiave, verificate che la chiave in uso sia la stessa che avete fornito al team di supporto Adobe per la configurazione dell&#39;istanza.
1. Se si utilizza FileZilla o uno strumento FTP equivalente, fornire i dettagli dei log di connessione nel ticket di supporto.

