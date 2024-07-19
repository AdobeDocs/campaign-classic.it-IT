---
product: campaign
title: Best practice di interazione con Adobe Campaign Classic
description: Questa sezione presenta l’approccio best practice per gestire il modulo di interazione in Adobe Campaign Classic
feature: Interaction, Offers
audience: interaction
content-type: reference
topic-tags: interaction-overview
exl-id: 98413cde-50c9-416c-8316-85837f724c27
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# Best practice di interazione{#interaction-best-practices}



## Raccomandazioni generali {#general-recommendations}

Questa sezione descrive l’approccio best practice per gestire il modulo di interazione in Adobe Campaign Classic, con regole di idoneità, filtri predefiniti, attività del flusso di lavoro e opzioni del database.

L’interazione in Adobe Campaign richiede un’attenta gestione per funzionare in modo efficiente. È necessario trovare un equilibrio tra il numero di contatti e il numero di categorie e di offerte di offerta. Se tali fattori non vengono gestiti attentamente, l’istanza di Adobe Campaign potrebbe riscontrare dei problemi.

### Implementazione {#implementation}

Di seguito sono elencati gli elementi importanti da tenere presenti durante l’implementazione e la configurazione delle interazioni.

* Per il motore batch (in genere utilizzato nelle comunicazioni in uscita come le e-mail), la velocità effettiva è il problema principale, in quanto è possibile gestire più contatti contemporaneamente. Il collo di bottiglia tipico è rappresentato dalle prestazioni del database.
* Il vincolo principale per il motore unitario (in genere utilizzato nelle comunicazioni in entrata come un banner su un sito web) è la latenza, in quanto qualcuno si aspetta una risposta. Il collo di bottiglia tipico è rappresentato dalle prestazioni della CPU.
* Il design del catalogo delle offerte ha un impatto enorme sulle prestazioni di Adobe Campaign Classic.
* Quando ci sono molte offerte, suddividile in diversi cataloghi di offerte.

### Regole di idoneità {#eligibility-rules}

Di seguito sono elencate alcune best practice relative alle regole di idoneità.

* Semplificare le regole. La complessità delle regole influisce sulle prestazioni in quanto estende la ricerca. Una regola complessa è una regola con più di cinque condizioni.
* Per migliorare le prestazioni, le regole possono essere suddivise in filtri predefiniti distinti condivisi tra più offerte.
* Posiziona le regole di categoria di offerta più restrittive nella posizione più alta possibile nella struttura. In questo modo, escluderanno prima il maggior numero di contatti, riducendo il numero di destinazione e impedendo che vengano elaborati da ulteriori regole.
* Metti le regole più costose in termini di tempo o di elaborazione nella parte inferiore dell’albero. In questo modo, queste regole verranno eseguite solo sul pubblico di destinazione rimanente.
* Inizia da una categoria specifica per evitare di eseguire la scansione dell’intera struttura.
* Per risparmiare tempo di elaborazione, precalcolare gli aggregati anziché creare regole complesse con join. A questo scopo, prova a memorizzare i dati dei clienti in una tabella di riferimento che può essere cercata all’interno delle regole di idoneità.
* Utilizza un numero minimo di pesi per limitare il numero di query.
* Si consiglia di avere un numero limitato di offerte per spazio dell’offerta. In questo modo è possibile recuperare più rapidamente le offerte in qualsiasi spazio.
* Utilizza gli indici, in particolare nelle colonne di ricerca utilizzate di frequente.

### Tabella delle proposte {#proposition-table}

Di seguito sono elencate alcune best practice relative alla tabella della proposta.

* Utilizza un numero minimo di regole per velocizzare l’elaborazione.
* Limita il numero di record nella tabella della proposta: conserva solo i record necessari per tenere traccia del suo aggiornamento di stato e di ciò che è necessario per le regole, quindi archiviali in un altro sistema.
* Esegui una manutenzione intensiva del database sulla tabella della proposta, ad esempio ricompila indici o ricrea tabella.
* Limita il numero di proposte richieste per target. Non impostare più di quello che si sta per utilizzare.
* Evita il più possibile i join nei criteri delle regole.

## Suggerimenti per la gestione delle offerte {#tips-managing-offers}

Questa sezione contiene consigli più dettagliati sulla gestione delle offerte e sull’utilizzo del modulo di interazione in Adobe Campaign Classic.

### Utilizzo di più spazi dell’offerta in una consegna e-mail {#multiple-offer-spaces}

Quando si includono le offerte nelle consegne, queste vengono generalmente selezionate a monte nel flusso di lavoro di Campaign tramite un’attività Enrichment (o un’altra attività simile).

Quando selezioni le offerte in un’attività di arricchimento, puoi scegliere quale spazio di offerta utilizzare. Tuttavia, indipendentemente dallo spazio dell’offerta selezionato, il menu di personalizzazione della consegna dipende dallo spazio dell’offerta configurato nella consegna.

Nell&#39;esempio seguente, lo spazio dell&#39;offerta selezionato nella consegna è **[!UICONTROL Email (Environment - Recipient)]**:

![](assets/Interaction-best-practices-offer-space-selected.png)

Se lo spazio dell’offerta selezionato nella consegna non dispone di una funzione di rendering HTML configurata, non verrà visualizzato nel menu della consegna e non sarà disponibile per la selezione. Anche in questo caso, è indipendente dallo spazio delle offerte selezionato nell’attività Enrichment.

Nell’esempio seguente, la funzione di rendering HTML è disponibile nell’elenco a discesa perché lo spazio dell’offerta selezionato nella consegna ha una funzione di rendering:

![](assets/Interaction-best-practices-HTML-rendering.png)

Questa funzione inserisce il codice seguente: `<%@ include proposition="targetData.proposition" view="rendering/html" %>`.

Quando si seleziona la proposta, il valore dell&#39;attributo **[!UICONTROL view]** è il seguente:
* &quot;rendering/html&quot;: rendering html. Utilizza la funzione di rendering HTML.
* &quot;offer/view/html&quot;: contenuto html. Non utilizza la funzione di rendering HTML. Include solo il campo HTML.

Se includi più spazi di offerta in una singola consegna e-mail e alcuni di essi dispongono di funzioni di rendering, è necessario ricordare quali offerte utilizzano quali spazi di offerta e quali spazi di offerta dispongono di funzioni di rendering.

Di conseguenza, per evitare problemi, si consiglia di definire una funzione di rendering HTML per tutti gli spazi dell’offerta, anche se lo spazio dell’offerta richiede solo contenuto HTML.

### Impostazione della classificazione nella tabella del registro delle proposte {#rank-proposition-log-table}

Gli spazi dell’offerta consentono di memorizzare i dati nella tabella delle proposte quando queste vengono generate o accettate:

![](assets/Interaction-best-practices-offer-space-storage.png)

Tuttavia, questo si applica solo alle interazioni in entrata.

È inoltre possibile memorizzare dati aggiuntivi nella tabella della proposta quando si utilizzano interazioni in uscita e anche quando si utilizzano offerte in uscita senza il modulo di interazione.

Qualsiasi campo della tabella temporanea del flusso di lavoro il cui nome corrisponde a un nome di campo della tabella della proposta viene copiato nello stesso campo della tabella della proposta.

Ad esempio, quando selezioni manualmente un’offerta (senza interazione) in un Arricchimento, i campi standard sono definiti come segue:

![](assets/Interaction-best-practices-manual-offer-std-fields.png)

È possibile aggiungere altri campi, ad esempio un campo @rank:

![](assets/Interaction-best-practices-manual-offer-add-fields.png)

Poiché nella tabella della proposta è presente un campo denominato @rank, il valore nella tabella temporanea del flusso di lavoro verrà copiato.

Per ulteriori informazioni sulla memorizzazione di campi aggiuntivi nella tabella delle proposte, consulta [Integrazione di un&#39;offerta tramite un flusso di lavoro](../../interaction/using/integrating-an-offer-via-a-workflow.md#storing-offer-rankings-and-weights).

Per le offerte in uscita con interazione, questo è utile quando sono selezionate più offerte e vuoi registrare in quale ordine verranno visualizzate in un’e-mail.

Puoi anche memorizzare metadati aggiuntivi direttamente nella tabella della proposta, ad esempio il livello di spesa corrente, per conservare registrazioni storiche sulla spesa nel momento in cui sono state generate le offerte.

Quando si utilizza l’interazione in uscita, è possibile aggiungere il campo @rank, come nell’esempio precedente, ma il suo valore viene impostato automaticamente in base all’ordine restituito dall’interazione. Ad esempio, se utilizzi Interazione per selezionare tre offerte, nel campo @rank vengono restituiti i valori 1, 2 e 3.

Quando si utilizza l’interazione e si selezionano manualmente le offerte, l’utente può combinare entrambi gli approcci. Ad esempio, l’utente può impostare manualmente il campo @rank su 1 per l’offerta selezionata manualmente e utilizzare un’espressione come &quot;1 + @rank&quot; per le offerte restituite da Interaction. Supponendo che Interaction selezioni tre offerte, le offerte restituite da entrambi gli approcci saranno classificate da 1 a 4:

![](assets/Interaction-best-practices-manual-offer-combined.png)

### Estensione dello schema nms:offer {#extending-nms-offer-schema}

Quando estendi lo schema nms:offer, accertati di seguire la struttura preconfigurata già impostata:
* Definire un nuovo campo per l&#39;archiviazione del contenuto in `<element name="view">`.
* Ogni nuovo campo deve essere definito due volte. Una volta come campo XML normale e una volta come campo XML CDATA con &quot;_jst&quot; aggiunto al nome. Ad esempio:

  ```
  <element label="Price" name="price" type="long" xml="true"/>
  <element advanced="true" label="Script price" name="price_jst" type="CDATA" xml="true"/>
  ```

* Tutti i campi che contengono URL da tracciare devono essere posizionati in `<element name="trackedUrls">`, che si trova in `<element name="view" >`.
