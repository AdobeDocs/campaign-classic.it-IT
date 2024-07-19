---
product: campaign
title: Configurazione delle impostazioni di consegna di Campaign
description: Scopri come configurare le impostazioni di consegna delle campagne
feature: Installation, Channel Configuration
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: 2968d8db-2b4b-48e6-a22e-daba5ffe0576
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 5%

---

# Configurare le impostazioni di consegna {#delivery-settings}



I parametri di consegna devono essere configurati nella cartella **serverConf.xml**.

* **Configurazione DNS**: specificare il dominio di consegna e gli indirizzi IP (o host) dei server DNS utilizzati per rispondere alle query DNS di tipo MX eseguite dal modulo MTA a partire da **`<dnsconfig>`**.

  >[!NOTE]
  >
  >Il parametro **nameServers** è essenziale per un&#39;installazione in Windows. Per un&#39;installazione in Linux, deve essere lasciata vuota.

  ```
  <dnsConfig localDomain="domain.com" nameServers="192.0.0.1,192.0.0.2"/>
  ```

Puoi anche eseguire le seguenti configurazioni in base alle tue esigenze e impostazioni: configura un [inoltro SMTP](#smtp-relay), adatta il numero di [processi secondari MTA](#mta-child-processes), [Gestisci traffico SMTP in uscita](#managing-outbound-smtp-traffic-with-affinities).

## Inoltro SMTP {#smtp-relay}

Il modulo MTA funge da agente di trasferimento di posta nativo per la trasmissione SMTP (porta 25).

È tuttavia possibile sostituirlo con un server di inoltro se richiesto dai criteri di sicurezza. In tal caso, la velocità effettiva globale sarà quella di inoltro (purché la velocità effettiva del server di inoltro sia inferiore a quella di Adobe Campaign).

In questo caso, questi parametri vengono impostati configurando il server SMTP nella sezione **`<relay>`**. È necessario specificare l&#39;indirizzo IP (o host) del server SMTP utilizzato per trasferire la posta e la relativa porta associata (25 per impostazione predefinita).

```
<relay address="192.0.0.3" port="25"/>
```

>[!IMPORTANT]
>
>Questa modalità operativa implica serie limitazioni sulle consegne, in quanto può ridurre notevolmente il throughput a causa delle prestazioni intrinseche del server di inoltro (latenza, larghezza di banda...). Inoltre, la capacità di qualificare gli errori di consegna sincrona (rilevati analizzando il traffico SMTP) sarà limitata e l’invio non sarà possibile se il server di inoltro non è disponibile.

## Processi secondari MTA {#mta-child-processes}

È possibile controllare il numero di processi secondari (maxSpareServers per impostazione predefinita 2) per ottimizzare le prestazioni di trasmissione in base alla potenza della CPU dei server e alle risorse di rete disponibili. Questa configurazione deve essere effettuata nella sezione **`<master>`** della configurazione MTA in ogni singolo computer.

```
<master dataBasePoolPeriodSec="30" dataBaseRetryDelaySec="60" maxSpareServers="2" minSpareServers="0" startSpareServers="0">
```

Consulta anche [Ottimizzazione invio e-mail](../../installation/using/email-deliverability.md#email-sending-optimization).

## Gestire il traffico SMTP in uscita con affinità {#managing-outbound-smtp-traffic-with-affinities}

>[!IMPORTANT]
>
>La configurazione dell’affinità deve essere coerente da un server all’altro. È consigliabile contattare l’Adobe per la configurazione dell’affinità, in quanto le modifiche alla configurazione devono essere replicate in tutti i server applicazioni che eseguono l’MTA.

Puoi migliorare il traffico SMTP in uscita attraverso le affinità con gli indirizzi IP.

A questo scopo, esegui i seguenti passaggi:

1. Immettere le affinità nella sezione **`<ipaffinity>`** del file **serverConf.xml**.

   Un&#39;affinità può avere diversi nomi: per separarli, utilizzare il carattere **;**.

   Esempio:

   ```
    IPAffinity name="mid.Server;WWserver;local.Server">
             <IP address="XX.XXX.XX.XX" heloHost="myserver.us.campaign.net" publicId="123" excludeDomains="neo.*" weight="5"/
   ```

   Per visualizzare i parametri rilevanti, fare riferimento al file **serverConf.xml**.

1. Per abilitare la selezione di affinità negli elenchi a discesa, è necessario aggiungere i nomi di affinità nell&#39;enumerazione **IPAffinity**.

   ![](assets/ipaffinity_enum.png)

   >[!NOTE]
   >
   >Le enumerazioni sono dettagliate in [questo documento](../../platform/using/managing-enumerations.md).

   Puoi quindi selezionare l’affinità da utilizzare, come mostrato di seguito per le tipologie:

   ![](assets/ipaffinity_typology.png)

   >[!NOTE]
   >
   >È inoltre possibile fare riferimento a [Configurazione del server di consegna](../../installation/using/email-deliverability.md#delivery-server-configuration).

**Argomenti correlati**
* [Configurazioni tecniche delle e-mail](email-deliverability.md)
* [Utilizzo dei server MX con Campaign](using-mx-servers.md)
* [Configurare CCN e-mail](email-archiving.md)
