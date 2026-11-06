---
keywords: Campaign Classic;home;argomenti principali
product: campaign
title: Documentazione del prodotto Adobe Campaign Classic v7
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: fbeb3bb6f89cd0b03d1fb4551496f96eda0cbf10
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 40%
---
# Documentazione di Campaign Classic v7 {#campaign-classic-documentation}

Questa documentazione tratta Campaign Classic v7 per **distribuzioni on-premise e ibride**: installazione, configurazione, aggiornamenti, operazioni e funzionalità specifiche di v7. Se l&#39;istanza è ospitata da Adobe (Managed Cloud Services), consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/campaign-home){target="_blank"}. Il contenuto che documenta Campaign v8 nello stesso modo non viene più duplicato qui: vedi [Da v7 a v8](#from-v7-to-v8).

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## Novità

Dai un’occhiata ai più recenti miglioramenti apportati al prodotto e alla documentazione di Adobe Campaign Classic v7. Per un elenco completo delle funzioni, miglioramenti e correzioni, consulta le [Note sulla versione](rn/using/latest-release.md).

>[!BEGINTABS]


>[!TAB La versione di ottobre 2026 è live!]

La build di Campaign Classic v7.4.5 - ottobre 2026 (Build 9420) fornisce correzioni per l’account esterno di Analytics, consegne bloccate nello stato di personalizzazione in sospeso, utilizzo del server CPU, errori intermittenti di aggiornamento del modello dati, errore di controllo della posta indesiderata nella creazione della consegna e quarantena dei mancati recapiti non permanenti ricorrenti.

[![immagine](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB Migrare ad Adobe IMS]

Al fine di rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare la modalità di autenticazione dell’utente finale dall’autenticazione nativa di login/password ad Adobe Identity Management System (IMS).

[![immagine](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## Inizia dalle basi

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>Avviare Adobe Campaign</strong><br/>Scopri come avviare la console client di Campaign e collegarti ai server applicazioni di Campaign.</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>Aggiungere e gestire i profili</strong><br/>Esplora con facilità la gestione dei profili nel database di Adobe Campaign v7. Aggiungi profili manualmente o tramite importazioni, perfezionando i dati dei clienti e personalizzando le campagne in modo semplice.</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/it/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>Automatizzare con i flussi di lavoro</strong><br/>Scopri come sfruttare il flusso di lavoro per progettare i processi come segmentazione, esecuzione di campagne, elaborazione di file, partecipazione di utenti, ecc.
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>Creare consegne</strong><br/>Scopri come inviare messaggi attraverso vari canali come ad esempio e-mail, SMS e notifiche push.</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/it/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## Esplora la documentazione

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>Amministratori</strong><br/><a href="production/using/architecture-and-open-ports.md">Principi dell'architettura</a> - <a href="production/using/syslogd-port-and-security-zones.md">Configura Campaign</a> - <a href="platform/using/launching-adobe-campaign.md">Connetti a Campaign</a> - <a href="installation/using/external-accounts.md">Connetti a sistemi esterni</a> - <a href="platform/using/access-management.md">Autorizzazioni</a> - <a href="platform/using/privacy-management.md">Privacy e consenso</a> - <a href="production/using/build-upgrade.md">Esecuzione di un aggiornamento della build</a> - <a href="delivery/using/about-deliverability.md">Recapito messaggi</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
      <br/>
      <strong>Esperti di marketing</strong><br/><a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">Interfaccia utente</a> (documentazione di Campaign v8) - <a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/data/import" target="_blank">Importa ed esporta dati</a> (documentazione di Campaign v8) - <a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">Crea elenchi</a> (documentazione di Campaign v8) - <a href="delivery/using/about-services-and-subscriptions.md">Servizi e abbonamenti</a> - <a href="delivery/using/communication-channels.md">Canali di comunicazione</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/create-message" target="_blank">Invia bozze</a> (documentazione di Campaign v8) - <a href="delivery/using/get-started-a-b-testing.md">Test A/B</a> - <a href="message-center/using/about-transactional-messaging.md">Transazionale messaggistica</a> - <a href="interaction/using/interaction-and-offer-management.md">Gestione delle interazioni e delle offerte</a> - <a href="https://experienceleague.adobe.com/it/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank">Automatizzare con i flussi di lavoro</a> (documentazione di Campaign v8) - <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=it" target="_blank">Campagna di marketing</a> - <a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">Tracciamento dei messaggi</a> (documentazione di Campaign v8) - <a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">Generazione rapporti</a> (documentazione di Campaign v8)
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>Sviluppatori</strong><br/><a href="https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/developer/datamodel" target="_blank">Descrizione del modello dati</a> (documentazione di Campaign v8) - <a href="configuration/using/about-schema-reference.md">Struttura dello schema</a> - <a href="configuration/using/editing-forms.md">Moduli di input</a> - <a href="configuration/using/about-web-services.md">API</a> - <a href="https://experienceleague.adobe.com/it/tools/campaign-api" target="_blank">Documentazione di riferimento JSAPI</a> - <a href="configuration/using/about-custom-recipient-table.md">Tabella dei destinatari personalizzata</a>
    </td>
  </tr>
</table>

## Da v7 a v8 {#from-v7-to-v8}

Il contenuto documentato nella documentazione di Campaign v8 è stato rimosso dalla documentazione di v7. Usa questa tabella per trovarla.

| Se stai cercando... | Vai alla documentazione di Campaign v8 |
| --- | --- |
| Interfaccia utente | [Scopri l&#39;interfaccia utente](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| Profili, elenchi, importazione ed esportazione | [Importare profili e dati](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/data/import){target="_blank"} |
| Flussi di lavoro | [Informazioni sui flussi di lavoro](https://experienceleague.adobe.com/it/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| Campagne di marketing | [Introduzione alle campagne di marketing](https://experienceleague.adobe.com/it/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| Creazione e invio di consegne | [Crea un messaggio](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| Rapporti incorporati | [Introduzione al reporting](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| Autorizzazioni | [Introduzione alle autorizzazioni](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| Moduli di input | [Introduzione ai moduli di input](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## Risorse aggiuntive

[Descrizione del prodotto Adobe Campaign](https://helpx.adobe.com/it/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} - [Matrice di compatibilità](rn/using/compatibility-matrix.md) - [Tutorial](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it){target="_blank"} - [Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=it){target="_blank"} - [Pixel di tracciamento nelle email e linee guida della CNIL](https://experienceleague.adobe.com/it/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}
