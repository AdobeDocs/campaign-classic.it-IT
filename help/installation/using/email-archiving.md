---
product: campaign
title: Archiviazione di e-mail
description: Archiviazione di e-mail
feature: Installation, Instance Settings, Email
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '1211'
ht-degree: 1%

---

# Configurare CCN e-mail {#email-archiving}



Puoi configurare Adobe Campaign per conservare una copia delle e-mail inviate dalla tua piattaforma.

Tuttavia, Adobe Campaign stessa non gestisce i file archiviati. Consente di inviare i messaggi scelti a un indirizzo dedicato, da cui possono essere elaborati e archiviati utilizzando un sistema esterno.

A questo scopo, i file .eml corrispondenti alle e-mail inviate vengono trasferiti a un server remoto, ad esempio un server e-mail SMTP. La destinazione di archiviazione è un indirizzo e-mail in Ccn (invisibile ai destinatari della consegna) che devi specificare.

## Raccomandazioni e limitazioni {#recommendations-and-limitations}

* La funzionalità CCN e-mail è facoltativa. Controlla il contratto di licenza.
* Per **architetture in hosting e ibride**, contatta il tuo account executive per attivarle. L’indirizzo e-mail Ccn scelto deve essere fornito al team di Adobe che lo configurerà per te.
* Per **installazioni on-premise**, attieniti alle istruzioni riportate di seguito per attivarlo. Consulta le sezioni [Attivazione del CCN e-mail (on-premise)](#activating-email-archiving--on-premise-) e [Configurazione dell&#39;indirizzo e-mail del CCN (on-premise)](#configuring-the-bcc-email-address--on-premise-).
* È possibile utilizzare un solo indirizzo e-mail Ccn.
* Dopo aver configurato il campo Ccn e-mail, assicurati che la funzione sia abilitata nel modello di consegna o nella consegna tramite l’opzione **[!UICONTROL Email BCC]**. consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/emails/email-bcc.html){target="_blank"}.
* Solo le e-mail inviate correttamente vengono prese in considerazione, i mancati recapiti non lo sono.
* Il sistema di archiviazione delle e-mail è stato modificato con Adobe Campaign 17.2 (build 8795). Se utilizzavi già l’archiviazione delle e-mail, devi eseguire manualmente l’aggiornamento al nuovo sistema CCN e-mail. Per ulteriori informazioni, vedere la sezione [Spostamento alla nuova CCN e-mail](#updated-email-archiving-system--bcc-).

## Attivazione CCN e-mail (locale) {#activating-email-archiving--on-premise-}

[!BADGE On-Premise e ibrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"}


Per attivare l’archiviazione delle e-mail in Ccn quando Adobe Campaign è installato sul posto, effettua le seguenti operazioni.

### Cartella locale {#local-folder}

Per abilitare il trasferimento delle e-mail inviate a un indirizzo e-mail Ccn, è necessario salvare le copie non elaborate esatte delle e-mail inviate come file .eml in una cartella locale.

Il percorso della cartella locale deve essere specificato nel file **config-`<instance>`.xml** della configurazione. Ad esempio:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>È responsabilità del team che implementa il progetto assicurarsi che le impostazioni di protezione consentano l&#39;accesso alla cartella definita tramite i parametri **dataLogPath**.

Percorso completo: **`<datalogpath>  YYYY-MM-DDHHh`**. La data e l’ora vengono impostate in base all’orologio del server MTA (UTC). Ad esempio:

```
C:\emails\2018-12-02\13h
```

Il nome del file di archivio è **`<deliveryid>-<broadlogid>.eml`** quando lo stato delle e-mail non è **[!UICONTROL Sent]**. Una volta cambiato lo stato in **[!UICONTROL Sent]**, il nome file diventa **`<deliveryid>-<broadlogid>-sent.eml`**. Ad esempio:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In un’istanza di mid-sourcing, la directory per le e-mail Ccn si trova sul server di mid-sourcing.
>
>Il deliveryID e il broadlogID provengono dal server di mid-sourcing quando lo stato delle e-mail non viene inviato. Una volta che lo stato è cambiato in **[!UICONTROL Sent]**, questi ID provengono dal server di marketing.

### Elemento “parameters” {#parameters}

Una volta definito il percorso della cartella locale, aggiungere e modificare gli elementi seguenti nel file **config-`<instance name>.xml`**. Di seguito sono riportati i valori predefiniti:

```
<archiving autoStart="false" compressionFormat="0" compressBatchSize="10000"
           archivingType="1" expirationDelay="2" purgeArchivesDelay="7"
           pollDelay="600" acquireLimit="5000" smtpNbConnection="2"/>
```

* **compressionFormat**: formato utilizzato per la compressione dei file eml. I valori possibili sono:

  **0**: nessuna compressione (valore predefinito)

  **1**: compressione (formato .zip)

* **compressBatchSize**: numero di file eml aggiunti a un archivio (file zip).


* **archivingType**: strategia di archiviazione da utilizzare. L&#39;unico valore possibile è **1**. Le copie non elaborate delle e-mail inviate vengono salvate in formato .eml nella cartella **dataLogPath** e inviate all&#39;indirizzo e-mail Ccn tramite SMTP. Una volta inviate le copie e-mail all&#39;indirizzo Ccn, il nome del file di archivio diventa **`<deliveryid>-<broadlogid>-sent-archived.eml`** e il file viene spostato nella cartella **dataLogPath/archives**. Il percorso del file e-mail archiviato in Ccn e inviato è quindi **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

  <!--
  **0**: raw copies of sent emails are saved in .eml format to the **dataLogPath** folder (default value). An archiving copy of the **`<deliveryid>-<broadlogid>-sent.eml`** file is saved to the **dataLogPath/archives** folder. The sent email file path becomes **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.-->

* **expirationDelay**: numero di giorni in cui i file eml vengono conservati per l&#39;archiviazione. Dopo questo ritardo, vengono spostati automaticamente nella cartella **dataLogPath/archives** per la compressione. Per impostazione predefinita, i file .eml scadono dopo due giorni.
* **purgeArchivesDelay**: numero di giorni in cui gli archivi vengono conservati nella cartella **dataLogPath/`<archives>`**. Dopo tale periodo, vengono eliminati definitivamente. L’eliminazione inizia quando viene avviato l’MTA. Per impostazione predefinita viene eseguita ogni sette giorni.
* **pollDelay**: verifica della frequenza (in secondi) di nuovi messaggi e-mail inviati alla cartella **dataLogPath**. Ad esempio, se questo parametro è impostato su 60, significa che ogni minuto il processo di archiviazione passa attraverso i file .eml all&#39;interno delle cartelle **dataLogPath/`<date and time>`**, applica una rimozione se necessario e invia copie e-mail all&#39;indirizzo Ccn e/o comprimi i file archiviati quando necessario.
* **acquisitionLimit**: numero di file eml elaborati contemporaneamente prima che il processo di archiviazione venga nuovamente applicato in base al parametro **pollDelay**. Ad esempio, se imposti il parametro **acquisitionLimit** su 100 mentre il parametro **pollDelay** è impostato su 60, verranno elaborati 100 file .eml al minuto.
* **smtpNbConnection**: numero di connessioni SMTP all&#39;indirizzo e-mail Ccn.

Assicurati di regolare questi parametri in base alla velocità effettiva di invio dell’e-mail. Ad esempio, in una configurazione in cui l&#39;MTA invia 30.000 e-mail all&#39;ora, puoi impostare il parametro **pollDelay** su 600, il parametro **acquisitionLimit** su 5000 e il parametro **smtpNbConnection** su 2. Ciò significa che utilizzando 2 connessioni SMTP, 5.000 e-mail verranno inviate all’indirizzo Ccn ogni 10 minuti.

## Configurazione dell’indirizzo e-mail Ccn (locale) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE On-Premise e ibrido]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"}


>[!IMPORTANT]
>
>Per motivi di privacy, le e-mail in formato Ccn devono essere elaborate da un sistema di archiviazione in grado di memorizzare informazioni personali (PII) protette.

Nel file **config-`<instance name>.xml`**, utilizzare i seguenti parametri per definire il server di posta elettronica SMTP in cui verranno trasferiti i file archiviati:

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
>Inoltre, l&#39;inoltro assegna lo stato **[!UICONTROL Sent]** a tutte le e-mail, incluse quelle non inviate. Pertanto, tutti i messaggi vengono archiviati.

<!--
## Moving to the new Email BCC {#updated-email-archiving-system--bcc-}

[!BADGE On-premise & Hybrid]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applies to on-premise and hybrid deployments only"}

>[!IMPORTANT]
>
>The email archiving system (BCC) changed with Adobe Campaign 17.2 (build 8795). If you are upgrading from an older build and were already using email archiving capabilities, you must upgrade manually to the new email archiving system (BCC).

To do this, make the following changes to the **`config-<instance>.xml`** file:

1. Remove the **zipPath** parameter from the **`<archiving>`** node.
1. Set the **compressionFormat** parameter to **1** if needed.
1. Set the **archivingType** parameter to **1**.

Once email BCC is configured, make sure you select the **[!UICONTROL Email BCC]** option in the delivery template or the delivery. For more on this, see [this section](../../delivery/using/sending-messages.md#archiving-emails).
-->

## Best practice per il CCN dell’e-mail {#best-practices}

* **Cassetta postale dell&#39;indirizzo Ccn**: assicurati che disponga di una capacità di ricezione sufficiente per archiviare tutte le e-mail inviate dall&#39;MTA.
* **MTA pooling**: la funzione di archiviazione Ccn funziona a livello di MTA. Ti consente di duplicare ogni e-mail inviata dall’MTA. Poiché l’MTA può essere raggruppato in più istanze (ad esempio sviluppo, test o produzione) o anche tra più client (in un ambiente di mid-sourcing), la configurazione di questa funzione influisce sulla sicurezza:

   * Se condividi un MTA con più client e uno di essi ha questa opzione attivata, questo client accederà a tutte le e-mail degli altri client che condividono lo stesso MTA. Per evitare tale situazione, utilizza un MTA diverso per ogni client.
   * Se utilizzi lo stesso MTA in più istanze (sviluppo, test, prod) per un singolo client, i messaggi inviati da tutte e tre le istanze verranno duplicati dall’opzione dataLogPath.

* **E-mail per connessione**: l&#39;archiviazione di e-mail in Ccn funziona aprendo una connessione e tentando di inviare tutte le e-mail tramite tale connessione. Adobe consiglia di verificare con il contatto tecnico interno il numero di e-mail accettate su una determinata connessione. L&#39;aumento di questo numero può avere un grande impatto sulla velocità effettiva CCN.
* **IP di invio CCN**: al momento, le e-mail CCN non vengono inviate tramite i normali proxy MTA. Viene invece aperta una connessione diretta dal server MTA al server e-mail di destinazione. Ciò significa che potrebbe essere necessario aggiungere altri IP al inserisco nell&#39;elenco Consentiti di rete, a seconda della configurazione del server e-mail.

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