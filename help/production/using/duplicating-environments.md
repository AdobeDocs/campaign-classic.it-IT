---
solution: Campaign Classic
product: campaign
title: Duplicazione di ambienti
description: Duplicazione di ambienti
audience: production
content-type: reference
topic-tags: data-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1289'
ht-degree: 1%

---


# Duplicazione di ambienti{#duplicating-environments}

## Introduzione {#introduction}

### Panoramica {#overview}

>[!IMPORTANT]
>
>Se non si dispone dell&#39;accesso al server e al database (ambienti ospitati), non sarà possibile eseguire le procedure descritte di seguito. Contatta  Adobe.

Per utilizzare  Adobe Campaign è necessario installare e configurare uno o più ambienti: sviluppo, test, preproduzione, produzione, ecc.

Ogni ambiente contiene un&#39;istanza Adobe Campaign  e ogni istanza Adobe Campaign  è collegata a uno o più database. Il server applicazioni può eseguire uno o più processi: quasi tutti questi utenti hanno accesso diretto al database delle istanze.

In questa sezione vengono descritti i processi da applicare per duplicare un ambiente Adobe Campaign , ovvero per ripristinare un ambiente di origine in un ambiente di destinazione e ottenere due ambienti di lavoro identici.

A questo scopo, eseguire i seguenti passaggi:

1. Creare una copia dei database su tutte le istanze nell&#39;ambiente di origine,
1. Ripristinare queste copie su tutte le istanze dell&#39;ambiente di destinazione,
1. Eseguire lo script di cauterizzazione **nms:FrostInstance.js** nell&#39;ambiente di destinazione prima di avviarlo.

   Questo processo non ha alcun impatto sui server e sulla loro configurazione.

   >[!NOTE]
   >
   >Nel contesto di  Adobe Campaign, una **cauterizzazione** combina azioni che consentono di interrompere l’interazione con l’esterno di tutti i processi: registri, tracciamento, consegne, flussi di lavoro delle campagne, ecc.\
   >Questo passaggio è necessario per evitare di inviare messaggi più volte (una volta dall&#39;ambiente nominale e una dall&#39;ambiente duplicato).

   >[!IMPORTANT]
   >
   >Un ambiente può contenere diverse istanze. Ogni istanza di Adobe Campaign  è soggetta a un contratto di licenza. Controllate il contratto di licenza per verificare quanti ambienti è possibile utilizzare.\
   >La procedura seguente consente di trasferire un ambiente senza influire sul numero di ambienti e istanze installati.

### Prima di iniziare {#before-you-start}

>[!IMPORTANT]
>
>È consigliabile eseguire un backup completo dei database per tutte le istanze degli ambienti di origine e di destinazione prima di avviare il processo di trasferimento. In questo modo, se si verifica un problema, sarà possibile ripristinare i backup e tornare alla configurazione iniziale.

Affinché questo processo funzioni, gli ambienti di origine e di destinazione devono avere lo stesso numero di istanze, lo stesso scopo (istanza di marketing, istanza di consegna) e configurazioni simili. La configurazione tecnica deve rispettare i prerequisiti software. Gli stessi componenti devono essere installati in entrambi gli ambienti.

## Implementazione {#implementation}

### Procedura di trasferimento {#transfer-procedure}

Questa sezione illustra i passaggi necessari per trasferire un ambiente di origine a un ambiente di destinazione tramite uno studio di casi: il nostro obiettivo è quello di ripristinare un ambiente di produzione (**prod** instance) in un ambiente di sviluppo (**dev** instance) per lavorare in un contesto il più vicino possibile alla piattaforma &quot;live&quot;.

I seguenti passaggi devono essere eseguiti con grande attenzione: alcuni processi potrebbero essere ancora in corso quando i database dell&#39;ambiente di origine vengono copiati. La cauterizzazione (passaggio 3 qui sotto) impedisce l&#39;invio di messaggi due volte e assicura la coerenza dei dati.

>[!IMPORTANT]
>
>* La seguente procedura è valida in linguaggio PostgreSQL. Se il linguaggio SQL è diverso ( Oracle, ad esempio), le query SQL devono essere adattate.
>* I comandi seguenti si applicano nel contesto di un&#39;istanza **prod** e di un&#39;istanza **dev** in PostgreSQL.

>



### Passaggio 1 - Eseguire un backup dei dati dell&#39;ambiente di origine (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiare i database

Per iniziare, copiate tutti i database dell&#39;ambiente di origine. L&#39;operazione dipende dal motore del database ed è responsabilità dell&#39;amministratore del database.

In PostgreSQL, il comando è:

```
pg_dump mydatabase > mydatabase.sql
```

### Passaggio 2 - Esportare la configurazione dell&#39;ambiente di destinazione (dev) {#step-2---export-the-target-environment-configuration--dev-}

La maggior parte degli elementi di configurazione sono diversi per ogni ambiente: account esterni (mid-sourcing, routing, ecc.), opzioni tecniche (nome piattaforma, ID database, indirizzi e-mail e URL predefiniti, ecc.).

Prima di salvare il database di origine nel database di destinazione, è necessario esportare la configurazione dell&#39;ambiente di destinazione (dev). A tal fine, esportare il contenuto delle due tabelle seguenti: **xtkoption** e **nmsextaccount**.

Questa esportazione consente di mantenere la configurazione di sviluppo e aggiornare solo i dati di sviluppo (flussi di lavoro, modelli, applicazioni Web, destinatari ecc.).

A tal fine, eseguite un&#39;esportazione di pacchetto per i due elementi seguenti:

* Esportate la tabella **xtk:option** in un file &#39;options_dev.xml&#39;, senza i record con i seguenti nomi interni: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; e &#39;NmsBroadcast_RegexRules&#39;.
* In un file &#39;extaccount_dev.xml&#39;, esportate la tabella **nms:extAccount** per tutti i record con ID diverso da 0 (@id &lt;> 0).

Verificare che il numero di opzioni/account esportati sia uguale al numero di righe da esportare in ciascun file.

>[!NOTE]
>
>Il numero di righe da esportare in un pacchetto di esportazione è di 1000 righe. Se il numero di opzioni o conti esterni è superiore a 1000, è necessario eseguire diverse esportazioni.
> 
>Per ulteriori informazioni, consulta [questa sezione](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Quando la tabella nmsextaccount viene esportata, le password correlate agli account esterni (ad esempio password per Mid-sourcing, Esecuzione centro messaggi, SMPP, IMS e altri account esterni) non vengono esportate. Assicuratevi di avere accesso alle password corrette in anticipo, in quanto potrebbero dover essere reinserite dopo che gli account esterni sono stati reimportati nell&#39;ambiente.

### Passo 3 - Arrestare l&#39;ambiente di destinazione (dev) {#step-3---stop-the-target-environment--dev-}

È necessario arrestare  processi Adobe Campaign su tutti i server dell&#39;ambiente di destinazione. Questa operazione dipende dal sistema operativo in uso.

È possibile arrestare tutti i processi, o solo quelli che scrivono nel database.

Per arrestare tutti i processi, utilizzare i comandi seguenti:

* In Windows:

   ```
   net stop nlserver6
   ```

* In Linux:

   ```
   /etc/init.d/nlserver6 stop
   ```

Utilizzate il comando seguente per verificare che tutti i processi siano stati interrotti:

```
nlserver pdump
```

>[!NOTE]
>
>In Windows, il processo **webmdl** può essere ancora attivo senza avere alcun impatto sulle altre operazioni.

È inoltre possibile verificare che non siano ancora in esecuzione processi di sistema.

A tal fine, attenersi alla procedura seguente:

* In Windows: aprire **Task Manager** e verificare che non siano presenti processi **nlserver.exe** .
* In Linux: eseguire il **ps aux | grep nlserver** e verificare che non siano presenti processi **nlserver** .

### Passaggio 4 - Ripristino dei database nell&#39;ambiente di destinazione (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Per ripristinare i database di origine nell&#39;ambiente di destinazione, utilizzare il comando seguente:

```
psql mydatabase < mydatabase.sql
```

### Passo 5 - Cauterizzare l&#39;ambiente di destinazione (dev) {#step-5---cauterize-the-target-environment--dev-}

Per evitare malfunzionamenti, i processi collegati all&#39;invio della distribuzione e all&#39;esecuzione del flusso di lavoro non devono essere eseguiti automaticamente quando l&#39;ambiente di destinazione è attivato.

A questo scopo, eseguite il comando seguente:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Passaggio 6 - Controllare la cauterizzazione {#step-6---check-cauterization}

1. Verificate che l&#39;unica parte di recapito sia quella con ID impostato su 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Verificate che l&#39;aggiornamento dello stato di consegna sia corretto:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Verificare che l&#39;aggiornamento dello stato del flusso di lavoro sia corretto:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Passaggio 7 - Riavviare il processo Web dell&#39;ambiente di destinazione (dev) {#step-7---restart-the-target-environment-web-process--dev-}

Nell&#39;ambiente di destinazione, riavviare i processi Adobe Campaign  per tutti i server.

>[!NOTE]
>
>Prima di riavviare  Adobe Campaign nell&#39;ambiente di **sviluppo** , potete applicare una procedura di sicurezza aggiuntiva: avviate solo il modulo **Web** .
>  
>A questo scopo, modificate il file di configurazione dell&#39;istanza (**config-dev.xml**), quindi aggiungete il carattere &quot;_&quot; prima delle opzioni autoStart=&quot;true&quot; per ciascun modulo (mta, stat, ecc.).

Eseguite il comando seguente per avviare il processo Web:

```
nlserver start web
```

Usate il comando seguente per verificare che sia stato avviato solo il processo Web:

```
nlserver pdump
```

Controllare l&#39;accesso alle funzioni della console client.

### Passaggio 8 - Importa opzioni e account esterni nell&#39;ambiente di destinazione (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>A questo punto dovrebbe essere avviato solo il processo Web. In caso contrario, interrompere gli altri processi in esecuzione prima di continuare

Soprattutto, verificate i valori di diverse righe dei file prima di importarli (ad esempio: &#39;NmsTracking_Pointer&#39; per la tabella delle opzioni e gli account di consegna o di mid-sourcing per la tabella dei conti esterni)

Per importare la configurazione dal database dell&#39;ambiente di destinazione (dev):

1. Aprite la console di amministrazione del database ed eliminate gli account esterni (tabella nms:extAccount) il cui ID non è 0 (@id &lt;> 0).
1. Nella console  Adobe Campaign, importate il pacchetto options_dev.xml creato in precedenza tramite la funzionalità del pacchetto di importazione.

   Verificare che le opzioni siano state effettivamente aggiornate nel **[!UICONTROL Administration > Platform > Options]** nodo.

1. Nella console  Adobe Campaign, importate il file extaccount_dev.xml creato in precedenza tramite la funzionalità del pacchetto di importazione

   Verificate che le banche dati esterne siano state effettivamente importate nel **[!UICONTROL Administration > Platform > External accounts]** .

### Passaggio 9 - Riavviate tutti i processi e modificate gli utenti (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Per avviare i processi Adobe Campaign , utilizzare i comandi seguenti:

* In Windows:

   ```
   net start nlserver6
   ```

* In Linux:

   ```
   /etc/init.d/nlserver6 start
   ```

Utilizzate il comando seguente per verificare che i processi siano avviati:

```
nlserver pdump
```

Modificate gli utenti per trovare gli utenti che già esistevano sulla piattaforma di sviluppo.
