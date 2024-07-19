---
product: campaign
title: Ultima versione
description: Note sulla versione più recente di Campaign Classic v7
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: d31aa28da06e65664da655b6b082563767b35f7a
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 100%

---

# Ultima versione {#latest-release}

In questa pagina sono elencate nuove funzionalità, miglioramenti e correzioni introdotti con l’**ultima versione di Campaign v7**. Ogni nuova build viene fornita con uno stato che viene materializzato da un colore. Ulteriori informazioni sugli stati della build di Campaign Classic v7 in [questa pagina](rn-overview.md).

## Versione 7.4.1 - Build 9383 {#release-7-4-1}

[!BADGE Disponibilità generale]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=it#rn-statuses" tooltip="Disponibilità generale"}

_18 giugno 2024_

### Modifiche e miglioramenti {#release-7-4-1-changes}

* Poiché le credenziali dell’account di servizio (JWT) sono state dichiarate obsolete da Adobe, le integrazioni in uscita di Campaign con le soluzioni e le app Adobe ora si basano sulle credenziali OAuth server-to-server. Se hai implementato integrazioni in uscita, ad esempio l’integrazione Campaign-Analytics o l’integrazione Experience Cloud Triggers, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a OAuth prima del 27 gennaio 2025. [Ulteriori informazioni](../../integrations/using/oauth-technical-account.md)

* Dopo aver [migrato gli operatori tecnici di Campaign a Developer Console](../../technotes/using/ims-migration.md) e aver effettuato la [transizione a IMS per l’autenticazione dell’utente finale](../../technotes/using/migrate-users-to-ims.md), puoi abilitare l’interfaccia utente e le restrizioni API per rimuovere le opzioni e le funzionalità specifiche dell’autenticazione nativa. [Ulteriori informazioni](../../technotes/using/impact-ims-migration.md)



### Aggiornamenti della compatibilità {#release-7-4-1-compat}

La [matrice di compatibilità di Adobe Campaign](compatibility-matrix.md) è stata aggiornata con le modifiche in arrivo con questa nuova versione ed elencate di seguito.

* Adobe Campaign è ora compatibile con **Microsoft Server 2022** e **RHEL 9** come sistemi operativi.

* Adobe Campaign è ora compatibile con **Microsoft SQL Server 2022** e **Oracle 23c** come sistemi di gestione del database relazionale e in Federated Data Access (FDA).

* Adobe Campaign ora richiede almeno un Java Development Kit (JDK) 11. In Windows, JRE deve essere disponibile come descritto in [questa sezione](../../installation/using/application-server.md#jdk).

* L’SDK Campaign (Neolane) per applicazioni mobili è ora obsoleto. Ora devi passare ad Adobe Experience Platform SDK. [Ulteriori informazioni](deprecated-features.md).

  Nel frattempo, per garantire la continuità del servizio, Campaign v7.4 include:

   * un nuovo Campaign SDK 1.0.27 per iOS, compatibile con iOS 16 e 17 e i più recenti [requisiti della richiesta di accesso a dati personali per Apple iOS](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * un nuovo SDK Campaign per Android 14.


### Patch {#release-7-4-1-patches}

Questa versione include le seguenti correzioni:

NEO-74754, NEO-73174, NEO-72504, NEO-71534, NEO-71473, NEO-70195, NEO-69663, NEO-69651, NEO-67620, NEO-67235, NEO-66797, NEO-64680, NEO-63706, NEO-63657, NEO-62964, NEO-62575, NEO-58734, NEO-40531, NEO-36189, NEO-29592

