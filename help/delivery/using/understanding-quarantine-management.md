---
product: campaign
title: Informazioni sulla gestione della quarantena
description: Informazioni sulla gestione della quarantena
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '2997'
ht-degree: 12%

---

# Informazioni sulla gestione della quarantena{#understanding-quarantine-management}



 Adobe Campaign gestisce un elenco di indirizzi in quarantena. I destinatari il cui indirizzo è stato messo in quarantena sono esclusi per impostazione predefinita durante l’analisi della consegna e non saranno oggetto di targeting. Un indirizzo e-mail può essere posto in quarantena, ad esempio, quando la casella di posta è piena o se l’indirizzo non esiste. In ogni caso, la procedura di quarantena è conforme alle norme specifiche descritte di seguito.

>[!NOTE]
>
>Questa sezione si applica ai canali online: e-mail, SMS, notifica push.

## Ottimizzazione della consegna tramite la gestione della quarantena {#optimizing-your-delivery-through-quarantines}

I profili con indirizzi e-mail o numeri di telefono in quarantena vengono automaticamente esclusi durante la preparazione dei messaggi (vedi [Identificare gli indirizzi messi in quarantena per una consegna](#identifying-quarantined-addresses-for-a-delivery)). In questo modo le consegne sono più rapide, poiché il tasso di errore ha un effetto significativo sulla velocità di consegna.

Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena ti consente quindi di evitare di essere aggiunta al elenco Bloccati da questi provider.

Inoltre, le quarantene contribuiscono a ridurre i costi di invio degli SMS escludendo numeri di telefono errati dalle consegne.

Per ulteriori informazioni sulle best practice per proteggere e ottimizzare le consegne, consulta [questa pagina](delivery-best-practices.md).

### Quarantena rispetto elenco Bloccati {#quarantine-vs-denylist}

La quarantena e il elenco Bloccati non si applicano allo stesso oggetto:

* **Quarantena** si applica solo a un **indirizzo** (o numero di telefono, ecc.), non al profilo stesso. Ad esempio, un profilo il cui indirizzo e-mail è messo in quarantena può aggiornare il proprio profilo e immettere un nuovo indirizzo e può quindi essere nuovamente oggetto di targeting mediante azioni di consegna. Allo stesso modo, se due profili hanno lo stesso numero di telefono, saranno entrambi interessati se il numero viene messo in quarantena.

   Gli indirizzi o i numeri di telefono messi in quarantena vengono visualizzati nella [registri di esclusione](#identifying-quarantined-addresses-for-a-delivery) (per una consegna) o [elenco di quarantena](#identifying-quarantined-addresses-for-the-entire-platform) (per l&#39;intera piattaforma).

* Essere sul **elenco Bloccati**, d&#39;altra parte, si tradurrà in **profilo** non viene più eseguito il targeting dalla consegna, ad esempio dopo un annullamento dell’abbonamento (opt-out), per un determinato canale. Ad esempio, se un profilo nel elenco Bloccati del canale e-mail ha due indirizzi e-mail, entrambi gli indirizzi saranno esclusi dalla consegna.

   Puoi verificare se un profilo è sul elenco Bloccati di uno o più canali nel **[!UICONTROL No longer contact]** della sezione del profilo **[!UICONTROL General]** scheda . Vedi [questa sezione](../../platform/using/editing-a-profile.md#general-tab).

>[!NOTE]
>
>La quarantena include una **[!UICONTROL Denylisted]** , che si applica quando i destinatari segnalano il messaggio come spam o rispondono a un messaggio SMS con una parola chiave come &quot;STOP&quot;. In tal caso, l’indirizzo o il numero di telefono del profilo in questione viene messo in quarantena con il **[!UICONTROL Denylisted]** stato. Per ulteriori informazioni sulla gestione dei messaggi SMS STOP, consulta [questa sezione](../../delivery/using/sms-send.md#processing-inbound-messages).

## Identificare gli indirizzi messi in quarantena {#identifying-quarantined-addresses}

È possibile elencare gli indirizzi messi in quarantena per una consegna specifica o per l’intera piattaforma.

### Identificare gli indirizzi messi in quarantena per una consegna {#identifying-quarantined-addresses-for-a-delivery}

Gli indirizzi messi in quarantena per una consegna specifica sono elencati durante la fase di preparazione della consegna, nei registri di consegna del dashboard di consegna (vedi [Log di consegna e cronologia](delivery-dashboard.md#delivery-logs-and-history)).

### Identificare gli indirizzi messi in quarantena per l’intera piattaforma {#identifying-quarantined-addresses-for-the-entire-platform}

Gli amministratori possono elencare gli indirizzi messi in quarantena per l’intera piattaforma dalla **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** nodo.

>[!NOTE]
>
>Questo menu elenca gli elementi messi in quarantena per i canali **e-mail**, **SMS** e di **notifiche push**.

Per ciascun indirizzo sono disponibili le seguenti informazioni:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>L’aumento del numero delle quarantene è un effetto normale, legato all’&quot;usura&quot; del database. Ad esempio, se la durata di un indirizzo e-mail è considerata di tre anni e la tabella dei destinatari aumenta del 50% ogni anno, l’aumento delle quarantene può essere calcolato come segue:
>
>Fine anno 1: 1&#42;0,33)/(1+0,5)=22%.
>
>Fine anno 2: (1.22)&#42;0,33)+0,33)/(1,5+0,75)=32,5%.

### Identificare gli indirizzi messi in quarantena nei rapporti di consegna {#identifying-quarantined-addresses-in-delivery-reports}

I seguenti rapporti forniscono informazioni sugli indirizzi messi in quarantena:

* Per ogni consegna, il **[!UICONTROL Delivery summary]** il rapporto mostra il numero di indirizzi messi in quarantena nel target di consegna. Viene visualizzato:

   * il numero di indirizzi messi in quarantena durante l’analisi della consegna,

   * Il numero di indirizzi messi in quarantena dopo l’azione di consegna.

* La **[!UICONTROL Non-deliverables and bounces]** il rapporto visualizza informazioni sugli indirizzi messi in quarantena, i tipi di errore rilevato, ecc. e un guasto per dominio.

Puoi cercare queste informazioni per tutte le consegne della piattaforma (**[!UICONTROL Home page > Reports]**) o per una consegna specifica. È inoltre possibile creare rapporti personalizzati e selezionare le informazioni da visualizzare.

### Identificare gli indirizzi messi in quarantena per un destinatario {#identifying-quarantined-addresses-for-a-recipient}

Puoi cercare lo stato dell’indirizzo e-mail di qualsiasi destinatario. A questo scopo, seleziona il profilo del destinatario e fai clic sul pulsante **[!UICONTROL Deliveries]** scheda . Per tutte le consegne a quel destinatario, puoi scoprire se l’indirizzo non è riuscito, se è stato messo in quarantena durante l’analisi, ecc. Per ogni cartella, puoi visualizzare solo i destinatari il cui indirizzo e-mail è in quarantena. Per eseguire questa operazione, utilizza la variabile **[!UICONTROL Quarantined email address]** filtro dell&#39;applicazione.

![](assets/tech_quarant_recipients_filter.png)


## Condizioni per la messa in quarantena di un indirizzo {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign gestisce la quarantena in base al tipo di consegna non riuscita e al motivo assegnato durante la qualifica dei messaggi di errore (consulta [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification) e [Tipi e motivi di errori di consegna](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **Errore ignorato**: gli errori ignorati non mettono un indirizzo in quarantena.
* **Errore rigido**: l’indirizzo e-mail corrispondente viene messo immediatamente in quarantena.
* **Errore morbido**: gli errori morbidi non mettono immediatamente un indirizzo in quarantena, ma incrementano un contatore di errori. Per ulteriori informazioni, consulta [Gestione degli errori software](#soft-error-management).

Se un utente qualifica un’e-mail come spam ([circuito di retroazione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)), il messaggio viene automaticamente reindirizzato verso una casella di posta tecnica gestita da Adobe. L’indirizzo e-mail dell’utente viene quindi messo automaticamente in quarantena con lo stato **[!UICONTROL Denylisted]**. Questo stato si riferisce solo all’indirizzo , il profilo non è nel elenco Bloccati, in modo che l’utente continui a ricevere messaggi SMS e notifiche push.

>[!NOTE]
>
>In Adobe Campaign la quarantena distingue tra maiuscole e minuscole. Accertati di importare gli indirizzi e-mail in lettere minuscole, in modo che non vengano reindirizzate in un secondo momento.

Nell’elenco degli indirizzi messi in quarantena (vedi [Identificazione degli indirizzi messi in quarantena per l’intera piattaforma](#identifying-quarantined-addresses-for-the-entire-platform)), **[!UICONTROL Error reason]** il campo indica perché l’indirizzo selezionato è stato messo in quarantena.

![](assets/tech_quarant_error_reasons.png)

### Gestione degli errori software {#soft-error-management}

Al contrario degli errori rigidi, gli errori morbidi non mettono immediatamente un indirizzo in quarantena, ma incrementano un contatore di errori.

I tentativi verranno eseguiti durante il [durata della consegna](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period). Quando il contatore di errori raggiunge la soglia limite, l’indirizzo viene messo in quarantena. Per ulteriori informazioni, consulta [Tentativi dopo un errore temporaneo di consegna](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

Il contatore degli errori viene reinizializzato se l’ultimo errore significativo si è verificato più di 10 giorni fa. Lo stato dell’indirizzo cambia in **Valido** e viene eliminato dall’elenco delle quarantene dal [Pulizia del database](../../production/using/database-cleanup-workflow.md) workflow.


Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), il numero massimo di tentativi da eseguire in caso di **[!UICONTROL Erroneous]** lo stato e il ritardo minimo tra i nuovi tentativi si basano ora sulle prestazioni di un IP sia storicamente che attualmente in un determinato dominio.

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign, puoi modificare il numero di errori e il periodo tra due errori. A questo scopo, modifica le impostazioni corrispondenti nella [procedura guidata di distribuzione](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) o [a livello di consegna](../../delivery/using/steps-sending-the-delivery.md#configuring-retries).


## Rimuovere un indirizzo dalla quarantena {#removing-a-quarantined-address}

### Aggiornamenti automatici {#unquarantine-auto}

Gli indirizzi che corrispondono a condizioni specifiche vengono eliminati automaticamente dall&#39;elenco di quarantena dalla [Pulizia del database](../../production/using/database-cleanup-workflow.md) workflow.

Gli indirizzi vengono rimossi automaticamente dall’elenco di quarantena nei seguenti casi:

* Indirizzi in un **[!UICONTROL With errors]** lo stato viene rimosso dall’elenco di quarantena dopo la consegna riuscita.
* Indirizzi in un **[!UICONTROL With errors]** lo stato verrà rimosso dall’elenco di quarantena se l’ultimo messaggio non recapitato è stato eseguito più di 10 giorni fa. Per ulteriori informazioni sulla gestione degli errori software, consulta [questa sezione](#soft-error-management).
* Indirizzi in un **[!UICONTROL With errors]** che rimbalzano con il **[!UICONTROL Mailbox full]** L&#39;errore verrà rimosso dall&#39;elenco di quarantena dopo 30 giorni.

Il loro stato cambia in **[!UICONTROL Valid]**.

>[!IMPORTANT]
>
>Destinatari con un indirizzo in un **[!UICONTROL Quarantine]** o **[!UICONTROL Denylisted]** lo stato non viene mai rimosso, anche se riceve un’e-mail.

### Aggiornamenti manuali {#unquarantine-manual}

Puoi anche rimuovere manualmente la quarantena di un indirizzo. Per rimuovere manualmente un indirizzo dall’elenco di quarantena, modificarne lo stato in **[!UICONTROL Valid]** dal **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** nodo.

![](assets/tech_quarant_error_status.png)

### Aggiornamenti in blocco {#unquarantine-bulk}

Potrebbe essere necessario eseguire aggiornamenti in blocco sull&#39;elenco di quarantena, ad esempio in caso di interruzione dell&#39;ISP. In questo caso, le e-mail vengono contrassegnate erroneamente come messaggi non recapitati perché non possono essere recapitate correttamente al destinatario. Questi indirizzi devono essere rimossi dall’elenco di quarantena.

Per eseguire questa operazione, crea un flusso di lavoro e aggiungi un **[!UICONTROL Query]** attività nella tabella di quarantena per filtrare tutti i destinatari interessati. Una volta identificati, possono essere rimossi dall’elenco di quarantena e inclusi nelle future consegne e-mail di Campaign.

Di seguito sono riportate le linee guida consigliate per questa query:

* Per ambienti Campaign Classic v7 con informazioni sulle regole di posta elettronica in entrata nel **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@dominio)** uguale a dominio1.com OR **Dominio e-mail (@dominio)** uguale a domain2.com OR **Dominio e-mail (@dominio)** uguale a domain3.com
   * **Stato aggiornamento (@lastModified)** su o dopo MM/GG/AAAA HH:MM:SS AM
   * **Stato aggiornamento (@lastModified)** su o prima MM/GG/AAAA HH:MM:PM SS

* Per le istanze Campaign Classic v7 con informazioni sulla risposta di mancato recapito SMTP nel **[!UICONTROL Error text]** campo dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;550-5.1.1&quot; E **Testo di errore (testo di quarantena)** contiene &quot;support.ISP.com&quot;

   dove &quot;support.ISP.com&quot; può essere: &quot;support.apple.com&quot; o &quot;support.google.com&quot; per esempio

   * **Stato aggiornamento (@lastModified)** su o dopo MM/GG/AAAA HH:MM:SS AM
   * **Stato aggiornamento (@lastModified)** su o prima MM/GG/AAAA HH:MM:PM SS


Dopo aver visualizzato l’elenco dei destinatari interessati, aggiungi un **[!UICONTROL Update data]** attività per impostare lo stato del proprio indirizzo e-mail su **[!UICONTROL Valid]** in modo che vengano rimosse dall&#39;elenco di quarantena **[!UICONTROL Database cleanup]** workflow. Puoi anche eliminarli dalla tabella di quarantena.

## quarantene di notifiche push {#push-notification-quarantines}

Il meccanismo di quarantena per le notifiche push è globalmente lo stesso del processo generale. Tuttavia alcuni errori vengono gestiti in modo diverso per le notifiche push. Ad esempio, per alcuni errori soft, non vengono eseguiti nuovi tentativi all’interno della stessa consegna. Le specificità della notifica push sono elencate di seguito. Il meccanismo di esecuzione di nuovi tentativi (numero di tentativi, frequenza) è lo stesso utilizzato per le e-mail.

Gli elementi messi in quarantena sono token dispositivo.

### quarantena iOS {#ios-quarantine}

Il protocollo HTTP/V2 consente un feedback e uno stato diretti per ogni consegna push. Se si utilizza il connettore del protocollo HTTP/V2, il servizio di feedback non viene più chiamato dal **[!UICONTROL mobileAppOptOutMgt]** workflow. Un token viene considerato non registrato quando un’app mobile viene disinstallata o reinstallata.

In modo sincrono, se le APN restituiscono uno stato &quot;non registrato&quot; per un messaggio, il token di destinazione viene messo immediatamente in quarantena.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Stato</strong><br /> </td> 
   <td> <strong>Messaggio di errore</strong><br /> </td> 
   <td> <strong>Tipo di errore</strong><br /> </td> 
   <td> <strong>Motivo dell'errore</strong><br /> </td> 
   <td> <strong>Riprova</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Dispositivo di destinazione alimentato su<br /> </td> 
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
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi - problema di formato di contenuto imprevisto<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Vari messaggi di errore in base all’errore<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non definito<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Problema del certificato (password, corruzione, ecc.) e verifica la connessione al problema APN<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Vari messaggi di errore in base all’errore<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Connessione di rete persa durante l'invio<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore di connessione<br /> </td> 
   <td> Non definito<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
   <td> Sì<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio APN: Annulla registrazione<br /> l'utente ha rimosso l'applicazione o il token è scaduto<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Non registrato<br /> </td> 
   <td> Duro<br /> </td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio APN: tutti gli altri errori<br /> </td> 
   <td> Errore<br /> </td> 
   <td> La causa del rifiuto dell’errore sarà presente nel messaggio di errore<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
 </tbody> 
</table>

### quarantena Android {#android-quarantine}

**Per Android V1**

Per ogni notifica, Adobe Campaign riceve gli errori sincroni direttamente dal server FCM. Adobe campagna li gestisce al volo e genera errori rigidi o morbidi in base alla gravità dell&#39;errore e possono essere eseguiti nuovi tentativi:

* Lunghezza del payload superata, problema di connessione, problema di disponibilità del servizio: esecuzione di un nuovo tentativo, errore morbido, motivo dell&#39;errore **[!UICONTROL Refused]**.
* Quota del dispositivo superata: nessun nuovo tentativo, errore soft, motivo di errore **[!UICONTROL Refused]**.
* Token non valido o non registrato, errore imprevisto, problema dell&#39;account del mittente: nessun nuovo tentativo, errore rigido, motivo errore **[!UICONTROL Refused]**.

La **[!UICONTROL mobileAppOptOutMgt]** il flusso di lavoro viene eseguito ogni 6 ore per aggiornare **AppSubscriptionRcp** tabella. Per i token dichiarati non registrati o non più validi, il campo **Disabilitato** è impostato su **True** e la sottoscrizione collegata a tale token dispositivo verrà automaticamente esclusa dalle consegne future.

Durante l’analisi della consegna, tutti i dispositivi esclusi dal target vengono aggiunti automaticamente al **excludeLogAppSubRcp** tabella.

>[!NOTE]
>
>Per i clienti che utilizzano il connettore Baidu, di seguito sono riportati i diversi tipi di errori:
>
>* Problema di connessione all’inizio della consegna: tipo di errore **[!UICONTROL Undefined]**, motivo dell&#39;errore **[!UICONTROL Unreachable]**, viene eseguito un nuovo tentativo.
>* Connessione persa durante una consegna: errore morbido, motivo errore **[!UICONTROL Refused]**, viene eseguito un nuovo tentativo.
>* Errore sincrono restituito da Baidu durante l&#39;invio: errore grave, motivo errore **[!UICONTROL Refused]**, non viene eseguito alcun nuovo tentativo.
>
>Adobe Campaign contatta il server Baidu ogni 10 minuti per recuperare lo stato del messaggio inviato e aggiorna i registri di trasmissione. Se un messaggio viene dichiarato come inviato, lo stato del messaggio nei registri di trasmissione è impostato su **[!UICONTROL Received]**. Se Baidu dichiara un errore, lo stato è impostato su **[!UICONTROL Failed]**.

**Per Android V2**

Il meccanismo di quarantena Android V2 utilizza lo stesso processo di Android V1, lo stesso vale per l’aggiornamento degli abbonamenti e delle esclusioni. Per ulteriori informazioni, consulta la sezione [Android V1](#android-quarantine) sezione .

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Stato</strong><br /> </td> 
   <td> <strong>Messaggio di errore</strong><br /> </td> 
   <td> <strong>Tipo di errore</strong><br /> </td> 
   <td> <strong>Motivo dell'errore</strong><br /> </td> 
   <td> <strong>Riprova</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi: parole chiave non valide utilizzate nei campi personalizzati<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Non è possibile utilizzare le seguenti parole chiave: {1}<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi: carico utile troppo grande<br /> </td> 
   <td> Errore<br /> </td> 
   <td> La notifica è troppo pesante: {1} bit, mentre sono autorizzati solo {2}<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Connessione di rete persa durante l'invio<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Nessuna risposta dal servizio Firebase Cloud Messaging sull'indirizzo: {1}<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
   <td> Sì<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Il server FCM non è temporaneamente disponibile (ad esempio con timeout). <br /> </td> 
   <td> Errore<br /> </td> 
   <td> Servizio Firebase Cloud Messaging temporaneamente non disponibile<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
   <td> Sì<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Errore durante l'autenticazione dell'account del mittente<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Impossibile identificare l'account sviluppatore. Controllare l'ID e la password<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Quota del dispositivo superata<br /> </td> 
   <td> Errore<br /> </td> 
   <td> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto del messaggio FCM: Registrazione non valida / non registrata<br /> </td> 
   <td> Errore<br /> </td> 
   <td> </td> 
   <td> Duro<br /> </td> 
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
   <td> Non definito<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: Errore di autenticazione di terze parti<br /> </td> 
   <td> Errore<br /> </td> 
   <td> THIRD_PARTY_AUTH_ERROR </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
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
   <td> Duro</td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: Interno<br /> </td> 
   <td> Errore<br /> </td> 
   <td> INTERNO </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto del messaggio FCM: Non disponibile<br /> </td> 
   <td> Errore<br /> </td> 
   <td> NON DISPONIBILE</td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
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
   <td> Sì<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Client o ambito non autorizzato nella richiesta.<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Client non autorizzato a recuperare token di accesso utilizzando questo metodo o client non autorizzato per nessuno degli ambiti richiesti.<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Accesso negato<br /> </td> 
   <td> Errore<br /> </td>
   <td> access_negato</td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: E-mail non valida<br /> </td> 
   <td> Errore<br /> </td> 
   <td> valid_Grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: JWT non valido<br /> </td> 
   <td> Errore<br /> </td> 
   <td> valid_Grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Firma JWT non valida<br /> </td> 
   <td> Errore<br /> </td> 
   <td> valid_Grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: Pubblico del token ID o dell’ambito OAuth non valido<br /> </td> 
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

Il meccanismo di quarantena per i messaggi SMS è globalmente lo stesso del processo generale. Vedi [Informazioni sulla quarantena](#about-quarantines). Le specificità di SMS sono elencate di seguito.

>[!NOTE]
>
>La **[!UICONTROL Delivery log qualification]** la tabella non si applica al **SMPP generico esteso** connettore.

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Scenario</strong><br /> </td> 
   <td> <strong>Stato</strong><br /> </td> 
   <td> <strong>Messaggio di errore</strong><br /> </td> 
   <td> <strong>Tipo di errore</strong><br /> </td> 
   <td> <strong>Motivo dell'errore</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> Inviato al provider<br /> </td> 
   <td> Inviato<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Ricevuto sul cellulare<br /> </td> 
   <td> Ricevuto<br /> </td> 
   <td> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> Errore restituito dal provider<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore durante la ricezione dei dati (SR o MO)<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Conferma MT non valida<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore '{1}' durante l'elaborazione del frame di conferma per la query di invio<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
  </tr> 
  <tr> 
   <td> Errore durante l'invio dell'MT<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore durante l'invio dei messaggi<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Per il connettore SMPP generico esteso**

Quando si utilizza il protocollo SMPP per inviare messaggi SMS, la gestione degli errori viene gestita in modo diverso. Per ulteriori informazioni sul connettore SMPP generico esteso, consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

Il connettore SMPP recupera i dati dal messaggio SR (Status Report) restituito utilizzando espressioni regolari (regexes) per filtrare il contenuto. Questi dati vengono quindi confrontati con le informazioni presenti in **[!UICONTROL Delivery log qualification]** (disponibile tramite **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** menu).

Prima che un nuovo tipo di errore sia qualificato, il motivo dell’errore è sempre impostato su **Rifiutato** per impostazione predefinita.

>[!NOTE]
>
>I tipi di errore e i motivi dell’errore sono gli stessi utilizzati per le e-mail. Vedi [Tipi e motivi di errori di consegna](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Chiedi al tuo provider di un elenco di stati e codici di errore per impostare i tipi di errori e i motivi corretti per un errore nella tabella di qualificazione del registro di consegna.

Esempio di messaggio generato:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Tutti i messaggi di errore iniziano con **SR** per distinguere i codici di errore SMS dai codici di errore e-mail.
* seconda parte (**Generico** in questo esempio) del messaggio di errore si riferisce al nome dell&#39;implementazione SMSC, come definito in **[!UICONTROL SMSC implementation name]** campo dell’account esterno SMS. Consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

   Poiché lo stesso codice di errore può avere un significato diverso per ogni provider, questo campo ti consente di sapere quale provider ha generato il codice di errore. Puoi quindi trovare l’errore nella documentazione del provider pertinente.

* terza parte (**DELIVRD** in questo esempio) del messaggio di errore corrisponde al codice di stato recuperato dall’SR utilizzando il regex di estrazione dello stato definito nell’account esterno SMS.

   Questo regex è specificato nel **[!UICONTROL SMSC specificities]** scheda dell’account esterno. Consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

   ![](assets/tech_quarant_error_regex.png)

   Per impostazione predefinita, il regex estrae il **stat:** come definito dal **Appendice B** della sezione **Specifiche di SMPP 3.4**.

* quarta parte (**000** in questo esempio) del messaggio di errore corrisponde al codice di errore estratto dall’SR utilizzando il regex di estrazione del codice di errore definito nell’account esterno SMS.

   Questo regex è specificato nel **[!UICONTROL SMSC specificities]** scheda dell’account esterno. Consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

   Per impostazione predefinita, il regex estrae il **errore:** come definito dal **Appendice B** della sezione **Specifiche di SMPP 3.4**.

* Tutto ciò che viene dopo il simbolo di tubo (|) viene visualizzato solo nel **[!UICONTROL First text]** della colonna **[!UICONTROL Delivery log qualification]** tabella. Questo contenuto viene sempre sostituito da **#MESSAGE#** dopo la normalizzazione del messaggio. Questo processo evita di avere più voci per errori simili ed è lo stesso delle e-mail. Per ulteriori informazioni, consulta [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification).

Il connettore SMPP generico esteso applica un euristico per trovare valori predefiniti ragionevoli: se lo stato inizia con **DELIV**, viene considerato un successo perché corrisponde agli stati comuni **DELIVRD** o **CONSEGNATO** utilizzato dalla maggior parte dei fornitori. Qualsiasi altro stato causa un errore grave.
