---
product: campaign
title: Risoluzione dei problemi
description: Ulteriori informazioni sulle prestazioni di consegna e su come risolvere i problemi relativi al monitoraggio della consegna.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---

# Risoluzione dei problemi di invio della consegna {#delivery-troubleshooting}

![](../../assets/common.svg)

In questa sezione sono elencati i problemi comuni che potresti riscontrare durante l’invio delle consegne e come risolverli.

Inoltre, assicurati di seguire le best practice e la checklist dettagliata in [questa pagina](delivery-performances.md) per garantire il corretto svolgimento delle consegne.

**Argomenti correlati:**

* [Stati di consegna](delivery-statuses.md)
* [Dashboard delle consegne](delivery-dashboard.md)
* [Informazioni sugli errori di consegna](understanding-delivery-failures.md)

## Consegne lente {#slow-deliveries}

Dopo aver fatto clic sul pulsante **[!UICONTROL Send]** pulsante, la consegna sembra richiedere più tempo del solito. Questo può essere causato da diversi elementi:

* Alcuni provider di posta elettronica potrebbero aver aggiunto i tuoi indirizzi IP a un elenco Bloccati. In questo caso, controlla i tuoi registri di trasmissione e consulta [questa sezione](about-deliverability.md).

* La consegna potrebbe essere troppo grande per essere elaborata rapidamente, potrebbe verificarsi con una personalizzazione JavaScript elevata o se la consegna pesa più di 60 kbyte. Consulta Adobe Campaign [Best practice per le consegne](delivery-best-practices.md) per informazioni sulle linee guida per i contenuti.

* È possibile che si sia verificata una limitazione nell’MTA di Adobe Campaign. Ciò è causato da:

   * Messaggi aperti (**[!UICONTROL quotas met]** messaggio): sono state soddisfatte le quote dichiarate dalle regole dichiarative MX definite in Campaign. Per ulteriori informazioni su questo messaggio, consulta [questa pagina](deliverability-faq.md). Per ulteriori informazioni sulle regole MX, consulta [questa sezione](../../installation/using/email-deliverability.md#about-mx-rules).

   * Messaggi aperti (**[!UICONTROL dynamic flow control]** messaggio): L’MTA di Campaign ha rilevato errori durante il tentativo di inviare messaggi per un determinato ISP, il che causa un rallentamento per evitare una densità di errore troppo elevata e quindi un potenziale elenco Bloccati.

* Un problema di sistema può impedire ai server di interagire tra loro: questo può rallentare l’intero processo di invio. Controlla i server per assicurarti che non ci siano problemi di memoria o di risorse che possono influenzare Campaign nel processo di ottenimento, ad esempio, dei dati di personalizzazione.

## Consegne pianificate {#scheduled-deliveries-}

Se le consegne non vengono eseguite alla data pianificata esatta, può essere correlato a una differenza tra il fuso orario dei server. L’istanza di mid-sourcing e l’istanza di produzione possono trovarsi in fusi orari diversi.

Ad esempio, se l’istanza di mid-sourcing si trova nel fuso orario di Brisbane e l’istanza di produzione si trova nel fuso orario di Darwin, entrambi i fusi orari sono a mezz’ora di distanza l’uno dall’altro, nel registro di controllo si vedrà chiaramente che se la consegna è pianificata per la produzione alle 11:56, la stessa consegna pianificata per la metà sarà alle 12:26 e avrà una differenza di mezz’ora.

## Stato non riuscito {#failed-status}

Se lo stato di una consegna e-mail è **[!UICONTROL Failed]**, può essere collegato a un problema relativo ai blocchi di personalizzazione. I blocchi di personalizzazione in una consegna possono generare errori se, ad esempio, gli schemi non corrispondono alla mappatura della consegna.

I registri di consegna sono la chiave per capire perché una consegna non è riuscita. Di seguito sono riportati possibili errori che è possibile rilevare dai log di consegna:

* I messaggi del destinatario non riescono con un errore &quot;Non raggiungibile&quot; che indica:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   La causa di questo problema è quasi sempre una personalizzazione all’interno di HTML che tenta di invocare una tabella o un campo che non è stato definito o mappato nel targeting a monte o nella mappatura di destinazione della consegna.

   Per correggere questo problema, è necessario rivedere il flusso di lavoro e il contenuto di consegna per determinare in modo specifico quale personalizzazione sta tentando di chiamare la tabella in questione e se è possibile mappare o meno la tabella. Da lì, rimuovere la chiamata a questa tabella in HTML o correggere la mappatura alla consegna sarebbe il percorso della risoluzione.

* Nel modello di distribuzione di mid-sourcing , il seguente messaggio può essere visualizzato nei log di consegna:

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   La causa è collegata a problemi di prestazioni. Significa che l’istanza di marketing impiega troppo tempo a generare i dati prima di inviarli al server di mid-sourcing.

   Per risolvere questo problema, si consiglia di eseguire un vuoto e reindicizzare il database. Per ulteriori informazioni sulla manutenzione del database, consulta [questa sezione](../../production/using/recommendations.md).

   È inoltre necessario riavviare tutti i flussi di lavoro con un’attività pianificata e tutti i flussi di lavoro in stato di errore. Fai riferimento a [questa sezione](../../workflow/using/scheduler.md).

* Quando una consegna non riesce, può apparire il seguente errore nei log di consegna:

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   Di solito, questo errore significa che c&#39;è un campo o un blocco di personalizzazione all&#39;interno dell&#39;e-mail che ha più di un valore per il destinatario. Viene utilizzato un blocco di personalizzazione che recupera più record per un particolare destinatario.

   Per risolvere questo problema, controlla i dati di personalizzazione utilizzati, quindi controlla il target per i destinatari che hanno più di una voce per ciascuno di questi campi. È inoltre possibile utilizzare un **[!UICONTROL Deduplication]** nel flusso di lavoro di targeting prima dell’attività di consegna per verificare che sia presente un solo campo di personalizzazione alla volta. Per ulteriori informazioni sulla deduplicazione, consulta [questa pagina](../../workflow/using/deduplication.md).

* Alcune consegne possono non riuscire con un errore &quot;Non raggiungibile&quot; che indica:

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   Ciò significa che la consegna è riuscita, ma Adobe Campaign ha ricevuto una risposta automatica dal destinatario (ad esempio una risposta &quot;Fuori sede&quot;) che corrisponde alle regole di posta in entrata &quot;Auto_reply&quot;.

   L’e-mail di risposta automatica viene ignorata da Adobe Campaign e l’indirizzo del destinatario non verrà inviato alla quarantena.
