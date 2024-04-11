---
product: campaign
title: Interazione - Buffer dati
description: Interazione - Buffer dati
feature: Installation, Instance Settings
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Interazione - Buffer dati{#interaction-data-buffer}



Puoi configurare una zona buffer dati per migliorare le prestazioni dell’interazione in entrata desincronizzando i calcoli della proposta di offerta. Questa configurazione deve essere eseguita nel file di configurazione dell’istanza (config-Instance.xml).

In Adobe Campaign, una **zona buffer dati** è stato introdotto nel modulo Interazione. Ciò ti consente di: **migliorare le prestazioni** dell’interazione in entrata tramite la desincronizzazione dei calcoli relativi alle azioni e alle offerte.

Riguarda solo l’interazione in entrata, sia tramite chiamata (con o senza dati di chiamata), sia tramite aggiornamento dello stato (updateStatus).

Per evitare una coda durante la scrittura di proposte relative a un destinatario, un nuovo processo genera un **zona buffer dati** che consente di **scritto in modo asincrono**. Questa zona buffer dati viene letta e svuotata periodicamente. Il periodo predefinito è nello spazio di circa un secondo. La scrittura delle proposte è quindi raggruppata.

>[!NOTE]
>
>Questo parametro è essenziale se utilizzi l’interazione con un’architettura distribuita.

Zona buffer dati **configurazione** può essere eseguita nel file di configurazione dell’istanza (config-Instance.xml).

>[!CAUTION]
>
>Alcune configurazioni possono essere eseguite solo da Adobe per le distribuzioni in hosting da Adobe. Ad esempio, per accedere ai file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle diverse implementazioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o a [questa pagina](../../installation/using/capability-matrix.md).
>
>Qualsiasi modifica apportata alla configurazione richiede il riavvio del server web (Apache:IIS) e dei processi di Adobe Campaign.\
>Dopo aver configurato la zona buffer dati, verificare che sia disponibile una configurazione hardware adattata. (quantità di memoria presente).


Dopo aver configurato la zona buffer dati, verificare che sia disponibile una configurazione hardware adattata. (quantità di memoria presente).

La definizione di un daemon di scrittura (processo denominato: interazione) è la seguente:

```
<interactiond args="" autoStart="false" callDataSize="0" initScript="" maxProcessMemoryAlertMb="1800"
maxProcessMemoryWarningMb="1600" maxSharedEntries="25000" nextOffersSize="0"
processRestartTime="06:00:00" runLevel="10" targetKeySize="16"/>
```

Se utilizzi l’interazione in entrata, l’attributo @autostart deve essere &quot;true&quot; per avviare automaticamente il processo all’avvio del server Adobe Campaign.

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
