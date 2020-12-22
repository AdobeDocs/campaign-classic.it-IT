---
solution: Campaign Classic
product: campaign
title: Protocollo e impostazioni del connettore SMS
description: Ulteriori informazioni sul connettore SMS e come configurarlo.
audience: delivery
content-type: reference
topic-tags: configuring-channels
translation-type: tm+mt
source-git-commit: 96ad3208c792efb47097768bc779bec59d9ca313
workflow-type: tm+mt
source-wordcount: '2745'
ht-degree: 0%

---


# Risoluzione dei problemi SMS {#troubleshooting-sms}

## Conflitto tra diversi conti esterni {#external-account-conflict}

Se l&#39;istanza dispone di più account esterni SMS, è necessario verificare che i problemi non siano causati da un conflitto tra account esterni.

 Adobe Campaign tratta gli account esterni come entità non correlate.

Se disponete di più account, seguite questa procedura per isolare l&#39;account esterno causando problemi:

1. Disattiva tutti gli account esterni.
1. Abilita un account esterno.
1. Prova a riprodurre il problema.
1. Se il problema iniziale non viene sempre visualizzato, eseguite un numero ragionevole di tentativi prima di concludere.
1. Se il problema non viene visualizzato con quel singolo account, disattivatelo e riavviate fino al punto 2 dell&#39;account successivo.

Dopo aver controllato ogni account singolarmente, sono disponibili 2 possibili scenari:

* **Il problema è apparso su uno o più account**

   In questo caso, potete applicare altre procedure di risoluzione dei problemi su ciascun account singolarmente. È consigliabile disattivare altri account durante la diagnosi di un account per ridurre il traffico di rete e il numero di log.

* **Il problema non veniva visualizzato quando un solo account era attivo in qualsiasi momento**

   C&#39;è un conflitto tra account. Come già detto,  Adobe Campaign tratta gli account singolarmente, ma il fornitore può trattarli come un unico account.

   * State utilizzando diverse combinazioni di login/password tra tutti gli account.
Dovrete contattare il fornitore per diagnosticare potenziali conflitti dalla loro parte.

   * Alcuni account esterni condividono la stessa combinazione di login/password.
Il provider non ha modo di sapere da quale account esterno proviene il `BIND PDU`, quindi tratta tutte le connessioni dai diversi account come un unico account. Potrebbero aver instradato MO e SR in modo casuale nei due account, causando problemi.
Se il provider supporta più codici brevi per la stessa combinazione di login/password, dovrete chiedere loro dove inserire il codice breve nella `BIND PDU`. Notare che questa informazione deve essere inserita all&#39;interno del `BIND PDU` e non in `SUBMIT_SM`, dal momento che il `BIND PDU` è l&#39;unico luogo che consentirà di indirizzare correttamente i MO.
Vedere le [Informazioni in ogni tipo di sezione PDU](../../delivery/using/sms-protocol.md#information-pdu) sopra per sapere quale campo è disponibile nella `BIND PDU`, in genere si aggiunge il codice breve in `address_range`, ma che richiede un supporto speciale da parte del provider. Contattateli per sapere come si aspettano di indirizzare più codici brevi in modo indipendente.
 Adobe Campaign supporta la gestione di più codici brevi sullo stesso account esterno.

## Problema con l&#39;account esterno in generale {#external-account-issues}

* Verificare se il connettore è stato modificato di recente e da chi (selezionare Account esterni come gruppo).

   ```
   select saccount, (sserver ||':'||sport) as serverPort, iextaccountid, CASE WHEN N0.iactive=1 THEN 'Yes' ELSE 'No' END as "(x) Enabled",
   
   (select X1.sname from xtkoperator X1 where N0.icreatedbyid = X1.ioperatorid) as "Created By",
   
   (select X1.sname from xtkoperator X1 where N0.imodifiedbyid = X1.ioperatorid) as "Last Modified By",
   
   N0.slabel as "External Account", N0.tslastmodified as "LastModifiedDate"
   
   from nmsextaccount N0 LEFT JOIN xtkoperator X0 ON (N0.icreatedbyid=X0.ioperatorid) order by 8 DESC LIMIT 50;
   ```

* Verificare (nella directory /postupgrade) se il sistema è stato aggiornato e quando
* Verificare se eventuali pacchetti che interessano SMS potrebbero essere stati aggiornati di recente (/var/log/dpkg.log).

## Problema con il mid-sourcing (ospitato){#issue-mid-sourcing}

* Se il problema si verifica in un ambiente di mid-sourcing, accertatevi che i log di consegna e di grandi dimensioni siano creati e aggiornati correttamente sul server di mid-sourcing. Se non è così, non si tratta di un problema relativo agli SMS.

* Se tutto funziona sul server mid e gli SMS vengono inviati correttamente, ma l&#39;istanza di marketing non viene aggiornata correttamente, potrebbe verificarsi un problema di metà sincronizzazione.

## Problema durante la connessione al provider {#issue-provider}

* Se il codice `BIND PDU` restituisce un codice `command_status` diverso da zero, chiedete al provider ulteriori informazioni.

* Verificare che la rete sia configurata correttamente in modo che la connessione TCP possa essere effettuata al provider.

* Chiedete al fornitore di verificare che abbia aggiunto correttamente gli IP al inserire nell&#39;elenco Consentiti  dell&#39;istanza Adobe Campaign .

* Controllare le impostazioni di **Account esterno**. Chiedete al provider il valore dei campi.

* Se la connessione ha esito positivo ma instabile, controllare la sezione [Problema con connessioni instabili](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Se i problemi di connessione sono difficili da diagnosticare, un&#39;acquisizione di rete può fornire informazioni. Verificare che l&#39;acquisizione di rete venga eseguita simultaneamente mentre il problema appare per essere analizzato in modo efficiente. È inoltre necessario tenere presente l&#39;ora esatta in cui appare il problema.

## Problemi con connessione instabile {#issues-unstable-connection}

Una connessione è considerata instabile se si verifica una delle seguenti situazioni:

* La connessione dura meno di 1 ora. Le connessioni dei trasmettitori Adobe Campaign Classic sono un&#39;eccezione a causa del funzionamento di Adobe Campaign Classic MTA.

* Il provider invia `UNBIND PDU`s.

* `enquire_link` timeout, dal lato Adobe Campaign  o dal lato del fornitore. In questo caso è possibile che venga visualizzato `ENQUIRE_LINK_RESP` un codice di errore diverso da zero.

* Ci sono un sacco di `BIND PDU`s. Non ci dovrebbe essere più di pochi durante un giorno, a seconda del numero di connessioni. Più di 1 BIND PDU all&#39;ora dovrebbe essere un avviso.

Come risolvere i problemi di stabilità della connessione:

* Le connessioni instabili sono raramente la causa principale, è spesso il risultato di un altro problema che innesca una disconnessione. Trovare la causa principale è la priorità.

* Abilitare tracce SMPP dettagliate. Sarà necessario che visualizzino gli eventi che si verificano al riavvio della connessione.

* Se il provider invia `BIND PDU`s, potrebbe essersi verificato un errore. Chiedete al vostro fornitore perché `UNBING` viene inviato.

* A volte, l&#39;acquisizione di una rete è l&#39;unico modo per vedere in che modo la connessione viene chiusa.

* Se il provider chiude le connessioni inviando un `TCP FIN` o un `TCP RST packet`, chiedere ulteriori informazioni al provider.

* Se il provider chiude la connessione dopo l&#39;invio di un errore &quot;pulito&quot;, ad esempio `DELIVER_SM_RESP`, con un codice di errore, deve correggere il connettore in modo da impedire la trasmissione di altri tipi di messaggi e attivare la limitazione MTA. Ciò è particolarmente importante in modalità trascrivitore, dove la chiusura della connessione influisce sia sul MT che sul SR.

## Problema relativo all&#39;invio di un MT (SMS regolare inviato a un utente finale){#issue-MT}

* Verificare che la connessione sia stabile. Una connessione SMPP deve rimanere al massimo per almeno 1 ora in modo continuo, ad eccezione dei trasmettitori su Adobe Campaign Classic. Vedere la sezione [Problema con connessioni instabili](../../delivery/using/sms-protocol.md#issues-unstable-connection).

* Se il riavvio dell&#39;MTA fa funzionare nuovamente MT per un breve periodo di tempo, probabilmente si ha la limitazione a causa di una connessione instabile. Vedere la sezione [Problema con connessioni instabili](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection).

* Verificate che il registro ampio sia presente e nello stato corretto con le date corrette. In caso contrario, potrebbe trattarsi di un problema di consegna o di preparazione.

* Verificate che l&#39;MTA elabori effettivamente il messaggio. Se non è così, potrebbe non essere un problema di SMS.

* Verificare che il connettore SMS sia effettivamente associato all&#39;apparecchiatura del fornitore. Chiedete un feedback al fornitore per verificare che tutti i sistemi siano in grado di comunicare correttamente. Per informazioni sul processo di binding, vedere `BIND_TRANSMITTER` e `BIND_TRANSCEIVER PDU`s. Potrebbe essere necessario abilitare le tracce SMPP per la risoluzione dei problemi corretta.

* Con le tracce SMPP abilitate, verificate che la `SUBMIT_SM PDU` contenga le informazioni giuste.

* Verificate che il provider risponda con un `SUBMIT_SM_RESP PDU` con un valore &quot;OK&quot; (codice 0). Assicurarsi che la PDU arrivi con un ritardo ragionevole: qualsiasi valore superiore a 1 secondo deve essere discusso con il fornitore, di solito arriva in meno di 100 ms.

* Se tutti questi passaggi funzionano, potete essere certi che il problema si trova sul lato del fornitore. Dovranno risolvere i problemi sulla loro piattaforma.

* Se funziona ma il throughput non è coerente, provare a regolare la finestra di invio e abbassare il throughput MT. Sarà necessario lavorare con il fornitore per regolarlo.  Adobe Campaign può inviare i messaggi molto rapidamente, in modo che possano verificarsi problemi di prestazioni sulle apparecchiature del fornitore.

## MT sono duplicati (lo stesso SMS viene inviato più volte in una riga){#duplicated-MT}

I duplicati sono spesso causati da tentativi. È normale avere duplicati quando si riprovano i messaggi, invece di rimuovere la causa principale dei tentativi.

* Se visualizzate duplicati inviati esattamente 60 secondi di differenza, probabilmente si tratta di un problema sul lato del fornitore, che non invia una `SUBMIT_SM_RESP` abbastanza rapidamente.

* Se ne visualizzano molti `BIND/UNBIND`, si ha una connessione instabile. Per informazioni sulle soluzioni, consultare la sezione [Problema con connessioni instabili](../../delivery/using/troubleshooting-sms.md#issues-unstable-connection) prima di provare a risolvere i problemi dei messaggi duplicati.

Riduzione della quantità di duplicati in caso di nuovo tentativo:

* Abbassare la finestra di invio. La finestra di invio deve essere sufficientemente grande da coprire la latenza `SUBMIT_SM_RESP`. Il suo valore rappresenta il numero massimo di messaggi che possono essere duplicati se si verifica un errore mentre la finestra è piena.

## Problema durante l&#39;elaborazione di SR (ricevute di consegna) {#issue-process-SR}

* Sarà necessario abilitare le tracce SMPP per eseguire qualsiasi tipo di risoluzione dei problemi SR.

* Verificare che il `DELIVER_SM PDU` provenga dal provider e che sia ben formato.

* Verificate che  Adobe Campaign risponda correttamente con `DELIVER_SM_RESP PDU` in modo tempestivo. Su Adobe Campaign Classic, questo garantisce che la SR sia stata inserita nella tabella `providerMsgId` per l&#39;elaborazione differita mediante il processo SMS.

Se il `DELIVER_SM PDU` non viene riconosciuto correttamente, è necessario verificare quanto segue:

* Controllare il regex relativo all&#39;estrazione ID e all&#39;elaborazione degli errori nell&#39; **account esterno**. Potrebbe essere necessario convalidarli rispetto al contenuto di `DELIVER_SM PDU`.

* Verificare che il provisioning degli errori sia corretto nella tabella `broadLogMsg`.

Se il `DELIVER_SM PDU` è stato riconosciuto dal connettore SMPP esteso Adobe Campaign Classic ma il file wideLog non viene aggiornato correttamente, verificare il processo di riconciliazione ID descritto nella sezione [Corrispondenza MT, SR e voci di broadcast](../../delivery/using/sms-protocol.md#matching-mt).

Se avete risolto tutto ma alcuni SR non validi si trovano ancora nei buffer del provider, potete ignorarli utilizzando l&#39;opzione &quot;Numero di riconoscimento ID non valido&quot;. Questo dovrebbe essere utilizzato con cura e reimpostato a 0 il più rapidamente possibile dopo che i buffer sono puliti.

## Problema durante l&#39;elaborazione di MO (e blacklist/risposta automatica){#issue-process-MO}

* Abilitare tracce SMPP durante i test. Se non si abilita TLS, è necessario eseguire un&#39;acquisizione di rete durante la risoluzione dei problemi MO per verificare che le PDU contengano le informazioni corrette e siano formattate correttamente.

* Durante l&#39;acquisizione del traffico di rete o l&#39;analisi delle tracce SMPP, assicurarsi di catturare l&#39;intera conversazione con il MO e la sua risposta MT, se è configurata una risposta.

* Se l&#39;MO (`DELIVER_SM PDU`) non viene visualizzato nelle tracce, il problema si trova sul lato del provider. Dovranno risolvere i problemi sulla loro piattaforma.

* Se viene visualizzato `DELIVER_SM PDU`, verificare che sia riconosciuto da  Adobe Campaign con un `DELIVER_SM_RESP PDU` (codice 0) di successo. Questo RESP garantisce che tutta la logica di elaborazione è stata applicata da  Adobe Campaign (risposta automatica e consenti/elenco Bloccati). In caso contrario, cercate un messaggio di errore nei registri del processo SMS.

* Se le risposte automatiche sono abilitate, controllate che `SUBMIT_SM` sia stato inviato al provider. In caso contrario, è garantito di trovare un messaggio di errore nei log del processo SMS.

* Se il `SUBMIT_SM MT PDU` contenente la risposta è presente nelle tracce ma l&#39;SMS non arriva al telefono cellulare, è necessario contattare il provider per assistenza nella risoluzione dei problemi.

## Problema durante la preparazione della consegna che non esclude i destinatari in quarantena (in quarantena dalla funzione di risposta automatica) {#issue-delivery-preparation}

* Verificare che il formato del numero di telefono sia esattamente lo stesso nella tabella di quarantena e nel registro di consegna. In caso contrario, fare riferimento a questa sezione [in caso di problemi con il prefisso più (+) del formato del numero di telefono internazionale.](../../delivery/using/sms-protocol.md#automatic-reply)

* Controllare i codici brevi. Le esclusioni possono verificarsi se il codice breve del destinatario è uguale a quello definito nell&#39;account esterno o se è vuoto (vuoto = qualsiasi codice di scelta rapida). Se viene utilizzato un solo codice breve per l&#39;intera istanza  Adobe Campaign, è più semplice lasciare vuoti tutti i campi **short code**.

## Problemi di codifica {#encoding-issues}

**Passaggio 1: Contatta il fornitore**

Contattateli e vedete cosa c&#39;è che non va. Dovrebbero essere in grado di dirvi se il problema è dalla loro parte o  lato Adobe Campaign. Se il problema è  Adobe Campaign, dovrebbero essere in grado di dirvi esattamente quale campo è errato.

**Passaggio 2: Scopri cosa contiene il tuo messaggio**

Unicode consente molte varianti di caratteri simili e  Adobe Campaign non è in grado di gestirli tutti.

La fonte più comune di problemi è la copia-incolla da un elaboratore di testi, che modifica i caratteri comuni in versioni tipografiche corrette: spazi modificati in spazi unificatori, virgolette doppie cambiate in virgolette di apertura e chiusura, segni meno modificati in vari tipi di trattini, ecc.

Non copiare e incollare il messaggio durante il test, digitalo sempre direttamente nell&#39;interfaccia.

Con l&#39;espressione esadecimale, è possibile distinguere tra caratteri simili. Una L minuscola, una I, O, 0 maiuscola, tutti i diversi tipi di virgolette, codifiche non latine o anche diversi tipi di spazi possono avere lo stesso aspetto o addirittura non essere visualizzati.

Per convertire Unicode in esadecimale, potete utilizzare strumenti online come il sito Web [Unicode code converter](https://r12a.github.io/app-conversion/). Digitare il testo desiderato, assicurarsi che non siano presenti PII, ad esempio i numeri di telefono, e fare clic su **Converti**. Verranno visualizzati i valori esadecimali nella parte inferiore (zona UTF-32).

Quando aprite i biglietti per problemi di codifica, sia con il provider che con il supporto Adobe Campaign , includete sempre una versione esadecimale di ciò che digitate e ciò che visualizzate.

**Passaggio 3: Sapere cosa inviare**

Determinare la codifica da utilizzare ed effettuare ricerche online per la tabella dei caratteri. Verificate che i caratteri che intendete inviare siano effettivamente disponibili nella tabella codici di destinazione. Verificare che il campo `data_coding` sia corretto e corrisponda alle aspettative dell&#39;utente e del fornitore.

**Passaggio 4: Scopri cosa hai inviato**

Sarà necessario l&#39;output di debug del connettore per vedere esattamente quali byte si inviano al provider. I problemi di codifica vengono visualizzati in `SUBMIT_SM PDU`s, pertanto accertatevi di acquisirli. Invia messaggi molto distinti e facili da trovare nel registro.

Inviate diversi tipi di caratteri speciali durante il test. Ad esempio, la codifica GSM7 contiene caratteri estesi che sono molto distinti nella forma esadecimale, ma che sono facili da individuare in quanto non vengono visualizzati in nessun’altra codifica.

## Elementi da includere nella comunicazione relativa a un problema di SMS {#element-include}

Ogni volta che cercate assistenza su un problema di SMS, che si tratti di aprire un biglietto di supporto per  Adobe Campaign, al provider di SMS, o qualsiasi tipo di comunicazione sul problema, dovrete includere le seguenti informazioni per essere certi che saranno correttamente qualificate. I problemi qualificati sono fondamentali per risolvere più rapidamente i problemi.

* **Abilitare** messaggi SMPP dettagliati quando viene visualizzato il problema. La maggior parte dei problemi legati agli SMS sono impossibili da risolvere senza questo.

* Se il problema riguarda il traffico SMS, contattate prima il fornitore. La loro piattaforma è ideale per una diagnosi efficiente dei problemi di traffico SMS in tempo reale.

* Includete una breve ma concreta descrizione del problema.

* Includete una descrizione del risultato previsto.

* Includete il feedback dal fornitore.

* Includere registri e/o acquisizioni di rete rilevanti. Durante l&#39;acquisizione, assicurarsi di riprodurre il problema durante l&#39;acquisizione.

* Se includete file di registro, tracce o acquisizioni, individuate la posizione esatta nel file quando viene visualizzato il problema.

* Se si fa riferimento a messaggi, PDU o file di registro, indicare chiaramente la marca temporale per facilitarne la ricerca.

* Provare a riprodurre il problema in un ambiente di test. Se non si è sicuri di un&#39;impostazione, provarla nell&#39;ambiente di test e verificare il risultato con le tracce SMPP. Di solito è meglio segnalare i problemi replicati negli ambienti di test piuttosto che segnalare direttamente i problemi negli ambienti di produzione.

* Includi eventuali modifiche o modifiche apportate alla piattaforma. Inoltre, includete eventuali modifiche che il fornitore potrebbe aver apportato al suo fianco.

### Acquisizione di rete {#network-capture}

L&#39;acquisizione di rete non è sempre necessaria, in genere i messaggi SMPP sono sufficienti. Seguono alcune linee guida che consentono di determinare se è necessaria un&#39;acquisizione di rete:

* Problemi di connessione, ma i messaggi visualizzati non mostrano `BIND_RESP PDU`.

* Disconnessioni non spiegate senza messaggio di errore, il comportamento abituale del connettore quando rileva un errore di protocollo di basso livello.

* Il provider si lamenta del processo di disconnessione/disconnessione.

* Problemi di codifica nei campi TLV facoltativi.

* Si sospetta che il traffico sia misto tra diverse connessioni.

In tutte le altre situazioni, provare ad analizzare prima i messaggi SMPP dettagliati e richiedere un&#39;acquisizione di rete solo se mancano informazioni nei registri dettagliati.

In alcuni casi, l&#39;acquisizione del traffico di rete non è necessaria. Le situazioni più comuni sono le seguenti:

* TLS abilitato: Per definizione, il traffico TLS è crittografato e non può essere acquisito.

* Problemi di prestazioni: I registri contengono tutte le informazioni necessarie per tenere traccia dei problemi di prestazioni.

* Problemi di temporizzazione (`retry timing`, `enquire_link` punto, limite di velocità, ecc.)

* Analisi ed elaborazione SR: i registri dettagliati forniscono molto più contesto e una presentazione migliore.

* Elaborazione MO (risposte automatiche, quarantena).

* Errori che non riguardano il traffico SMPP effettivo: Preparazione della distribuzione, problemi dell&#39;API del Centro messaggi, problemi del flusso di lavoro, ecc.

## Abilitazione delle tracce SMPP {#enabling-smpp-traces}

Il nuovo connettore supporta la registrazione estesa attraverso le tracce: SMPP. Le tracce vengono emesse nel registro MTA, non nell&#39;output standard.

**Abilitazione per account esterno (metodo preferito)**

1. Nell&#39; **account esterno**, selezionare **Abilita tracce SMPP dettagliate nel file di registro**.
1. Attendere 10 minuti per consentire al server di ricaricare gli account esterni.

Dovrebbe essere attiva ora.

**Abilitazione nella configurazione**

Nel file `config-instance.xml`, impostate i seguenti parametri:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Controllo del numero di connessioni aperte su un contenitore {#open-connections}

Per verificare il numero di connessioni aperte su un contenitore, è possibile utilizzare questo comando:

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

4 connessioni aperte per il processo sms e 2 per il bambino MTA con 5 bambini.
