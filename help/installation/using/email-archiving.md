---
product: campaign
title: Archiviazione di e-mail
description: Archiviazione di e-mail
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 424faf25-2fd5-40d1-a2fc-c715fc0b8190
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1359'
ht-degree: 5%

---

# Configurare CCN e-mail {#email-archiving}



Puoi configurare Adobe Campaign per mantenere una copia delle e-mail inviate dalla piattaforma.

Tuttavia, Adobe Campaign non gestisce i file archiviati. Permette infatti di inviare i messaggi di tua scelta a un indirizzo dedicato, dal quale possono essere elaborati e archiviati utilizzando un sistema esterno.

A questo scopo, i file .eml corrispondenti alle e-mail inviate vengono trasferiti a un server remoto, ad esempio un server e-mail SMTP. La destinazione di archiviazione è un indirizzo e-mail CCN (invisibile ai destinatari della consegna) che devi specificare.

## Recommendations e limitazioni {#recommendations-and-limitations}

* La funzionalità CCN dell’e-mail è facoltativa. Controlla il contratto di licenza.
* Per **architetture ospitate e ibride**, contatta il tuo account executive per attivarlo. L’indirizzo e-mail CCN desiderato deve essere fornito al team di Adobe che lo configurerà per te.
* Per **installazioni on-premise**, segui le linee guida riportate di seguito per attivarlo - consulta la sezione [Attivazione del CCN dell’e-mail (on-premise)](#activating-email-archiving--on-premise-) e [Configurazione dell’indirizzo e-mail CCN (on-premise)](#configuring-the-bcc-email-address--on-premise-) sezioni.
* Puoi utilizzare un solo indirizzo e-mail CCN.
* Una volta configurato il CCN dell’e-mail, assicurati che la funzione sia abilitata nel modello di consegna o nella consegna tramite il **[!UICONTROL Email BCC]** opzione . Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/sending-messages.md#archiving-emails).
* Vengono prese in considerazione solo le e-mail inviate con successo. I messaggi non recapitati non lo sono.
* Il sistema di archiviazione e-mail è stato modificato con Adobe Campaign 17.2 (build 8795). Se stavi già utilizzando l’archiviazione e-mail, devi eseguire manualmente l’aggiornamento al nuovo sistema CCN di posta elettronica. Per ulteriori informazioni, consulta la sezione [Passaggio al nuovo Ccn e-mail](#updated-email-archiving-system--bcc-) sezione .

## Attivazione di indirizzi Ccn e-mail (on-premise) {#activating-email-archiving--on-premise-}

[!BADGE On-Premise e ibrida]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Si applica solo alle distribuzioni on-premise e ibride"}


Per attivare l’archiviazione delle e-mail in CCN quando Adobe Campaign è installato in locale, segui i passaggi riportati di seguito.

### Cartella locale {#local-folder}

Per abilitare il trasferimento di e-mail inviate a un indirizzo e-mail CCN, le copie non elaborate esatte delle e-mail inviate devono prima essere salvate come file .eml in una cartella locale.

Il percorso della cartella locale deve essere specificato nel **config-`<instance>`.xml** dalla configurazione. Ad esempio:

```
<mta dataLogPath="C:\emails">
```

>[!NOTE]
>
>È responsabilità del team che implementa il progetto assicurarsi che le impostazioni di protezione consentano l’accesso alla cartella definita tramite il **dataLogPath** Parametri.

Il percorso completo è il seguente: **`<datalogpath>  YYYY-MM-DDHHh`**. La data e l’ora sono impostate in base all’orologio del server MTA (UTC). Ad esempio:

```
C:\emails\2018-12-02\13h
```

Il nome del file di archivio è **`<deliveryid>-<broadlogid>.eml`** quando lo stato delle e-mail non è **[!UICONTROL Sent]**. Una volta che lo stato è cambiato in **[!UICONTROL Sent]**, il nome del file diventa **`<deliveryid>-<broadlogid>-sent.eml`**. Ad esempio:

```
C:\emails\2018-12-02\13h\4012-8040-sent.eml
```

>[!NOTE]
>
>In un’istanza di mid-sourcing , la directory per le e-mail CCN si trova sul server di mid-sourcing .
>
>Il deliveryID e il broadlogID provengono dal server di mid-sourcing quando lo stato delle e-mail non viene inviato. Una volta che lo stato è cambiato in **[!UICONTROL Sent]**, questi ID provengono dal server di marketing.

### Elemento “parameters” {#parameters}

Una volta definito il percorso della cartella locale, aggiungi e modifica i seguenti elementi come desiderato nel **config-`<instance name>.xml`** file. Di seguito sono riportati i valori predefiniti:

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

   **0**: le copie non elaborate delle e-mail inviate vengono salvate in formato .eml nel formato . **dataLogPath** folder (valore predefinito). Una copia di archiviazione del **`<deliveryid>-<broadlogid>-sent.eml`** viene salvato nel **dataLogPath/archives** cartella. Il percorso del file e-mail inviato diventa **`<datalogpath>archivesYYYY-MM-DDHHh <deliveryid>-<broadlogid>-sent.eml`**.

   **1**: le copie non elaborate delle e-mail inviate vengono salvate in formato .eml nel formato . **dataLogPath** e vengono inviati all&#39;indirizzo e-mail CCN tramite SMTP. Una volta inviate le copie dell’e-mail all’indirizzo CCN, il nome del file di archivio diventa **`<deliveryid>-<broadlogid>-sent-archived.eml`** e il file viene spostato nella **dataLogPath/archives** cartella. Il percorso del file e-mail inviato e archiviato CCN viene quindi **`<datalogpath>archivesYYYY-MM-DDHHh<deliveryid>- <broadlogid>-sent-archived.eml`**.

* **expirationDelay**: numero di giorni in cui i file .eml vengono conservati per l&#39;archiviazione. Dopo tale ritardo, vengono automaticamente spostati nel **dataLogPath/archives** cartella per la compressione. Per impostazione predefinita, i file .eml scadono dopo due giorni.
* **purgeArchivesDelay**: il numero di giorni in cui gli archivi sono conservati nel **dataLogPath/`<archives>`** cartella. Dopo tale periodo, vengono definitivamente cancellati. L&#39;eliminazione inizia all&#39;avvio dell&#39;MTA. Per impostazione predefinita viene eseguita ogni sette giorni.
* **pollDelay**: verifica della frequenza (in secondi) delle nuove e-mail inviate al **dataLogPath** cartella. Ad esempio, se questo parametro è impostato su 60, significa che ogni minuto, il processo di archiviazione passa attraverso i file .eml all&#39;interno del **dataLogPath/`<date and time>`** cartelle, applicare un&#39;eliminazione se necessario e inviare copie e-mail all&#39;indirizzo CCN e/o comprimere i file archiviati ogni volta che necessario.
* **acquisitionLimit**: numero di file .eml elaborati contemporaneamente prima che il processo di archiviazione venga nuovamente applicato in base a **pollDelay** parametro . Ad esempio, se imposti la **acquisitionLimit** a 100 mentre il valore **pollDelay** Il parametro è impostato su 60, verranno elaborati 100 file .eml al minuto.
* **smtpNbConnection**: numero di connessioni SMTP all&#39;indirizzo e-mail CCN.

Assicurati di regolare questi parametri in base alla velocità effettiva di invio dell’e-mail. Ad esempio, in una configurazione in cui l’MTA invia 30.000 e-mail all’ora, puoi impostare l’ **pollDelay** a 600, il **acquisitionLimit** a 5000 e al **smtpNbConnection** a 2. Ciò significa che utilizzando 2 connessioni SMTP, 5.000 e-mail verranno inviate all&#39;indirizzo CCN ogni 10 minuti.

## Configurazione dell’indirizzo e-mail CCN (on-premise) {#configuring-the-bcc-email-address--on-premise-}

[!BADGE On-Premise e ibrida]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Si applica solo alle distribuzioni on-premise e ibride"}


>[!IMPORTANT]
>
>Per motivi di privacy, le e-mail CCN devono essere elaborate da un sistema di archiviazione in grado di memorizzare informazioni personali (PII) sicure.

In **config-`<instance name>.xml`** file, utilizza i seguenti parametri per definire il server di posta elettronica SMTP a cui verranno trasferiti i file archiviati:

```
<archiving smtpBccAddress="" smtpEnableTLS="false" smtpRelayAddress="" smtpRelayPort="25"/>
```

* **smtpBccAddress**: destinazione di archiviazione
* **smtpEnableTLS**: utilizzo di una connessione SMTP protetta (protocollo TLS/SSL)
* **smtpRelayAddress**: indirizzo relay da utilizzare
* **smtpRelayPort**: porta relè da utilizzare

>[!NOTE]
>
>Se utilizzi un relè SMTP, le modifiche alle e-mail apportate dal relay non vengono prese in considerazione nel processo di archiviazione.
>
>Inoltre, il relè assegna un **[!UICONTROL Sent]** stato per tutte le e-mail, incluse quelle che non vengono inviate. Pertanto, tutti i messaggi vengono archiviati.

## Passaggio al nuovo Ccn e-mail {#updated-email-archiving-system--bcc-}

[!BADGE On-Premise e ibrida]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Si applica solo alle distribuzioni on-premise e ibride"}



>[!IMPORTANT]
>
>Il sistema di archiviazione delle e-mail (CCN) è stato modificato con Adobe Campaign 17.2 (build 8795). Se si esegue l’aggiornamento da una build precedente e si utilizzano già le funzionalità di archiviazione e-mail, è necessario eseguire l’aggiornamento manuale al nuovo sistema di archiviazione e-mail (CCN).

A questo scopo, apporta le seguenti modifiche al **`config-<instance>.xml`** file:

1. Rimuovi **zipPath** dal **`<archiving>`** nodo.
1. Imposta la **compressioneFormat** parametro a **1** se necessario.
1. Imposta la **archiveType** parametro a **1**.

Una volta configurato il CCN dell’e-mail, assicurati di selezionare il **[!UICONTROL Email BCC]** nel modello di consegna o nella consegna. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/sending-messages.md#archiving-emails).

## Best practice per indirizzi CCN e-mail {#best-practices}

* **Cassetta postale indirizzi CCN**: assicurati che disponga di una capacità di ricezione sufficiente per archiviare tutte le e-mail inviate dall’MTA.
* **Pool MTA**: la funzione di archiviazione CCN funziona a livello di MTA. Ti consente di duplicare ogni e-mail inviata dall’MTA. Poiché l’MTA può essere raggruppato in più istanze (ad esempio dev, test o prod) o anche tra più client (in un ambiente di mid-sourcing), l’impostazione di questa funzione influisce sulla sicurezza:

   * Se condividi un MTA con più client e questa opzione è attivata per uno di essi, questo client accederà a tutte le e-mail degli altri client che condividono lo stesso MTA. Per evitare tale situazione, utilizza un MTA diverso per ogni client.
   * Se utilizzi lo stesso MTA su più istanze (sviluppo, test, prod) per un singolo client, i messaggi inviati da tutte e tre le istanze verranno duplicati dall’opzione dataLogPath .

* **E-mail per connessione**: L’archiviazione delle e-mail CCN funziona aprendo una connessione e tentando di inviare tutte le e-mail tramite tale connessione. Adobe consiglia di verificare con il contatto tecnico interno il numero di e-mail accettate su una determinata connessione. L&#39;aumento di questo numero può avere un grande impatto sul throughput CCN.
* **IP di invio CCN**: attualmente, le e-mail CCN non vengono inviate attraverso i normali proxy MTA. Al contrario, viene aperta una connessione diretta dal server MTA al server e-mail di destinazione. Ciò significa che potrebbe essere necessario aggiungere altri IP all’inserire nell&#39;elenco Consentiti sulla rete, a seconda della configurazione del server e-mail.

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