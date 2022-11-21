---
product: campaign
title: Test della migrazione
description: Test della migrazione
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 2594e4943ba24ae65d1fc005da589dc674aa2b0f
workflow-type: tm+mt
source-wordcount: '706'
ht-degree: 4%

---

# Test di migrazione{#testing-the-migration}

![](../../assets/v7-only.svg)

## Procedura generale {#general-procedure}

A seconda della configurazione, esistono diversi modi per eseguire i test di migrazione.

Devi disporre di un ambiente di test/sviluppo per eseguire i test di migrazione. Gli ambienti Adobe Campaign sono soggetti a licenza: controlla il contratto di licenza o contatta il tuo rappresentante Adobe.

1. Arrestare tutti gli sviluppi in corso e trasferirli all&#39;ambiente di produzione.
1. Esegui un backup del database dell&#39;ambiente di sviluppo.
1. Interrompi tutti i processi Adobe Campaign nell’istanza di sviluppo.
1. Esegui un backup del database dell&#39;ambiente di produzione e ripristinalo come ambiente di sviluppo.
1. Prima di avviare i servizi Adobe Campaign, esegui la **frozenInstance.js** script di cauterizzazione che consente di cancellare il database degli oggetti in esecuzione all&#39;avvio del backup.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Il comando viene avviato per impostazione predefinita in **secco** e elenca tutte le richieste eseguite da tale comando, senza avviarle. Per eseguire richieste di cautela, utilizza **eseguire** nel comando .

1. Assicurati che i backup siano corretti cercando di ripristinarli. Assicurati di poter accedere al database, alle tabelle, ai dati e così via.
1. Verifica la procedura di migrazione nell’ambiente di sviluppo.
1. Se la migrazione dell’ambiente di sviluppo ha esito positivo, puoi eseguire la migrazione dell’ambiente di produzione.

>[!CAUTION]
>
>A causa di modifiche apportate alla struttura dei dati, l’importazione e l’esportazione di pacchetti di dati non è possibile tra una piattaforma v5 e una piattaforma v7.


## Strumenti di migrazione {#migration-tools}

Le varie opzioni consentono di misurare l’impatto di una migrazione e identificare i potenziali problemi. Queste opzioni devono essere eseguite:

* in **config** comando:

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* o al successivo aggiornamento:

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>* È necessario utilizzare **-istanza:`<instanceame>`** opzione . Si sconsiglia di utilizzare **-allinstance** opzione .
>* Comando di aggiornamento di Adobe Campaign (**postupgrade**) consente di sincronizzare le risorse e aggiornare gli schemi e il database. Questa operazione può essere eseguita solo una volta e solo sul server dell&#39;applicazione. Dopo la sincronizzazione delle risorse, la **postupgrade** consente di rilevare se la sincronizzazione genera errori o avvisi.


### Oggetti non standard o mancanti

* La **-showCustomEntities** visualizza l’elenco di tutti gli oggetti non standard:

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   Esempio di messaggio inviato:

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* La **-showDeletedEntities** visualizza l&#39;elenco di tutti gli oggetti standard mancanti nel database o nel file system. Per ogni oggetto mancante viene specificato il percorso.

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
>Con il codice JST-310040 puoi ignorare tutti gli avvisi e gli errori.

Viene eseguita la ricerca delle seguenti espressioni (distinzione maiuscole/minuscole):

<table> 
 <thead> 
  <tr> 
   <th> Espressione<br /> </th> 
   <th> Codice errore<br /> </th> 
   <th> Tipo di registro<br /> </th> 
   <th> Commenti<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> Avvertenza<br /> </td> 
   <td> Questo tipo di sintassi non è più supportato nella personalizzazione della consegna. <br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> Avvertenza<br /> </td> 
   <td> Questa libreria non deve essere utilizzata.<br /> </td> 
  </tr> 
  <tr> 
   <td> logon(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> Avvertenza<br /> </td> 
   <td> Questo metodo di connessione non deve più essere utilizzato.<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> Avvertenza<br /> </td> 
   <td> Questa funzione è supportata solo quando viene utilizzata nel codice JavaScript eseguito da una zona di sicurezza in <strong>sessionTokenOnly</strong> modalità.<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Questo tipo di errore causa un errore di migrazione.<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Questo tipo di distribuzione non è più supportato. Il tipo di distribuzione del connettore Microsoft CRM locale e Office 365 è stato dichiarato obsoleto. 
   </br>Se utilizzi uno di questi tipi di distribuzione obsoleti in un account esterno, devi eliminare questo account esterno ed eseguire quindi il <b>postupgrade</b> comando. 
   </br>Per passare alla distribuzione API Web, consulta <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Applicazioni web</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscriptWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Le attività di azione Microsoft CRM, Salesforce, Oracle CRM On Demand non sono più disponibili. Per configurare la sincronizzazione dei dati tra Adobe Campaign e un sistema CRM, devi utilizzare il <a href="../../workflow/using/crm-connector.md" target="_blank">Connettore CRM</a> attività di targeting.<br /> </td>
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

### Riprendere la migrazione {#resuming-migration}

Se riavvii l&#39;aggiornamento dopo un errore di migrazione, riprende dalla stessa posizione in cui è stato interrotto.
