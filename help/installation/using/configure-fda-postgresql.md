---
product: campaign
title: Configurare l’accesso a PostgreSQL
description: Scopri come configurare l’accesso a PostgreSQL
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 4%

---

# Configurare l’accesso a PostgreSQL {#configure-fda-postgresql}



Utilizzare Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database PostgreSQL esterno.

## Configurazione PostgreSQL {#postgresql-configuration}

Devi innanzitutto installare Libpq. Libpq consente ai programmi client di inviare query al server back-end PostgreSQL e di ricevere i risultati di tali query.

Segui i passaggi seguenti per configurare l’accesso a [!DNL PostgreSQL]:

* Per CentOS, esegui il seguente comando `sudo apt-get -y install libpq-dev`.

* Per Linux, eseguire il comando seguente `yum install postgresql-devel`.

* Per Windows, Libpq è implementato tramite `libpq.dll` incluso nell’installazione di Adobe Campaign.

In Adobe Campaign, puoi quindi configurare i [!DNL PostgreSQL] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#postgresql-external).

## Account esterno PostgreSQL {#postgresql-external}

>[!NOTE]
>
> PostgreSQL è disponibile su CentOS 7 e 6.

Devi creare un [!DNL PostgreSQL] account esterno per collegare la tua istanza Campaign al tuo [!DNL PostgreSQL] database esterno.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come dell’account esterno **[!UICONTROL Type]**.

1. Sotto **[!UICONTROL Configuration]**, seleziona [!DNL PostgreSQL, Greenplum] dal **[!UICONTROL Type]** a discesa.

   ![](assets/postgresql_1.png)

1. Configurare **[!UICONTROL PostgreSQL]** autenticazione account esterno:

   * **[!UICONTROL Server]**: URL del [!DNL PostgreSQL] server.

   * **[!UICONTROL Account]**: nome dell’utente.

   * **[!UICONTROL Password]**: password dell’account utente.

   * **[!UICONTROL Database]**: nome del database (facoltativo).

   * **[!UICONTROL Working schema]**: nome dello schema di lavoro. [Ulteriori informazioni](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**: fuso orario impostato in [!DNL PostgreSQL]. [Ulteriori informazioni](https://www.postgresql.org/docs/7.2/timezones.html)

1. Fai clic su **[!UICONTROL Parameters]** , quindi la scheda **[!UICONTROL Deploy functions]** per creare funzioni.

   >[!NOTE]
   >
   >Affinché tutte le funzioni siano disponibili, è necessario creare le funzioni SQL di Adobe Campaign nel database remoto. Per ulteriori informazioni, consulta questa [pagina](../../configuration/using/adding-additional-sql-functions.md).

1. Clic **[!UICONTROL Save]** al termine della configurazione.

Il connettore supporta le seguenti opzioni:

| Opzione | Descrizione |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | Attesa massima della connessione, in secondi. <br>Per ulteriori informazioni, consulta [Documentazione di PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | Numero di secondi di inattività dopo i quali il TCP deve inviare un messaggio keepalive al server. <br>Per ulteriori informazioni, consulta [Documentazione di PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | Numero di secondi dopo i quali deve essere ritrasmesso il messaggio TCP keepalive non riconosciuto dal server.  <br>Per ulteriori informazioni, consulta [Documentazione di PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | Numero di chiavi TCP che possono essere perse prima che la connessione del client al server venga considerata inattiva. <br>Per ulteriori informazioni, consulta [Documentazione di PostgreSQL](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
