---
product: campaign
title: 'Interazione: buffer dati'
description: 'Interazione: buffer dati'
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# Interazione: buffer dati{#interaction-data-buffer}

È possibile configurare una zona buffer dati per migliorare le prestazioni di interazione in entrata desincronizzando i calcoli delle proposte di offerta. Questa configurazione deve essere eseguita nel file di configurazione dell&#39;istanza (config-Instance.xml).

In Adobe Campaign, nel modulo di interazione è stata introdotta una **zona buffer dati**. Questo ti consente di **aumentare le prestazioni** di Interazione in entrata desincronizzando i calcoli di stock e offerte.

Riguarda solo l’interazione in entrata, sia tramite una chiamata (con o senza dati di chiamata), sia tramite un aggiornamento di stato (updateStatus).

Per evitare una coda durante la scrittura di proposte relative a un destinatario, un nuovo processo genera una **zona buffer dati** che consente di scrivere le proposte in modo **asincrono**. Questa zona del buffer dati viene periodicamente letta e svuotata. Il periodo predefinito si trova nello spazio di circa un secondo.La scrittura della proposta è quindi raggruppata.

>[!NOTE]
>
>Questo parametro è essenziale se utilizzi l’interazione con un’architettura distribuita.

La zona del buffer dati **configuration** può essere fatta nel file di configurazione dell&#39;istanza (config-Instance.xml).

>[!CAUTION]
>
>Alcune configurazioni possono essere eseguite solo per Adobe per le distribuzioni ospitate da Adobe. Ad esempio, per accedere ai file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle diverse distribuzioni, consulta la sezione [Modelli di hosting](../../installation/using/hosting-models.md) o [questa pagina](../../installation/using/capability-matrix.md).
>
>Qualsiasi modifica apportata alla configurazione richiede un riavvio del server web (Apache:IIS) e dei processi Adobe Campaign.\
>Dopo aver configurato la zona del buffer dati, verificare che sia disponibile una configurazione hardware adattata. (quantità di memoria presente).


Dopo aver configurato la zona del buffer dati, verificare che sia disponibile una configurazione hardware adattata. (quantità di memoria presente).

Definizione di un daemon di scrittura (processo denominato: interazione) è la seguente:

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
