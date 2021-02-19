---
solution: Campaign Classic
product: campaign
title: Informazioni sulla gestione della quarantena
description: Informazioni sulla gestione della quarantena
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 6d5dbc16ed6c6e5a2e62ceb522e2ccd64b142825
workflow-type: tm+mt
source-wordcount: '2799'
ht-degree: 15%

---


# Informazioni sulla gestione della quarantena{#understanding-quarantine-management}

## Informazioni sulla quarantena {#about-quarantines}

 Adobe Campaign gestisce un elenco di indirizzi in quarantena. I destinatari il cui indirizzo è stato messo in quarantena sono esclusi per impostazione predefinita durante l’analisi della consegna e non saranno oggetto di targeting. Un indirizzo e-mail può essere posto in quarantena, ad esempio, quando la casella di posta è piena o se l’indirizzo non esiste. In ogni caso, la procedura di quarantena è conforme alle norme specifiche descritte di seguito.

>[!NOTE]
>
>Questa sezione si applica ai canali online: email, SMS, notifica push.

### Ottimizzazione della consegna tramite quarantena {#optimizing-your-delivery-through-quarantines}

I profili con indirizzi e-mail o numeri di telefono in quarantena vengono automaticamente esclusi durante la preparazione dei messaggi (vedi [Identificazione degli indirizzi messi in quarantena per una consegna](#identifying-quarantined-addresses-for-a-delivery)). In questo modo le consegne sono più rapide, poiché il tasso di errore ha un effetto significativo sulla velocità di consegna.

Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. Quarantine quindi consente di evitare di essere aggiunti al elenco Bloccati da questi provider.

Inoltre, le quarantene contribuiscono a ridurre i costi di invio degli SMS escludendo numeri di telefono errati dalle consegne. Per ulteriori informazioni sulle best practice per proteggere e ottimizzare le consegne, consulta [questa pagina](../../delivery/using/delivery-best-practices.md) .

### Quarantena e elenco Bloccati {#quarantine-vs-denylist}

La **quarantena** si applica solo a un indirizzo, non a tutto il profilo. Ciò significa che se due profili hanno lo stesso indirizzo e-mail, vengono entrambi coinvolti se l’indirizzo viene messo in quarantena.

Allo stesso modo, un profilo con un indirizzo e-mail messo in quarantena potrebbe aggiornare il profilo e immettere un nuovo indirizzo e potrebbe quindi essere nuovamente indirizzato mediante azioni di consegna.

Essere sul **elenco Bloccati**, d&#39;altra parte, il profilo non sarà più mirato da alcuna consegna, ad esempio dopo un annullamento dell&#39;iscrizione (opt-out).

>[!NOTE]
>
>Quando un utente risponde a un messaggio SMS con una parola chiave come &quot;STOP&quot; al fine di rifiutare le consegne degli SMS, il suo profilo non viene aggiunto al elenco Bloccati come nel processo di rifiuto dell&#39;e-mail. Il numero di telefono del profilo viene inviato in quarantena, in modo che l&#39;utente continui a ricevere i messaggi e-mail.

## Identificazione degli indirizzi messi in quarantena {#identifying-quarantined-addresses}

È possibile elencare gli indirizzi messi in quarantena per una consegna specifica o per l’intera piattaforma.

### Identificazione di indirizzi messi in quarantena per una consegna {#identifying-quarantined-addresses-for-a-delivery}

Gli indirizzi in quarantena per una consegna specifica sono elencati durante la fase di preparazione della consegna, nei registri di consegna del dashboard di consegna (vedere [Registri di consegna e cronologia](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)).

### Identificazione degli indirizzi messi in quarantena per l’intera piattaforma {#identifying-quarantined-addresses-for-the-entire-platform}

Gli amministratori possono elencare gli indirizzi in quarantena per l&#39;intera piattaforma dal nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

>[!NOTE]
>
>Questo menu elenca gli elementi messi in quarantena per i canali **e-mail**, **SMS** e di **notifiche push**.

Per ogni indirizzo sono disponibili le seguenti informazioni:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>L&#39;aumento delle quarantena è un effetto normale, legato all&#39;usura del database. Ad esempio, se la durata di un indirizzo e-mail è considerata di tre anni e la tabella dei destinatari aumenta del 50% ogni anno, l’aumento delle quarantena può essere calcolato come segue:
>
>Fine anno 1: (1*0.33)/(1+0.5)=22%.
Fine anno 2: ((1.22*0.33)+0.33)/(1.5+0.75)=32,5%.

### Identificazione degli indirizzi in quarantena nei report di consegna {#identifying-quarantined-addresses-in-delivery-reports}

I seguenti rapporti forniscono informazioni sugli indirizzi in quarantena:

* Per ogni consegna, il rapporto **[!UICONTROL Delivery summary]** mostra il numero di indirizzi in quarantena nella destinazione di consegna. Viene visualizzato:

   * il numero di indirizzi messi in quarantena durante l&#39;analisi della consegna,

   * Numero di indirizzi posti in quarantena dopo l&#39;azione di consegna.

* Il rapporto **[!UICONTROL Non-deliverables and bounces]** visualizza informazioni sugli indirizzi in quarantena, sui tipi di errori rilevati, ecc., e una suddivisione non riuscita per dominio.

Potete cercare queste informazioni per tutte le consegne della piattaforma (**[!UICONTROL Home page > Reports]**) o per una consegna specifica. Potete anche creare rapporti personalizzati e selezionare le informazioni da visualizzare.

### Identificazione di indirizzi in quarantena per un destinatario {#identifying-quarantined-addresses-for-a-recipient}

Puoi cercare lo stato dell’indirizzo e-mail di qualsiasi destinatario. A tal fine, selezionare il profilo del destinatario e fare clic sulla scheda **[!UICONTROL Deliveries]**. Per tutte le consegne a quel destinatario, potete verificare se l&#39;indirizzo ha avuto esito negativo, è stato messo in quarantena durante l&#39;analisi, ecc. Per ogni cartella, potete visualizzare solo i destinatari il cui indirizzo e-mail è in quarantena. A questo scopo, utilizzare il filtro dell&#39;applicazione **[!UICONTROL Quarantined email address]**.

![](assets/tech_quarant_recipients_filter.png)

### Rimozione di un indirizzo in quarantena {#removing-a-quarantined-address}

Se necessario, è possibile rimuovere manualmente un indirizzo dall&#39;elenco di quarantena. Inoltre, gli indirizzi che corrispondono a condizioni specifiche vengono eliminati automaticamente dall&#39;elenco di quarantena dal flusso di lavoro **[!UICONTROL Database cleanup]**.

Per rimuovere manualmente un indirizzo dall&#39;elenco di quarantena:

* È possibile modificarne lo stato in **[!UICONTROL Valid]** dal nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

   ![](assets/tech_quarant_error_status.png)

* È inoltre possibile modificarne lo stato in **[!UICONTROL Allowlisted]**. In questo caso, l&#39;indirizzo rimane nell&#39;elenco di quarantena, ma sarà mirato sistematicamente, anche se si verifica un errore.

Gli indirizzi vengono rimossi automaticamente dall&#39;elenco di quarantena nei seguenti casi:

* Gli indirizzi in uno stato **[!UICONTROL With errors]** verranno rimossi dall&#39;elenco di quarantena dopo la corretta consegna.
* Gli indirizzi in uno stato **[!UICONTROL With errors]** saranno rimossi dall&#39;elenco di quarantena se l&#39;ultimo rimbalzo morbido si è verificato più di 10 giorni fa. Per ulteriori informazioni sulla gestione degli errori software, vedere [questa sezione](#soft-error-management).
* Gli indirizzi in uno stato **[!UICONTROL With errors]** rimbalzato con l&#39;errore **[!UICONTROL Mailbox full]** verranno rimossi dall&#39;elenco di quarantena dopo 30 giorni.

Il relativo stato viene quindi modificato in **[!UICONTROL Valid]**.

>[!IMPORTANT]
I destinatari con un indirizzo nello stato **[!UICONTROL Quarantine]** o **[!UICONTROL On denylist]** non verranno mai rimossi, anche se ricevono un&#39;e-mail.

È possibile modificare il numero di errori e il periodo compreso tra due errori. A questo scopo, modificate le impostazioni corrispondenti nella procedura guidata di distribuzione (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**). Per ulteriori informazioni sulla procedura guidata di distribuzione, consultare [questa sezione](../../installation/using/deploying-an-instance.md).

## Condizioni per la messa in quarantena di un indirizzo {#conditions-for-sending-an-address-to-quarantine}

 Adobe Campaign gestisce la quarantena in base al tipo di consegna non riuscita e al motivo assegnato durante la qualifica dei messaggi di errore (vedere [Qualificazione della posta in sospeso](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)) e [Tipi e motivi di consegna non riuscita](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).

* **Errore ignorato**: gli errori ignorati non mettono un indirizzo in quarantena.
* **Errore rigido**: l’indirizzo e-mail corrispondente viene messo immediatamente in quarantena.
* **Errore morbido**: gli errori morbidi non mettono immediatamente un indirizzo in quarantena, ma incrementano un contatore di errori. Per ulteriori informazioni, vedere [Gestione degli errori soft](#soft-error-management).

Se un utente qualifica un&#39;e-mail come spam ([Ciclo di feedback](../../delivery/using/technical-recommendations.md#feedback-loop)), il messaggio viene automaticamente reindirizzato verso una cassetta postale tecnica gestita da  Adobe. L&#39;indirizzo e-mail dell&#39;utente viene quindi inviato automaticamente alla quarantena.

Nell&#39;elenco degli indirizzi posti in quarantena, il campo **[!UICONTROL Error reason]** indica perché l&#39;indirizzo selezionato è stato messo in quarantena. In Adobe Campaign la quarantena distingue tra maiuscole e minuscole. Accertati di importare gli indirizzi e-mail in lettere minuscole, in modo che non vengano reindirizzate in un secondo momento.

![](assets/tech_quarant_error_reasons.png)

### Gestione degli errori soft {#soft-error-management}

Invece di errori gravi, gli errori software non inviano immediatamente un indirizzo alla quarantena, ma incrementano un contatore di errori.

* Quando il contatore di errori raggiunge la soglia limite, l&#39;indirizzo viene messo in quarantena.
* Nella configurazione predefinita, la soglia è impostata a cinque errori, dove due errori sono significativi se si verificano almeno a 24 ore di distanza. L’indirizzo viene messo in quarantena al quinto errore.
* È possibile modificare la soglia del contatore di errori. Per ulteriori informazioni, fare riferimento a [Tentativi dopo un errore temporaneo di consegna](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

Il contatore di errori viene reinizializzato se l&#39;ultimo errore significativo si è verificato più di 10 giorni fa. Lo stato dell&#39;indirizzo diventa quindi **Valido** e viene eliminato dall&#39;elenco delle quarantena dal flusso di lavoro **Pulizia del database**.

## quarantena delle notifiche push {#push-notification-quarantines}

Il meccanismo di quarantena per le notifiche push è globalmente uguale al processo generale. Vedere [Informazioni sulle quarantena](#about-quarantines). Tuttavia, alcuni errori vengono gestiti in modo diverso per le notifiche push. Ad esempio, per alcuni errori software, non vengono eseguiti tentativi all&#39;interno della stessa consegna. Le specifiche per la notifica push sono elencate di seguito. Il meccanismo dei tentativi (numero di tentativi, frequenza) è lo stesso utilizzato per le e-mail.

Gli elementi messi in quarantena sono token dispositivo.

### quarantena iOS {#ios-quarantine}

**Per iOS - connettore binario**

>[!NOTE]
A partire dalla release Campaign 20.3, il connettore legacy binario per iOS è diventato obsoleto. Se utilizzi questo connettore, devi adattare di conseguenza l’implementazione. [Ulteriori informazioni](https://helpx.adobe.com/it/campaign/kb/migrate-to-apns-http2.html)

Per ogni notifica,  Adobe Campaign riceve gli errori sincroni e asincroni dal server APN. Per i seguenti errori sincroni,  Adobe Campaign genera errori software:

* Problemi di lunghezza del payload: nessun tentativo, il motivo dell&#39;errore è **[!UICONTROL Unreachable]**.
* Problemi di scadenza del certificato: nessun tentativo, il motivo dell&#39;errore è **[!UICONTROL Unreachable]**.
* Connessione persa durante la consegna: il motivo dell&#39;errore è **[!UICONTROL Unreachable]**.
* Problema di configurazione del servizio (certificato non valido, password del certificato non valida, nessun certificato): nessun tentativo, il motivo dell&#39;errore è **[!UICONTROL Unreachable]**.

Il server APN avvisa in modo asincrono  Adobe Campaign che un token dispositivo è stato deregistrato (quando l&#39;applicazione mobile è stata disinstallata dall&#39;utente). Il flusso di lavoro **[!UICONTROL mobileAppOptOutMgt]** viene eseguito ogni 6 ore per contattare i servizi di feedback APN per aggiornare la tabella **AppSubscriptionRcp**. Per tutti i token disattivati, il campo **Disabled** è impostato su **True** e la sottoscrizione collegata a tale token dispositivo verrà automaticamente esclusa dalle consegne future.

**Per iOS - Connettore HTTP/V2**

Il protocollo HTTP/V2 consente un feedback diretto e uno stato per ogni invio push. Se si utilizza il connettore del protocollo HTTP/V2, il servizio di feedback non viene più chiamato dal flusso di lavoro **[!UICONTROL mobileAppOptOutMgt]**. I token non registrati vengono gestiti in modo diverso tra il connettore binario iOS e il connettore iOS HTTP/V2. Un token viene considerato non registrato quando un’applicazione mobile viene disinstallata o reinstallata.

Sincrona, se le APN restituiscono uno stato &quot;non registrato&quot; per un messaggio, il token di destinazione verrà messo immediatamente in quarantena.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Stato</strong><br /> </td> 
   <td> <strong>Messaggio di errore</strong><br /> </td> 
   <td> <strong>Tipo di errore</strong><br /> </td> 
   <td> <strong>Motivo errore</strong><br /> </td> 
   <td> <strong>Riprova</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dispositivo di destinazione attivato su<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Dispositivo di destinazione spento<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> L'utente disabilita le notifiche per l'applicazione<br /> </td> 
   <td> OK<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi: payload troppo grande<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Payload troppo lungo<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi: problema di formato di contenuto imprevisto<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Vari messaggi di errore in base all'errore<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Undefined<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Problema del certificato (password, danneggiamento, ecc.) e verifica la connessione a APNs issue<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Vari messaggi di errore in base all'errore<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Connessione di rete persa durante l'invio<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore di connessione<br /> </td> 
   <td> Undefined<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio APN: Annullamento della registrazione<br /> l'utente ha rimosso l'applicazione o il token è scaduto<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Non registrato<br /> </td> 
   <td> Hard<br /> </td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio APN: tutti gli altri errori<br /> </td> 
   <td> Errore<br /> </td> 
   <td> La causa del rifiuto dell'errore sarà presente nel messaggio di errore<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
 </tbody> 
</table>

### quarantena Android {#android-quarantine}

**Per Android V1**

Per ogni notifica,  Adobe Campaign riceve gli errori sincroni direttamente dal server FCM.  campagna di Adobe li gestisce al volo e genera errori rigidi o morbidi in base alla gravità dell&#39;errore e i tentativi possono essere eseguiti:

* Lunghezza payload superata, problema di connessione, problema di disponibilità del servizio: tentativi eseguiti, errore software, motivo errore è **[!UICONTROL Refused]**.
* Quota dispositivo superata: nessun tentativo, errore software, motivo errore è **[!UICONTROL Refused]**.
* Token non valido o non registrato, errore imprevisto, problema dell&#39;account del mittente: nessun tentativo, errore rigido, motivo errore è **[!UICONTROL Refused]**.

Il flusso di lavoro **[!UICONTROL mobileAppOptOutMgt]** viene eseguito ogni 6 ore per aggiornare la tabella **AppSubscriptionRcp**. Per i token dichiarati non registrati o non più validi, il campo **Disabled** è impostato su **True** e la sottoscrizione collegata a tale token dispositivo verrà automaticamente esclusa dalle consegne future.

Durante l&#39;analisi della consegna, tutti i dispositivi esclusi dalla destinazione vengono automaticamente aggiunti alla tabella **excludeLogAppSubRcp**.

>[!NOTE]
Per i clienti che utilizzano il connettore Baidu, ecco i diversi tipi di errori:
* Problema di connessione all&#39;inizio della consegna: tipo di errore **[!UICONTROL Undefined]**, motivo di errore **[!UICONTROL Unreachable]**, il tentativo viene eseguito.
* Connessione persa durante la consegna: errore soft, motivo di errore **[!UICONTROL Refused]**, il tentativo viene eseguito.
* Errore sincrono restituito da Baidu durante l&#39;invio: errore rigido, motivo errore **[!UICONTROL Refused]**, non viene eseguito alcun nuovo tentativo.

 Adobe Campaign contatta il server di Baidu ogni 10 minuti per recuperare lo stato del messaggio inviato e aggiorna i registri di trasmissione. Se un messaggio viene dichiarato come inviato, lo stato del messaggio nei registri di trasmissione è impostato su **[!UICONTROL Received]**. Se Baidu dichiara un errore, lo stato è impostato su **[!UICONTROL Failed]**.

**Per Android V2**

Il meccanismo di quarantena Android V2 utilizza lo stesso processo di Android V1, lo stesso vale per l&#39;aggiornamento delle sottoscrizioni e delle esclusioni. Per ulteriori informazioni, consultare la sezione [Android V1](#android-quarantine).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Stato</strong><br /> </td> 
   <td> <strong>Messaggio di errore</strong><br /> </td> 
   <td> <strong>Tipo di errore</strong><br /> </td> 
   <td> <strong>Motivo errore</strong><br /> </td> 
   <td> <strong>Riprova</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi: parole chiave non consentite utilizzate nei campi personalizzati<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Non è possibile utilizzare le seguenti parole chiave: {1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi: payload troppo grande<br /> </td> 
   <td> Errore<br /> </td> 
   <td> La notifica è troppo pesante: {1} bit, mentre solo {2} sono autorizzati<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Connessione di rete persa durante l'invio<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Nessuna risposta dal servizio Firebase Cloud Messaging all'indirizzo: {1}<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Il server FCM non è temporaneamente disponibile (ad esempio con timeout). <br /> </td> 
   <td> Errore<br /> </td> 
   <td> Il servizio Firebase Cloud Messaging è temporaneamente non disponibile<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Errore durante l'autenticazione dell'account del mittente<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Impossibile identificare l'account sviluppatore. Controllare l'ID e la password<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Quota dispositivo superata<br /> </td> 
   <td> Errore<br /> </td> 
   <td> </td> 
   <td> Soft<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> Yes<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Registrazione non valida / non registrata<br /> </td> 
   <td> Errore<br /> </td> 
   <td> </td> 
   <td> Hard<br /> </td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Tutti gli altri errori<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Il server Firebase Cloud Messaging ha restituito un codice di errore imprevisto: {1} </td> 
   <td> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
    <tr> 
   <td> Rifiuto del messaggio FCM: Argomento non valido<br /> </td> 
   <td> Errore<br /> </td> 
   <td> INVALID_ARGUMENT </td> 
   <td> Ignorato</td> 
   <td> Undefined<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: Errore di autenticazione di terze parti<br /> </td> 
   <td> Errore<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: ID mittente non corrispondente<br /> </td> 
   <td> Errore<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Morbido</td>
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: Non registrato<br /> </td> 
   <td> Errore<br /> </td>
   <td> NON REGISTRATO </td> 
   <td> Rigido</td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: Internal<br /> </td> 
   <td> Errore<br /> </td> 
   <td> INTERNO </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: Non disponibile<br /> </td> 
   <td> Errore<br /> </td> 
   <td> NON DISPONIBILE</td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: codice di errore imprevisto<br /> </td> 
   <td> Errore<br /> </td> 
   <td> codice di errore imprevisto</td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
  <tr> 
   <td> Autenticazione: Problema di connessione<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Impossibile connettersi al server di autenticazione </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> Yes<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Client o ambito non autorizzati nella richiesta.<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Il client non è autorizzato a recuperare i token di accesso utilizzando questo metodo, oppure il client non è autorizzato per alcuno degli ambiti richiesti.<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Accesso negato<br /> </td> 
   <td> Errore<br /> </td>
   <td> access_disabled</td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: E-mail non valida<br /> </td> 
   <td> Errore<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: JWT<br /> non valido </td> 
   <td> Errore<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Firma JWT<br /> non valida </td> 
   <td> Errore<br /> </td> 
   <td> invalid_Grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Ambito OAuth o pubblico token ID non valido fornito<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client</td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Client OAuth disabilitato<br /> </td> 
   <td> Errore<br /> </td> 
   <td> disabled_client</td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
 </tbody> 
</table>

## quarantena SMS {#sms-quarantines}

**Per connettori standard**

Il meccanismo di quarantena per i messaggi SMS è globalmente lo stesso del processo generale. Vedere [Informazioni sulle quarantena](#about-quarantines). Le specifiche per gli SMS sono elencate di seguito.

>[!NOTE]
La tabella **[!UICONTROL Delivery log qualification]** non si applica al connettore **SMPP** generico esteso.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Stato</strong><br /> </td> 
   <td> <strong>Messaggio di errore</strong><br /> </td> 
   <td> <strong>Tipo di errore</strong><br /> </td> 
   <td> <strong>Motivo errore</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Inviato al provider<br /> </td> 
   <td> Inviato<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ricevuto sul dispositivo mobile<br /> </td> 
   <td> Received<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Errore restituito dal provider<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore durante la ricezione dei dati (SR o MO)<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Conferma MT non valida<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore '{1}' durante l'elaborazione del frame di riconoscimento per la query di invio<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Errore durante l'invio del MT<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore durante l'invio dei messaggi<br /> </td> 
   <td> Soft<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Per il connettore SMPP generico esteso**

Quando si utilizza il protocollo SMPP per inviare messaggi SMS, la gestione degli errori viene gestita in modo diverso. Per ulteriori informazioni sul connettore SMPP generico esteso, fare riferimento a [questa pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

Il connettore SMPP recupera i dati dal messaggio SR (Status Report) restituito utilizzando espressioni regolari (regex) per filtrare il contenuto. Questi dati vengono quindi confrontati con le informazioni presenti nella tabella **[!UICONTROL Delivery log qualification]** (disponibile dal menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**).

Prima che un nuovo tipo di errore sia qualificato, il motivo dell&#39;errore è sempre impostato su **Rifiutato** per impostazione predefinita.

>[!NOTE]
I tipi di errore e i motivi dell&#39;errore sono gli stessi utilizzati per le e-mail. Vedere [Tipi e motivi di mancata consegna](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons).
Chiedete al vostro fornitore un elenco di stati e codici di errore al fine di impostare i tipi di errore e i motivi corretti per l&#39;errore nella tabella delle qualifiche del registro di consegna.

Esempio di messaggio generato:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Tutti i messaggi di errore iniziano con **SR** per distinguere i codici di errore SMS dai codici di errore e-mail.
* La seconda parte (**Generic** in questo esempio) del messaggio di errore fa riferimento al nome dell&#39;implementazione SMSC, come definito nel campo **[!UICONTROL SMSC implementation name]** dell&#39;account esterno SMS. Consulta [questa pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Poiché lo stesso codice di errore può avere un significato diverso per ciascun provider, questo campo consente di sapere quale provider ha generato il codice di errore. L&#39;errore può essere trovato nella documentazione del fornitore pertinente.

* La terza parte (**DELIVRD** in questo esempio) del messaggio di errore corrisponde al codice di stato recuperato dalla SR utilizzando il regex di estrazione dello stato definito nell&#39;account esterno di SMS.

   Questo regex è specificato nella scheda **[!UICONTROL SMSC specificities]** dell&#39;account esterno. Consulta [questa pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Per impostazione predefinita, il regex estrae il campo **stat:** come definito nella sezione **Appendice B** della specifica **SMPP 3.4**.

* La quarta parte (**000** in questo esempio) del messaggio di errore corrisponde al codice di errore estratto dalla SR utilizzando il regex di estrazione del codice di errore definito nell&#39;account esterno di SMS.

   Questo regex è specificato nella scheda **[!UICONTROL SMSC specificities]** dell&#39;account esterno. Consulta [questa pagina](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

   Per impostazione predefinita, il regex estrae il campo **err:** come definito nella sezione **Appendice B** della specifica **SMPP 3.4**.

* Tutto ciò che viene dopo il simbolo di tubo (|) viene visualizzato solo nella colonna **[!UICONTROL First text]** della tabella **[!UICONTROL Delivery log qualification]**. Questo contenuto viene sempre sostituito da **#MESSAGE#** dopo la normalizzazione del messaggio. Questo processo evita di inserire più voci per errori simili ed è lo stesso delle e-mail. Per ulteriori informazioni, vedere [Qualificazione della posta in sospeso](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification).

Il connettore SMPP generico esteso applica un euristico per trovare valori predefiniti ragionevoli: se lo stato inizia con **DELIV**, viene considerato un successo perché corrisponde agli stati comuni **DELIVRD** o **DELIVERED** utilizzati dalla maggior parte dei fornitori. Qualsiasi altro stato porta a un duro fallimento.
