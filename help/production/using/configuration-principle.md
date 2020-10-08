---
title: Principio di configurazione
seo-title: Principio di configurazione
description: Principio di configurazione
seo-description: null
page-status-flag: never-activated
uuid: 6315d526-b820-46ab-96c7-e64e101c6a7d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: d08ff769-da93-4f86-8802-f0fb5b051ece
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 5%

---


# Principio di configurazione{#configuration-principle}

La piattaforma Adobe Campaign  si basa sul concetto di istanze, simile a quello degli host virtuali utilizzati da Apache. Questa modalità di funzionamento consente di condividere un server assegnandogli più istanze. Le istanze sono completamente separate l&#39;una dall&#39;altra e funzionano con il proprio database e file di configurazione.

Per un determinato server, esistono due elementi comuni a tutte  istanze Adobe Campaign:

* La password **interna** : questa è la password dell&#39;amministratore generale. È comune a tutte le istanze di un particolare server applicazione.

   >[!CAUTION]
   >
   >Per accedere con l&#39;identificatore **Interno** , è necessario aver già definito una password. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/campaign-server-configuration.md#internal-identifier).

* Configurazioni server tecniche multiple: tutte queste configurazioni possono essere sovraccaricate nella configurazione specifica di un&#39;istanza.

I file di configurazione vengono salvati nella directory **conf** della directory di installazione. La configurazione è suddivisa in tre file:

* **serverConf.xml**: configurazione globale per tutte le istanze.
* **config-**`<instance>`**.xml** (dove **`<instance>`** è il nome dell&#39;istanza): specifica configurazione di un&#39;istanza.
* **serverConf.xml.diff**: delta tra la configurazione iniziale e quella corrente. Questo file viene generato automaticamente dall&#39;applicazione e non deve essere modificato manualmente. Viene utilizzato per estendere automaticamente le modifiche apportate dagli utenti durante l&#39;aggiornamento di una versione di build.

Una configurazione di istanza viene caricata come segue:

* Il modulo carica il file **serverConf.xml** per ottenere i parametri condivisi da tutte le istanze.
* Quindi carica il file **config-**`<instance>`**.xml** . I valori trovati in questo file hanno priorità rispetto ai valori contenuti in **serverConf.xml**.

   Questi due file hanno lo stesso formato. Qualsiasi valore in **serverConf.xml** può essere sovraccaricato per una determinata istanza nel file **config-`<instance>`.xml** .

Questa modalità operativa offre grande flessibilità per le configurazioni.
