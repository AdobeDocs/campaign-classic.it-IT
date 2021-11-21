---
product: campaign
title: Nota tecnica
description: Nota tecnica
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: ed9e76495efb0cb49e248a7d38417642c5094a11
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 35%

---

# Problema di firma degli URL tracciati {#tracked-urls}

![](../../assets/v7-only.svg)

In seguito alle modifiche recenti, gli URL tracciati possono non riuscire quando la firma URL è attiva in Campaign. Alcune caselle e-mail possono essere più interessate di altre, in particolare quelle di aziende che usano strumenti di sicurezza specifici che possono interessare i collegamenti e modificare il meccanismo di firma degli URL.

Di conseguenza, l’Adobe consiglia di disabilitare il meccanismo di firma per i collegamenti di tracciamento. Questa procedura corregge i vecchi collegamenti di tracciamento, ad eccezione di quelli ricevuti con un doppio escape.

Tieni presente che anche i collegamenti di annullamento di abbonamento, come tutti gli altri collegamenti, possono non riuscire; la frequenza varia da host a host ma è comunque inferiore all’1%.

**Sei interessato da questo problema?**

Per migliorare la sicurezza, è stato introdotto il meccanismo di firma per il tracciamento dei collegamenti nelle e-mail in [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - Aprile 2020 - ed è abilitato per impostazione predefinita per tutti i clienti a partire da Build 19.1.4 (9032@3a9dc9c) e Campaign 20.2.

Se l’ambiente è in esecuzione su una delle versioni elencate di seguito, può essere interessato:

* Gold Standard da 8 a 11. [Ulteriori informazioni](../../rn/using/gold-standard.md#gs-8)
* Rilasci di Campaign 21.1.1 (build 9277) a 21.1.2 (build 9282). [Ulteriori informazioni](../../rn/using/latest-release.md)
* versioni da Campaign 20.3.1 (build 9228) a 20.3.3 (build 9234). [Ulteriori informazioni](../../rn/using/release--20-3.md)
* versioni da Campaign 20.2.1 (build 9178) a 20.2.4 (build 9187). [Ulteriori informazioni](../../rn/using/release--20-2.md)
* versioni da Campaign 20.1.1 (build 9122) a 21.1.3 (build 9124). [Ulteriori informazioni](../../rn/using/release--20-1.md)
* Rilasci di Campaign 19.2.2 (build 9080) a 19.2.3 (build 9081). [Ulteriori informazioni](../../rn/using/release--19-2.md)
* Rilasci di Campaign 19.1.5 (build 9033) a 19.1.7 (build 9036). [Ulteriori informazioni](../../rn/using/release--19-1.md)

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

Come **cliente ospitato**, Adobe collaborerà con te per aggiornare la configurazione a breve.

Come **cliente on-premise/ibrido**, devi aggiornare la configurazione.

Segui il passaggio seguente:

1. In [file di configurazione del server](../../installation/using/the-server-configuration-file.md) (serverConf.xml), modifica **signEmailLinks** a **false**.
1. Riavvia **nlserver** servizio.
1. Sul server di tracciamento, riavvia il server web (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>La **config-`<instance>`.xml** sostituisce il file **serverConf.xml** impostazioni. Se la **signEmailLinks** è presente nel  **config-`<instance>`.xml** (4) **istanza** è il nome della tua istanza), deve anche essere girato a **false**.

**Quale sarà l’impatto dell&#39;aggiornamento?**

La manutenzione richiede un massimo di 25 minuti di inattività e durante questo periodo tutte le consegne, i collegamenti di tracciamento e le chiamate API non funzioneranno.

Al termine dell’aggiornamento, tutti i collegamenti torneranno a funzionare come previsto.

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
