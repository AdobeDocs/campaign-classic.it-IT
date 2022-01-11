---
product: campaign
title: Guida introduttiva agli aggiornamenti della build
description: Scopri i passaggi chiave per l’aggiornamento a una nuova build
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
exl-id: c5a9c99a-4078-45d8-847b-6df9047a2fe2
source-git-commit: 1d32161d60f6b382188012b104c642f504e28645
workflow-type: tm+mt
source-wordcount: '2356'
ht-degree: 3%

---

# Esecuzione di un aggiornamento della build{#performing-a-build-upgrade}

![](../../assets/v7-only.svg)

Questa sezione fornisce una descrizione dettagliata del processo di aggiornamento e dei passaggi per identificare e risolvere i conflitti.

L&#39;aggiornamento della build deve essere effettuato con cautela, i suoi impatti devono essere considerati in anticipo e la procedura deve essere completata con un elevato livello di disciplina. Per garantire il successo dell’aggiornamento, assicurati che solo gli utenti esperti eseguano i passaggi descritti di seguito. Inoltre, consigliamo vivamente di entrare in contatto con [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) prima di avviare qualsiasi aggiornamento.

Sono necessari i seguenti prerequisiti:

* Informazioni sull’architettura di Campaign
* Conoscenza dei sistemi e del lato server
* Diritti e autorizzazioni amministrativi

Puoi trovare ulteriori informazioni in queste sezioni: [Aggiornamento di Adobe Campaign](../../production/using/upgrading.md), [Migrazione a una nuova versione](../../migration/using/about-migration.md).

Per le istanze in hosting e ibride, è necessario richiedere l’aggiornamento della build al team di Adobe Technical Operations. Per ulteriori informazioni, consulta la sezione Domande frequenti in basso se questa pagina. Consulta anche [domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md).

## Preparare l&#39;aggiornamento

![](assets/do-not-localize/icon_planification.png)

Prima di avviare l’aggiornamento della build, devi eseguire una preparazione completa come descritto di seguito.
Una volta che il sistema è pronto per essere aggiornato, un aggiornamento della build richiede **almeno** 2 ore.

Il processo di aggiornamento della build richiede le seguenti risorse:

* un architetto di Adobe: per comprendere le strutture del database (schemi predefiniti e tutti gli schemi aggiuntivi aggiunti, le progettazioni delle campagne e tutte le funzionalità critiche del percorso che devono essere avviate e testate in un ordine specifico).
* un project manager: nel caso in cui l&#39;aggiornamento della build coinvolga diverse istanze (produzione, staging, test) e altri server e applicazioni di terze parti (database, siti SFTP, fornitori di servizi di messaggistica), è consigliabile che un project manager coordini tutti i test.
* un amministratore Adobe Campaign : il tuo amministratore conosce la configurazione del server, che include ma non si limita a: requisiti di sicurezza, layout delle cartelle, reporting e importazione\esportazione. Non eseguire un aggiornamento della build senza l&#39;amministratore.
* un operatore Adobe Campaign (utente di marketing) : un aggiornamento riuscito si basa sulla capacità dell’utente di eseguire correttamente le attività quotidiane. Per questo motivo, includi sempre almeno uno degli operatori giornalieri nel test dei server aggiornati.

### Pianificazione

Di seguito sono riportati i punti chiave su come pianificare un aggiornamento della build:

1. Riserva almeno 2 ore per l&#39;aggiornamento.
1. Distribuire i dati di contatto per Adobe e personale cliente.
1. Per le istanze in hosting: L’Adobe e il personale cliente coordineranno l’ora dell’aggiornamento e l’utente che verrà eseguito.
1. Per le istanze on-premise: il personale clienti gestisce l&#39;intero processo: se è necessaria assistenza per testare flussi di lavoro personalizzati e la logica di distribuzione, è necessario fornire servizi di consulenza.
1. Determina e conferma la versione di Adobe Campaign a cui desideri eseguire l&#39;aggiornamento - consulta la sezione [Note sulla versione di Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Conferma il possesso dei file eseguibili di aggiornamento.

### Persone chiave

Il processo di aggiornamento della build richiede il coinvolgimento delle seguenti persone:

* Architetto Adobe: per le architetture ospitate o ibride, l’architetto deve coordinarsi con l’Assistenza clienti Adobe Campaign.

* Gestione progetti:
   * per installazioni on-premise: il Project Leader interno del cliente guida l&#39;aggiornamento e gestisce i test del ciclo di vita.

   * per installazione in hosting: il team di hosting collaborerà con il team di assistenza clienti Adobe Campaign e il cliente per coordinare la cronologia dell’aggiornamento per tutte le istanze.

* Amministratore Adobe Campaign:
   * per installazioni on-premise: l&#39;amministratore esegue l&#39;aggiornamento.

   * per installazioni in hosting: il team di hosting esegue l&#39;aggiornamento.

* Operatore Adobe Campaign\utente marketing: l’operatore esegue test sulle istanze di sviluppo, test e produzione.

### Preparare l’aggiornamento della build

Prima di avviare l’aggiornamento della build, i clienti on-premise devono eseguire la seguente preparazione:

1. Assicurati che qualsiasi lavoro di sviluppo possa essere esportato prima dell&#39;aggiornamento, esportato come pacchetti.

1. Esegui un backup completo dei database per tutte le istanze degli ambienti di origine e di destinazione.

1. Scarica la versione più recente del tuo [file di configurazione del server](../../installation/using/the-server-configuration-file.md).

1. [Scarica la build più recente](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html). [Ulteriori informazioni](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=it).

Devi anche sapere tutte le [linee di comando utili](../../installation/using/command-lines.md) prima di avviare un aggiornamento della build:

* **pdump nlserver**: elenchi dei processi in esecuzione
* **nlserver pdump -who**: elenca le sessioni client attive
* **monitor nlserver - mancante**: elenca le proprietà mancanti
* **avvio server process@instanceName**: avvia un processo
* **arresto del server process@instanceName**: interrompe un processo
* **riavvio del server process@instanceName**: riavvia un processo
* **chiusura nlserver**: interrompe tutti i processi di Campaign
* **nlserver watchdog -svc**: avvia il watchdog (solo UNIX)

## Esegui l&#39;aggiornamento

![](assets/do-not-localize/icon_process.png)

Le procedure seguenti vengono eseguite solo da **on-premise** clienti. Per i clienti in hosting, è gestito dal team di hosting. Per aggiornare Adobe Campaign a una nuova build, la procedura dettagliata è descritta di seguito.

### Duplicare l’ambiente

È possibile duplicare un ambiente Adobe Campaign per ripristinare un ambiente di origine in un ambiente di destinazione, in modo da ottenere due ambienti di lavoro identici.

Per farlo, segui la procedura indicata di seguito:

1. Crea una copia dei database su tutte le istanze nell&#39;ambiente di origine.

1. Ripristina queste copie su tutte le istanze dell’ambiente di destinazione.

1. Esegui il **nms:frozenInstance.js** script di cauterizzazione nell’ambiente di destinazione prima di avviarlo. In questo modo tutti i processi che interagiscono con l&#39;esterno verranno interrotti: registri, tracciamento, consegne, flussi di lavoro per campagne, ecc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Controllare la cauterizzazione come segue:

   * Verifica che l’unica parte di consegna sia quella con ID impostato su **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * Verifica che l’aggiornamento dello stato di consegna sia corretto:

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * Verifica che l’aggiornamento dello stato del flusso di lavoro sia corretto:

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### Servizi di arresto

Per sostituire tutti i file con la nuova versione, è necessario che tutte le istanze del servizio nlserverservice siano spente.

1. Spegni i seguenti servizi:

   * Servizi Web (IIS): **iisreset /stop**
   * Servizio Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Assicurati che il server di reindirizzamento (webmdl) sia arrestato, in modo che il file nlsrvmod.dll utilizzato da IIS possa essere sostituito con la nuova versione.

1. Convalida che nessuna attività sia attiva eseguendo il **pdump nlserver** comando. In assenza di attività, l&#39;output deve essere simile al seguente:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Controllare Gestione attività di Windows per confermare che tutti i processi sono stati interrotti.

### Aggiornare l’applicazione server Adobe Campaign

1. Esegui il **Setup.exe** file. Se devi scaricare questo file, accedi a [il Centro download](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html).

1. Seleziona la modalità di installazione: **Aggiorna** o **Riparazione**.

1. Fai clic su **Successivo**.

1. Fai clic su **Fine**: il programma di installazione copia i nuovi file.

1. Al termine dell&#39;operazione, fai clic su **Fine**.

### Sincronizzare le risorse

1. Apri la riga di comando.

1. Esegui **nlserver config -postupgrade -allinstances** per eseguire le seguenti operazioni:

   * Sincronizzare le risorse
   * Aggiorna schemi
   * Aggiornare il database

   >[!NOTE]
   >
   >Questa operazione deve essere eseguita una sola volta e solo su un server applicazioni web nlserverweb.

   Per sincronizzare un solo database, esegui il comando seguente:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Controlla se la sincronizzazione ha generato errori o avvisi.

### Riavvia i servizi

È necessario riavviare i seguenti servizi:

* Servizi Web (IIS): **issreset /start**
* Servizio Adobe Campaign: **net start nlserver6**

### Aggiornamento delle console client

La console client deve trovarsi nella stessa build dell’istanza server.

Sul computer in cui è installato l’application server di Adobe Campaign (nlserverweb), scarica e copia il file:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Alla successiva connessione delle console client, una finestra informa gli utenti della disponibilità di un nuovo aggiornamento e offre loro la possibilità di scaricarlo e installarlo.

### Attività aggiuntive specifiche

Alcune configurazioni richiedono attività aggiuntive specifiche per l&#39;aggiornamento a una nuova build.

#### Messaggistica transazionale

Quando la messaggistica transazionale (Message Center) è abilitata nell’istanza Campaign, devi eseguire questi passaggi aggiuntivi per eseguire l’aggiornamento:

1. Aggiorna il server di produzione del Centro messaggi alla versione scelta.
1. Esegui gli script successivi all’aggiornamento.
1. Esegui i test e assicurati che le e-mail vengano ricevute correttamente tramite l’istanza di produzione Message Center.
1. Aggiorna i client e cancella la cache.
1. Pacchetti di esportazione:
   * Esportare pacchetti utilizzando lo strumento di esportazione del pacchetto client
   * Importa pacchetto schema
   * Disconnetti e riconnette client
   * Aggiorna database
   * Disconnessione e riconnessione
   * Importa pacchetto amministratore
   * Importa pacchetto di contenuti
   * Importa pacchetto di gestione dei contenuti
   * Disconnessione e riconnessione
   * Esegui un controllo rapido dei flussi di lavoro

1. Pubblica i modelli del Centro messaggi per garantire il funzionamento dell’interfaccia tra i server e l’istanza del Centro messaggi.
1. Esegui i test per garantire che le e-mail vengano ricevute correttamente tramite l’istanza di produzione del Centro messaggi .
1. Esegui test del flusso di lavoro in produzione per garantire che le consegne vengano ricevute.

#### Mid-sourcing

Nel contesto di un ambiente di mid-sourcing, devi eseguire questi passaggi aggiuntivi per aggiornare:

1. Contatto [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per coordinare l&#39;aggiornamento del server Mid-Sourcing.
1. Verifica che la versione sia stata aggiornata eseguendo un collegamento di prova. Ad esempio:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Il server di mid-Sourcing deve sempre eseguire la stessa versione (o più recente) dei server di marketing.

## In caso di conflitti

### Identificare i conflitti

È necessario controllare il risultato della sincronizzazione. Questa procedura viene eseguita solo dai clienti on-premise. Per i clienti in hosting, è gestito dal team di hosting. Esistono due modi per visualizzare il risultato della sincronizzazione:

Nell&#39;interfaccia a riga di comando, gli errori vengono materializzati da una tripla freccia &quot;>>&quot; e la sincronizzazione viene arrestata automaticamente. Gli avvisi vengono materializzati da una doppia freccia &quot;>>&quot; e devono essere risolti una volta completata la sincronizzazione. Al termine del post aggiornamento, nel prompt dei comandi viene visualizzato un riepilogo. Può essere così:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Se l’avviso riguarda un conflitto di risorse, è necessario prestare attenzione a risolverlo.

La **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** il file contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **installationDirectory/var/instanceName/postupgrade**. Gli errori e gli avvisi sono indicati dagli attributi di errore e avviso.

### Analizzare i conflitti

**Come si trova un conflitto?**

I conflitti si trovano all’interno del post aggiornamento.log sul server in questione o nell’interfaccia client di Campaign (Amministrazione > Configurazione > Gestione pacchetti > Modifica conflitti).

Il documento con l’identificatore &quot;stockOverview&quot; e il tipo &quot;nms:webApp&quot; è in conflitto con la nuova versione.

Se viene rilevato un conflitto, verifica se le seguenti condizioni corrispondono:

* L’oggetto è stato modificato o personalizzato dal cliente?
* L’oggetto è stato modificato nel prodotto?

Se nessuna di queste condizioni è applicabile, si tratta di un falso positivo. Se entrambe queste condizioni sono applicabili, è stato trovato un vero conflitto.

**L’oggetto è stato modificato dal cliente?**

1. Identificare l&#39;oggetto in conflitto.
1. Chiedi al cliente se ha modificato l’oggetto.
1. C&#39;è qualcosa di insolito nell&#39;oggetto?
1. La data dell’ultima modifica è impostata nel codice dell’oggetto?
1. Esamina il codice XML dal conflitto per gli attributi &quot;_Conflist&quot;. Assomiglia a una personalizzazione?

**L’oggetto è stato modificato nella nuova build?**

1. Qualche &quot;solito sospetto&quot;? Applicazioni web o rapporti incorporati (ad esempio: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Esamina i registri delle modifiche per eventuali aggiornamenti.
1. Chiedi agli esperti Adobe Campaign.
1. Esegui una &quot;diff&quot; sul codice.

### Risolvere un conflitto

Per risolvere i conflitti, applicare il seguente processo:

1. In Adobe Campaign Explorer, vai a **Amministrazione > Configurazione > Gestione pacchetti > Modifica conflitti**.

1. Selezionare il conflitto da risolvere nell&#39;elenco.
Sono disponibili tre opzioni per risolvere i conflitti: **Accettare la nuova versione**, **Mantieni la versione corrente**, **Unisci il codice (e dichiara come risolto)**, **Ignora il conflitto (scelta non consigliata)**.

**Quando posso accettare la nuova versione?**

* Se si desidera utilizzare le funzioni standard.
* Se non disponi di personalizzazioni (tutte le personalizzazioni verranno rimosse)

**Quando posso mantenere la versione corrente?**

* Se disponi di personalizzazioni
* Se non si desidera unire
* Se non è necessario apportare alcuna correzione all&#39;oggetto in conflitto dall&#39;aggiornamento

**Quando eseguire un&#39;unione?**

* È possibile unire solo moduli, rapporti e applicazioni web.
* Alcune fusioni minori possono essere risolte senza comprendere il codice.
* Unioni più complesse dovrebbero essere eseguite da un soggetto con le competenze e le capacità adeguate.
* Vedi [Eseguire un&#39;unione](#perform-a-merge).

**E se ignorassi i conflitti?**

* Il conflitto rimarrà
* L’oggetto non verrà aggiornato
* Impatto a lungo termine: incompatibilità delle versioni, il cliente non beneficerà di correzioni di bug.

>[!IMPORTANT]
>Si consiglia vivamente di risolvere i conflitti.

### Eseguire un&#39;unione{#perform-a-merge}

Esistono diversi tipi di unione:

1. Unione semplice: gli elementi personalizzati e nuovi sono piccoli e non correlati e non è necessaria alcuna codifica.
1. Nessuna modifica: accetta nuova versione, cambia solo la data dell’ultimo aggiornamento, vengono modificati solo i commenti, le schede, gli spazi o le nuove righe. Esempio: salvataggio accidentale.
1. Modifiche di tendenza: cambiò solo una riga. Esempio: xpathToLoad
1. Unione complessa: quando è richiesta la codifica. Sono necessarie le capacità di sviluppo. Vedi [Unioni complesse](#complex-merges).

#### Come fondersi?

1. Ottieni tutte e tre le versioni: la versione originale, la nuova versione e la versione personalizzata.
1. Esegui un &quot;diff&quot; tra la versione originale e quella nuova.
1. Isolare le modifiche.
1. Se non vengono apportate modifiche, è necessario risolvere il problema mantenendo la versione corrente.

#### Dove trovare il codice?

1. Il codice incorporato viene memorizzato in file XML nella cartella del datakit. Individuare il file XML corrispondente all&#39;oggetto in conflitto. Esempio: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recupera la versione originale: tramite [Centro di download](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) o un&#39;altra installazione non aggiornata del prodotto.
1. Recupera la nuova versione: tramite [Centro di download](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html) o i file installati del cliente.
1. Recupera la versione personalizzata: recupera il codice sorgente dell’oggetto dall’interno del client Campaign.

### Come fare una differenza?

1. Installa un editor di testo o unione, ad esempio Blocco note ++, AraxisMerge, WinMerge.
1. Apri il file originale e il nuovo file nell&#39;editor.
1. Esegui il confronto (confronta i due file).
1. Identifica eventuali differenze.

### Come fondersi?

1. Inizia dalla versione personalizzata.
1. Applica le modifiche.
1. Risolvere il conflitto dichiarandolo come risolto.
1. Verifica la non regressione.

Se si sceglie di risolvere il conflitto manualmente, procedere come segue:

1. Nella sezione inferiore della finestra, cerca il **_string_conflitto_** per individuare le entità con conflitti. L&#39;entità installata con la nuova versione contiene il nuovo argomento, l&#39;entità che corrisponde alla versione precedente contiene l&#39;argomento personalizzato.
1. Elimina la versione che non desideri mantenere. Elimina **_conflitto_argomento_** stringa dell&#39;entità che si sta tenendo.
1. Vai al conflitto che hai risolto. Fai clic sul pulsante **Azioni** e seleziona **Dichiara come risolto**.
1. Salva le modifiche: il conflitto è ora risolto.

#### Unioni complesse{#complex-merges}

1. Scopri le operazioni della modifica: decodificare le modifiche, esaminare i registri delle modifiche e seguire le istruzioni degli esperti di Adobe Campaign.
1. Decidi cosa fare con il cambiamento.
1. Scopri le operazioni delle personalizzazioni: decodificare le modifiche

Di seguito sono riportati i passaggi per eseguire un’unione complessa:

1. Copia bit di codice dal set di modifiche
1. Incolla alla versione personalizzata
1. Test di non regressione della personalizzazione
1. Prova della funzione dei cambiamenti
1. Eseguire test di accettazione degli utenti
1. Esecuzione in ambiente di test


>[!IMPORTANT]
>Le competenze di sviluppo sono necessarie per eseguire fusioni complesse.

**Argomenti correlati**

* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Note sulla versione di Campaign Classic](../../rn/using/rn-overview.md)
* [Opzioni di aiuto e supporto per Campaign Classic](../../support.md)
* [Programma di aggiornamento annuale di Campaign](../../rn/using/rn-overview.md)
