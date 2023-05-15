---
product: campaign
title: Ottimizzare la consegna dei messaggi
description: Scopri come ottimizzare la consegna dei messaggi
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: 24b2ee47-bec7-43ce-81b3-0b2d1a5cebae
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 8%

---

# Ottimizzare la consegna {#optimize-delivery}



Prima ancora di iniziare la creazione delle consegne, puoi intraprendere diverse azioni per proteggere e ottimizzare il processo di invio a monte.

La sezione seguente illustra le best practice e le procedure consigliate per una configurazione ottimale di Adobe Campaign. Seguendo queste pratiche, i problemi che potresti riscontrare a valle verranno ridotti al minimo.

## Prestazioni della piattaforma

Diversi fattori possono influenzare direttamente le prestazioni del server e rallentare la piattaforma:

* Numero e tipo di elementi di personalizzazione: la personalizzazione nelle e-mail estrae i dati dal database per ciascun destinatario. Se sono presenti molti elementi di personalizzazione, ciò aumenta la quantità di dati necessari per preparare la consegna.  Ulteriori informazioni sulla personalizzazione in [questa sezione](about-personalization.md)

* Caricamento server: quando il server di marketing gestisce contemporaneamente diverse attività, può rallentare le prestazioni. Il server di marketing deve coordinare tutti i dati in entrata e in uscita per tutte le consegne per garantire che i dati siano corretti e puntuali.

   **SUGGERIMENTO** - Per evitare questo problema, coordina la pianificazione delle consegne con gli altri membri del team per garantire le migliori prestazioni.

* Esecuzione del flusso di lavoro: il monitoraggio dei flussi di lavoro è essenziale per evitare problemi di prestazioni della piattaforma. Seguire le linee guida elencate [in questo documento](../../workflow/using/workflow-best-practices.md#execution-and-performance).

* Se sei idoneo, puoi sfruttare [Funzionalità di Pannello di controllo Campaign di Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it) per monitorare la piattaforma, utilizzando [monitoraggio delle prestazioni](https://experienceleague.adobe.com/docs/control-panel/using/performance-monitoring/about-performance-monitoring.html?lang=it) funzionalità.

## Controllare la configurazione di rete {#network-config}

Per ottimizzare la consegna quando gestisci le e-mail in grandi volumi ed evitare errori per uno spammer, assicurati di disporre di una configurazione di rete legittima che non tenti di nascondere l’identità del server.

**Suggerimento**: Utilizza un indirizzo mittente trasparente corrispondente al sito web del tuo marchio. Ad esempio, la società TravelAgency gestisce la catena alberghiera Valentino. Possiede il dominio valentino.com per il suo sito web. Per promuovere il Valentino hotel a Parigi, utilizza il sottodominio paris.valentino.com. Pertanto, un indirizzo del mittente pertinente può essere hotel@paris.valentino.com.

## Gestione del recapito messaggi {#deliverability-management}

Per raggiungere la casella in entrata dei destinatari senza rimbalzare o contrassegnare come spam, devi migliorare il tasso di recapito dei messaggi.

* Che cos’è il recapito messaggi?

   * Si riferisce ai fattori di un’e-mail che determinano la sua capacità di essere accettata dal server di un destinatario. Gli ISP (Internet Service Provider) filtrano le e-mail che identificano come SPAM o impediscono il download delle immagini. Se determinano che un determinato dominio sta inviando troppe e-mail, imposteranno un limite al numero di e-mail che accetteranno da quel mittente.

   * Quando controlli l&#39;e-mail per il recapito messaggi, vuoi concentrarti su quattro categorie principali: qualità dei dati, messaggi e contenuti, infrastruttura di invio e reputazione. Per maggiori informazioni su questo argomento, consulta [questa sezione](about-deliverability.md).

* Applicare le raccomandazioni dettagliate [in questo documento](about-deliverability.md).

* Contatta il tuo rappresentante Adobe per assistenza.

## Gestione della quarantena {#quarantine-management}

È nel tuo interesse mantenere buoni processi di gestione della quarantena.

Quando inizi a inviare e-mail su una nuova piattaforma, puoi utilizzare un elenco di indirizzi non completamente qualificati. Se invii a indirizzi non validi o a indirizzi di articoli da miele (caselle di posta create solo per gli spammer ingannatori), questo inizierà a diminuire la reputazione della tua piattaforma. I buoni processi di gestione della quarantena aiutano a: mantenere la qualità degli indirizzi, evitare elenchi Bloccati da parte dei provider di accesso a Internet e ridurre il tasso di errore, velocizzando le consegne e il throughput.

**Suggerimenti**

* Se disponi di un elenco di indirizzi non validi, Adobe consiglia di importarlo nella tabella di quarantena, tramite **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Non deliverables Management]** > **[!UICONTROL Non deliverables and addresses]**.

* I destinatari i cui indirizzi sono messi in quarantena sono esclusi per impostazione predefinita durante l’analisi della consegna: non sono mirati. In questo modo le consegne sono più rapide, poiché il tasso di errore ha un effetto significativo sulla velocità di consegna. È possibile mettere in quarantena un indirizzo e-mail, ad esempio se la casella in entrata è piena o se l’indirizzo non esiste. [Ulteriori informazioni](#identifying-quarantined-addresses-for-a-delivery)

* Adobe Campaign gestisce gli indirizzi errati in base al tipo di errore restituito. Per ulteriori informazioni al riguardo, consulta [questa sezione](understanding-quarantine-management.md).


* Alcuni provider di accesso a Internet considerano automaticamente le e-mail come spam se il tasso di indirizzi non validi è troppo alto. La quarantena ti consente quindi di evitare di essere aggiunta al elenco Bloccati da questi provider.

* La gestione delle quarantena aiuterà anche a ridurre i costi di invio degli SMS escludendo numeri di telefono errati dalle consegne.

## Doppio meccanismo di consenso {#double-opt-in}

Per evitare l’invio di messaggi a indirizzi non validi, limitare le comunicazioni non corrette e migliorare la reputazione del mittente, l’Adobe consiglia di implementare un doppio meccanismo di consenso per la conferma post-abbonamento. In questo modo il destinatario si è iscritto intenzionalmente.

I dettagli relativi all&#39;attuazione di tale meccanismo sono descritti in [questa sezione](../../web/using/use-cases--web-forms.md).
