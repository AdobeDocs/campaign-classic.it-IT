---
product: campaign
title: Account esterni
description: Scopri come creare account esterni
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: 4a17d5e8-c73f-42e7-b641-0fee6a52c5c0
source-git-commit: 4a41aea9edfe5e6ca0454049cbb2892449eec153
workflow-type: tm+mt
source-wordcount: '1540'
ht-degree: 8%

---

# Account esterni{#external-accounts}

Adobe Campaign è dotato di un set di account esterni predefiniti. Per impostare connessioni con sistemi esterni, puoi creare nuovi account esterni.

Gli account esterni sono utilizzati da processi tecnici quali flussi di lavoro tecnici o flussi di lavoro per campagne. Ad esempio, quando imposti un trasferimento di file in un flusso di lavoro o uno scambio di dati con un’altra applicazione (Adobe Target, Experience Manager, ecc.), devi selezionare un account esterno.

## Creare un account esterno {#creating-an-external-account}

Per creare un nuovo account esterno, effettua le seguenti operazioni. Le impostazioni dettagliate dipendono dal tipo di account esterno.

1. Dalla campagna **[!UICONTROL Explorer]**, seleziona **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

   ![](assets/ext_account_1.png)

1. Fai clic sul pulsante **[!UICONTROL New]**.

   ![](assets/ext_account_2.png)

1. Immetti un **[!UICONTROL Label]** e un **[!UICONTROL Internal Name]**.
1. Seleziona il tuo account esterno **[!UICONTROL Type]** che desideri creare.
1. Configura l’accesso all’account specificando le credenziali in base al tipo di account esterno scelto.

   Le informazioni necessarie vengono in genere fornite dal provider del server a cui ti stai connettendo.

1. Seleziona l’opzione **[!UICONTROL Enabled]** per attivare la connessione.
1. Fai clic su **[!UICONTROL Save]**.

L’account esterno viene creato e aggiunto all’elenco degli account esterni.

## Account esterni specifici per la campagna

### Messaggi non recapitati {#bounce-mails-external-account}

L&#39;account esterno **Bounce mails** specifica l&#39;account POP3 esterno da utilizzare per la connessione al servizio e-mail. Per ulteriori informazioni su questo account esterno, consulta questa [pagina](../../workflow/using/inbound-emails.md).

Tutti i server configurati per l&#39;accesso POP3 possono essere utilizzati per ricevere la posta di ritorno.

![](assets/ext_account_6.png)

Per configurare l’account esterno **[!UICONTROL Bounce mails (defaultPopAccount)]**:

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

### Indirizzamento{#routing-external-account}

L’account esterno **[!UICONTROL Routing]** ti consente di configurare ogni canale disponibile in Adobe Campaign in base ai pacchetti installati.

![](assets/ext_account_7.png)

È possibile configurare i seguenti canali:

* [E-mail](../../installation/using/deploying-an-instance.md#email-channel-parameters)
* [Dispositivo mobile (SMS)](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account)
* [Telefono](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Direct mailing](../../delivery/using/about-direct-mail-channel.md)
* [Agenzia](../../delivery/using/steps-about-delivery-creation-steps.md#other-channels)
* [Facebook](../../social/using/publishing-on-facebook-walls.md#delegating-write-access-to-adobe-campaign)
* [Twitter](../../social/using/configuring-publishing-on-twitter.md)
* [Canale iOS](../../delivery/using/configuring-the-mobile-application.md)
* [Canale Android](../../delivery/using/configuring-the-mobile-application-android.md)


### Istanza di esecuzione {#execution-instance-external-account}

Se si dispone di un’architettura suddivisa, è necessario specificare le istanze di esecuzione collegate all’istanza di controllo e collegarle. I modelli di messaggio transazionali vengono distribuiti nell’istanza di esecuzione

![](assets/ext_account_13.png)

* **[!UICONTROL URL]**

   URL del server in cui è installata l’istanza di esecuzione.

* **[!UICONTROL Account]**

   Nome dell&#39;account, deve corrispondere all&#39;agente del centro messaggi come definito nella cartella dell&#39;operatore.

* **[!UICONTROL Password]**

   Password dell’account definita nella cartella dell’operatore.

Per ulteriori informazioni su questa configurazione, consulta questa [pagina](../../message-center/using/configuring-instances.md#control-instance).


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

Per sapere dove individuare queste credenziali, consulta questa [pagina](https://help.dreamhost.com/hc/en-us/articles/115000675027-FTP-overview-and-credentials).

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

### Database esterno (FDA) {#external-database-external-account}

Utilizza il tipo di account esterno **Database esterno** per connettersi a un database esterno. Ulteriori informazioni sull&#39;opzione Federated Data Access (FDA) in [questa sezione](../../installation/using/about-fda.md).

I database esterni compatibili con Campaign sono elencati nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md)

![](assets/ext_account_11.png)

Le impostazioni di configurazione dell’account esterno dipendono dal motore di database. Ulteriori informazioni nelle sezioni seguenti:

* Configura l&#39;accesso a [Azure synapse](../../installation/using/configure-fda-synapse.md)
* Configura l&#39;accesso a [Hadoop](../../installation/using/configure-fda-hadoop.md)
* Configura l&#39;accesso a [Oracle](../../installation/using/configure-fda-oracle.md)
* Configura l&#39;accesso a [Netezza](../../installation/using/configure-fda-netezza.md)
* Configurare l&#39;accesso a [SAP HANA](../../installation/using/configure-fda-sap-hana.md)
* Configura l&#39;accesso a [Snowflake](../../installation/using/configure-fda-snowflake.md)
* Configura l&#39;accesso a [Sybase IQ](../../installation/using/configure-fda-sybase.md)
* Configura l&#39;accesso a [Teradata](../../installation/using/configure-fda-teradata.md)

### Connessione facebook {#facebook-connect-external-account}

L’ account esterno **[!UICONTROL Facebook Connect]** consente di visualizzare contenuti personalizzati nelle applicazioni Facebook, facilitando l’acquisizione di potenziali clienti tramite questo social network.

Per ogni applicazione Facebook, devi creare un account esterno di tipo **[!UICONTROL Facebook Connect]**. Per ulteriori informazioni, consulta [page](../../social/using/creating-a-facebook-application.md#configuring-external-accounts).

![](assets/ext_account_12.png)

* **[!UICONTROL Hosting mode]**

   Modalità di hosting dell&#39;applicazione tra **[!UICONTROL hosted by a partner]** o **[!UICONTROL hosted by this instance]**.

* **[!UICONTROL Application ID]**

   ID app della tua applicazione Facebook.

* **[!UICONTROL Application secret]**

   Segreto app dell’applicazione Facebook.

Se si sceglie l&#39;ospitato da questa modalità di istanza, l&#39;URL dell&#39;area di lavoro protetta deve essere incollato nel campo **Giochi web Facebook (https)** in Facebook

Per sapere dove individuare queste credenziali, consulta questa [pagina](https://developers.facebook.com/docs/facebook-login/access-tokens).

## Account esterni per l&#39;integrazione della soluzione Adobe

### Adobe Experience Cloud {#adobe-experience-cloud-external-account}

Per connetterti alla console Adobe Campaign utilizzando un account Adobe ID, devi configurare l’ account esterno **[!UICONTROL Adobe Experience Cloud (MAC)]** .

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

   ID della tua organizzazione IMS. Per trovare l’ID organizzazione, fai riferimento a [questa pagina](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/faq.html) (**Dove posso trovare il mio ID organizzazione IMS?**).

* **[!UICONTROL Association mask]**

   Sintassi che consentirà la sincronizzazione dei nomi di configurazione in Enterprise Dashboard con i gruppi in Adobe Campaign.

* **[!UICONTROL Server]**

   URL dell’istanza Adobe Experience Cloud.

* **[!UICONTROL Tenant]**

   Nome del tenant Adobe Experience Cloud.

Per ulteriori informazioni su questa configurazione, consulta [questa pagina](../../integrations/using/configuring-ims.md).

## Analisi web {#web-analytics-external-account}

L’ account esterno **[!UICONTROL Web Analytics]** ti consente di inoltrare i dati da Adobe Analytics ad Adobe Campaign sotto forma di segmenti. Al contrario, invia indicatori e attributi delle campagne e-mail consegnate da Adobe Campaign al connettore Adobe Analytics.

![](assets/ext_account_10.png)

Per questo account esterno, la formula di calcolo per gli URL tracciati deve essere arricchita e la connessione tra le due soluzioni deve essere approvata. Per ulteriori informazioni, consulta questa [pagina](../../platform/using/adobe-analytics-connector.md#external-account-classic).

### Adobe Experience Manager {#adobe-experience-manager-external-account}

L’ account esterno **[!UICONTROL AEM (AEM instance)]** ti consente di gestire il contenuto delle consegne e-mail e dei moduli direttamente in Adobe Experience Manager.

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

L’account esterno **[!UICONTROL Microsoft Dynamics CRM]** ti consente di importare ed esportare dati di Microsoft Dynamics in Adobe Campaign.

Ulteriori informazioni su Campaign - Connettore Microsoft Dynamics CRM in questa [pagina](../../platform/using/crm-ms-dynamics.md).

>[!NOTE]
>
> **[!UICONTROL On-premise]** i tipi di  **[!UICONTROL Office 365]** distribuzione e sono ora obsoleti. [Ulteriori informazioni](../../rn/using/deprecated-features.md).

Con il tipo di distribuzione **[!UICONTROL Web API]** e l&#39;autenticazione **[!UICONTROL Password credentials]**, devi fornire i seguenti dettagli:

![](assets/ext_account_14.png)

* **[!UICONTROL Account]**

   Account utilizzato per accedere a Microsoft CRM.

* **[!UICONTROL Server]**

   URL del server Microsoft CRM in uso.

* **[!UICONTROL Client identifier]**

   ID client che si trova dal portale di gestione di Microsoft Azure nella categoria **[!UICONTROL Update your code]**, **[!UICONTROL Client ID]** campo .

* **[!UICONTROL CRM version]**

   Versione del CRM compresa tra **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** o **[!UICONTROL Dynamics CRM 2016]**.

Con il tipo di distribuzione **[!UICONTROL Web API]** e l&#39;autenticazione **[!UICONTROL Certificate]**, devi fornire i seguenti dettagli:

![](assets/ext_account_22.png)

* **[!UICONTROL Server]**

   URL del server Microsoft CRM in uso.

* **[!UICONTROL Private Key (Base64 encoded)]**

   Chiave privata codificata in Base64

* **[!UICONTROL Custom Key identifier]**

* **[!UICONTROL Key ID]**

* **[!UICONTROL Client identifier]**

   ID client che si trova dal portale di gestione di Microsoft Azure nella categoria **[!UICONTROL Update your code]**, **[!UICONTROL Client ID]** campo .

* **[!UICONTROL CRM version]**

   Versione del CRM compresa tra **[!UICONTROL Dynamics CRM 2007]**, **[!UICONTROL Dynamics CRM 2015]** o **[!UICONTROL Dynamics CRM 2016]**.

Per ulteriori informazioni su questa configurazione, consulta questa [pagina](../../platform/using/crm-connectors.md).

### CRM Salesforce.com {#salesforce-crm-external-account}

L’account esterno **[!UICONTROL Salesforce CRM]** ti consente di importare ed esportare dati Salesforce in Adobe Campaign.

![](assets/ext_account_17.png)

Per configurare l&#39;account esterno di gestione delle relazioni con i clienti Salesforce affinché funzioni con Adobe Campaign, devi fornire i seguenti dettagli:

* **[!UICONTROL Account]**

   Account utilizzato per accedere a CRM Salesforce.

* **[!UICONTROL Password]**

   Password utilizzata per accedere a CRM Salesforce.

* **[!UICONTROL Client identifier]**

   Per sapere dove trovare l&#39;identificatore client, consulta questa [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL Security token]**

   Per sapere dove trovare il token di sicurezza, consulta questa [pagina](https://help.salesforce.com/articleView?id=000205876&amp;type=1).

* **[!UICONTROL API version]**

   Seleziona la versione dell’API.

Per questo account esterno, devi configurare il tuo CRM Salesforce con la procedura guidata di configurazione.

Per ulteriori informazioni su questa configurazione, consulta questa [pagina](../../platform/using/crm-connectors.md).

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

   Per sapere dove trovare il tuo ID chiave di accesso AWS, fai riferimento a questa [pagina](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys) .

* **[!UICONTROL Secret access key to AWS]**

   Per sapere dove trovare la chiave di accesso segreto per AWS, consulta questa [pagina](https://aws.amazon.com/fr/blogs/security/wheres-my-secret-access-key/).

* **[!UICONTROL AWS Region]**

   Per ulteriori informazioni sull&#39;area geografica AWS, consulta questa [pagina](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/).

* La casella di controllo **[!UICONTROL Use server side encryption]** consente di memorizzare il file in modalità crittografata S3.

Per sapere dove trovare l&#39;ID chiave di accesso e la chiave di accesso segreto, consulta la documentazione di Amazon Web Services [](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

### Archiviazione BLOB di Azure (#azure-blob-external-account)

L&#39;account esterno **Azure Blob storage** può essere utilizzato per importare o esportare dati in Adobe Campaign utilizzando un&#39;attività del flusso di lavoro **[!UICONTROL Transfer file]**. Per ulteriori informazioni, consulta questa [sezione](../../workflow/using/file-transfer.md).

![](assets/ext_account_23.png)

Per configurare il **[!UICONTROL Azure external account]** in modo che funzioni con Adobe Campaign, devi fornire i seguenti dettagli:

* **[!UICONTROL Server]**

   URL del server di archiviazione BLOB di Azure.

* **[!UICONTROL Encryption]**

   Tipo di crittografia scelto tra **[!UICONTROL None]** o **[!UICONTROL SSL]**.

* **[!UICONTROL Access key]**

   Per sapere dove trovare il tuo **[!UICONTROL Access key]**, fai riferimento a questa [pagina](https://docs.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).
