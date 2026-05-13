---
product: campaign
title: Versioni di Campaign Classic 2024
description: Ulteriori informazioni sulle versioni di Campaign Classic 2024
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
TQID: https://experienceleague.adobe.com/xYAjQLPvvsTN7DqzdIC8cdyODew3nA-ipPjccmY8LDY
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
subfeature_v2: id: c3bf7e1e-1db5-4c72-9293-e2f0b1ab73d0id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 410
ht-degree: 100%

---

# Versioni 2024{#release-2024}

## Versione 7.4.1 - Build 9383 {#release-7-4-1}

[!BADGE Disponibilità generale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}

_18 giugno 2024_

### Modifiche e miglioramenti {#release-7-4-1-changes}

* Poiché le credenziali dell’account di servizio (JWT) sono state dichiarate obsolete da Adobe, le integrazioni in uscita di Campaign con le soluzioni e le app Adobe ora si basano sulle credenziali OAuth server-to-server. Se hai implementato integrazioni in uscita, ad esempio l’integrazione Campaign-Analytics o l’integrazione Experience Cloud Triggers, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a OAuth prima del 27 gennaio 2025. [Ulteriori informazioni](../../integrations/using/oauth-technical-account.md)

* Dopo aver [migrato gli operatori tecnici di Campaign a Developer Console](../../technotes/using/ims-migration.md) e aver effettuato la [transizione a IMS per l’autenticazione dell’utente finale](../../technotes/using/migrate-users-to-ims.md), puoi abilitare l’interfaccia utente e le restrizioni API per rimuovere le opzioni e le funzionalità specifiche dell’autenticazione nativa. [Ulteriori informazioni](../../technotes/using/impact-ims-migration.md)


### Aggiornamenti della compatibilità {#release-7-4-1-compat}

La [matrice di compatibilità di Adobe Campaign](compatibility-matrix.md) è stata aggiornata con le modifiche in arrivo con questa nuova versione ed elencate di seguito.

* Adobe Campaign è ora compatibile con **Microsoft Server 2022** come sistema operativo.
* Adobe Campaign è ora compatibile con **RHEL 9** come sistema operativo.

  >[!CAUTION]
  >
  >In qualità di cliente on-premise che utilizza RHEL 9, se desideri utilizzare l’autenticazione DKIM (Domain Keys Identified Mail) devi aggiornare le impostazioni di sistema come descritto in [questa sezione](../../installation/using/installing-packages-with-linux.md#rhel-9-update).


* Adobe Campaign è ora compatibile con **Microsoft SQL Server 2022** e **Oracle 23c** come sistemi di gestione del database relazionale e in Federated Data Access (FDA).

* Adobe Campaign ora richiede almeno un Java Development Kit (JDK) 11. In Windows, JRE deve essere disponibile come descritto in [questa sezione](../../installation/using/application-server.md#jdk).

* L’SDK Campaign (Neolane) per applicazioni mobili è ora obsoleto. Ora devi passare ad Adobe Experience Platform SDK. [Ulteriori informazioni](deprecated-features.md).

  Nel frattempo, per garantire la continuità del servizio, Campaign v7.4 include:

   * un nuovo SDK di Campaign 1.0.27 per iOS, compatibile con iOS 16 e 17 e con i [requisiti Apple per le richieste sulla privacy di iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"} più recenti.
   * un nuovo SDK Campaign per Android 14.

### Altre modifiche {#release-7-4-1-other}

A partire dalla versione 7.4.1, le librerie XML per i pacchetti RPM Linux non sono più incluse in Campaign. In qualità di cliente on-premise o ibrido, l’amministratore deve installare queste librerie. [Ulteriori informazioni](../../installation/using/installing-packages-with-linux.md)

### Patch {#release-7-4-1-patches}

Questa versione include le seguenti correzioni:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592


