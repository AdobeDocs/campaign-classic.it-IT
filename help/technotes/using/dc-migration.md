---
product: campaign
title: Migrazione a cloud pubblico
description: Ulteriori informazioni sulla migrazione di Campaign Classic a Public Cloud
feature: Overview
role: User
level: Beginner
exl-id: 2b282221-d048-4f6e-b52e-f8e584af2c0e
source-git-commit: 1a9e0f8bf374e10af938d15dcebe943819ae327b
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 2%

---

# Panoramica{#dc-ovv}

![](../../assets/v7-only.svg)

## Contesto

In qualità di cliente Adobe Campaign Classic di valore, ci impegniamo a fornirti la migliore esperienza e il miglior valore. Nel corso degli anni, ci siamo resi conto del valore e dell&#39;affidabilità dell&#39;hosting dei nostri clienti nel cloud.  Come parte del nostro [Iniziativa Gold Standard](../../rn/using/gold-standard.md), stiamo spostando tutti i nostri clienti in Adobe Managed Services (Public Cloud on AWS) per fornire servizi migliori e più affidabili.

Questo programma si prefigge tre obiettivi principali:

* Affrontare le vulnerabilità di sicurezza identificate spostando l’infrastruttura in un ambiente protetto e moderno (AWS).
* Elimina i processi di scalabilità potenzialmente ingombranti e fornisci accesso ai nostri [MTA ottimizzati](../../delivery/using//sending-with-enhanced-mta.md) e migliorare tutti i livelli di servizio di manutenzione.
* Prepara la tua istanza per il futuro di Adobe Campaign Classic, inclusi aggiornamenti più automatizzati e regolari che non richiederanno più risorse né tanto tempo.

### Glossario

* **Aggiornamento della build** - Quando il software Adobe Campaign Classic viene aggiornato al numero di build sicuro più recente, ma rimane nello stesso livello di build principale/secondario. Ad esempio: Campaign v7 20.2.3 build 9182 a Campaign v7 21.2.5 build 9188. [Ulteriori informazioni](../../platform/using/faq-build-upgrade.md).
* **MID/RT** - Server di esecuzione dei messaggi ospitati su Adobe Cloud (MID per campagne batch e RT per messaggi unitari in tempo reale)
* **Aggiornamento Gold Standard** - questo programma offre una maggiore sicurezza, un migliore supporto, una maggiore manutenzione e stabilità. Inoltre, semplifica gli aggiornamenti futuri e consente l’accesso a nuove funzionalità in Campaign.  [Ulteriori informazioni](../../rn/using/gs-overview.md).
* **AWS** - Amazon Web Services (Amazon Public Cloud)
* **SFTP** - Secure File Transfer Protocol (protocollo di trasferimento file protetto). [Ulteriori informazioni](../../platform/using/sftp-server-usage.md).


>[!NOTE]
>La migrazione di Campaign Classic v7 a Public Cloud ha un impatto sui clienti che utilizzano **Adobe Managed Services** solo.


## Vantaggi

**Sicurezza**

* Correzioni di sicurezza più recenti
* Crittografia dei dati a riposo
* Autenticazione migliorata (IMS)

**Infrastrutture**

* Scalabilità hardware semplice
* Ripristino più rapido
* Maggiore affidabilità e stabilità
* Procedure operative armonizzate

**Prestazioni**

* Maggiore capacità e-mail
* Database più grandi
* Versione di campagna protetta - Gold Standard

**Soluzioni affidabili e affidabili per i clienti Adobe Campaign Classic**

1. Migliori procedure di produzione, che consentono una maggiore affidabilità, una reattività più rapida in caso di problemi, un recupero più rapido in caso di incidenti gravi.
1. Maggiore capacità di invio delle e-mail. Le istanze ospitate nel nuovo centro dati avranno la possibilità di usufruire di un’infrastruttura specializzata per la consegna delle e-mail. Questo potrebbe comportare una maggiore velocità di consegna delle e-mail o consentire l’utilizzo di un numero inferiore di IP di invio.
1. Migliore scalabilità hardware. L&#39;aumento delle risorse hardware può essere fatto molto più velocemente. Tecnicamente, sarebbe nell&#39;ordine di grandezza di 1 ora invece di diversi giorni.

**Gold Standard semplifica gli aggiornamenti futuri**

1. Più l’organizzazione attende l’aggiornamento, più complesso diventerà l’aggiornamento e il potenziale di affrontare le vulnerabilità aumenta (soprattutto quando si passa da una versione precedente).
1. Con Gold Standard Upgrade, la tua istanza verrà modernizzata e sarà pronta a ricevere aggiornamenti più automatizzati e regolari con meno interventi manuali e meno risorse.

![](assets/GSMigrations.png)

## Informazioni sulla migrazione

La migrazione ad Adobe Managed Services (Public Cloud) avverrà nel 2020/2021 per gli account interessati. Adobe guiderà e guiderà la tua organizzazione attraverso questo percorso.

Per avviare questo sforzo, gli account che richiedono questa migrazione riceveranno una comunicazione e-mail dall’Adobe che fornisce una timeline e l’accesso alla documentazione. Questa sarà la notifica della pianificazione della migrazione dell&#39;account.

È possibile avviare una migrazione tramite [apertura di un nuovo ticket di assistenza clienti](https://experienceleague.adobe.com/?support-solution=Campaign#support). Utilizza l’oggetto &quot;Migrazione ad AWS&quot;.

### Questa migrazione è obbligatoria?

Questa migrazione al cloud è **primo passo del [Certificazione Gold Standard](../../rn/using/gs-overview.md)** delle istanze Adobe Campaign. Questa migrazione è obbligatoria se ti trovi in un Data Center che non è Public Cloud (AWS).

Il cloud Adobe Managed Services è ospitato su Amazon Web Services (AWS), un ambiente moderno, sicuro e ottimizzato. [Ulteriori informazioni su AWS](https://aws.amazon.com/application-hosting/benefits/).

Adobe pianifica di disattivare il Data Center legacy. Le istanze Adobe Campaign in esecuzione devono essere trasferite al nuovo Data Center di riferimento, AWS.

Questo è un percorso critico in avanti, in quanto la posizione corrente potrebbe essere esposta a **vulnerabilità di sicurezza e prestazioni**.

Inoltre, questa migrazione è ora un **prerequisito per qualsiasi aggiornamento della build futuro** del tuo Adobe Campaign. L’aggiornamento della build non è più possibile in Data Center legacy.

Adobe si impegna a proteggere i tuoi dati e a tenerti traccia del futuro di Adobe Campaign. Abbiamo bisogno del vostro partenariato per renderlo un successo congiunto!


**Abbiamo organizzato un team** di rappresentanti dell’Assistenza clienti dedicati, responsabili del successo dei clienti, responsabili di prodotto, ingegneri, specialisti di TechOps e consulenti di prodotto per assistere e garantire che l’esperienza sia fluida e fluida. Facciamo tutto il possibile affinché tu possa disporre sempre delle informazioni di progetto e di contatto di cui puoi avere bisogno.

Abbiamo investito un enorme sforzo nello sviluppo di tecnologie che rendano questa migrazione rapida, continua e sicura.

### Vincoli

* La migrazione verrà effettuata con un tempo di inattività inevitabile della piattaforma. L&#39;obiettivo di questo piano è di ridurre al minimo i tempi di inattività.
* Modifica IP per le integrazioni di dati.
* Incremento del recapito messaggi dei nuovi IP di invio. Tuttavia, il piano è quello di rendere trasparente questa operazione per l&#39;azienda, a differenza della rampa iniziale che viene fatta durante il go-live.

Ulteriori informazioni sulla migrazione di Campaign a [Domande frequenti su Public Cloud](dc-migration-faq.md).


## Certificazione Percorsi to Gold Standard

Verrà fornita assistenza per i passaggi di convalida tra ogni fase cardine.

![](assets/GS-milestones.png)

## Percorso di migrazione a Public Cloud

Adobe gestisce la maggior parte delle azioni. Abbiamo bisogno di te per la convalida e la firma.

![](assets/MigrationPath.png)

## Linee guida sulla migrazione

### Approccio globale

**Database**

Il database verrà scaricato dal data center legacy e ripristinato in Public Cloud (AWS). Al riavvio del nuovo data center, l&#39;applicazione riprenderà dallo stato esatto in cui si trovava prima dello spegnimento. Gli utenti non vedranno alcuna differenza, tranne per il fatto che alcune attività pianificate saranno state ritardate.

**Inviare IP tramite e-mail**

Una volta completata la migrazione, l’istanza Campaign avrà IP di invio completamente diversi. Al fine di garantire una transizione senza problemi, Adobe implementerà un&#39;espansione dei nuovi IP di invio tramite il passaggio graduale del traffico dai vecchi ai nuovi IP.

**IP di integrazione dei dati**

L’integrazione dei dati sul lato client potrebbe essere influenzata dal cambiamento degli IP per l’integrazione dei dati. La modifica potrebbe influenzare entrambe le direzioni, a seconda che Campaign agisca come server o client.
Casi tipici:

* SFTP, possibilmente entrambe le direzioni
* HTTP, possibilmente entrambe le direzioni
* SMPP (connessione al provider SMS), Campaign come client, modifica dell’IP di origine

In generale, ciò significa che il cliente deve controllare eventuali restrizioni IP impostate sui loro firewall e adattarle di conseguenza.*

**Server Campaign**

I server Campaign esistenti (in realtà i contenitori) verranno spostati in Public Cloud (AWS) con un approccio di tipo &quot;incremento e cambiamento&quot;. In altre parole, non sarà necessaria alcuna nuova installazione del server, ma l&#39;intero server verrà trasferito al nuovo data center. L&#39;operazione richiede solo una riconfigurazione tecnica di basso livello.

**Nomi server**

Sotto i sottodomini utilizzati per le comunicazioni di marketing: rimarrà lo stesso. Tuttavia, a seconda dell’implementazione, potrebbero essere necessarie azioni dal lato client:

* In caso di delega di sottodominio (caso normale), l’Adobe si occuperà di tutte le modifiche e garantirà una transizione senza soluzione di continuità
* In caso di configurazione CNAME (eccezione), al client verrà richiesto di implementare le modifiche. Sarà necessario un coordinamento con l&#39;Adobe.

Per l&#39;accesso degli utenti e l&#39;integrazione dei dati, i nomi sotto neolane.net rimarranno invariati.

Ciò significa che la modifica sarà trasparente per gli utenti e le implementazioni di integrazione dei dati, se i nomi dei server non sono stati sostituiti da IP hardcoded.

### Preparazione

**Inviare IP tramite e-mail**

In primo luogo, Adobe Deliverability valuterà lo stato di consegna della piattaforma e raccomanderà un piano per il passaggio ai nuovi IP.

Adobe fornirà lo stesso numero di IP nel nuovo data center.

L’espansione dei nuovi IP può iniziare non appena viene eseguito il provisioning dei nuovi IP.

**Pulizia dell’applicazione**
Il trasferimento dei dati tra i centri dati è sul percorso critico del downtime.

I dati vengono memorizzati in due modi:

1. Di gran lunga il più importante, il database
1. File sul server applicazioni (importazioni ed esportazioni di dati)

Ridurre le dimensioni del database è di estrema importanza per accelerare il trasferimento dei dati.

Suggerimenti:

* Riduci i periodi di conservazione dei dati storici (registri di consegna, registri di tracciamento, ecc.)
* Elimina i record inutili su altre tabelle (consegne, destinatari, tabelle personalizzate)

### Execution

**Sospendi le esecuzioni**

È consigliabile rallentare e mettere in pausa idealmente tutte le esecuzioni immediatamente prima che l’applicazione venga chiusa nel data center legacy: consegne e flussi di lavoro. In questo modo, il riavvio di Public Cloud (AWS) verrà semplificato in quanto ai processi verrà concesso il tempo necessario per mettere in pausa &quot;in modo graduale&quot; e salvare eventuali stati di esecuzione in corso.

**Durante la migrazione**

Durante la migrazione, rimarrà operativo un solo servizio: reindirizzamento collegamenti e-mail. In altre parole, i destinatari possono raggiungere la pagina di destinazione quando fanno clic in un messaggio e-mail. Questi clic non verranno tuttavia registrati, pertanto i tassi di clic per le consegne avviate poco prima della migrazione saranno inferiori al normale.

**Riavvio**

Dopo la migrazione al nuovo ambiente, l&#39;applicazione verrà riavviata progressivamente:

* Primo accesso alla console, in modo che gli utenti possano controllare lo stato senza che nulla sia ancora in esecuzione attiva
* Quindi, flussi di lavoro e consegne

### Post-migrazione

**Eliminazione delle istanze nel Data Center legacy**

Una volta completata la migrazione dell’applicazione, non è previsto alcun piano per eseguire nuovamente alcun processo nel data center legacy. Ci aspettiamo che tutti i dati del data center legacy possano essere cancellati, ad eccezione dei backup temporanei, fino a quando i processi di backup pianificati non saranno eseguiti su Public Cloud (AWS).

**Delega DNS**

Normalmente, il dominio utilizzato per inviare e-mail (parte a destra del simbolo @ nell’indirizzo di errore) da Campaign è stato delegato ad Adobe. La delega può essere modificata e implementata nei server DNS AWS.


## Supporto e altri collegamenti utili{#support}

* [Domande frequenti sulla migrazione ad Adobe Managed Services (Public Cloud)](dc-migration-faq.md)
* [Aggiornamento Gold Standard](../../rn/using/gs-overview.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
