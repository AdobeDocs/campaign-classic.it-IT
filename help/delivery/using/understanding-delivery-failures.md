---
product: campaign
title: Errori di consegna
description: Scopri come comprendere gli errori di consegna
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring, Deliverability
role: User
exl-id: 86c7169a-2c71-4c43-8a1a-f39871b29856
source-git-commit: 8b0162680d6a3a2d4891d1f71020b44b28046ad7
workflow-type: tm+mt
source-wordcount: '2570'
ht-degree: 12%

---

# Errori di consegna{#understanding-delivery-failures}

## Informazioni sugli errori di consegna {#about-delivery-failures}

Quando un messaggio (e-mail, SMS, notifica push) non può essere inviato a un profilo, il server remoto invia automaticamente un messaggio di errore, raccolto dalla piattaforma Adobe Campaign e qualificato per determinare se l’indirizzo e-mail o il numero di telefono devono essere posti in quarantena o meno. Consulta [Gestione posta non recapitata](#bounce-mail-management).

>[!NOTE]
>
>I messaggi di errore **E-mail** (o &quot;mancati recapiti&quot;) sono qualificati dall’MTA avanzato (mancati recapiti sincroni) o dal processo inMail (mancati recapiti asincroni).
>
>I messaggi di errore **SMS** (o &quot;SR&quot; per &quot;Report di stato&quot;) sono qualificati dal processo MTA.

Dopo l’invio del messaggio, i registri di consegna ti consentono di visualizzare lo stato di consegna per ciascun profilo e il tipo e il motivo dell’errore associati.

I messaggi possono essere esclusi anche durante la preparazione della consegna se un indirizzo è messo in quarantena o se un profilo è in fase di inserisco nell&#39;elenco Bloccati. I messaggi esclusi sono elencati nel dashboard di consegna.

**Argomenti correlati:**

* [Registri e cronologia delle consegne](delivery-dashboard.md#delivery-logs-and-history)
* [Stato non riuscito](delivery-performances.md#failed-status)
* [Tipi e motivi di errori di consegna](#delivery-failure-types-and-reasons)

## Tipi e motivi di errori di consegna {#delivery-failure-types-and-reasons}

Quando un messaggio non riesce, sono disponibili tre tipi di errore. Ogni tipo di errore determina se un indirizzo viene inviato alle quarantene. Per ulteriori informazioni, consulta [Condizioni per la messa in quarantena di un indirizzo](understanding-quarantine-management.md#conditions-for-sending-an-address-to-quarantine)

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
   <td> Morbido/rigido </td> 
   <td> 4 </td> 
   <td> L’account collegato all’indirizzo non è più attivo. Quando il provider di accesso a Internet (IAP) rileva un periodo prolungato di inattività, può chiudere l'account dell'utente. Le consegne all’indirizzo dell’utente saranno quindi impossibili. Se l’account è temporaneamente disabilitato a causa di sei mesi di inattività e può ancora essere attivato, verrà assegnato lo stato Con errori e l’account verrà ritentato fino a quando il contatore degli errori non raggiunge 5. Se l’errore segnala che l’account è disattivato in modo permanente, verrà impostato direttamente su Quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo in quarantena </td> 
   <td> Rigido </td> 
   <td> 9 </td> 
   <td> L’indirizzo è stato messo in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo non specificato </td> 
   <td> Rigido </td> 
   <td> 7 </td> 
   <td> Nessun indirizzo specificato per il destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo di bassa qualità </td> 
   <td> Ignorato </td> 
   <td> 14 </td> 
   <td> La valutazione della qualità per questo indirizzo è troppo bassa.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo inserito nell’elenco bloccati </td> 
   <td> Rigido </td> 
   <td> 8 </td> 
   <td> L’indirizzo è stato aggiunto al inserisco nell'elenco Bloccati di invio della. Questo stato viene utilizzato per importare i dati da elenchi esterni e sistemi esterni nell’elenco di quarantena di Adobe Campaign.<br /> </td> 
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
   <td> L’indirizzo del destinatario era già in questa consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Errore ignorato </td> 
   <td> Ignorato </td> 
   <td> 25 </td> 
   <td> L'indirizzo si trova nel elenco Consentiti di. L’errore viene quindi ignorato e verrà inviata un’e-mail.<br /> </td> 
  </tr> 
  <tr> 
   <td> Escluso dopo arbitrato </td> 
   <td> Ignorato </td> 
   <td> 12 </td> 
   <td> Il destinatario è stato escluso da una regola di tipologia di campagna di tipo "arbitrato".<br /> </td> 
  </tr> 
  <tr> 
   <td> Escluso da una regola SQL </td> 
   <td> Ignorato </td> 
   <td> 11 </td> 
   <td> Il destinatario è stato escluso da una regola di tipologia di campagna di tipo 'SQL'.<br /> </td> 
  </tr> 
  <tr> 
   <td> Dominio non valido </td> 
   <td> Morbido </td> 
   <td> 2 </td> 
   <td> Il dominio dell’indirizzo e-mail non è corretto o non esiste più. Questo profilo sarà nuovamente oggetto di targeting fino a raggiungere 5 errori. In seguito, il record verrà impostato sullo stato di quarantena e non verrà eseguito alcun nuovo tentativo.<br /> </td> 
  </tr> 
  <tr> 
   <td> Cassetta postale piena </td> 
   <td> Morbido </td> 
   <td> 5 </td> 
   <td> La cassetta postale dell'utente è piena e non può accettare altri messaggi. Questo profilo sarà nuovamente oggetto di targeting fino a raggiungere 5 errori. Successivamente, il record verrà impostato sullo stato di quarantena e non verrà eseguito alcun nuovo tentativo.<br /> Questo tipo di errore è gestito da un processo di pulizia, l’indirizzo viene impostato su uno stato valido dopo 30 giorni.<br /> Avviso: per consentire la rimozione automatica dell’indirizzo dall’elenco degli indirizzi in quarantena, è necessario avviare il flusso di lavoro tecnico Database cleanup.<br /> </td> 
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
   <td> L’indirizzo è in qualificazione perché l’errore non è stato ancora incrementato. Questo tipo di errore si verifica quando un nuovo messaggio di errore viene inviato dal server: può essere un errore isolato, ma se si verifica di nuovo, il contatore degli errori aumenta, avvisando i team tecnici. Possono quindi eseguire l’analisi dei messaggi e qualificare questo errore tramite <span class="uicontrol">Amministrazione</span> / <span class="uicontrol">Campaign Management</span> / <span class="uicontrol">Gestione non consegnabili</span> nella struttura.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non idoneo per le offerte </td> 
   <td> Ignorato </td> 
   <td> 16 </td> 
   <td> Il destinatario non era idoneo per le offerte nella consegna.<br /> </td> 
  </tr> 
  <tr> 
   <td> Rifiutato </td> 
   <td> Morbido/rigido </td> 
   <td> 20 </td> 
   <td> L’indirizzo è stato messo in quarantena a causa di un feedback di sicurezza come segnalazione di spam. In base all’errore, l’indirizzo verrà ritentato fino a quando il contatore degli errori non raggiunge il valore 5, oppure verrà inviato direttamente in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Target di dimensioni limitate </td> 
   <td> Ignorato </td> 
   <td> 17 </td> 
   <td> È stata raggiunta la dimensione massima di consegna per il destinatario.<br /> </td> 
  </tr> 
  <tr> 
   <td> Indirizzo non qualificato </td> 
   <td> Ignorato </td> 
   <td> 15 </td> 
   <td> L'indirizzo postale non è stato qualificato.<br /> </td> 
  </tr> 
  <tr> 
   <td> Non raggiungibile </td> 
   <td> Morbido/rigido </td> 
   <td> 3 </td> 
   <td> Si è verificato un errore nella catena di consegna del messaggio. Potrebbe trattarsi di un problema nell’inoltro SMTP, un dominio temporaneamente non raggiungibile, ecc. In base all’errore, l’indirizzo verrà ritentato fino a quando il contatore degli errori non raggiunge il valore 5, oppure verrà inviato direttamente in quarantena.<br /> </td> 
  </tr> 
  <tr> 
   <td> Utente sconosciuto </td> 
   <td> Rigido </td> 
   <td> 1 </td> 
   <td> L'indirizzo non esiste. Per questo profilo non verranno tentate ulteriori consegne.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Tentativi dopo un errore temporaneo di consegna {#retries-after-a-delivery-temporary-failure}

Se un messaggio non riesce a causa di un **Morbido** o **Ignorato** errore temporaneo, verranno eseguiti nuovi tentativi per la durata della consegna.

>[!NOTE]
>
>I messaggi temporaneamente non consegnati possono essere correlati solo a una **Morbido** o **Ignorato** errore, ma non un **Rigido** errore (vedere [Tipi e motivi di errori di consegna](#delivery-failure-types-and-reasons)).

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), le impostazioni per i nuovi tentativi nella consegna non vengono più utilizzate da Campaign. I nuovi tentativi di mancato recapito non permanenti e il periodo di tempo che intercorre tra di essi sono determinati dall’MTA avanzato in base al tipo e alla gravità delle risposte di mancato recapito provenienti dal dominio e-mail del messaggio.

Per le installazioni on-premise e le installazioni in hosting/ibride che utilizzano l’MTA di Campaign legacy, per modificare la durata di una consegna, passa ai parametri avanzati della consegna o del modello di consegna e specifica la durata desiderata nel campo corrispondente. Consulta [Definizione del periodo di validità](steps-sending-the-delivery.md#defining-validity-period).

La configurazione predefinita consente cinque tentativi a intervalli di un’ora, seguiti da un nuovo tentativo al giorno per quattro giorni. Il numero di tentativi può essere modificato a livello globale (contatta l’amministratore tecnico Adobe) o per ogni modello di consegna o consegna. Consulta [Configurare nuovi tentativi](steps-sending-the-delivery.md#configuring-retries).

## Errori sincroni e asincroni {#synchronous-and-asynchronous-errors}

Un messaggio può non riuscire immediatamente (errore sincrono) o in seguito, dopo che è stato inviato (errore asincrono).

* Errore sincrono: il server di posta remota contattato dal server di consegna Adobe Campaign ha restituito immediatamente un messaggio di errore. La consegna non può essere inviata al server del profilo. Adobe Campaign qualifica ogni errore per determinare se gli indirizzi e-mail interessati devono essere posti in quarantena o meno. Consulta [Qualificazione di mail non recapitate](#bounce-mail-qualification).
* Errore asincrono: una mail non recapitata o un SR è stato inviato in seguito dal server ricevente. Il messaggio viene caricato in una cassetta postale tecnica utilizzata dall&#39;applicazione per etichettare i messaggi con un errore. Gli errori asincroni possono verificarsi fino a una settimana dopo l’invio di una consegna.

  >[!NOTE]
  >
  >La configurazione della cassetta postale di mancato recapito è descritta in [questa sezione](../../installation/using/deploying-an-instance.md#managing-bounced-emails).

  Il [ciclo di feedback](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#feedback-loops) funziona come le e-mail non recapitate. Quando un utente qualifica un’e-mail come spam, puoi configurare le regole e-mail in Adobe Campaign per bloccare tutte le consegne a questo utente. I messaggi inviati agli utenti che hanno qualificato un’e-mail come spam vengono automaticamente reindirizzati verso una casella e-mail creata appositamente a tale scopo. Gli indirizzi di questi utenti sono in inserita nell&#39;elenco Bloccati di anche se non hanno fatto clic sul collegamento di annullamento dell’iscrizione. Gli indirizzi sono in inserito nell&#39;elenco Bloccati di nel (**NmsAddress**) e non nella tabella di quarantena (**NmsRecipient**) tabella dei destinatari.

  >[!NOTE]
  >
  >La gestione dei reclami è descritta nel [Gestione del recapito messaggi](about-deliverability.md) sezione.

## Gestione posta non recapitata {#bounce-mail-management}

La piattaforma Adobe Campaign consente di gestire gli errori di consegna e-mail tramite la funzionalità di mail non recapitate.

Quando un messaggio e-mail non può essere recapitato a un destinatario, il server di messaggistica remota restituisce automaticamente un messaggio di errore (messaggio non recapitato) a una casella in entrata tecnica progettata a tale scopo.

Per le installazioni on-premise e le installazioni in hosting/ibride che utilizzano l’MTA di Campaign legacy, i messaggi di errore vengono raccolti dalla piattaforma Adobe Campaign e qualificati dal processo inMail per arricchire l’elenco delle regole di gestione e-mail.

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), la maggior parte delle regole di gestione e-mail non viene più utilizzata. Per ulteriori informazioni, consulta [questa sezione](#email-management-rules).

### Qualificazione di mail non recapitate {#bounce-mail-qualification}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md):
>
>* Le qualifiche di mancato recapito in **[!UICONTROL Delivery log qualification]** tabella non più utilizzata per **sincrono** messaggi di errore di consegna. L’MTA avanzato determina il tipo e la qualifica di mancato recapito e invia nuovamente tali informazioni a Campaign.
>
>* **Asincrono** i mancati recapiti sono ancora qualificati dal processo inMail attraverso **[!UICONTROL Inbound email]** regole. Per ulteriori informazioni, consulta [Regole di gestione e-mail](#email-management-rules).
>
>* Per le istanze che utilizzano l’MTA avanzato **senza webhook**, il **[!UICONTROL Inbound email]** Le regole verranno utilizzate anche per elaborare le e-mail non recapitate sincrone provenienti dall’MTA avanzato, utilizzando lo stesso indirizzo e-mail utilizzato per le e-mail non recapitate asincrone.

Per le installazioni on-premise e in hosting/ibride utilizzando l’MTA di Campaign legacy, quando la consegna di un’e-mail non riesce, il server di consegna Adobe Campaign riceve un messaggio di errore dal server di messaggistica o dal server DNS remoto. L&#39;elenco degli errori è costituito dalle stringhe contenute nel messaggio restituito dal server remoto. A ogni messaggio di errore vengono assegnati tipi e motivi di errore.

Questo elenco è disponibile tramite **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Delivery log qualification]** nodo. Contiene tutte le regole utilizzate da Adobe Campaign per qualificare gli errori di consegna. Non è esaustivo, è regolarmente aggiornato da Adobe Campaign e può anche essere gestito dall’utente.

![](assets/tech_quarant_rules_qualif.png)

Il messaggio restituito dal server remoto alla prima occorrenza di questo tipo di errore viene visualizzato nel **[!UICONTROL First text]** colonna del **[!UICONTROL Delivery log qualification]** tabella. Se questa colonna non viene visualizzata, fare clic su **[!UICONTROL Configure list]** nella parte inferiore destra dell&#39;elenco per selezionarlo.

![](assets/tech_quarant_rules_qualif_text.png)

Adobe Campaign filtra questo messaggio per eliminare il contenuto della variabile (ad esempio ID, date, indirizzi e-mail, numeri di telefono, ecc.) e visualizza il risultato filtrato nel **[!UICONTROL Text]** colonna. Le variabili sono sostituite da **`#xxx#`**, ad eccezione degli indirizzi sostituiti con **`*`**.

Questo processo consente di riunire tutti gli errori dello stesso tipo ed evitare più voci per errori simili nella tabella Qualificazione del registro di consegna.

>[!NOTE]
>
>Il **[!UICONTROL Number of occurrences]** visualizza il numero di occorrenze del messaggio nell’elenco. Tale numero è limitato a 100 000. È possibile modificare il campo, ad esempio per reimpostarlo.

I messaggi non recapitati possono avere il seguente stato di qualifica:

* **[!UICONTROL To qualify]** : impossibile qualificare la posta non recapitata. È necessario assegnare la qualifica al team Deliverability per garantire un recapito della piattaforma efficiente. Se non è qualificata, la posta non recapitata non viene utilizzata per arricchire l’elenco delle regole di gestione e-mail.
* **[!UICONTROL Keep]** : la mail non recapitata è stata qualificata e verrà utilizzata da **Aggiorna per il recapito messaggi** flusso di lavoro da confrontare con le regole di gestione e-mail esistenti e arricchire l’elenco.
* **[!UICONTROL Ignore]** : la mail non recapitata viene ignorata dall’MTA della campagna, il che significa che non verrà mai messa in quarantena l’indirizzo del destinatario. Non verrà utilizzato da **Aggiorna per il recapito messaggi** e non verrà inviato alle istanze client.

![](assets/deliverability_qualif_status.png)

>[!NOTE]
>
>In caso di interruzione di un ISP, le e-mail inviate tramite Campaign verranno contrassegnate erroneamente come messaggi non recapitati. Per risolvere questo problema, devi aggiornare la qualifica di mancato recapito. Per ulteriori informazioni, consulta [questa pagina](update-bounce-qualification.md).

### Regole di gestione e-mail {#email-management-rules}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), la maggior parte delle regole di gestione e-mail non viene più utilizzata. Per ulteriori dettagli, consulta le sezioni seguenti.

Le regole di posta sono accessibili tramite **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Mail rule sets]** nodo. Le regole di gestione delle e-mail sono visualizzate nella parte inferiore della finestra.

![](assets/tech_quarant_rules.png)

>[!NOTE]
>
>I parametri predefiniti della piattaforma sono configurati nella procedura guidata di distribuzione. Per ulteriori informazioni, fare riferimento a [questa sezione](../../installation/using/deploying-an-instance.md).

Le regole predefinite sono le seguenti.

>[!IMPORTANT]
>
>* Se i parametri sono stati modificati, il server di consegna (MTA) deve essere riavviato.
>* La modifica o la creazione di regole di gestione è riservata agli utenti esperti.

#### E-mail in entrata {#inbound-email}

<!--
STATEMENT ONLY TRUE with Momentum and EFS+:
For hosted or hybrid installations, if you have upgraded to the [Enhanced MTA](sending-with-enhanced-mta.md), and if your instance has **Webhooks** functionality, the **[!UICONTROL Inbound email]** rules are no longer used for synchronous delivery failure error messages. For more on this, see [this section](#bounce-mail-qualification).

For on-premise installations and hosted/hybrid installations using the legacy Campaign MTA, these rules contain the list of character strings which can be returned by remote servers and which let you qualify the error (**Hard**, **Soft** or **Ignored**).-->

Il **[!UICONTROL Inbound email]** le regole contengono l’elenco di stringhe di caratteri che possono essere restituite dai server remoti e che ti consentono di qualificare l’errore (**Rigido**, **Morbido** o **Ignorato**).

Quando un messaggio e-mail non riesce, il server remoto restituisce un messaggio di mancato recapito all’indirizzo specificato nella [parametri piattaforma](../../installation/using/deploying-an-instance.md). Adobe Campaign confronta il contenuto di ogni e-mail non recapitata con le stringhe nell’elenco delle regole, quindi assegna a ciascuna una delle tre opzioni [tipi di errore](#delivery-failure-types-and-reasons).

>[!NOTE]
>
>L’utente può creare le proprie regole. Durante l’importazione di un pacchetto e l’aggiornamento dei dati tramite **Aggiorna per il recapito messaggi** , le regole create dall&#39;utente vengono sovrascritte.

Per ulteriori informazioni sulla qualifica della posta non recapitata, consulta [questa sezione](#bounce-mail-qualification).

#### Gestione del dominio {#domain-management}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), il **[!UICONTROL Domain management]** le regole non vengono più utilizzate. La firma di autenticazione dell’e-mail **DKIM (DomainKeys Identified Mail)** viene eseguita dall’MTA avanzato per tutti i messaggi di tutti i domini. La firma non viene eseguita con **ID mittente**, **DomainKeys** o **S/MIME**, a meno che non venga specificato diversamente a livello di MTA avanzato.

Per le installazioni on-premise e in hosting/ibride utilizzando l’MTA di Campaign legacy, il server di messaggistica Adobe Campaign applica un singolo **Gestione del dominio** a tutti i domini.

<!--![](assets/tech_quarant_domain_rules_02.png)-->

* Puoi scegliere se attivare o meno determinati standard di identificazione e chiavi di crittografia per controllare il nome di dominio, ad esempio **ID mittente**, **DomainKeys**, **DKIM**, e **S/MIME**.
* Il **Inoltro SMTP** I parametri consentono di configurare l&#39;indirizzo IP e la porta di un server di inoltro per un dominio specifico. Per ulteriori informazioni, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#smtp-relay).

Se i messaggi vengono visualizzati in Outlook con **[!UICONTROL on behalf of]** nell’indirizzo del mittente, assicurati di non firmare le e-mail con **ID mittente**, che è lo standard obsoleto di autenticazione delle e-mail proprietarie di Microsoft. Se il **[!UICONTROL Sender ID]** è attivata, deseleziona la casella corrispondente e contatta [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Il recapito messaggi non sarà influenzato.

#### Gestione MX {#mx-management}

>[!IMPORTANT]
>
>Per le installazioni in hosting o ibride, se hai effettuato l’aggiornamento al [MTA avanzato](sending-with-enhanced-mta.md), il **[!UICONTROL MX management]** le regole di velocità effettiva di consegna non vengono più utilizzate. L’MTA avanzato utilizza le proprie regole MX, che gli consentono di personalizzare la velocità effettiva per dominio in base alla reputazione cronologica dell’e-mail e al feedback in tempo reale proveniente dai domini in cui invii le e-mail.

Per le installazioni on-premise e le installazioni in hosting/ibride che utilizzano l’MTA di Campaign legacy:

* Le regole di gestione MX vengono utilizzate per regolare il flusso delle e-mail in uscita per un dominio specifico. Campionano i messaggi di mancato recapito e bloccano l’invio dove appropriato.

* Il server di messaggistica Adobe Campaign applica regole specifiche ai domini, quindi le regole per il caso generale rappresentato da un asterisco nell’elenco delle regole.

* Per configurare le regole di gestione MX, è sufficiente impostare una soglia e selezionare alcuni parametri SMTP. A **soglia** è un limite calcolato come percentuale di errore oltre la quale tutti i messaggi verso un dominio specifico vengono bloccati. Ad esempio, nel caso generale, per un minimo di 300 messaggi, l’invio di e-mail viene bloccato per tre ore se il tasso di errore raggiunge il 90%.

Per ulteriori informazioni sulla gestione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).
