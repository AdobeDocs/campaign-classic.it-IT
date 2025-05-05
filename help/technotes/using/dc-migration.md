---
product: campaign
title: Migrazione a cloud pubblico
description: Ulteriori informazioni sulla migrazione di Campaign Classic a cloud pubblico
feature: Technote, Upgrade
role: User
level: Beginner
exl-id: 2b282221-d048-4f6e-b52e-f8e584af2c0e
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1533'
ht-degree: 2%

---

# Panoramica{#dc-ovv}



## Contesto

In qualità di cliente Adobe Campaign Classic, ci impegniamo a fornirti la migliore esperienza e il miglior valore. Nel corso degli anni, abbiamo realizzato il valore e l&#39;affidabilità di ospitare i nostri clienti nel cloud.  Nell&#39;ambito della [Iniziativa di aggiornamento annuale](../../rn/using/rn-overview.md#yearly-upgrade), stiamo spostando tutti i nostri clienti in Adobe Managed Services (Public Cloud su AWS) per fornire servizi migliori e più affidabili.

Il programma ha tre obiettivi principali:

* Affrontare le vulnerabilità di sicurezza identificate spostando l’infrastruttura in un ambiente protetto e moderno (AWS).
* Eliminare i processi di scalabilità potenzialmente complessi, fornire accesso ai nostri [MTA avanzati](../../delivery/using//sending-with-enhanced-mta.md) e migliorare tutti i livelli di servizio di manutenzione.
* Prepara l’istanza per il futuro di Adobe Campaign Classic, inclusi aggiornamenti più automatizzati e regolari che non richiederanno troppe risorse né tanto tempo.

### Glossario

* **Aggiornamento build** - Quando il software Adobe Campaign Classic viene aggiornato al numero di build sicuro più recente, rimane comunque nello stesso livello di build principale/secondario. Ad esempio: da Campaign v7 20.2.3 build 9182 a Campaign v7 21.2.5 build 9188. [Ulteriori informazioni](../../platform/using/faq-build-upgrade.md).
* **MID/RT** - Server di esecuzione messaggi ospitati su Adobe Cloud (MID per campagne batch e RT per messaggi unitari in tempo reale)
* **Programma di aggiornamento annuale** - questo programma offre maggiore sicurezza, supporto migliorato, manutenzione e stabilità migliorate. Semplifica inoltre gli aggiornamenti futuri e consente l’accesso a nuove funzionalità in Campaign.  [Ulteriori informazioni](../../rn/using/rn-overview.md#yearly-upgrade).
* **AWS** - Amazon Web Services (cloud pubblico Amazon)
* **SFTP** - Protocollo di trasferimento file protetto. [Ulteriori informazioni](../../platform/using/sftp-server-usage.md).


>[!NOTE]
>La migrazione di Campaign Classic v7 a Public Cloud influisce sui clienti che utilizzano solo **Adobe Managed Services**.


## Vantaggi

**Sicurezza**

* Correzioni di sicurezza più recenti
* Crittografia dei dati a riposo
* Autenticazione migliorata (IMS)

**Infrastruttura**

* Scalabilità hardware agile
* Ripristino più rapido
* Maggiore affidabilità e stabilità
* Procedure operative armonizzate

**Prestazioni**

* Capacità e-mail migliorata
* Database più grandi
* Versione di Campaign provata

**Soluzione affidabile e affidabile per i clienti Adobe Campaign Classic**

1. Procedure di produzione migliori, che garantiscono maggiore affidabilità, reattività più rapida in caso di problemi e ripristino più rapido in caso di incidenti gravi.
1. Maggiore capacità di invio di e-mail. Le istanze ospitate nel nuovo data center avranno la possibilità di beneficiare di un’infrastruttura specializzata per la distribuzione delle e-mail. Questo potrebbe portare a una maggiore velocità di consegna delle e-mail o consentire l’utilizzo di meno IP di invio.
1. Migliore scalabilità dell&#39;hardware. L&#39;aumento delle risorse hardware può essere realizzato molto più rapidamente. Tecnicamente, sarebbe nell&#39;ordine di grandezza di 1 ora invece di diversi giorni.

**Gli aggiornamenti annuali semplificano gli aggiornamenti futuri**

1. Più si rimanda l’aggiornamento, più l’aggiornamento diventa complesso e più aumenta il rischio di vulnerabilità (in particolare quando si passa da una versione precedente).
1. Con l’aggiornamento annuale di Campaign (precedentemente iniziativa Gold Standard), l’istanza verrà modernizzata e sarà pronta per ricevere aggiornamenti più automatizzati e regolari con meno interventi manuali e meno risorse.

![](assets/GSMigrations.png)

## Informazioni sulla migrazione

Per iniziare, gli account che richiedono questa migrazione riceveranno una comunicazione e-mail da Adobe, con una timeline e l’accesso alla documentazione. Questa sarà la notifica che avvisa che è pianificata la migrazione del tuo account.

È possibile avviare una migrazione [aprendo un nuovo ticket di assistenza clienti](https://experienceleague.adobe.com/it?support-solution=Campaign#support). Utilizza la riga dell’oggetto &quot;Migrazione ad AWS&quot;.

### Questa migrazione è obbligatoria?

Questa migrazione al cloud è **il primo passaggio al [programma di aggiornamento annuale](../../rn/using/rn-overview.md#yearly-upgrade)** delle istanze Adobe Campaign. Questa migrazione è obbligatoria se sei ospitato in un centro dati che non è il cloud pubblico (AWS).

Il cloud Managed Services di Adobe è ospitato su Amazon Web Services (AWS), un ambiente moderno, sicuro e ottimizzato. [Ulteriori informazioni su AWS](https://aws.amazon.com/application-hosting/benefits/).

Adobe prevede di rimuovere il centro dati legacy, le istanze Adobe Campaign in esecuzione in tale centro devono essere trasferite al nuovo centro dati di riferimento, AWS.

Si tratta di un percorso critico in avanti in quanto la posizione corrente potrebbe essere esposta a **vulnerabilità di sicurezza e prestazioni**.

Inoltre, questa migrazione è ora un **prerequisito per qualsiasi aggiornamento della build** futuro del tuo Adobe Campaign. L&#39;aggiornamento della build non è più possibile sui datacenter legacy.

Adobe si impegna a proteggere i dati e a metterti sulla buona strada per il futuro di Adobe Campaign. Abbiamo bisogno della vostra collaborazione per farne un successo comune!


**Abbiamo organizzato un team** di responsabili dell&#39;Assistenza clienti, Customer Success Manager, Product Manager, ingegneri, specialisti TechOps e consulenti di prodotto per assistere e garantire un&#39;esperienza fluida e fluida. Facciamo tutto il possibile affinché tu possa disporre sempre delle informazioni di progetto e di contatto di cui puoi avere bisogno.

Abbiamo investito molto nello sviluppo di tecnologie che renderanno la migrazione veloce, semplice e sicura.

### Vincoli

* La migrazione comporterà inevitabili tempi di inattività della piattaforma. L&#39;obiettivo di questo piano è quello di guidare verso la riduzione al minimo di questi tempi di inattività.
* Modifica dell’IP per le integrazioni di dati.
* Aumento del recapito messaggi dei nuovi IP di invio. Tuttavia, il piano è quello di rendere trasparente questa operazione per l&#39;azienda, a differenza dell&#39;incremento iniziale che viene fatto durante il go-live.

Ulteriori informazioni sono disponibili in Migrazione di Campaign a [Domande frequenti su Public Cloud](dc-migration-faq.md).


## Percorso di migrazione a cloud pubblico

Adobe gestisce la maggior parte delle azioni. Abbiamo bisogno di te per la convalida e l&#39;approvazione.

![](assets/MigrationPath.png)

## Linee guida per la migrazione

### Approccio globale

**Database**

Il database verrà scaricato dal data center legacy e ripristinato in Public Cloud (AWS). Al riavvio del nuovo data center, l&#39;applicazione riprenderà dallo stato esatto precedente all&#39;arresto. Gli utenti non vedranno alcuna differenza, tranne per il fatto che alcune attività pianificate saranno state ritardate.

**Invio di indirizzi IP tramite posta elettronica**

Al termine della migrazione, l’istanza Campaign avrà IP di invio completamente diversi. Al fine di garantire una transizione senza intoppi, Adobe implementerà un aumento graduale dei nuovi IP di invio cambiando in modo progressivo il traffico dai vecchi IP a quelli nuovi.

**IP di integrazione dei dati**

L’integrazione dei dati sul lato client potrebbe essere influenzata dalla modifica degli IP per l’integrazione dei dati. La modifica potrebbe influire su entrambe le direzioni, a seconda che Campaign agisca come server o client.
Casi tipici:

* SFTP, possibilmente entrambe le direzioni
* HTTP, possibilmente in entrambe le direzioni
* SMPP (connessione al provider SMS), Campaign as a client, modifica dell’IP sorgente

In generale, ciò significa che il client deve verificare le eventuali restrizioni IP impostate sui propri firewall e adattarle di conseguenza.*

**Server campagne**

I server Campaign esistenti (contenitori in realtà) verranno spostati in Cloud pubblico (AWS) in un approccio &quot;lift-and-shift&quot;. In altre parole, non sarà necessaria alcuna nuova installazione del server, ma l&#39;intero server verrà trasferito al nuovo centro dati. L&#39;operazione non richiederà altro lavoro che una riconfigurazione tecnica di basso livello.

**Nomi server**

Nel/i sottodominio/i utilizzato/i per le comunicazioni di marketing: rimarrà lo stesso. Tuttavia, a seconda dell’implementazione, potrebbero essere necessarie azioni sul lato client:

* In caso di delega dei sottodomini (caso normale), Adobe si occuperà di tutte le modifiche e garantirà una transizione senza soluzione di continuità
* In caso di configurazione CNAME (eccezione), al client verrà richiesto di implementare le modifiche. Sarà necessario il coordinamento con l&#39;Adobe.

Per l’accesso degli utenti e l’integrazione dei dati, i nomi in neolane.net rimarranno invariati.

Ciò significa che la modifica sarà trasparente per gli utenti e le implementazioni di integrazione dei dati, se i nomi dei server non sono stati sostituiti da IP hardcoded.

### Preparazione

**Invio di indirizzi IP tramite posta elettronica**

Innanzitutto, Adobe Deliverability valuta lo stato di recapito della piattaforma e consiglia un piano per il passaggio ai nuovi IP.

Adobe eseguirà il provisioning dello stesso numero di IP sul nuovo centro dati.

L’incremento dei nuovi IP può iniziare non appena viene effettuato il provisioning dei nuovi IP.

**Pulizia applicazione**
Il trasferimento dei dati tra i data center si trova nel percorso critico dei tempi di inattività.

I dati vengono memorizzati in due modi:

1. Di gran lunga il più importante, il database
1. File sul server applicazioni (importazioni ed esportazioni di dati)

Ridurre le dimensioni del database è della massima importanza per accelerare il trasferimento dei dati.

Suggerimenti:

* Riduci i periodi di conservazione dei dati storici (registri di consegna, registri di tracciamento, ecc.)
* Elimina record inutili in altre tabelle (consegne, destinatari, tabelle personalizzate)

### Execution

**Pausa esecuzioni**

È consigliabile rallentare e sospendere tutte le esecuzioni immediatamente prima che l’applicazione venga arrestata nel data center legacy: consegne e flussi di lavoro. Questo semplifica il riavvio su Cloud pubblico (AWS), in quanto ai processi è stato dato il tempo di sospendere &quot;agevolmente&quot; e salvare qualsiasi stato di esecuzione in corso.

**Durante la migrazione**

Durante la migrazione, rimarrà funzionante un solo servizio: reindirizzamento dei collegamenti e-mail. In altre parole, i destinatari saranno in grado di raggiungere la pagina di destinazione quando fanno clic in un’e-mail. Tuttavia, questi clic non verranno registrati, pertanto le percentuali di clic per le consegne avviate poco prima della migrazione saranno inferiori al normale.

**Riavvia**

Dopo la migrazione al nuovo ambiente, l’applicazione verrà riavviata progressivamente:

* Primo accesso alla console, per consentire agli utenti di controllare lo stato senza dover eseguire ancora nulla
* Quindi, flussi di lavoro e consegne

### Post-migrazione

**Eliminazione di istanze nel datacenter legacy**

Una volta completata la migrazione dell&#39;applicazione, non è prevista l&#39;esecuzione di alcun processo nel data center legacy. Prevediamo che tutti i dati del centro dati legacy possano essere cancellati, ad eccezione di quelli per scopi di backup temporanei, fino all’esecuzione dei processi di backup pianificati su Cloud pubblico (AWS).

**Delega DNS**

Normalmente, il dominio utilizzato per inviare e-mail (parte a destra del simbolo @ nell’indirizzo di errore) da Campaign è stato delegato ad Adobe. La delega può essere modificata e implementata nei confronti dei server DNS di AWS.


## Supporto e altri collegamenti utili{#support}

* [Domande frequenti sulla migrazione ad Adobe Managed Services (Public Cloud)](dc-migration-faq.md)
* [Aggiornamenti annuali delle campagne](../../rn/using/rn-overview.md)
* [Domande frequenti sull’aggiornamento della build](../../platform/using/faq-build-upgrade.md)
