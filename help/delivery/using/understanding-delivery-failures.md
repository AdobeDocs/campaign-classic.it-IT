---
title: Informazioni sugli errori di consegna
seo-title: Informazioni sugli errori di consegna
description: Informazioni sugli errori di consegna
seo-description: null
page-status-flag: never-activated
uuid: 03a91f84-77fe-40a9-8be9-a6a35a873ae1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 78b58a7a-b387-4d5d-80d5-01c06f83d759
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0932d0836c53b8dea715f471f9319603140c9950

---


# Informazioni sugli errori di consegna{#understanding-delivery-failures}

## Informazioni sugli errori di consegna {#about-delivery-failures}

Quando un messaggio (e-mail, SMS, notifica push) non può essere inviato a un profilo, il server remoto invia automaticamente un messaggio di errore, prelevato dalla piattaforma Adobe Campaign e qualificato per determinare se l&#39;indirizzo e-mail o il numero di telefono devono essere posti in quarantena o meno. Consultate Gestione [della posta](#bounce-mail-management)rimbalzata.

>[!NOTE]
>
>I messaggi di errore e-mail (o &quot;rimbalzi&quot;) sono qualificati dal processo inMail. I messaggi di errore SMS (o &quot;SR&quot; per &quot;Report di stato&quot;) sono qualificati dal processo MTA.

Una volta inviato il messaggio, i registri di consegna consentono di visualizzare lo stato di consegna per ciascun profilo e il tipo e il motivo di errore associati.

I messaggi possono essere esclusi durante la preparazione del recapito se un indirizzo viene messo in quarantena o se un profilo viene inserito in una blacklist. I messaggi esclusi sono elencati nel dashboard di distribuzione.

**Argomenti correlati:**

* [Registri di consegna e cronologia](../../delivery/using/monitoring-a-delivery.md#delivery-logs-and-history)
* [Stato non riuscito](../../delivery/using/monitoring-a-delivery.md#failed-status)
* [Tipi e motivi di mancata consegna](#delivery-failure-types-and-reasons)

## Tipi e motivi di mancata consegna {#delivery-failure-types-and-reasons}

Esistono tre tipi di errore quando un messaggio non riesce. Ogni tipo di errore determina se un indirizzo viene inviato alle quarantena. Per ulteriori informazioni, vedere [Condizioni per l&#39;invio di un indirizzo alla quarantena](../../delivery/using/understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Duro**: Un errore &quot;hard&quot; indica un indirizzo non valido. Ciò comporta un messaggio di errore che indica esplicitamente che l&#39;indirizzo non è valido, ad esempio: &quot;Utente sconosciuto&quot;.
* **Morbido**: Potrebbe trattarsi di un errore temporaneo o di un errore che non è stato possibile classificare, ad esempio: &quot;Dominio non valido&quot; o &quot;Cassetta postale completa&quot;.
* **Ignorato**: Si tratta di un errore che è noto come temporaneo, ad esempio &quot;Fuori sede&quot; o un errore tecnico, ad esempio se il tipo di mittente è &quot;postmaster&quot;.

I possibili motivi di un mancato recapito sono:

<table> 
 <tbody> 
  <tr> 
   <td> Etichetta errore </td> 
   <td> Tipo errore </td> 
   <td> Valore tecnico </td> 
   <td> Descrizione </td> 
  </tr> 
  <tr> 
   <td> Account disattivato </td> 
   <td> Soft/Hard </td> 
   <td> 4 </td> 
   <td> L'account collegato all'indirizzo non è più attivo. Quando Internet Access Provider (IAP) rileva un lungo periodo di inattività, può chiudere l'account dell'utente. Le consegne all'indirizzo dell'utente saranno quindi impossibili. Se l'account è temporaneamente disattivato a causa di sei mesi di inattività e può essere ancora attivato, lo stato Con errori verrà assegnato e l'account verrà riprovato fino a quando il contatore di errori non raggiunge 5. Se l'errore segnala che l'account è disattivato in modo permanente, verrà impostato direttamente su Quarantine.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo in quarantena </td> 
   <td> Rigido </td> 
   <td> 9 </td> 
   <td> L'indirizzo è stato messo in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo non specificato </td> 
   <td> Rigido </td> 
   <td> 7 </td> 
   <td> Nessun indirizzo specificato per il destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo di qualità non valida </td> 
   <td> Ignorato </td> 
   <td> 14 </td> 
   <td> Il valore di qualità per questo indirizzo è troppo basso.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo Blacklist </td> 
   <td> Rigido </td> 
   <td> 8 </td> 
   <td> L'indirizzo è stato inserito in una blacklist al momento dell'invio. Questo stato viene utilizzato per importare dati da elenchi esterni e sistemi esterni durante l'importazione di dati nell'elenco quarantena di Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo di controllo </td> 
   <td> Ignorato </td> 
   <td> 127 </td> 
   <td> L'indirizzo del destinatario è parte del gruppo di controllo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Doppio </td> 
   <td> Ignorato </td> 
   <td> 10 </td> 
   <td> L'indirizzo del destinatario era già in questa consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Errore ignorato </td> 
   <td> Ignorato </td> 
   <td> 25 </td> 
   <td> L'indirizzo è inserito nella white list. L’errore viene quindi ignorato e viene inviato un messaggio e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> Escluso dopo l'arbitrato </td> 
   <td> Ignorato </td> 
   <td> 12 </td> 
   <td> Il destinatario è stato escluso da una regola di tipologia della campagna di 'arbitrato'.<br /> </td> 
  </tr> 
  <tr> 
   <td> Escluso da una regola SQL </td> 
   <td> Ignorato </td> 
   <td> 11 </td> 
   <td> Il destinatario è stato escluso da una regola di tipo campagna 'SQL'.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio non valido </td> 
   <td> Morbido </td> 
   <td> 2 </td> 
   <td> Il dominio dell'indirizzo e-mail non è corretto o non esiste più. Questo profilo verrà nuovamente eseguito il targeting fino a raggiungere 5. Successivamente, il record verrà impostato sullo stato Quarantine e non verrà seguito alcun nuovo tentativo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Cassetta postale completa </td> 
   <td> Morbido </td> 
   <td> 5 </td> 
   <td> La cassetta postale di questo utente è piena e non può accettare altri messaggi. Questo profilo verrà nuovamente eseguito il targeting fino a raggiungere 5. Successivamente, il record verrà impostato sullo stato Quarantine e non verrà seguito alcun nuovo tentativo.<br /> Questo tipo di errore viene gestito da un processo di pulizia. L'indirizzo viene impostato su uno stato valido dopo 30 giorni.<br /> Avviso: per rimuovere automaticamente l'indirizzo dall'elenco degli indirizzi in quarantena, è necessario avviare il flusso di lavoro tecnico di pulizia del database.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non connesso </td> 
   <td> Ignorato </td> 
   <td> 6 </td> 
   <td> Il telefono cellulare del destinatario viene spento o non è connesso alla rete quando il messaggio viene inviato.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non definito </td> 
   <td> Non definito </td> 
   <td> 0 </td> 
   <td> L'indirizzo è nella qualifica perché l'errore non è ancora stato incrementato. Questo tipo di errore si verifica quando un nuovo messaggio di errore viene inviato dal server: può essere un errore isolato, ma se si verifica di nuovo, il contatore di errori aumenta, che avviserà i team tecnici. Possono quindi eseguire l'analisi dei messaggi e individuare l'errore tramite il nodo <span class="uicontrol">Amministrazione</span> /Gestione <span class="uicontrol"></span> campagne/Gestione <span class="uicontrol"></span> non risultati finali nella struttura ad albero.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non ammissibile alle offerte </td> 
   <td> Ignorato </td> 
   <td> 16 </td> 
   <td> Il destinatario non era idoneo per le offerte nella consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiutato </td> 
   <td> Soft/Hard </td> 
   <td> 20 </td> 
   <td> L'indirizzo è stato messo in quarantena a causa di un feedback sulla sicurezza come rapporto di spam. In base all'errore, l'indirizzo verrà riprovato fino a quando il contatore di errori raggiunge 5, o verrà inviato direttamente alle quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Target con dimensioni limitate </td> 
   <td> Ignorato </td> 
   <td> 17 </td> 
   <td> È stata raggiunta la dimensione massima di consegna per il destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo non qualificato </td> 
   <td> Ignorato </td> 
   <td> 15 </td> 
   <td> L'indirizzo postale non è qualificato.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non Raggiungibile </td> 
   <td> Soft/Hard </td> 
   <td> 3 </td> 
   <td> Si è verificato un errore nella catena di distribuzione dei messaggi. Potrebbe essere un incidente sul relè SMTP, un dominio temporaneamente irraggiungibile, ecc. In base all'errore, l'indirizzo verrà riprovato fino a quando il contatore di errori raggiunge 5, o verrà inviato direttamente alle quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Utente sconosciuto </td> 
   <td> Rigido </td> 
   <td> 1 </td> 
   <td> L'indirizzo non esiste. Per questo profilo non verranno tentate altre consegne.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tentativi dopo un errore temporaneo di consegna {#retries-after-a-delivery-temporary-failure}

Se un messaggio non riesce a causa di un errore **soft** o **Ignorato** temporaneo, i tentativi verranno eseguiti durante la durata del recapito.

>[!NOTE]
>
>I messaggi temporaneamente non inviati possono essere correlati solo a un errore **soft** o **Ignorato** , ma non a un errore **hard** (vedere Tipi di errore [di consegna e motivi](#delivery-failure-types-and-reasons)).

Per modificare la durata di una consegna, passate ai parametri avanzati del modello di consegna o consegna e specificate la durata desiderata nel campo corrispondente. Le proprietà di consegna avanzate sono presentate in [questa sezione](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period).

La configurazione predefinita consente cinque tentativi a intervalli di un&#39;ora, seguiti da un nuovo tentativo al giorno per quattro giorni. Il numero di tentativi può essere modificato a livello globale (rivolgetevi al vostro amministratore tecnico Adobe) o per ogni modello di consegna o consegna (consultate [questa sezione](../../delivery/using/steps-sending-the-delivery.md#configuring-retries)).

## Errori sincroni e asincroni {#synchronous-and-asynchronous-errors}

Un messaggio può non riuscire immediatamente (errore sincrono), o successivamente, dopo che è stato inviato (errore asincrono).

* Errore sincrono: il server di posta elettronica remoto contattato dal server di consegna di Adobe Campaign ha immediatamente restituito un messaggio di errore. La consegna non è consentita al server del profilo. Adobe Campaign qualifica ogni errore per determinare se gli indirizzi e-mail in questione devono essere posti in quarantena o meno. Consultate Qualificazione [della posta](#bounce-mail-qualification)Bounce.
* Errore asincrono: un messaggio di rimbalzo o un SR veniva inviato successivamente dal server ricevente. Questo messaggio viene caricato in una cassetta postale tecnica utilizzata dall&#39;applicazione per etichettare i messaggi con un errore. Gli errori asincroni possono verificarsi fino a una settimana dopo l&#39;invio di una consegna.

   >[!NOTE]
   >
   >La configurazione della cassetta postale di rimbalzo è dettagliata in [questa sezione](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

   Il ciclo di feedback funziona come un messaggio e-mail di rimbalzo. Quando un utente qualifica un&#39;e-mail come spam, puoi configurare le regole e-mail in Adobe Campaign per bloccare tutte le consegne a questo utente. I messaggi inviati agli utenti che hanno qualificato un&#39;e-mail come spam vengono automaticamente reindirizzati verso una casella e-mail creata appositamente a tale scopo. Gli indirizzi di questi utenti vengono inseriti in blacklist anche se non hanno fatto clic sul collegamento di annullamento dell’iscrizione. Gli indirizzi sono inseriti in una blacklist nella tabella di quarantena (**NmsAddress**) e non nella tabella del destinatario (**NmsRecipient**).

   >[!NOTE]
   >
   >La gestione dei reclami è descritta in dettaglio nella sezione Gestione [](../../delivery/using/about-deliverability.md) dell&#39;offerta.

## Gestione della posta {#bounce-mail-management}

La piattaforma Adobe Campaign consente di gestire gli errori di distribuzione delle e-mail mediante la funzionalità e-mail di rimbalzo. Quando un&#39;e-mail non può essere inviata a un destinatario, il server di messaggistica remota restituisce automaticamente un messaggio di errore (messaggio di rimbalzo) a una inbox tecnica progettata a tal fine. I messaggi di errore vengono raccolti dalla piattaforma Adobe Campaign e qualificati dal processo inMail per arricchire l&#39;elenco delle regole di gestione delle e-mail

### Qualificazione della posta {#bounce-mail-qualification}

Quando la consegna di un&#39;e-mail non riesce, il server di consegna di Adobe Campaign riceve un messaggio di errore dal server di messaggistica o dal server DNS remoto. L&#39;elenco degli errori è costituito da stringhe contenute nel messaggio restituito dal server remoto. I tipi di errore e i motivi sono assegnati a ciascun messaggio di errore.

Questo elenco è disponibile tramite il **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** nodo. Contiene tutte le regole utilizzate da Adobe Campaign per qualificare gli errori di consegna. Non è esaustivo, viene aggiornato regolarmente da Adobe Campaign e può essere gestito anche dall&#39;utente.

![](assets/tech_quarant_rules_qualif.png)

* Il messaggio restituito dal server remoto sulla prima occorrenza di questo tipo di errore viene visualizzato nella **[!UICONTROL First text]** colonna della **[!UICONTROL Delivery log qualification]** tabella. Se la colonna non è visualizzata, fate clic sul **[!UICONTROL Configure list]** pulsante nella parte inferiore destra dell’elenco per selezionarla.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtra questo messaggio per eliminare il contenuto variabile (come ID, date, indirizzi e-mail, numeri di telefono, ecc.) e visualizza il risultato filtrato nella **[!UICONTROL Text]** colonna. Le variabili vengono sostituite con **`#xxx#`**, ad eccezione degli indirizzi sostituiti con **`*`**.

Questo processo consente di raggruppare tutti gli errori dello stesso tipo ed evitare più voci per errori simili nella tabella delle qualifiche del registro di consegna.

>[!NOTE]
>
>Il **[!UICONTROL Number of occurrences]** campo visualizza il numero di occorrenze del messaggio nell&#39;elenco. È limitato a 100 000 occorrenze. È possibile modificare il campo se, ad esempio, si desidera reimpostarlo.

I messaggi di rimbalzo possono avere il seguente stato di qualifica:

* **[!UICONTROL To qualify]** : impossibile qualificare il messaggio di rimbalzo. La qualifica deve essere assegnata al team di distribuzione per garantire una distribuzione efficiente della piattaforma. Finché non è qualificato, il messaggio di rimbalzo non viene utilizzato per arricchire l&#39;elenco delle regole di gestione delle e-mail.
* **[!UICONTROL Keep]** : il messaggio di rimbalzo è stato qualificato e verrà utilizzato dal flusso di lavoro **Aggiorna per la recapito** , da confrontare con le regole di gestione e-mail esistenti e arricchire l&#39;elenco.
* **[!UICONTROL Ignore]** : il messaggio di rimbalzo viene ignorato dall&#39;MTA della campagna, il che significa che questo messaggio di rimbalzo non causerà mai la quarantena dell&#39;indirizzo del destinatario. Non verrà utilizzato dal flusso di lavoro **Aggiorna per la recapito** e non verrà inviato alle istanze client.

![](assets/deliverability_qualif_status.png)

>[!IMPORTANT]
>
>Per le installazioni ospitate o ibride, se avete effettuato l’aggiornamento all’MTA avanzato:
>
>* I titoli di rimbalzo contenuti nella **[!UICONTROL Delivery log qualification]** tabella non vengono più utilizzati per i messaggi di errore di consegna sincrona. L&#39;MTA avanzata determina il tipo di rimbalzo e la qualifica e invia nuovamente tali informazioni a Campaign.
   >
   >
* I rimbalzi asincroni sono ancora qualificati dal processo inMail attraverso le **[!UICONTROL Inbound email]** regole. Per ulteriori informazioni, consultate Regole di gestione delle [e-mail](#email-management-rules).
   >
   >
* Per le istanze che utilizzano l&#39;MTA avanzata senza **Webhooks/EFS**, le **[!UICONTROL Inbound email]** regole saranno utilizzate anche per elaborare le e-mail di rimbalzo sincrone provenienti dall&#39;MTA avanzata, utilizzando lo stesso indirizzo e-mail come per le e-mail di rimbalzo asincrone.
>
>
Per ulteriori informazioni sull&#39;MTA avanzata di Adobe Campaign, consulta questo [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

### Regole di gestione e-mail {#email-management-rules}

Le regole della posta sono accessibili tramite il **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nodo. Le regole di gestione e-mail sono visualizzate nella parte inferiore della finestra.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>I parametri predefiniti della piattaforma sono configurati nella procedura guidata di distribuzione. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/deploying-an-instance.md).

Le regole predefinite sono le seguenti.

>[!IMPORTANT]
>
>* Se i parametri sono stati modificati, è necessario riavviare il server di consegna (MTA).
>* La modifica o la creazione di regole di gestione è riservata esclusivamente agli utenti esperti.


#### E-mail in ingresso {#inbound-email}

Queste regole contengono l&#39;elenco di stringhe di caratteri che possono essere restituite dai server remoti e che consentono di qualificare l&#39;errore (**Hard**, **Soft** o **Ignored**).

Quando un&#39;e-mail ha esito negativo, il server remoto restituisce un messaggio di rimbalzo all&#39;indirizzo specificato nei parametri della piattaforma. Adobe Campaign confronta il contenuto di ogni messaggio di rimbalzo con le stringhe nell&#39;elenco delle regole, quindi le assegna uno dei tre tipi [di](#delivery-failure-types-and-reasons)errore.

>[!NOTE]
>
>L&#39;utente può creare regole personalizzate. Quando importate un pacchetto e aggiornate i dati tramite il flusso di lavoro **Aggiorna per la recapito** , le regole create dall&#39;utente vengono sovrascritte.

Per ulteriori informazioni sulla qualifica della posta indesiderata, consulta [questa sezione](#bounce-mail-qualification).

>[!IMPORTANT]
>
>Per le installazioni ospitate o ibride, se avete effettuato l’aggiornamento all’MTA avanzato e se l’istanza dispone di funzionalità **Webhooks/EFS** , le **[!UICONTROL Inbound email]** regole non vengono più utilizzate per i messaggi di errore di consegna sincrona. Per ulteriori informazioni, consulta [questa sezione](#bounce-mail-qualification).
>
>Per ulteriori informazioni sull&#39;MTA avanzata di Adobe Campaign, consulta questo [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

#### Gestione del dominio {#domain-management}

Il server di messaggistica di Adobe Campaign applica una singola regola di gestione **del** dominio a tutti i domini.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* È possibile scegliere se attivare o meno determinati standard di identificazione e chiavi di crittografia per controllare il nome di dominio, ad esempio **Sender ID**, **DomainKeys**, **DKIM** e **S/MIME**.
* I parametri di inoltro **** SMTP consentono di configurare l&#39;indirizzo IP e la porta di un server di inoltro per un dominio specifico. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#smtp-relay).

Se i messaggi vengono visualizzati in Outlook con **[!UICONTROL on behalf of]** l&#39;indirizzo del mittente, assicurarsi di non firmare le e-mail con l&#39;ID **** mittente, che è lo standard obsoleto di autenticazione proprietaria delle e-mail di Microsoft. Se l&#39; **[!UICONTROL Sender ID]** opzione è abilitata, deseleziona la casella corrispondente e contatta il supporto di Adobe Campaign. La sua recapito non verrà influenzata.

>[!IMPORTANT]
>
>Per le installazioni ospitate o ibride, se avete effettuato l’aggiornamento all’MTA avanzato, le **[!UICONTROL Domain management]** regole non vengono più utilizzate. **La firma dell&#39;autenticazione dell&#39;e-mail DKIM (DomainKeys Identified Mail)** viene fatta dall&#39;MTA avanzata per tutti i messaggi con tutti i domini. Non firma con **Sender ID**, **DomainKeys** o **S/MIME** , a meno che non venga specificato diversamente a livello Enhanced MTA.
>
>Per ulteriori informazioni sull&#39;MTA avanzata di Adobe Campaign, consulta questo [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).

#### Gestione MX {#mx-management}

* Le regole di gestione MX vengono utilizzate per regolare il flusso di e-mail in uscita per un dominio specifico. Se necessario, vengono campionati i messaggi di rimbalzo e l’invio di blocchi.

* Il server di messaggistica di Adobe Campaign applica regole specifiche per i domini, quindi le regole per il caso generale rappresentate da un asterisco nell&#39;elenco delle regole.

* Per configurare le regole di gestione MX, è sufficiente impostare una soglia e selezionare alcuni parametri SMTP. Una **soglia** è un limite calcolato come percentuale di errore oltre il quale tutti i messaggi verso un dominio specifico vengono bloccati. Ad esempio, nel caso generale, per un minimo di 300 messaggi, l&#39;invio di e-mail viene bloccato per tre ore se il tasso di errore raggiunge il 90%.

For more on MX management, refer to [this section](../../installation/using/email-deliverability.md#mx-configuration).

>[!IMPORTANT]
>
>Per le installazioni ospitate o ibride, se avete effettuato l’aggiornamento all’MTA avanzato, le regole di **[!UICONTROL MX management]** consegna effettiva non vengono più utilizzate. L&#39;MTA avanzata utilizza le proprie regole MX che le consentono di personalizzare il throughput in base al dominio in base alla reputazione storica dell&#39;e-mail e al feedback in tempo reale proveniente dai domini in cui invii le e-mail.
>
>Per ulteriori informazioni sull&#39;MTA avanzata di Adobe Campaign, consulta questo [documento](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html).
