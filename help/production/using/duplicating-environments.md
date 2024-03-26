---
product: campaign
title: Duplicazione di ambienti
description: Duplicazione di ambienti
feature: Monitoring
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
badge-v7-prem: label="on-premise e ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 2c933fc5-1c0a-4c2f-9ff2-90d09a79c55a
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 2%

---

# Duplicazione di ambienti{#duplicating-environments}



## Introduzione {#introduction}

### Panoramica {#overview}

>[!IMPORTANT]
>
>Se non hai accesso al server e al database (ambienti in hosting), non potrai eseguire le procedure descritte di seguito. Contatta l’Adobe.

L’utilizzo di Adobe Campaign richiede l’installazione e la configurazione di uno o più ambienti: sviluppo, test, preproduzione, produzione, ecc.

Ogni ambiente contiene un’istanza di Adobe Campaign e ogni istanza di Adobe Campaign è collegata a uno o più database. Il server applicazioni può eseguire uno o più processi: quasi tutti hanno accesso diretto al database delle istanze.

Questa sezione descrive i processi da applicare per duplicare un ambiente Adobe Campaign, ovvero per ripristinare un ambiente di origine in un ambiente di destinazione, creando due ambienti di lavoro identici.

A questo scopo, esegui i seguenti passaggi:

1. Creare una copia dei database in tutte le istanze dell&#39;ambiente di origine.
1. Ripristinare queste copie in tutte le istanze dell&#39;ambiente di destinazione.
1. Esegui il **nms:freezeInstance.js** script di cauterizzazione nell’ambiente di destinazione prima di avviarlo.

   Questo processo non influisce sui server e sulla loro configurazione.

   >[!NOTE]
   >
   >Nel contesto di Adobe Campaign, un’ **cauterizzazione** combina azioni che consentono di arrestare tutti i processi che interagiscono con l’esterno: registri, tracciamento, consegne, flussi di lavoro delle campagne, ecc.\
   >Questo passaggio è necessario per evitare di inviare messaggi più volte (una volta dall’ambiente nominale e una dall’ambiente duplicato).

   >[!IMPORTANT]
   >
   >Un ambiente può contenere diverse istanze. Ogni istanza di Adobe Campaign è soggetta a un contratto di licenza. Controlla il contratto di licenza per vedere quanti ambienti puoi avere.\
   >La procedura seguente consente di trasferire un ambiente senza influire sul numero di ambienti e istanze installati.

### Prima di iniziare {#before-you-start}

>[!IMPORTANT]
>
>Si consiglia vivamente di eseguire un backup completo dei database per tutte le istanze degli ambienti di origine e di destinazione prima di avviare il processo di trasferimento. In questo modo, se si verifica un problema, sarà possibile ripristinare i backup e tornare alla configurazione iniziale.

Affinché questo processo funzioni, gli ambienti di origine e di destinazione devono avere lo stesso numero di istanze, lo stesso scopo (istanza di marketing, istanza di consegna) e configurazioni simili. La configurazione tecnica deve soddisfare i prerequisiti software. Gli stessi componenti devono essere installati in entrambi gli ambienti.

## Implementazione {#implementation}

### Procedura di trasferimento {#transfer-procedure}

Questa sezione ti aiuta a capire i passaggi necessari per trasferire un ambiente sorgente a un ambiente di destinazione tramite un caso di studio: il nostro obiettivo è quello di ripristinare un ambiente di produzione (**prod** a un ambiente di sviluppo (**dev** per lavorare in un contesto il più vicino possibile alla piattaforma &quot;live&quot;.

È necessario eseguire con molta attenzione i seguenti passaggi: alcuni processi potrebbero essere ancora in corso quando vengono copiati i database dell’ambiente di origine. La cauterizzazione (passaggio 3 di seguito) impedisce l’invio doppio dei messaggi e mantiene la coerenza dei dati.

>[!IMPORTANT]
>
>* La procedura seguente è valida nel linguaggio PostgreSQL. Se il linguaggio SQL è diverso (ad Oracle), è necessario adattare le query SQL.
>* I comandi riportati di seguito si applicano nel contesto di un **prod** e un **dev** in PostgreSQL.
>

### Passaggio 1: eseguire un backup dei dati dell’ambiente di origine (prod) {#step-1---make-a-backup-of-the-source-environment--prod--data}

Copiare i database

Iniziare copiando tutti i database dell&#39;ambiente di origine. L&#39;operazione dipende dal motore del database ed è responsabilità dell&#39;amministratore del database.

In PostgreSQL, il comando è:

```
pg_dump mydatabase > mydatabase.sql
```

### Passaggio 2: esportare la configurazione dell’ambiente di destinazione (dev) {#step-2---export-the-target-environment-configuration--dev-}

La maggior parte degli elementi di configurazione sono diversi per ciascun ambiente: account esterni (mid-sourcing, routing, ecc.), opzioni tecniche (nome piattaforma, DatabaseId, indirizzi e-mail e URL predefiniti, ecc.).

Prima di salvare il database di origine nel database di destinazione, è necessario esportare la configurazione dell&#39;ambiente di destinazione (dev). A questo scopo, esporta il contenuto di queste due tabelle: **xtkoption** e **nmsextaccount**.

Questa esportazione consente di mantenere la configurazione di sviluppo e di aggiornare solo i dati di sviluppo (flussi di lavoro, modelli, applicazioni web, destinatari, ecc.).

A questo scopo, esegui un’esportazione del pacchetto per i due elementi seguenti:

* Esporta il **xtk:opzione** tabella in un file &#39;options_dev.xml&#39;, senza i record con i seguenti nomi interni: &#39;WdbcTimeZone&#39;, &#39;NmsServer_LastPostUpgrade&#39; e &#39;NmsBroadcast_RegexRules&#39;.
* In un file &#39;extaccount_dev.xml&#39;, esportare il file **nms:extAccount** tabella per tutti i record il cui ID non è 0 (@id &lt;> 0).

Verifica che il numero di opzioni/conti esportati sia uguale al numero di righe da esportare in ciascun file.

>[!NOTE]
>
>Il numero di righe da esportare in un&#39;esportazione di pacchetto è 1000 righe. Se il numero di opzioni o account esterni è superiore a 1000, è necessario eseguire diverse esportazioni.
> 
>Per ulteriori informazioni, consulta [questa sezione](../../platform/using/working-with-data-packages.md#exporting-packages).

>[!NOTE]
>
>Quando la tabella nmsextaccount viene esportata, le password relative agli account esterni (ad esempio le password per Mid-sourcing, Message Center Execution, SMPP, IMS e altri account esterni) non vengono esportate. Assicurati di disporre in anticipo dell’accesso alle password corrette, in quanto potrebbe essere necessario inserirle nuovamente dopo che gli account esterni saranno stati importati nuovamente nell’ambiente.

### Passaggio 3: arrestare l’ambiente di destinazione (dev) {#step-3---stop-the-target-environment--dev-}

È necessario interrompere i processi di Adobe Campaign su tutti i server dell’ambiente di destinazione. Questa operazione dipende dal sistema operativo.

È possibile arrestare tutti i processi o solo quelli che scrivono nel database.

Per arrestare tutti i processi, utilizzare i seguenti comandi:

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
>In Windows, il **webmdl** Il processo può essere ancora attivo senza influire su altre operazioni.

È inoltre possibile verificare che non siano ancora in esecuzione processi di sistema.

A questo scopo, utilizza il seguente processo:

* In Windows: apri **Gestione attività** e verifica che non siano presenti **nlserver.exe** processi.
* In Linux: esegui **ps aux | grep nlserver** e verificare che non siano presenti **nlserver** processi.

### Passaggio 4: ripristinare i database nell&#39;ambiente di destinazione (dev) {#step-4---restore-the-databases-in-the-target-environment--dev-}

Per ripristinare i database di origine nell&#39;ambiente di destinazione, utilizzare il comando seguente:

```
psql mydatabase < mydatabase.sql
```

### Passaggio 5: cauterizzare l’ambiente di destinazione (dev) {#step-5---cauterize-the-target-environment--dev-}

Per evitare malfunzionamenti, i processi collegati all’invio della consegna e all’esecuzione del flusso di lavoro non devono essere eseguiti automaticamente quando l’ambiente di destinazione è attivato.

A tale scopo, eseguire il comando seguente:

```
nlserver javascript nms:freezeInstance.js -instance:<dev> -arg:run
```

### Passaggio 6 - Controllare la cauterizzazione {#step-6---check-cauterization}

1. Verifica che l’unica parte di consegna sia quella il cui ID è impostato su 0:

   ```
   SELECT * FROM neolane.nmsdeliverypart;
   ```

1. Verifica che l’aggiornamento dello stato della consegna sia corretto:

   ```
   SELECT iState, count(*) FROM neolane.nmsdelivery GROUP BY iState;
   ```

1. Verifica che l’aggiornamento dello stato del flusso di lavoro sia corretto:

   ```
   SELECT iState, count(*) FROM neolane.xtkworkflow GROUP BY iState;
   SELECT iStatus, count(*) FROM neolane.xtkworkflow GROUP BY iStatus;
   ```

### Passaggio 7: riavviare il processo Web dell&#39;ambiente di destinazione (dev) {#step-7---restart-the-target-environment-web-process--dev-}

Nell’ambiente di destinazione, riavvia i processi di Adobe Campaign per tutti i server.

>[!NOTE]
>
>Prima di riavviare Adobe Campaign su **dev** è possibile applicare una procedura di sicurezza aggiuntiva: avviare il **web** solo modulo.
>  
>A questo scopo, modifica il file di configurazione dell’istanza (**config-dev.xml**), quindi aggiungi il carattere &quot;_&quot; prima delle opzioni autoStart=&quot;true&quot; per ciascun modulo (mta, stat, ecc.).

Eseguire il comando seguente per avviare il processo Web:

```
nlserver start web
```

Utilizza il comando seguente per verificare che sia stato avviato solo il processo web:

```
nlserver pdump
```

Verifica che l’accesso alle funzioni della console client sia corretto.

### Passaggio 8: importare opzioni e account esterni nell’ambiente di destinazione (dev) {#step-8---import-options-and-external-accounts-into-the-target-environment--dev-}

>[!IMPORTANT]
>
>Solo il processo web deve essere avviato in questo passaggio. In caso contrario, arrestare gli altri processi in esecuzione prima di continuare

Soprattutto, controlla i valori di diverse righe dei file prima di importarli (ad esempio: &quot;NmsTracking_Pointer&quot; per la tabella delle opzioni e i conti di consegna o di mid-sourcing per la tabella dei conti esterni)

Per importare la configurazione dal database dell’ambiente di destinazione (dev):

1. Apri Admin Console del database ed elimina gli account esterni (tabella nms:extAccount) il cui ID non è 0 (@id &lt;> 0).
1. Nella console Adobe Campaign, importa il pacchetto options_dev.xml creato in precedenza tramite la funzionalità di importazione del pacchetto.

   Verifica che le opzioni siano state effettivamente aggiornate in **[!UICONTROL Administration > Platform > Options]** nodo.

1. Nella console Adobe Campaign, importa il file extaccount_dev.xml creato in precedenza tramite la funzionalità di importazione dei pacchetti

   Verificare che le banche dati esterne siano state effettivamente importate nel **[!UICONTROL Administration > Platform > External accounts]** .

### Passaggio 9: riavviare tutti i processi e modificare gli utenti (dev) {#step-9---restart-all-processes-and-change-users--dev-}

Per avviare i processi di Adobe Campaign, utilizza i seguenti comandi:

* In Windows:

  ```
  net start nlserver6
  ```

* In Linux:

  ```
  /etc/init.d/nlserver6 start
  ```

Utilizza il seguente comando per verificare che i processi siano avviati:

```
nlserver pdump
```

Cambia gli utenti per trovare gli utenti che già esistevano sulla piattaforma di sviluppo.
