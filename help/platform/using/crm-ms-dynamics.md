---
product: campaign
title: Campaign - Connettore Microsoft Dynamics CRM
description: Connetti Campaign e Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 3%

---

# Connetti Campaign e Microsoft Dynamics 365{#connect-to-msdyn}

![](../../assets/common.svg)

In questa pagina imparerai a collegare Campaign Classic a **Microsoft Dynamics CRM 365**.

La distribuzione possibile è tramite **API Web** (scelta consigliata). Per informazioni su come impostare la connessione con Microsoft Dynamics, consulta [la sezione seguente](#microsoft-dynamics-implementation-step) .

La sincronizzazione dei dati viene eseguita tramite un’attività del flusso di lavoro dedicata. [Ulteriori informazioni](../../platform/using/crm-data-sync.md).

## Passaggi di implementazione{#microsoft-dynamics-implementation-steps}

Per collegare Microsoft Dynamics 365 al funzionamento con Adobe Campaign tramite **API Web**, è necessario applicare i seguenti passaggi:

In Microsoft Dynamics CRM:
1. Ottieni ID client Microsoft Dynamics
1. Genera l’identificatore chiave del certificato Microsoft Dynamics e l’ID chiave
1. Configurare le autorizzazioni
1. Creare un utente di app
1. Codifica la chiave privata

[Per ulteriori informazioni, consulta questa sezione.](#config-crm-microsoft)

In Campaign Classic:
1. Creare un nuovo account esterno
1. Configurare l’account esterno con le impostazioni di Microsoft Dynamics
1. Utilizza la procedura guidata di configurazione per mappare le tabelle e sincronizzare le enumerazioni
1. Creare il flusso di lavoro di sincronizzazione

[Per ulteriori informazioni, consulta questa sezione.](#configure-acc-for-microsoft)


>[!CAUTION]
> Quando si collega Adobe Campaign a Microsoft Dynamics, non è possibile:
> * Installa plug-in che possono modificare il comportamento del CRM e portare a problemi di compatibilità con Adobe Campaign
> * Selezionare più enumerazioni


## Configurare Microsoft Dynamics CRM {#config-crm-microsoft}

Per generare il token di accesso e le chiavi per configurare l&#39;account, è necessario accedere a [Directory di Microsoft Azure](https://portal.azure.com) utilizzando le credenziali **Amministratore globale**. Quindi segui i passaggi descritti di seguito.

### Ottieni ID client Microsoft Dynamics {#get-client-id-microsoft}

Per ottenere l’ID client, è necessario registrare un’app in Azure Active Directory. L&#39;ID client è lo stesso dell&#39;ID applicazione.

1. Passa a **Azure Active Directory > Registrazioni app** e fai clic su **Nuova registrazione applicazione**.
1. Assegna un nome univoco che possa aiutare a identificare un&#39;istanza, ad esempio **adobecamcampaign`<instance identifier>`**.
1. Scegli **Tipo di applicazione** come **App web / API**.
1. Utilizza `http://localhost` per **URL di accesso**.

Una volta salvato, ottieni un **ID applicazione** che è l’identificatore client per Campaign.

Per ulteriori informazioni, consulta [questa pagina](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Genera l’identificatore chiave del certificato Microsoft Dynamics e l’ID chiave {#config-certificate-key-id}

Per ottenere l’ **identificatore della chiave del certificato (customKeyIdentifier)** e l’ **ID della chiave (keyId)**, segui i passaggi seguenti:

1. Passa a **Azure Active Directory > Registrazioni app** e seleziona l&#39;applicazione creata in precedenza.
1. Fai clic su **Certificati e segreto**.
1. Fai clic su **Carica certificato**, quindi sfoglia e carica il certificato pubblico generato.
1. Per generare il certificato puoi utilizzare openssl.

   Ad esempio:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >Puoi modificare il numero di giorni, qui `-days 365`, nell’esempio di codice per un periodo di validità del certificato più lungo.

1. Sarà quindi necessario codificarlo in base64. Per farlo, puoi utilizzare l&#39;aiuto di un encoder Base64 o la riga di comando `base64 -w0 private.key` per Linux.

1. Fai clic sul collegamento **Manifest** per ottenere l’ **Identificatore chiave del certificato (customKeyIdentifier)** e l’ **ID chiave (keyId)**.

L’ **Identificatore chiave del certificato (customKeyIdentifier)** e l’ **ID chiave (keyId)** saranno necessari in seguito per configurare l’account esterno di Microsoft Dynamics CRM utilizzando il certificato **[!UICONTROL CRM O-Auth type]**.

### Configurare le autorizzazioni {#config-permissions-microsoft}

**Passaggio 1**: Configura le  **Autorizzazioni** necessarie per l&#39;app creata.

1. Passa a **Azure Active Directory > Registrazioni app** e seleziona l&#39;applicazione creata in precedenza.
1. Fai clic su **Impostazioni** in alto a sinistra.
1. In **Autorizzazioni richieste**, fai clic su **Aggiungi** e **Seleziona un&#39;API > Dynamics CRM Online**.
1. Fai clic su **Seleziona**, abilita la casella di controllo **Accedi a Dynamics 365 come utenti dell’organizzazione** e fai clic su **Seleziona**.
1. Quindi, dalla tua app, seleziona il **Manifest** nel menu **Gestisci**.

1. Dall&#39;editor **Manifest**, imposta la proprietà `allowPublicClient` da `null` a `true` e fai clic su **Salva**.

**Passaggio 2**: Concedere il consenso dell’amministratore

1. Passa a **Azure Active Directory > Applicazioni Enterprise**.

1. Seleziona l’applicazione a cui desideri concedere il consenso dell’amministratore a livello di tenant.

1. Dal menu del riquadro a sinistra, seleziona **Autorizzazioni** in **Sicurezza**.

1. Fai clic su **Concedi consenso amministratore**.

Per ulteriori informazioni, consulta la [documentazione di Azure](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### Creare un utente di app {#create-app-user-microsoft}

>[!NOTE]
>
> Questo passaggio è facoltativo con l’autenticazione **[!UICONTROL Password credentials]** .

L&#39;utente dell&#39;app è l&#39;utente che verrà utilizzato dall&#39;applicazione registrata in precedenza. Tutte le modifiche apportate a Microsoft Dynamics utilizzando l’app registrata sopra verranno eseguite tramite questo utente.

**Passaggio 1**: Crea un utente non interattivo nella directory attiva azure

1. Fare clic su **Azure Active Directory > Utenti** e fare clic su **Nuovo utente**.
1. Assegna un nome appropriato da utilizzare e il nome utente deve essere un formato e-mail.
1. Scegliere **Amministratore Dynamics 365** in **Ruolo directory**.

**Passaggio 2**: Assegnare una licenza corretta all&#39;utente creato

1. In [Microsoft Azure](https://portal.azure.com), fai clic su **Admin app**.
1. Vai a **Utenti > Utenti attivi** e fai clic sull&#39;utente appena creato.
1. Fai clic su **Modifica licenze prodotto** e seleziona il **Piano di coinvolgimento cliente Dynamics 365**.
1. Fai clic su **Chiudi**.

**Passaggio 3**: Creare un utente dell’applicazione in Dynamics CRM

1. Da [Microsoft Azure](https://portal.azure.com), passa a **Impostazioni > Protezione > Utenti**.
1. Fai clic sull&#39;elenco a discesa, seleziona **Utenti applicazioni** e fai clic su **Nuovo**.
1. Utilizza lo stesso nome utente dell&#39;utente creato nella directory attiva qui sopra

   >[!NOTE]
   >
   >L’utilizzo dello stesso nome genera un errore di chiave duplicato, quindi finché non viene ricevuta una conferma della necessità di questo passaggio, utilizza un nome utente diverso e procedi.

1. Assegna l&#39; **ID applicazione** per [l&#39;applicazione creata in precedenza](#get-client-id-microsoft).
1. Fai clic su **Gestisci ruoli** e scegli il ruolo **Amministratore di sistema** per l&#39;utente.

## Configurare Campaign {#configure-acc-for-microsoft}

>[!NOTE]
>
> Dopo la disattivazione di [RDS da Microsoft](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint), i tipi di distribuzione di gestione delle relazioni con i clienti on-premise e Office 365 non sono più compatibili con Campaign. Adobe Campaign ora supporta solo la distribuzione API Web per la versione CRM **Dynamic CRM 365**. [Ulteriori informazioni](../../rn/using/deprecated-features.md#crm-connectors).

Per collegare Microsoft Dynamics 365 e Campaign, devi creare e configurare un **[!UICONTROL External Account]** dedicato in Campaign.

1. Passa a **[!UICONTROL Administration > Platform > External accounts]**.

1. Seleziona l’account esterno **[!UICONTROL Microsoft Dynamics CRM]**. Seleziona l’opzione **[!UICONTROL Enabled]**.

1. Immetti le informazioni necessarie per collegare Microsoft Dynamics 365 e Campaign.

   >[!NOTE]
   >
   >La configurazione dell’account esterno Microsoft Dynamics CRM con ogni **[!UICONTROL CRM O-Auth type]** è dettagliata [in questa sezione](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. Fai clic sul collegamento **[!UICONTROL Microsoft CRM configuration wizard...]**. Adobe Campaign rileva automaticamente le tabelle dal modello dati di Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selezionare le tabelle da recuperare.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Fai clic su **[!UICONTROL Next]** per iniziare a creare lo schema corrispondente.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Per approvare la configurazione, è necessario disconnettersi/riconnettersi alla console Adobe Campaign.

   Puoi verificare che lo schema di dati corrispondente sia disponibile in Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Fai clic sul collegamento **[!UICONTROL Synchronizing enumerations...]** per avviare la sincronizzazione delle enumerazioni tra Adobe Campaign e Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign e Microsoft Dynamics sono ora connessi. È possibile impostare la sincronizzazione dei dati tra i due sistemi. Ulteriori informazioni sono disponibili nella sezione [Sincronizzazione dati](../../platform/using/crm-data-sync.md) .

>[!NOTE]
>
> Assicurati di aggiungere all’inserire nell&#39;elenco Consentiti due URL: l&#39;URL del server e `login.microsoftonline.com` nella configurazione del server.

## Tipi di dati campo supportati {#ms-dyn-supported-types}

Per i tipi di attributi supportati o non supportati da Microsoft Dynamics 365, consulta l’elenco seguente:


| Tipo di attributo | Supportato |
| --------------------------------------------------------------------------------- | --------- |
| Tipi di base : booleano, datetime, decimal, float, double, integer, bigint, string | Sì |
| Denaro (come doppio) | Sì |
| promemoria, entity yname , primarykey, uniqueidentifier (come stringhe) | Sì |
| Stato, elenco a discesa (memorizziamo i valori possibili nelle enumerazioni), stato (stringa) | Sì |
| proprietario (come stringa) | Sì |
| Ricerca (solo ricerche di riferimenti a entità singola) | Sì |
| cliente | No |
| Riguardo | No |
| PartyList | No |
| ManagedProperty | No |
