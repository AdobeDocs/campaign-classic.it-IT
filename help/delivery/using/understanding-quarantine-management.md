---
product: campaign
title: Informazioni sulla gestione della quarantena
description: Informazioni sulla gestione della quarantena
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: cfd8f5c9-f368-4a31-a1e2-1d77ceae5ced
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '3008'
ht-degree: 7%

---

# Informazioni sulla gestione della quarantena{#understanding-quarantine-management}

 Adobe Campaign gestisce un elenco di indirizzi in quarantena. I destinatari il cui indirizzo è stato messo in quarantena sono esclusi per impostazione predefinita durante l’analisi della consegna e non saranno oggetto di targeting. Un indirizzo e-mail può essere messo in quarantena, ad esempio, quando la casella di posta è piena o se l’indirizzo non esiste. In ogni caso, la procedura di quarantena è conforme alle norme specifiche descritte di seguito.

>[!NOTE]
>
>Questa sezione si applica ai canali online: e-mail, SMS, notifiche push.

## Ottimizzazione della consegna attraverso la gestione della quarantena {#optimizing-your-delivery-through-quarantines}

I profili con indirizzi e-mail o numeri di telefono in quarantena vengono automaticamente esclusi durante la preparazione dei messaggi (vedi [Identificare gli indirizzi messi in quarantena per una consegna](#identifying-quarantined-addresses-for-a-delivery)). In questo modo le consegne sono più rapide, poiché il tasso di errore ha un effetto significativo sulla velocità di consegna.

Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena consente quindi di evitare che questi provider aggiungano altri elementi al elenco Bloccati del sistema di protezione.

Inoltre, le quarantene contribuiscono a ridurre i costi di invio degli SMS escludendo numeri di telefono errati dalle consegne.

Per ulteriori informazioni sulle best practice per proteggere e ottimizzare le consegne, consulta questa pagina nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html){target="_blank"}.

### Quarantena e inserisco nell&#39;elenco Bloccati di {#quarantine-vs-denylist}

La quarantena e il elenco Bloccati di non si applicano allo stesso oggetto:

* **Quarantena** si applica solo a un **indirizzo** (o numero di telefono, ecc.), non al profilo stesso. Ad esempio, un profilo con un indirizzo e-mail messo in quarantena può aggiornare il profilo e immettere un nuovo indirizzo, per poi essere nuovamente indirizzato mediante azioni di consegna. Allo stesso modo, se due profili hanno lo stesso numero di telefono, saranno entrambi interessati se il numero viene messo in quarantena.

  Gli indirizzi o i numeri di telefono messi in quarantena vengono visualizzati nei [registri di esclusione](#identifying-quarantined-addresses-for-a-delivery) (per una consegna) o nell&#39;[elenco di quarantena](#identifying-quarantined-addresses-for-the-entire-platform) (per l&#39;intera piattaforma).

* Se invece si trova nel **inserisco nell&#39;elenco Bloccati di**, il **profilo** non sarà più oggetto della consegna, ad esempio dopo l&#39;annullamento dell&#39;abbonamento (opt-out) per un determinato canale. Ad esempio, se un profilo nell’elenco Bloccati di per il canale e-mail ha due indirizzi e-mail, entrambi gli indirizzi verranno esclusi dalla consegna.

  È possibile verificare se un profilo si trova nel elenco Bloccati di accesso a uno o più canali nella sezione **[!UICONTROL No longer contact]** della scheda **[!UICONTROL General]** del profilo.
>[!NOTE]
>
>La quarantena include uno stato **[!UICONTROL Denylisted]** che si applica quando i destinatari segnalano il messaggio come spam o rispondono a un messaggio SMS con una parola chiave come &quot;STOP&quot;. In tal caso, l&#39;indirizzo o il numero di telefono del profilo viene messo in quarantena con lo stato **[!UICONTROL Denylisted]**. Per ulteriori informazioni sulla gestione dei messaggi STOP SMS, consulta [questa sezione](../../delivery/using/sms-send.md#processing-inbound-messages).

## Identificare gli indirizzi messi in quarantena {#identifying-quarantined-addresses}

È possibile elencare gli indirizzi messi in quarantena per una consegna specifica o per l’intera piattaforma.

### Identificare gli indirizzi messi in quarantena per una consegna {#identifying-quarantined-addresses-for-a-delivery}

Gli indirizzi messi in quarantena per una consegna specifica vengono elencati durante la fase di preparazione della consegna, nei registri di consegna del dashboard di consegna (vedi [Registri di consegna e cronologia](delivery-dashboard.md#delivery-logs-and-history)).

### Identificare gli indirizzi messi in quarantena per l’intera piattaforma {#identifying-quarantined-addresses-for-the-entire-platform}

Gli amministratori possono elencare gli indirizzi messi in quarantena per l&#39;intera piattaforma dal nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

>[!NOTE]
>
>Questo menu elenca gli elementi messi in quarantena per i canali **e-mail**, **SMS** e di **notifiche push**.

Per ogni indirizzo sono disponibili le seguenti informazioni:

![](assets/tech_quarant_npai.png)

>[!NOTE]
>
>L’aumento del numero di quarantene è un effetto normale, legato all’&quot;usura&quot; del database. Ad esempio, se la durata di un indirizzo e-mail è considerata di tre anni e la tabella dei destinatari aumenta del 50% ogni anno, l’aumento delle quarantene può essere calcolato come segue:
>
>Fine anno 1: (1&#42;0,33)/(1+0,5)=22%.
>
>Fine anno 2: ((1,22&#42;0,33)+0,33)/(1,5+0,75)=32,5%.

### Identificare gli indirizzi messi in quarantena nei rapporti di consegna {#identifying-quarantined-addresses-in-delivery-reports}

I seguenti rapporti forniscono informazioni sugli indirizzi in quarantena:

* Per ogni consegna, il report **[!UICONTROL Delivery summary]** mostra il numero di indirizzi in quarantena nel target della consegna. Vengono visualizzati i seguenti elementi:

   * Il numero di indirizzi messi in quarantena durante l’analisi della consegna,

   * Il numero di indirizzi messi in quarantena dopo l’azione di consegna.

* Il report **[!UICONTROL Non-deliverables and bounces]** visualizza informazioni sugli indirizzi in quarantena, sui tipi di errore riscontrati e così via e un raggruppamento degli errori per dominio.

È possibile cercare queste informazioni per tutte le consegne della piattaforma (**[!UICONTROL Home page > Reports]**) o per una consegna specifica. Puoi anche creare rapporti personalizzati e selezionare le informazioni da visualizzare.

### Identificare gli indirizzi messi in quarantena per un destinatario {#identifying-quarantined-addresses-for-a-recipient}

Puoi cercare lo stato dell’indirizzo e-mail di qualsiasi destinatario. A tale scopo, selezionare il profilo del destinatario e fare clic sulla scheda **[!UICONTROL Deliveries]**. Per tutte le consegne a quel destinatario, puoi scoprire se l’indirizzo non è riuscito, è stato messo in quarantena durante l’analisi, ecc. Per ogni cartella, puoi visualizzare solo i destinatari il cui indirizzo e-mail è in quarantena. A tale scopo, utilizzare il filtro dell&#39;applicazione **[!UICONTROL Quarantined email address]**.

![](assets/tech_quarant_recipients_filter.png)


## Condizioni per la messa in quarantena di un indirizzo {#conditions-for-sending-an-address-to-quarantine}

Adobe Campaign gestisce la quarantena in base al tipo di consegna non riuscita e al motivo assegnato durante la qualifica dei messaggi di errore (consulta [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification) e [Tipi e motivi di consegna non riuscita](understanding-delivery-failures.md#delivery-failure-types-and-reasons)).

* **Errore ignorato**: gli errori ignorati non mettono un indirizzo in quarantena.
* **Errore rigido**: l’indirizzo e-mail corrispondente viene messo immediatamente in quarantena.
* **Errore morbido**: gli errori morbidi non mettono immediatamente un indirizzo in quarantena, ma incrementano un contatore di errori. Per ulteriori informazioni, consulta [Gestione degli errori software](#soft-error-management).

Se un utente qualifica un&#39;e-mail come spam ([ciclo di feedback](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops)), il messaggio viene automaticamente reindirizzato verso una casella di posta tecnica gestita da Adobe. L’indirizzo e-mail dell’utente viene quindi messo automaticamente in quarantena con lo stato **[!UICONTROL Denylisted]**. Questo stato si riferisce solo all’indirizzo, il profilo non è nel inserisco nell&#39;elenco Bloccati di, in modo che l’utente continui a ricevere messaggi SMS e notifiche push.

>[!NOTE]
>
>In Adobe Campaign la quarantena distingue tra maiuscole e minuscole. Accertati di importare gli indirizzi e-mail in lettere minuscole, in modo che non vengano reindirizzate in un secondo momento.

Nell&#39;elenco degli indirizzi messi in quarantena (vedere [Identificazione degli indirizzi messi in quarantena per l&#39;intera piattaforma](#identifying-quarantined-addresses-for-the-entire-platform)), il campo **[!UICONTROL Error reason]** indica il motivo per cui l&#39;indirizzo selezionato è stato messo in quarantena.

![](assets/tech_quarant_error_reasons.png)

### Gestione degli errori morbidi {#soft-error-management}

Al contrario degli errori rigidi, gli errori morbidi non mettono immediatamente un indirizzo in quarantena, ma incrementano un contatore di errori.

I tentativi verranno eseguiti durante la durata della consegna. Consulta questa [pagina](communication-channels.md) in **Invio consegna** > **Definisci il periodo di validità**. Quando il contatore di errori raggiunge la soglia limite, l’indirizzo viene messo in quarantena. Per ulteriori informazioni, consulta [Tentativi dopo un errore temporaneo di consegna](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).

Il contatore degli errori viene reinizializzato se l&#39;ultimo errore significativo si è verificato più di 10 giorni fa. Lo stato dell&#39;indirizzo cambia quindi in **Valido** e viene eliminato dall&#39;elenco delle quarantene dal flusso di lavoro [Database cleanup](../../production/using/database-cleanup-workflow.md).


Per le installazioni in hosting o ibride, se hai eseguito l&#39;aggiornamento all&#39;[MTA avanzato](sending-with-enhanced-mta.md), il numero massimo di tentativi da eseguire in caso di stato **[!UICONTROL Erroneous]** e il ritardo minimo tra i tentativi si basano ora sulle prestazioni sia cronologiche che attuali di un IP in un determinato dominio.

Per le installazioni on-premise e le installazioni in hosting/ibride che utilizzano l’MTA di Campaign legacy, puoi modificare il numero di errori e il periodo tra due errori. A tale scopo, modificare le impostazioni corrispondenti nella [procedura guidata di distribuzione](../../installation/using/deploying-an-instance.md) (**[!UICONTROL Email channel]** > **[!UICONTROL Advanced parameters]**) o a livello di consegna. Vedi questa [pagina](communication-channels.md) in **Invio consegna** > **Configura nuovi tentativi**.


## Rimuovere un indirizzo dalla quarantena {#removing-a-quarantined-address}

### Aggiornamenti automatici {#unquarantine-auto}

Gli indirizzi che soddisfano condizioni specifiche vengono eliminati automaticamente dall&#39;elenco di quarantena dal flusso di lavoro [Database cleanup](../../production/using/database-cleanup-workflow.md).

Gli indirizzi vengono rimossi automaticamente dall’elenco di quarantena nei seguenti casi:

* Gli indirizzi con stato **[!UICONTROL With errors]** verranno rimossi dall&#39;elenco di quarantena dopo una consegna riuscita.
* Gli indirizzi con lo stato **[!UICONTROL With errors]** verranno rimossi dall&#39;elenco di quarantena se l&#39;ultimo messaggio non recapitato è stato eseguito più di 10 giorni fa. Per ulteriori informazioni sulla gestione degli errori software, consulta [questa sezione](#soft-error-management).
* Gli indirizzi con stato **[!UICONTROL With errors]** che non hanno superato l&#39;errore **[!UICONTROL Mailbox full]** verranno rimossi dall&#39;elenco di quarantena dopo 30 giorni.

Il loro stato diventa quindi **[!UICONTROL Valid]**.

>[!IMPORTANT]
>
>I destinatari con un indirizzo nello stato **[!UICONTROL Quarantine]** o **[!UICONTROL Denylisted]** non vengono mai rimossi, anche se ricevono un&#39;e-mail.

### Aggiornamenti manuali {#unquarantine-manual}

È inoltre possibile rimuovere manualmente la quarantena di un indirizzo. Per rimuovere manualmente un indirizzo dall&#39;elenco di quarantena, modificarne lo stato in **[!UICONTROL Valid]** dal nodo **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.

![](assets/tech_quarant_error_status.png)

### Aggiornamenti in blocco {#unquarantine-bulk}

Potrebbe essere necessario eseguire aggiornamenti in blocco sull’elenco di quarantena, ad esempio in caso di interruzione del servizio dell’ISP. In questo caso, le e-mail vengono erroneamente contrassegnate come mancate consegne perché non possono essere consegnate correttamente al destinatario. Questi indirizzi devono essere rimossi dall’elenco di quarantena.

Per eseguire questa operazione, crea un flusso di lavoro e aggiungi un&#39;attività **[!UICONTROL Query]** nella tabella di quarantena per filtrare tutti i destinatari interessati. Una volta identificate, possono essere rimosse dall’elenco di quarantena e incluse nelle consegne e-mail future di Campaign.

Di seguito sono riportate le linee guida consigliate per questa query:

* Per gli ambienti Campaign Classic v7 con informazioni sulle regole e-mail in entrata nel campo **[!UICONTROL Error text]** dell’elenco di quarantena:

   * **Testo di errore (testo di quarantena)** contiene &quot;Momen_Code10_InvalidRecipient&quot;
   * **Dominio e-mail (@domain)** uguale a domain1.com OPPURE **Dominio e-mail (@domain)** uguale a domain2.com OPPURE **Dominio e-mail (@domain)** uguale a domain3.com
   * **Aggiorna stato (@lastModified)** in data o dopo `MM/DD/YYYY HH:MM:SS AM`
   * **Aggiorna stato (@lastModified)** in data `MM/DD/YYYY HH:MM:SS PM` o prima

* Per le istanze di Campaign Classic v7 con informazioni di risposta SMTP non recapitate nel campo **[!UICONTROL Error text]** dell&#39;elenco di quarantena:

   * **Testo di errore (testo quarantena)** contiene &quot;550-5.1.1&quot; E **Testo di errore (testo quarantena)** contiene &quot;support.ISP.com&quot;

  dove &quot;support.ISP.com&quot; può essere: &quot;support.apple.com&quot; o &quot;support.google.com&quot;, ad esempio

   * **Aggiorna stato (@lastModified)** in data o dopo `MM/DD/YYYY HH:MM:SS AM`
   * **Aggiorna stato (@lastModified)** in data `MM/DD/YYYY HH:MM:SS PM` o prima

Una volta ottenuto l&#39;elenco dei destinatari interessati, aggiungere un&#39;attività **[!UICONTROL Update data]** per impostare lo stato del loro indirizzo e-mail su **[!UICONTROL Valid]** in modo che vengano rimossi dall&#39;elenco di quarantena dal flusso di lavoro **[!UICONTROL Database cleanup]**. Puoi anche semplicemente eliminarli dalla tabella di quarantena.

## Quarantene di notifica push {#push-notification-quarantines}

Il meccanismo di quarantena per le notifiche push è globalmente lo stesso del processo generale. Tuttavia, alcuni errori vengono gestiti in modo diverso per le notifiche push. Ad esempio, per alcuni errori soft, non vengono eseguiti nuovi tentativi all’interno della stessa consegna. Le specificità per le notifiche push sono elencate di seguito. Il meccanismo di esecuzione dei nuovi tentativi (numero di tentativi, frequenza) è lo stesso utilizzato per le e-mail.

Gli elementi messi in quarantena sono token del dispositivo.

### quarantena di iOS {#ios-quarantine}

Il protocollo HTTP/V2 consente un feedback diretto e uno stato per ogni consegna push. Se si utilizza il connettore del protocollo HTTP/V2, il servizio di feedback non verrà più chiamato dal flusso di lavoro **[!UICONTROL mobileAppOptOutMgt]**. Un token viene considerato non registrato quando un’app mobile viene disinstallata o reinstallata.

In modo sincrono, se il servizio APN restituisce lo stato &quot;unregistered&quot; per un messaggio, il token di destinazione verrà messo immediatamente in quarantena.

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
   <td> Dispositivo di destinazione acceso<br /> </td> 
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
   <td> Fase di creazione/analisi dei messaggi - Payload troppo grande<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Payload troppo lungo<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi dei messaggi - problema di formato del contenuto imprevisto<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Vari messaggi di errore in base all'errore<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non definito<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Problema del certificato (password, danneggiamento e così via) e verifica della connessione al problema APNs<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Vari messaggi di errore in base all'errore<br /> </td> 
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
   <td> Messaggio APNs rifiutato: annullamento della registrazione<br /> l'utente ha rimosso l'applicazione o il token è scaduto<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Non registrati<br /> </td> 
   <td> Rigido<br /> </td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiuto messaggio APN: tutti gli altri errori<br /> </td> 
   <td> Errore<br /> </td> 
   <td> La causa del rifiuto dell'errore sarà presente nel messaggio di errore<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
 </tbody> 
</table>

### quarantena di Android {#android-quarantine}

**Per Android V1**

Per ogni notifica, Adobe Campaign riceve gli errori sincroni direttamente dal server FCM. Adobe campaign li gestisce al volo e genera errori rigidi o morbidi in base alla gravità dell’errore. È possibile eseguire nuovi tentativi:

* Lunghezza del payload superata, problema di connessione, problema di disponibilità del servizio: nuovo tentativo eseguito, errore morbido. Motivo dell&#39;errore: **[!UICONTROL Refused]**.
* Quota dispositivo superata: nessun nuovo tentativo, errore soft, motivo errore: **[!UICONTROL Refused]**.
* Token non valido o non registrato, errore imprevisto, problema dell&#39;account del mittente: nessun nuovo tentativo, errore rigido, motivo errore: **[!UICONTROL Refused]**.

Il flusso di lavoro **[!UICONTROL mobileAppOptOutMgt]** viene eseguito ogni 6 ore per aggiornare la tabella **AppSubscriptionRcp**. Per i token dichiarati non registrati o non più validi, il campo **Disabilitato** è impostato su **True** e la sottoscrizione collegata al token del dispositivo verrà automaticamente esclusa dalle consegne future.

Durante l&#39;analisi della consegna, tutti i dispositivi esclusi dalla destinazione vengono aggiunti automaticamente alla tabella **excludeLogAppSubRcp**.

>[!NOTE]
>
>Per i clienti che utilizzano il connettore Baidu, di seguito sono riportati i diversi tipi di errori:
>
>* Problema di connessione all&#39;inizio della consegna: tipo di errore **[!UICONTROL Undefined]**, motivo dell&#39;errore **[!UICONTROL Unreachable]**, nuovo tentativo eseguito.
>* Connessione persa durante una consegna: errore morbido, motivo errore **[!UICONTROL Refused]**, nuovo tentativo eseguito.
>* Errore sincrono restituito da Baidu durante l&#39;invio: errore rigido, motivo dell&#39;errore **[!UICONTROL Refused]**, nessun nuovo tentativo eseguito.
>
>Adobe Campaign contatta il server Baidu ogni 10 minuti per recuperare lo stato del messaggio inviato e aggiorna i broadLog. Se un messaggio viene dichiarato come inviato, lo stato del messaggio nei broadLog è impostato su **[!UICONTROL Received]**. Se Baidu dichiara un errore, lo stato viene impostato su **[!UICONTROL Failed]**.

**Per Android V2**

Il meccanismo di quarantena di Android V2 utilizza lo stesso processo di Android V1, lo stesso vale per l’aggiornamento delle sottoscrizioni e delle esclusioni. Per ulteriori informazioni, consulta la sezione [Android V1](#android-quarantine).

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
   <td> Fase di creazione/analisi del messaggio: utilizzo di parole chiave non valide nei campi personalizzati<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Impossibile utilizzare le seguenti parole chiave: {1}<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Fase di creazione/analisi del messaggio: payload troppo grande<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Notifica troppo pesante: {1} bit, mentre solo {2} sono autorizzati<br /> </td> 
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
   <td> Rifiuto del messaggio FCM: il server FCM è temporaneamente non disponibile (ad esempio con timeout). <br /> </td> 
   <td> Errore<br /> </td> 
   <td> Il servizio Firebase Cloud Messaging non è al momento disponibile<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
   <td> Sì<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggio FCM rifiutato: errore durante l'autenticazione dell'account mittente<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Impossibile identificare l'account sviluppatore. Controllare ID e password<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggio FCM rifiutato: quota dispositivo superata<br /> </td> 
   <td> Errore<br /> </td> 
   <td> </td> 
   <td> Morbido<br /> </td> 
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggio FCM rifiutato: registrazione non valida / non registrata<br /> </td> 
   <td> Errore<br /> </td> 
   <td> </td> 
   <td> Rigido<br /> </td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
  <tr> 
   <td> Messaggio FCM rifiutato: tutti gli altri errori<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Il server Firebase Cloud Messaging ha restituito un codice di errore imprevisto: {1} </td> 
   <td> </td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr> 
    <tr> 
   <td> Messaggio FCM rifiutato: argomento non valido<br /> </td> 
   <td> Errore<br /> </td> 
   <td> ARGOMENTO_NON VALIDO </td> 
   <td> Ignorato</td> 
   <td> Non definito<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Messaggio FCM rifiutato: errore di autenticazione di terze parti<br /> </td> 
   <td> Errore<br /> </td> 
   <td> ERRORE_AUTH_TERZE PARTI </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
  </tr>
    <tr> 
   <td> Messaggio FCM rifiutato: ID mittente non corrispondente<br /> </td> 
   <td> Errore<br /> </td> 
   <td> SENDER_ID_MISMATCH </td> 
   <td> Morbido</td>
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Rifiuto messaggio FCM: annullamento registrazione<br /> </td> 
   <td> Errore<br /> </td>
   <td> NON REGISTRATO </td> 
   <td> Rigido</td> 
   <td> Utente sconosciuto<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Messaggio FCM rifiutato: interno<br /> </td> 
   <td> Errore<br /> </td> 
   <td> INTERNO </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
  </tr>
    <tr> 
   <td> Messaggio FCM rifiutato: non disponibile<br /> </td> 
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
   <td> Autenticazione: problema di connessione<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Impossibile connettersi al server di autenticazione </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> Sì<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: client o ambito non autorizzato nella richiesta.<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: il client non è autorizzato a recuperare i token di accesso utilizzando questo metodo oppure il client non è autorizzato per nessuno degli ambiti richiesti.<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client </td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: accesso negato<br /> </td> 
   <td> Errore<br /> </td>
   <td> accesso negato</td> 
   <td> Ignorato</td>
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: e-mail non valida<br /> </td> 
   <td> Errore<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: JWT<br /> non valido </td> 
   <td> Errore<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: firma JWT non valida<br /> </td> 
   <td> Errore<br /> </td> 
   <td> invalid_grant </td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: ambito OAuth o pubblico del token ID non valido fornito<br /> </td> 
   <td> Errore<br /> </td> 
   <td> unauthorized_client</td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
    <tr> 
   <td> Autenticazione: client OAuth disabilitato<br /> </td> 
   <td> Errore<br /> </td> 
   <td> disabled_client</td> 
   <td> Ignorato</td> 
   <td> Rifiutato<br /> </td> 
   <td> No<br /> </td> 
  </tr>
 </tbody> 
</table>

## Quarantene SMS {#sms-quarantines}

**Per connettori standard**

Il meccanismo di quarantena per i messaggi SMS è globalmente lo stesso del processo generale. Consulta [Informazioni sulla quarantena](#about-quarantines). Le specificità per gli SMS sono elencate di seguito.

>[!NOTE]
>
>La tabella **[!UICONTROL Delivery log qualification]** non si applica al connettore **SMPP** generico esteso.

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
   <td> Errore durante l'invio del messaggio MT<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Errore durante l'invio dei messaggi<br /> </td> 
   <td> Morbido<br /> </td> 
   <td> Non raggiungibile<br /> </td> 
  </tr> 
 </tbody> 
</table>

**Per il connettore SMPP generico esteso**

Quando si utilizza il protocollo SMPP per inviare messaggi SMS, la gestione degli errori viene gestita in modo diverso. Per ulteriori informazioni sul connettore SMPP generico esteso, consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

Il connettore SMPP recupera i dati dal messaggio SR (Status Report) restituito utilizzando espressioni regolari (regex) per filtrarne il contenuto. Questi dati vengono quindi confrontati con le informazioni presenti nella tabella **[!UICONTROL Delivery log qualification]** (disponibile tramite il menu **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]**).

Prima che venga qualificato un nuovo tipo di errore, il motivo dell&#39;errore è sempre impostato su **Rifiutato** per impostazione predefinita.

>[!NOTE]
>
>I tipi di errore e i motivi dell’errore sono gli stessi delle e-mail. Vedi [Tipi e motivi di errori di consegna](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>Chiedi al provider un elenco di stati e codici di errore per impostare i tipi di errore e i motivi dell’errore nella tabella Qualificazione del registro di consegna.

Esempio di messaggio generato:

```
SR Generic DELIVRD 000|#MESSAGE#
```

* Tutti i messaggi di errore iniziano con **SR** per distinguere i codici di errore SMS dai codici di errore e-mail.
* La seconda parte (**Generic** in questo esempio) del messaggio di errore fa riferimento al nome dell&#39;implementazione SMSC, come definito nel campo **[!UICONTROL SMSC implementation name]** dell&#39;account esterno SMS. Consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

  Poiché lo stesso codice di errore può avere un significato diverso per ogni provider, questo campo consente di sapere quale provider ha generato il codice di errore. L’errore è quindi disponibile nella documentazione del provider pertinente.

* La terza parte (**DELIVRD** in questo esempio) del messaggio di errore corrisponde al codice di stato recuperato dall&#39;SR utilizzando il regex di estrazione dello stato definito nell&#39;account esterno SMS.

  Regex specificato nella scheda **[!UICONTROL SMSC specificities]** dell&#39;account esterno. Consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

  ![](assets/tech_quarant_error_regex.png)

  Per impostazione predefinita, regex estrae il campo **stat:** come definito dalla sezione **Appendice B** della specifica **SMPP 3.4**.

* La quarta parte (**000** in questo esempio) del messaggio di errore corrisponde al codice di errore estratto dall&#39;SR utilizzando il codice di errore regex definito nell&#39;account esterno SMS.

  Regex specificato nella scheda **[!UICONTROL SMSC specificities]** dell&#39;account esterno. Consulta [questa pagina](sms-set-up.md#creating-an-smpp-external-account).

  Per impostazione predefinita, il regex estrae il campo **err:** come definito dalla sezione **Appendice B** della specifica **SMPP 3.4**.

* Tutto ciò che segue il simbolo di barra verticale (|) viene visualizzato solo nella colonna **[!UICONTROL First text]** della tabella **[!UICONTROL Delivery log qualification]**. Questo contenuto viene sempre sostituito da **#MESSAGE#** dopo la normalizzazione del messaggio. Questo processo evita di inserire più voci per errori simili ed è lo stesso delle e-mail. Per ulteriori informazioni, consulta [Qualificazione di mail non recapitate](understanding-delivery-failures.md#bounce-mail-qualification).

Il connettore SMPP generico esteso applica un criterio euristico per trovare valori predefiniti sensibili: se lo stato inizia con **DELIV**, viene considerato un completamento perché corrisponde agli stati comuni **DELIVRD** o **DELIVERED** utilizzati dalla maggior parte dei provider. Qualsiasi altro stato comporta un errore grave.
