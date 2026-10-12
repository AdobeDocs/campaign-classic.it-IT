---
title: Migrazione degli operatori di Campaign ad Adobe Identity Management System (IMS)
description: Scopri come migrare gli operatori Campaign ad Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
TQID: 'https://experienceleague.adobe.com/drpNkA9cj7Prid--GixHMQ48CO7ZC9qqX4w5fnTiD88'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: d5ef99fa-df0c-4153-bf94-105ad0724167
    internal-label: Integrations
subfeature_v2:
  - id: efa38731-2723-4334-8d8b-a778af834835
    internal-label: Access management
  - id: cbcf4d90-26be-46e2-b16a-aebc529dc41e
    internal-label: Analytics integration
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 4bc1e76d129c6a6aa15b7e3915232043bd6f4286
workflow-type: tm+mt
source-wordcount: '676'
ht-degree: 2%
---
# Migrazione degli operatori di Campaign ad Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Per rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare la modalità di autenticazione dell’utente finale dall’autenticazione nativa di login/password ad Adobe Identity Management System (IMS). Tutti gli operatori devono implementare [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/identity.html){target="_blank"} per connettersi a Campaign.

Ulteriori informazioni su questa migrazione in [questa pagina](ac-ims.md).

## Cosa è cambiato? {#move-to-ims-changes}

Con Campaign Classic, tutti gli utenti normali possono già connettersi alla console client di Adobe Campaign utilizzando il proprio Adobe ID, tramite Adobe Identity Management System (IMS). Tuttavia, le connessioni utente/password sono ancora disponibili. Questo non sarà più consentito con Campaign v8.

Inoltre, come parte del tentativo di rafforzare la sicurezza e il processo di autenticazione, l’applicazione client Adobe Campaign ora chiama le API di Campaign direttamente utilizzando il token dell’account tecnico IMS. La migrazione per gli operatori tecnici è descritta in un articolo dedicato, disponibile in [questa pagina](ims-migration.md).

Questa modifica è già applicabile in Campaign Classic v7 e sarà **obbligatoria** per passare a Campaign v8.

Adobe ti supporta in questo sforzo di migrazione. Il contesto dettagliato e le linee guida passo passo sono disponibili nell’articolo seguente.

## Sei interessato?{#migrate-ims-impacts}

Questa procedura si applica a tutti gli utenti di Campaign che non si connettono già a Campaign con il proprio Adobe ID.

Se gli operatori della tua organizzazione si connettono alla console client di Campaign utilizzando il proprio login/password (alias. autenticazione nativa), sei interessato e devi migrare questi operatori in Adobe IMS come descritto di seguito.

La migrazione a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/identity.html){target="_blank"} è un imperativo di sicurezza per rendere gli ambienti sicuri e standardizzati, in quanto la maggior parte delle altre soluzioni e app Adobe Experience Cloud sono già in IMS.

Questa modifica è applicabile a partire da Campaign Classic v7.4.1 (e dalle ultime [versioni compatibili con la migrazione IMS](ac-ims.md#ims-versions)) ed è **obbligatorio** per il passaggio ad Adobe Campaign v8.

>[!IMPORTANT]
>
>**Impatto di accesso al Pannello di controllo Campaign**
>
>Dopo aver trasferito gli utenti a IMS, tieni presente che qualsiasi profilo di prodotto nel Adobe Admin Console che contiene la parola &quot;admin&quot; nel nome (ad esempio &quot;Administrators&quot;, &quot;admin&quot;, &quot;admins&quot;, &quot;approval admin&quot;, ecc.) concederà automaticamente l’accesso al Pannello di controllo Campaign Campaign. Pannelli di controllo Campaign è uno strumento self-service che consente di apportare modifiche significative alle istanze di Campaign.
>
>Esamina attentamente le convenzioni di denominazione del profilo di prodotto per assicurarti che solo gli utenti autorizzati abbiano accesso al Pannello di controllo Campaign. Per ulteriori informazioni sulla gestione delle autorizzazioni di Pannello di controllo Campaign, consulta la [documentazione del Pannello di controllo Campaign](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=it){target="_blank"}.


## Come si esegue la migrazione degli ambienti ibridi e on-premise? {#ims-migration-procedure-on-prem}

I passaggi chiave per questa migrazione sono elencati di seguito:

1. Aggiorna gli ambienti a Campaign v7.4.1 (o a una versione compatibile con [IMS](#ims-versions)).
1. Dopo l’aggiornamento, è comunque possibile creare nuovi utenti con entrambi i metodi, come utente nativo o con IMS.
1. L&#39;amministratore interno di Campaign deve configurare Adobe IMS come descritto in [questa sezione](../../integrations/using/configuring-ims.md).
1. Quindi aggiungi e-mail univoche a tutti gli utenti nativi nella console client di Campaign. Questo passaggio è descritto in [questa sezione](https://experienceleague.adobe.com/it/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-id){target="_blank"} (documentazione di Campaign v8).
1. Crea utenti e profili di prodotto in Adobe Admin Console come descritto nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=it){target="_blank"}.
1. Abilita l&#39;opzione **Connetti con Adobe ID** per tutti gli operatori.
1. Implementa Adobe IMS per la tua connessione come descritto in [questa pagina](../../integrations/using/implementing-ims.md).

È inoltre possibile eseguire la migrazione degli operatori tecnici a Adobe Developer Console come descritto in [questa nota tecnica](ims-migration.md).

## Domande frequenti {#ims-migration-faq}

Per le risposte alle domande comuni sulla migrazione (creazione di utenti dopo la migrazione, aggiunta di e-mail per gli utenti nativi, accesso tramite IMS, downtime, organizzazioni che già utilizzano IMS, visualizzazione del tipo di autenticazione degli operatori), consulta la [nota tecnica di Campaign v8](https://experienceleague.adobe.com/it/docs/campaign/technotes-ac/tn-new/migrate-users-to-ims#ims-migration-faq){target=_blank} (documentazione di Campaign v8).

>[!MORELIKETHIS]
>
>* [Migrazione degli utenti tecnici alla console Adobe Developer](ims-migration.md)
>* [Note sulla versione di Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Che cos&#39;è Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/identity.html){target="_blank"}
