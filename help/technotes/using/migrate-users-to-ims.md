---
title: Migrazione degli operatori di Campaign ad Adobe Identity Management System (IMS)
description: Scopri come migrare gli operatori di Campaign ad Adobe Identity Management System (IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 2%

---

# Migrazione degli operatori di Campaign ad Adobe Identity Management System (IMS) {#migrate-users-to-ims}

Come parte degli sforzi per rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare la modalità di autenticazione dell’utente finale dall’autenticazione nativa di login/password ad Adobe Identity Management System (IMS). Tutti gli operatori devono implementare [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} per connettersi a Campaign.

Ulteriori informazioni su questa migrazione in [questa pagina](ac-ims.md).

## Cosa è cambiato? {#move-to-ims-changes}

Con Campaign Classic, tutti gli utenti normali possono già connettersi alla console client di Adobe Campaign utilizzando il proprio Adobe ID, tramite Adobe Identity Management System (IMS). Tuttavia, le connessioni utente/password sono ancora disponibili. Questo non sarà più consentito con Campaign v8.

Inoltre, come parte del tentativo di rafforzare la sicurezza e il processo di autenticazione, l’applicazione client Adobe Campaign ora chiama le API di Campaign direttamente utilizzando il token dell’account tecnico IMS. La migrazione per gli operatori tecnici è descritta in un articolo dedicato, disponibile in [questa pagina](ims-migration.md).

Questa modifica è già applicabile in Campaign Classic v7 e sarà **obbligatoria** per passare a Campaign v8.

Adobe ti supporta in questo sforzo di migrazione. Il contesto dettagliato e le linee guida passo passo sono disponibili nell’articolo seguente.

## Sei interessato?{#migrate-ims-impacts}

Questa procedura si applica a tutti gli utenti di Campaign che non si connettono già a Campaign con il proprio Adobe ID.

Se gli operatori della tua organizzazione si connettono alla console client di Campaign utilizzando il proprio login/password (alias. autenticazione nativa), sei interessato e devi migrare questi operatori in Adobe IMS come descritto di seguito.

La migrazione a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} è un imperativo di sicurezza per rendere gli ambienti sicuri e standardizzati, in quanto la maggior parte delle altre soluzioni e app Adobe Experience Cloud sono già in IMS.

Questa modifica è applicabile a partire da Campaign Classic v7.4.1 (e dalle ultime [versioni compatibili con la migrazione IMS](ac-ims.md#ims-versions)) ed è **obbligatorio** per il passaggio ad Adobe Campaign v8.


## Come effettuare la migrazione degli ambienti in hosting e Managed Services? {#ims-migration-procedure}

### Prerequisiti {#ims-migration-prerequisites}

Prima di avviare il processo di migrazione, devi contattare il tuo Adobe Transition Manager (per i clienti Managed Services) o l’Assistenza clienti di Adobe (per altri clienti in hosting), in modo che i team tecnici di Adobe possano migrare i gruppi di operatori e i diritti denominati esistenti ad Adobe Identity Management System (IMS).

### Passaggi chiave {#ims-migration-steps}

I passaggi chiave per questa migrazione sono elencati di seguito:

1. Adobe aggiorna gli ambienti a Campaign v7.4.1 (o a una versione [compatibile con la migrazione IMS](ac-ims.md#ims-versions)).
1. Dopo l’aggiornamento, è comunque possibile creare nuovi utenti con entrambi i metodi, come utente nativo o con IMS.
1. L’amministratore di Campaign interno deve aggiungere e-mail univoche a tutti gli utenti nativi sulla console client di Campaign e confermare al rappresentante/Assistenza clienti Adobe al termine.  Questo passaggio è descritto in [questa sezione](#ims-migration-id).
1. Adobe Collabora con il tuo rappresentante/Assistenza clienti per proteggere una data entro la quale Adobe potrà eseguire la migrazione automatizzata per gli utenti non tecnici (operatori) e i profili di prodotto. Questo passaggio richiede una finestra temporale senza tempi di inattività per nessuno dei servizi.
1. L’amministratore di Campaign interno convalida queste modifiche e fornisce l’approvazione. Dopo questa migrazione, non sarà più necessario creare alcun operatore che effettui l’autenticazione con il suo login e la sua password.

È inoltre possibile eseguire la migrazione degli operatori tecnici a Adobe Developer Console come descritto in [questa nota tecnica](ims-migration.md).

Al termine della migrazione, conferma su Adobe Transition Manager (per gli utenti di Managed Services) o su Adobe Customer Care (per i clienti in hosting). Adobe contrassegna quindi la migrazione come completata. L’ambiente viene quindi protetto e standardizzato.


## Come si esegue la migrazione degli ambienti ibridi e on-premise? {#ims-migration-procedure-on-prem}

I passaggi chiave per questa migrazione sono elencati di seguito:

1. Aggiorna gli ambienti a Campaign v7.4.1 (o a una versione compatibile con [IMS](#ims-versions)).
1. Dopo l’aggiornamento, è comunque possibile creare nuovi utenti con entrambi i metodi, come utente nativo o con IMS.
1. L&#39;amministratore interno di Campaign deve configurare Adobe IMS come descritto in [questa sezione](../../integrations/using/configuring-ims.md).
1. Quindi aggiungi e-mail univoche a tutti gli utenti nativi nella console client di Campaign. Questo passaggio è descritto in [questa sezione](#ims-migration-id).
1. Crea utenti e profili di prodotto in Adobe Admin Console come descritto nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. Abilita l&#39;opzione **Connetti con Adobe ID** per tutti gli operatori.
1. Implementa Adobe IMS per la tua connessione come descritto in [questa pagina](../../integrations/using/implementing-ims.md).

È inoltre possibile eseguire la migrazione degli operatori tecnici a Adobe Developer Console come descritto in [questa nota tecnica](ims-migration.md).


## Domande frequenti {#ims-migration-faq}

### Come creare gli utenti dopo la migrazione? {#ims-migration-native}

Adobe consiglia di creare solo utenti IMS dopo l&#39;aggiornamento a Campaign Classic v7.4.1 (o a una versione [compatibile con la migrazione IMS](#ims-versions)).
A partire da Campaign v7.4.1, puoi impedire la creazione di operatori nativi aggiornando la configurazione dell&#39;istanza come descritto in [questa pagina](impact-ims-migration.md).

In qualità di amministratore di Campaign, puoi concedere autorizzazioni agli utenti della tua organizzazione tramite Adobe Admin Console e la console client di Campaign. Gli utenti accedono ad Adobe Campaign con il proprio Adobe ID. Scopri come impostare le autorizzazioni con IMS nella [documentazione di Campaign v8](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=it){target="_blank"}.

### Come si aggiungono le e-mail per gli utenti nativi attuali? {#ims-migration-id}

In qualità di amministratore di Campaign, devi aggiungere gli ID e-mail a tutti gli utenti nativi dalla console client. A tale scopo, segui i passaggi indicati di seguito:

1. Connettersi alla console client e passare a **Amministrazione > Gestione degli accessi > Operatori**.
1. Selezionare l&#39;operatore da aggiornare nell&#39;elenco degli operatori.
1. Immetti l&#39;e-mail dell&#39;operatore nella sezione **Punti di contatto** del modulo dell&#39;operatore.
1. Salva le modifiche.

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### Come effettuare l’accesso a Campaign tramite IMS? {#ims-migration-log}

Scopri come connetterti a Campaign con il tuo Adobe ID in [questa sezione](../../integrations/using/implementing-ims.md).

### Durante questa migrazione si verificherà un tempo di inattività? {#ims-migration-downtime}

Per i clienti in hosting e Managed Services, per finalizzare la migrazione (migrazione di utenti e profili di prodotto), Adobe richiede una finestra di un’ora senza tempi di inattività per nessuna delle istanze (flussi di lavoro, ecc.).

Durante questo arco temporale, tutti gli utenti di Campaign devono disconnettersi e tornare con il proprio Adobe ID una volta completata la migrazione a IMS.

Adobe consiglia vivamente di disconnettersi da tutti gli utenti durante la finestra di migrazione.

### Gli utenti della mia organizzazione utilizzano già IMS: devo ancora eseguire la migrazione IMS?{#ims-migration-needed}

Questa migrazione presenta due aspetti: migrazione degli utenti finali (più profili di prodotto) e migrazione degli utenti tecnici (utilizzata nelle API nel codice personalizzato).

Adobe Se tutti gli utenti (operatori di Campaign) utilizzano IMS, dovrai comunque contattare il rappresentante/supporto clienti per pianificare la migrazione dei profili di prodotto. Sarà inoltre necessario eseguire la migrazione degli utenti tecnici eventualmente utilizzati nel codice personalizzato. Per ulteriori informazioni, consulta [questa pagina](ims-migration.md).

### Come si visualizza il tipo di autenticazione degli operatori?

Scopri come visualizzare il tipo di autenticazione degli operatori in Campaign:

1. Da **Explorer**, accedere a **Administration** `>` **Access Management** `>` **Operators**.

1. Fare clic con il pulsante destro del mouse sulla riga di intestazione e selezionare il menu **Configura elenco**.

   ![](assets/ims_2.png)

1. Aggiungi **Account disabilitato** e **Tipo di autenticazione** come **Colonne di output**.

   ![](assets/ims_1.png)

Ora puoi visualizzare l&#39;elenco dei tuoi **operatori** e il relativo **tipo di autenticazione**.

![](assets/ims_3.png)


>[!MORELIKETHIS]
>
>* [Migrazione degli utenti tecnici alla console Adobe Developer](ims-migration.md)
>* [Note sulla versione di Adobe Campaign Classic v7](../../rn/using/latest-release.md)
>* [Che cos&#39;è Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}
