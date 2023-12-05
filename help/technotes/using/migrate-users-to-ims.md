---
title: Migrazione degli operatori di Campaign a Adobe Identity Management System (IMS)
description: Scopri come migrare gli operatori di Campaign a Adobe Identity Management System (IMS)
source-git-commit: 18166dd389847d6b844ed478e19c42e457abeb80
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 2%

---

# Migrazione degli operatori di Campaign a Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Come parte degli sforzi per rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare la modalità di autenticazione dell’utente finale dall’autenticazione nativa di login/password ad Adobe Identity Management System (IMS). Tutti gli operatori devono implementare [Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} per connettersi a Campaign.

In Campaign v8, la connessione con l’utente o la password (autenticazione nativa) non sarà più consentita. **L’Adobe consiglia di eseguire questa migrazione in Campaign v7.3.5 per eseguire in modo fluido la migrazione a Campaign v8.**

Questo articolo descrive i passaggi necessari per migrare un operatore tecnico all’account tecnico nella console Adobe Developer.

## Cosa è cambiato?{#move-to-ims-changes}

Con Campaign Classic, tutti gli utenti normali possono già connettersi alla console client di Adobe Campaign utilizzando il proprio Adobe ID, tramite Adobe Identity Management System (IMS). Tuttavia, le connessioni utente/password sono ancora disponibili. Questo non sarà più consentito con Campaign v8.

Inoltre, come parte del tentativo di rafforzare la sicurezza e il processo di autenticazione, l’applicazione client Adobe Campaign ora chiama le API di Campaign direttamente utilizzando il token dell’account tecnico IMS. La migrazione per gli operatori tecnici è descritta in un articolo dedicato, disponibile in [questa pagina](ims-migration.md).

Questa modifica è già applicabile in Campaign Classic v7 e sarà **obbligatorio** per passare a Campaign v8.

## Sei interessato?{#migrate-ims-impacts}

Questa procedura si applica a tutti gli utenti di Campaign che non si connettono già a Campaign con il proprio Adobe ID.

Se gli operatori della tua organizzazione si connettono alla console client di Campaign utilizzando il proprio login/password (alias. autenticazione nativa), sei interessato e devi migrare questi operatori in Adobe IMS come descritto di seguito.

Migrazione a [Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} è un imperativo di sicurezza per rendere gli ambienti sicuri e standardizzati, in quanto la maggior parte delle altre soluzioni e app Adobe Experience Cloud sono già su IMS.

## Come effettuare la migrazione degli ambienti in hosting e Managed Services? {#ims-migration-procedure}

### Prerequisiti {#ims-migration-prerequisites}

Prima di iniziare la migrazione, devi contattare il tuo Adobe Transition Manager (per i clienti Managed Services) o l’Assistenza clienti Adobe (per altri clienti in hosting), in modo che i team tecnici Adobe possano migrare i gruppi di operatori e i diritti denominati esistenti ad Adobe Identity Management System (IMS).

### Passaggi chiave {#ims-migration-steps}

I passaggi chiave per questa migrazione sono elencati di seguito:

1. Adobe aggiorna gli ambienti a Campaign v7.3.5.
1. Dopo l’aggiornamento, è comunque possibile creare nuovi utenti con entrambi i metodi, come utente nativo o con IMS.
1. L’amministratore di Campaign interno deve aggiungere e-mail univoche a tutti gli utenti nativi sulla console client di Campaign e confermare al rappresentante di Adobe/all’Assistenza clienti al termine.  Questo passaggio è descritto in [questa sezione](#ims-migration-id).
1. Collabora con il tuo rappresentante di Adobe/Assistenza clienti per proteggere una data, ad Adobe per l’esecuzione della migrazione automatizzata per gli utenti non tecnici (operatori) e i profili di prodotto. Questo passaggio richiede una finestra temporale senza tempi di inattività per nessuno dei servizi.
1. L’amministratore di Campaign interno convalida queste modifiche e fornisce l’approvazione. Dopo questa migrazione, non sarà più necessario creare alcun operatore che effettui l’autenticazione con il suo login e la sua password.

Puoi anche eseguire la migrazione degli operatori tecnici alla console Adobe Developer, come descritto in [questa nota tecnica](ims-migration.md).

Al termine della migrazione, conferma su Adobe Transition Manager (per gli utenti Managed Services) o su Adobe Customer Care (per i clienti in hosting). L’Adobe contrassegna quindi la migrazione come completata. L’ambiente viene quindi protetto e standardizzato.


## Come si esegue la migrazione degli ambienti ibridi e on-premise? {#ims-migration-procedure-on-prem}

I passaggi chiave per questa migrazione sono elencati di seguito:

1. Aggiorna gli ambienti a Campaign v7.3.5.
1. Dopo l’aggiornamento, è comunque possibile creare nuovi utenti con entrambi i metodi, come utente nativo o con IMS.
1. L’amministratore interno di Campaign deve configurare Adobe IMS come descritto in [questa sezione](../../integrations/using/configuring-ims.md).
1. Quindi aggiungi e-mail univoche a tutti gli utenti nativi nella console client di Campaign. Questo passaggio è descritto in [questa sezione](#ims-migration-id).
1. Creare utenti e profili di prodotto in Adobe Admin Console come descritto in [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Abilita **Connettersi con Adobe ID** per tutti gli operatori.
1. Implementare Adobe IMS per la connessione come descritto in [questa pagina](../../integrations/using/implementing-ims.md).

Puoi anche eseguire la migrazione degli operatori tecnici alla console Adobe Developer, come descritto in [questa nota tecnica](ims-migration.md).


## Domande frequenti {#ims-migration-faq}

### Quando posso avviare la migrazione? {#ims-migration-start}

Una raccomandazione per la migrazione a [Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} è quello di aggiornare l’ambiente a Campaign Classic v7.3.5.

Una volta effettuato l’aggiornamento a Campaign Classic v7.3.5, puoi avviare la migrazione IMS nell’ambiente di stage e pianificare di conseguenza l’ambiente di produzione.

### Cosa succede dopo l’aggiornamento della build a Campaign Classic v7.3.5? {#ims-migration-after-upgrade}

Dopo aver aggiornato gli ambienti a Campaign Classic v7.3.5, puoi avviare la transizione a [Sistema Adobe Identity Management (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}.

### Quando è stata completata la migrazione? {#ims-migration-end}

Al termine della migrazione degli utenti finali e della migrazione tecnica degli utenti ad Adobe Identity Management System (IMS), contatta il rappresentante/supporto clienti di Adobe in modo che Adobe possa contrassegnare la migrazione come completata.

### Come creare gli utenti dopo la migrazione? {#ims-migration-native}

L’Adobe consiglia di creare solo utenti IMS dopo l’aggiornamento a Campaign Classic v7.3.5.

In qualità di amministratore di Campaign, puoi concedere autorizzazioni agli utenti della tua organizzazione tramite Adobe Admin Console e la console client di Campaign. Gli utenti accedono ad Adobe Campaign con il proprio Adobe ID. Scopri come impostare le autorizzazioni con IMS in [Documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=it){target="_blank"}.

### Come si aggiungono le e-mail per gli utenti nativi attuali? {#ims-migration-id}

In qualità di amministratore di Campaign, devi aggiungere gli ID e-mail a tutti gli utenti nativi dalla console client. A tale scopo, segui i passaggi indicati di seguito:

1. Connettiti alla console client e individua **Amministrazione > Gestione degli accessi > Operatori**.
1. Selezionare l&#39;operatore da aggiornare nell&#39;elenco degli operatori.
1. Inserisci l’e-mail dell’operatore nel **Punti di contatto** sezione del modulo operatore.
1. Salva le modifiche.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### Come effettuare l’accesso a Campaign tramite IMS? {#ims-migration-log}

Scopri come connetterti a Campaign con il tuo Adobe ID in [questa sezione](../../integrations/using/implementing-ims.md).

### Durante questa migrazione si verificherà un tempo di inattività? {#ims-migration-downtime}

Per i clienti in hosting e Managed Services, per finalizzare la migrazione (migrazione di utenti e profili di prodotto), Adobe richiede una finestra di un’ora senza tempi di inattività per nessuna delle istanze (flussi di lavoro, ecc.).

Durante questo arco temporale, tutti gli utenti di Campaign devono disconnettersi e tornare con il proprio Adobe ID una volta completata la migrazione a IMS.

L’Adobe consiglia vivamente di disconnettersi da tutti gli utenti durante la finestra di migrazione.

### Gli utenti della mia organizzazione utilizzano già IMS: devo ancora eseguire la migrazione IMS?{#ims-migration-needed}

Questa migrazione presenta due aspetti: migrazione degli utenti finali (più profili di prodotto) e migrazione degli utenti tecnici (utilizzata nelle API nel codice personalizzato).

Se tutti gli utenti (operatori di Campaign) utilizzano IMS, dovrai comunque contattare il rappresentante Adobe/supporto clienti per pianificare la migrazione dei profili di prodotto. Sarà inoltre necessario eseguire la migrazione degli utenti tecnici eventualmente utilizzati nel codice personalizzato. Per ulteriori informazioni, consulta [questa pagina](ims-migration.md).

## Collegamenti utili {#ims-useful-links}

* [Migrazione degli utenti tecnici alla console Adobe Developer](ims-migration.md)
* [Note sulla versione di Adobe Campaign v8](../../rn/using/latest-release.md)
* [Che cos’è Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}
