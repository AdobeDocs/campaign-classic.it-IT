---
title: Migrazione ad Adobe Identity Management System (IMS)
description: Scopri come migrare il processo di autenticazione ad Adobe Identity Management System (IMS)
exl-id: 84853dbe-8b6f-4875-b29a-c1b755423a3c
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# Migrazione ad Adobe Identity Management System (IMS) {#migrate-to-ims}

Per rafforzare la sicurezza e il processo di autenticazione, Adobe Campaign consiglia vivamente di migrare la modalità di autenticazione dell&#39;utente finale dall&#39;autenticazione nativa di login/password a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}.

Inoltre, l’applicazione client Adobe Campaign ora chiama le API di Campaign direttamente utilizzando il token dell’account tecnico IMS. È necessario eseguire la migrazione degli operatori tecnici a Adobe Developer Console.

>[!CAUTION]
>
>Questa modifica è già applicabile in Campaign Classic v7 e sarà **obbligatoria** per passare a Campaign v8. L’autenticazione nativa utente/password non è consentita in Campaign v8. **Adobe consiglia di eseguire questa migrazione a partire da Campaign v7.3.5 per eseguire senza problemi la migrazione a Campaign v8.**
>

## Passaggi di migrazione {#ims-steps}

La migrazione a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} è un imperativo di sicurezza per rendere gli ambienti sicuri e standardizzati, in quanto la maggior parte delle altre soluzioni e app Adobe Experience Cloud sono già in IMS.

Adobe ti supporta in questo sforzo di migrazione. Puoi trovare il contesto dettagliato e le linee guida dettagliate nei seguenti articoli:

* La migrazione per l&#39;autenticazione degli utenti finali è descritta in [questa pagina](migrate-users-to-ims.md).
* La migrazione per l&#39;autenticazione degli operatori tecnici è descritta in [questa pagina](ims-migration.md).
* A partire da Campaign v7.4.1, abilita l&#39;interfaccia utente e le restrizioni API per rimuovere le opzioni e le funzionalità specifiche dell&#39;autenticazione nativa, come descritto in [questa pagina](impact-ims-migration.md).


## Versioni compatibili con la migrazione IMS {#ims-versions}

Un prerequisito per questa migrazione è aggiornare l’ambiente a una delle seguenti versioni del prodotto:

* Campaign v7.4.1 (consigliato)
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

Queste versioni di Campaign sono descritte in dettaglio nelle [Note sulla versione](../../rn/using/latest-release.md).

## Domande frequenti {#ims-migration-faq}

### Quando posso avviare la migrazione? {#ims-migration-start}

Si consiglia di eseguire la migrazione a [Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} aggiornando l&#39;ambiente a Campaign Classic v7.4.1 (o a una versione [compatibile con la migrazione IMS](#ims-versions)).

È possibile avviare la migrazione IMS nell’ambiente di stage, una volta effettuato l’aggiornamento alla versione più recente, e pianificare di conseguenza l’ambiente di produzione.

### Cosa succede dopo l’aggiornamento della build a Campaign Classic v7.4.1? {#ims-migration-after-upgrade}

Dopo aver aggiornato gli ambienti a Campaign Classic v7.4.1 (o a una versione [compatibile con la migrazione IMS](#ims-versions)), puoi avviare la transizione a [Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"} di Adobe.

### Quando è stata completata la migrazione? {#ims-migration-end}

Una volta effettuata la migrazione degli utenti finali e degli operatori tecnici ad Adobe Identity Management System (IMS), è necessario aggiornare l’ambiente per rimuovere le opzioni specifiche dell’autenticazione nativa e non più applicabili con l’autenticazione IMS. Questo aggiornamento è disponibile solo a partire da Campaign v7.4.1. [Ulteriori informazioni](impact-ims-migration.md)



## Collegamenti utili {#ims-useful-links}

* [Migrazione degli utenti finali a IMS](migrate-users-to-ims.md)
* [Migrazione degli operatori tecnici alla console Adobe Developer](ims-migration.md)
* [Note sulla versione più recente di Adobe Campaign Classic v7](../../rn/using/latest-release.md)
* [Che cos&#39;è Adobe Identity Management System (IMS)](https://helpx.adobe.com/it/enterprise/using/users.html){target="_blank"}
