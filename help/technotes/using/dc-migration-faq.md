---
product: campaign
title: Domande frequenti sulla migrazione ad Adobe Managed Services (Public Cloud)
description: Domande frequenti sulla migrazione di Campaign Classic a Public Cloud
feature: Technote, Upgrade
role: User
level: Beginner
exl-id: a9cd08b0-55c2-4405-9fb8-f0c623cd4ccb
source-git-commit: 6803b6628313db9108a191fd143dac68ee799149
workflow-type: tm+mt
source-wordcount: '2225'
ht-degree: 0%

---

# Domande frequenti sulla migrazione al cloud pubblico{#dc-faq}



L’Adobe disattiva il centro dati legacy: le istanze Campaign Classic devono essere trasferite a Public Cloud Amazon Web Services (AWS). [Ulteriori informazioni su questa iniziativa](dc-migration.md).

Di seguito è riportata una serie di domande comuni su questo progetto, sull’impatto sugli ambienti Campaign e su altre risorse utili.

Per qualsiasi altra domanda, puoi contattare [Assistenza clienti Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support).

## Impatto sull&#39;infrastruttura

![](assets/do-not-translate/database.png)

Gli impatti globali su database e infrastruttura sono elencati di seguito.

* **Il database verrà modificato? Versione del nuovo database Quale sistema operativo verrà utilizzato?**

  Adobe si riserva il diritto di scegliere e implementare il motore di gestione del database più adatto a fornire il servizio Adobe Campaign in condizioni ottimali.

  Inoltre, al fine di preservare il miglior livello di sicurezza, Adobe non fornirà informazioni dettagliate relative all’infrastruttura.

* **Esiste il rischio di perdita dei dati?**

  Il database verrà scaricato dal centro dati legacy e ripristinato in Cloud pubblico (AWS). Quando viene riavviata sul nuovo data center, l’applicazione riprenderà dallo stato esatto in cui si trovava prima della migrazione. Gli utenti non vedranno alcuna differenza, tranne per il fatto che alcune attività pianificate saranno state ritardate.

* **Esistono differenze nelle dimensioni del pacchetto tra il centro dati legacy e il cloud pubblico?**

  Stiamo eseguendo il provisioning in Cloud pubblico (AWS) con nuove definizioni di pacchetti basate sulle dimensioni correnti del database, del disco e così via. Ad esempio, se un cliente dispone di un server applicazioni nei centri dati legacy, può disporre di due server applicazioni nel cloud pubblico (AWS) in base alle definizioni dei pacchetti.

* **Il numero di build o la versione di Campaign cambieranno?**

  Come primo passo, manterremo la stessa build Campaign Classic con la migrazione.

  In un passaggio successivo, effettueremo l’aggiornamento alla build Campaign Classic GA più recente. Per ulteriori informazioni, consulta [questa pagina](../../rn/using/rn-overview.md).

* **Qual è il piano per risolvere eventuali problemi post-migrazione?**

  Prima della migrazione dei sistemi di produzione vengono eseguiti test approfonditi. Tuttavia, in caso di problemi, [Assistenza clienti Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) rimarrà il principale punto di contatto. Adobe ha istituito un team di esperti per fornire supporto avanzato, se necessario.

## Impatto sul recapito messaggi

![](assets/do-not-translate/features.png)

Gli impatti globali su IP, elenchi Bloccati, sottodomini e URL sono elencati di seguito.

* **Come verrà gestito l’IP sul elenco Consentiti di gestione del sistema di gestione dei rapporti con i clienti ()? I clienti dovranno aggiungere nuovi indirizzi IP al elenco Consentiti di per il traffico in entrata da Campaign?**

  L’indirizzo IP dei server di Adobe cambierà. Pertanto, i clienti potrebbero dover aggiungere questi nuovi indirizzi IP nel inserisco nell&#39;elenco Consentiti di nel proprio sistema.

  [Ulteriori informazioni](#config) informazioni su IP nel inserisco nell&#39;elenco Consentiti di selezione del.

* **Come gestiremo la porta aggiunta al inserisco nell&#39;elenco Consentiti di accesso SFTP/FTP del?**

  Anche la configurazione SFTP (chiavi pubbliche + IP sul inserisco nell&#39;elenco Consentiti di) verrà spostata dal datacenter legacy al cloud pubblico (AWS). Nessuna azione prevista dal cliente.

* **Stiamo cambiando gli IP?**

  L’indirizzo IP dei server di Adobe cambierà. Pertanto, i clienti potrebbero dover aggiungere questi nuovi indirizzi IP al inserisco nell&#39;elenco Consentiti di nel proprio sistema.

  [Ulteriori informazioni](#config) informazioni su IP nel inserisco nell&#39;elenco Consentiti di selezione del.

* **Come verrà gestita la delega dei sottodomini?**

  I sottodomini esistenti verranno spostati dal datacenter legacy al cloud pubblico (AWS). Questa parte verrà gestita dal team di recapito messaggi Adobe come parte del processo di migrazione.

  >[!NOTE]
  >
  >Il team di recapito messaggi si basa sul contratto e i clienti devono contattare il proprio rappresentante di Adobe per informazioni relative al progetto di recapito messaggi.

  Adobe guiderà il cliente attraverso i test richiesti per garantire che la configurazione sia attiva e in esecuzione sui nuovi server Public Cloud (AWS) dopo la migrazione.

* **La migrazione produrrà nuovi URL per il tracciamento, le risorse e le applicazioni web?**

  No, gli URL esistenti verranno mantenuti.

* **Si verificherà una modifica nel sottodominio da Neolane.net a campaign.adobe.com?**

  Entrambi `neolane.net` e `campaign.adobe.com` dopo la migrazione. Per semplificare, effettueremo il reindirizzamento di neolane.net alle nuove istanze in Public Cloud (AWS), in modo che non siano necessarie modifiche da parte del cliente.

* **Qual è il piano per il riscaldamento dell’IP?**

  Innanzitutto, Adobe Deliverability valuta lo stato di recapito della piattaforma e consiglia un piano per il passaggio ai nuovi IP

  Non è necessario alcun riscaldamento dopo la migrazione. Potrebbe trattarsi di un&#39;eccezione e, in tal caso, [Assistenza clienti Adobe](https://experienceleague.adobe.com/?support-solution=Campaign#support) contatterà i clienti.

  Tuttavia, il piano è quello di rendere trasparente questa operazione per l&#39;azienda, a differenza dell&#39;incremento iniziale che viene fatto durante il go-live.

  Al termine della migrazione, l’istanza Campaign avrà IP di invio completamente diversi. Al fine di garantire una transizione senza intoppi, Adobe implementerà un incremento dei nuovi IP di invio passando progressivamente dal vecchio ai nuovi IP.

* **Si sta spostando l&#39;URL sul inserisco nell&#39;elenco Consentiti di?**

  Sì, viene memorizzato nel file di configurazione del server che verrà copiato dall’origine alla nuova istanza.

* **Quale dovrebbe essere l’impatto del sottodominio delegato che utilizziamo per marcare la nostra comunicazione?**

  I sottodomini utilizzati per le comunicazioni di marketing rimangono gli stessi. Tuttavia, a seconda dell’implementazione, sono necessarie azioni sul lato client:
   * In caso di delega del sottodominio ad Adobe (impostazione predefinita), Adobe si occupa di tutte le modifiche e garantisce una transizione senza soluzione di continuità.
   * In caso di configurazione di CNAME (eccezione), al client viene richiesto di implementare le modifiche, in coordinamento con Adobe.

## Impatto su configurazione e connettività

![](assets/do-not-translate/maintenance.png)

### Nota sull&#39;IP sul inserisco nell&#39;elenco Consentiti di{#config}

La migrazione al cloud pubblico sarà accompagnata da nuovi IP per i server applicazioni Adobe Campaign, in modo che la modifica dell’IP possa avere un impatto sulla connettività tra i server Adobe e i sistemi informativi.

![](assets/migration.png)

Prendiamo in considerazione i due casi:

* Traffico in entrata: tutte le attività di rete avviate dai sistemi o da terze parti ai server Adobe Campaign. La configurazione verrà gestita da Adobe e quindi copiata da legacy a cloud pubblico durante la migrazione. La connettività per il traffico in entrata verrà quindi mantenuta invariata dopo la migrazione e non è prevista alcuna azione da parte del cliente

* Traffico in uscita: tutte le attività di rete avviate dai server Adobe Campaign al sistema informativo o a terze parti (ad esempio, il provider SMS). A seconda dei criteri di sicurezza in vigore nell&#39;organizzazione, la modifica degli IP potrebbe richiedere l&#39;operazione di inserisce nell&#39;elenco Consentiti del sistema informativo o di qualsiasi altra terza parte

### Impatti globali

Di seguito sono elencati gli impatti globali su configurazione, connettività con altri sistemi e prodotti, API e fuso orario.

* **La migrazione influirà sulla connettività con account esterni?**

  Sì. Le integrazioni di terze parti, ad esempio i provider di SMS, devono aggiungere al Adobe Campaign nuovi indirizzi IP dei server applicazioni di inserire nell&#39;elenco Consentiti.

* **La migrazione influirà sulla connettività ad Adobe Analytics utilizzando il connettore di Genesis? E se si aggiungessero gli indirizzi IP di Campaign al inserisco nell&#39;elenco Consentiti di sul lato Adobe Analytics?**

  Gli indirizzi IP dei server applicazioni Adobe Campaign cambieranno. Questo passaggio sarà gestito da Adobe Customer Care dopo la migrazione.

* **La migrazione influirà sulla connettività con altre soluzioni Adobi (AEM, Target, ecc.)?**

  Le integrazioni sono una combinazione di indirizzi IP dichiarati nel inserisco nell&#39;elenco Consentiti di gestione dei rapporti con i clienti e nella configurazione dell’account del servizio web. Questo sarà registrato e di proprietà dell’Assistenza clienti Adobe.

  Nel inserisco nell&#39;elenco Consentiti di saranno presenti indirizzi IP che saranno necessari nella soluzione esterna man mano che l&#39;IP degli Application Server cambierà. Queste informazioni verranno fornite. Altre parti dell’integrazione sono basate su IMS e dovrebbero funzionare così come sono.

* **E per quanto riguarda i clienti che non sono associati all’ID organizzazione per l’integrazione IMS?**

  Ai clienti che non dispongono di IMS ne verrà fornito uno: all’istanza verrà allegato un ID organizzazione.

* **La migrazione influisce sulle configurazioni a più marchi?**

  Non appena il sottodominio e tutte le relative configurazioni vengono spostati/reindirizzati correttamente dal datacenter legacy al cloud pubblico (AWS), non dovrebbe verificarsi alcun impatto.

* **La connettività API è interessata dalla migrazione?**

  L’indirizzo IP dei server di Adobe cambierà. Pertanto, i clienti potrebbero dover aggiungere questi nuovi indirizzi IP al inserisco nell&#39;elenco Consentiti di nel proprio sistema.

  [Ulteriori informazioni](#config) informazioni su IP in modalità di inserisce nell&#39;elenco Consentiti di.

* **Dopo la migrazione, verrà verificato che tutti i parametri di configurazione della memoria JavaScript siano impostati correttamente?**

  Copieremo la configurazione dell’istanza dal datacenter legacy al cloud pubblico (AWS), in modo che questi valori vengano mantenuti dopo la migrazione.

* **Esistono rischi per l’accesso a determinate estensioni di file?**

  È possibile che il cliente desideri consentire il caricamento dei file dei tipi di carattere e dei file delle riunioni di Outlook nella cartella delle risorse pubbliche. Questa configurazione viene eseguita nel `config-<instance>.xml` file. Verrà copiato con i file di configurazione.

* **Il fuso orario cambia sul nuovo server? Il cliente sarà in grado di mantenere il proprio fuso orario corrente?**

  Può variare in base alla nuova posizione dei server. Tuttavia, il cliente sarà in grado di mantenere il proprio fuso orario corrente.

  [Ulteriori informazioni](../../workflow/using/managing-time-zones.md) informazioni sulla gestione del fuso orario in Adobe Campaign Classic v7.


## Sicurezza e autorizzazioni

![](assets/do-not-translate/security.png)

Con questa migrazione a Public Cloud (AWS), gli ambienti dei clienti verranno tenuti aggiornati con tutti i requisiti di sicurezza necessari. Ciò include:

* Nuove patch periodiche per il sistema operativo e la sicurezza
* isolamento dell&#39;infrastruttura per cliente;
* Revisioni gestite di sicurezza e audit per il supporto di infrastrutture cloud quali load balancer, regole di sicurezza della rete e crittografia dello storage.

Gli impatti su autorizzazioni, certificati e accesso SFTP sono elencati di seguito.

* **Intendiamo spostare tutti i certificati nei nuovi server?**

  Sì, tutti i certificati verranno spostati nell’ambito di questa migrazione.

* **È necessario richiedere al cliente nuove chiavi di accesso STP?**

  No, Adobe copia le chiavi di accesso SFTP così come sono sul nuovo server.

* **Come vengono gestite le autorizzazioni SFTP?**

  Stiamo garantendo che i nuovi server SFTP, utenti, directory e file abbiano esattamente gli stessi livelli di autorizzazione.

* **Se non è stato possibile stabilire la connessione SFTP, qual è la soluzione alternativa o il piano per mantenere operativo il cliente?**

  L’unico problema di connettività che può sorgere è relativo al inserisco nell&#39;elenco Consentiti di sul lato cliente. Il cliente deve aggiungere questo test all’ambiente non di produzione per assicurarsi che funzioni prima di passare alla produzione.

* **Esistono configurazioni di inserisco nell&#39;elenco Consentiti specifiche per i data center che devono essere spostate?**

  No, non esiste una configurazione di inserisco nell&#39;elenco Consentiti specifica per il centro dati da gestire.

* **Stiamo garantendo che gli script personalizzati vengano eseguiti correttamente nel nuovo ambiente?**

  L’implementazione del cliente può utilizzare script personalizzati (Perl/Shell/Python/Java Script) nei flussi di lavoro, ad esempio per manipolare file e cartelle.

  Nell’istanza ospitata, gli script vengono eseguiti solo tramite il motore JavaScript. Queste implementazioni specifiche possono causare divari di sicurezza e problemi di post-aggiornamento. Non sono supportati.

* **Con l’integrazione IMS, funzionerà come nella nuova istanza o sarà necessario un ulteriore aggiornamento della configurazione?**

  Poiché manteniamo gli stessi nomi DNS, dovrebbe funzionare come dopo la migrazione.


## Esecuzione della migrazione

![](assets/do-not-translate/upgrades.png)

Gli impatti globali durante la migrazione sono elencati di seguito.

* **È necessario pianificare l’interruzione dell’attività di marketing durante la migrazione?**

  L’Adobe consiglia di rallentare e sospendere idealmente tutte le esecuzioni immediatamente prima che l’applicazione venga chiusa nel datacenter legacy: consegne e flussi di lavoro. Questo semplifica il riavvio su Cloud Server (AWS), in quanto ai processi è stato dato il tempo di sospendere &quot;agevolmente&quot; e salvare qualsiasi stato di esecuzione in corso.

* **Il servizio Adobe Campaign prevede tempi di inattività?**

  La migrazione comporterà inevitabili tempi di inattività della piattaforma. L&#39;obiettivo di questo piano è quello di guidare verso la riduzione al minimo di questi tempi di inattività.

  Il trasferimento dei dati tra centri dati si trova nel percorso critico dei tempi di inattività. I dati vengono memorizzati in due modi:

   * Di gran lunga il più importante, il database
   * File sul server applicazioni (importazioni ed esportazioni di dati)

  Ridurre le dimensioni del database è della massima importanza per accelerare il trasferimento dei dati. Suggerimenti:

   * Riduci i periodi di conservazione dei dati storici (registri di consegna, registri di tracciamento, ecc.)
   * Elimina record inutili in altre tabelle (consegne, destinatari, tabelle personalizzate)

* **Qual è il tempo di inattività stimato per la migrazione di un’istanza?**

  I tempi di inattività dipendono interamente dalle dimensioni del database del cliente e dalle dimensioni dell’archiviazione dei file SFTP. Rivolgiti al tuo contatto di Assistenza clienti per ricevere assistenza per un periodo di tempo stimato.

* **Informazioni sui messaggi inviati dal server legacy. I collegamenti saranno sempre accessibili?**

  Durante l’esecuzione della migrazione, rimarrà funzionale un solo servizio: reindirizzamento dei collegamenti e-mail. Tutti i destinatari saranno in grado di raggiungere la pagina di destinazione quando fanno clic in un messaggio e-mail. Tuttavia, questi clic non verranno tracciati, pertanto le percentuali di clic per le consegne avviate poco prima della migrazione saranno inferiori al solito.

* **E per gli ambienti mid-sourcing/RT?**

  Il MID sourcing e l&#39;RT sono gestiti come qualsiasi altra infrastruttura in hosting.

* **In quale ordine verranno eseguite le migrazioni?**

  La migrazione degli ambienti verrà eseguita nell’ordine seguente:

   1. Ambienti di sviluppo
   1. Ambienti stage
   1. Ambienti di produzione
   1. Ambienti RT
   1. Ambienti di mid-sourcing

* **Qual è il piano di ripristino?**

  Il piano di rollback prevede il ripristino del DNS e la reimpostazione del database di origine in lettura/scrittura da sola lettura. Alla fine avremo l&#39;automazione per esso.

* **Dopo la migrazione, possiamo ancora accedere alle vecchie istanze?**

  Una volta completata la migrazione dell&#39;applicazione, non è prevista l&#39;esecuzione di alcun processo nel datacenter legacy. Prevediamo che tutti i dati del datacenter legacy possano essere cancellati, ad eccezione di quelli per scopi di backup temporanei, fino a quando i processi di backup pianificati non saranno in esecuzione su Public Cloud (AWS).

* **Quanto tempo sarà consentito per il test di ogni istanza dopo la migrazione a Cloud pubblico?**

  A seconda della complessità del cliente, è necessario un tempo di almeno 1 settimana tra le migrazioni dell’ambiente di staging e dell’ambiente di produzione.

* **Chi gestirà l’aggiunta di nuovi IP al elenco Consentiti di?**

  Il team di assistenza clienti di Adobe provvederà a garantire che il cliente e tutte le terze parti possano accedere al nuovo elenco Consentiti aggiungendo i nuovi IP al sistema di.

## Supporto e altri collegamenti utili{#support}

* [Migrazione ad Adobe Managed Services (cloud pubblico)](dc-migration.md)
* [Aggiornamento annuale della campagna](../../rn/using/rn-overview.md#yeary-upgrade)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
