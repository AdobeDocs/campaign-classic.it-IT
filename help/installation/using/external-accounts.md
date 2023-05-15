---
product: campaign
title: Account esterni
description: Scopri come creare account esterni
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1714'
ht-degree: 9%

---

# Account esterni{#external-accounts}



Adobe Campaign è dotato di un set di account esterni predefiniti. Per impostare connessioni con sistemi esterni, puoi creare nuovi account esterni.

Gli account esterni sono utilizzati da processi tecnici quali flussi di lavoro tecnici o flussi di lavoro per campagne. Ad esempio, quando imposti un trasferimento di file in un flusso di lavoro o uno scambio di dati con un’altra applicazione (Adobe Target, Experience Manager, ecc.), devi selezionare un account esterno.

## Creare un account esterno {#creating-an-external-account}

Per creare un nuovo account esterno, effettua le seguenti operazioni. Le impostazioni dettagliate dipendono dal tipo di account esterno.

1. Da campagna **[!UICONTROL Explorer]**, seleziona **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Fai clic sul pulsante **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Inserisci un **[!UICONTROL Label]** e **[!UICONTROL Internal Name]**.
1. Seleziona l’account esterno **[!UICONTROL Type]** quale desideri creare.
1. Configura l’accesso all’account specificando le credenziali in base al tipo di account esterno scelto.

   Le informazioni necessarie vengono in genere fornite dal provider del server a cui ti stai connettendo.

1. Controlla la **[!UICONTROL Enabled]** per attivare la connessione.
1. Fai clic su **[!UICONTROL Save]**.

L’account esterno viene creato e aggiunto all’elenco degli account esterni.

## Account esterni specifici per la campagna

### Messaggi non recapitati {#bounce-mails-external-account}

La **Messaggi non recapitati** account esterno specifica l’account POP3 esterno da utilizzare per connettersi al servizio e-mail. Per ulteriori informazioni su questo account esterno, consulta questo [page](../../workflow/using/inbound-emails.md).

Tutti i server configurati per l&#39;accesso POP3 possono essere utilizzati per ricevere la posta di ritorno.

![](assets/ext_account_6.png)

Per configurare le **[!UICONTROL Bounce mails (defaultPopAccount)]** account esterno:

* **[!UICONTROL Server]**

   URL del server POP3.

* **[!UICONTROL Port]**

   Numero della porta di connessione POP3. La porta predefinita è 110.

* **[!UICONTROL Account]**

   Nome dell&#39;utente.

* **[!UICONTROL Password]**

   Password dell&#39;account utente.

* **[!UICONTROL Encryption]**

   Tipo di crittografia scelto tra **[!UICONTROL By default]**, **[!UICONTROL POP3 + STARTTLS]**, **[!UICONTROL POP3]** o **[!UICONTROL POP3S]**.

* **[!UICONTROL Function]**

   Router e-mail o SOAP in entrata

>[!IMPORTANT]
>
>Prima di configurare l’account esterno POP3 utilizzando Microsoft OAuth 2.0, è necessario registrare l’applicazione nel portale di Azure. Per ulteriori informazioni, consulta [questa pagina](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app).

Per configurare un POP3 esterno utilizzando **Microsoft OAuth 2.0**, controlla **[!UICONTROL Microsoft OAuth 2.0]** e compila i campi seguenti:

* **[!UICONTROL Azure tenant]**

   L&#39;ID di Azure (o ID di directory (tenant)) si trova nella **Elementi essenziali** panoramica dell’applicazione nel portale di Azure.

* **[!UICONTROL Azure Client ID]**

   L&#39;ID client (o l&#39;ID applicazione (client)) si trova nella **Elementi essenziali** panoramica dell’applicazione nel portale di Azure.

* **[!UICONTROL Azure Client secret]**

   L&#39;ID segreto client si trova nella **Segmenti client** dalla colonna **Certificati e segreti** menu dell’applicazione nel portale di Azure.

* **[!UICONTROL Azure Redirect URL]**

   L’URL di reindirizzamento si trova nella sezione **Autenticazione** menu dell’applicazione nel portale di Azure. Deve terminare con la seguente sintassi `nl/jsp/oauth.jsp`ad esempio `https://redirect.adobe.net/nl/jsp/oauth.jsp`.

Dopo aver immesso le diverse credenziali, puoi fare clic su **[!UICONTROL Setup the connection]** per completare la configurazione dell’account esterno.

### Indirizzamento{#routing-external-account}

La **[!UICONTROL Routing]** l’account esterno ti consente di configurare ogni canale disponibile in Adobe Campaign in base ai pacchetti installati.

![](assets/ext_account_7.png)

È possibile configurare i seguenti canali:

* [E-mail](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Dispositivo mobile (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefono](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Direct mail](../../delivery/using/about-direct-mail-channel.md)
* [Agenzia](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Twitter](../../social/using/about-social-marketing.md)
* [Canale iOS](../../delivery/using/configuring-the-mobile-application.md)
* [Canale Android](../../delivery/using/configuring-the-mobile-application-android.md)

### Istanza di esecuzione  {#execution-instance-external-account}

Se si dispone di un’architettura suddivisa, è necessario specificare le istanze di esecuzione collegate all’istanza di controllo e collegarle. I modelli di messaggio transazionali vengono distribuiti nell’istanza di esecuzione

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL del server in cui è installata l’istanza di esecuzione.

* **[!UICONTROL Account]**

   Nome dell&#39;account, deve corrispondere all&#39;agente del centro messaggi come definito nella cartella dell&#39;operatore.

* **[!UICONTROL Password]**

   Password dell’account definita nella cartella dell’operatore.

Per ulteriori informazioni su questa configurazione, consulta questo [page](../../message-center/using/configuring-instances.md#control-instance).

## Accesso agli account esterni dei sistemi esterni

### FTP {#ftp-external-account}

L&#39;account esterno FTP ti consente di configurare e testare l&#39;accesso a un server esterno ad Adobe Campaign. Per impostare connessioni con sistemi esterni come i server FTP 898 utilizzati per i trasferimenti di file, puoi creare account esterni personalizzati. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/file-transfer.md).

Per farlo, specifica in questo account esterno l&#39;indirizzo e le credenziali utilizzati per stabilire la connessione al server FTP

![](assets/ext_account_8.png)

* **[!UICONTROL Server]**

   Nome del server FTP.

* **[!UICONTROL Port]**

   Numero di porta di connessione FTP. La porta predefinita è 21.

* **[!UICONTROL Account]**

   Nome dell&#39;utente.

* **[!UICONTROL Password]**

   Password dell&#39;account utente.

* **[!UICONTROL Encryption]**

   Tipo di crittografia scelto tra **[!UICONTROL None]** o **[!UICONTROL SSL]**.

Per sapere dove individuare queste credenziali, consulta questo [page](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

### SFTP {#sftp-external-account}

L’account esterno SFTP ti consente di configurare e testare l’accesso a un server esterno ad Adobe Campaign. Per impostare connessioni con sistemi esterni come SFTP utilizzati per i trasferimenti di file, puoi creare account esterni personalizzati. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/file-transfer.md).

![](assets/ext_account_4.png)

* **[!UICONTROL Server]**

   URL del server SFTP.

* **[!UICONTROL Port]**

   Numero di porta di connessione FTP. La porta predefinita è 22.

* **[!UICONTROL Account]**

   Nome account utilizzato per la connessione al server SFTP.

* **[!UICONTROL Password]**

   Password utilizzata per la connessione al server SFTP.

Per aggiungere chiavi SSH in Windows:

1. Crea il **HOME** variabile di ambiente con valore impostato come directory di installazione.

2. Aggiungi la tua chiave privata al `/$HOME/.ssh/id_rsa` cartella.

3. Riavvia i servizi Adobe Campaign.

### Database esterno (FDA) {#external-database-external-account}

Utilizza la **Database esterno** digitare account esterno per la connessione a un database esterno. Ulteriori informazioni sull’opzione Federated Data Access (FDA) in [questa sezione](../../installation/using/about-fda.md).

I database esterni compatibili con Campaign sono elencati in [Matrice di compatibilità](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Le impostazioni di configurazione dell’account esterno dipendono dal motore di database. Ulteriori informazioni nelle sezioni seguenti:

* Configurare l’accesso a [vertiche analytics](../../installation/using/configure-fda-vertica.md)
* Configurare l’accesso a [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configurare l’accesso a [BigQuery Google](../../installation/using/configure-fda-google-big-query.md)
* Configurare l’accesso a [azure synapse](../../installation/using/configure-fda-synapse.md)
* Configurare l’accesso a [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Configurare l’accesso a [Oracle](../../installation/using/configure-fda-oracle.md)
* Configurare l’accesso a [Netezza](../../installation/using/configure-fda-netezza.md)
* Configurare l’accesso a [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Configurare l’accesso a [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configurare l’accesso a [sybase IQ](../../installation/using/configure-fda-sybase.md)
* Configurare l’accesso a [Teradata](../../installation/using/configure-fda-teradata.md)


## Account esterni per l&#39;integrazione della soluzione Adobe

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Per connetterti alla console Adobe Campaign utilizzando un’Adobe ID, devi configurare l’ **[!UICONTROL Adobe Experience Cloud (MAC)]** conto esterno.

![](assets/ext_account_9.png)

* **[!UICONTROL IMS server]**

   URL del server IMS. Assicurati che entrambe le istanze di stage e produzione puntino allo stesso punto finale di produzione IMS.

* **[!UICONTROL IMS scope]**

   Gli ambiti qui definiti devono essere un sottoinsieme di quelli forniti da IMS.

* **[!UICONTROL IMS client identifier]**

   ID del client IMS.

* **[!UICONTROL IMS client secret]**

   Credenziale del segreto client IMS.

* **[!UICONTROL Callback server]**

   Accedi all’URL della tua istanza Adobe Campaign.

* **[!UICONTROL IMS organization ID]**

   ID della tua organizzazione. Per trovare l&#39;ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=it){_blank}.

* **[!UICONTROL Association mask]**

   Sintassi che consentirà la sincronizzazione dei nomi di configurazione in Enterprise Dashboard con i gruppi in Adobe Campaign.

* **[!UICONTROL Server]**

   URL dell’istanza Adobe Experience Cloud.

* **[!UICONTROL Tenant]**

   Nome del tenant Adobe Experience Cloud.

Per ulteriori informazioni su questa configurazione, consulta [questa pagina](../../integrations/using/configuring-ims.md).

## Analisi web {#web-analytics-external-account}

La **[!UICONTROL Web Analytics]** l’account esterno ti consente di inoltrare dati da Adobe Analytics ad Adobe Campaign sotto forma di segmenti. Al contrario, invia indicatori e attributi delle campagne e-mail consegnate da Adobe Campaign al connettore Adobe Analytics.

![](assets/ext_account_10.png)

Per questo account esterno, la formula di calcolo per gli URL tracciati deve essere arricchita e la connessione tra le due soluzioni deve essere approvata. Per ulteriori informazioni, consulta questa [pagina](../../platform/using/adobe-analytics-connector.md#external-account-classic).

### Adobe Experience Manager {#adobe-experience-manager-external-account}

La **[!UICONTROL AEM (AEM instance)]** l’account esterno ti consente di gestire il contenuto delle consegne e-mail e dei moduli direttamente in Adobe Experience Manager.

![](assets/ext_account_5.png)

* **[!UICONTROL Server]**

   URL del server Adobe Experience Manager.

* **[!UICONTROL Port]**

   Nome account utilizzato per connettersi all’istanza di authoring di Adobe Experience Manager.

* **[!UICONTROL Password]**

   Password utilizzata per connettersi all’istanza di authoring di Adobe Experience Manager.

Per ulteriori informazioni, consulta questa [sezione](../../integrations/using/about-adobe-experience-manager.md).

## Account esterni del connettore di gestione delle relazioni con i clienti

### Microsoft Dynamics CRM {#microsoft-dynamics-crm-external-account}

>[!NOTE]
>
> **[!UICONTROL On-premise]** e **[!UICONTROL Office 365]** i tipi di distribuzione sono ora obsoleti. [Ulteriori informazioni](../../rn/using/deprecated-features.md).

La **[!UICONTROL Microsoft Dynamics CRM]** l’account esterno ti consente di importare ed esportare dati di Microsoft Dynamics in Adobe Campaign.

Ulteriori informazioni su Campaign - Connettore Microsoft Dynamics CRM in questo [page](../../platform/using/crm-ms-dynamics.md).

Con **[!UICONTROL Web API]** tipo di distribuzione e **[!UICONTROL Password credentials]** autenticazione, devi fornire i seguenti dettagli:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Account utilizzato per accedere a Microsoft CRM.

* **[!UICONTROL Server]**

   URL del server Microsoft CRM.

   Per trovare il tuo Microsoft CRM **[!UICONTROL Server URL]**, accedi al tuo account Microsoft Dynamics CRM e fai clic su **Dynamics 365** e seleziona la tua app. È quindi possibile trovare il **[!UICONTROL Server URL]** nella barra degli indirizzi del browser, ad esempio `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Client identifier]**

   ID client che è possibile trovare dal portale di gestione di Microsoft Azure in **[!UICONTROL Update your code]** categoria, **[!UICONTROL Client ID]** campo .

* **[!UICONTROL CRM version]**

   Scegli **[!UICONTROL Dynamics CRM 365]** Versione CRM.

Con **[!UICONTROL Web API]** tipo di distribuzione e **[!UICONTROL Certificate]** autenticazione, devi fornire i seguenti dettagli:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL del server Microsoft CRM.

   Per trovare il tuo Microsoft CRM **[!UICONTROL Server URL]**, accedi al tuo account Microsoft Dynamics CRM e fai clic su **Dynamics 365** e seleziona la tua app. È quindi possibile trovare il **[!UICONTROL Server URL]** nella barra degli indirizzi del browser, ad esempio `https://myserver.crm.dynamics.com/`.

* **[!UICONTROL Private Key (Base64 encoded)]**

   La chiave privata deve essere codificata in Base64.

   Per farlo, puoi utilizzare l&#39;aiuto di un encoder Base64 o la riga di comando `base64 -w0 private.key` per Linux.

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   ID client che è possibile trovare dal portale di gestione di Microsoft Azure in **[!UICONTROL Update your code]** categoria, **[!UICONTROL Client ID]** campo .

* **[!UICONTROL CRM version]**

   Versione del CRM tra **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** o **[!UICONTROL Dynamics CRM 2016]**.

Per ulteriori informazioni su questa configurazione, consulta questo [page](../../platform/using/crm-connectors.md).

### CRM Salesforce.com  {#salesforce-crm-external-account}

La **[!UICONTROL Salesforce CRM]** l’account esterno ti consente di importare ed esportare dati Salesforce in Adobe Campaign.

![](assets/ext_account_17.png)

Per configurare l&#39;account esterno di gestione delle relazioni con i clienti Salesforce affinché funzioni con Adobe Campaign, devi fornire i seguenti dettagli:

* **[!UICONTROL Account]**

   Account utilizzato per accedere a CRM Salesforce.

* **[!UICONTROL Password]**

   Password utilizzata per accedere a CRM Salesforce.

* **[!UICONTROL Client identifier]**

   Per sapere dove trovare l’identificatore client, consulta questo [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Per sapere dove trovare il token di sicurezza, consulta questo [page](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Seleziona la versione dell’API.

Per questo account esterno, devi configurare il tuo CRM Salesforce con la procedura guidata di configurazione.

Per ulteriori informazioni su questa configurazione, consulta questo [page](../../platform/using/crm-connectors.md).

## Trasferisci account esterni dati

### Servizio di archiviazione semplice Amazon (S3) {#amazon-simple-storage-service--s3--external-account}

Il connettore Amazon Simple Storage Service (S3) può essere utilizzato per importare o esportare dati in Adobe Campaign. Può essere configurato in un’attività del flusso di lavoro. Per ulteriori informazioni, consulta questa [pagina](../../workflow/using/file-transfer.md).

![](assets/ext_account_3.png)

Quando imposti questo nuovo account esterno, dovrai fornire i seguenti dettagli:

* **[!UICONTROL AWS S3 Account Server]**

   URL del server, deve essere compilato come segue:

   ```
   <S3bucket name>.s3.amazonaws.com/<s3object path>
   ```

* **[!UICONTROL AWS access key ID]**

   Per sapere dove trovare il tuo ID chiave di accesso AWS, consulta questo [page](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

   Per sapere dove trovare la chiave di accesso segreto per AWS, consulta questo [page](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Per ulteriori informazioni sull’area geografica di AWS, consulta questo articolo [page](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* La **[!UICONTROL Use server side encryption]** casella di controllo consente di memorizzare il file in modalità crittografata S3.

Per sapere dove trovare l’ID chiave di accesso e la chiave di accesso segreto, consulta Servizi Web Amazon [documentazione](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Archiviazione BLOB di Azure {#azure-blob-external-account}

La **Archiviazione BLOB di Azure** l’account esterno può essere utilizzato per importare o esportare dati in Adobe Campaign utilizzando un **[!UICONTROL Transfer file]** attività del flusso di lavoro. Per ulteriori informazioni, consulta questa [sezione](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Per configurare le **[!UICONTROL Azure external account]** per lavorare con Adobe Campaign, devi fornire i seguenti dettagli:

* **[!UICONTROL Server]**

   URL del server di archiviazione BLOB di Azure.

* **[!UICONTROL Encryption]**

   Tipo di crittografia scelto tra **[!UICONTROL None]** o **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Per sapere dove trovare il tuo **[!UICONTROL Access key]**, fai riferimento a [page](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
