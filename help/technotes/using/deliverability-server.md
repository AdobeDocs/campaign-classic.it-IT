---
product: campaign
title: Migrazione al nuovo server di recapito messaggi
description: Scopri come implementare il server di recapito messaggi di Campaign
hide: true
hidefromtoc: true
source-git-commit: 65ab862ec568647dd06c1f7b7b83e5b921353cc7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Server di recapito messaggi di Campaign {#acc-deliverability}

A partire dalla versione 21.1 di Campaign Classic v7, Adobe Campaign propone un nuovo server di recapito messaggi che offre elevata disponibilità e risolve i problemi di conformità in materia di sicurezza. Campaign Classic ora sincronizza le regole di recapito messaggi, i registri di trasmissione e l’indirizzo di eliminazione da e verso il nuovo server di recapito messaggi.

In qualità di cliente Campaign Classic, devi implementare il nuovo server di recapito messaggi

>[!NOTE]
>
>Per qualsiasi domanda su queste modifiche, leggi il [Domande frequenti](#faq-aa). Per ulteriori informazioni, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

## Cosa è cambiato?{#acc-deliverability-changes}

L&#39;Adobe sta disattivando i centri dati più vecchi per motivi di conformità alla sicurezza. I client Adobe Campaign Classic devono migrare al nuovo servizio di recapito messaggi, ospitato su Amazon Web Service (AWS).

Questo nuovo server garantisce un’elevata disponibilità (99.9) &#x200B; e fornisce endpoint sicuri e autenticati per consentire ai server delle campagne di recuperare i dati richiesti: invece di connettersi al database per ogni richiesta, il nuovo server di recapito messaggi memorizza in cache i dati per elaborare le richieste laddove possibile. Questo meccanismo migliora il tempo di risposta. &#x200B;


## Sei interessato da questo problema?{#acc-deliverability-impacts}

Se utilizzi il vecchio server di recapito messaggi di Adobe Campaign e il tuo ambiente è stato implementato in una build inferiore a Campaign 21.1.1, sei interessato. Devi eseguire l’aggiornamento a Campaign 21.1 (o più).

Scopri come controllare la versione [in questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Come si esegue l’aggiornamento?{#acc-deliverability-update}

In qualità di cliente in hosting, Adobe collaborerà con te per aggiornare le tue istanze alla versione più recente.

In qualità di cliente on-premise/ibrido, devi effettuare l’aggiornamento a una delle versioni più recenti per beneficiare del nuovo server di recapito messaggi .
Una volta aggiornate tutte le istanze, potrai [implementare la nuova integrazione](#implementation-steps) ad Adobe il server di recapito messaggi e garantire una transizione senza soluzione di continuità.

## Passaggi di implementazione (clienti ibridi e on-premise) {#implementation-steps}

>[!IMPORTANT]
>
>Questi passaggi devono essere eseguiti solo da implementazioni ibride e on-premise.
>
>Per le implementazioni in hosting, contatta [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

### Prerequisiti{#prerequisites}

Come parte della nuova integrazione del server di recapito messaggi, Campaign deve comunicare con Adobe Shared Services tramite un’autenticazione basata su Identity Management Service (IMS). Il modo migliore è quello di utilizzare il token gateway basato su Adobe Developer (chiamato anche Token account tecnico o JWT IO di Adobe).

### Passaggio 1: Crea/aggiorna il progetto Adobe Developer {#adobe-io-project}

1. Accesso [Console Adobe Developer](https://developer.adobe.com/console/home) e accedi con l&#39;accesso Developer della tua organizzazione.

   >[!NOTE]
   >
   > Assicurati di aver effettuato l&#39;accesso al portale organizzazione corretto.

1. Seleziona **[!UICONTROL + Add to Project]** e scegli **[!UICONTROL API]**.
1. In **[!UICONTROL Add an API]** finestra, seleziona **[!UICONTROL Adobe Campaign]**.
1. Scegli **[!UICONTROL Service Account (JWT)]** come tipo di autenticazione.
1. Se l&#39;ID client era vuoto, seleziona **[!UICONTROL Generate a key pair]** per creare una coppia di chiavi pubblica e privata.

   Le chiavi vengono quindi scaricate automaticamente con una data di scadenza predefinita di 365 giorni. Una volta scaduta, dovrai creare una nuova coppia di chiavi e aggiornare l’integrazione nel file di configurazione. Utilizzando l&#39;opzione 2, puoi scegliere di creare e caricare manualmente il tuo **[!UICONTROL Public key]** con una data di scadenza più lunga.

   >[!CAUTION]
   >
   >È necessario salvare il file config.zip quando viene visualizzato il prompt di download, poiché non sarà più possibile scaricarlo di nuovo.

1. Fai clic su **[!UICONTROL Next]**.
1. Scegli qualsiasi **[!UICONTROL Product profile]** oppure creane uno nuovo, se necessario. Non è necessaria alcuna autorizzazione **[!UICONTROL Product profile]**. Per ulteriori informazioni su [!DNL Analytics] **[!UICONTROL Product Profiles]**, fare riferimento a [questa pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html).

   Quindi, fai clic su **[!UICONTROL Save configured API]**.

1. Dal progetto, seleziona **[!UICONTROL Adobe Campaign]** e copia le seguenti informazioni in **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

>[!CAUTION]
>
>Il certificato Adobe Developer scade dopo 12 mesi. Devi generare una nuova coppia di chiavi ogni anno.

### Passaggio 2: Aggiungere le credenziali del progetto in Adobe Campaign {#add-credentials-campaign}

La chiave privata deve essere codificata in formato UTF-8 base64.

Per eseguire questa operazione:

1. Utilizza la chiave privata generata nei passaggi precedenti.
1. Codifica la chiave privata utilizzando il seguente comando: `base64 ./private.key > private.key.base64`. In questo modo il contenuto base64 verrà salvato in un nuovo file `private.key.base64`.

   >[!NOTE]
   >
   >Talvolta è possibile aggiungere automaticamente righe extra quando si copia/incolla la chiave privata. Ricorda di rimuoverlo prima di codificare la chiave privata.

1. Copia il contenuto dal file `private.key.base64`.
1. Accedi tramite SSH a ciascun contenitore in cui è installata l’istanza Adobe Campaign e aggiungi le credenziali Progetto in Adobe Campaign eseguendo il seguente comando come `neolane` utente. Verrà inserito il **[!UICONTROL Technical Account]** nel file di configurazione dell&#39;istanza.

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

1. È necessario arrestare e quindi riavviare il server per tenere conto della modifica. È inoltre possibile eseguire un `config -reload` comando.

### Passaggio 3: Controlla la configurazione

Al termine delle impostazioni, puoi controllare la configurazione dell’istanza. Segui i passaggi seguenti:

1. Apri la console del client e accedi ad Adobe Campaign come amministratore.
1. Sfoglia per **Amministrazione > Piattaforma > Opzioni**.
1. Controlla la `DmRendering_cuid` il valore dell&#39;opzione è compilato. Deve essere compilato su tutte le istanze Campaign (MKT, MID, RT, EXEC). Se non viene compilato, è necessario compilare il valore. Se non viene compilato alcun valore, contatta [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) per ottenere il tuo CUID.

### Passaggio 4: Abilita il nuovo server di recapito messaggi

Ora puoi abilitare il nuovo server di recapito messaggi. Per eseguire questa operazione:

1. Apri la console del client e accedi ad Adobe Campaign come amministratore.
1. Sfoglia per **Amministrazione > Piattaforma > Opzioni**.
1. Accedere al `NewDeliverabilityServer_FeatureFlag` e imposta il valore su `1`. Questa configurazione deve essere eseguita su tutte le istanze Campaign (MKT, MID, RT, EXEC).


### Passaggio 5: Convalida la configurazione

Per verificare che l’integrazione abbia esito positivo, effettua le seguenti operazioni:


1. Apri la console del client e accedi ad Adobe Campaign.
1. Sfoglia per **Amministrazione > Produzione > Flussi di lavoro tecnici**.
1. Riavvia **Aggiornamento per il recapito messaggi** Flusso di lavoro (deliverabilityUpdate). Questa deve essere eseguita su tutte le istanze Campaign (MKT, MID, RT, EXEC).
1. Controlla log: il flusso di lavoro deve essere eseguito senza errori.

## Domande frequenti{#faq-aa}

D: R:

D: R:



Per maggiori informazioni, contatta [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).
