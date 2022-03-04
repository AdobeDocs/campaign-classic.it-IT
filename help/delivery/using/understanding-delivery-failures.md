---
product: campaign
title: Errori di consegna
description: Scopri come comprendere gli errori di consegna
feature: Monitoring, Deliverability
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '2614'
ht-degree: 14%

---

# Errori di consegna{#understanding-delivery-failures}

![](../../assets/common.svg)

## Informazioni sugli errori di consegna {#about-delivery-failures}

Quando un messaggio (e-mail, SMS, notifica push) non può essere inviato a un profilo, il server remoto invia automaticamente un messaggio di errore, rilevato dalla piattaforma Adobe Campaign e qualificato per determinare se l’indirizzo e-mail o il numero di telefono devono essere messi in quarantena o meno. Vedi [Gestione della posta non recapitata](#bounce-mail-management).

>[!NOTE]
>
>I messaggi di errore **E-mail** (o &quot;mancati recapiti&quot;) sono qualificati dall’MTA avanzato (mancati recapiti sincroni) o dal processo inMail (mancati recapiti asincroni).
>
>I messaggi di errore **SMS** (o &quot;SR&quot; per &quot;Report di stato&quot;) sono qualificati dal processo MTA.

Una volta inviato un messaggio, i registri di consegna ti consentono di visualizzare lo stato di consegna per ciascun profilo e il tipo e il motivo dell’errore associati.

I messaggi possono essere esclusi anche durante la preparazione della consegna se un indirizzo viene messo in quarantena o se un profilo è in elenco Bloccati. I messaggi esclusi sono elencati nel dashboard di consegna.

**Argomenti correlati:**

* [Log di consegna e cronologia](delivery-dashboard.md#delivery-logs-and-history)
* [Stato non riuscito](delivery-performances.md#failed-status)
* [Tipi e motivi di errori di consegna](#delivery-failure-types-and-reasons)

## Tipi e motivi di errori di consegna {#delivery-failure-types-and-reasons}

Quando un messaggio non riesce, si possono verificare tre tipi di errore. Ogni tipo di errore determina se un indirizzo viene inviato alla quarantena. Per ulteriori informazioni, consulta [Condizioni per la messa in quarantena di un indirizzo](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

* **Rigido**: un errore &quot;rigido&quot; indica un indirizzo non valido. Ciò comporta un messaggio di errore che indica esplicitamente che l’indirizzo non è valido, ad esempio: &quot;Utente sconosciuto&quot;.
* **Morbido**: potrebbe trattarsi di un errore temporaneo o di un errore che non è stato possibile classificare, ad esempio: &quot;Dominio non valido&quot; o &quot;Casella in entrata piena&quot;.
* **Ignorato**: si tratta di un errore che è noto come temporaneo, ad esempio &quot;Fuori sede&quot;, o di un errore tecnico, ad esempio se il tipo di mittente è &quot;postmaster&quot;.

I possibili motivi di un errore di consegna sono:

<table> 
 <tbody> 
  <tr> 
   <td> Etichetta errore </td> 
   <td> Tipo di errore </td> 
   <td> Valore tecnico </td> 
   <td> Descrizione </td> 
  </tr> 
  <tr> 
   <td> Account disabilitato </td> 
   <td> Morbido/Duro </td> 
   <td> 4 </td> 
   <td> L'account collegato all'indirizzo non è più attivo. Quando il provider di accesso a Internet (IAP) rileva un periodo prolungato di inattività, può chiudere l'account dell'utente. Le consegne all’indirizzo dell’utente saranno quindi impossibili. Se l’account è temporaneamente disattivato a causa di sei mesi di inattività e può ancora essere attivato, verrà assegnato lo stato Con errori e l’account verrà ritentato finché il contatore degli errori non raggiunge 5. Se l’errore segnala che l’account è disattivato in modo permanente, viene impostato direttamente su Quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo in quarantena </td> 
   <td> Duro </td> 
   <td> 9 </td> 
   <td> L'indirizzo è stato messo in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo non specificato </td> 
   <td> Duro </td> 
   <td> 7 </td> 
   <td> Il destinatario non riceve alcun indirizzo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo di cattiva qualità </td> 
   <td> Ignorato </td> 
   <td> 14 </td> 
   <td> Il punteggio di qualità per questo indirizzo è troppo basso.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo Inserita nell'elenco Bloccati </td> 
   <td> Duro </td> 
   <td> 8 </td> 
   <td> L’indirizzo è stato aggiunto al elenco Bloccati al momento dell’invio. Questo stato viene utilizzato per importare dati da elenchi esterni e sistemi esterni nell’elenco quarantena di Adobe Campaign.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo di controllo </td> 
   <td> Ignorato </td> 
   <td> 127 </td> 
   <td> L'indirizzo del destinatario fa parte del gruppo di controllo.<br /> </td> 
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
   <td> L'indirizzo è sull'inserire nell'elenco Consentiti. L’errore viene quindi ignorato e viene inviato un messaggio e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> Escluso dopo arbitrato </td> 
   <td> Ignorato </td> 
   <td> 12 </td> 
   <td> Il destinatario è stato escluso da una regola di tipologia della campagna di tipo "arbitrale".<br /> </td> 
  </tr> 
  <tr> 
   <td> Escluso da una regola SQL </td> 
   <td> Ignorato </td> 
   <td> 11 </td> 
   <td> Il destinatario è stato escluso da una regola di tipologia della campagna di tipo SQL.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio non valido </td> 
   <td> Morbido </td> 
   <td> 2 </td> 
   <td> Il dominio dell'indirizzo e-mail non è corretto o non esiste più. Questo profilo sarà nuovamente oggetto di targeting fino a raggiungere 5 errori. Successivamente, il record verrà impostato sullo stato di quarantena e non verrà eseguito alcun nuovo tentativo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Cassetta postale piena </td> 
   <td> Morbido </td> 
   <td> 5 </td> 
   <td> La cassetta postale di questo utente è piena e non può accettare altri messaggi. Questo profilo sarà nuovamente oggetto di targeting fino a raggiungere 5 errori. Successivamente, il record verrà impostato sullo stato di quarantena e non verrà eseguito alcun nuovo tentativo.<br /> Questo tipo di errore viene gestito da un processo di pulizia, l’indirizzo viene impostato su uno stato valido dopo 30 giorni.<br /> Avviso: per rimuovere automaticamente l’indirizzo dall’elenco degli indirizzi in quarantena, è necessario avviare il flusso di lavoro tecnico Database cleanup .<br /> </td> 
  </tr> 
  <tr> 
   <td> Non connesso </td> 
   <td> Ignorato </td> 
   <td> 6 </td> 
   <td> Il telefono cellulare del destinatario è spento o non è connesso alla rete quando il messaggio viene inviato.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non definito </td> 
   <td> Non definito </td> 
   <td> 0 </td> 
   <td> L’indirizzo è in qualificazione perché l’errore non è ancora stato incrementato. Questo tipo di errore si verifica quando un nuovo messaggio di errore viene inviato dal server: può essere un errore isolato, ma se si verifica di nuovo, il contatore degli errori aumenta, avvisando i team tecnici. Possono quindi eseguire un'analisi dei messaggi e qualificare questo errore tramite il <span class="uicontrol">Amministrazione</span> / <span class="uicontrol">Gestione delle campagne</span> / <span class="uicontrol">Gestione non consegnabili</span> nella struttura ad albero.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non ammissibile alle offerte </td> 
   <td> Ignorato </td> 
   <td> 16 </td> 
   <td> Il destinatario non era idoneo per le offerte nella consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiutato </td> 
   <td> Morbido/Duro </td> 
   <td> 20 </td> 
   <td> L’indirizzo è stato messo in quarantena a causa di un feedback di sicurezza come un rapporto spam. In base all’errore, l’indirizzo verrà ritentato finché il contatore degli errori non raggiunge 5, o verrà inviato direttamente alle quarantene.<br /> </td> 
  </tr> 
  <tr> 
   <td> Target con dimensioni limitate </td> 
   <td> Ignorato </td> 
   <td> 17 </td> 
   <td> La dimensione massima di consegna è stata raggiunta per il destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo non qualificato </td> 
   <td> Ignorato </td> 
   <td> 15 </td> 
   <td> L'indirizzo postale non è stato qualificato.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non raggiungibile </td> 
   <td> Morbido/Duro </td> 
   <td> 3 </td> 
   <td> Errore nella catena di consegna dei messaggi. Potrebbe essere un problema sul relay SMTP, un dominio temporaneamente irraggiungibile, ecc. In base all’errore, l’indirizzo verrà ritentato finché il contatore degli errori non raggiunge 5, o verrà inviato direttamente alle quarantene.<br /> </td> 
  </tr> 
  <tr> 
   <td> Utente sconosciuto </td> 
   <td> Duro </td> 
   <td> 1 </td> 
   <td> L'indirizzo non esiste. Per questo profilo non verranno tentate ulteriori consegne.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tentativi dopo un errore temporaneo di consegna {#retries-after-a-delivery-temporary-failure}

Se un messaggio non riesce a causa di un errore **Morbido** o **Ignorato** Se si tratta di un errore temporaneo, verranno eseguiti nuovi tentativi durante la durata della consegna.

>[!NOTE]
>
>I messaggi temporaneamente non consegnati possono essere correlati solo a un **Morbido** o **Ignorato** errore, ma non un errore **Duro** error (vedi [Tipi e motivi di errori di consegna](#delivery-failure-types-and-reasons)).

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), le impostazioni relative ai nuovi tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito e il periodo di tempo che li separa sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte non recapitate provenienti dal dominio e-mail del messaggio.

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign, per modificare la durata di una consegna, passa ai parametri avanzati della consegna o del modello di consegna e specifica la durata desiderata nel campo corrispondente. Vedi [Definizione del periodo di validità](steps-sending-the-delivery.md#defining-validity-period).

La configurazione predefinita consente cinque tentativi a intervalli di un’ora, seguiti da un nuovo tentativo al giorno per quattro giorni. Il numero di tentativi può essere modificato a livello globale (contatta l’amministratore tecnico di Adobe) o per ogni consegna o modello di consegna. Vedi [Configura nuovi tentativi](steps-sending-the-delivery.md#configuring-retries).

## Errori sincroni e asincroni {#synchronous-and-asynchronous-errors}

Un messaggio può non riuscire immediatamente (errore sincrono) o in seguito, dopo che è stato inviato (errore asincrono).

* Errore sincrono: il server di posta remota contattato dal server di consegna Adobe Campaign ha restituito immediatamente un messaggio di errore. la consegna non può essere inviata al server del profilo. Adobe Campaign qualifica ogni errore per determinare se gli indirizzi e-mail in questione devono essere messi in quarantena o meno. Consulta [Qualificazione di mail non recapitate](#bounce-mail-qualification).
* Errore asincrono: una mail non recapitata o un SR è stato inviato in seguito dal server ricevente. Questa posta viene caricata in una cassetta postale tecnica utilizzata dall&#39;applicazione per etichettare i messaggi con un errore. Gli errori asincroni possono verificarsi fino a una settimana dopo l’invio di una consegna.

   >[!NOTE]
   >
   >La configurazione della cassetta postale non recapitata è dettagliata in [questa sezione](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

   La [circuito di retroazione](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops) funziona come e-mail non recapitate. Quando un utente qualifica un’e-mail come posta indesiderata, puoi configurare le regole e-mail in Adobe Campaign per bloccare tutte le consegne a questo utente. I messaggi inviati agli utenti che hanno qualificato un’e-mail come spam vengono automaticamente reindirizzati verso una casella e-mail appositamente creata a questo scopo. Gli indirizzi di questi utenti sono in elenco Bloccati anche se non hanno fatto clic sul collegamento di annullamento dell’abbonamento. Gli indirizzi sono in elenco Bloccati nel (**NmsAddress**) tabella di quarantena e non in (**NmsRecipient**) tabella dei destinatari.

   >[!NOTE]
   >
   >La gestione dei reclami è descritta nel [Gestione del recapito messaggi](about-deliverability.md) sezione .

## Gestione della posta non recapitata {#bounce-mail-management}

La piattaforma Adobe Campaign consente di gestire gli errori di consegna delle e-mail tramite la funzionalità mail non recapitata.

Quando un messaggio e-mail non può essere recapitato a un destinatario, il server di messaggistica remota restituisce automaticamente un messaggio di errore (messaggio non recapitato) a una casella in entrata tecnica progettata a tal fine.

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign, i messaggi di errore vengono raccolti dalla piattaforma Adobe Campaign e qualificati dal processo inMail per arricchire l’elenco delle regole di gestione delle e-mail.

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), la maggior parte delle regole di gestione delle e-mail non viene più utilizzata. Per ulteriori informazioni, consulta [questa sezione](#email-management-rules).

### Qualificazione di mail non recapitate {#bounce-mail-qualification}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md):
>
>* Le qualifiche non recapitate nel **[!UICONTROL Delivery log qualification]** tabella non più utilizzata per **sincrono** messaggi di errore di consegna. L’MTA avanzato determina il tipo di messaggio non recapitato e la relativa qualifica e invia nuovamente tali informazioni a Campaign.
>
>* **** Le mancate consegne asincrone vengono comunque qualificate dal processo inMail attraverso le regole **[!UICONTROL Inbound email]**. Per ulteriori informazioni, consulta [Regole di gestione e-mail](#email-management-rules).
>
>* Per le istanze che utilizzano l’MTA avanzato **senza Webhook/EFS**, **[!UICONTROL Inbound email]** Le regole verranno inoltre utilizzate per elaborare le e-mail non recapitate sincrone provenienti dall’MTA avanzato, utilizzando lo stesso indirizzo e-mail delle e-mail non recapitate asincrone.


Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign, quando la consegna di un’e-mail non riesce, il server di consegna Adobe Campaign riceve un messaggio di errore dal server di messaggistica o dal server DNS remoto. L&#39;elenco degli errori è costituito da stringhe contenute nel messaggio restituito dal server remoto. I tipi e i motivi di errore vengono assegnati a ogni messaggio di errore.

Questo elenco è disponibile tramite **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** nodo. Contiene tutte le regole utilizzate da Adobe Campaign per qualificare gli errori di consegna. Non è esaustivo, viene aggiornato regolarmente da Adobe Campaign e può essere gestito anche dall’utente.

![](assets/tech_quarant_rules_qualif.png)

Il messaggio restituito dal server remoto sulla prima occorrenza di questo tipo di errore viene visualizzato nella **[!UICONTROL First text]** della colonna **[!UICONTROL Delivery log qualification]** tabella. Se questa colonna non è visualizzata, fai clic sul pulsante **[!UICONTROL Configure list]** nella parte inferiore destra dell’elenco per selezionarlo.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtra questo messaggio per eliminare il contenuto della variabile (come ID, date, indirizzi e-mail, numeri di telefono, ecc.) e visualizza il risultato filtrato nel **[!UICONTROL Text]** colonna. Le variabili vengono sostituite con **`#xxx#`**, ad eccezione degli indirizzi sostituiti con **`*`**.

Questo processo consente di raggruppare tutti gli errori dello stesso tipo ed evitare più voci per errori simili nella tabella di qualificazione del registro di consegna.

>[!NOTE]
>
>La **[!UICONTROL Number of occurrences]** visualizza il numero di occorrenze del messaggio nell’elenco. È limitato a 100.000 occorrenze. È possibile modificare il campo se, ad esempio, si desidera ripristinarlo.

Le mail non recapitate possono avere il seguente stato di qualifica:

* **[!UICONTROL To qualify]** : impossibile qualificare la posta non recapitata. La qualifica deve essere assegnata al team di recapito messaggi per garantire un recapito efficiente della piattaforma. Se non è qualificato, la mail non recapitata non viene utilizzata per arricchire l’elenco delle regole di gestione delle e-mail.
* **[!UICONTROL Keep]** : la mail non recapitata è stata qualificata e verrà utilizzata dal **Aggiornamento per il recapito messaggi** da confrontare con le regole di gestione e-mail esistenti e arricchire l’elenco.
* **[!UICONTROL Ignore]** : la mail non recapitata viene ignorata dall’MTA di Campaign, il che significa che questo messaggio non causerà mai la quarantena dell’indirizzo del destinatario. Non verrà utilizzato dal **Aggiornamento per il recapito messaggi** e non verrà inviato alle istanze client.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>In caso di interruzione di un ISP, le e-mail inviate tramite Campaign verranno erroneamente contrassegnate come mancate consegne. Per correggere questo problema, è necessario aggiornare la qualifica di mancato recapito. Per ulteriori informazioni, consulta [questa pagina](update-bounce-qualification.md).

### Regole di gestione e-mail {#email-management-rules}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), la maggior parte delle regole di gestione delle e-mail non viene più utilizzata. Per ulteriori dettagli, consulta le sezioni seguenti.

Le regole della posta sono accessibili tramite **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nodo. Le regole di gestione e-mail vengono visualizzate nella parte inferiore della finestra.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>I parametri predefiniti della piattaforma sono configurati nella procedura guidata di distribuzione. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/deploying-an-instance.md).

Le regole predefinite sono le seguenti.

>[!IMPORTANT]
>
>* Se i parametri sono stati modificati, è necessario riavviare il server di consegna (MTA).
>* La modifica o la creazione di regole di gestione è riservata esclusivamente agli utenti esperti.


#### E-mail in entrata {#inbound-email}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md)e se la tua istanza ha **Webhook/EFS** la funzionalità **[!UICONTROL Inbound email]** le regole non vengono più utilizzate per i messaggi di errore di consegna sincroni. Per ulteriori informazioni, consulta [questa sezione](#bounce-mail-qualification).

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign, queste regole contengono l’elenco di stringhe di caratteri che possono essere restituite dai server remoti e che consentono di qualificare l’errore (**Duro**, **Morbido** o **Ignorato**).

Quando un’e-mail non riesce, il server remoto restituisce un messaggio non recapitato all’indirizzo specificato nei parametri della piattaforma. Adobe Campaign confronta il contenuto di ogni messaggio non recapitato alle stringhe nell’elenco delle regole, quindi lo assegna a una delle tre [tipi di errore](#delivery-failure-types-and-reasons).

>[!NOTE]
>
>L’utente può creare le proprie regole. Durante l’importazione di un pacchetto e durante l’aggiornamento dei dati tramite **Aggiornamento per il recapito messaggi** le regole create dall’utente vengono sovrascritte.

Per ulteriori informazioni sulla qualifica della posta non recapitata, consulta [questa sezione](#bounce-mail-qualification).

#### Gestione del dominio {#domain-management}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), **[!UICONTROL Domain management]** le regole non vengono più utilizzate. La firma di autenticazione dell’e-mail **DKIM (DomainKeys Identified Mail)** viene eseguita dall’MTA avanzato per tutti i messaggi di tutti i domini. La firma non viene eseguita con **ID mittente**, **DomainKeys** o **S/MIME**, a meno che non venga specificato diversamente a livello di MTA avanzato.

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign, il server di messaggistica Adobe Campaign applica un singolo **Gestione del dominio** a tutti i domini.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* È possibile scegliere se attivare o meno determinati standard di identificazione e chiavi di crittografia per controllare il nome di dominio, ad esempio **ID mittente**, **DomainKeys**, **DKIM** e **S/MIME**.
* La **relè SMTP** I parametri ti consentono di configurare l’indirizzo IP e la porta di un server relay per un determinato dominio. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#smtp-relay).

Se i messaggi vengono visualizzati in Outlook con **[!UICONTROL on behalf of]** nell’indirizzo del mittente, assicurati di non firmare le e-mail con **ID mittente**, che è lo standard di autenticazione e-mail proprietario obsoleto di Microsoft. Se la **[!UICONTROL Sender ID]** è abilitata, deseleziona la casella corrispondente e contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Il recapito messaggi non sarà interessato.

#### Gestione MX {#mx-management}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), **[!UICONTROL MX management]** le regole di velocità effettiva di consegna non vengono più utilizzate. L’MTA avanzato utilizza le proprie regole MX che gli consentono di personalizzare il throughput in base al dominio in base alla reputazione cronologica dell’e-mail e al feedback in tempo reale proveniente dai domini in cui invii e-mail.

Per le installazioni on-premise e le installazioni in hosting/ibride utilizzando l’MTA legacy di Campaign:

* Le regole di gestione MX vengono utilizzate per regolare il flusso di e-mail in uscita per un dominio specifico. Campione dei messaggi non recapitati e blocco dell’invio, se necessario.

* Il server di messaggistica Adobe Campaign applica regole specifiche ai domini e quindi le regole per il caso generale rappresentato da un asterisco nell&#39;elenco delle regole.

* Per configurare le regole di gestione MX, è sufficiente impostare una soglia e selezionare alcuni parametri SMTP. A **soglia** è un limite calcolato come percentuale di errore oltre la quale vengono bloccati tutti i messaggi verso un dominio specifico. Ad esempio, nel caso generale, per un minimo di 300 messaggi, l’invio di e-mail viene bloccato per tre ore se il tasso di errore raggiunge il 90%.

Per ulteriori informazioni sulla gestione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).
