---
product: campaign
title: Duplicazione di ambienti
description: Duplicazione di ambienti
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 1%

---

# Duplicazione di ambienti{#duplicating-environments}

![](../../assets/v7-only.svg)

## Introduzione {#introduction}

### Panoramica {#overview}

>[!IMPORTANT]
>
>Se non si dispone dell&#39;accesso al server e al database (ambienti ospitati), non sarà possibile eseguire le procedure descritte di seguito. Contattare l&#39;Adobe.

L’utilizzo di Adobe Campaign richiede l’installazione e la configurazione di uno o più ambienti: sviluppo, test, preproduzione, produzione, ecc.

Ogni ambiente contiene un&#39;istanza Adobe Campaign e ogni istanza Adobe Campaign è collegata a uno o più database. Il server applicazioni può eseguire uno o più processi: quasi tutti hanno accesso diretto al database delle istanze.

Questa sezione descrive i processi da applicare per duplicare un ambiente Adobe Campaign, ovvero per ripristinare un ambiente di origine in un ambiente di destinazione, in modo da ottenere due ambienti di lavoro identici.

A questo scopo, esegui i seguenti passaggi:

1. Creare una copia dei database su tutte le istanze nell&#39;ambiente di origine,
1. Ripristinare queste copie su tutte le istanze dell&#39;ambiente di destinazione,
1. Esegui il **nms:frozenInstance.js** script di cauterizzazione nell’ambiente di destinazione prima di avviarlo.

   Questo processo non influisce sui server e sulla loro configurazione.

   >[!NOTE]
   >
   >Nel contesto di Adobe Campaign, un **cauterizzazione** combina azioni che consentono di interrompere l’interazione di tutti i processi con l’esterno: registri, tracciamento, consegne, flussi di lavoro per campagne, ecc.\
   >Questo passaggio è necessario per evitare di consegnare i messaggi più volte (una volta dall’ambiente nominale e una dall’ambiente duplicato).

   >[!IMPORTANT]
   >
   >Un ambiente può contenere diverse istanze. Ogni istanza di Adobe Campaign è soggetta a un contratto di licenza. Controlla il tuo contratto di licenza per vedere quanti ambienti puoi avere.\
   >La procedura seguente consente di trasferire un ambiente senza influire sul numero di ambienti e istanze installati.

### Prima di iniziare {#before-you-start}

>[!IMPORTANT]
>
>È consigliabile eseguire un backup completo dei database per tutte le istanze degli ambienti di origine e di destinazione prima di avviare il processo di trasferimento. In questo modo, se si verifica un problema, potrai ripristinare i backup e tornare alla configurazione iniziale.

Affinché questo processo funzioni, gli ambienti di origine e di destinazione devono avere lo stesso numero di istanze, lo stesso scopo (istanza di marketing, istanza di consegna) e configurazioni simili. La configurazione tecnica deve soddisfare i prerequisiti software. Gli stessi componenti devono essere installati in entrambi gli ambienti.

## Implementazione {#implementation}

### Procedura di trasferimento {#transfer-procedure}

Questa sezione ti aiuterà a comprendere i passaggi necessari per trasferire un ambiente sorgente a un ambiente di destinazione tramite un case study: il nostro obiettivo è ripristinare un ambiente produttivo (**prod** a un ambiente di sviluppo (**dev** per lavorare in un contesto il più vicino possibile alla piattaforma &quot;live&quot;.

I seguenti passaggi devono essere eseguiti con grande attenzione: alcuni processi potrebbero essere ancora in corso quando i database dell&#39;ambiente di origine vengono copiati. La personalizzazione (passaggio 3 successivo) impedisce l’invio di messaggi due volte e mantiene la coerenza dei dati.

>[!IMPORTANT]
>
>* La seguente procedura è valida nel linguaggio PostgreSQL. Se il linguaggio SQL è diverso (ad Oracle,), le query SQL devono essere adattate.
>* I comandi seguenti si applicano nel contesto di un **prod** istanza e **dev** istanza in PostgreSQL.

>


### Passaggio 1: eseguire un backup dei dati dell’ambiente di origine (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiare i database

Per iniziare, copia tutti i database dell&#39;ambiente di origine. L&#39;operazione dipende dal motore di database ed è responsabilità dell&#39;amministratore del database.

In PostgreSQL, il comando è:

```
pg_dump mydatabase > mydatabase.sql
```

### Passaggio 2: esportare la configurazione dell’ambiente di destinazione (dev) {#step-2---export-the-target-environment-configuration--dev-}

La maggior parte degli elementi di configurazione sono diversi per ogni ambiente: account esterni (mid-sourcing, routing, ecc.), opzioni tecniche (nome piattaforma, ID database, indirizzi e-mail e URL predefiniti, ecc.).

Prima di salvare il database di origine nel database di destinazione, è necessario esportare la configurazione dell’ambiente di destinazione (dev). A questo scopo, esportare il contenuto delle due tabelle seguenti: **xtkoption** e **nmsextaccount**.

Questa esportazione consente di mantenere la configurazione di sviluppo e aggiornare solo i dati di sviluppo (flussi di lavoro, modelli, applicazioni web, destinatari, ecc.).

A questo scopo, esegui un’esportazione del pacchetto per i due elementi seguenti:

* Esporta il **xtk:opzione** in un file &#39;options_dev.xml&#39;, senza i record con i seguenti nomi interni: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; e &#39;NmsBroadcast_RegexRules&#39;.
* In un file &#39;extaccount_dev.xml&#39;, esporta il **nms:extAccount** per tutti i record il cui ID non è 0 (@id &lt;> 0).

Verifica che il numero di opzioni/account esportati sia uguale al numero di righe da esportare in ciascun file.

>[!NOTE]
>
>Il numero di righe da esportare in un pacchetto di esportazione è di 1000 righe. Se il numero di opzioni o account esterni è superiore a 1000, è necessario eseguire diverse esportazioni.
> 
>Per ulteriori informazioni, consulta [questa sezione](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Quando la tabella nmsextaccount viene esportata, le password relative agli account esterni (ad esempio password per Mid-sourcing, Message Center Execution, SMPP, IMS e altri account esterni) non vengono esportate. Assicurati di avere in anticipo l&#39;accesso alle password corrette, in quanto potrebbero dover essere reinserite dopo che gli account esterni sono stati importati di nuovo nell&#39;ambiente.

### Passaggio 3: interrompere l’ambiente di destinazione (dev) {#step-3---stop-the-target-environment--dev-}

È necessario arrestare i processi Adobe Campaign su tutti i server dell’ambiente di destinazione. Questa operazione dipende dal sistema operativo in uso.

È possibile interrompere tutti i processi o solo quelli che scrivono nel database.

Per interrompere tutti i processi, utilizzare i seguenti comandi:

* In Windows:

   ```
   net stop nlserver6
   ```

* In Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

Utilizzare il comando seguente per verificare che tutti i processi siano stati interrotti:

```
nlserver pdump
```

>[!NOTE]
>
>In Windows, la **webmdl** Il processo può essere ancora attivo senza influire su altre operazioni.

È inoltre possibile verificare che nessun processo di sistema sia ancora in esecuzione.

A questo scopo, utilizza il seguente processo:

* In Windows: apri **Gestione attività** e controlla che non ci siano **nlserver.exe** processi.
* In Linux: eseguire **ps aux | nlserver grep** controlla che non ci siano **nlserver** processi.

### Passaggio 4: ripristinare i database nell&#39;ambiente di destinazione (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Per ripristinare i database di origine nell&#39;ambiente di destinazione, utilizzare il comando seguente:

```
psql mydatabase < mydatabase.sql
```

### Passaggio 5 - Ottimizzare l’ambiente di destinazione (dev) {#step-5---cauterize-the-target-environment--dev-}

Per evitare malfunzionamenti, i processi collegati all’invio della consegna e all’esecuzione del flusso di lavoro non devono essere eseguiti automaticamente quando l’ambiente di destinazione è attivato.

A questo scopo, esegui il seguente comando:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Passaggio 6 - Controllare la cautela {#step-6---check-cauterization}

1. Verifica che l’unica parte di consegna sia quella con ID impostato su 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Verifica che l’aggiornamento dello stato di consegna sia corretto:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Verifica che l’aggiornamento dello stato del flusso di lavoro sia corretto:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Passaggio 7: riavviare il processo Web dell&#39;ambiente di destinazione (dev) {#step-7---restart-the-target-environment-web-process--dev-}

Nell’ambiente di destinazione, riavvia i processi Adobe Campaign per tutti i server.

>[!NOTE]
>
>Prima di riavviare Adobe Campaign sul **dev** ambiente, puoi applicare una procedura di sicurezza aggiuntiva: avvia **web** solo modulo.
>  
>A questo scopo, modifica il file di configurazione dell’istanza (**config-dev.xml**), quindi aggiungi il carattere &quot;_&quot; prima delle opzioni autoStart=&quot;true&quot; per ciascun modulo (mta, stat, ecc.).

Esegui il comando seguente per avviare il processo Web:

```
nlserver start web
```

Utilizzare il comando seguente per verificare che sia stato avviato solo il processo Web:

```
nlserver pdump
```

Controlla l’accesso alle funzioni della console client.

### Passaggio 8: importare opzioni e account esterni nell’ambiente di destinazione (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>A questo punto dovrebbe essere avviato solo il processo web. In caso contrario, interrompere altri processi in esecuzione prima di continuare

Soprattutto, controlla i valori di diverse righe dei file prima dell’importazione (ad esempio: &#39;NmsTracking_Pointer&#39; per la tabella delle opzioni e gli account di consegna o mid-sourcing per la tabella dell&#39;account esterno)

Per importare la configurazione dal database dell’ambiente di destinazione (dev):

1. Apri la Admin Console del database ed elimina gli account esterni (tabella nms:extAccount) il cui ID non è 0 (@id &lt;> 0).
1. Nella console Adobe Campaign, importa il pacchetto options_dev.xml creato in precedenza tramite la funzionalità del pacchetto di importazione.

   Verifica che le opzioni siano state effettivamente aggiornate nel **[!UICONTROL Administration > Platform > Options]** nodo.

1. Nella console Adobe Campaign, importa il file extaccount_dev.xml creato in precedenza tramite la funzionalità del pacchetto di importazione.

   Verificare che le banche dati esterne siano state effettivamente importate nel **[!UICONTROL Administration > Platform > External accounts]** .

### Passaggio 9: riavviare tutti i processi e modificare gli utenti (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Per avviare i processi Adobe Campaign, utilizza i seguenti comandi:

* In Windows:

   ```
   net start nlserver6
   ```

* In Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

Utilizzare il comando seguente per verificare che i processi siano avviati:

```
nlserver pdump
```

Modifica gli utenti per trovare gli utenti che erano già presenti sulla piattaforma di sviluppo.
