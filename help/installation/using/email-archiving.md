---
product: campaign
title: Archiviazione di e-mail
description: Archiviazione di e-mail
feature: Installation, Instance Settings, Email
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1366'
ht-degree: 5%

---

# Configurare CCN e-mail {#email-archiving}



Puoi configurare Adobe Campaign per conservare una copia delle e-mail inviate dalla tua piattaforma.

Tuttavia, Adobe Campaign stessa non gestisce i file archiviati. Consente di inviare i messaggi scelti a un indirizzo dedicato, da cui possono essere elaborati e archiviati utilizzando un sistema esterno.

A questo scopo, i file .eml corrispondenti alle e-mail inviate vengono trasferiti a un server remoto, ad esempio un server e-mail SMTP. La destinazione di archiviazione è un indirizzo e-mail in Ccn (invisibile ai destinatari della consegna) che devi specificare.

## Recommendations e limitazioni {#recommendations-and-limitations}

* La funzionalità CCN e-mail è facoltativa. Controlla il contratto di licenza.
* Per **architetture in hosting e ibride**, contatta il responsabile del tuo account per attivarlo. L&#39;indirizzo e-mail Ccn scelto deve essere fornito al team di Adobi che lo configurerà per te.
* Per **installazioni locali**, seguire le linee guida riportate di seguito per attivarlo - vedere [Attivazione CCN e-mail (locale)](#activating-email-archiving--on-premise-) e [Configurazione dell’indirizzo e-mail Ccn (locale)](#configuring-the-bcc-email-address--on-premise-) sezioni.
* È possibile utilizzare un solo indirizzo e-mail Ccn.
* Una volta configurata la funzione Ccn e-mail, accertati che sia abilitata nel modello di consegna o nella consegna tramite il **[!UICONTROL Email BCC]** opzione. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/sending-messages.md#archiving-emails).
* Solo le e-mail inviate correttamente vengono prese in considerazione, i mancati recapiti non lo sono.
* Il sistema di archiviazione delle e-mail è stato modificato con Adobe Campaign 17.2 (build 8795). Se utilizzavi già l’archiviazione delle e-mail, devi eseguire manualmente l’aggiornamento al nuovo sistema CCN e-mail. Per ulteriori informazioni, consulta [Passaggio al nuovo campo CCN e-mail](#updated-email-archiving-system--bcc-) sezione.

## Attivazione CCN e-mail (locale) {#activating-email-archiving--on-premise-}

[!BADGE On-premise e ibrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"}


Per attivare l’archiviazione delle e-mail in Ccn quando Adobe Campaign è installato sul posto, effettua le seguenti operazioni.

### Cartella locale {#local-folder}

Per abilitare il trasferimento delle e-mail inviate a un indirizzo e-mail Ccn, è necessario salvare le copie non elaborate esatte delle e-mail inviate come file .eml in una cartella locale.

Il percorso della cartella locale deve essere specificato in **config-`<instance>`.xml** dalla configurazione. Ad esempio:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>È responsabilità del team che implementa il progetto assicurarsi che le impostazioni di protezione consentano l&#39;accesso alla cartella definita tramite il **dataLogPath** parametri.

Il percorso completo è il seguente: **`<datalogpath>  YYYY-MM-DDHHh`**. La data e l’ora vengono impostate in base all’orologio del server MTA (UTC). Ad esempio:

```
C:\emails\2018-12-02\13h
```

Il nome del file di archivio è **`<deliveryid>-<broadlogid>.eml`** quando lo stato delle e-mail non è **[!UICONTROL Sent]**. Una volta che lo stato è cambiato in **[!UICONTROL Sent]**, il nome del file diventa **`<deliveryid>-<broadlogid>-sent.eml`**. Ad esempio:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In un’istanza di mid-sourcing, la directory per le e-mail Ccn si trova sul server di mid-sourcing.
>
>Il deliveryID e il broadlogID provengono dal server di mid-sourcing quando lo stato delle e-mail non viene inviato. Una volta che lo stato è cambiato in **[!UICONTROL Sent]**, questi ID provengono dal server di marketing.

### Elemento “parameters” {#parameters}

Una volta definito il percorso della cartella locale, aggiungi e modifica i seguenti elementi come desiderato nel **config-`<instance name>.xml`** file. Di seguito sono riportati i valori predefiniti:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="0" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formato utilizzato per comprimere i file .eml. I valori possibili sono:

  **0**: nessuna compressione (valore predefinito)

  **1**: compressione (formato .zip)

* **compressBatchSize**: numero di file eml aggiunti a un archivio (file .zip).
* **archivingType**: strategia di archiviazione da utilizzare. I valori possibili sono:

  **0**: le copie non elaborate delle e-mail inviate vengono salvate in formato .eml in **dataLogPath** cartella (valore predefinito). Una copia di archiviazione del **`<deliveryid>-<broadlogid>-sent.eml`** il file viene salvato in **dataLogPath/archivi** cartella. Il percorso del file e-mail inviato diventa **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

  **1**: le copie non elaborate delle e-mail inviate vengono salvate in formato .eml in **dataLogPath** e vengono inviati all’indirizzo e-mail Ccn tramite SMTP. Una volta inviate le copie dell&#39;e-mail all&#39;indirizzo Ccn, il nome del file di archivio diventa **`<deliveryid>-<broadlogid>-sent-archived.eml`** e il file viene spostato in **dataLogPath/archivi** cartella. Il percorso del file e-mail archiviato in Ccn e inviato è quindi **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: numero di giorni in cui i file eml vengono conservati per l’archiviazione. Dopo questo ritardo, vengono automaticamente spostati nel **dataLogPath/archivi** cartella per la compressione. Per impostazione predefinita, i file .eml scadono dopo due giorni.
* **purgeArchivesDelay**: numero di giorni in cui gli archivi vengono conservati nel **dataLogPath/`<archives>`** cartella. Dopo tale periodo, vengono eliminati definitivamente. L’eliminazione inizia quando viene avviato l’MTA. Per impostazione predefinita viene eseguita ogni sette giorni.
* **pollDelay**: verifica della frequenza (in secondi) di nuove e-mail in arrivo inviate al **dataLogPath** cartella. Ad esempio, se questo parametro è impostato su 60, significa che ogni minuto il processo di archiviazione passa attraverso i file .eml all’interno del **dataLogPath/`<date and time>`** , applicare un&#39;eliminazione se necessario e inviare copie e-mail all&#39;indirizzo Ccn e/o comprimere i file archiviati quando necessario.
* **acquisitionLimit**: numero di file .eml elaborati contemporaneamente prima che il processo di archiviazione venga nuovamente applicato in base al **pollDelay** parametro. Ad esempio, se imposti il **acquisitionLimit** a 100 mentre il **pollDelay** Il parametro è impostato su 60. Verranno elaborati 100 file eml al minuto.
* **smtpNbConnection**: numero di connessioni SMTP all’indirizzo e-mail Ccn.

Assicurati di regolare questi parametri in base alla velocità effettiva di invio dell’e-mail. Ad esempio, in una configurazione in cui l’MTA invia 30.000 e-mail all’ora, puoi impostare **pollDelay** parametro a 600, il **acquisitionLimit** parametro a 5000 e **smtpNbConnection** parametro a 2. Ciò significa che utilizzando 2 connessioni SMTP, 5.000 e-mail verranno inviate all’indirizzo Ccn ogni 10 minuti.

## Configurazione dell’indirizzo e-mail Ccn (locale) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE On-premise e ibrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"}


>[!IMPORTANT]
>
>Per motivi di privacy, le e-mail in formato Ccn devono essere elaborate da un sistema di archiviazione in grado di memorizzare informazioni personali (PII) protette.

In **config-`<instance name>.xml`** , utilizzare i seguenti parametri per definire il server di posta elettronica SMTP in cui verranno trasferiti i file memorizzati:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: archiviazione della destinazione
* **smtpEnableTLS**: utilizzo di una connessione SMTP protetta (protocollo TLS/SSL)
* **smtpRelayAddress**: indirizzo di inoltro da utilizzare
* **smtpRelayPort**: porta di inoltro da utilizzare

>[!NOTE]
>
>Se utilizzi un inoltro SMTP, le modifiche apportate alle e-mail dall’inoltro non vengono prese in considerazione nel processo di archiviazione.
>
>Inoltre, l&#39;inoltro assegna un **[!UICONTROL Sent]** stato di tutte le e-mail, incluse quelle che non vengono inviate. Pertanto, tutti i messaggi vengono archiviati.

## Passaggio al nuovo campo CCN e-mail {#updated-email-archiving-system--bcc-}

[!BADGE On-premise e ibrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"}



>[!IMPORTANT]
>
>Il sistema di archiviazione delle e-mail (CCN) è stato modificato con Adobe Campaign 17.2 (build 8795). Se si esegue l&#39;aggiornamento da una build precedente e si utilizzavano già le funzionalità di archiviazione delle e-mail, è necessario eseguire l&#39;aggiornamento manualmente al nuovo sistema di archiviazione delle e-mail (CCN).

A questo scopo, apporta le seguenti modifiche alla **`config-<instance>.xml`** file:

1. Rimuovi il **zipPath** parametro da **`<archiving>`** nodo.
1. Imposta il **compressionFormat** parametro a **1** se necessario.
1. Imposta il **archivingType** parametro a **1**.

Una volta configurato il campo CCN e-mail, assicurati di selezionare **[!UICONTROL Email BCC]** nel modello di consegna o nella consegna. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/sending-messages.md#archiving-emails).

## Best practice per il CCN dell’e-mail {#best-practices}

* **Cassetta postale indirizzo Ccn**: accertati che abbia una capacità di ricezione sufficiente per archiviare tutte le e-mail inviate dall’MTA.
* **Pooling MTA**: la funzione di archiviazione Ccn funziona a livello di MTA. Ti consente di duplicare ogni e-mail inviata dall’MTA. Poiché l’MTA può essere raggruppato in più istanze (ad esempio sviluppo, test o produzione) o anche tra più client (in un ambiente di mid-sourcing), la configurazione di questa funzione influisce sulla sicurezza:

   * Se condividi un MTA con più client e uno di essi ha questa opzione attivata, questo client accederà a tutte le e-mail degli altri client che condividono lo stesso MTA. Per evitare tale situazione, utilizza un MTA diverso per ogni client.
   * Se utilizzi lo stesso MTA in più istanze (sviluppo, test, prod) per un singolo client, i messaggi inviati da tutte e tre le istanze verranno duplicati dall’opzione dataLogPath.

* **E-mail per connessione**: l’archiviazione delle e-mail in Ccn funziona aprendo una connessione e tentando di inviare tutte le e-mail tramite tale connessione. L’Adobe consiglia di verificare con il contatto tecnico interno il numero di e-mail accettate su una determinata connessione. L&#39;aumento di questo numero può avere un grande impatto sulla velocità effettiva CCN.
* **IP di invio CCN**: attualmente, le e-mail Ccn non vengono inviate tramite i normali proxy MTA. Viene invece aperta una connessione diretta dal server MTA al server e-mail di destinazione. Ciò significa che potrebbe essere necessario aggiungere altri IP al inserisco nell&#39;elenco Consentiti di sulla rete, a seconda della configurazione del server e-mail.

<!--## Email BCC with Enhanced MTA {#email-bcc-with-enhanced-mta}

For **hosted and hybrid architectures**, if you have the latest instance of Adobe Campaign, or if you have upgraded to the Enhanced MTA and using Adobe Campaign 19.2 or later, you can use Email BCC with Enhanced MTA, which is more reliable, efficient, and has lower latency.

### Activating Email BCC with Enhanced MTA

To activate this feature, you must contact your account executive to communicate the BCC email address to be used for archiving.

>[!NOTE]
>
>If you were already using BCC email archiving, you can provide the same address as you were using before or use a new one. If you keep the same, you still have to contact your account executive to set it up for you.

### Specificities and recommendations

Email BCC with Enhanced MTA is not activated at the delivery level: once this feature is enabled, **all sent deliveries** are sent to the BCC email address. There is no need to select the **[!UICONTROL Email BCC]** option in the delivery template or in the delivery.

If you were already using BCC and if you keep the same address, you could see a significant increase in the volumes sent to the BCC address.

Consequently, make sure:
* The BCC address has enough reception capacity to archive all the emails that are sent.
* You have the required MTA infrastructure capacity to receive 100% of your email volume delivered to a single address.

### Limitations

* Email BCC with Enhanced MTA delivers to the BCC email address before delivering to the recipients, which can result in BCC messages being sent even though the original deliveries may have bounced. For more on bounces, see [Understanding delivery failures](../../delivery/using/understanding-delivery-failures.md).

* There is no reporting available on the delivery status of the emails sent to the BCC email address.-->