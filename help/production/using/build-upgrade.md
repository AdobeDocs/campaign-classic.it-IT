---
solution: Campaign Classic
product: campaign
title: Guida introduttiva agli aggiornamenti di build
description: Scopri i passaggi chiave per effettuare l'aggiornamento a una nuova build
audience: production
content-type: reference
topic-tags: updating-adobe-campaign
translation-type: tm+mt
source-git-commit: 5b35d2ffdd0f591e2fe31dc98a54be9ea0c0c18d
workflow-type: tm+mt
source-wordcount: '2368'
ht-degree: 0%

---


# Esecuzione di un aggiornamento della build{#performing-a-build-upgrade}

In questa sezione viene fornita una dettagliata panoramica sul processo di aggiornamento e sui passaggi per identificare e risolvere i conflitti.

L&#39;aggiornamento della costruzione deve essere effettuato con cautela, i suoi impatti devono essere presi in considerazione in anticipo e la procedura deve essere completata con un alto livello di disciplina. Per garantire il successo dell’aggiornamento, accertatevi che solo gli utenti esperti eseguano i passaggi descritti di seguito. Inoltre, consigliamo vivamente di contattare l&#39;Assistenza clienti [ Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) prima di avviare qualsiasi aggiornamento.

Sono necessari i seguenti prerequisiti:

* Conoscenza dell&#39;architettura della campagna
* Conoscenza dei sistemi e del lato server
* Diritti e autorizzazioni amministrativi

Ulteriori informazioni sono disponibili nelle sezioni seguenti: [Aggiornamento  Adobe Campaign](../../production/using/upgrading.md), [Migrazione a una nuova versione](../../migration/using/about-migration.md).

Per le istanze ospitate e ibride, è necessario richiedere l&#39;aggiornamento della build al team  Operazioni tecniche di Adobe. Per ulteriori informazioni, consultare la sezione Domande frequenti in fondo alla pagina. Consultare anche le [domande frequenti sull&#39;aggiornamento della build](../../platform/using/faq-build-upgrade.md).

## Preparare l&#39;aggiornamento

![](assets/do-not-localize/icon_planification.png)

Prima di avviare l&#39;aggiornamento della build, è necessario eseguire una preparazione completa come descritto di seguito.
Una volta che il sistema è pronto per essere aggiornato, un aggiornamento della build richiede **almeno** 2 ore.

Il processo di aggiornamento della build richiede le risorse seguenti:

* un architetto  Adobe: per comprendere le strutture del database (schemi out-of-the-box ed eventuali schemi aggiuntivi aggiunti, le progettazioni delle campagne e tutte le funzionalità critiche del percorso che devono essere avviate e testate in un ordine specifico).
* un project manager: nel caso in cui l&#39;aggiornamento della build coinvolga molti casi diversi (produzione, staging, test) e altri server e applicazioni di terze parti (database, siti SFTP, provider di servizi di messaggistica), è consigliabile che un project manager coordini tutti i test.
* un amministratore Adobe Campaign : l&#39;amministratore conosce la configurazione del server, che include, tra l&#39;altro: requisiti di sicurezza, layout delle cartelle, reporting e importazione\esportazione. Non eseguire un aggiornamento della build senza l&#39;amministratore.
* operatore Adobe Campaign  (utente di marketing): un aggiornamento di successo dipende dalla capacità dell&#39;utente di eseguire le proprie attività quotidiane con successo. Per questo motivo, includete sempre almeno uno degli operatori giornalieri nel test dei server aggiornati.

### Pianificazione

Seguono alcuni punti chiave su come pianificare un aggiornamento della build:

1. Riservare almeno 2 ore per l&#39;aggiornamento.
1. Distribuire i dati di contatto per  Adobe e personale cliente.
1. Per le istanze ospitate:  Adobe e personale cliente coordineranno l&#39;ora dell&#39;aggiornamento e chi eseguirà l&#39;aggiornamento.
1. Per le istanze locali: il personale clienti gestisce l&#39;intero processo - se è necessario fornire assistenza per testare flussi di lavoro personalizzati e per la logica di distribuzione, è necessario fornire servizi di consulenza.
1. Determinare e confermare la versione di  Adobe Campaign a cui effettuare l&#39;aggiornamento: consultare le [note sulla versione di Adobe Campaign Classic](../../rn/using/rn-overview.md).
1. Confermare il possesso di eseguibili di aggiornamento.

### Persone chiave

Il processo di aggiornamento della build richiede il coinvolgimento delle seguenti persone:

*  architetto Adobe: per le architetture ospitate o ibride, l&#39;architetto deve coordinarsi con  Adobe Campaign Client Care.

* Project Manager:
   * per le installazioni aziendali interne: il Project Leader interno del cliente è leader nell&#39;aggiornamento e gestisce i test del ciclo di vita.

   * per l&#39;installazione ospitata: il team di hosting collaborerà con il team di assistenza clienti  Adobe Campaign e il cliente per coordinare la cronologia dell&#39;aggiornamento per tutte le istanze.

* Amministratore Adobe Campaign :
   * per le installazioni aziendali interne: l&#39;amministratore esegue l&#39;aggiornamento.

   * per le installazioni ospitate: il team di hosting esegue l&#39;aggiornamento.

*  operatore Adobe Campaign\utente marketing: l&#39;operatore esegue test sulle istanze di sviluppo, test e produzione.

### Preparare l&#39;aggiornamento della build

Prima di avviare l&#39;aggiornamento della build, i clienti interni devono eseguire la seguente preparazione:

1. Assicurati che qualsiasi lavoro di sviluppo possa essere esportato prima dell&#39;aggiornamento, esportato come pacchetti.

1. Eseguire un backup completo dei database per tutte le istanze degli ambienti di origine e di destinazione.

1. Ottenere la versione più recente del file di configurazione [server ](../../installation/using/the-server-configuration-file.md).

1. Scaricate la build più recente. [Scopri di più sul Centro](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) download.

È inoltre necessario conoscere tutte le [utili righe di comando](../../installation/using/command-lines.md) prima di avviare un aggiornamento della build:

* **nlserver pdump**: elenca i processi in esecuzione
* **nlserver pdump -who**: elenca le sessioni client attive
* **monitor nlserver -missing**: elenca le proprietà mancanti
* **avvio nlserver process@instanceName**: avvia un processo
* **server di arresto process@instanceName**: interrompe un processo
* **riavvio del server process@instanceName**: riavvia un processo
* **arresto** nlserver: arresta tutti i processi Campaign
* **nlserver watchdog -svc**: avvia il watchdog (solo UNIX)

## Eseguire l&#39;aggiornamento

![](assets/do-not-localize/icon_process.png)

Le procedure riportate di seguito sono eseguite solo dai clienti **locali**. Per i clienti ospitati, è gestito dal team di hosting. Per aggiornare  Adobe Campaign a una nuova build, la procedura dettagliata è descritta di seguito.

### Duplicare l&#39;ambiente

Di seguito viene illustrato come duplicare un ambiente Adobe Campaign , al fine di ripristinare un ambiente di origine in un ambiente di destinazione, ottenendo due ambienti di lavoro identici.

Per farlo, segui la procedura indicata di seguito:

1. Create una copia dei database su tutte le istanze nell&#39;ambiente di origine.

1. Ripristinare queste copie in tutte le istanze dell&#39;ambiente di destinazione.

1. Eseguire lo script di cauterizzazione **nms:FrostInstance.js** nell&#39;ambiente di destinazione prima di avviarlo. In questo modo tutti i processi che interagiscono con l&#39;esterno verranno interrotti: registri, tracciamento, consegne, flussi di lavoro delle campagne, ecc.

   ```
   nlserverjavacsriptnms:freezeInstance.js–instance:<dev> -arg:run
   ```

1. Controllare la cauterizzazione, come segue:

   * Verificare che l&#39;unica parte di consegna sia quella con ID impostato su **0**:

      ```
      SELECT * FROM neolane.nmsdeliverypart;
      ```

   * Verificate che l&#39;aggiornamento dello stato di consegna sia corretto:

      ```
      SELECT iSate, count(*) FROM neolane.nmsdeliveryGroup By iProd;
      ```

   * Verificare che l&#39;aggiornamento dello stato del flusso di lavoro sia corretto:

      ```
      SELECT iState, count (*) FROM neolane.xtkworkflowGROUP BY iState;
      SELECT iStatus, count (*) FROM neolane.xtkworkflowGROUP BY iStatus;
      ```

### Arrestare i servizi

Per sostituire tutti i file con la nuova versione, è necessario che tutte le istanze del servizio nlserverservice siano chiuse.

1. Arrestate i seguenti servizi:

   * Servizi Web (IIS): **iisreset /stop**
   *  servizio Adobe Campaign: **net stop nlserver6**

   >[!NOTE]
   >
   >Assicurarsi che il server di reindirizzamento (webmdl) sia arrestato, in modo che il file nlsrvmod.dll utilizzato da IIS possa essere sostituito con la nuova versione.

1. Verificare che non siano attive attività eseguendo il comando **nlserver pdump**. Se non sono presenti attività, l&#39;output deve essere simile a quanto segue:

   ```
   C:\<installation path>\bin>nlserverpdump HH:MM:SS > Application Server for Adobe Campaign version x.x (build xxx) dated xx/xx/xxxx No tasks
   ```

1. Controllare Task Manager di Windows per confermare che tutti i processi sono stati interrotti.

### Aggiornamento dell&#39;applicazione Adobe Campaign Server 

1. Eseguire il file **Setup.exe**. Se devi scaricare questo file, accedi a [Centro download](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html).

1. Selezionate la modalità di installazione: **Aggiornamento** o **riparazione**.

1. Fare clic su **Next**.

1. Fare clic su **Fine**: il programma di installazione copia i nuovi file.

1. Al termine dell&#39;operazione, fare clic su **Fine**.

### Sincronizzare le risorse

1. Aprite la riga di comando.

1. Eseguire **configurazione del server nlserver -postupgrade -allinstance** per eseguire le operazioni seguenti:

   * Sincronizzare le risorse
   * Aggiorna schemi
   * Aggiornare il database

   >[!NOTE]
   >
   >Questa operazione deve essere eseguita una sola volta e solo su un server applicazione nlserverweb.

   Per sincronizzare un solo database, eseguite il comando seguente:

   ```
   nlserver config -postupgrade -instance: <instance_name>
   ```

1. Verificate se la sincronizzazione ha generato errori o avvisi.

### Riavvia servizi

È necessario riavviare i servizi seguenti:

* Servizi Web (IIS): **issreset /start**
*  servizio Adobe Campaign: **net start nlserver6**

### Aggiornamento delle console client

La console client deve trovarsi nella stessa build dell&#39;istanza server.

Nel computer in cui è installato il server applicazioni Adobe Campaign  (nlserverweb), scaricate e copiate il file:

```
Setup-client-7.xxxx.exe in [path of the application]\datakit\nl\en\jsp
```

Alla successiva connessione delle console client, una finestra informerà gli utenti della disponibilità di un nuovo aggiornamento e offrirà loro la possibilità di scaricarlo e installarlo.

### Attività aggiuntive specifiche

Alcune configurazioni richiedono specifiche attività aggiuntive per l&#39;aggiornamento a una nuova build.

#### Messaggi transazionali

Quando Messaggi transazionali (Centro messaggi) è abilitato nell&#39;istanza Campaign, devi eseguire i seguenti passaggi aggiuntivi per effettuare l&#39;aggiornamento:

1. Aggiorna il server di produzione di Message Center alla versione scelta.
1. Eseguire gli script postupgrade.
1. Eseguite i test e assicuratevi che i messaggi e-mail vengano ricevuti correttamente tramite l&#39;istanza di produzione del Centro messaggi.
1. Aggiornare i client e cancellare la cache.
1. Pacchetti di esportazione:
   * Esportare pacchetti con lo strumento di esportazione del pacchetto client
   * Importa pacchetto schema
   * Disconnessione e riconnessione del client
   * Aggiorna database
   * Disconnessione e riconnessione
   * Importa pacchetto Amministratore
   * Importa pacchetto di contenuto
   * Importa pacchetto di gestione dei contenuti
   * Disconnessione e riconnessione
   * Verifica rapida dei flussi di lavoro

1. Pubblicare i modelli di Centro messaggi per assicurare il funzionamento dell’interfaccia tra i server e l’istanza del Centro messaggi.
1. Eseguite i test per verificare che le e-mail vengano ricevute correttamente tramite l&#39;istanza di produzione del Centro messaggi.
1. Eseguite i test del flusso di lavoro in produzione per verificare che le consegne vengano ricevute.

#### Media-sourcing

Nel contesto di un ambiente di mid-sourcing, devi eseguire i seguenti passaggi aggiuntivi per aggiornare:

1. Contattate l&#39;Assistenza clienti [ Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per coordinare l&#39;aggiornamento del server Media Source.
1. Verificare che la versione sia stata aggiornata mediante un collegamento di prova. Ad esempio:

   ```
   http://[InsertServerURL]/r/test
   ```

>[!NOTE]
>
>Il server di origine media deve sempre eseguire la stessa versione (o più recente) dei server di marketing.


## In caso di conflitti

### Identificare i conflitti

È necessario verificare il risultato della sincronizzazione. Questa procedura viene eseguita solo dai clienti interni. Per i clienti ospitati, è gestito dal team di hosting. Esistono due modi per visualizzare il risultato della sincronizzazione:

Nell&#39;interfaccia della riga di comando, gli errori vengono generati da una tripla freccia &#39;>>>&#39; e la sincronizzazione viene arrestata automaticamente. Le avvertenze vengono materializzate da una doppia freccia &#39;>>&#39; e devono essere risolte una volta completata la sincronizzazione. Alla fine del post aggiornamento, nel prompt dei comandi viene visualizzato un riepilogo. Può essere simile al seguente:

```
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log =========Summary of the update==========
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 info log <instance name> instance, 6 warning(s) and 0 error(s) during the update.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.749Z 00002E7A 1 warning log The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
YYYY-MM-DD HH:MM:SS.750Z 00002E7A 1 warning log Document of identifier 'nms:includeView‘ and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
```

Se l&#39;avviso riguarda un conflitto di risorse, è necessario prestare attenzione alla risoluzione del problema.

Il file **postupgrade_ServerVersionNumber_TimeOfPostupgrade.log** contiene il risultato della sincronizzazione. È disponibile per impostazione predefinita nella seguente directory: **installDirectory/var/instanceName/postupgrade**. Gli errori e gli avvisi sono indicati dagli attributi di errore e avviso.

### Analisi dei conflitti

**Come si trova un conflitto?**

I conflitti si trovano all&#39;interno del post upgrade.log sul server in questione o nell&#39;interfaccia client di Campaign (Amministrazione > Configurazione > Gestione pacchetti > Modifica conflitti).

Il documento con l’identificatore ‘stockOverview’ e il tipo ‘nms:webApp’ è in conflitto con la nuova versione.

Se viene rilevato un conflitto, verificate che le seguenti condizioni corrispondano:

* L&#39;oggetto è stato modificato o personalizzato dal cliente?
* L&#39;oggetto è stato modificato nel prodotto?

Se nessuna di queste condizioni è valida, si tratta di un falso positivo. Se si applicano entrambe queste condizioni, è stato trovato un vero conflitto.

**L&#39;oggetto è stato modificato dal cliente?**

1. Identificare l&#39;oggetto in conflitto.
1. Chiedere al cliente se ha modificato l&#39;oggetto.
1. C&#39;è qualcosa di insolito con l&#39;oggetto?
1. La data dell&#39;ultima modifica è impostata nel codice dell&#39;oggetto?
1. Esaminate il codice XML dal conflitto per gli attributi &quot;_Conflitti&quot;. Sembra una personalizzazione?

**L&#39;oggetto è stato modificato nella nuova build?**

1. Qualche &quot;solito sospetto?&quot; Applicazioni Web o rapporti incorporati (ad esempio: &#39;deliveryValidation&#39;, &#39;deliveryOverview&#39;, &#39;budget&#39;).
1. Esaminate i registri delle modifiche per eventuali aggiornamenti.
1. Chiedete  esperti Adobe Campaign.
1. Eseguire una &quot;diff&quot; sul codice.

### Risoluzione di un conflitto

Per risolvere i conflitti, eseguire il seguente processo:

1. In Adobe Campaign Explorer , andate a **Amministrazione > Configurazione > Gestione pacchetti > Modifica conflitti**.

1. Selezionare il conflitto da risolvere nell&#39;elenco.
Esistono tre opzioni per risolvere i conflitti: **Accettare la nuova versione**, **Mantenere la versione corrente**, **Unire il codice (e dichiarare come risolto)**, **Ignorare il conflitto (non consigliato)**.

**Quando posso accettare la nuova versione?**

* Se desiderate le funzioni standard.
* Se non disponete di personalizzazioni (tutte le personalizzazioni verranno rimosse)

**Quando posso mantenere la versione corrente?**

* Se disponete di personalizzazioni
* Se non si desidera unire
* Se non sono necessarie correzioni all&#39;oggetto in conflitto dall&#39;aggiornamento

**Quando eseguire un&#39;unione?**

* È possibile unire solo moduli, rapporti e applicazioni Web.
* Alcune piccole unioni possono essere risolte senza comprendere il codice.
* Le fusioni più complesse dovrebbero essere eseguite da un utente con le competenze e le capacità adeguate.
* Vedere [Eseguire un&#39;unione](#perform-a-merge).

**E se ignorassi i conflitti?**

* Il conflitto rimarrà
* L&#39;oggetto non verrà aggiornato
* Impatto a lungo termine: incompatibilità delle versioni, il cliente non trarrà alcun beneficio dalle correzioni dei bug.

>[!IMPORTANT]
>Si consiglia vivamente di risolvere i conflitti.


### Eseguire un&#39;unione{#perform-a-merge}

Esistono diversi tipi di unione:

1. Unione semplice: gli elementi personalizzati e nuovi sono piccoli e non correlati, e non è necessaria alcuna codifica.
1. Nessuna modifica: accetta nuova versione, cambia solo la data dell&#39;ultimo aggiornamento, solo commenti, schede, spazi o nuove righe. Esempio: salvataggio accidentale.
1. Modifiche ripetitive: è cambiata solo una riga. Esempio: xpathToLoad
1. Unione complessa: quando la codifica è obbligatoria. Sono necessarie capacità di sviluppo. Vedere [Unioni complesse](#complex-merges).

#### Come si unisce?

1. Ottenete tutte e tre le versioni: la versione originale, la nuova versione e la versione personalizzata.
1. Eseguite una &quot;diff&quot; tra la versione originale e quella nuova.
1. Isolare le modifiche.
1. Se non vengono apportate modifiche, risolvete il problema mantenendo la versione corrente.

#### Dove trovare il codice?

1. Il codice predefinito viene memorizzato in file XML nella cartella del dataKit. Individuare il file XML che corrisponde all&#39;oggetto in conflitto. Esempio: installationDirectory\datakit\nms\fra\form\recipient.xml
1. Recuperate la versione originale: tramite il [Centro di download](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) o un&#39;altra installazione non aggiornata del prodotto.
1. Recuperate la nuova versione: tramite il [Centro di download](https://docs.adobe.com/content/help/en/experience-cloud/software-distribution/home.html) o i file installati dal cliente.
1. Recuperate la versione personalizzata: recupera il codice sorgente dell&#39;oggetto dall&#39;interno del client Campaign.

### Come fare una diff?

1. Installate un editor di testo o di unione, ad esempio Blocco note ++, AraxisMerge, WinMerge.
1. Aprite il file originale e il nuovo file nell’editor.
1. Eseguite la diff (confrontate i due file).
1. Identificare eventuali differenze.

### Come si unisce?

1. Iniziate dalla versione personalizzata.
1. Applicate le modifiche.
1. Risolvere il conflitto dichiarandolo come risolto.
1. Verificare la presenza di non regressioni.

Se scegliete di risolvere il conflitto manualmente, procedete come segue:

1. Nella sezione inferiore della finestra, cercare la **_stringa_conflitto_** per individuare le entità con conflitti. L&#39;entità installata con la nuova versione contiene il nuovo argomento, l&#39;entità che corrisponde alla versione precedente contiene l&#39;argomento personalizzato.
1. Eliminate la versione che non desiderate mantenere. Eliminate la stringa **_conflitto_argomento_** dell&#39;entità da mantenere.
1. Vai al conflitto risolto. Fare clic sull&#39;icona **Actions** e selezionare **Dichiara come risolto**.
1. Salvare le modifiche: il conflitto ora è risolto.

#### Unioni complesse{#complex-merges}

1. Comprendere le operazioni eseguite dalla modifica: decodificare le modifiche, esaminare i registri delle modifiche e seguire  esperti Adobe Campaign.
1. Decidete cosa fare con il cambiamento.
1. Comprendere le operazioni di personalizzazione: decodificare le modifiche

Di seguito sono riportati i passaggi per eseguire un&#39;unione complessa:

1. Copiare bit di codice dal set di modifiche
1. Incolla sulla versione personalizzata
1. Test per non regressioni di personalizzazione
1. Test per la funzione dei cambiamenti
1. Esegui test di accettazione utente
1. Eseguire in ambiente di test


>[!IMPORTANT]
>Le competenze di sviluppo sono necessarie per eseguire complesse operazioni di unione.


**Argomenti correlati**

* [Domande frequenti sull&#39;aggiornamento della build](../../platform/using/faq-build-upgrade.md)
* [Note sulla versione Campaign Classic](../../rn/using/rn-overview.md)
* [Opzioni di assistenza e supporto per Campaign Classic](https://helpx.adobe.com/campaign/kb/ac-support.html#acc-support-req)
* [Programma Gold Standard](https://helpx.adobe.com/it/campaign/kb/gold-standard.html)