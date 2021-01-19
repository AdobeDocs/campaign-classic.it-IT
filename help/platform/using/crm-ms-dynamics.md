---
solution: Campaign Classic
product: campaign
title: Connettore Microsoft Dynamics CRM
description: Connect Campaign e Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 7478ae37aee5e8b0d9c904f5b9d810375d9d6481
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 0%

---


# Connect Campaign e Microsoft Dynamics 365{#connect-to-msdyn}

In questa pagina verrà illustrato come collegare il Campaign Classic a **Microsoft Dynamics CRM 365**.

Le installazioni possibili sono:

* tramite **API Web** (consigliato). Fare riferimento alla sezione [sotto](#microsoft-dynamics-implementation-step) per informazioni sui passaggi da seguire per configurare la connessione con Microsoft Dynamics.
* con **Office 365**. Fate riferimento a [questo video](#microsoft-dynamics-office-365) per apprendere i passaggi chiave per configurare questa integrazione.
* per una distribuzione **locale**, applicate i passaggi chiave di Office 365.

La sincronizzazione dei dati viene eseguita tramite un&#39;attività di flusso di lavoro dedicata. [Ulteriori informazioni](../../platform/using/crm-data-sync.md).


>[!NOTE]
>
> Le versioni dei sistemi CRM compatibili con Campaign sono elencate nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#CRMconnectors).


## Passaggi di implementazione{#microsoft-dynamics-implementation-steps}

Per collegare Microsoft Dynamics 365 a  Adobe Campaign tramite **API Web**, è necessario applicare i seguenti passaggi:

In Microsoft Dynamics CRM:
1. Ottieni ID client Microsoft Dynamics
1. Genera Segreto Client Microsoft Dynamics
1. Configurare le autorizzazioni
1. Creare un utente app
1. Codifica la chiave privata

[Ulteriori informazioni in questa sezione](#config-crm-microsoft)

In Campaign Classic:
1. Creare un nuovo account esterno
1. Configurare l&#39;account esterno con le impostazioni di Microsoft Dynamics
1. Utilizzare la procedura guidata di configurazione per mappare tabelle e sincronizzare enumerazioni
1. Creare il flusso di lavoro di sincronizzazione

[Ulteriori informazioni in questa sezione](#configure-acc-for-microsoft)


>[!CAUTION]
> Durante la connessione  Adobe Campaign con Microsoft Dynamics non è possibile:
> * Installare i plug-in che possono modificare il comportamento di CRM e causare problemi di compatibilità con  Adobe Campaign
> * Selezione di più enumerazioni

>



## Configurare Microsoft Dynamics CRM {#config-crm-microsoft}

Per generare il token di accesso e le chiavi di configurazione dell&#39;account, è necessario accedere a [Microsoft Azure Directory](https://portal.azure.com) utilizzando le credenziali **Global Administrator**. Seguite quindi i passaggi descritti di seguito.

### Ottieni ID client Microsoft Dynamics {#get-client-id-microsoft}

Per ottenere l&#39;ID client, è necessario registrare un&#39;app in Azure Active Directory. L&#39;ID client è uguale all&#39;ID applicazione.

1. Passare a **Azure Active Directory > Registrazioni app** e fare clic su **Nuova registrazione applicazione**.
1. Assegnare un nome univoco che consenta di identificare un&#39;istanza, ad esempio **adobecamcampaign`<instance identifier>`**.
1. Scegliete **Tipo di applicazione** come **App Web / API**.
1. Utilizzate `http://localhost` per **URL di accesso**.

Una volta salvato, ottenete un **ID applicazione** che è l&#39;identificatore client per la campagna.

Ulteriori informazioni in [questa pagina](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory).

### Genera segreto client Microsoft Dynamics {#config-client-secret-microsoft}

Il segreto client è la chiave univoca per l&#39;ID client. Per ottenere l’identificatore della chiave del certificato, effettuate le seguenti operazioni:

1. Accedete a **Azure Active Directory > Registrazioni app** e selezionate l&#39;applicazione creata in precedenza.
1. Fare clic su **Certificati e Segreto**.
1. Fate clic su **Carica certificato**, quindi individuate e caricate il certificato pubblico generato.
1. Per generare il certificato è possibile utilizzare open ssl.

   Ad esempio:

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. Fare clic sul collegamento **manifest** per ottenere l&#39; **identificatore della chiave del certificato** e l&#39; **ID della chiave**.

### Configurare le autorizzazioni {#config-permissions-microsoft}

È necessario configurare le **Autorizzazioni necessarie** per l&#39;app creata.

1. Accedete a **Azure Active Directory > Registrazioni app** e selezionate l&#39;applicazione creata in precedenza.
1. Fare clic su **Impostazioni** in alto a sinistra.
1. In **Autorizzazioni richieste**, fare clic su **Aggiungi** e **Selezionare un&#39;API > Dynamics CRM Online**.
1. Fare clic su **Seleziona**, abilitare **Accesso a Dynamics 365 come utenti dell&#39;organizzazione** e fare clic su **Seleziona**.

### Creare un utente app {#create-app-user-microsoft}

L&#39;utente dell&#39;app è l&#39;utente che verrà utilizzato dall&#39;applicazione registrata in precedenza. Tutte le modifiche apportate a Microsoft Dynamics utilizzando l&#39;app registrata in precedenza verranno effettuate tramite questo utente.

**Passaggio 1**: Creare un utente non interattivo nella directory attiva di Azure

1. Fare clic su **Azure Active Directory > Utenti** e fare clic su **Nuovo utente**.
1. Assegna un nome appropriato e il nome utente deve essere un formato e-mail.
1. Scegliere **Amministratore Dynamics 365** in **Ruolo directory**.

**Passaggio 2**: Assegnazione di una licenza appropriata all&#39;utente creato

1. In [Microsoft Azure](https://portal.azure.com), fare clic su **Admin app**.
1. Vai a **Utenti > Utenti attivi** e fai clic sull&#39;utente appena creato.
1. Fare clic su **Modifica licenze prodotto** e selezionare il **Piano di coinvolgimento cliente Dynamics 365**.
1. Fai clic su **Chiudi**.

**Passaggio 3**: Creare un utente dell&#39;applicazione in Dynamics CRM

1. Da [Microsoft Azure](https://portal.azure.com), passare a **Impostazioni > Protezione > Utenti**.
1. Fare clic sul menu a discesa, selezionare **Utenti applicazione** e fare clic su **Nuovo**.
1. Utilizzate lo stesso nome utente dell&#39;utente creato nella directory attiva sopra

   >[!NOTE]
   >
   >L&#39;utilizzo dello stesso nome genera un errore di chiave duplicato, quindi finché non viene confermato se questo passaggio è necessario, usate un nome utente diverso e continuate.

1. Assegnare l&#39; **ID applicazione** per [l&#39;applicazione creata in precedenza](#get-client-id-microsoft).
1. Fare clic su **Gestisci ruoli** e scegliere il ruolo **Amministratore di sistema** per l&#39;utente.

## Configura campagna {#configure-acc-for-microsoft}

Per collegare Microsoft Dynamics 365 e Campaign, devi creare e configurare un account esterno dedicato in Campaign.

1. Passare a **[!UICONTROL Administration > Platform > External accounts]**.

1. Create un nuovo account esterno, selezionate il tipo **[!UICONTROL Microsoft Dynamics CRM]** e l&#39;opzione **[!UICONTROL Enable]**.

1. Selezionare il tipo di distribuzione **[!UICONTROL Web API]**:

   Adobe Campaign Classic supporta l&#39;interfaccia REST di Dynamics 365 con protocollo OAuth per l&#39;autenticazione con **[!UICONTROL Certificate]** o **[!UICONTROL Password Credentials]**.

   Utilizzare le impostazioni [precedentemente definite](#get-client-id-microsoft) in Azure Directory per configurare l&#39;account esterno.

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >La configurazione dell&#39;account esterno di Microsoft Dynamics CRM è dettagliata [in questa sezione](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

1. Fare clic sul collegamento **[!UICONTROL Microsoft CRM configuration wizard...]**:  Adobe Campaign rileva automaticamente le tabelle dal modello dati di Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_02.png)

1. Selezionare le tabelle da recuperare.

   ![](assets/crm_connectors_msdynamics_03.png)

1. Fare clic su **[!UICONTROL Next]** per iniziare a creare lo schema corrispondente.

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >Per approvare la configurazione, è necessario disconnettersi/riconnettersi alla console Adobe Campaign .

   È possibile verificare che lo schema di dati corrispondente sia disponibile in  Adobe Campaign.

   ![](assets/crm_connectors_msdynamics_05.png)

1. Fare clic sul collegamento **[!UICONTROL Synchronizing enumerations...]** per avviare la sincronizzazione delle enumerazioni tra  Adobe Campaign e Microsoft Dynamics.

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign e Microsoft Dynamics sono ora connessi. È possibile impostare la sincronizzazione dei dati tra i due sistemi. Ulteriori informazioni sono disponibili nella sezione [Sincronizzazione dati](../../platform/using/crm-data-sync.md).

## Configurare l&#39;integrazione di Microsoft Dynamics CRM Office 365{#microsoft-dynamics-office-365}

Guardate questo video per apprendere come integrare Dynamics 365 con Adobe Campaign Classic, nel contesto di una distribuzione di Office 365.

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)
