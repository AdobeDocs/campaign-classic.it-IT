---
product: campaign
title: Principio di configurazione
description: Principio di configurazione
feature: Monitoring, Configuration
badge-v7-prem: label="Solo on-premise/ibrido" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Applicabile solo alle distribuzioni on-premise e ibride"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 5%

---

# Principio di configurazione{#configuration-principle}



La piattaforma Adobe Campaign si basa sul concetto di istanze, simile a quella degli host virtuali utilizzati da Apache. Questa modalità operativa consente di condividere un server assegnandovi più istanze. Le istanze sono completamente separate tra loro e funzionano con il proprio database e file di configurazione.

Per un determinato server, esistono due elementi comuni a tutte le istanze di Adobe Campaign:

* La password **internal**: è la password dell&#39;amministratore generale. È comune a tutte le istanze di un determinato server applicazioni.

  >[!IMPORTANT]
  >
  >Per accedere con l&#39;identificatore **Internal**, è necessario aver già definito una password. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Più configurazioni tecniche del server: queste configurazioni possono essere tutte sovraccariche nella configurazione specifica di un’istanza.

I file di configurazione vengono salvati nella directory **conf** della directory di installazione. La configurazione è suddivisa in tre file:

* **serverConf.xml**: configurazione globale per tutte le istanze.
* **config-**`<instance>`**.xml** (dove **`<instance>`** è il nome dell&#39;istanza): configurazione specifica di un&#39;istanza.
* **serverConf.xml.diff**: delta tra la configurazione iniziale e la configurazione corrente. Questo file viene generato automaticamente dall&#39;applicazione e non deve essere modificato manualmente. Viene utilizzato per propagare automaticamente le modifiche utente quando si aggiorna una versione di build.

Viene caricata una configurazione di istanza come segue:

* Il modulo carica il file **serverConf.xml** per ottenere i parametri condivisi da tutte le istanze.
* Quindi carica il file **config-**`<instance>`**.xml**. I valori trovati in questo file hanno priorità rispetto ai valori contenuti in **serverConf.xml**.

  Questi due file hanno lo stesso formato. Qualsiasi valore in **serverConf.xml** può essere sovraccaricato per una determinata istanza nel file **config-`<instance>`.xml**.

Questa modalità operativa offre grande flessibilità per le configurazioni.
