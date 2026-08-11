---
product: campaign
title: Migrare all’API Adobe Analytics 2.0
description: Campaign Classic - Guida alla migrazione API di Adobe Analytics 2.0
feature: Technote, Analytics Integration
hide: true
source-git-commit: 64460d51b002a7821bba9c2998d9ccccab3046ad
workflow-type: tm+mt
source-wordcount: '874'
ht-degree: 1%

---

# Migrare all’API Adobe Analytics 2.0 {#analytics-2-migration}

Le API di Adobe Analytics 1.4 stanno per [raggiungere la fine del ciclo di vita](https://developer.adobe.com/analytics-apis/docs/1.4/guides/eol){target="_blank"}. Il [connettore Web Analytics](../../integrations/using/gs-aa.md) che collega l&#39;istanza Campaign ad Adobe Analytics si basa su queste API, pertanto devi eseguire l&#39;aggiornamento a una build che utilizza le nuove API Analytics 2.0 per mantenere l&#39;integrazione in esecuzione.

>[!CAUTION]
>
>L&#39;aggiornamento reimporta i due flussi di lavoro tecnici incorporati che alimentano il connettore, [!UICONTROL webAnalyticsSendMetrics] e [!UICONTROL webAnalyticsGetWebEvents] (consulta il [riferimento ai flussi di lavoro di Web Analytics](../../workflow/using/web-analytics.md) per le operazioni di ciascuno di essi). Eventuali personalizzazioni apportate sopra questi flussi di lavoro vengono sovrascritte dalla reimportazione. Evita di modificare direttamente questi flussi di lavoro incorporati: crea la personalizzazione in un flusso di lavoro personalizzato separato, in modo che gli aggiornamenti futuri non la sovrascrivano. L’aggiornamento aggiorna anche i file integrati di Analytics JavaScript: se uno dei flussi di lavoro personalizzati fa riferimento a tali file, questi verranno interrotti e dovranno essere adattati al nuovo codice.

## Sei interessato? {#are-you-impacted}

Sei interessato se la tua istanza utilizza l&#39;account esterno [!UICONTROL Web Analytics] per uno dei seguenti elementi:

* Invio di indicatori e attributi della campagna e-mail ad Adobe Analytics come metriche.
* Invio dei dati di classificazione ad Adobe Analytics.
* Il flusso di remarketing (identificazione dei contatti convertiti dopo una campagna).
* Un account esterno [!UICONTROL Web Analytics] che intendi configurare per la prima volta.

Non sei sicuro di quale di queste ti riguardi? Controlla quali dei flussi di lavoro tecnici sopra riportati sono attivi nell&#39;istanza e controlla la configurazione dell&#39;account esterno [!UICONTROL Web Analytics] in [!UICONTROL Administration > Platform > External accounts] (consulta [Account esterno di Web Analytics](../../installation/using/external-accounts.md#web-analytics-external-account)).

## Come effettuare la migrazione {#how-to-migrate}

Se ti trovi in un&#39;istanza **ospitata da Adobe**, Adobe gestisce automaticamente il provisioning SFTP, l&#39;inserimento di IP nell&#39;elenco Consentiti e la configurazione delle chiavi nell&#39;ambito dell&#39;aggiornamento. Devi convalidare i tuoi casi d&#39;uso solo una volta che la nuova build è attiva.

Se ti trovi in una distribuzione **on-premise o ibrida**, completa i passaggi seguenti.

1. [Aggiorna l&#39;ambiente Campaign](../../production/using/build-upgrade.md) a una build che includa le modifiche di Adobe Analytics 2.0. Puoi verificare da quale build esegui [!UICONTROL Help > About...] (consulta [come controllare la versione di Campaign](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)).
1. Esamina quali dei casi d’uso sopra riportati si applicano alla tua istanza, poiché da essa dipende il passaggio successivo.
1. Se utilizzi il flusso di remarketing, il flusso di lavoro [!UICONTROL webAnalyticsFindConverted] richiede un canale SFTP dedicato per scambiare dati con Adobe Analytics 2.0. Impostare come segue; in caso contrario, andare al passaggio successivo.
   1. Esegui il provisioning di un server SFTP per l&#39;istanza utilizzando l&#39;autenticazione basata su chiave, seguendo le [best practice per il server SFTP](../../platform/using/sftp-server-usage.md) che avresti applicato a qualsiasi altra integrazione SFTP esterna. Adobe fornisce uno [script di configurazione SFTP di esempio](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html?package=/content/software-distribution/en/details.html/content/dam/campaign/public/setup_sftp.zip){target="_blank"} per aiutarti a iniziare.
   1. Registra i dettagli di connessione del server in Adobe Analytics eseguendo lo script consegnato con la nuova build:

      ```
      nlserver javascript -instance:<instance_name> -arg:host=<sftp_host_url>#user=<sftp_user> -file <path_to_the_file>/aaremarketingLocation.js
      ```

      Esempio:

      ```
      nlserver javascript -instance:test_mkt_stage2 -arg:host=test-mkt-stage1.campaign.adobe.com#user=test -file ./nl6/datakit/nms/eng/js/aaremarketingLocation.js
      ```

   1. Inserisci nell’elenco Consentiti Adobe Analytics sul server SFTP, poiché le esportazioni di remarketing vengono avviate solo da un set fisso di intervalli IP di Adobe:
      * [Cerca gli indirizzi IP correnti della raccolta dati di Adobe Analytics](https://experienceleague.adobe.com/en/docs/core-services/interface/data-collection/ip-addresses){target="_blank"} e aggiungili all&#39;elenco consentiti del tuo server SFTP. Le esportazioni di Analytics basate su FTP (inclusi i feed di dati) provengono solo da indirizzi IPv4 nelle aree di Londra, Oregon e Singapore.
      * [Recupera la chiave pubblica di Adobe Analytics](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-18141){target="_blank"} e aggiungila al file `authorized_keys` sul tuo server SFTP in modo che Analytics possa eseguire l&#39;autenticazione.
1. Abilita il flag di funzione `FEATUREFLAG_USE_ANALYTICS_20_API` nell&#39;istanza creando o impostando `longvalue` dell&#39;opzione su `1` in [!UICONTROL xtkOption], in **[!UICONTROL Administration]> [!UICONTROL Platform] >[!UICONTROL Options]** nella struttura di Campaign Explorer. Questo passaggio è obbligatorio indipendentemente dal caso d’uso applicabile in precedenza.
1. Convalida la migrazione esercitando ogni caso d’uso che si applica alla tua istanza (invia una campagna di test, verifica che gli indicatori arrivino in Analytics e conferma i dati di remarketing, se applicabile) prima di disattivare qualsiasi connettività precedente.

## Configurazione di un nuovo account esterno di Web Analytics {#setting-up-a-new-web-analytics-external-account}

Ciò si applica sia che l’istanza sia ospitata da Adobe che on-premise/ibrida.

Se stai configurando l&#39;account esterno [!UICONTROL Web Analytics] per la prima volta anziché migrarne uno esistente, segui i [passaggi per la configurazione dell&#39;account esterno](../../installation/using/external-accounts.md#web-analytics-external-account) e la [guida introduttiva del connettore](../../integrations/using/gs-aa.md).

Poiché Analytics 2.0 introduce una nuova gestione delle classificazioni, è necessario creare anche un set di classificazione in Adobe Analytics prima che l’account esterno possa raccogliere i dati di classificazione della suite di rapporti. Questo è un nuovo passaggio: crealo dopo aver configurato le variabili di conversione e gli eventi di successo e prima di configurare l’account esterno in Campaign.

Per creare il set di classificazione:

1. Dalla barra dei menu superiore di [!DNL Adobe Analytics], seleziona **[!UICONTROL Components]** > **[!UICONTROL Classification sets]**, quindi fai clic su **[!UICONTROL New]**.

   ![](assets/analytics-classification-set-menu.png)

1. Nella finestra di dialogo **[!UICONTROL Add New Classification Set]**:

   ![](assets/analytics-classification-set-dialog.png)

   * Immetti **[!UICONTROL Name]** per il set di classificazione.
   * Imposta **[!UICONTROL Type]** su **[!UICONTROL Primary]**.
   * In **[!UICONTROL Job notifications]**, scegli gli utenti a cui inviare la notifica relativa al completamento o al fallimento dei processi del set di classificazione e fornisci gli indirizzi e-mail corrispondenti.
   * In **[!UICONTROL Subscriptions]**, seleziona la suite di rapporti e la variabile di conversione create per il nome della campagna interna nel passaggio precedente.

1. Fai clic su **[!UICONTROL Save]**.

Questo set di classificazione verrà individuato automaticamente da Campaign al momento della configurazione dell’account esterno nel passaggio successivo. Per ulteriori informazioni sui set di classificazione, consulta la [documentazione di Adobe Analytics](https://experienceleague.adobe.com/en/docs/analytics/components/classifications/sets/create-set){target="_blank"}.

## Hai bisogno di aiuto? {#need-help}

Se riscontri problemi durante la migrazione, contatta l&#39;[Assistenza clienti Adobe](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.
