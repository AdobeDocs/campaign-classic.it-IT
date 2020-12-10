---
solution: Campaign Classic
product: campaign
title: Risoluzione dei problemi
description: Scopri ulteriori informazioni sulle prestazioni di distribuzione e come risolvere i problemi relativi al monitoraggio delle consegne.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: f3ba836bbb5a5f82d6a7868dcb15edc8e61b9a5b
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---


# Risoluzione dei problemi di invio {#delivery-troubleshooting}

In questa sezione sono elencati i problemi più comuni che si possono incontrare durante l&#39;invio delle consegne e come risolverli.

Inoltre, assicurati di seguire le procedure ottimali e l&#39;elenco di controllo descritti in [questa pagina](../../delivery/using/delivery-performances.md) per garantire il corretto svolgimento delle consegne.

**Argomenti correlati:**

* [Stati di consegna](../../delivery/using/delivery-statuses.md)
* [Pannello consegna](../../delivery/using/delivery-dashboard.md)
* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)

## Consegne lente {#slow-deliveries}

Dopo aver fatto clic sul pulsante **[!UICONTROL Send]**, la consegna sembra richiedere più tempo del solito. Ciò può essere causato da diversi elementi:

* Alcuni provider di posta elettronica potrebbero aver aggiunto gli indirizzi IP a un elenco Bloccati. In questo caso, controllate i registri di trasmissione e consultate [questa sezione](../../delivery/using/about-deliverability.md).

* La consegna potrebbe essere troppo grande per essere elaborata rapidamente, questo potrebbe verificarsi con una personalizzazione JavaScript elevata o se il volume di consegna supera i 60 Kbyte. Per informazioni sulle linee guida relative ai contenuti, fare riferimento  procedure ottimali di distribuzione di Adobe Campaign [.](../../delivery/using/delivery-best-practices.md)

* Potrebbe essersi verificata una limitazione all&#39;interno della  MTA Adobe Campaign. Ciò è causato da:

   * Messaggi aperti (**[!UICONTROL quotas met]** messaggio): sono state rispettate le quote dichiarate dalle regole dichiarative MX definite in Campaign. Per ulteriori informazioni su questo messaggio, fare riferimento a [questa pagina](../../delivery/using/deliverability-faq.md) . Per ulteriori informazioni sulle regole MX, fare riferimento a [questa pagina](../../delivery/using/technical-recommendations.md#mx-rules).

   * Messaggi aperti (**[!UICONTROL dynamic flow control]** messaggio): Campaign MTA ha rilevato degli errori quando si tenta di inviare messaggi per un dato ISP che causano un rallentamento per evitare una densità di errore troppo elevata e quindi di fronte a un potenziale elenco Bloccati.

* Un problema del sistema può impedire ai server di interagire tra loro: questo può rallentare l&#39;intero processo di invio. Controlla i server per assicurarti che non ci siano problemi di memoria o di risorse che possano avere un impatto su Campaign, ad esempio nel processo di ottenimento dei dati di personalizzazione.

## Spedizioni programmate {#scheduled-deliveries-}

Se le consegne non vengono eseguite alla data pianificata esatta, è possibile che si tratti di una differenza tra il fuso orario dei server. L&#39;istanza mid-sourcing e l&#39;istanza di produzione possono essere in fusi orari diversi.

Ad esempio, se l’istanza mid-sourcing si trova nel fuso orario di Brisbane e l’istanza di produzione si trova nel fuso orario di Darwin, entrambi i fusi orari sono distanti mezz’ora, quindi nel registro di controllo si può vedere chiaramente che se la consegna è pianificata per la produzione alle 11:56, la stessa consegna prevista per metà sarà alle 12:26, con una differenza di mezz’ora.

## Stato non riuscito {#failed-status}

Se lo stato di invio di un&#39;e-mail è **[!UICONTROL Failed]**, può essere collegato a un problema con i blocchi di personalizzazione. I blocchi di personalizzazione in una consegna possono generare errori se, ad esempio, gli schemi non corrispondono alla mappatura della consegna.

I registri di consegna sono la chiave per capire perché una consegna non è riuscita. Di seguito sono riportati possibili errori che è possibile rilevare dai registri di consegna:

* I messaggi del destinatario non riescono con un errore &quot;Impossibile raggiungere&quot; che indica:

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   La causa di questo problema è quasi sempre una personalizzazione all&#39;interno dell&#39;HTML che tenta di richiamare una tabella o un campo che non è stato definito o mappato nel targeting upstream o nella mappatura di destinazione della consegna.

   Per correggere questo problema, è necessario rivedere il flusso di lavoro e il contenuto di distribuzione per determinare in modo specifico quale personalizzazione sta tentando di chiamare la tabella in questione e se è possibile mappare la tabella. Da qui, la rimozione della chiamata a questa tabella nell’HTML o la correzione della mappatura alla consegna costituirebbe il percorso della risoluzione.

* Nel modello di distribuzione mid-sourcing, il seguente messaggio può essere visualizzato nei registri di distribuzione:

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   La causa è collegata a problemi di prestazioni. Significa che l&#39;istanza di marketing impiega troppo tempo a generare dati prima di inviarli al server di mid-sourcing.

   Per risolvere questo problema, si consiglia di eseguire un vuoto e reindicizzare il database. Per ulteriori informazioni sulla manutenzione del database, consultare [questa sezione](../../production/using/recommendations.md).

   È inoltre necessario riavviare tutti i flussi di lavoro con un&#39;attività pianificata e tutti i flussi di lavoro con stato di errore. Fai riferimento a [questa sezione](../../workflow/using/scheduler.md).

* Quando una consegna non riesce, nei registri di consegna può comparire il seguente errore:

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   Solitamente, questo errore indica che all&#39;interno dell&#39;e-mail è presente un campo o un blocco di personalizzazione con più valori per il destinatario. Viene utilizzato un blocco di personalizzazione che raccoglie più record per un particolare destinatario.

   Per risolvere questo problema, controllate i dati di personalizzazione utilizzati, quindi verificate se nel target sono presenti più voci per i destinatari con più di una voce per ciascuno di questi campi. Potete inoltre utilizzare un&#39;attività **[!UICONTROL Deduplication]** nel flusso di lavoro di targeting prima dell&#39;attività di consegna per verificare che sia presente un solo campo di personalizzazione alla volta. Per ulteriori informazioni sulla deduplicazione, fare riferimento a [questa pagina](../../workflow/using/deduplication.md).

* Alcune consegne potrebbero non riuscire con un errore &quot;Impossibile da raggiungere&quot; che indica:

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   Ciò significa che la consegna è riuscita, ma  Adobe Campaign ha ricevuto una risposta automatica dal destinatario (ad es. una risposta &quot;Fuori sede&quot;) che corrispondeva alle regole e-mail in entrata &#39;Auto_answer&#39;.

   L&#39;e-mail di risposta automatica viene ignorata da  Adobe Campaign e l&#39;indirizzo del destinatario non verrà inviato alle quarantena.
