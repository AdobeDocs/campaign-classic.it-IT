---
product: campaign
title: 'Interazione: buffer dati'
description: 'Interazione: buffer dati'
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: additional-configurations
exl-id: 7250b885-0606-466a-bfc2-6dd3cc5a012d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 3%

---

# Interazione: buffer dati{#interaction-data-buffer}



È possibile configurare una zona buffer dati per migliorare le prestazioni di interazione in entrata desincronizzando i calcoli delle proposte di offerta. Questa configurazione deve essere eseguita nel file di configurazione dell&#39;istanza (config-Instance.xml).

In Adobe Campaign, un **zona buffer dati** è stato introdotto nel modulo Interaction. Questo consente di: **migliorare le prestazioni** di Interazione in entrata tramite la desincronizzazione dei calcoli di stock e offerte.

Riguarda solo l’interazione in entrata, sia tramite una chiamata (con o senza dati di chiamata), sia tramite un aggiornamento di stato (updateStatus).

Per evitare una coda durante la scrittura di proposte relative a un destinatario, un nuovo processo genera un **zona buffer dati** che consente di presentare proposte **scritto in modo asincrono**. Questa zona del buffer dati viene periodicamente letta e svuotata. Il periodo predefinito si trova nello spazio di circa un secondo.La scrittura della proposta è quindi raggruppata.

>[!NOTE]
>
>Questo parametro è essenziale se utilizzi l’interazione con un’architettura distribuita.

Zona buffer dati **configurazione** può essere eseguito nel file di configurazione dell&#39;istanza (config-Instance.xml).

>[!CAUTION]
>
>Alcune configurazioni possono essere eseguite solo per Adobe per le distribuzioni ospitate da Adobe. Ad esempio, per accedere ai file di configurazione del server e dell’istanza. Per ulteriori informazioni sulle diverse implementazioni, consulta [Modelli di hosting](../../installation/using/hosting-models.md) sezione o [questa pagina](../../installation/using/capability-matrix.md).
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
