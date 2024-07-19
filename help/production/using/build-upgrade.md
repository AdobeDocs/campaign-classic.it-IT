---
product: campaign
title: Introduzione agli aggiornamenti della build
description: Scopri i passaggi chiave per l’aggiornamento a una nuova build
feature: Monitoring, Upgrade
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '2324'
ht-degree: 0%

---

# Esecuzione di un aggiornamento della build{#performing-a-build-upgrade}



Questa sezione fornisce una descrizione dettagliata del processo di aggiornamento e dei passaggi per identificare e risolvere i conflitti.

L’aggiornamento della build deve essere eseguito con cautela, i suoi impatti devono essere considerati in anticipo e la procedura deve essere completata con un livello elevato di disciplina. Per garantire un aggiornamento corretto, accertati che solo gli utenti esperti eseguano i passaggi descritti di seguito. Inoltre, consigliamo vivamente di contattare [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) prima di avviare qualsiasi aggiornamento.

Sono necessari i seguenti prerequisiti:

* Informazioni sull’architettura di Campaign
* Conoscenza dei sistemi e dei server
* Diritti e autorizzazioni amministrativi

Puoi trovare ulteriori informazioni nelle seguenti sezioni: [Aggiornamento di Adobe Campaign](../../production/using/upgrading.md), [Migrazione a una nuova versione](../../migration/using/about-migration.md).

Per le istanze in hosting e ibride, devi richiedere l’aggiornamento della build al team Operazioni tecniche Adobe. Per ulteriori informazioni, consulta la sezione Domande frequenti in basso, se questa pagina. Consulta anche le [domande frequenti sull&#39;aggiornamento della build](../../platform/using/faq-build-upgrade.md).

## Preparare l’aggiornamento

![](assets/do-not-localize/icon_planification.png)

Prima di avviare l’aggiornamento della build, devi eseguire una preparazione completa come descritto di seguito.
Una volta che il sistema è pronto per essere aggiornato, un aggiornamento della build richiede **almeno** 2 ore.

Il processo di aggiornamento della build richiede le seguenti risorse:

* un architetto Adobe: per comprendere le strutture del database (schemi predefiniti ed eventuali schemi aggiuntivi aggiunti, progettazioni di campagne ed eventuali funzionalità di percorso critiche che devono essere avviate e testate in un ordine specifico).
* un project manager: nel caso in cui l’aggiornamento della build coinvolga molte istanze diverse (produzione, staging, test) e altri server e applicazioni di terze parti (database, siti SFTP, provider di servizi di messaggistica), è considerata una best practice disporre di un project manager per coordinare tutti i test.
* amministratore di Adobe Campaign: l’amministratore conosce la configurazione del server, compresi, tra l’altro: sicurezza, layout delle cartelle, reporting e requisiti di importazione/esportazione. Non eseguire un aggiornamento della build senza l’amministratore.
* un operatore di Adobe Campaign (utente marketing): un aggiornamento corretto si basa sulla capacità dell’utente di eseguire correttamente le attività quotidiane. Per questo motivo, includi sempre almeno uno degli operatori giornalieri nel test dei server aggiornati.

### Pianificazione

Di seguito sono riportati i punti chiave su come pianificare un aggiornamento della build:

1. Riserva almeno 2 ore per l’aggiornamento.
1. Distribuisci i dettagli di contatto per il personale Adobe e del cliente.
1. Per le istanze in hosting: il personale di Adobe e del cliente coordinerà il tempo per l’aggiornamento e chi verrà eseguito.
1. Per le istanze on-premise: il personale del cliente gestisce l’intero processo; se è necessaria assistenza nella verifica di flussi di lavoro personalizzati e nella logica di consegna, è necessario inserire i servizi di consulenza.
1. Determinare e confermare a quale versione di Adobe Campaign si desidera eseguire l&#39;aggiornamento. Consultare le [note sulla versione di Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Confermare il possesso dei file eseguibili di aggiornamento.

### Persone chiave

Il processo di aggiornamento della build richiede il coinvolgimento delle seguenti persone:

* Architetto di Adobe: per le architetture in hosting o ibride, l’architetto deve coordinarsi con l’Assistenza clienti di Adobe Campaign.

* Project manager:
   * per le installazioni on-premise: il responsabile di progetto interno del cliente guida l’aggiornamento e gestisce i test del ciclo di vita.

   * per l’installazione in hosting: il team di hosting collaborerà con il team di assistenza clienti di Adobe Campaign e con il cliente per coordinare la timeline di aggiornamento per tutte le istanze.

* Amministratore Adobe Campaign:
   * per le installazioni locali: l’amministratore esegue l’aggiornamento.

   * per le installazioni in hosting: il team di hosting esegue l’aggiornamento.

* Adobe Campaign operator\marketing user (operatore di marketing): esegue test sulle istanze di sviluppo, test e produzione.

### Preparare l’aggiornamento della build

Prima di avviare l’aggiornamento della build, i clienti on-premise devono eseguire la seguente preparazione:

1. Assicurati che qualsiasi lavoro di sviluppo possa essere esportato prima dell’aggiornamento ed esporta come pacchetti.

1. Eseguire un backup completo dei database per tutte le istanze degli ambienti di origine e di destinazione.

1. Ottieni la versione più recente del [file di configurazione del server](../../installation/using/the-server-configuration-file.md).

1. [Scarica la build più recente](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html). [Ulteriori informazioni](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).

È inoltre necessario conoscere tutte le [righe di comando utili](../../installation/using/command-lines.md) prima di avviare un aggiornamento della build:

* **nlserver pdump**: elenca i processi in esecuzione
* **nlserver pdump -who**: elenca le sessioni client attive
* **nlserver monitor -missing**: elenca le proprietà mancanti
* **nlserver start process@instance-name**: avvia un processo
* **nlserver stop process@instance-name**: arresta un processo
* **nlserver restart process@instance-name**: riavvia un processo
* **nlserver shutdown**: arresta tutti i processi di Campaign
* **nlserver watchdog -svc**: avvia il watchdog (solo UNIX)

## Eseguire l’aggiornamento

![](assets/do-not-localize/icon_process.png)

Le procedure seguenti vengono eseguite solo dai clienti **on-premise**. Per i clienti in hosting, viene gestito dal team di hosting. Per aggiornare Adobe Campaign a una nuova build, la procedura dettagliata è descritta di seguito.

### Duplicare l’ambiente

Ecco come duplicare un ambiente Adobe Campaign per ripristinare un ambiente di origine in un ambiente di destinazione, creando due ambienti di lavoro identici.

A questo scopo, segui la procedura indicata di seguito:

1. Creare una copia dei database in tutte le istanze nell&#39;ambiente di origine.

1. Ripristina queste copie in tutte le istanze dell’ambiente di destinazione.

1. Eseguire lo script di cauterizzazione **nms:freezeInstance.js** nell&#39;ambiente di destinazione prima di avviarlo. In questo modo tutti i processi interagiscono con l’esterno: registri, tracciamento, consegne, flussi di lavoro delle campagne, ecc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Controllare la cauterizzazione, come segue:

   * Verificare che l&#39;unica parte di consegna sia quella con ID impostato su **0**:

     ```
     SELECT * FROM neolane.nmsdeliverypart;
     ```

   * Verifica che l’aggiornamento dello stato della consegna sia corretto:

     ```
     SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
     ```

   * Verifica che l’aggiornamento dello stato del flusso di lavoro sia corretto:

     ```
     SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
     SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
     ```

### Arresta servizi

Per sostituire tutti i file con la nuova versione, è necessario che tutte le istanze di nlserverservice vengano chiuse.

1. Arrestare i servizi seguenti:

   * Servizi Web (IIS): **iisreset /stop**
   * Servizio Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Verificare che il server di reindirizzamento (webmdl) sia arrestato, in modo che il file nlsrvmod.dll utilizzato da IIS possa essere sostituito con la nuova versione.
   >

1. Verificare che nessuna attività sia attiva eseguendo il comando **nlserver pdump**. Se non sono presenti attività, l’output deve essere simile al seguente:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Verificare che tutti i processi siano stati arrestati.

### Aggiornare l’applicazione server Adobe Campaign

1. Eseguire il file **Setup.exe**. Se devi scaricare questo file, accedi a [Centro download](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html).

1. Selezionare la modalità di installazione: **Aggiorna** o **Ripristina**.

1. Fai clic su **Avanti**.

1. Fare clic su **Fine**: il programma di installazione copia i nuovi file.

1. Al termine dell&#39;operazione, fare clic su **Fine**.

### Sincronizzare le risorse

1. Apri la riga di comando.

1. Eseguire **nlserver config -postupgrade -allinstances** per eseguire le operazioni seguenti:

   * Sincronizzare le risorse
   * Aggiornare schemi
   * Aggiornare il database

   >[!NOTE]
   >
   >Questa operazione deve essere eseguita una sola volta e solo su un server applicazioni nlserverweb.
   >

   Per sincronizzare un solo database, eseguire il comando seguente:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Verificare se la sincronizzazione ha generato errori o avvisi.

### Riavvia servizi

È necessario riavviare i seguenti servizi:

* Servizi Web (IIS): **issreset /start**
* Servizio Adobe Campaign: **net start nlserver6**

### Aggiornamento delle console client

La console client deve trovarsi nella stessa build dell’istanza del server.

Nel computer in cui è installato il server applicazioni di Adobe Campaign (nlserverweb), scarica e copia il file:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un nuovo aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

### Compiti aggiuntivi specifici

Alcune configurazioni richiedono attività aggiuntive specifiche per l’aggiornamento a una nuova build.

#### Messaggistica transazionale

Quando la messaggistica transazionale (Centro messaggi) è abilitata nell’istanza Campaign, è necessario eseguire questi passaggi aggiuntivi per aggiornare:

1. Aggiornare il server di produzione del Centro messaggi alla versione scelta.
1. Eseguire gli script post-aggiornamento.
1. Esegui i test e assicurati che le e-mail vengano ricevute correttamente tramite l’istanza di produzione del Centro messaggi.
1. Aggiornare i client e cancellare la cache.
1. Esporta pacchetti:
   * Esportare i pacchetti utilizzando lo strumento di esportazione dei pacchetti client
   * Importa pacchetto schema
   * Disconnetti e riconnetti client
   * Aggiorna database
   * Disconnetti e riconnetti
   * Importa pacchetto di amministrazione
   * Importa pacchetto contenuti
   * Importa pacchetto gestione contenuti
   * Disconnetti e riconnetti
   * Eseguire un rapido controllo di integrità dei flussi di lavoro

1. Modelli di Centro messaggi di Publish per garantire il funzionamento dell&#39;interfaccia tra i server e l&#39;istanza del Centro messaggi.
1. Esegui i test per garantire che le e-mail vengano ricevute correttamente tramite l’istanza di produzione del Centro messaggi.
1. Esegui test del flusso di lavoro in produzione per garantire che le consegne siano ricevute.

#### Mid-sourcing

Nel contesto di un ambiente di mid-sourcing, è necessario eseguire questi passaggi aggiuntivi per aggiornare:

1. Contatta [l&#39;Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per coordinare l&#39;aggiornamento del server Mid-Sourcing.
1. Verifica che la versione sia stata aggiornata eseguendo un collegamento di test. Ad esempio:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Il server Mid-Sourcing deve sempre eseguire la stessa versione (o più recente) dei server di marketing.
>

## In caso di conflitti

### Identificare i conflitti

È necessario controllare il risultato della sincronizzazione. Questa procedura viene eseguita solo dai clienti on-premise. Per i clienti in hosting, viene gestito dal team di hosting. Esistono due modi per visualizzare il risultato della sincronizzazione:

Nell&#39;interfaccia della riga di comando, gli errori vengono materializzati da una tripla freccia &#39;>>>&#39; e la sincronizzazione viene interrotta automaticamente. Gli avvisi vengono materializzati da una doppia freccia &#39;>>&#39; e devono essere risolti al termine della sincronizzazione. Al termine del post-aggiornamento, al prompt dei comandi viene visualizzato un riepilogo. Può essere simile al seguente:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Se l’avviso riguarda un conflitto di risorse, è necessario l’attenzione dell’utente per risolverlo.

Il file **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **installationDirectory/var/`<instance-name>`/postupgrade**. Gli errori e gli avvisi sono indicati dagli attributi di errore e di avviso.

### Analizzare i conflitti

**Come è stato trovato un conflitto?**

I conflitti si trovano all’interno del file postupgrade.log sul server in questione o all’interno dell’interfaccia client di Campaign (Amministrazione > Configurazione > Gestione pacchetti > Modifica conflitti).

Il documento con identificatore &quot;stockOverview&quot; e tipo &quot;nms:webApp&quot; è in conflitto con la nuova versione.

Se viene rilevato un conflitto, verifica se le seguenti condizioni corrispondono:

* L&#39;oggetto è stato modificato o personalizzato dal cliente?
* L’oggetto è stato modificato nel prodotto?

Se non si applica nessuna di queste condizioni, si tratta di un falso positivo. Se si applicano entrambe queste condizioni, è stato trovato un vero conflitto.

**L&#39;oggetto è stato modificato dal cliente?**

1. Identificare l&#39;oggetto in conflitto.
1. Chiedere al cliente se ha modificato l&#39;oggetto.
1. C&#39;è qualcosa di insolito nell&#39;oggetto?
1. La data dell&#39;ultima modifica è impostata nel codice dell&#39;oggetto?
1. Esaminate il codice XML dal conflitto per gli attributi &quot;_conflitto&quot;. Ti sembra una personalizzazione?

**L&#39;oggetto è stato modificato nella nuova compilazione?**

1. Qualche &quot;solito sospetto&quot;? Applicazioni web o rapporti incorporati (ad esempio, &quot;deliveryValidation&quot;, &quot;deliveryOverview&quot;, &quot;budget&quot;).
1. Esaminare i registri delle modifiche per individuare eventuali aggiornamenti.
1. Chiedi agli esperti di Adobe Campaign.
1. Esegui una &quot;diff&quot; sul codice.

### Risolvere un conflitto

Per risolvere i conflitti, attenersi alla seguente procedura:

1. In Adobe Campaign Explorer, vai a **Amministrazione > Configurazione > Gestione pacchetti > Modifica conflitti**.

1. Selezionare il conflitto che si desidera risolvere nell&#39;elenco.
Sono disponibili tre opzioni per risolvere i conflitti: **Accetta la nuova versione**, **Mantieni la versione corrente**, **Unisci il codice (e dichiaralo risolto)**, **Ignora il conflitto (scelta non consigliata)**.

**Quando posso accettare la nuova versione?**

* Se desiderate utilizzare le feature standard.
* Se non hai personalizzazioni (tutte le personalizzazioni verranno rimosse)

**Quando posso mantenere la versione corrente?**

* Se disponi di personalizzazioni
* Se non si desidera eseguire l&#39;unione
* Se non è necessario correggere l&#39;oggetto in conflitto dall&#39;aggiornamento

**Quando eseguire un&#39;unione?**

* È possibile unire solo maschere, report e applicazioni Web.
* Alcune unioni minori possono essere risolte senza comprendere il codice.
* Unioni più complesse dovrebbero essere eseguite da un utente con le competenze e le capacità appropriate.
* Vedere [Eseguire un&#39;unione](#perform-a-merge).

**Cosa succede se ignoro i conflitti?**

* Il conflitto rimarrà
* L&#39;oggetto non verrà aggiornato
* Impatti a lungo termine: incompatibilità di versione, il cliente non trarrà vantaggio dalle correzioni di bug.

>[!IMPORTANT]
>Si consiglia vivamente di risolvere i conflitti.
>

### Eseguire un&#39;unione{#perform-a-merge}

Esistono diversi tipi di unione:

1. Unione semplice: gli elementi personalizzati e nuovi sono piccoli e non correlati e non è richiesta alcuna codifica.
1. Nessuna modifica: accetta la nuova versione, cambia solo la data dell’ultimo aggiornamento, solo commenti, tabulazioni, spazi o nuove righe. Esempio: salvataggio accidentale.
1. Modifiche banali: è stata modificata solo una riga. Esempio: xpathToLoad
1. Unione complessa: quando è richiesta la codifica. Sono necessarie competenze di sviluppo. Vedi [Unioni complesse](#complex-merges).

#### Come si esegue l&#39;unione?

1. Scarica tutte e tre le versioni: la versione originale, la nuova versione e la versione personalizzata.
1. Esegui una &quot;differenza&quot; tra la versione originale e quella nuova.
1. Isolare le modifiche.
1. Se non vengono apportate modifiche, risolvi il problema mantenendo la versione corrente.

#### Dove trovare il codice?

1. Il codice incorporato viene memorizzato in file XML nella cartella del datakit. Trovare il file XML corrispondente all&#39;oggetto in conflitto. Esempio: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recuperare la versione originale tramite l&#39;[Area download](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) o un&#39;altra installazione non aggiornata del prodotto.
1. Recupera la nuova versione tramite l&#39;[Area download](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html) o i file installati del cliente.
1. Recuperare la versione personalizzata: recupera il codice sorgente dell’oggetto dall’interno del client Campaign.

### Come fare una differenza?

1. Installare un editor di testo o di unione, ad esempio Blocco note ++, AraxisMerge, WinMerge.
1. Apri il file originale e il nuovo file nell’editor.
1. Esegui la differenza (confronta i due file).
1. Identifica eventuali differenze.

### Come si esegue l&#39;unione?

1. Inizia dalla versione personalizzata.
1. Applica le modifiche.
1. Risolvere il conflitto dichiarandolo risolto.
1. Verificare la presenza di non regressioni.

Se si sceglie di risolvere il conflitto manualmente, procedere come segue:

1. Nella sezione inferiore della finestra, cerca la **_stringa_conflitto_** per individuare le entità con conflitti. L’entità installata con la nuova versione contiene il nuovo argomento, l’entità che corrisponde alla versione precedente contiene l’argomento personalizzato.
1. Elimina la versione che non desideri mantenere. Eliminare la stringa **_conflitto_argomento_** dell&#39;entità che si desidera mantenere.
1. Passare al conflitto risolto. Fai clic sull&#39;icona **Azioni** e seleziona **Dichiara come risolte**.
1. Salva le modifiche: il conflitto è stato risolto.

#### Unioni complesse{#complex-merges}

1. Scopri le funzioni della modifica: decodificare le modifiche, esaminare i registri di modifica e consultare gli esperti di Adobe Campaign.
1. Decidi cosa fare con la modifica.
1. Informazioni sulle personalizzazioni: decodificare le modifiche

Di seguito sono riportati i passaggi per eseguire un’unione complessa:

1. Copiare bit di codice dal set di modifiche
1. Incolla nella versione personalizzata
1. Test di non regressione della personalizzazione
1. Verifica della funzione delle modifiche
1. Esegui test di accettazione utente
1. Esecuzione in ambiente di test


>[!IMPORTANT]
>Per eseguire unioni complesse sono necessarie competenze di sviluppo.
>

**Argomenti correlati**

* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Note sulla versione di Campaign Classic](../../rn/using/rn-overview.md)
* [Opzioni di assistenza e supporto per Campaign Classic](../../support.md)
* [Programma di aggiornamento annuale della campagna](../../rn/using/rn-overview.md)
