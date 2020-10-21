---
title: 'Interazione: buffer dati'
seo-title: 'Interazione: buffer dati'
description: 'Interazione: buffer dati'
seo-description: null
page-status-flag: never-activated
uuid: 4cb742b5-6bde-43e8-b26b-16f27dd65f72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: additional-configurations
discoiquuid: cbfdeb2f-4f20-45b8-8cc0-89362f9ea9c1
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 4%

---


# Interazione: buffer dati{#interaction-data-buffer}

>[!NOTE]
>
>Alcune configurazioni possono essere eseguite solo da  Adobe per le distribuzioni ospitate da  Adobe. Ad esempio, per accedere ai file di configurazione del server e dell&#39;istanza. Per ulteriori informazioni sulle diverse distribuzioni, fare riferimento alla sezione Modelli [di](../../installation/using/hosting-models.md) hosting o a [questa pagina](../../installation/using/capability-matrix.md).

In  Adobe Campaign, nel modulo Interaction è stata introdotta una zona **del buffer** dati. Questo consente di **aumentare le prestazioni** dell&#39;interazione in entrata desincronizzando i calcoli di azioni e offerte.

Riguarda solo l&#39;interazione in ingresso, sia tramite una chiamata (con o senza dati di chiamata), sia tramite un aggiornamento dello stato (updateStatus).

Per evitare una coda durante la scrittura di proposte relative a un destinatario, un nuovo processo W genera una zona **buffer** dati che consente di **scrivere le proposte in modo asincrono**. Questa zona del buffer dati viene letta e svuotata periodicamente. Il periodo predefinito si trova nello spazio di circa un secondo.La scrittura delle proposte è quindi raggruppata.

La **configurazione** della zona del buffer dati può essere effettuata nel file di configurazione dell&#39;istanza (config-Instance.xml).

>[!NOTE]
>
>Qualsiasi modifica apportata alla configurazione richiede il riavvio del server Web (Apache:IIS) e dei processi Adobe Campaign .\
>Dopo aver configurato la zona del buffer dati, verificare che sia disponibile una configurazione hardware adattata. (quantità di memoria presente).

Dopo aver configurato la zona del buffer dati, verificare che sia disponibile una configurazione hardware adattata. (quantità di memoria presente).

Definizione per un demone di scrittura (processo denominato: interazione) è la seguente:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Se utilizzate Interazione in ingresso, l&#39;attributo @autostart deve essere &quot;true&quot; per avviare automaticamente il processo all&#39;avvio del server Adobe Campaign .

Dettagli argomento:

```
 args: Start-up parameters 
 autoStart: Automatic start Default: false 
 callDataSize: Max. number of characters stored in the shared memory for call data
 Default: 0 
 initScript: ID of JavaScript to execute when starting the process 
 maxProcessMemoryAlertMb: Alert concerning the amount of RAM consumed (in Mb) by a given process Default: 1800 
 maxProcessMemoryWarningMb: Warning concerning the amount of RAM consumed (in Mb) by a given process Default: 1600 
 maxSharedEntries: Max. number of events stored in the shared memory. Default: 25000 
 nextOffersSize: Maximum number of eligible offers sorted right after propositions, to be stored for statistics Default: 0 
 processRestartTime: Time of the day when the process is automatically restartedDefault: '06:00:00' 
 runLevel: Priority at start Default: 10 
 targetKeySize: Max. number of characters stored in the shared memory for identifying individuals Default: 16 
```

