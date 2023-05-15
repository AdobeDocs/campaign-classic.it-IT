---
product: campaign
title: Risoluzione dei problemi relativi agli SMS
description: Scopri come risolvere i problemi del canale SMS
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: SMS
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '2744'
ht-degree: 0%

---

# Risoluzione dei problemi SMS {#troubleshooting-sms}



## Conflitto tra account esterni diversi {#external-account-conflict}

Se l’istanza dispone di più account esterni SMS, è necessario verificare che i problemi non siano causati da un conflitto tra account esterni.

Adobe Campaign tratta gli account esterni come entità non collegate.

Se disponi di più account, segui questa procedura per isolare l’account esterno causando problemi:

1. Disattiva tutti gli account esterni.
1. Abilita un account esterno.
1. Provate a riprodurre il problema.
1. Se il problema iniziale non viene sempre visualizzato, eseguire un numero ragionevole di tentativi prima di concludere.
1. Se il problema non viene visualizzato con quel singolo account, disattivalo e riavvia al passaggio 2 sull&#39;account successivo.

Una volta verificato singolarmente ogni account, ci sono 2 possibili scenari:

* **Il problema è apparso su uno o più account**

   In questo caso, puoi applicare altre procedure di risoluzione dei problemi su ciascun account singolarmente. È consigliabile disattivare altri account durante la diagnosi di un account per ridurre il traffico di rete e il numero di registri.

* **Il problema non veniva visualizzato quando un solo account era attivo in qualsiasi momento**

   Hai un conflitto tra account. Come accennato in precedenza, Adobe Campaign tratta gli account singolarmente, ma il fornitore può trattarli come un singolo account.

   * Stai utilizzando diverse combinazioni di login/password tra tutti i tuoi account.
Sarà necessario contattare il provider per diagnosticare potenziali conflitti dalla loro parte.

   * Alcuni account esterni condividono la stessa combinazione di login/password.
Il provider non ha modo di sapere da quale account esterno il `BIND PDU` proviene da, quindi tratta tutte le connessioni da account multipli come una singola. Avrebbero potuto instradare casualmente MO e SR nei due account, causando problemi.
Se il provider supporta più codici brevi per la stessa combinazione di login/password, dovrai chiedere loro dove inserire quel codice breve nel `BIND PDU`. Tieni presente che questa informazione deve essere inserita nel `BIND PDU`e non in `SUBMIT_SM`, dal `BIND PDU` è l’unico posto che consentirà di indirizzare correttamente gli M0.
Consulta la sezione [Informazioni in ciascun tipo di PDU](sms-protocol.md#information-pdu) sezione precedente per sapere quale campo è disponibile nel `BIND PDU`, in genere si aggiunge il codice breve in `address_range`, ma ciò richiede un supporto speciale da parte del provider. Contattateli per sapere come si aspettano di indirizzare più codici brevi in modo indipendente.
Adobe Campaign supporta la gestione di più codici brevi sullo stesso account esterno.

## Problema con l’account esterno in generale {#external-account-issues}

* Verifica se il connettore è stato modificato di recente e da chi (controlla Account esterni come gruppo).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Controlla (nella directory /postupgrade) se il sistema è stato aggiornato e quando
* Verifica se eventuali pacchetti che interessano SMS potrebbero essere stati aggiornati di recente (/var/log/dpkg.log).

## Problema con il mid-sourcing (in hosting){#issue-mid-sourcing}

* Se il problema si verifica in un ambiente di mid-sourcing, assicurati che i log di consegna e quelli generali siano creati e aggiornati correttamente sul server di mid-sourcing. Se non è così, non è un problema SMS.

* Se tutto funziona sul server mid e gli SMS vengono inviati correttamente, ma l’istanza di marketing non viene aggiornata correttamente, potresti riscontrare un problema di sincronizzazione mid.

## Problema durante la connessione al provider {#issue-provider}

* Se la `BIND PDU` restituisce un valore diverso da zero `command_status` , chiedi al provider ulteriori informazioni.

* Verificare che la rete sia configurata correttamente in modo che sia possibile effettuare la connessione TCP al provider.

* Chiedi al provider di verificare di aver aggiunto correttamente gli IP all&#39;inserire nell&#39;elenco Consentiti dell&#39;istanza Adobe Campaign.

* Controlla **Account esterno** impostazioni. Chiedi al provider il valore dei campi.

* Se la connessione ha esito positivo ma è instabile, controlla il [Problema con connessioni instabili](troubleshooting-sms.md#issues-unstable-connection) sezione .

* In caso di problemi di connessione difficili da diagnosticare, un&#39;acquisizione di rete può fornire informazioni. Assicurati che l&#39;acquisizione di rete venga eseguita simultaneamente mentre il problema appare per essere analizzato in modo efficiente. Si dovrebbe anche notare l&#39;ora esatta in cui appare il problema.

## Problemi di connessione instabile {#issues-unstable-connection}

Una connessione è considerata instabile se si verifica uno dei seguenti casi:

* La connessione dura meno di 1 ora. Le connessioni del trasmettitore Adobe Campaign Classic sono un&#39;eccezione a causa del modo in cui funziona l&#39;MTA Adobe Campaign Classic.

* Il provider invia `UNBIND PDU`s.

* `enquire_link` si verifica un timeout sul lato Adobe Campaign o sul lato provider. Potresti vedere `ENQUIRE_LINK_RESP` con un codice di errore diverso da zero in questo caso.

* Ci sono molti `BIND PDU`s. Non ci dovrebbero essere più di pochi durante un giorno, a seconda del numero di connessioni. Più di 1 PDU BIND all&#39;ora dovrebbe essere un avviso.

Come risolvere i problemi di stabilità della connessione:

* Le connessioni instabili raramente sono la causa principale, spesso è il risultato di un altro problema che innesca una disconnessione. Trovare la causa principale è la priorità.

* Abilita tracce SMPP dettagliate. Sarà necessario che visualizzino cosa sta succedendo al riavvio della connessione.

* Se il provider invia `BIND PDU`s, qualcosa potrebbe essere sbagliato. Chiedi al provider perché `UNBING` viene inviato.

* L&#39;acquisizione di una rete è talvolta l&#39;unico modo per vedere come viene chiusa la connessione.

* Se il provider chiude le connessioni inviando un `TCP FIN` o `TCP RST packet`, chiedi ulteriori informazioni al tuo provider.

* Se il provider chiude la connessione dopo l’invio di un errore di pulizia, ad esempio `DELIVER_SM_RESP` con un codice di errore, devono correggere il connettore in caso contrario, in modo da impedire la trasmissione di altri tipi di messaggi e attivare la limitazione MTA. Questo è particolarmente importante nella modalità ricetrasmettitore dove la chiusura della connessione ha un impatto sia sul MT che sul SR.

## Problema durante l’invio di un MT (SMS regolare inviato a un utente finale){#issue-MT}

* Verificare che la connessione sia stabile. Una connessione SMPP deve rimanere in attività per almeno 1 ora in modo continuo, ad eccezione dei trasmettitori su Adobe Campaign Classic. Vedi la sezione [Problema con connessioni instabili](sms-protocol.md#issues-unstable-connection).

* Se il riavvio dell&#39;MTA fa sì che l&#39;invio di MT funzioni di nuovo per un breve periodo di tempo, probabilmente si ha la limitazione a causa di una connessione instabile. Vedi la sezione [Problema con connessioni instabili](troubleshooting-sms.md#issues-unstable-connection).

* Verificare che il log ampio sia presente e nello stato corretto con le date corrette. In caso contrario, potrebbe trattarsi di un problema di preparazione della consegna o della consegna.

* Verifica che l’MTA elabori effettivamente il messaggio. Se non è così, potrebbe non essere un problema SMS.

* Verifica che il connettore SMS sia effettivamente associato all’apparecchiatura del provider. Chiedi al provider un feedback per assicurarsi che tutti i sistemi comunichino correttamente. Vedi `BIND_TRANSMITTER` e `BIND_TRANSCEIVER PDU`s per informazioni sul processo di binding. Potrebbe essere necessario abilitare tracce SMPP per una corretta risoluzione dei problemi.

* Con le tracce SMPP abilitate, controlla che il `SUBMIT_SM PDU` contiene le informazioni corrette.

* Verifica che il provider risponda con un `SUBMIT_SM_RESP PDU` con un valore &quot;OK&quot; (codice 0). Assicurati che la PDU arrivi con un ritardo ragionevole: qualsiasi valore superiore a 1 secondo deve essere discusso con il provider, di solito arriva in meno di 100 ms.

* Se tutti questi passaggi funzionano, puoi essere sicuro che il problema sia dal lato del fornitore. Dovranno risolvere i problemi sulla loro piattaforma.

* Se funziona ma la velocità effettiva è incoerente, prova a regolare la finestra di invio e ad abbassare la velocità effettiva MT. Per regolarlo, dovrai collaborare con il provider. Adobe Campaign può inviare i messaggi molto rapidamente, in modo che possano verificarsi problemi di prestazioni sulle apparecchiature del fornitore.

## MT sono duplicati (lo stesso SMS viene inviato più volte di seguito){#duplicated-MT}

I duplicati sono spesso causati da nuovi tentativi. È normale avere duplicati quando si riprovano i messaggi, invece di rimuovere la causa principale dei nuovi tentativi.

* Se vedi duplicati inviati esattamente 60 secondi di distanza, probabilmente si tratta di un problema sul lato del provider, non inviano un `SUBMIT_SM_RESP` abbastanza rapidamente.

* Se ne visualizzano molti `BIND/UNBIND`, hai una connessione instabile. Consulta la sezione[Problema con connessioni instabili](troubleshooting-sms.md#issues-unstable-connection) per le soluzioni prima di tentare di risolvere i problemi dei messaggi duplicati.

Riduzione della quantità di duplicati in caso di nuovi tentativi:

* Abbassa la finestra di invio. La finestra di invio deve essere sufficientemente grande da coprire `SUBMIT_SM_RESP` latenza. Il suo valore rappresenta il numero massimo di messaggi che possono essere duplicati se si verifica un errore mentre la finestra è piena.

## Problema durante l’elaborazione dell’SR (ricevute di consegna) {#issue-process-SR}

* Sarà necessario che le tracce SMPP siano abilitate per eseguire qualsiasi tipo di risoluzione dei problemi SR.

* Controlla che la `DELIVER_SM PDU` viene dal fornitore e che è ben formato.

* Verifica che Adobe Campaign risponda con successo `DELIVER_SM_RESP PDU` in modo tempestivo. Su Adobe Campaign Classic, questo garantisce che l&#39;SR sia stato inserito nel `providerMsgId` tabella per l’elaborazione differita da parte del processo SMS.

Se la `DELIVER_SM PDU` non è stato riconosciuto correttamente, è necessario verificare quanto segue:

* Controlla regex relativo all’estrazione dell’id e all’elaborazione degli errori nel **Account esterno**. Potrebbe essere necessario convalidarli rispetto al contenuto della `DELIVER_SM PDU`.

* Verifica che gli errori siano correttamente forniti nel `broadLogMsg` tabella.

Se la `DELIVER_SM PDU` è stato riconosciuto dal connettore SMPP esteso Adobe Campaign Classic ma l&#39;ampio registro non è aggiornato correttamente, controlla il processo di riconciliazione ID descritto nella sezione [Voci MT, SR e broadlog corrispondenti](sms-protocol.md#matching-mt).

Se hai corretto tutto ma alcuni SR non validi si trovano ancora nei buffer del provider, puoi ignorarli utilizzando l&#39;opzione &quot;Numero di riconoscimenti ID non valido&quot;. Questo deve essere utilizzato con cura e reimpostato a 0 il più rapidamente possibile dopo che i buffer sono puliti.

## Problema durante l’elaborazione di MO (e blacklist/risposta automatica){#issue-process-MO}

* Abilitare le tracce SMPP durante i test. Se non abiliti TLS, devi eseguire un&#39;acquisizione di rete durante la risoluzione dei problemi di MO per verificare che le PDU contengano le informazioni corrette e siano formattate correttamente.

* Durante l&#39;acquisizione del traffico di rete o l&#39;analisi delle tracce SMPP, assicurati di catturare l&#39;intera conversazione con il MO e la sua risposta MT se è configurata una risposta.

* Se il MO (`DELIVER_SM PDU`) non viene visualizzata nelle tracce, il problema è dal lato del provider. Dovranno risolvere i problemi sulla loro piattaforma.

* Se la `DELIVER_SM PDU` viene visualizzato, verifica che Adobe Campaign lo riconosca con successo `DELIVER_SM_RESP PDU` (codice 0). Questo RESP garantisce che tutta la logica di elaborazione sia stata applicata da Adobe Campaign (risposta automatica e /elenco Bloccati). In caso contrario, cerca un messaggio di errore nei log del processo SMS.

* Se le risposte automatiche sono abilitate, controlla che la `SUBMIT_SM` è stato inviato al provider. In caso contrario, è garantito di trovare un messaggio di errore nei log del processo SMS.

* Se la `SUBMIT_SM MT PDU` contenente la risposta si trova nelle tracce ma l&#39;SMS non arriva al telefono cellulare, sarà necessario contattare il fornitore per assistenza nella risoluzione dei problemi.

## Problema durante la preparazione della consegna che non esclude i destinatari in quarantena (messi in quarantena dalla funzione di risposta automatica) {#issue-delivery-preparation}

* Verifica che il formato del numero di telefono sia esattamente lo stesso nella tabella di quarantena e nel registro di consegna. In caso contrario, fai riferimento a [sezione](sms-protocol.md#automatic-reply) in caso di problemi con il prefisso più del formato del numero di telefono internazionale.

* Controlla i codici brevi. Le esclusioni possono verificarsi se il codice breve del destinatario è lo stesso definito nell’account esterno o se è vuoto (vuoto = eventuale codice scorrevole). Se viene utilizzato un solo codice breve per l’intera istanza di Adobe Campaign, è più facile lasciare tutto **codice breve** campi vuoti.

## Problemi di codifica {#encoding-issues}

**Passaggio 1: Contatta il provider**

Contattateli e scoprite cosa c&#39;è che non va. Dovrebbero essere in grado di dirvi se il problema è dalla loro parte o da Adobe Campaign. Se il problema è in Adobe Campaign, dovrebbero essere in grado di dirvi esattamente quale campo non è corretto.

**Passaggio 2: Scopri cosa c&#39;è nel tuo messaggio**

Unicode consente molte varianti per caratteri simili e Adobe Campaign non può gestirli tutti.

La fonte più comune di problemi è una copia-incolla da un elaboratore di testi, che cambia i caratteri soliti in versioni tipograficamente corrette: spazi modificati in spazi unificatori, virgolette doppie modificate in virgolette di apertura e chiusura, meno segni modificati in vari tipi di trattini, ecc.

Non copiare e incollare il messaggio durante il test, scrivilo sempre direttamente nell’interfaccia.

Con esadecimale, è possibile distinguere tra caratteri simili. Una L minuscola, una I, O, 0 maiuscola, tutti i diversi tipi di virgolette, codifiche non latine o anche diversi tipi di spazi possono avere lo stesso aspetto o addirittura non essere visualizzati affatto.

Per convertire unicode in esadecimale, è possibile utilizzare strumenti online come [Convertitore di codice Unicode](https://r12a.github.io/app-conversion/) sito web. Digita il testo, accertati che non vi siano PII, ad esempio i numeri di telefono e fai clic su **Converti**. Verranno visualizzati i valori esadecimali nella parte inferiore (zona UTF-32).

Quando si aprono i ticket per problemi di codifica, sia con il provider che con [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), includi sempre una versione esadecimale di ciò che digiti e di ciò che vedi.

**Passaggio 3: Sapere cosa inviare**

Determina la codifica da utilizzare ed effettua una ricerca online per la relativa tabella di caratteri. Verifica che i caratteri che intendi inviare siano effettivamente disponibili nella tabella codici di destinazione. Controlla che la `data_coding` Il campo è corretto e corrisponde alle aspettative dell’utente e del provider.

**Passaggio 4: Sapere cosa hai effettivamente inviato**

Sarà necessario l&#39;output di debug del connettore per vedere esattamente quali byte si inviano al provider. I problemi di codifica vengono visualizzati in `SUBMIT_SM PDU`s, quindi assicurati di catturarli. Invia messaggi molto distinti che sono facili da trovare nel registro.

Invia diversi tipi di caratteri speciali durante il test. Ad esempio, la codifica GSM7 presenta caratteri estesi molto distinti nella forma esadecimale, facili da individuare in quanto non compaiono in nessun’altra codifica.

## Elementi da includere nella comunicazione su un problema SMS {#element-include}

Ogni volta che cerchi assistenza su un problema SMS, sia che si tratti di aprire un ticket di supporto ad Adobe Campaign, al provider SMS, o qualsiasi tipo di comunicazione sul problema, dovrai includere le seguenti informazioni per essere sicuro che sarà correttamente qualificato. Problemi qualificati sono fondamentali per risolvere i problemi più rapidamente.

* **Abilitare messaggi SMPP dettagliati** quando appare il problema. La maggior parte dei problemi degli SMS sono impossibili da risolvere senza questo.

* Se il problema è correlato al traffico SMS, contatta prima il provider . La loro piattaforma è più adatta per una diagnosi efficiente dei problemi di traffico SMS in tempo reale.

* Includi una breve ma fattuale descrizione del problema.

* Includi una descrizione del risultato previsto.

* Includi il feedback dal provider.

* Includi registri e/o acquisizioni di rete rilevanti. Durante l&#39;acquisizione, assicurati di riprodurre il problema durante l&#39;acquisizione.

* Se includi log, tracce o acquisizioni, individua la posizione esatta nel file quando viene visualizzato il problema.

* Se fai riferimento a messaggi, PDU o registri, specifica chiaramente la marca temporale per facilitarne la ricerca.

* Prova a riprodurre il problema in un ambiente di test. Se non sei sicuro di un&#39;impostazione, prova a utilizzarla nell&#39;ambiente di test e controlla il risultato con le tracce SMPP. Di solito è meglio segnalare i problemi replicati negli ambienti di test piuttosto che segnalare direttamente i problemi negli ambienti di produzione.

* Includi eventuali modifiche o modifiche apportate sulla piattaforma. Inoltre, includi qualsiasi modifica che il fornitore potrebbe aver apportato sul suo lato.

### Acquisizione in rete {#network-capture}

Non è sempre necessaria un&#39;acquisizione di rete, in genere i messaggi SMPP sono sufficienti. Di seguito sono riportate alcune linee guida che consentono di determinare se è necessaria un’acquisizione di rete:

* Problemi di connessione, ma i messaggi non visualizzati non mostrano alcun `BIND_RESP PDU`.

* Disconnessioni non spiegate senza messaggio di errore, il comportamento abituale del connettore quando rileva un errore di protocollo di basso livello.

* Il provider si lamenta del processo di disconnessione/disconnessione.

* Problemi di codifica nei campi TLV facoltativi.

* Si sospetta che il traffico sia misto tra diverse connessioni.

In tutte le altre situazioni, prova ad analizzare prima i messaggi SMPP dettagliati e richiedi un&#39;acquisizione di rete solo se mancano informazioni nei log dettagliati.

In alcuni casi, l’acquisizione del traffico di rete non è necessaria. Di seguito sono riportate le situazioni più comuni:

* TLS abilitato: Per definizione, il traffico TLS è crittografato e non può essere acquisito.

* Problemi di prestazioni: I registri contengono tutte le informazioni necessarie per tracciare i problemi di prestazioni.

* Problemi di temporizzazione (`retry timing`, `enquire_link` periodo, limite di velocità effettiva, ecc.)

* Analisi ed elaborazione SR: i registri verbose offrono molto più contesto e una presentazione migliore.

* Elaborazione MO (risposte automatiche, quarantena).

* Errori che non coinvolgono il traffico SMPP effettivo: Preparazione della consegna, problemi API del Centro messaggi, problemi del flusso di lavoro, ecc.

## Abilitazione delle tracce SMPP {#enabling-smpp-traces}

Il nuovo connettore supporta la registrazione estesa attraverso le tracce: SMPP. Le tracce vengono emesse nel registro MTA, non nell&#39;output standard.

**Abilitazione per account esterno (metodo preferito)**

1. In **Account esterno**, controlla **Abilita tracce SMPP dettagliate nel file di registro**.
1. Attendi 10 minuti per consentire al server di ricaricare account esterni.

Dovrebbe essere attivo ora.

**Abilitazione nella configurazione**

In `config-instance.xml` imposta i seguenti parametri:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Controllo del numero di connessioni aperte in un contenitore {#open-connections}

Per controllare il numero di connessioni aperte su un contenitore, è possibile utilizzare questo comando:

```
(for pid in $(ss -neopts  | sed -n ‘s/^.*:3600[ \t].*users:(([0-9A-Za-z”]*,pid=\([0-9]*\),.*$/\1/p’ | sort ); do  cat /proc/$pid/cmdline; echo  ” $pid” ;done;) | uniq --count
```

Verrà visualizzato il numero di connessioni aperte per una determinata porta. Qui stiamo usando la porta 3600.

Il risultato deve essere il seguente:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 connessioni aperte per il processo sms e 2 per bambino mta con 5 bambini.
