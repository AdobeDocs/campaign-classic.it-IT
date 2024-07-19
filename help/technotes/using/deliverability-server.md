---
product: campaign
title: Aggiornamento al nuovo server di recapito messaggi
description: Scopri come aggiornare al nuovo server di recapito messaggi di Campaign
feature: Technote, Deliverability
hide: true
hidefromtoc: true
exl-id: bc62ddb9-beff-4861-91ab-dcd0fa1ed199
source-git-commit: 19b40f0b827c4b5b7b6484fe4953aebe61d00d1d
workflow-type: tm+mt
source-wordcount: '991'
ht-degree: 1%

---

# Aggiornamento al nuovo server di recapito messaggi {#acc-deliverability}

A partire dalla versione [v7.2.2](../../rn/using/latest-release.md#release-7-2-2), Adobe Campaign si basa su un nuovo server di recapito messaggi che offre elevata disponibilità e risolve i problemi di conformità relativi alla sicurezza. Campaign Classic ora sincronizza le regole di recapito messaggi, i registri di trasmissione e l’indirizzo di eliminazione da e verso il nuovo server di recapito messaggi. Il vecchio server di recapito messaggi verrà disattivato il 31 agosto 2022.

In qualità di cliente Campaign Classic, devi implementare il nuovo server di recapito messaggi **prima del 31 agosto 2022**.

>[!NOTE]
>
>Per ulteriori domande su queste modifiche, consulta le [domande frequenti](#faq) o contatta l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank}.
>

## Cosa è cambiato?{#acc-deliverability-changes}

Ad Adobe, è in corso la disattivazione dei datacenter meno recenti per motivi di conformità in materia di sicurezza. I client Adobe Campaign Classic devono migrare al nuovo servizio di recapito messaggi, in hosting su Amazon Web Service (AWS).

Questo nuovo server garantisce un’elevata disponibilità (99.9)&#x200B; e fornisce endpoint sicuri e autenticati per consentire ai server di Campaign di recuperare i dati richiesti: anziché connettersi al database per ogni richiesta, il nuovo server di recapito messaggi memorizza in cache i dati per soddisfare le richieste, ove possibile. Questo meccanismo migliora il tempo di risposta&#x200B;

## Sei interessato?{#acc-deliverability-impacts}

Tutti i clienti sono interessati e devono effettuare l’aggiornamento a [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (o più) e implementare il proprio ambiente per beneficiare del nuovo server di recapito messaggi.

## Come si esegue l’aggiornamento?{#acc-deliverability-update}

In qualità di **cliente in hosting**, Adobe collaborerà con te per aggiornare le tue istanze alla versione più recente e creare il progetto in Adobe Developer Console.

In qualità di **cliente on-premise/ibrido**, devi eseguire l’aggiornamento a [Campaign v7.2.2](../../rn/using/latest-release.md#release-7-2-2) (o più) per beneficiare del nuovo server di recapito messaggi. Una volta aggiornate tutte le istanze, devi [implementare la nuova integrazione](#implementation-steps) per Adobe deliverability server e garantire una transizione senza soluzione di continuità.

## Passaggi di implementazione {#implementation-steps}

>[!WARNING]
>
>Questi passaggi devono essere eseguiti solo per le implementazioni ibride e on-premise.

Come parte della nuova integrazione del server di recapito messaggi, Campaign deve comunicare con Adobe Shared Services tramite un’autenticazione basata su Identity Management Service (IMS). Il modo migliore è quello di utilizzare il token gateway basato su Adobe Developer (detto anche token account tecnico o Adobe di IO JWT).

>[!AVAILABILITY]
>
> Le credenziali dell’account di servizio (JWT) sono state dichiarate obsolete da Adobe. Le integrazioni di Campaign con le soluzioni e le app Adobe ora devono basarsi sulle credenziali server-to-server OAuth. </br>
>
> * Se hai implementato integrazioni in entrata con Campaign, devi migrare l&#39;account tecnico come descritto in [questa documentazione](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank). Le credenziali dell’account di servizio (JWT) esistenti continueranno a funzionare fino al 27 gennaio 2025. </br>
>
> * Se hai implementato integrazioni in uscita, ad esempio l’integrazione Campaign-Analytics o l’integrazione Experience Cloud Triggers, queste continueranno a funzionare fino al 27 gennaio 2025. Tuttavia, prima di tale data, devi aggiornare l’ambiente Campaign alla versione v7.4.1 e migrare l’account tecnico a oAuth.

### Prerequisiti{#prerequisites}

Prima di avviare l’implementazione, controlla la configurazione dell’istanza.

1. Apri la console del client Campaign e accedi ad Adobe Campaign come amministratore.
1. Selezionare **Amministrazione > Piattaforma > Opzioni**.
1. Verificare che il valore dell&#39;opzione `DmRendering_cuid` sia compilato.

   * Se l’opzione è compilata, puoi avviare l’implementazione.
   * Se non viene compilato alcun valore, contatta l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} per ottenere il tuo CUID.

   Questa opzione deve essere compilata su tutte le istanze Campaign (MKT, MID, RT, EXEC) con il valore corretto. In qualità di cliente ibrido, rivolgiti a Adobe per avere l’opzione impostata sulle istanze MID, RT ed EXEC.

In qualità di cliente on-premise, devi anche verificare che una campagna **[!UICONTROL Product profile]** sia disponibile per la tua organizzazione. A tale scopo, segui i passaggi indicati di seguito:

1. Come amministratore, connettiti a [Adobe Admin Console](https://adminconsole.adobe.com/){_blank}.
1. Accedi alla sezione **Prodotti e servizi** e verifica che **Adobe Campaign** sia elencato.
Se non riesci a visualizzare **Adobe Campaign**, contatta l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){_blank} per aggiungerlo.
1. Fai clic su **Adobe Campaign** e seleziona la tua organizzazione.
   **Attenzione**: se hai più di un&#39;organizzazione, assicurati di selezionare quella corretta. Ulteriori informazioni sulle organizzazioni [in questa pagina](https://experienceleague.adobe.com/docs/control-panel/using/faq.html#ims-org-id){_blank}.

1. Verificare che esista un **[!UICONTROL Product profile]**. In caso contrario, creala. Nessuna autorizzazione richiesta per **[!UICONTROL Product profile]**.


>[!CAUTION]
>
>In qualità di cliente on-premise, se un firewall è implementato sul tuo lato, devi aggiungere questo URL `https://deliverability-service.adobe.io` al tuo inserisco nell&#39;elenco Consentiti di. [Ulteriori informazioni](../../installation/using/url-permissions.md).


### Passaggio 1: creare/aggiornare il progetto Adobe Developer {#adobe-io-project}

Per procedere con la configurazione del connettore Adobe Analytics, accedi alla console Adobe Developer e crea il progetto server-to-server OAuth.

Per la documentazione dettagliata, consulta [questa pagina](../../integrations/using/oauth-technical-account.md#oauth-service).

### Passaggio 2: aggiungere le credenziali del progetto in Adobe Campaign {#add-credentials-campaign}

Segui i passaggi descritti in [questa pagina](../../integrations/using/oauth-technical-account.md#add-credentials) per aggiungere le credenziali del progetto OAuth in Adobe Campaign.

### Passaggio 3: Convalidare la configurazione

Per verificare il successo dell’integrazione, segui i passaggi seguenti:

1. Apri la console client e accedi ad Adobe Campaign.
1. Selezionare **Amministrazione > Produzione > Flussi di lavoro tecnici**.
1. Riavvia il flusso di lavoro **Aggiorna per il recapito messaggi** (deliverabilityUpdate). Questa operazione deve essere eseguita su tutte le istanze di Campaign (MKT, MID, RT, EXEC). In qualità di cliente ibrido, rivolgiti a Adobe per riavviare il flusso di lavoro sulle istanze MID, RT ed EXEC.
1. Check logs: il flusso di lavoro deve essere eseguito senza errori.

>[!CAUTION]
>
>Dopo l&#39;aggiornamento, è necessario interrompere il flusso di lavoro **Aggiorna rete seed per Inbox Rendering (updateRenderingSeeds)**, poiché non verrà più applicato e non riuscirà.

## Domande frequenti {#faq}

### Qual è la timeline per l’aggiornamento?

La transizione al nuovo server di recapito messaggi, che consente di aggiungere queste funzionalità migliorate e di rafforzare la sicurezza, inizierà il 22 luglio per i clienti in hosting (Campaign Managed Services). Tutti i clienti in hosting verranno aggiornati entro la fine di agosto.

I clienti on-premise e ibridi devono effettuare la transizione durante lo stesso arco temporale.

### Cosa succede se non aggiorna l’ambiente?

Qualsiasi istanza di Campaign non aggiornata entro il 31 agosto non sarà più in grado di connettersi al server di recapito messaggi di Campaign. Di conseguenza, il flusso di lavoro **Aggiorna per il recapito messaggi** (deliverabilityUpdate) non riuscirà e questo influirà sul recapito messaggi.

Se non aggiorni l’ambiente, la sincronizzazione delle impostazioni e-mail verrà interrotta (regole di gestione MX, regole e-mail in entrata, regole di gestione del dominio e regole di qualificazione dei messaggi non recapitati). Questo potrebbe influire sul tempo di consegna dei messaggi. Se si apportano modifiche significative a tali norme, queste dovranno essere applicate manualmente a partire da questo momento.

Per le istanze MKT, è interessato solo [Elenco di soppressione globale](../../campaign-opt/using/filtering-rules.md#default-deliverability-exclusion-rules).
