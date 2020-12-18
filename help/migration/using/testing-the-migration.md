---
solution: Campaign Classic
product: campaign
title: Test della migrazione
description: Test della migrazione
audience: migration
content-type: reference
topic-tags: migration-procedure
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 1%

---


# Test della migrazione{#testing-the-migration}

## Procedura generale {#general-procedure}

A seconda della configurazione, esistono diversi modi per eseguire i test di migrazione.

È necessario disporre di un ambiente di test/sviluppo per eseguire i test di migrazione. Gli ambienti di sviluppo sono soggetti a licenza: controllare il contratto di licenza o contattare  servizio vendite Adobe Campaign.

1. Arrestare tutti gli sviluppi in corso e trasmetterli nell&#39;ambiente di produzione.
1. Eseguire un backup del database dell&#39;ambiente di sviluppo.
1. Arrestate tutti  processi Adobe Campaign nell&#39;istanza di sviluppo.
1. Eseguire un backup del database dell&#39;ambiente di produzione e ripristinarlo come ambiente di sviluppo.
1. Prima di avviare i servizi Adobe Campaign , eseguire lo script di cauterizzazione **congelamentoInstance.js** che consente di cancellare il database degli oggetti in esecuzione all&#39;avvio del backup.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Il comando viene avviato per impostazione predefinita in modalità **dry** ed elenca tutte le richieste eseguite da tale comando, senza avviarle. Per eseguire richieste di cautela, utilizzare **run** nel comando.

1. Verificare che i backup siano corretti cercando di ripristinarli. Assicuratevi di poter accedere al database, alle tabelle, ai dati e così via.
1. Verificare la procedura di migrazione nell&#39;ambiente di sviluppo.

   Le procedure complete sono descritte nella sezione [Prerequisiti per la migrazione a  Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md).

1. Se la migrazione dell&#39;ambiente di sviluppo ha esito positivo, è possibile migrare l&#39;ambiente di produzione.

>[!IMPORTANT]
>
>A causa delle modifiche apportate alla struttura dei dati, non è possibile importare ed esportare pacchetti di dati tra una piattaforma v5 e una piattaforma v7.

>[!NOTE]
>
>Il comando  aggiornamento Adobe Campaign (**postupgrade**) consente di sincronizzare le risorse e gli schemi di aggiornamento e il database. Questa operazione può essere eseguita solo una volta sul server dell&#39;applicazione. Dopo la sincronizzazione delle risorse, il comando **postupgrade** consente di rilevare se la sincronizzazione genera errori o avvisi.

## Strumenti di migrazione {#migration-tools}

Le varie opzioni consentono di misurare l’impatto di una migrazione e identificare i potenziali problemi. Devono essere eseguite le seguenti opzioni:

* nel comando **config**:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* o in seguito all&#39;aggiornamento:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>È necessario utilizzare l&#39;opzione **-instance:`<instanceame>`**. Non è consigliabile utilizzare l&#39;opzione **-allinstance**.

### -showCustomEntities e -showDeletedEntities opzioni {#showcustomentities-and--showdeletedentities-options}

* L&#39;opzione **-showCustomEntities** visualizza l&#39;elenco di tutti gli oggetti non standard:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Esempio di messaggio inviato:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* L&#39;opzione **-showDeletedEntities** visualizza l&#39;elenco di tutti gli oggetti standard mancanti nel database o nel file system. Per ogni oggetto mancante, il percorso è specificato.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Esempio di messaggio inviato:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Processo di verifica {#verification-process}

Integrato come standard nel comando post-aggiornamento, questo processo consente di visualizzare avvisi ed errori che potrebbero causare il fallimento della migrazione. **Se vengono visualizzati degli errori, la migrazione non è stata eseguita.** In questo caso, correggete tutti gli errori e riavviate il postaggiornamento.

È possibile avviare il processo di verifica autonomamente (senza migrazione) utilizzando il comando:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Ignorare tutti gli avvisi e gli errori con codice JST-310040.

Vengono cercate le seguenti espressioni (con distinzione tra maiuscole e minuscole):

<table> 
 <thead> 
  <tr> 
   <th> Expression<br /> </th> 
   <th> Codice errore<br /> </th> 
   <th> Tipo di registro<br /> </th> 
   <th> Commenti<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Avviso<br /> </td> 
   <td> Questo tipo di sintassi non è più supportato nella personalizzazione della distribuzione. Fare riferimento a <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. In caso contrario, verificare che il tipo di valore sia corretto.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Avviso<br /> </td> 
   <td> Questa libreria non deve essere utilizzata.<br /> </td> 
  </tr> 
  <tr> 
   <td> access(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Avviso<br /> </td> 
   <td> Questo metodo di connessione non deve più essere utilizzato. Fare riferimento a <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Applicazioni Web identificate</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Avviso<br /> </td> 
   <td> Questa funzione è supportata solo quando viene utilizzata nel codice JavaScript eseguito da una zona di sicurezza in modalità <strong>sessionTokenOnly</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Questo tipo di errore genera un errore di migrazione. Fare riferimento a <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Questo tipo di errore genera un errore di migrazione. Fare riferimento a <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Se si ottengono i registri di errore dell'applicazione Web di tipo panoramica (migrazione dalla versione 6.02), fare riferimento a <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Applicazioni Web</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Viene inoltre eseguita una verifica della coerenza del database e dello schema.

### Opzione di ripristino {#restoration-option}

Questa opzione consente di ripristinare gli oggetti out-of-the-box se sono stati modificati. Per ciascun oggetto ripristinato, un backup delle modifiche viene memorizzato nella cartella selezionata:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>È consigliabile utilizzare percorsi di cartella assoluti e mantenere la struttura ad albero delle cartelle. Ad esempio: backupFolder\nms\srcSchema\billing.xml.

### Ripresa della migrazione {#resuming-migration}

Se si riavvia il post-aggiornamento dopo un errore di migrazione, questo riprende dalla stessa posizione in cui è stato interrotto.
