---
title: Archiviazione e-mail
seo-title: Archiviazione e-mail
description: Archiviazione e-mail
seo-description: null
page-status-flag: never-activated
uuid: a5ed0659-be61-4d73-98e7-db3da24d92f3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: d6467875-949b-4b47-940f-620efd4db5e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7de74feb61cc8f4b386a6ff86fc58b9c9e9ca1d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 1%

---


# Archiviazione e-mail{#email-archiving}

Potete configurare  Adobe Campaign per mantenere una copia delle e-mail inviate dalla piattaforma in uso.

Tuttavia,  Adobe Campaign stesso non gestisce i file archiviati. Consente di inviare i messaggi di vostra scelta a un indirizzo dedicato, da dove possono essere elaborati e archiviati utilizzando un sistema esterno.

A tal fine, i file .eml corrispondenti alle e-mail inviate vengono trasferiti a un server remoto, ad esempio un server di posta elettronica SMTP. La destinazione di archiviazione è un indirizzo e-mail CCN (invisibile ai destinatari della consegna) che è necessario specificare.

## Recommendations e limitazioni {#recommendations-and-limitations}

* La funzione di archiviazione delle e-mail è opzionale. Controllare il contratto di licenza.
* Per architetture **** ospitate e ibride, contattate il vostro responsabile commerciale per attivarla. L&#39;indirizzo CCN desiderato deve essere fornito al team Adobe che lo configurerà automaticamente.
* Per le installazioni **** locali, seguite le linee guida riportate di seguito per attivarle. Consultate le sezioni [Attivazione dell&#39;archiviazione delle e-mail (in sede)](#activating-email-archiving--on-premise-) e [Configurazione dell&#39;indirizzo e-mail CCN (in sede)](#configuring-the-bcc-email-address--on-premise-) .
* È possibile utilizzare un solo indirizzo e-mail CCN.
* Una volta configurato il CCN dell&#39;e-mail, accertatevi che la funzione sia abilitata nel modello di consegna o nella consegna tramite l&#39; **[!UICONTROL Archive emails]** opzione. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
* Solo le e-mail inviate con successo vengono prese in considerazione, i messaggi non vengono visualizzati.
* Il sistema di archiviazione delle e-mail è cambiato con  Adobe Campaign 17.2 (build 8795). Se si utilizza già l&#39;archiviazione delle e-mail, è necessario eseguire manualmente l&#39;aggiornamento al nuovo sistema di archiviazione delle e-mail (CCN). Per ulteriori informazioni, consulta la sezione [Aggiornato sistema di archiviazione delle e-mail (CCN)](#updated-email-archiving-system--bcc-) .

## Attivazione dell&#39;archiviazione delle e-mail (in sede) {#activating-email-archiving--on-premise-}

Per attivare l&#39;archiviazione delle e-mail CCN quando  Adobe Campaign è installato in sede, attenetevi alla procedura indicata di seguito.

### Cartella locale {#local-folder}

Per abilitare il trasferimento di e-mail inviate a un indirizzo e-mail CCN, è innanzitutto necessario salvare le copie originali esatte dei messaggi e-mail inviati come file .eml in una cartella locale.

Il percorso della cartella locale deve essere specificato nel file **config-`<instance>`.xml** , dalla configurazione. Ad esempio:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>È responsabilità del team che implementa il progetto assicurarsi che le impostazioni di protezione consentano l&#39;accesso alla cartella definita tramite i parametri **dataLogPath** .

Il percorso completo è il seguente: **`<datalogpath>  YYYY-MM-DDHHh`**. La data e l&#39;ora sono impostate in base all&#39;orologio del server MTA (UTC). Ad esempio:

```
C:\emails\2018-12-02\13h
```

Il nome del file di archivio è **`<deliveryid>-<broadlogid>.eml`** quando lo stato delle e-mail non è **[!UICONTROL Sent]**. Una volta cambiato lo stato in **[!UICONTROL Sent]**, il nome del file diventa **`<deliveryid>-<broadlogid>-sent.eml`**. Ad esempio:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In un&#39;istanza mid-sourcing, la directory per le e-mail archiviate si trova sul server mid-sourcing.
>
>L’ID di distribuzione e l’ID di trasmissione provengono dal server di mid-sourcing quando lo stato delle e-mail non viene inviato. Una volta cambiato lo stato in **[!UICONTROL Sent]**, questi ID provengono dal server di marketing.

### Parametri {#parameters}

Una volta definito il percorso della cartella locale, aggiungete e modificate gli elementi seguenti nel modo desiderato nel file **config-`<instance name>.xml`**. Di seguito sono riportati i valori predefiniti:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressioneFormat**: utilizzato per comprimere i file .eml. I valori possibili sono:

   **0**: nessuna compressione (valore predefinito)

   **1**: compressione (formato .zip)

* **compressBatchSize**: numero di file .eml aggiunti a un archivio (file .zip).
* **archiveType**: strategia di archiviazione da utilizzare. I valori possibili sono:

   **0**: le copie non elaborate dei messaggi e-mail inviati vengono salvate in formato .eml nella cartella **dataLogPath** (valore predefinito). Una copia di archiviazione del **`<deliveryid>-<broadlogid>-sent.eml`** file viene salvata nella cartella **dataLogPath/archives** . Il percorso del file e-mail inviato diventa **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: le copie raw delle e-mail inviate vengono salvate in formato .eml nella cartella **dataLogPath** e inviate all&#39;indirizzo e-mail CCN tramite SMTP. Una volta inviate le copie dell’e-mail all’indirizzo CCN, il nome del file di archivio diventa **`<deliveryid>-<broadlogid>-sent-archived.eml`** e il file viene spostato nella cartella **dataLogPath/archives** . Il percorso del file e-mail inviato e archiviato in CCN viene **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **scadenzaRitardo**: numero di giorni in cui i file .eml vengono conservati per l&#39;archiviazione. Dopo tale ritardo, vengono automaticamente spostati nella cartella **dataLogPath/archives** per la compressione. Per impostazione predefinita, i file .eml scadono dopo due giorni.
* **purgeArchivesDelay**: il numero di giorni in cui gli archivi vengono conservati nella cartella **dataLogPath/`<archives>`**. Dopo tale periodo, vengono eliminati definitivamente. La rimozione inizia all&#39;avvio dell&#39;MTA. Per impostazione predefinita, viene eseguita ogni sette giorni.
* **pollDelay**: verifica della frequenza (in secondi) per i nuovi messaggi e-mail inviati alla cartella **dataLogPath** . Ad esempio, se questo parametro è impostato su 60, significa che ogni minuto, il processo di archiviazione passa attraverso i file .eml all&#39;interno delle cartelle **dataLogPath/`<date and time>`**, applica una rimozione se necessario e invia copie e-mail all&#39;indirizzo CCN e/o comprime i file archiviati ogni volta che necessario.
* **acquisitionLimit**: numero di file .eml elaborati contemporaneamente prima che il processo di archiviazione venga nuovamente applicato in base al parametro **pollDelay** . Ad esempio, se impostate il parametro **acquisitionLimit** su 100 mentre il parametro **pollDelay** è impostato su 60, verranno elaborati 100 file .eml al minuto.
* **smtpNbConnection**: numero di connessioni SMTP all&#39;indirizzo e-mail CCN.

Assicuratevi di regolare questi parametri in base al throughput di invio e-mail. Ad esempio, in una configurazione in cui MTA invia 30.000 e-mail all’ora, potete impostare il parametro **pollDelay** su 600, il parametro **acquisitionLimit** su 5000 e il parametro **smtpNbConnection** su 2. Ciò significa che utilizzando 2 connessioni SMTP, 5.000 email verranno inviate all&#39;indirizzo CCN ogni 10 minuti.

## Configurazione dell’indirizzo e-mail CCN (in sede) {#configuring-the-bcc-email-address--on-premise-}

>[!CAUTION]
>
>Per motivi di privacy, le e-mail in CCN devono essere elaborate da un sistema di archiviazione in grado di memorizzare informazioni personali (PII) sicure.

Nel file **config-`<instance name>.xml`**, utilizzate i seguenti parametri per definire il server di posta elettronica SMTP a cui verranno trasferiti i file memorizzati:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: destinazione di archiviazione
* **smtpEnableTLS**: utilizzo di una connessione SMTP protetta (protocollo TLS/SSL)
* **smtpRelayAddress**: indirizzo relay da utilizzare
* **smtpRelayPort**: porta relè da utilizzare

>[!NOTE]
>
>Se si utilizza un relè SMTP, le modifiche apportate alle e-mail dal relè non vengono prese in considerazione nel processo di archiviazione.
>
>Inoltre, il relay assegna uno **[!UICONTROL Sent]** stato a tutte le e-mail, incluse quelle che non vengono inviate. Pertanto, tutti i messaggi vengono archiviati.

## Sistema di archiviazione e-mail aggiornato (CCN) {#updated-email-archiving-system--bcc-}

>[!CAUTION]
>
>Il sistema di archiviazione delle e-mail (CCN) è stato modificato con  Adobe Campaign 17.2 (build 8795). Se state effettuando l’aggiornamento da una build precedente e state già utilizzando le funzionalità di archiviazione delle e-mail, dovete eseguire l’aggiornamento manuale al nuovo sistema di archiviazione delle e-mail (CCN).

A questo scopo, apportare le seguenti modifiche al **`config-<instance>.xml`** file:

1. Rimuovete il parametro **zipPath** dal **`<archiving>`** nodo.
1. Impostate il parametro **compressioneFormat** su **1** , se necessario.
1. Impostare il parametro **archiveType** su **1**.

Una volta configurato il CCN dell&#39;e-mail, accertatevi di selezionare l&#39; **[!UICONTROL Archive emails]** opzione nel modello di consegna o nella consegna. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).

## Best practice {#best-practices}

* **Cassetta postale** indirizzi CCN: verificare che la capacità di ricezione sia sufficiente per archiviare tutte le e-mail inviate dall&#39;MTA.
* **Mutualizzazione** MTA: la funzione di archiviazione CCN funziona a livello di MTA. Consente di duplicare ogni e-mail inviata dall&#39;MTA. Poiché il MTA può essere mutualizzato in più istanze (ad esempio dev, test o prod) o anche tra più client (in un ambiente mid-sourcing), l&#39;impostazione di questa funzione influisce sulla sicurezza:

   * Se condividete un MTA con più client e uno di essi ha attivato questa opzione, il client accederà a tutte le e-mail degli altri client che condividono lo stesso MTA. Per evitare tale situazione, utilizzate un MTA diverso per ciascun client.
   * Se si utilizza lo stesso MTA per più istanze (sviluppo, test, prod) per un singolo client, i messaggi inviati da tutte e tre le istanze saranno duplicati dall&#39;opzione dataLogPath.

* **E-mail per connessione**: L&#39;archiviazione delle e-mail CCN funziona aprendo una connessione e provando a inviare tutte le e-mail tramite quella connessione. Adobe consiglia di verificare con il contatto tecnico interno il numero di e-mail accettate su una determinata connessione. Aumentare questo numero può avere un grande impatto sul throughput CCN.
* **IP** invio CCN: attualmente, le e-mail CCN non vengono inviate attraverso i normali proxy MTA. Viene invece aperta una connessione diretta dal server MTA al server e-mail di destinazione. Ciò significa che potrebbe essere necessario aggiungere altri IP all&#39;elenco di indirizzi consentiti nella rete, a seconda della configurazione del server di posta elettronica.

