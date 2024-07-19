---
product: campaign
title: Ottimizzare la consegna dei messaggi
description: Scopri come ottimizzare la consegna dei messaggi
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Deliverability
role: User
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 4%

---

# Ottimizzare la consegna {#optimize-delivery}

Prima ancora di iniziare a creare le consegne, puoi intraprendere diverse azioni per proteggere e ottimizzare il processo di invio a monte.

La sezione seguente illustra le best practice e le procedure consigliate per la configurazione ottimale di Adobe Campaign. L’aderenza a queste procedure riduce al minimo i problemi che potresti riscontrare a valle.

## Prestazioni della piattaforma

Diversi fattori possono influire direttamente sulle prestazioni del server e rallentare la piattaforma:

* Il numero e il tipo di elementi di personalizzazione: la personalizzazione nelle e-mail estrae dati dal database per ogni destinatario. Se sono presenti molti elementi di personalizzazione, aumenta la quantità di dati necessari per preparare la consegna.  Ulteriori informazioni sulla personalizzazione in [questa sezione](about-personalization.md)

* Caricamento del server: quando il server di marketing gestisce più attività diverse contemporaneamente, può rallentare le prestazioni. Il server di marketing deve coordinare tutti i dati in entrata e in uscita per tutte le consegne per garantire che i dati siano corretti e puntuali.

  **SUGGERIMENTO** - Per evitare questo problema, coordina la pianificazione delle consegne con gli altri membri del tuo team per garantire le migliori prestazioni.

* Esecuzione del flusso di lavoro: il monitoraggio dei flussi di lavoro è essenziale per evitare problemi di prestazioni della piattaforma. Segui le linee guida elencate [in questo documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Se sei idoneo, puoi sfruttare le [funzionalità di Pannello di controllo Campaign di Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it) per monitorare la tua piattaforma utilizzando le [funzionalità di monitoraggio delle prestazioni](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=it).

## Verifica la configurazione di rete {#network-config}

Per ottimizzare la consegna quando gestisci le e-mail in grandi volumi ed evitare di essere scambiato per uno spammer, assicurati di disporre di una configurazione di rete legittima che non tenti di nascondere l’identità del server.

**Suggerimento**: utilizza un indirizzo mittente trasparente corrispondente al sito Web del tuo marchio. Ad esempio, la società TravelAgency gestisce la catena alberghiera Valentino. È il proprietario del dominio valentino.com per il suo sito web. Per promuovere l&#39;hotel Valentino a Parigi, utilizza il sottodominio paris.valentino.com. Pertanto, un indirizzo del mittente pertinente può essere hotel@paris.valentino.com.

## Gestione del recapito messaggi {#deliverability-management}

Per raggiungere la casella in entrata dei destinatari senza che vengano generati o contrassegnati come spam, devi migliorare il tasso di recapito dei messaggi.

* Che cos’è il recapito messaggi?

   * Si riferisce ai fattori di un’e-mail che determinano la sua capacità di essere accettata dal server di un destinatario. Gli ISP (Internet Service Provider) filtrano le e-mail che identificano come SPAM, oppure bloccano il download delle immagini. Se determinano che un determinato dominio sta inviando troppe e-mail, imposteranno un limite al numero di e-mail che accetteranno da quel mittente.

   * Durante il controllo della consegna delle e-mail, desideri concentrarti su quattro categorie principali: qualità dei dati, messaggio e contenuto, infrastruttura di invio e reputazione. Per ulteriori informazioni su questo argomento, consulta [questa sezione](about-deliverability.md).

* Applica i consigli dettagliati [ in questo documento](about-deliverability.md).

* Contatta il rappresentante del tuo Adobe per assistenza.

## Gestione della quarantena {#quarantine-management}

È nel tuo interesse mantenere processi di gestione della quarantena efficaci.

Quando inizi a inviare e-mail su una nuova piattaforma, puoi utilizzare un elenco di indirizzi non completamente qualificati. Se invii a indirizzi non validi o a indirizzi honeypot (cassette postali create solo per ingannare gli spammer), questo comincerà a ridurre la reputazione della tua piattaforma. Una buona gestione della quarantena aiuta a: mantenere la qualità dell’indirizzo, evitare l’inserisco nell&#39;elenco Bloccati da parte dei provider di accesso a Internet e ridurre il tasso di errore, velocizzando le consegne e la velocità effettiva.

**Suggerimenti**

* Se disponi di un elenco di indirizzi non validi, Adobe consiglia di importarlo nella tabella di quarantena tramite **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* I destinatari i cui indirizzi sono in quarantena sono esclusi per impostazione predefinita durante l’analisi della consegna: non sono oggetto di targeting. In questo modo le consegne saranno più rapide, poiché il tasso di errore ha un effetto significativo sulla velocità di consegna. Un indirizzo e-mail può essere messo in quarantena, ad esempio quando la casella in entrata è piena o se l’indirizzo non esiste. [Ulteriori informazioni](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign gestisce gli indirizzi errati in base al tipo di errore restituito. Per ulteriori informazioni al riguardo, consulta [questa sezione](understanding-quarantine-management.md).


* Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena consente quindi di evitare che questi provider aggiungano altri elementi al elenco Bloccati del sistema di protezione.

* La gestione delle quarantene contribuirà inoltre a ridurre i costi di invio degli SMS escludendo numeri di telefono errati dalle consegne.

## Doppio meccanismo di consenso {#double-opt-in}

Per evitare l’invio di messaggi a indirizzi non validi, limitare le comunicazioni improprie e migliorare la reputazione del mittente, l’Adobe consiglia di implementare un doppio meccanismo di consenso per la conferma dopo l’abbonamento. Questo aiuta a garantire che un destinatario si sia iscritto intenzionalmente.

I dettagli relativi all&#39;implementazione di questo meccanismo sono descritti in [questa sezione](../../web/using/use-cases-web-forms.md).
