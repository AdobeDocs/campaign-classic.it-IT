---
product: campaign
title: Risoluzione dei problemi di invio della consegna
description: Ulteriori informazioni sulle prestazioni di consegna e su come risolvere i problemi relativi al monitoraggio della consegna
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring, Deliverability, Troubleshooting
role: User
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 1%

---

# Risoluzione dei problemi di invio della consegna {#delivery-troubleshooting}

In questa sezione sono elencati i problemi comuni che possono verificarsi durante l’invio delle consegne e come risolverli.

Inoltre, assicurati di seguire le best practice e gli elenchi di controllo descritti in [questa pagina](delivery-performances.md) per garantire il buon funzionamento delle consegne.

**Argomenti correlati:**

* [Stati di consegna](delivery-statuses.md)
* [Dashboard delle consegne](delivery-dashboard.md)
* [Informazioni sugli errori di consegna](understanding-delivery-failures.md)

## Consegne lente {#slow-deliveries}

Dopo aver fatto clic su **[!UICONTROL Send]** pulsante, la consegna sembra richiedere più tempo del solito. Ciò può essere dovuto a diversi elementi:

* Alcuni provider di posta elettronica potrebbero aver aggiunto i tuoi indirizzi IP a un inserisco nell&#39;elenco Bloccati di. In questo caso, controlla i registri e consulta [questa sezione](about-deliverability.md).

* La consegna potrebbe essere troppo grande per essere elaborata rapidamente. Ciò può verificarsi con una personalizzazione JavaScript elevata o se la consegna pesa più di 60 kbyte. Fai riferimento a Adobe Campaign [Best practice per la consegna](delivery-best-practices.md) per informazioni sulle linee guida per i contenuti.

* La limitazione potrebbe essersi verificata all’interno dell’MTA di Adobe Campaign. Ciò è causato da:

   * Messaggi sospesi (**[!UICONTROL quotas met]** message): sono state soddisfatte le quote dichiarate dalle regole MX dichiarative definite in Campaign. Per ulteriori informazioni su questo messaggio, consulta [questa pagina](deliverability-faq.md). Per ulteriori informazioni sulle regole MX, consulta [questa sezione](../../installation/using/email-deliverability.md#about-mx-rules).

   * Messaggi sospesi (**[!UICONTROL dynamic flow control]** message): l’MTA della campagna ha riscontrato errori durante il tentativo di recapitare messaggi per un determinato ISP, il che provoca un rallentamento per evitare una densità di errori troppo elevata e quindi il rischio di potenziali elenchi Bloccati da parte dell’.

* Un problema di sistema può impedire l’interazione tra i server, rallentando l’intero processo di invio. Controlla i server per assicurarti che non vi siano problemi di memoria o risorse che possano influire su Campaign nel processo di recupero dei dati di personalizzazione, ad esempio.

## Consegne pianificate {#scheduled-deliveries-}

Se le consegne non vengono eseguite alla data pianificata esatta, possono essere correlate a una differenza tra i fusi orari dei server. L’istanza di mid-sourcing e l’istanza di produzione possono trovarsi in fusi orari diversi.

Ad esempio, se l’istanza di mid-sourcing si trova nel fuso orario di Brisbane e l’istanza di produzione nel fuso orario di Darwin, entrambi i fusi orari sono a mezz’ora di distanza l’uno dall’altro, nel registro di audit risulterebbe chiaramente che se la consegna è pianificata per la produzione alle 11:56, la stessa consegna pianificata per il mid sarebbe alle 12:26, con una differenza di mezz’ora.

## Stato non riuscito {#failed-status}

Se lo stato di una consegna e-mail è **[!UICONTROL Failed]**, può essere collegata a un problema con blocchi di personalizzazione. I blocchi di personalizzazione in una consegna possono generare errori quando, ad esempio, gli schemi non corrispondono alla mappatura della consegna.

I registri di consegna sono fondamentali per comprendere il motivo per cui una consegna non è riuscita. Di seguito sono riportati possibili errori che puoi rilevare dai registri di consegna:

* I messaggi dei destinatari non riescono e viene visualizzato un errore &quot;Non raggiungibile&quot; che indica:

  ```
  Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
  ```

  La causa di questo problema è quasi sempre una personalizzazione in HTML che tenta di invocare una tabella o un campo che non è stato definito o mappato nel targeting a monte o nella mappatura di destinazione della consegna.

  Per risolvere questo problema, è necessario rivedere il flusso di lavoro e il contenuto della consegna per determinare in modo specifico quale personalizzazione sta tentando di chiamare la tabella in questione e se è possibile mappare o meno la tabella. Da lì, il percorso per la risoluzione sarà la rimozione della chiamata a questa tabella nel HTML o la correzione della mappatura alla consegna.

* Nel modello di distribuzione mid-sourcing, nei registri di consegna può essere visualizzato il seguente messaggio:

  ```
  Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
  ```

  La causa è collegata a problemi di prestazioni. Significa che l’istanza di marketing impiega troppo tempo a creare i dati prima di inviarli al server di mid-sourcing.

  Per risolvere questo problema, si consiglia di effettuare una prova di vuoto e reindicizzare il database. Per ulteriori informazioni sulla manutenzione del database, fare riferimento a [questa sezione](../../production/using/recommendations.md).

  È inoltre necessario riavviare tutti i flussi di lavoro con un&#39;attività pianificata e tutti i flussi di lavoro con stato non riuscito. Fai riferimento a [questa sezione](../../workflow/using/scheduler.md).

* Quando una consegna non riesce, nei registri di consegna può essere visualizzato il seguente errore:

  ```
  DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
  ```

  In genere, questo errore indica che esiste un campo o un blocco di personalizzazione all’interno dell’e-mail con più valori per il destinatario. Un blocco di personalizzazione è in uso e sta recuperando più di un record per un destinatario specifico.

  Per risolvere questo problema, controlla i dati di personalizzazione utilizzati, quindi controlla il target per i destinatari che hanno più di una voce per uno qualsiasi di questi campi. È inoltre possibile utilizzare un’ **[!UICONTROL Deduplication]** attività nel flusso di lavoro di targeting prima dell’attività di consegna per verificare che sia presente un solo campo di personalizzazione alla volta. Per ulteriori informazioni sulla deduplicazione, consulta [questa pagina](../../workflow/using/deduplication.md).

* Alcune consegne possono non riuscire e viene visualizzato un errore &quot;Non raggiungibile&quot; che indica:

  ```
  Inbound email bounce (rule 'Auto_replies' has matched this bounce).
  ```

  Ciò significa che la consegna è riuscita, ma Adobe Campaign ha ricevuto una risposta automatica dal destinatario (ad esempio, una risposta &quot;Fuori sede&quot;) corrispondente alle regole di e-mail in entrata &quot;Auto_reply&quot;.

  L’e-mail di risposta automatica viene ignorata da Adobe Campaign e l’indirizzo del destinatario non verrà messo in quarantena.
