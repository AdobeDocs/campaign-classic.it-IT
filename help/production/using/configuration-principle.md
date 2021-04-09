---
solution: Campaign Classic
product: campaign
title: Principio di configurazione
description: Principio di configurazione
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 03d7e579-8678-44b8-bbe7-cf4204bffb25
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 4%

---

# Principio di configurazione{#configuration-principle}

La piattaforma Adobe Campaign si basa sul concetto di istanze, simile a quella degli host virtuali utilizzati da Apache. Questa modalità di funzionamento consente di condividere un server assegnandogli più istanze. Le istanze sono completamente separate l&#39;una dall&#39;altra e operano con il proprio database e file di configurazione.

Per un determinato server, esistono due elementi comuni a tutte le istanze Adobe Campaign:

* Password **interna**: password dell&#39;amministratore generale. È comune a tutte le istanze di un particolare server applicazioni.

   >[!IMPORTANT]
   >
   >Per accedere con l&#39;identificatore **Interno**, è necessario aver precedentemente definito una password. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

* Configurazioni di più server tecnici: queste configurazioni possono essere tutte sovraccaricate nella configurazione specifica di un’istanza.

I file di configurazione vengono salvati nella directory **conf** della directory di installazione. La configurazione è suddivisa in tre file:

* **serverConf.xml**: configurazione complessiva per tutte le istanze.
* **config-**`<instance>`**.xml**  (dove  **`<instance>`** è il nome dell&#39;istanza): configurazione specifica di un&#39;istanza.
* **serverConf.xml.diff**: delta tra la configurazione iniziale e la configurazione corrente. Questo file viene generato automaticamente dall&#39;applicazione e non deve essere modificato manualmente. Viene utilizzato per propagare automaticamente le modifiche utente quando si aggiorna una versione di build.

Viene caricata una configurazione di istanza come segue:

* Il modulo carica il file **serverConf.xml** per ottenere i parametri condivisi da tutte le istanze.
* Quindi carica il file **config-**`<instance>`**.xml**. I valori trovati in questo file hanno priorità rispetto ai valori contenuti in **serverConf.xml**.

   Questi due file hanno lo stesso formato. Qualsiasi valore in **serverConf.xml** può essere sovraccaricato per una determinata istanza nel file **config-`<instance>`.xml**.

Questa modalità operativa offre una grande flessibilità per le configurazioni.
