---
product: campaign
title: Risoluzione dei problemi relativi agli SMS
description: Scopri come risolvere i problemi del canale SMS
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: SMS, Troubleshooting
role: User
exl-id: 841f0c2f-90ef-4db0-860a-75fc7c48804a
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '2767'
ht-degree: 0%

---

# Risoluzione dei problemi SMS {#troubleshooting-sms}

## Conflitto tra diversi account esterni {#external-account-conflict}

Se l’istanza dispone di più account esterni SMS, è necessario verificare che i problemi non siano causati da un conflitto tra account esterni.

Adobe Campaign tratta gli account esterni come entità non correlate.

Se disponi di più account, segui questa procedura per isolare l’account esterno che causa problemi:

1. Disattiva tutti gli account esterni.
1. Abilita un account esterno.
1. Prova a riprodurre il problema.
1. Se il problema iniziale non compare sempre, eseguire una quantità ragionevole di tentativi prima di concludere.
1. Se il problema non viene visualizzato con l&#39;account singolo, disattivarlo e riavviare il sistema al passaggio 2 dell&#39;account successivo.

Una volta verificato ogni singolo account, esistono due possibili scenari:

* **Il problema è apparso su uno o più account**

  In questo caso, puoi applicare altre procedure di risoluzione dei problemi su ogni singolo account. È consigliabile disabilitare altri account durante la diagnosi di un account per ridurre il traffico di rete e il numero di registri.

* **Il problema non è stato visualizzato quando è attivo un solo account alla volta**

  Si è verificato un conflitto tra gli account. Come accennato in precedenza, Adobe Campaign tratta gli account singolarmente, ma il provider può trattarli come un singolo account.

   * Stai utilizzando diverse combinazioni login/password tra tutti i tuoi account.
Dovrai contattare il fornitore per diagnosticare potenziali conflitti dalla loro parte.

   * Alcuni account esterni condividono la stessa combinazione login/password.
Il provider non ha modo di dire da quale account esterno proviene il `BIND PDU` mittente, quindi tratta tutte le connessioni da più account come una sola. Potrebbero aver indirizzato MO e SR in modo casuale sui due account, causando problemi.
Se il provider supporta più codici brevi per la stessa combinazione di login/password, dovrai chiedere loro dove inserire tale codice breve nella `BIND PDU`. Tieni presente che questa informazione deve essere inserita all’interno del `BIND PDU`, e non in `SUBMIT_SM`, poiché `BIND PDU` è l&#39;unica posizione in cui sarà possibile instradare correttamente i moduli di gestione di rete.
Consulta la [Informazioni in ogni tipo di PDU](sms-protocol.md#information-pdu) per sapere quale campo è disponibile nella sezione `BIND PDU`, in genere si aggiunge il codice breve in `address_range`, ma questo richiede un supporto speciale da parte del provider. Contattali per sapere in che modo si aspettano di instradare più codici brevi in modo indipendente.
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

* Verificare (nella directory /postupgrade) se il sistema è stato aggiornato e quando
* Controlla se i pacchetti che interessano gli SMS potrebbero essere stati aggiornati di recente (/var/log/dpkg.log).

## Problema con il mid-sourcing (ospitato){#issue-mid-sourcing}

* Se il problema si verifica in un ambiente di mid-sourcing, accertati che i registri di consegna e generali siano creati e aggiornati correttamente sul server di mid-sourcing. In caso contrario, non si tratta di un problema SMS.

* Se tutto funziona sul server mid e gli SMS vengono inviati correttamente, ma l’istanza di marketing non viene aggiornata correttamente, si potrebbe verificare un problema di sincronizzazione intermedia.

## Problema durante la connessione al provider {#issue-provider}

* Se restituisce `BIND PDU` un codice diverso da zero `command_status` , chiedere ulteriori informazioni al provider.

* Verificare che la rete sia configurata correttamente in modo che la connessione TCP possa essere effettuata al provider.

* Chiedi al provider di verificare che gli IP siano stati aggiunti correttamente alla allowlist del Adobe Campaign istanza.

* Controlla **le impostazioni dei account** esterni. Chiedi al provider il valore dei campi.

* Se la connessione ha esito positivo ma è instabile, controllare [Problema con connessioni instabili](troubleshooting-sms.md#issues-unstable-connection) sezione.

* Se i problemi di connessione sono difficili da diagnosticare, un&#39;acquisizione di rete può fornire informazioni. Verificare che l&#39;acquisizione di rete venga eseguita contemporaneamente mentre il problema viene visualizzato per essere analizzato in modo efficiente. È inoltre necessario prendere nota dell&#39;ora esatta in cui viene visualizzato il problema.

## Problemi di connessione instabile {#issues-unstable-connection}

Una connessione è considerata instabile se si verifica una delle seguenti situazioni:

* La connessione dura meno di 1 ora. Le connessioni del trasmettitore Adobe Campaign Classic sono un’eccezione a causa del modo in cui funziona l’MTA di Adobe Campaign Classic.

* Il provider invia `UNBIND PDU`s.

* `enquire_link` va in timeout, sul lato Adobe Campaign o sul lato provider. Potresti vedere `ENQUIRE_LINK_RESP` con un codice di errore diverso da zero in questo caso.

* Ci sono molti `BIND PDU`s. Non dovrebbero essercene più di alcuni in un giorno, a seconda del numero di connessioni. Deve essere emesso un avviso da più di 1 PDU BIND all&#39;ora.

Come risolvere i problemi di stabilità della connessione:

* Le connessioni instabili sono raramente la causa principale, spesso è il risultato di un altro problema che attiva una disconnessione. Trovare la causa principale è la priorità.

* Abilita tracce SMPP dettagliate. Saranno necessarie per vedere cosa accade al riavvio della connessione.

* Se il provider invia `BIND PDU`s, qualcosa potrebbe andare storto. Chiedi al tuo provider perché `UNBING` viene inviato.

* L&#39;acquisizione di una rete a volte è l&#39;unico modo per vedere come viene chiusa la connessione.

* Se il provider chiude le connessioni inviando una `TCP FIN` o un `TCP RST packet`, per ulteriori informazioni, rivolgersi al provider.

* Se il provider chiude la connessione dopo l’invio di un errore pulito, ad esempio `DELIVER_SM_RESP` con un codice di errore, devono correggere il connettore in caso contrario, impedendo la trasmissione di altri tipi di messaggi e attivando la limitazione dell’MTA. Ciò è particolarmente importante nella modalità ricetrasmettitore, dove la chiusura della connessione influisce sia su MT che su SR.

## Problema durante l’invio di un messaggio MT (SMS regolare inviato a un utente finale){#issue-MT}

* Verificare che la connessione sia stabile. Una connessione SMPP deve rimanere attiva per almeno 1 ora di seguito, ad eccezione dei trasmettitori su Adobe Campaign Classic. Consulta la sezione [Problema con connessioni instabili](sms-protocol.md#issues-unstable-connection).

* Se il riavvio dell’MTA fa sì che l’invio di messaggi MT torni a funzionare per un breve periodo di tempo, probabilmente si hanno limitazioni a causa di una connessione instabile. Consulta la sezione [Problema con connessioni instabili](troubleshooting-sms.md#issues-unstable-connection).

* Verificare che l&#39;ampio registro sia presente e che lo stato sia corretto con le date corrette. In caso contrario, potrebbe trattarsi di un problema di consegna o di preparazione della consegna.

* Verifica che l’MTA elabori effettivamente il messaggio. In caso contrario, potrebbe non trattarsi di un problema SMS.

* Verifica che il connettore SMS sia effettivamente associato all’apparecchiatura del provider. Chiedere al provider di fornire un feedback per verificare che tutti i sistemi comunichino correttamente. Consulta `BIND_TRANSMITTER` e `BIND_TRANSCEIVER PDU`s per informazioni sul processo di associazione. Per una corretta risoluzione dei problemi, potrebbe essere necessario abilitare le tracce SMPP.

* Con le tracce SMPP abilitate, verifica che `SUBMIT_SM PDU` contiene le informazioni corrette.

* Verifica che il provider risponda con un `SUBMIT_SM_RESP PDU` con un valore &quot;OK&quot; (codice 0). Assicurati che la PDU arrivi con un ritardo ragionevole: qualsiasi elemento di durata superiore a 1 secondo deve essere discusso con il provider, in genere arriva in meno di 100 ms.

* Se tutti questi passaggi funzionano, si può essere certi che il problema è sul lato del fornitore. Dovranno risolvere i problemi sulla loro piattaforma.

* Se funziona ma la velocità effettiva non è coerente, prova a regolare la finestra di invio e ad abbassare la velocità effettiva di MT. Per regolare l’impostazione, dovrai collaborare con il provider. Adobe Campaign è in grado di inviare messaggi molto rapidamente, in modo che l&#39;apparecchiatura del provider possa presentare problemi di prestazioni.

## MT sono duplicati (lo stesso SMS viene inviato più volte di fila){#duplicated-MT}

I duplicati sono spesso causati da nuovi tentativi. È normale disporre di duplicati quando si ritenta il messaggio, è invece consigliabile provare a rimuovere la causa principale dei nuovi tentativi.

* Se vedi duplicati inviati a distanza di esattamente 60 secondi, è probabile che si tratti di un problema dal lato del fornitore, che non invia un `SUBMIT_SM_RESP` abbastanza velocemente.

* Se ne vedi molti `BIND/UNBIND`, la connessione è instabile. Consulta la[Problema con connessioni instabili](troubleshooting-sms.md#issues-unstable-connection) sezione per le soluzioni prima di tentare di risolvere i problemi relativi ai messaggi duplicati.

Riduzione della quantità di duplicati in caso di un nuovo tentativo:

* Abbassa la finestra di invio. La finestra di invio deve essere sufficientemente grande da coprire `SUBMIT_SM_RESP` la latenza. Il suo valore rappresenta il numero massimo di messaggi che possono essere duplicati se si verifica un errore mentre la finestra è piena.

## Problema durante l&#39;elaborazione di SR (ricevute di consegna) {#issue-process-SR}

* Per eseguire qualsiasi tipo di risoluzione dei problemi SR, è necessario abilitare le tracce SMPP.

* Verifica che la `DELIVER_SM PDU` proviene dal provider e ha un formato corretto.

* Controlla che Adobe Campaign risponda con un `DELIVER_SM_RESP PDU` tempestivamente. Su Adobe Campaign Classic, questo garantisce che l’SR sia stato inserito nel `providerMsgId` tabella per l’elaborazione differita da parte del processo SMS.

Se il `DELIVER_SM PDU` non è stato riconosciuto correttamente, è necessario verificare quanto segue:

* Controlla la regex relativa all’estrazione degli ID e all’elaborazione degli errori nel **Account esterno**. Potrebbe essere necessario convalidarli rispetto al contenuto di `DELIVER_SM PDU`.

* Verifica che gli `broadLogMsg` errori siano correttamente forniti nella tabella.

Se il `DELIVER_SM PDU` è stato confermato dal connettore SMPP esteso di Adobe Campaign Classic, ma il broadLog non viene aggiornato correttamente. Controlla il processo di riconciliazione degli ID descritto nella sezione [Voci MT, SR e broadlog corrispondenti](sms-protocol.md#matching-mt).

Se hai corretto tutto ma alcuni SR non validi si trovano ancora nei buffer del provider, puoi saltarli utilizzando l’opzione &quot;Conteggio conferme ID non valido&quot;. Questo deve essere usato con cautela e azzerato a 0 il più rapidamente possibile dopo la pulizia dei buffer.

## Problema durante l’elaborazione di MO (e blacklist/risposta automatica){#issue-process-MO}

* Abilitare le tracce SMPP durante i test. Se non si abilita TLS, è necessario eseguire un&#39;acquisizione di rete durante la risoluzione dei problemi relativi a MO per verificare che le PDU contengano le informazioni corrette e siano formattate correttamente.

* Quando acquisisci il traffico di rete o analizzi le tracce SMPP, assicurati di acquisire l’intera conversazione con il MO e il relativo messaggio MT di risposta se è configurata una risposta.

* Se il simbolo MO (`DELIVER_SM PDU`) non viene visualizzato nelle tracce, il problema si trova sul lato del fornitore. Dovranno risolvere i problemi sulla loro piattaforma.

* Se il `DELIVER_SM PDU` viene visualizzato, verifica che sia confermato da Adobe Campaign con un `DELIVER_SM_RESP PDU` (codice 0) Questo RESP garantisce che tutta la logica di elaborazione sia stata applicata da Adobe Campaign (risposta automatica e inserisce nell&#39;elenco Bloccati consenti/). In caso contrario, cerca un messaggio di errore nei registri di processo SMS.

* Se sono abilitate le risposte automatiche, verificare che `SUBMIT_SM` è stato inviato al provider. In caso contrario, troverai sicuramente un messaggio di errore nei registri di processo degli SMS.

* Se il `SUBMIT_SM MT PDU` contenente la risposta si trova nelle tracce ma l&#39;SMS non arriva al telefono cellulare, dovrai contattare il provider per assistenza sulla risoluzione dei problemi.

## Problema durante la preparazione della consegna che non esclude i destinatari in quarantena (messi in quarantena dalla funzione di risposta automatica) {#issue-delivery-preparation}

* Verifica che il formato del numero di telefono sia esattamente lo stesso nella tabella di quarantena e nel registro di consegna. In caso contrario, fai riferimento a questo [sezione](sms-protocol.md#automatic-reply) in caso di problemi con il prefisso più del formato del numero di telefono internazionale.

* Controlla i codici brevi. Le esclusioni possono verificarsi se il codice breve del destinatario è uguale a quello definito nell’account esterno o se è vuoto (vuoto = qualsiasi codice breve). Se viene utilizzato un solo codice breve per l’intera istanza di Adobe Campaign, è più semplice lasciare tutto **codice breve** campi vuoti.

## Problemi di codifica {#encoding-issues}

**Passaggio 1: Contatta il provider**

Contattali e vedi cosa c&#39;è di sbagliato con loro. Dovrebbero essere in grado di dirti se il problema è dalla loro parte o da quella di Adobe Campaign. Se il problema è in Adobe Campaign, dovrebbe essere in grado di dirti esattamente quale campo non è corretto.

**Passaggio 2: conoscere il contenuto del messaggio**

Unicode consente molte varianti per caratteri simili e Adobe Campaign non è in grado di gestirli tutti.

La causa più comune di problemi è il copia-incolla da un elaboratore di testi, che cambia i caratteri usuali in versioni tipograficamente corrette: spazi modificati in spazi unificatori, virgolette doppie modificate in virgolette di apertura e chiusura, segni meno modificati in vari tipi di trattini, ecc.

Non copiare e incollare il messaggio durante il test, digitalo sempre direttamente nell’interfaccia.

Con esadecimale, puoi distinguere la differenza tra caratteri simili. Una L minuscola, una I maiuscola, O, 0, tutti i diversi tipi di virgolette, codifiche non latine o anche diversi tipi di spazi possono tutti avere lo stesso aspetto o anche non essere visualizzati affatto.

Per convertire Unicode in esadecimale, puoi utilizzare strumenti online quali [Convertitore di codice Unicode](https://r12a.github.io/app-conversion/) sito Web. Digita il testo, assicurati che non siano presenti dati PII come i numeri di telefono e fai clic su **Converti**. I valori esadecimali sono visualizzati nella parte inferiore (zona UTF-32).

Quando si aprono ticket sui problemi di codifica, sia con il provider che con [Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html), includi sempre una versione esadecimale di ciò che digiti e ciò che visualizzi.

**Passaggio 3: sapere cosa inviare**

Determina la codifica che prevedi di utilizzare e cerca online la tabella dei caratteri corrispondente. Verifica che i caratteri che intendi inviare siano effettivamente disponibili nella tabella codici di destinazione. Verifica che la `data_coding` è corretto e corrisponde a quello che tu e il fornitore vi aspettate.

**Passaggio 4: sapere cosa è stato inviato**

Per visualizzare esattamente i byte inviati al provider, è necessario l&#39;output di debug del connettore. I problemi di codifica vengono visualizzati in `SUBMIT_SM PDU`s, assicurati di catturarli. Invia messaggi molto distinti e facili da trovare nel registro.

Invia diversi tipi di caratteri speciali durante il test. Ad esempio, la codifica GSM7 dispone di caratteri estesi molto distinti nella loro forma esadecimale, che sono facili da individuare poiché non compaiono in nessun’altra codifica.

## Elementi da includere durante la comunicazione relativa a un problema SMS {#element-include}

Ogni volta che chiedi assistenza su un problema relativo agli SMS, che si tratti dell’apertura di un ticket di supporto ad Adobe Campaign, al provider SMS o a qualsiasi tipo di comunicazione su tale problema, dovrai includere le seguenti informazioni per assicurarti che sia qualificato correttamente. I problemi correttamente qualificati sono fondamentali per risolverli più rapidamente.

* **Abilita messaggi SMPP dettagliati** quando viene visualizzato il problema. La maggior parte dei problemi relativi agli SMS è impossibile da risolvere senza questo.

* Se il problema è relativo al traffico SMS, contatta prima il provider. La loro piattaforma è ideale per una diagnosi efficiente dei problemi di traffico SMS in tempo reale.

* Includere una breve descrizione del problema.

* Includi una descrizione del risultato previsto.

* Includi il feedback del provider.

* Includere registri e/o acquisizioni di rete pertinenti. Quando si eseguono le acquisizioni, assicurarsi di riprodurre il problema durante la cattura.

* Se si includono registri, tracce o acquisizioni, individuare la posizione esatta nel file quando viene visualizzato il problema.

* Se fai riferimento a messaggi, PDU o registri, indica chiaramente la marca temporale per semplificarne la ricerca.

* Prova a riprodurre il problema in un ambiente di test. Se non sei sicuro di un’impostazione, prova nell’ambiente di test e verifica il risultato con le tracce SMPP. In genere è meglio segnalare i problemi replicati negli ambienti di test piuttosto che segnalare direttamente i problemi negli ambienti di produzione.

* Includi eventuali modifiche o modifiche apportate sulla piattaforma. Inoltre, includi eventuali modifiche che il provider potrebbe aver apportato dalla sua parte.

### Acquisizione della rete {#network-capture}

L’acquisizione di rete non è sempre necessaria, in genere è sufficiente disporre di messaggi SMPP dettagliati. Di seguito sono riportate alcune linee guida utili per determinare se è necessario acquisire una rete:

* Problemi di connessione, ma i messaggi dettagliati non mostrano alcun `BIND_RESP PDU`.

* Disconnessioni inspiegabili senza messaggio di errore, il comportamento abituale del connettore quando rileva un errore di protocollo di basso livello.

* Il provider si lamenta del processo di annullamento/disconnessione.

* Problemi di codifica nei campi TLV facoltativi.

* Si sospetta che il traffico sia misto tra connessioni diverse.

In tutte le altre situazioni, prova ad analizzare prima i messaggi SMPP dettagliati e a richiedere un’acquisizione di rete solo se mancano informazioni nei registri dettagliati.

In alcuni casi, non è necessario acquisire il traffico di rete. Di seguito sono elencate le situazioni più comuni:

* TLS abilitato: per definizione, il traffico TLS è crittografato e non può essere acquisito.

* Problemi di prestazioni: i registri contengono tutte le informazioni necessarie per tracciare i problemi di prestazioni.

* Problemi di tempistica (`retry timing`, `enquire_link` periodo, limitazione della velocità effettiva, ecc.)

* Analisi ed elaborazione SR: i registri dettagliati forniscono molto più contesto e una presentazione migliore.

* Elaborazione MO (risposte automatiche, quarantena).

* Errori che non coinvolgono il traffico SMPP effettivo: preparazione della consegna, problemi API del Centro messaggi, problemi del flusso di lavoro, ecc.

## Abilitazione delle tracce SMPP {#enabling-smpp-traces}

Il nuovo connettore supporta la registrazione estesa tramite tracce: SMPP. Le tracce vengono generate nel registro MTA, non nell’output standard.

**Abilitazione per account esterno (metodo preferito)**

1. In **Account esterno**, spunta **Abilita tracce SMPP dettagliate nel file di registro**.
1. Attendere 10 minuti per consentire al server di ricaricare gli account esterni.

Dovrebbe essere attivo ora.

**Abilitazione nella configurazione**

In `config-instance.xml` file, impostare i seguenti parametri:

```
<mta>
  <child extraArgs="-tracefilter:SMPP"/>
</mta>
<sms args="-tracefilter:SMPP"/>
```

## Verifica del numero di connessioni aperte in un contenitore {#open-connections}

Per verificare il numero di connessioni aperte in un contenitore, è possibile utilizzare questo comando:

```
(for pid in $(ss -neopts  | sed -n 's/^.*:3600[ \t].*users:(([0-9A-Za-z"]*,pid=\([0-9]*\),.*$/\1/p' | sort ); do  cat /proc/$pid/cmdline; echo  " $pid" ;done;) | uniq --count
```

Elenca il numero di connessioni aperte per una determinata porta. In questo caso viene utilizzata la porta 3600.

Il risultato dovrebbe essere il seguente:

```
4 nlserversms -noconsole -tracefile:sms@INSTANCE_NAME -instance:INSTANCE_NAME -detach 15180
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 1838
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24025
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 24029
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 29088
2 nlservermtachild -tracefile:mtachild@INSTANCE_NAME -instance:INSTANCE_NAME -detach 30390
```

4 connessioni aperte per il processo sms e 2 per elemento secondario mta con 5 elementi secondari.
