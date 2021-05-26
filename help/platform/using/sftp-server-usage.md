---
solution: Campaign Classic
product: campaign
title: Utilizzo di server SFTP
description: Ulteriori informazioni sulle best practice e la risoluzione dei problemi del server SFTP.
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '1156'
ht-degree: 14%

---

# Best practice e risoluzione dei problemi per il server SFTP {#sftp-server-usage}

## Raccomandazioni globali per server SFTP {#global-recommendations}

Quando gestisci file e dati per un processo di ETL, questi file vengono memorizzati in un server SFTP in hosting fornito da Adobe. Accertati di seguire le raccomandazioni riportate di seguito quando utilizzi i server SFTP.

* Per evitare la scadenza della password (le password hanno un periodo di validità di 90 giorni), utilizza l’autenticazione basata sulle chiavi anziché l’autenticazione tramite password. Inoltre, l’autenticazione basata sulle chiavi consente di generare più chiavi, ad esempio quando gestisci più entità. Al contrario, l&#39;autenticazione tramite password richiede la condivisione della password con tutte le entità che stai gestendo.

   Il formato chiave supportato è SSH-2 RSA 2048. Le chiavi possono essere generate con strumenti come PyTTY (Windows) o ssh-keygen (Unix).Per caricare le chiavi sul server Campaign, devi fornire la chiave pubblica al team di supporto Adobe tramite [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) .

* Utilizza la suddivisione in batch nei caricamenti SFTP e nei flussi di lavoro.

* Gestisci gli errori/le eccezioni.

* Per impostazione predefinita, tutte le cartelle create sono in modalità di lettura/scrittura solo per l&#39;identificatore. Quando crei cartelle a cui è necessario accedere da Campaign, assicurati di configurarle con diritti di lettura/scrittura per l’intero gruppo. In caso contrario, i flussi di lavoro potrebbero non essere in grado di creare/eliminare file in quanto vengono eseguiti con un identificatore diverso all’interno dello stesso gruppo per motivi di sicurezza.

* Gli IP pubblici da cui stai tentando di avviare la connessione SFTP devono essere aggiunti all’inserire nell&#39;elenco Consentiti nell’istanza Campaign. L&#39;aggiunta di indirizzi IP all&#39;inserire nell&#39;elenco Consentiti può essere richiesta tramite [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Best practice di utilizzo del database {#sftp-server-best-practices}

I server SFTP sono progettati per essere spazi di archiviazione temporanei in cui puoi controllare la conservazione e l’eliminazione dei file.

Se non utilizzati o monitorati correttamente, questi spazi possono riempire rapidamente lo spazio fisico disponibile sul server e portare al troncamento dei file durante i successivi caricamenti. Una volta saturato lo spazio, l&#39;eliminazione automatica può attivare e cancellare i file meno recenti dall&#39;archiviazione SFTP.

Per evitare tali problemi, l&#39;Adobe consiglia di seguire le best practice riportate di seguito.

>[!NOTE]
>
>Se l&#39;istanza è ospitata su AWS, puoi monitorare l&#39;archiviazione del server SFTP con Campaign Classic [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). Per verificare se l’istanza è ospitata su AWS, segui i passaggi descritti in [questa sezione](https://experienceleague.adobe.com/docs/control-panel/using/faq.html).
>
>Il Pannello di controllo Campaign è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente l’accesso come amministratore sono descritti in[questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel).
>
>Tieni presente che l’istanza deve essere aggiornata con la build [Gold Standard](../../rn/using/gs-overview.md) più recente o con la build [GA più recente (21.1)](../../rn/using/latest-release.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

* Le capacità del server variano a seconda della licenza. In ogni caso, mantieni i dati minimi possibili e conserva i dati solo per il tempo richiesto (15 giorni è il limite massimo di tempo).

* Utilizza i flussi di lavoro per eliminare correttamente i dati (gestisci la conservazione dai flussi di lavoro che consumano i dati).

* Di tanto in tanto, effettua l’accesso a SFTP per verificare direttamente ciò che vi si trova.

* Ricorda che la gestione del disco SFTP è principalmente una tua responsabilità.

## Utilizzo server SFTP esterno {#external-SFTP-server}

Se utilizzi il tuo server SFTP, assicurati di seguire il più possibile le raccomandazioni di cui sopra.

Inoltre, quando si specifica in Campaign Classic un percorso a un server SFTP esterno, la sintassi del percorso è diversa a seconda del sistema operativo del server SFTP:

* Se il server SFTP è su **Windows**, utilizza sempre un percorso relativo.
* Se il server STP è su **Linux**, utilizza sempre un percorso relativo alla home (a partire da &quot;~/&quot;), o un percorso assoluto (a partire da &quot;/&quot;).

## Problemi di connessione con il server SFTP ospitato da Adobe {#sftp-server-troubleshooting}

La sezione seguente elenca le informazioni da controllare e fornire al team di supporto Adobe tramite [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) quando si verificano problemi di connessione con i server SFTP ospitati da Adobe.

1. Verifica che l&#39;istanza sia in esecuzione. A questo scopo, apri il browser, quindi effettua una chiamata **[!UICONTROL GET]** sull&#39;endpoint dell&#39;istanza **[!UICONTROL /r/test]**:

   ```
   https://instanceUrl/r/test
   ```

   Se l&#39;istanza è in esecuzione, dovresti ottenere questo tipo di risposta:

   ```
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instanceName'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instanceName'/>
   ```

   In ogni caso, fornisci la risposta del comando nel ticket di supporto.

1. Controlla se la porta in uscita 22 è aperta nel sito da cui stai tentando di avviare la connessione SFTP. A questo scopo, utilizza il seguente comando:

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
   >Lo strumento Netcat consente di gestire facilmente le connessioni di rete su vari sistemi operativi (vedere [https://eternallybored.org/misc/netcat/](https://eternallybored.org/misc/netcat/)).

   Se la porta non è aperta, assicurati di aprire le connessioni in uscita sul tuo lato, quindi riprova. Se riscontri ancora problemi di connessione, condividi l&#39;output del comando con il team [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

1. Verifica che l’IP pubblico da cui stai tentando di avviare la connessione SFTP sia quello fornito al supporto Adobe per l’inserire nell&#39;elenco Consentiti.
1. Se utilizzi un&#39;autenticazione basata su password, la password potrebbe essere scaduta (le password hanno un periodo di validità di 90 giorni). Pertanto, consigliamo vivamente di utilizzare un’autenticazione basata sulle chiavi (consulta [Best practice per i server SFTP](#sftp-server-best-practices)).
1. Se utilizzi un’autenticazione basata su chiave, verifica che la chiave utilizzata sia la stessa fornita al team [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per la configurazione dell’istanza.
1. Se utilizzi FileZilla o uno strumento FTP equivalente, fornisci i dettagli dei log di connessione nel ticket di supporto.

## Errore &quot;Impossibile risolvere il nome host&quot;

Questa sezione fornisce informazioni sui controlli e sulle azioni da eseguire quando viene visualizzato l&#39;errore &quot;Impossibile risolvere il nome host&quot; dopo la connessione al server FTP da Campaign Classic.

Il giornale di registrazione del flusso di lavoro mostra i seguenti registri:

```
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Questo errore si verifica quando si tenta di collegare il server FTP da un flusso di lavoro e si scaricano i file dal server, mentre si è ancora in grado di connettersi tramite FTP utilizzando FileZilla o WinSCP.

Questo errore indica che il nome di dominio del server FTP non può essere risolto correttamente. Per risolvere i problemi, procedi come segue:

1. Risolvere i problemi relativi alla **configurazione del server DNS**:

   1. Controlla se il nome del server è stato aggiunto al server DNS locale.
   1. Se sì, esegui il seguente comando sul server Adobe Campaign per ottenere l&#39;indirizzo IP:

      `nslookup <server domain name>`

      Questo conferma il funzionamento del server FTP e la sua reperibilità dal server dell&#39;applicazione Adobe Campaign.

1. Risolvere i problemi **log di sessione**:

   1. Nel flusso di lavoro, fai doppio clic sull’attività [Trasferimento file](../../workflow/using/file-transfer.md) .
   1. Vai alla scheda **[!UICONTROL File Transfer]**, quindi fai clic su **[!UICONTROL Advanced Parameters]**.
   1. Seleziona l’opzione **[!UICONTROL Display the session logs]**.

      ![](assets/sftp-error-display-logs.png)

   1. Vai al controllo del flusso di lavoro e controlla se i registri mostrano l&#39;errore &quot;Impossibile risolvere il nome host&quot;.

1. Se il server SFTP è ospitato da Adobe, verifica se l’IP viene aggiunto all’inserire nell&#39;elenco Consentiti contattando l’Assistenza clienti.

   In caso contrario, convalida:

   * La password non contiene &#39;@&#39;. Connessione non riuscita se la password contiene &#39;@&#39;.
   * Non ci sono problemi di firewall che possono ostacolare la comunicazione tra il server dell’applicazione Adobe Campaign e il server SFTP.
   * Esegui i comandi tracert e telnet dal server della campagna all’sftp per verificare se sono presenti problemi di connessione.
   * Non ci sono problemi di protocollo di comunicazione.
   * Porta aperta.
