---
product: campaign
title: Configurare l’accesso a PostgreSQL
description: Scopri come configurare l’accesso a PostgreSQL
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---

# Configurare l’accesso a PostgreSQL {#configure-fda-postgresql}



Utilizza l&#39;opzione **Federated Data Access** (FDA) di Campaign per elaborare le informazioni archiviate in un database PostgreSQL esterno.

## Configurazione PostgreSQL {#postgresql-configuration}

Devi innanzitutto installare Libpq. Libpq consente ai programmi client di inviare query al server back-end PostgreSQL e di ricevere i risultati di tali query.

Per configurare l&#39;accesso a [!DNL PostgreSQL], eseguire la procedura seguente:

* Per CentOS, eseguire il comando seguente `sudo apt-get -y install libpq-dev`.

* Per Linux, eseguire il comando seguente `yum install postgresql-devel`.

* Per Windows, Libpq è implementato tramite `libpq.dll` incluso nell&#39;installazione di Adobe Campaign.

In Adobe Campaign, puoi quindi configurare l&#39;account esterno [!DNL PostgreSQL]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#postgresql-external).

## Account esterno PostgreSQL {#postgresql-external}

>[!NOTE]
>
> PostgreSQL è disponibile su CentOS 7 e 6.

È necessario creare un account esterno [!DNL PostgreSQL] per collegare l&#39;istanza Campaign al database esterno [!DNL PostgreSQL].

1. Dalla campagna **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come **[!UICONTROL Type]** del tuo account esterno.

1. In **[!UICONTROL Configuration]**, selezionare [!DNL PostgreSQL, Greenplum] dal menu a discesa **[!UICONTROL Type]**.

   ![](assets/postgresql_1.png)

1. Configurare l&#39;autenticazione dell&#39;account esterno **[!UICONTROL PostgreSQL]**:

   * **[!UICONTROL Server]**: URL del server [!DNL PostgreSQL].

   * **[!UICONTROL Account]**: nome dell&#39;utente.

   * **[!UICONTROL Password]**: password account utente.

   * **[!UICONTROL Database]**: nome del database (facoltativo).

   * **[!UICONTROL Working schema]**: nome dello schema di lavoro. [Ulteriori informazioni](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: Fuso orario impostato in [!DNL PostgreSQL]. [Ulteriori informazioni](https://www.postgresql.org/docs/7.2/timezones.html)

1. Fare clic sulla scheda **[!UICONTROL Parameters]** e quindi sul pulsante **[!UICONTROL Deploy functions]** per creare le funzioni.

   >[!NOTE]
   >
   >Affinché tutte le funzioni siano disponibili, è necessario creare le funzioni SQL di Adobe Campaign nel database remoto. Per ulteriori informazioni, consulta questa [pagina](../../configuration/using/adding-additional-sql-functions.md).

1. Al termine della configurazione, fai clic su **[!UICONTROL Save]**.

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Attesa massima della connessione, in secondi. <br>Per ulteriori informazioni, consulta la [documentazione PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Numero di secondi di inattività dopo i quali il TCP deve inviare un messaggio keepalive al server. <br>Per ulteriori informazioni, consulta la [documentazione PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Numero di secondi dopo i quali deve essere ritrasmesso il messaggio TCP keepalive non riconosciuto dal server.  <br>Per ulteriori informazioni, consulta la [documentazione PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Numero di chiavi TCP che possono essere perse prima che la connessione del client al server venga considerata inattiva. <br>Per ulteriori informazioni, consulta la [documentazione PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
