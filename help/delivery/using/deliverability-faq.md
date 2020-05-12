---
title: Punti chiave per la gestione della recapito in Adobe Campaign Classic
description: Quali sono i punti chiave da verificare nella gestione della recapito in Adobe Campaign Classic?
page-status-flag: never-activated
uuid: 2681042b-3018-42ae-b252-2367b56616bd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 6a394eeb-fbe1-4712-bb13-db5d7965fb73
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 0%

---


# Risoluzione dei problemi di recapito{#deliverability-faq}

Si è verificato un problema di recapito? Puoi trovare la soluzione qui.

## Errore regola MX {#mx-rule-error}

**Cosa significa il messaggio di errore &quot;quote rispettate&quot;?**

Questo messaggio indica che è stato raggiunto il limite di quota per un MX specifico e che è necessario attendere di poter inviare un&#39;altra e-mail a questo provider.

In Adobe Campaign, esiste una configurazione relativa al numero di e-mail all&#39;ora che è possibile inviare. Questa configurazione deve essere utilizzata con attenzione, in quanto il numero definito nell&#39;istanza riguarda il numero di connessioni effettuate con l&#39;ISP e non il numero di e-mail effettivamente inviate.

Ciò significa che una connessione può utilizzare una regola MX senza inviare correttamente un&#39;e-mail. In questo caso, una configurazione con un IP o un dominio con una reputazione ridotta dovrà provare diverse connessioni prima di inviare un&#39;e-mail. Per ogni tentativo, verrà utilizzato un messaggio all&#39;ora di credito. Di conseguenza, le prestazioni della campagna di marketing avranno un impatto significativo.

Pertanto, il &quot;rispetto delle quote&quot; non è solo un problema di configurazione, ma può anche essere collegato alla reputazione. È importante analizzare i messaggi di errore nel registro [](../../production/using/monitoring-processes.md#smtp-errors-per-domain)SMTP.

Per ulteriori informazioni sulla configurazione MX, consulta [questa sezione](../../installation/using/email-deliverability.md#mx-configuration).

## Stesso messaggio di errore per un ISP {#same-error-for-an-isp}

**Perché ricevo sempre lo stesso messaggio di errore per un particolare ISP?**

Se si riceve sempre lo stesso messaggio di errore per un ISP, l&#39;e-mail o l&#39;IP potrebbe essere stato rilevato come difettoso dal provider di servizi Internet. Eseguite le seguenti raccomandazioni:
* Verificate se ricevete una percentuale elevata di errori collegati a indirizzi e-mail inesistenti (errori **utente sconosciuti** ).
* Aggiornare i moduli di iscrizione per rilevare eventuali errori nei nomi di dominio immessi (ad esempio: gmaul.com o yaho.com).
* Se noti degli errori che indicano che i messaggi sono dichiarati come spam o che i messaggi sono costantemente bloccati, prova ad escludere i destinatari che non hanno aperto o fatto clic in uno dei tuoi messaggi negli ultimi 12 mesi dalla destinazione.

Se il problema persiste, contatta i servizi commerciali o di recapito, Adobe Campaign Client Care o il supporto Adobe Campaign.

## Lista nera e quarantena {#blacklisting-versus-quarantine}

* **Qual è la differenza tra un indirizzo e-mail inserito in blacklist e un indirizzo e-mail in quarantena?**

   * Lo stato **[!UICONTROL Blacklisted]** è il risultato di un ciclo di feedback (quando una persona segnala un messaggio come spam).

   * Lo stato **[!UICONTROL Quarantined]** è il risultato di un rimbalzo morbido o duro.
   Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-blacklisting).

* **Cosa significano i diversi motivi di errore di quarantena?**

   I motivi possibili sono 10: non definito, utente sconosciuto, dominio non valido, indirizzo inserito in blacklist, rifiutato, errore ignorato, non raggiungibile, account disabilitato, cassetta postale piena, non connesso.

   Per ulteriori informazioni, consulta [Informazioni sulla gestione](../../delivery/using/understanding-quarantine-management.md)della quarantena.

## Senza blacklist {#unblacklisting}

* **Uno dei miei destinatari è stato inserito in blacklist per errore. Come posso cancellarli in modo da poter iniziare a inviarli nuovamente?**

   * Vai a **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]**.
   * Nei dettagli del record corrispondente, impostare il valore del **[!UICONTROL Status]** campo su **[!UICONTROL Valid]**.
   * Salvare il record.

* **Come posso sapere se uno dei miei IP è in lista nera? Come posso rimuovere la blacklist dei miei IP?**

   Per verificare se l&#39;indirizzo IP è inserito in una blacklist, potete usare diversi siti Web per verificarlo:
   * [https://mxtoolbox.com/](https://mxtoolbox.com/)
   * [https://whatismyipaddress.com/blacklist-check](https://whatismyipaddress.com/blacklist-check)
   * [https://www.blacklistalert.org/](https://www.blacklistalert.org/)
   In genere, il risultato della verifica dell&#39;indirizzo IP restituirà un elenco contenente i dettagli della blacklist e il nome del sito Web che ha inserito in blacklist l&#39;indirizzo IP.

   Facendo clic sul collegamento corrispondente, potete accedere ai dettagli del sito Web. Quindi, potete richiedere che il vostro sito Web venga cancellato dal sito Web che ha inserito in blacklist l&#39;indirizzo IP.

   >[!NOTE]
   >
   >Il processo di eliminazione può variare a seconda del sito Web. Alcuni siti richiedono la creazione di un account, mentre altri richiedono solo l’indirizzo IP.

## Best practice {#best-practices}

Di seguito sono riportate alcune best practice che possono aiutare a identificare e risolvere i problemi di recapito.

### Identificare un problema di recapito {#identify-deliverability-issue}

I seguenti elementi possono attirare la vostra attenzione:

* Metriche di posta elettronica o campagna: annulla sottoscrizione, denuncia e/o tassi di rimbalzo sono più alti del solito.
* Attività utente iscritto: aperture, clic e/o transazioni sono inferiori al normale.
* Gli account di sementi mostrano gli invii filtrati o non consegnati.

### Ipotefice potenziali cause {#potential-causes}

Fai le seguenti domande per identificare le possibili cause del problema di recapito:

* Si è verificato un recente cambiamento nella segmentazione degli elenchi?
* Sono state acquisite nuove origini dati?
* Ho inviato accidentalmente un file di quarantena?
* Il problema potrebbe essere dovuto al contenuto del mio messaggio?
* Invio spesso di posta abbastanza per mantenere gli IP caldi?
* Sto segmentando i miei messaggi per attività/coinvolgimento, o sto inviando file completi?
* Qual è il segmento &quot;sicuro&quot; del mio file in termini di aggiornamento?
* Esistono strategie di riattivazione e riconferma per segmenti non definiti sicuri?

### Risolvere il problema {#address-issue}

**Reclami**

I reclami sono definiti dagli abbonati che **segnalano l&#39;e-mail come spam** premendo il pulsante corrispondente dalla loro inbox.

Se il problema di consegna è stato causato da reclami:
* È necessario cercare di determinare il motivo per cui i destinatari si lamentano.
* Potreste anche decidere di spostare il collegamento per l’annullamento della sottoscrizione nella parte superiore dell’e-mail. Questo incoraggerà gli abbonati a cancellare l&#39;iscrizione invece di lamentarsi con il pulsante dello spam.

I mittenti possono ricavare una serie di informazioni dai loro reclami relativi al ciclo di [feedback](../../delivery/using/technical-recommendations.md#feedback-loop) :
* È importante evitare i dati e cercare i pattern in cose come l&#39;origine di consenso, per quanto tempo l&#39;indirizzo è stato sottoscritto, o anche alcune caratteristiche demografiche comportamentali.
* I reclami possono spesso identificare un&#39;origine dati o un segmento rischiosi all&#39;interno del file. Rischioso è definito come la maggior parte delle probabilità di lamentarsi, che può danneggiare la reputazione, e, a sua volta, le tariffe inbox.

I reclami provengono anche dagli abbonati che semplicemente non desiderano più ricevere e-mail:
* Ciò può essere dovuto spesso a messaggi in eccesso, alla percezione da parte degli abbonati del messaggio, al fatto che non si aspettavano il messaggio o che non si ricorderebbero di aver acconsentito al consenso.
* È inoltre importante eseguire un audit per garantire che tutti i punti di raccolta siano chiari e che nei punti di acquisizione non siano presenti caselle di controllo preselezionate.
* È inoltre necessario inviare un messaggio e-mail di benvenuto quando gli abbonati scelgono di impostare il tono e spiegare la frequenza con cui possono ricevere e-mail dall&#39;utente.

**Validità dei dati**

**I rimbalzi** forti si verificano quando si invia a un **indirizzo** non consegnabile presso un ISP. Un indirizzo può non essere recapitato per diversi motivi, ad esempio:
* Indirizzo con errore ortografico. Questo problema può essere risolto con un servizio di convalida dei dati in tempo reale, o richiedendo una scelta confermata prima di inviare e-mail di marketing a tale indirizzo.
* Elenco o origine dati non valida. Se proviene da una nuova origine, controlla in che modo gli indirizzi sono stati raccolti e verifica che sia presente l&#39;autorizzazione.
* Invio a un indirizzo che era in una volta attivo, ma che è stato chiuso o terminato dopo un periodo di inattività.

**Coinvolgimento**

Oltre ai reclami e alla validità dei dati, gli ISP si stanno concentrando più che mai sull&#39;impegno **** positivo per prendere decisioni sulla consegna. Stanno cercando di vedere se i vostri abbonati stanno aprendo le vostre e-mail, o se le stanno cancellando senza leggerle. Poiché non condividono questi dati con i mittenti, dobbiamo utilizzare le informazioni disponibili e tradurre aperture/clic/transazioni come coinvolgimento.

Come parte della manutenzione continua della reputazione, è importante comprendere in che modo gli abbonati coinvolti si trovano nell&#39;elenco e sviluppare una gerarchia **dei rischi di** recency per gli abbonati su ciascun file. Recency è definita come ultima data di apertura/clic/transazione o registrazione. Questo intervallo di tempo può essere diverso per verticale. Per eseguire questa operazione:

1. Determinare segmenti attivi (&quot;sicuri&quot;) per ogni verticale. Si tratta in genere di abbonati che sono stati attivi negli ultimi 3-6 mesi.
1. Ridurre la frequenza agli inattivi.
1. Crea una serie di [ri-coinvolgimento](../../delivery/using/re-engagement-best-practices.md) per ridurre i rischi. Di solito, questi sono 6-9 mesi senza impegno.
1. Sviluppare una campagna di riconferma per inattivi a rischio più elevato. Generalmente si tratta di utenti che non hanno mai partecipato a un’e-mail per 9-12 mesi.
1. Infine, impostate una regola di rilascio e rimuovete gli utenti che non hanno aperto le e-mail nei &#39;x&#39; mesi. In genere consigliamo 12 mesi, ma questo può variare in base al ciclo di vendita e di acquisto.
