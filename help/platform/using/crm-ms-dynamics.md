---
product: campaign
title: Campaign - Connettore Microsoft Dynamics CRM
description: Scopri come collegare Campaign e Microsoft Dynamics
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 2%

---

# Connettere Campaign e Microsoft Dynamics 365{#connect-to-msdyn}



In questa pagina verrà illustrato come connettere Campaign Classic a **Microsoft Dynamics CRM 365**.

La possibile distribuzione avviene tramite **API Web** (scelta consigliata). Consulta [la sezione seguente](#microsoft-dynamics-implementation-step) per informazioni su come configurare la connessione con Microsoft Dynamics.

La sincronizzazione dei dati viene eseguita tramite un’attività del flusso di lavoro dedicata. [Ulteriori informazioni](../../platform/using/crm-data-sync.md).

## Passaggi di implementazione{#microsoft-dynamics-implementation-steps}

Per connettere Microsoft Dynamics 365 per lavorare con Adobe Campaign tramite **API Web**, è necessario attenersi alla seguente procedura:

In Microsoft Dynamics CRM:
1. Ottieni ID client Microsoft Dynamics
1. Genera ID chiave e identificatore chiave del certificato di Microsoft Dynamics
1. Configurare le autorizzazioni
1. Creare un utente dell’app
1. Codifica la chiave privata

[Ulteriori informazioni](#config-crm-microsoft)

In Campaign Classic:
1. Crea un nuovo account esterno
1. Configurare l’account esterno con le impostazioni di Microsoft Dynamics
1. Utilizzare la configurazione guidata per mappare tabelle e sincronizzare enumerazioni
1. Creare il flusso di lavoro di sincronizzazione

[Ulteriori informazioni](#configure-acc-for-microsoft)


>[!CAUTION]
> Quando si collega Adobe Campaign con Microsoft Dynamics, non è possibile:
> * Installa plug-in che possono modificare il comportamento del sistema CRM e causare problemi di compatibilità con Adobe Campaign
> * Seleziona più enumerazioni

## Configurare Microsoft Dynamics CRM {#config-crm-microsoft}

Per generare il token di accesso e le chiavi per configurare l&#39;account, è necessario accedere a [Microsoft Azure Directory](https://portal.azure.com) utilizzando le credenziali di **Global Administrator**. Quindi segui i passaggi descritti di seguito.

### Ottieni ID client Microsoft Dynamics {#get-client-id-microsoft}

Per ottenere l&#39;ID client, è necessario registrare un&#39;app in Azure Active Directory. L’ID client è uguale all’ID applicazione.

1. Passare a **Azure Active Directory > Registrazioni app** e fare clic su **Nuova registrazione applicazione**.
1. Assegna un nome univoco che possa aiutare a identificare un&#39;istanza, ad esempio **adobecampaign`<instance identifier>`**.
1. Scegliere **Tipo di applicazione** come **App Web / API**.
1. Utilizza `http://localhost` per **URL di accesso**.

Dopo il salvataggio, si ottiene un **ID applicazione** che è l&#39;identificatore client per Campaign.

Per ulteriori informazioni, consulta [questa pagina](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Genera ID chiave e identificatore chiave del certificato di Microsoft Dynamics {#config-certificate-key-id}

Per ottenere l&#39;**identificatore chiave del certificato (customKeyIdentifier)** e l&#39;**ID chiave (keyId)**, attenersi alla seguente procedura:

1. Passare a **Azure Active Directory > Registrazioni app** e selezionare l&#39;applicazione creata in precedenza.
1. Fai clic su **Certificati e segreto**.
1. Fai clic su **Carica certificato**, quindi sfoglia e carica il certificato pubblico generato.
1. Per generare il certificato è possibile utilizzare openssl.

   Ad esempio:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >È possibile modificare il numero di giorni, qui `-days 365`, nell&#39;esempio di codice per un periodo di validità del certificato più lungo.

1. Sarà quindi necessario codificarlo in base64. A tale scopo, è possibile utilizzare l&#39;aiuto di un codificatore Base64 o la riga di comando `base64 -w0 private.key` per Linux.

1. Fai clic sul collegamento **Manifest** per ottenere l&#39;**identificatore chiave del certificato (customKeyIdentifier)** e l&#39;**ID chiave (keyId)**.

L&#39;identificatore della chiave del certificato **(customKeyIdentifier)** e l&#39;ID della chiave **(keyId)** saranno necessari in seguito per configurare l&#39;account esterno di Microsoft Dynamics CRM utilizzando il certificato **[!UICONTROL CRM O-Auth type]**.

### Configurare le autorizzazioni {#config-permissions-microsoft}

**Passaggio 1**: configurare le **autorizzazioni richieste** per l&#39;app creata.

1. Passare a **Azure Active Directory > Registrazioni app** e selezionare l&#39;applicazione creata in precedenza.
1. Fai clic su **Impostazioni** in alto a sinistra.
1. In **Autorizzazioni richieste**, fare clic su **Aggiungi** e **Seleziona un&#39;API > Dynamics CRM Online**.
1. Fai clic su **Seleziona**, abilita **Access Dynamics 365 come utenti dell&#39;organizzazione**, seleziona la casella di controllo e fai clic su **Seleziona**.
1. Quindi, dall&#39;app, seleziona **Manifesto** nel menu **Gestisci**.

1. Dall&#39;editor **Manifest**, impostare la proprietà `allowPublicClient` da `null` a `true` e fare clic su **Salva**.

**Passaggio 2**: concedere il consenso dell&#39;amministratore

1. Passare a **Azure Active Directory > Applicazioni aziendali**.

1. Seleziona l’applicazione a cui desideri concedere il consenso dell’amministratore a livello di tenant.

1. Dal menu del riquadro a sinistra, selezionare **Autorizzazioni** in **Sicurezza**.

1. Fai clic su **Concedi il consenso dell&#39;amministratore**.

Per ulteriori informazioni, consulta [Documentazione di Azure](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Creare un utente dell’app {#create-app-user-microsoft}

>[!NOTE]
>
> Questo passaggio è facoltativo con autenticazione **[!UICONTROL Password credentials]**.

L’utente dell’app è l’utente che verrà utilizzato dall’applicazione registrata in precedenza. Eventuali modifiche apportate a Microsoft Dynamics utilizzando l’app registrata in precedenza verranno eseguite tramite questo utente.

**Passaggio 1**: creare un utente non interattivo in Azure Active Directory

1. Fare clic su **Azure Active Directory > Utenti** e quindi su **Nuovo utente**.
1. Assegna un nome appropriato che desideri utilizzare e il nome utente deve essere in formato e-mail.
1. Scegliere **Amministratore Dynamics 365** in **Ruolo directory**.

**Passaggio 2**: assegna una licenza corretta all&#39;utente creato

1. Da [Microsoft Azure](https://portal.azure.com), fare clic su **App amministratore**.
1. Vai a **Utenti > Utenti attivi** e fai clic sull&#39;utente appena creato.
1. Fai clic su **Modifica licenze prodotto** e seleziona il **Piano di coinvolgimento del cliente Dynamics 365**.
1. Fai clic su **Chiudi**.

**Passaggio 3**: creare un utente dell&#39;applicazione in Dynamics CRM

1. Da [Microsoft Azure](https://portal.azure.com), passare a **Impostazioni > Protezione > Utenti**.
1. Fai clic sull&#39;elenco a discesa, seleziona **Utenti applicazioni** e fai clic su **Nuovo**.
1. Utilizza lo stesso nome utente creato in Active Directory in precedenza

   >[!NOTE]
   >
   >Se si utilizza lo stesso nome, viene generato un errore di chiave duplicata; finché non viene confermato se questo passaggio è necessario, utilizza un nome utente diverso e procedi.
   >

1. Assegna **ID applicazione** per [l&#39;applicazione creata in precedenza](#get-client-id-microsoft).
1. Fai clic su **Gestisci ruoli** e scegli il ruolo **Amministratore di sistema** per l&#39;utente.

## Configurare Campaign {#configure-acc-for-microsoft}

>[!NOTE]
>
> Dopo la disattivazione di [RDS da Microsoft](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint), i tipi di distribuzione CRM On-Premise e Office 365 non sono più compatibili con Campaign. Adobe Campaign ora supporta solo la distribuzione API Web per la versione CRM **Dynamic CRM 365**. [Ulteriori informazioni](../../rn/using/deprecated-features.md#crm-connectors).

Per connettere Microsoft Dynamics 365 e Campaign, è necessario creare e configurare un **[!UICONTROL External Account]** dedicato in Campaign.

1. Passa a **[!UICONTROL Administration > Platform > External accounts]**.

1. Selezionare l&#39;account esterno **[!UICONTROL Microsoft Dynamics CRM]**. Seleziona l’opzione **[!UICONTROL Enabled]**.

1. Inserisci le informazioni necessarie per connettere Microsoft Dynamics 365 e Campaign.

   >[!NOTE]
   >
   >La configurazione dell&#39;account esterno di Microsoft Dynamics CRM con ogni **[!UICONTROL CRM O-Auth type]** è descritta [in questa sezione](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Fare clic sul collegamento **[!UICONTROL Microsoft CRM configuration wizard...]**. Adobe Campaign rileva automaticamente le tabelle dal modello dati di Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Seleziona le tabelle da recuperare.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Fare clic su **[!UICONTROL Next]** per iniziare a creare lo schema corrispondente.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Per approvare la configurazione, devi disconnetterti/riconnetterti alla console Adobe Campaign.

   Puoi verificare che lo schema di dati corrispondente diventi disponibile in Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Fare clic sul collegamento **[!UICONTROL Synchronizing enumerations...]** per avviare la sincronizzazione delle enumerazioni tra Adobe Campaign e Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign e Microsoft Dynamics sono ora connessi. È possibile impostare la sincronizzazione dei dati tra i due sistemi. Ulteriori informazioni nella sezione [Sincronizzazione dati](../../platform/using/crm-data-sync.md).

>[!NOTE]
>
> È necessario assicurarsi di aggiungere al elenco Consentiti due URL: l&#39;URL del server e `login.microsoftonline.com` nella configurazione del server. Per ulteriori informazioni su come configurare le autorizzazioni URL, consulta questa [pagina](../../installation/using/url-permissions.md).

## Tipi di dati dei campi supportati {#ms-dyn-supported-types}

Di seguito sono elencati i tipi di attributo supportati/non supportati per Microsoft Dynamics 365:


| Tipo di attributo | Supportato |
| --------------------------------------------------------------------------------- | --------- |
| Tipi di base : boolean, datetime, decimal, float, double, integer, bigint , string | Sì |
| Denaro (doppio) | Sì |
| memo, entityname , primarykey, uniqueidentifier (come stringhe) | Sì |
| Stato, elenco a discesa (i valori possibili vengono memorizzati nelle enumerazioni), stato (stringa) | Sì |
| proprietario (come stringa) | Sì |
| Ricerca (solo ricerche di riferimento a entità singola) | Sì |
| cliente | No |
| Riguardo | No |
| PartyList | No |
| ManagedProperty | No |
| Set di opzioni MultiSelect | No |
