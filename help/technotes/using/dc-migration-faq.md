---
product: campaign
title: Domande frequenti sulla migrazione ad Adobe Managed Services (Public Cloud)
description: Domande frequenti sulla migrazione di Campaign Classic a Public Cloud
feature: Overview
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 1f050ada481a7307a59ea6c81290bb0b24a3bf6c
workflow-type: tm+mt
source-wordcount: '2243'
ht-degree: 0%

---

# Domande frequenti sulla migrazione a Public Cloud{#dc-faq}

![](../../assets/v7-only.svg)

Come parte dell’ [Gold Standard Initiative](../../rn/using/gold-standard.md), Adobe decomprime il Data Center legacy. Le istanze di Campaign Classic devono essere trasferite a Public Cloud Amazon Web Services (AWS). [Ulteriori informazioni su questa iniziativa](dc-migration.md).

Di seguito è riportata una serie di domande comuni su questo progetto, sull’impatto sugli ambienti Campaign e su altre risorse utili.

Per qualsiasi altra domanda, puoi rivolgerti ad [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support).

## Effetti dell&#39;infrastruttura

![](assets/do-not-translate/database.png)

Gli impatti globali su database e infrastrutture sono elencati di seguito.

* **Il database cambierà? Qual è la versione del nuovo database? Quale sistema operativo verrà utilizzato?**

   Adobe si riserva il diritto di scegliere e implementare il motore di gestione del database più adatto per fornire Adobe Campaign Service in condizioni ottimali.

   Inoltre, al fine di preservare il miglior livello di sicurezza, l&#39;Adobe non fornirà informazioni dettagliate relative all&#39;infrastruttura.

* **Esiste il rischio di perdita di dati?**

   Il database verrà scaricato dal datacenter legacy e ripristinato in Public Cloud (AWS). Al riavvio del nuovo data center, l&#39;applicazione riprenderà dallo stato esatto in cui si trovava prima della migrazione. Gli utenti non vedranno alcuna differenza, tranne per il fatto che alcune attività pianificate saranno state ritardate.

* **Esistono differenze nelle dimensioni del pacchetto tra il data center legacy e il cloud pubblico?**

   Stiamo effettuando il provisioning in Public Cloud (AWS) con nuove definizioni di pacchetti basate sulle dimensioni correnti del database, sulle dimensioni del disco, ecc. Ad esempio, se un cliente dispone di un server applicazioni nei data center legacy, può disporre di due server applicazioni in Public Cloud (AWS) in base alle definizioni dei pacchetti.

* **Cambierà il numero di build o la versione di Campaign?**

   Come primo passo, manterremo la stessa build Campaign Classic con la migrazione.

   In un ulteriore passaggio, si procederà all’aggiornamento alla build Campaign Classic GA più recente. Per ulteriori informazioni, consulta le [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md) e le [Note sulla versione di Campaign Gold Standard](../../rn/using/gold-standard.md).

* **Qual è il piano per affrontare eventuali problemi post-migrazione?**

   Si effettuerebbero test approfonditi prima della migrazione dei sistemi di produzione. Tuttavia, in caso di problemi, [l&#39;Assistenza clienti Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) rimarrà il punto di contatto principale. Se necessario, Adobe ha istituito un team di esperti per fornire supporto avanzato.

## Effetti sul recapito messaggi

![](assets/do-not-translate/features.png)

Di seguito sono elencati gli impatti globali su IP, elenchi Bloccati, sottodomini e URL.

* **Come verrà gestito l’IP sull’inserire nell&#39;elenco Consentiti? I clienti dovranno aggiungere nuovi indirizzi IP all’inserire nell&#39;elenco Consentiti del traffico in entrata da Campaign?**

   L’indirizzo IP dei server di Adobe verrà modificato. Pertanto, i clienti potrebbero dover aggiungere questi nuovi indirizzi IP nell’inserire nell&#39;elenco Consentiti nel loro sistema.

   [Fai clic ](#config) qui per ulteriori dettagli sull’IP nell’inserire nell&#39;elenco Consentiti.

* **Come gestiremo la porta aggiunta all’inserire nell&#39;elenco Consentiti per l’accesso SFTP/FTP?**

   La configurazione SFTP (chiavi pubbliche + IP sull’inserire nell&#39;elenco Consentiti) verrà spostata anche dal Data Center legacy a Public Cloud (AWS). Nessuna azione prevista dal cliente.

* **Stiamo cambiando gli IP?**

   L’indirizzo IP dei server di Adobe verrà modificato. Pertanto, i clienti potrebbero dover aggiungere questi nuovi indirizzi IP all’inserire nell&#39;elenco Consentiti nel loro sistema.

   [Fai clic ](#config) qui per ulteriori dettagli sull’IP nell’inserire nell&#39;elenco Consentiti.

* **Come verrà gestita la delega del sottodominio?**

   I sottodomini esistenti verranno spostati da Data Center legacy a Public Cloud (AWS). Questa parte verrà gestita dal team Adobe Deliverability come parte del processo di migrazione.

   L’Adobe guiderà il cliente attraverso i test richiesti per garantire che la configurazione sia attiva e in esecuzione sui nuovi server Public Cloud (AWS) dopo la migrazione.

* **La migrazione produrrà nuovi URL per il tracciamento, le risorse e le applicazioni web?**

   No, gli URL esistenti verranno mantenuti.

* **Ci sarà una modifica nel sottodominio da Neolane.net a campaign.adobe.com?**

   Dopo la migrazione saranno presenti sia `neolane.net` che `campaign.adobe.com`. Per semplificarlo: reindirizzeremo neolane.net a nuove istanze in Public Cloud (AWS), quindi non sono richieste modifiche da parte del cliente.

* **Qual è il piano per il riscaldamento dell&#39;IP?**

   In primo luogo, Adobe Deliverability valuterà lo stato di consegna della piattaforma e raccomanderà un piano per il passaggio ai nuovi IP

   Dopo la migrazione non è necessario alcun riscaldamento. Potrebbe essere un&#39;eccezione e, in questo caso, [Adobe Customer Care](https://experienceleague.adobe.com/?support-solution=Campaign#support) contatterà i clienti.

   Tuttavia, il piano è quello di rendere trasparente questa operazione per l&#39;azienda, a differenza della rampa iniziale che viene fatta durante il go-live.

   Una volta completata la migrazione, l’istanza Campaign avrà IP di invio completamente diversi. Al fine di garantire una transizione senza problemi, Adobe implementerà un&#39;espansione dei nuovi IP di invio cambiando progressivamente il traffico dai vecchi ai nuovi IP.

* **Stiamo passando all’URL sull’inserire nell&#39;elenco Consentiti?**

   Sì, questo viene memorizzato nel file di configurazione del server che verrà copiato dall&#39;origine nella nuova istanza.

* **Quale dovrebbe essere l&#39;impatto con il nostro sottodominio delegato che usiamo per brand la nostra comunicazione?**

   I sottodomini utilizzati per le comunicazioni di marketing rimangono gli stessi. Tuttavia, a seconda dell’implementazione, sono necessarie azioni dal lato client:
   * In caso di delega del sottodominio ad Adobe (impostazione predefinita), Adobe si occupa di tutte le modifiche e garantisce una transizione senza soluzione di continuità.
   * In caso di configurazione CNAME (eccezione), al cliente viene richiesto di implementare le modifiche, in coordinamento con l&#39;Adobe.

## Impatto di configurazione e connettività

![](assets/do-not-translate/maintenance.png)

### Nota sull’IP nell’inserire nell&#39;elenco Consentiti{#config}

La migrazione a public Cloud verrà fornita con nuovi IP per i server delle applicazioni Adobe Campaign, in modo che la modifica degli IP possa avere un impatto sulla connettività tra i server Adobe e i sistemi informativi.

![](assets/migration.png)

Consideriamo i due casi :

* Traffico in entrata: Tutte le attività di rete avviate dai sistemi o da qualsiasi altra parte terza ai server Adobe Campaign. La configurazione verrà gestita da Adobe e quindi copiata da legacy a public Cloud durante la migrazione. La connettività per il traffico in entrata verrà quindi mantenuta così come avviene dopo la migrazione e non è prevista alcuna azione dal lato cliente

* Traffico in uscita: Tutte le attività di rete avviate dai server Adobe Campaign al sistema informativo o a qualsiasi altra terza parte (ad esempio: provider SMS). A seconda dei criteri di sicurezza in vigore nell’organizzazione, la modifica degli IP potrebbe richiedere inserire nell&#39;elenco Consentiti funzionamento del sistema di informazioni o di qualsiasi altra parte terza

### Impatto globale

Di seguito sono elencati gli impatti globali sulla configurazione, la connettività con altri sistemi e prodotti, API e fuso orario.

* **La migrazione influisce sulla connettività agli account esterni?**

   Sì. Le integrazioni di terze parti, ad esempio i provider SMS, devono aggiungere nuovi indirizzi IP dell’applicazione server Adobe Campaign all’inserire nell&#39;elenco Consentiti.

* **La migrazione influisce sulla connettività ad Adobe Analytics utilizzando il connettore di Genesis? Che ne dici dell’aggiunta di indirizzi IP di Campaign all’inserire nell&#39;elenco Consentiti sul lato Adobe Analytics?**

   Gli indirizzi IP dei server applicazioni Adobe Campaign verranno modificati. Questo passaggio verrà gestito dall’Assistenza clienti di Adobe dopo la migrazione.

* **La migrazione avrà un impatto sulla connettività con altre soluzioni Adobe (AEM, Target, ecc.)?**

   Le integrazioni sono una combinazione di indirizzi IP dichiarati nella configurazione dell’account del servizio Web e dell’inserire nell&#39;elenco Consentiti. Sarà contabilizzata e posseduta dall’Assistenza clienti Adobe.

   Nell’inserire nell&#39;elenco Consentiti saranno necessari indirizzi IP nella soluzione esterna, in quanto l’IP dei server applicazioni cambierà. Queste informazioni saranno fornite. Altre parti dell’integrazione sono basate su IMS e devono funzionare normalmente.

* **Cosa succede ai clienti che non sono collegati all’ID organizzazione per l’integrazione IMS?**

   Ai clienti privi di IMS verrà fornito uno: un ID organizzazione IMS verrà allegato alla loro istanza.

* **La migrazione influisce sulle configurazioni con più marchi?**

   Non appena il sottodominio e tutte le configurazioni correlate vengono spostati/reindirizzati correttamente da Data Center a Public Cloud (AWS) legacy, non ci si dovrebbe aspettare alcun impatto.

* **La connettività API è interessata dalla migrazione?**

   L’indirizzo IP dei server di Adobe verrà modificato. Pertanto, i clienti potrebbero dover aggiungere questi nuovi indirizzi IP all’inserire nell&#39;elenco Consentiti nel loro sistema.

   [Fai clic ](#config) qui per ulteriori dettagli sull’IP inserire nell&#39;elenco Consentiti.

* **Ci assicureremo che tutti i parametri di configurazione della memoria JavaScript siano impostati correttamente dopo la migrazione?**

   Copieremo la configurazione dell’istanza dal Data Center legacy a Public Cloud (AWS), in modo che questi valori vengano mantenuti dopo la migrazione.

* **C&#39;è qualche rischio nell&#39;accesso a determinate estensioni di file?**

   Il cliente può voler consentire il caricamento di file di font, file di riunione di outlook nella cartella delle risorse pubbliche. Questa configurazione viene eseguita nel file `config-<instance>.xml` corrente. Questo verrà copiato con i file di configurazione.

* **Il fuso orario cambia sul nuovo server? Il cliente sarà in grado di mantenere il proprio fuso orario corrente?**

   Può cambiare in base alla nuova posizione dei server. Tuttavia, il cliente potrà mantenere il proprio fuso orario corrente.

   [Fai clic ](../../workflow/using/managing-time-zones.md) qui per ulteriori dettagli sulla gestione del fuso orario in Adobe Campaign Classic v7.


## Sicurezza e autorizzazioni

![](assets/do-not-translate/security.png)

Con questa migrazione a Public Cloud (AWS), gli ambienti dei clienti saranno aggiornati con tutti i requisiti di sicurezza necessari. Ciò include :

* Sistemi operativi e patch di sicurezza più recenti su base periodica
* Isolamento dell&#39;infrastruttura per cliente
* Revisioni di sicurezza e controllo gestite per supportare l&#39;infrastruttura cloud, ad esempio load balancer, regole di sicurezza della rete e crittografia dello storage.

Gli effetti su autorizzazioni, certificati e accesso SFTP sono elencati di seguito.

* **Sposteremo tutti i certificati sui nuovi server?**

   Sì, tutti i certificati verranno spostati come parte della migrazione.

* **È necessario richiedere al cliente nuove chiavi di accesso STP?**

   No, Adobe copierà le chiavi di accesso SFTP così come sono sul nuovo server.

* **Come vengono gestite le autorizzazioni SFTP?**

   Stiamo assicurando che i nuovi server SFTP, gli utenti, le directory e i file abbiano esattamente gli stessi livelli di autorizzazione.

* **Se non è stato possibile stabilire la connessione SFTP, qual è la soluzione o il piano per mantenere il funzionamento del cliente?**

   L’unico problema di connettività che può verificarsi è relativo all’inserire nell&#39;elenco Consentiti lato cliente. Il cliente deve aggiungere questo test su un ambiente non di produzione per assicurarsi che funzioni prima di passare a prod.

* **Esistono configurazioni di inserire nell&#39;elenco Consentiti del centro dati specifiche che devono essere trasferite?**

   No, non esiste una configurazione di inserire nell&#39;elenco Consentiti specifica del centro dati da gestire.

* **Gli script personalizzati verranno eseguiti correttamente nel nuovo ambiente?**

   L’implementazione del cliente può utilizzare script personalizzati (Perl/Shell/Python/Java Script) nei flussi di lavoro, ad esempio per manipolare file e cartelle.

   Nell&#39;istanza in hosting, gli script vengono eseguiti solo tramite il motore JavaScript. Queste implementazioni specifiche possono causare problemi di sicurezza e problemi successivi all’aggiornamento. Non sono supportate.

* **Con l’integrazione IMS, funzionerà come in una nuova istanza o sarà necessario un ulteriore aggiornamento della configurazione?**

   Poiché manteniamo gli stessi nomi DNS, dovrebbe funzionare come dopo la migrazione.


## Esecuzione della migrazione

![](assets/do-not-translate/upgrades.png)

Gli impatti globali durante la migrazione sono elencati di seguito.

* **È necessario pianificare l’arresto dell’attività di marketing durante la migrazione?**

   Adobe consiglia di rallentare e mettere in pausa idealmente tutte le esecuzioni poco prima che l’applicazione venga chiusa sul Data Center legacy: consegne e flussi di lavoro. In questo modo, il riavvio su Cloud Server (AWS) verrà semplificato in quanto ai processi verrà concesso il tempo necessario per mettere in pausa &quot;in modo graduale&quot; e salvare eventuali stati di esecuzione in corso.

* **Prevediamo tempi di inattività del servizio Adobe Campaign?**

   La migrazione verrà effettuata con un tempo di inattività inevitabile della piattaforma. L&#39;obiettivo di questo piano è quello di ridurre al minimo i tempi di inattività.

   Il trasferimento dei dati tra i centri dati è sul percorso critico del downtime. I dati vengono memorizzati in due modi:

   * Di gran lunga il più importante, il database
   * File sul server applicazioni (importazioni ed esportazioni di dati)

   Ridurre le dimensioni del database è di estrema importanza per accelerare il trasferimento dei dati. Suggerimenti:

   * Riduci i periodi di conservazione dei dati storici (registri di consegna, registri di tracciamento, ecc.)
   * Elimina i record inutili su altre tabelle (consegne, destinatari, tabelle personalizzate)


* **Qual è il tempo di inattività stimato per la migrazione di un’istanza?**

   I tempi di inattività dipendono interamente dalle dimensioni del database del cliente e dalle dimensioni dell’archiviazione dei file SFTP. Contatta l’Assistenza clienti per ricevere una stima della durata.

* **Informazioni sui messaggi inviati dal server legacy. I collegamenti saranno sempre accessibili?**

   Durante l’esecuzione della migrazione, rimarrà operativo un solo servizio: reindirizzamento collegamenti e-mail. Tutti i destinatari possono raggiungere la pagina di destinazione facendo clic su un messaggio e-mail. Questi clic non verranno tuttavia tracciati, pertanto le percentuali di clic per le consegne avviate poco prima della migrazione saranno inferiori al solito.

* **E gli ambienti mid-sourcing/RT?**

   L’origine MID e l’RT sono gestiti come qualsiasi altra infrastruttura in hosting.

* **In quale ordine verranno effettuate le migrazioni?**

   Gli ambienti verranno migrati nel seguente ordine:

   1. Ambienti di sviluppo
   1. Ambienti di stage
   1. Ambienti di produzione
   1. Ambienti RT
   1. Ambienti di mid-sourcing

* **Qual è il piano di rollback?**

   Il piano di ripristino consiste nel ripristinare il DNS e impostare di nuovo il database di origine in lettura-scrittura da sola lettura. Alla fine avremo l&#39;automazione.

* **Dopo la migrazione, possiamo ancora accedere alle istanze precedenti?**

   Una volta completata la migrazione dell’applicazione, non è previsto alcun piano per eseguire nuovamente alcun processo nel Data Center legacy. Prevediamo che tutti i dati del Data Center legacy possano essere cancellati, ad eccezione dei backup temporanei, fino a quando i processi di backup pianificati non saranno eseguiti su Public Cloud (AWS).

* **Quanto tempo sarà concesso per testare ogni istanza dopo la migrazione a Public Cloud?**

   A seconda della complessità del cliente È necessario un periodo di almeno 1 settimana tra le migrazioni dell’ambiente Stage e dell’ambiente di produzione.

* **Chi gestirà l’aggiunta di nuovi IP all’inserire nell&#39;elenco Consentiti?**

   Il team di Assistenza clienti di Adobe si occuperà di garantire che il cliente e qualsiasi terza parte possano accedere al nuovo sistema aggiungendo i nuovi IP all’inserire nell&#39;elenco Consentiti.

## Supporto e altri collegamenti utili{#support}

* [Migrazione ad Adobe Managed Services (Public Cloud)](dc-migration.md)
* [Aggiornamento Gold Standard](../../rn/using/gs-overview.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
