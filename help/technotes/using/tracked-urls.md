---
product: campaign
title: Problema di firma degli URL tracciati
description: Problema di firma degli URL tracciati
feature: Technote
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 30%

---

# Problema di firma degli URL tracciati {#tracked-urls}



In seguito alle modifiche recenti, gli URL tracciati possono non riuscire quando la firma URL è attiva in Campaign. Alcune caselle e-mail possono essere più interessate di altre, in particolare quelle di aziende che usano strumenti di sicurezza specifici che possono interessare i collegamenti e modificare il meccanismo di firma degli URL.

Di conseguenza, l’Adobe consiglia di disabilitare il meccanismo di firma per il tracciamento dei collegamenti. Questa procedura corregge i vecchi collegamenti di tracciamento, ad eccezione di quelli ricevuti con un doppio escape.

Tieni presente che anche i collegamenti di annullamento di abbonamento, come tutti gli altri collegamenti, possono non riuscire; la frequenza varia da host a host ma è comunque inferiore all’1%.

**Sei interessato da questo problema?**

Per migliorare la sicurezza, il meccanismo di firma per i collegamenti nelle e-mail è stato introdotto in [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - aprile 2020 - ed è abilitato per impostazione predefinita per tutti i clienti che iniziano la build 19.1.4 (9032@3a9dc9c) e Campaign 20.2.

Se l’ambiente è in esecuzione su una delle versioni elencate di seguito, il problema può interessarti:

* Gold Standard da 8 a 11. [Ulteriori informazioni](../../rn/using/gold-standard.md#gs-8)
* Campaign da 21.1.1 (build 9277) a 21.1.2 (build 9282). [Ulteriori informazioni](../../rn/using/latest-release.md)
* Da Campaign 20.3.1 (build 9228) a 20.3.3 (build 9234).
* Campaign versioni da 20.2.1 (build 9178) a 20.2.4 (build 9187).
* Da Campaign 20.1.1 (build 9122) a 21.1.3 (build 9124).
* Campaign dalle versioni 19.2.2 (build 9080) alla versione 19.2.3 (build 9081).
* Campaign: versioni da 19.1.5 (build 9033) a 19.1.7 (build 9036).


Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**Come si esegue l’aggiornamento?**

In qualità di **cliente ospitato**, Adobe collaborerà con te per aggiornare la tua configurazione a breve.

In qualità di **cliente on-premise/ibrido**, devi aggiornare la configurazione.

Effettua le seguenti operazioni:

1. Nel [file di configurazione del server](../../installation/using/the-server-configuration-file.md) (serverConf.xml), modificare **signEmailLinks** in **false**.
1. Riavviare il servizio **nlserver**.
1. Sul server di tracciamento, riavvia il server web (apache2 su Debian, httpd su CentOS/RedHat, IIS su Windows).

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>Il file **config-`<instance>`.xml** sostituisce le impostazioni **serverConf.xml**. Se **signEmailLinks** è presente in **config-`<instance>`.xml** (dove **istanza** è il nome dell&#39;istanza), deve essere convertito anche in **false**.
>

**Quale sarà l’impatto dell&#39;aggiornamento?**

La manutenzione richiede un massimo di 25 minuti di inattività e durante questo periodo tutte le consegne, i collegamenti di tracciamento e le chiamate API non funzioneranno.

Al termine dell’aggiornamento, tutti i collegamenti torneranno a funzionare come previsto.

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
>
