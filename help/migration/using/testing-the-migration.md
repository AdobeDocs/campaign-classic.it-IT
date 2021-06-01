---
product: campaign
title: Test della migrazione
description: Test della migrazione
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 1%

---

# Test della migrazione{#testing-the-migration}

## Procedura generale {#general-procedure}

A seconda della configurazione, esistono diversi modi per eseguire i test di migrazione.

Devi disporre di un ambiente di test/sviluppo per eseguire i test di migrazione. Gli ambienti di sviluppo sono soggetti a licenza: controlla il contratto di licenza o contatta il servizio vendite Adobe Campaign.

1. Arrestare tutti gli sviluppi in corso e trasferirli all&#39;ambiente di produzione.
1. Esegui un backup del database dell&#39;ambiente di sviluppo.
1. Interrompi tutti i processi Adobe Campaign nell’istanza di sviluppo.
1. Esegui un backup del database dell&#39;ambiente di produzione e ripristinalo come ambiente di sviluppo.
1. Prima di avviare i servizi Adobe Campaign, esegui lo script di avvertenza **frozenInstance.js** che consente di cancellare il database degli oggetti in esecuzione all&#39;avvio del backup.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Il comando viene avviato per impostazione predefinita in modalità **dry** ed elenca tutte le richieste eseguite da tale comando, senza avviarle. Per eseguire richieste di cautela, utilizza **run** nel comando .

1. Assicurati che i backup siano corretti cercando di ripristinarli. Assicurati di poter accedere al database, alle tabelle, ai dati e così via.
1. Verifica la procedura di migrazione nell’ambiente di sviluppo.

   Le procedure complete sono descritte in dettaglio nella sezione [Prerequisiti per la migrazione ad Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) .

1. Se la migrazione dell’ambiente di sviluppo ha esito positivo, puoi eseguire la migrazione dell’ambiente di produzione.

>[!IMPORTANT]
>
>A causa di modifiche apportate alla struttura dei dati, l’importazione e l’esportazione di pacchetti di dati non è possibile tra una piattaforma v5 e una piattaforma v7.

>[!NOTE]
>
>Il comando di aggiornamento di Adobe Campaign (**postupgrade**) consente di sincronizzare le risorse e aggiornare gli schemi e il database. Questa operazione può essere eseguita solo una volta e solo sul server dell&#39;applicazione. Dopo aver sincronizzato le risorse, il comando **postupgrade** consente di rilevare se la sincronizzazione genera errori o avvisi.

## Strumenti di migrazione {#migration-tools}

Le varie opzioni consentono di misurare l’impatto di una migrazione e identificare i potenziali problemi. Queste opzioni devono essere eseguite:

* nel comando **config** :

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* o al successivo aggiornamento:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>È necessario utilizzare l&#39;opzione **-instance:`<instanceame>`**. Si sconsiglia di utilizzare l&#39;opzione **-allinstances**.

### Opzioni -showCustomEntities e -showDeletedEntities {#showcustomentities-and--showdeletedentities-options}

* L&#39;opzione **-showCustomEntities** visualizza l&#39;elenco di tutti gli oggetti non standard:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Esempio di messaggio inviato:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* L&#39;opzione **-showDeletedEntities** visualizza l&#39;elenco di tutti gli oggetti standard mancanti nel database o nel file system. Per ogni oggetto mancante viene specificato il percorso.

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   Esempio di messaggio inviato:

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### Processo di verifica {#verification-process}

Integrato come standard nel comando post aggiornamento, questo processo consente di visualizzare avvisi ed errori che potrebbero impedire la migrazione. **Se vengono visualizzati degli errori, la migrazione non è stata eseguita.** In questo caso, correggi tutti gli errori e riavvia il post aggiornamento.

È possibile avviare il processo di verifica da solo (senza migrazione) utilizzando il comando:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>Ignora tutti gli avvisi e gli errori che hanno il codice JST-310040.

Viene eseguita la ricerca delle seguenti espressioni (distinzione maiuscole/minuscole):

<table> 
 <thead> 
  <tr> 
   <th> Espressione<br /> </th> 
   <th> Codice di errore<br /> </th> 
   <th> Tipo di registro<br /> </th> 
   <th> Commenti<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Avviso<br /> </td> 
   <td> Questo tipo di sintassi non è più supportato nella personalizzazione della consegna. Fare riferimento a <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>. In caso contrario, verifica che il tipo di valore sia corretto.<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Avviso<br /> </td> 
   <td> Questa libreria non deve essere utilizzata.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Avviso<br /> </td> 
   <td> Questo metodo di connessione non deve più essere utilizzato. Fare riferimento a <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">Applicazioni web identificate</a>.<br /> </td> 
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
   <td> Questo tipo di errore causa un errore di migrazione. Fare riferimento a <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Questo tipo di errore causa un errore di migrazione. Fare riferimento a <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>. Se ottieni i log degli errori dell'applicazione web di tipo panoramica (migrazione dalla versione 6.02), fai riferimento a <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Applicazioni web</a>.<br /> </td> 
  </tr> 
 </tbody> 
</table>

Viene inoltre eseguito un controllo della coerenza del database e dello schema.

### Opzione di ripristino {#restoration-option}

Questa opzione consente di ripristinare gli oggetti predefiniti se sono stati modificati. Per ogni oggetto ripristinato, un backup delle modifiche viene memorizzato nella cartella selezionata:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>È consigliabile utilizzare percorsi di cartella assoluti e mantenere la struttura ad albero delle cartelle. Ad esempio: backupFolder\nms\srcSchema\billing.xml.

### Ripresa della migrazione {#resuming-migration}

Se riavvii l&#39;aggiornamento dopo un errore di migrazione, riprende dalla stessa posizione in cui è stato interrotto.
