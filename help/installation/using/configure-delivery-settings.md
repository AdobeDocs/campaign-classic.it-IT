---
product: campaign
title: Configurazione delle impostazioni di consegna Campaign
description: Scopri come configurare le impostazioni di consegna di Campaign
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 5%

---

# Configurare le impostazioni di consegna {#delivery-settings}



I parametri di consegna devono essere configurati nel **serverConf.xml** cartella.

* **Configurazione DNS**: specifica il dominio di consegna e gli indirizzi IP (o host) dei server DNS utilizzati per rispondere alle query DNS di tipo MX effettuate dal modulo MTA dal **`<dnsconfig>`** a partire da .

   >[!NOTE]
   >
   >La **nameServers** è essenziale per un&#39;installazione in Windows. Per un&#39;installazione in Linux, deve essere lasciata vuota.

   ```
   <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
   ```

Puoi anche eseguire le seguenti configurazioni in base alle tue esigenze e impostazioni: configurare un [relè SMTP](#smtp-relay), adegua il numero di [Processi figlio MTA](#mta-child-processes), [Gestione del traffico SMTP in uscita](#managing-outbound-smtp-traffic-with-affinities).

## relè SMTP {#smtp-relay}

Il modulo MTA agisce come agente nativo di trasferimento della posta per la trasmissione SMTP (porta 25).

È tuttavia possibile sostituirlo con un server relay se richiesto dal criterio di sicurezza. In tal caso, il throughput globale sarà quello relay (purché il throughput del server relay sia inferiore a quello di Adobe Campaign).

In questo caso, questi parametri vengono impostati configurando il server SMTP nel **`<relay>`** sezione . È necessario specificare l’indirizzo IP (o l’host) del server SMTP utilizzato per trasferire la posta e la relativa porta associata (25 per impostazione predefinita).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Questa modalità operativa implica gravi limitazioni delle consegne, in quanto può ridurre notevolmente il throughput a causa delle prestazioni intrinseche del server relay (latenza, larghezza di banda...). Inoltre, la capacità di qualificare gli errori di consegna sincroni (rilevati analizzando il traffico SMTP) sarà limitata e l’invio non sarà possibile se il server relay non è disponibile.

## Processi figlio MTA {#mta-child-processes}

È possibile controllare il numero di processi figlio (maxSpareServers per impostazione predefinita 2) al fine di ottimizzare le prestazioni di trasmissione in base alla potenza della CPU dei server e alle risorse di rete disponibili. Questa configurazione deve essere effettuata nella **`<master>`** sezione della configurazione MTA su ogni singolo computer.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Fai riferimento anche a [Ottimizzazione dell’invio di e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

## Gestire il traffico SMTP in uscita con le affinità {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configurazione dell’affinità deve essere coerente da un server all’altro. È consigliabile contattare l’Adobe per la configurazione dell’affinità, in quanto le modifiche di configurazione devono essere replicate su tutti i server applicativi che eseguono l’MTA.

Puoi migliorare il traffico SMTP in uscita tramite affinità con indirizzi IP.

A questo scopo, esegui i seguenti passaggi:

1. Immetti le affinità in **`<ipaffinity>`** della sezione **serverConf.xml** file.

   Un&#39;affinità può avere diversi nomi diversi: per separarli, utilizza **;** carattere.

   Esempio:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Per visualizzare i parametri rilevanti, fai riferimento alla sezione **serverConf.xml** file.

1. Per abilitare la selezione dell’affinità negli elenchi a discesa, devi aggiungere i nomi di affinità in **IPAffinity** enumerazione.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Le enumerazioni sono descritte in [presente documento](../../platform/using/managing-enumerations.md).

   Puoi quindi selezionare l’affinità da utilizzare, come mostrato di seguito per le tipologie:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >Puoi anche fare riferimento a [Configurazione del server di consegna](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Argomenti correlati**
* [Configurazioni tecniche delle e-mail](email-deliverability.md)
* [Utilizzo dei server MX con Campaign](using-mx-servers.md)
* [Configurare CCN e-mail](email-archiving.md)
