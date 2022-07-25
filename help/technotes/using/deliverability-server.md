---
product: campaign
title: Aggiornamento al nuovo server di recapito messaggi
description: Scopri come aggiornare al nuovo server di recapito messaggi di Campaign
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 8b8935b181b615c0a243799b14d01f778b84b715
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Aggiornamento al nuovo server di recapito messaggi {#acc-deliverability}

Avvio [versione v7.2.1](../../rn/using/latest-release.md#release-7-2-2), Adobe Campaign si basa su un nuovo server di recapito messaggi che offre elevata disponibilità e risolve i problemi di conformità in materia di sicurezza. Campaign Classic ora sincronizza le regole di recapito messaggi, i registri di trasmissione e l’indirizzo di eliminazione da e verso il nuovo server di recapito messaggi. Il vecchio server di recapito messaggi verrà disattivato il 31 agosto 2022.

In qualità di cliente Campaign Classic, devi implementare il nuovo server di recapito messaggi **prima del 31 agosto 2022**.

>[!NOTE]
>
>Per ulteriori domande su queste modifiche, consulta la sezione [Domande frequenti](#faq)o contattare [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.

## Cosa è cambiato?{#acc-deliverability-changes}

L&#39;Adobe sta disattivando i centri dati più vecchi per motivi di conformità alla sicurezza. I client Adobe Campaign Classic devono migrare al nuovo servizio di recapito messaggi, ospitato su Amazon Web Service (AWS).

Questo nuovo server garantisce un’elevata disponibilità (99.9) &#x200B; e fornisce endpoint sicuri e autenticati per consentire ai server delle campagne di recuperare i dati richiesti: invece di connettersi al database per ogni richiesta, il nuovo server di recapito messaggi memorizza in cache i dati per elaborare le richieste laddove possibile. Questo meccanismo migliora il tempo di risposta. &#x200B;

## Sei interessato da questo problema?{#acc-deliverability-impacts}

Tutti i clienti sono interessati e devono effettuare l’aggiornamento a [Campaign v7.2.1](../../rn/using/latest-release.md#release-7-2-2) (o più) e implementa il loro ambiente per beneficiare del nuovo server di recapito messaggi.

## Come si esegue l’aggiornamento?{#acc-deliverability-update}

Come **cliente ospitato**, Adobe collaborerà con te per aggiornare le istanze alla versione più recente e creare il progetto in Adobe Developer Console.

Come **cliente on-premise/ibrido**, devi effettuare l’aggiornamento a [Campaign v7.2.1](../../rn/using/latest-release.md#release-7-2-2) (o più) per beneficiare del nuovo server di recapito messaggi. Una volta aggiornate tutte le istanze, è necessario [implementare la nuova integrazione](#implementation-steps) ad Adobe il server di recapito messaggi e garantire una transizione senza soluzione di continuità.

## Passaggi di implementazione {#implementation-steps}

Come parte della nuova integrazione del server di recapito messaggi, Campaign deve comunicare con Adobe Shared Services tramite un’autenticazione basata su Identity Management Service (IMS). Il modo migliore è quello di utilizzare il token gateway basato su Adobe Developer (chiamato anche Token account tecnico o JWT IO di Adobe).


>[!WARNING]
>
>Questi passaggi devono essere eseguiti solo per le implementazioni ibride e on-premise.

### Prerequisiti{#prerequisites}

Prima di avviare l&#39;implementazione, controlla la configurazione dell&#39;istanza.

1. Apri la console del client Campaign e accedi ad Adobe Campaign come amministratore.
1. Sfoglia per **Amministrazione > Piattaforma > Opzioni**.
1. Controlla la `DmRendering_cuid` il valore dell&#39;opzione è compilato.

   * Se l’opzione è compilata, puoi avviare l’implementazione.
   * Se non viene compilato alcun valore, contatta [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} per ottenere il tuo CUID.

   Questa opzione deve essere compilata su tutte le istanze Campaign (MKT, MID, RT, EXEC) con il valore corretto. In qualità di cliente ibrido, contatta l’Adobe per avere l’opzione impostata sulle istanze MID, RT ed EXEC.

>[!CAUTION]
>
>In qualità di cliente on-premise, se sul tuo lato è implementato un firewall, devi aggiungere questo url `https://deliverability-service.adobe.io` al tuo inserire nell&#39;elenco Consentiti. [Ulteriori informazioni](../../installation/using/url-permissions.md).

### Passaggio 1: Crea/aggiorna il progetto Adobe Developer {#adobe-io-project}

1. Accesso [Console Adobe Developer](https://developer.adobe.com/console/home) e accedi con l&#39;accesso Developer della tua organizzazione. Assicurati di aver effettuato l&#39;accesso al portale organizzazione corretto.

1. Seleziona **[!UICONTROL Create new project]**.
   ![](assets/New-Project.png)


   >[!CAUTION]
   >
   >Se utilizzi già la funzionalità di autenticazione Adobe IO JWT per un’altra integrazione, ad esempio il connettore Analytics o i trigger Adobe, devi aggiornare il progetto aggiungendo **API di Campaign** a quel progetto.

1. Scegli **[!UICONTROL Add API]**.
   ![](assets/Add-API.png)
1. In **[!UICONTROL Add an API]** finestra, seleziona **[!UICONTROL Adobe Campaign]**.
   ![](assets/AC-API.png)
1. Se l&#39;ID client era vuoto, seleziona **[!UICONTROL Generate a key pair]** per creare una coppia di chiavi pubblica e privata.
   ![](assets/Generate-a-key-pair.png)

   Le chiavi vengono quindi scaricate automaticamente con una data di scadenza predefinita di 365 giorni. Una volta scaduta, dovrai creare una nuova coppia di chiavi e aggiornare l’integrazione nel file di configurazione. Utilizzando l&#39;opzione 2, puoi scegliere di creare e caricare manualmente il tuo **[!UICONTROL Public key]** con una data di scadenza più lunga.
   ![](assets/New-key-pair.png)

   >[!CAUTION]
   >
   >È necessario salvare il `config.zip` file quando viene visualizzato il prompt di download perché non sarà più possibile scaricarlo.

1. Fai clic su **[!UICONTROL Next]**.
1. Scegli qualsiasi **[!UICONTROL Product profile]** oppure creane uno nuovo, se necessario. Non è necessaria alcuna autorizzazione **[!UICONTROL Product profile]**. Per ulteriori informazioni su **[!UICONTROL Product Profiles]**, fare riferimento a [questa pagina](https://helpx.adobe.com/enterprise/using/manage-developers.html){_blank}.
   ![](assets/Product-Profile-API.png)

   Quindi, fai clic su **[!UICONTROL Save configured API]**.

1. Dal progetto, seleziona **[!UICONTROL Adobe Campaign]** e copia le seguenti informazioni in **[!UICONTROL Service Account (JWT)]**

   ![](assets/Config-API.png)

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

### Passaggio 3: Abilita il nuovo server di recapito messaggi

Ora puoi abilitare il nuovo server di recapito messaggi. Per eseguire questa operazione:

1. Apri la console del client e accedi ad Adobe Campaign come amministratore.
1. Sfoglia per **Amministrazione > Piattaforma > Opzioni**.
1. Accedere al `NewDeliverabilityServer_FeatureFlag` e imposta il valore su `1`. Questa configurazione deve essere eseguita su tutte le istanze Campaign (MKT, MID, RT, EXEC). In qualità di cliente ibrido, contatta l’Adobe per avere l’opzione impostata sulle istanze MID, RT ed EXEC.

### Passaggio 4: Convalida la configurazione

Per verificare che l’integrazione abbia esito positivo, effettua le seguenti operazioni:


1. Apri la console del client e accedi ad Adobe Campaign.
1. Sfoglia per **Amministrazione > Produzione > Flussi di lavoro tecnici**.
1. Riavvia **Aggiornamento per il recapito messaggi** Flusso di lavoro (deliverabilityUpdate). Questa deve essere eseguita su tutte le istanze Campaign (MKT, MID, RT, EXEC). In qualità di cliente ibrido, contatta l’Adobe per far riavviare il flusso di lavoro sulle istanze MID, RT ed EXEC.
1. Controlla log: il flusso di lavoro deve essere eseguito senza errori.


## Domande frequenti {#faq}

### Qual è la timeline dell’aggiornamento?

La transizione al nuovo server di recapito messaggi, che consente di aggiungere queste funzionalità migliorate e di rafforzare la sicurezza, inizierà il 22 luglio per i clienti in hosting (Campaign Managed Services). Tutti i clienti in hosting verranno aggiornati entro la fine di agosto.

I clienti on-premise e ibridi devono effettuare la transizione durante lo stesso periodo di tempo.

### Cosa succede se non aggiorno l’ambiente?

Qualsiasi istanza di Campaign non aggiornata entro il 31 agosto non sarà più in grado di connettersi al server di recapito messaggi di Campaign. Di conseguenza, il **Aggiornamento per il recapito messaggi** Il flusso di lavoro (deliverabilityUpdate) avrà esito negativo e questo influirà sul recapito messaggi.

Se non aggiorni l’ambiente, le impostazioni e-mail cesseranno di essere sincronizzate (regole di gestione MX, regole e-mail in entrata, regole di gestione del dominio e regole di qualificazione non recapitate). Questo potrebbe influenzare nel tempo il recapito messaggi. Se si apporta una modifica significativa a queste regole, queste dovranno essere applicate manualmente da questo momento in poi.

Solo per le istanze MKT [Elenco globale di soppressione](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules) è interessato.

