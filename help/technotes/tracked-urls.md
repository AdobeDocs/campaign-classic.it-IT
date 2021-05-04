---
solution: Campaign Classic
product: campaign
title: Nota tecnica
description: Nota tecnica
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 51773f48bac90febe44c6796b8cc08fce072bab3
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 5%

---

# Problema di firma degli URL tracciati {#tracked-urls}

In seguito alle modifiche recenti, gli URL tracciati possono non riuscire quando la firma URL è attiva in Campaign. Alcune cassette postali possono essere più interessate di altre, in quanto alcune aziende dispongono di strumenti di sicurezza specifici che possono influenzare i collegamenti e modificare il meccanismo di firma degli URL.

Di conseguenza, l’Adobe consiglia di disabilitare il meccanismo di firma per i collegamenti di tracciamento. Questa procedura corregge i vecchi collegamenti di tracciamento, ad eccezione di quelli ricevuti con un doppio escape.

I collegamenti di annullamento all’abbonamento possono non riuscire come qualsiasi altro collegamento, la frequenza è variabile da host a host ma è inferiore all’1%.

**Siete interessati?**

Per migliorare la sicurezza, il meccanismo di firma per i collegamenti di tracciamento nelle e-mail è stato introdotto in [Campaign Gold Standard 8](../rn/using/gold-standard.md#gs8) - aprile 2020 - ed è abilitato per impostazione predefinita per tutti i clienti che iniziano Build 19.1.4 (9032@3a9dc9c) e Campaign 20.2.

Se l’ambiente è in esecuzione su una delle versioni elencate di seguito, può essere interessato:

* Gold Standard da 8 a 11. [Ulteriori informazioni](../rn/using/gold-standard.md#gs-8)
* Rilasci di Campaign 21.1.1 (build 9277) a 21.1.2 (build 9282). [Ulteriori informazioni](../rn/using/latest-release.md)
* versioni da Campaign 20.3.1 (build 9228) a 20.3.3 (build 9234). [Ulteriori informazioni](../rn/using/release--20-3.md)
* versioni da Campaign 20.2.1 (build 9178) a 20.2.4 (build 9187). [Ulteriori informazioni](../rn/using/release--20-2.md)
* versioni da Campaign 20.1.1 (build 9122) a 21.1.3 (build 9124). [Ulteriori informazioni](../rn/using/release--20-1.md)
* Rilasci di Campaign 19.2.2 (build 9080) a 19.2.3 (build 9081). [Ulteriori informazioni](../rn/using/release--19-2.md)
* Rilasci di Campaign 19.1.5 (build 9033) a 19.1.7 (build 9036). [Ulteriori informazioni](../rn/using/release--19-1.md)

Scopri come controllare la versione [in questa sezione](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si aggiorna?**

In qualità di **cliente in hosting**, Adobe collaborerà con te per aggiornare la tua configurazione a breve.

In qualità di **cliente on-premise/ibrido**, devi aggiornare la configurazione.

Segui il passaggio seguente:

1. Nel [file di configurazione del server](../installation/using/the-server-configuration-file.md) (serverConf.xml), cambia **signEmailLinks** in **false**.
1. Riavvia il servizio **nlserver** .
1. Sul server di tracciamento, riavvia il server web (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Il file **config-`<instance>`.xml** sostituisce le impostazioni **serverConf.xml**. Se il **signEmailLinks** è presente nel **config-`<instance>`.xml** (dove **instance** è il nome della tua istanza), deve anche essere ruotato su **false**.


**Qual è l&#39;impatto?**

La manutenzione richiede un massimo di 25 minuti di inattività e durante questo periodo tutte le consegne, i collegamenti di tracciamento e le chiamate API non funzioneranno.

Al termine dell’aggiornamento, tutti i collegamenti funzionano come previsto.

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta l&#39; [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

