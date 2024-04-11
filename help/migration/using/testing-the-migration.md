---
product: campaign
title: Test della migrazione
description: Test della migrazione
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Test di migrazione{#testing-the-migration}



## Procedura generale {#general-procedure}

A seconda della configurazione, esistono diversi modi per eseguire i test di migrazione.

È necessario disporre di un ambiente di test/sviluppo per eseguire i test di migrazione. Gli ambienti Adobe Campaign sono soggetti a licenza: controlla il contratto di licenza o contatta il tuo rappresentante Adobe.

1. Arrestare tutti gli sviluppi in corso e trasferirli nell&#39;ambiente di produzione.
1. Eseguire un backup del database dell’ambiente di sviluppo.
1. Arresta tutti i processi Adobe Campaign nell’istanza di sviluppo.
1. Eseguire un backup del database dell’ambiente di produzione e ripristinarlo come ambiente di sviluppo.
1. Prima di avviare i servizi di Adobe Campaign, esegui **freezeInstance.js** script di cauterizzazione che consente di cancellare il database di tutti gli oggetti in esecuzione all&#39;avvio del backup.

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >Il comando viene avviato per impostazione predefinita in **asciutto** ed elenca tutte le richieste eseguite da tale comando, senza avviarle. Per eseguire le richieste di cauterizzazione, utilizzare **eseguire** nel comando.

1. Per verificare che i backup siano corretti, provare a ripristinarli. Assicurati di poter accedere al database, alle tabelle, ai dati e così via.
1. Verifica la procedura di migrazione nell’ambiente di sviluppo.
1. Se la migrazione dell’ambiente di sviluppo ha esito positivo, puoi eseguire la migrazione dell’ambiente di produzione.

>[!CAUTION]
>
>A causa delle modifiche apportate alla struttura dei dati, non è possibile importare ed esportare pacchetti di dati tra una piattaforma v5 e una piattaforma v7.


## Strumenti di migrazione {#migration-tools}

Varie opzioni consentono di misurare l’impatto di una migrazione e identificare i potenziali problemi. Devono essere eseguite le seguenti opzioni:

* nel **config** comando:

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* o al momento del post-aggiornamento:

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* È necessario utilizzare il **-instance:`<instanceame>`** opzione. Si sconsiglia di utilizzare **-allinstances** opzione.
>* Il comando di aggiornamento di Adobe Campaign (**post-aggiornamento**) consente di sincronizzare le risorse e aggiornare gli schemi e il database. Questa operazione può essere eseguita solo una volta e solo sul server applicazioni. Dopo aver sincronizzato le risorse, il **post-aggiornamento** consente di rilevare se la sincronizzazione genera errori o avvisi.

### Oggetti mancanti o non standard

* Il **-showCustomEntities** viene visualizzato l&#39;elenco di tutti gli oggetti non standard:

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  Esempio di messaggio inviato:

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* Il **-showDeletedEntities** viene visualizzato l&#39;elenco di tutti gli oggetti standard mancanti nel database o nel file system. Per ogni oggetto mancante, viene specificato il percorso.

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  Esempio di messaggio inviato:

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### Processo di verifica {#verification-process}

Integrato come standard nel comando post-aggiornamento, questo processo consente di visualizzare avvisi ed errori che potrebbero impedire il corretto completamento della migrazione. **Se vengono visualizzati degli errori, la migrazione non è stata eseguita.** In questo caso, correggi tutti gli errori e riavvia il post-aggiornamento.

Puoi avviare il processo di verifica da solo (senza migrazione) utilizzando il comando:

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>Puoi ignorare tutti gli avvisi e gli errori con il codice JST-310040.

Vengono cercate le seguenti espressioni (distinzione maiuscole/minuscole):

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
   <td> Questa funzione è supportata solo quando viene utilizzata nel codice JavaScript eseguito da un’area di sicurezza in <strong>sessionTokenOnly</strong> modalità.<br /> </td> 
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
   <td> Questo tipo di distribuzione non è più supportato. Il tipo di distribuzione del connettore Microsoft CRM per Office 365 e on-premise è ora obsoleto. 
   </br>Se utilizzi uno di questi tipi di distribuzione obsoleti in un account esterno, devi eliminarlo ed eseguire il comando <b>post-aggiornamento</b> comando. 
   </br>Per modificare la distribuzione API web, consulta <a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">Applicazioni web</a>.<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> Errore<br /> </td> 
   <td> Le attività di azione Microsoft CRM, Salesforce, Oracle CRM On Demand non sono più disponibili. Per configurare la sincronizzazione dei dati tra Adobe Campaign e un sistema CRM, è necessario utilizzare <a href="../../workflow/using/crm-connector.md" target="_blank">Connettore CRM</a> attività di targeting.<br /> </td>
  </tr> 
 </tbody> 
</table>

Viene inoltre eseguita una verifica della coerenza di database e schemi.

### Opzione di ripristino {#restoration-option}

Questa opzione consente di ripristinare gli oggetti preconfigurati, se sono stati modificati. Per ogni oggetto ripristinato, nella cartella selezionata viene memorizzato un backup delle modifiche:

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>Si consiglia vivamente di utilizzare percorsi di cartelle assoluti e di mantenere la struttura ad albero delle cartelle. Ad esempio: backupFolder\nms\srcSchema\billing.xml.

### Riprendi la migrazione {#resuming-migration}

Se si riavvia il post-aggiornamento dopo un errore di migrazione, il processo riprende dalla stessa posizione in cui era stato interrotto.
