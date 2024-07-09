---
product: campaign
title: Utilizzo del server SFTP
description: Ulteriori informazioni sulle best practice e sulla risoluzione dei problemi per il server SFTP
feature: Troubleshooting
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: d585a5d4-ea33-43c8-aa37-4d892025374a
source-git-commit: e40331266f34e2d6aa7b7720948d0cf26d4c6009
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 8%

---

# Best practice e risoluzione dei problemi per il server SFTP {#sftp-server-usage}

## Raccomandazioni globali per il server SFTP {#global-recommendations}

Quando gestisci file e dati per un processo di ETL, questi file vengono memorizzati in un server SFTP in hosting fornito da Adobe. Accertati di seguire le raccomandazioni riportate di seguito quando utilizzi server SFTP.

* Utilizza l’autenticazione basata su chiave anziché su password, per evitare la scadenza della password (le password hanno un periodo di validità di 90 giorni). Inoltre, l’autenticazione basata su chiave consente di generare più chiavi, ad esempio quando si gestiscono più entità. Al contrario, l’autenticazione tramite password richiede che tu condivida la password con tutte le entità che stai gestendo.

  Il formato di chiave supportato è SSH-2 RSA 2048. Lo strumento per generare le chiavi SSH per Windows è PuTTYgen e ssh-keygen per Linux. Puoi caricare le chiavi SSH pubbliche tramite il Pannello di controllo Campaign Campaign. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/key-management){target="_blank"}

* Utilizza la suddivisione in batch nei caricamenti SFTP e nei flussi di lavoro.

* Gestisci gli errori/le eccezioni.

* Per impostazione predefinita, tutte le cartelle create sono in modalità di lettura/scrittura solo per l&#39;identificatore. Durante la creazione delle cartelle a cui Campaign deve accedere, accertati di configurarle con diritti di lettura/scrittura per l’intero gruppo. In caso contrario, i flussi di lavoro potrebbero non essere in grado di creare/eliminare file in quanto vengono eseguiti con un identificatore diverso all’interno dello stesso gruppo per motivi di sicurezza.

* Gli IP pubblici da cui stai tentando di avviare la connessione SFTP devono essere aggiunti al inserisco nell&#39;elenco Consentiti di nell’istanza Campaign. Gli IP pubblici possono essere aggiunti tramite il Pannello di controllo Campaign. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/control-panel/using/sftp-management/ip-range-allow-listing){target="_blank"}

## Best practice per l’utilizzo dell’archiviazione SFTP {#sftp-server-best-practices}

I server SFTP sono progettati per essere spazi di archiviazione temporanei su cui puoi controllare la conservazione e l’eliminazione dei file.

Se non utilizzati o monitorati correttamente, questi spazi possono riempire rapidamente lo spazio fisico disponibile sul server e causare il troncamento dei file nei caricamenti successivi. Una volta saturato lo spazio, l’eliminazione automatica può attivare e cancellare i file meno recenti dall’archiviazione SFTP.

Per evitare tali problemi, l’Adobe consiglia di seguire le best practice riportate di seguito.

>[!NOTE]
>
>* Puoi monitorare l’archiviazione del server SFTP con Campaign Classic [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html){target="_blank"}.
>
>* Il Pannello di controllo è accessibile a tutti gli utenti amministratori. I passaggi per concedere a un utente i diritti da amministratore sono descritti in [questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it#discover-control-panel){target="_blank"}.
>
>* La tua istanza deve essere aggiornata con [build GA più recente](../../rn/using/rn-overview.md). Scopri come controllare la versione in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version){target="_blank"}.

* Le dimensioni del server variano a seconda della licenza. In ogni caso, mantieni i dati minimi possibili e conservali solo per il tempo necessario (15 giorni è il limite di tempo massimo).

* Utilizza i flussi di lavoro per eliminare correttamente i dati (gestisci la conservazione dai flussi di lavoro che consumano i dati).

* Di tanto in tanto, effettua l’accesso a SFTP per verificare direttamente ciò che vi si trova.

* Ricorda che la gestione del disco SFTP è principalmente una tua responsabilità.

## Utilizzo di server SFTP esterno {#external-SFTP-server}

Se utilizzi un server SFTP personalizzato, assicurati di seguire il più possibile le raccomandazioni riportate sopra.

Inoltre, quando si specifica in Campaign Classic un percorso per un server SFTP esterno, la sintassi del percorso varia a seconda del sistema operativo del server SFTP:

* Se il server SFTP è attivo **Windows**, utilizza sempre un percorso relativo.
* Se il server STP è attivo **Linux**, utilizza sempre un percorso relativo alla home (che inizia con &quot;~/&quot;) o un percorso assoluto (che inizia con &quot;/&quot;).

## Problemi di connessione con il server SFTP ospitato da Adobe {#sftp-server-troubleshooting}

La sezione seguente elenca le informazioni da verificare e fornire al team di supporto Adobe tramite [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"} quando si verificano problemi di connessione con i server SFTP ospitati da Adobe.

1. Verifica che l’istanza sia in esecuzione. Per farlo, apri il browser, quindi fai una **[!UICONTROL GET]** chiama sull’istanza **[!UICONTROL /r/test]** endpoint:

   ```xml
   https://instanceUrl/r/test
   ```

   Se l’istanza è in esecuzione, dovresti ricevere questo tipo di risposta:

   ```xml
   <redir status='OK' date='YYYY-MM-DD HH:MM:SS' build='XXXX' instance='instance-name'
   sourceIP='AAA.BB.CCC.DD' host='instanceUrl' localHost='instance-name'/>
   ```

   In ogni caso, fornisci la risposta del comando nel ticket di supporto.

1. Verifica se la porta in uscita 22 è aperta nel sito da cui stai tentando di avviare la connessione SFTP. A questo scopo, utilizza il seguente comando:

   ```xml
   bash-3.2$ nc -vz <SFTP_URL> 22
   # Replace the SFTP_URL with actual SFTP instance URL
   # If the port 22 is opened you will see output similar to the below one
   # for e.g. the  output for the command on myCompany-stage-sftp.neolane.net after ssh-out, will give
   bash-3.2$ nc -vz myCompagny-stage-sftp.neolane.net 22
   myCompany-stage-sftp.neolane.net [AAA.BBB.CCC.D] 22 (ssh) open
   ```

   Se la porta non è aperta, assicurarsi di aprire le connessioni in uscita sul lato, quindi riprovare. Se riscontri ancora problemi di connessione, condividi l’output del comando con [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team.

1. Verifica che l’IP pubblico da cui stai tentando di avviare la connessione SFTP sia quello fornito all’Adobe di supporto per il inserisco nell&#39;elenco Consentiti di.
1. Se si utilizza un&#39;autenticazione basata su password, la password potrebbe essere scaduta (le password hanno un periodo di validità di 90 giorni). Pertanto, consigliamo vivamente di utilizzare un’autenticazione basata su chiave (consulta [Best practice per il server SFTP](#sftp-server-best-practices)).
1. Se utilizzi un’autenticazione basata su chiave, verifica che la chiave utilizzata sia la stessa fornita a [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) team per la configurazione dell’istanza.
1. Se utilizzi FileZilla o uno strumento FTP equivalente, fornisci i dettagli dei registri di connessione nel ticket di supporto.

## Errore &quot;Impossibile risolvere il nome host&quot;

Questa sezione fornisce informazioni sui controlli e sull’azione da eseguire quando viene visualizzato l’errore &quot;Impossibile risolvere il nome host&quot; dopo la connessione al server FTP da Campaign Classic.

Il giornale di registrazione del flusso di lavoro mostra i seguenti registri:

```xml
16/05/2016 12:49:03    fileTransfer    Upload error in cURL
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Couldn't resolve host name
16/05/2016 12:49:03    fileTransfer    Starting transfer of '/usr/local/neolane/nl6/var/williamreed/export/Recipients' to 'ftp://213.253.61.250/Recipients'
16/05/2016 12:49:03    fileTransfer    1 file(s) to transfer
```

Questo errore si verifica quando si tenta di connettere il server FTP da un flusso di lavoro e si scaricano i file dal server, mentre è ancora possibile connettersi tramite FTP utilizzando FileZilla o WinSCP.

Questo errore indica che il nome di dominio del server FTP non è stato risolto correttamente. Per risolvere i problemi, effettuare le seguenti operazioni:

1. Risoluzione dei problemi **Configurazione server DNS**:

   1. Verificare se il nome del server è stato aggiunto al server DNS locale.
   1. In caso affermativo, esegui il seguente comando sul server Adobe Campaign per ottenere l’indirizzo IP:

      `nslookup <server domain name>`

      Questo conferma che il server FTP funziona e che è raggiungibile dal server applicazioni Adobe Campaign.

1. Risoluzione dei problemi **registri di sessione**:

   1. Nel flusso di lavoro, fai doppio clic sul pulsante [Trasferimento file](../../workflow/using/file-transfer.md) attività.
   1. Vai a **[!UICONTROL File Transfer]** , quindi fai clic su **[!UICONTROL Advanced Parameters]**.
   1. Seleziona l’opzione **[!UICONTROL Display the session logs]**.

      ![](assets/sftp-error-display-logs.png)

   1. Vai a Audit del flusso di lavoro e controlla se i registri mostrano l’errore &quot;Impossibile risolvere il nome host&quot;.

1. Se il server SFTP è ospitato da Adobe, verifica se l’IP viene aggiunto al inserisco nell&#39;elenco Consentiti di contattando l’Assistenza clienti.

   In caso contrario, convalida:

   * La password non contiene `@` carattere. La connessione non riesce se è presente un `@` nella password.
   * Non vi sono problemi di firewall che possono ostacolare la comunicazione tra il server applicazioni Adobe Campaign e il server SFTP.
   * Esegui i comandi tracert e telnet dal server della campagna all’sftp per verificare se sono presenti problemi di connessione.
   * Nessun problema relativo al protocollo di comunicazione.
   * Porta aperta.
