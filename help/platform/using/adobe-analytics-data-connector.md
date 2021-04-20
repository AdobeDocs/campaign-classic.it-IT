---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Data Connector
description: Connettore dati Adobe Analytics
feature: Overview
role: Business Practitioner, Administrator
level: Beginner
translation-type: tm+mt
source-git-commit: f2bd093d3a010e079b7f5adf3371e21d07a4f3ae
workflow-type: tm+mt
source-wordcount: '1662'
ht-degree: 1%

---


# Adobe Analytics Data Connector{#adobe-analytics-data-connector}

## Informazioni sull’integrazione del connettore dati {#about-data-connector-integration}

>[!IMPORTANT]
>
>Connettore dati Adobe Analytics non è compatibile con i messaggi transazionali (Centro messaggi).

Il connettore dati (precedentemente noto come Adobe Genesis) consente ad Adobe Campaign e Adobe Analytics di interagire attraverso il pacchetto **Connettori di Web Analytics** . Invia dati ad Adobe Campaign sotto forma di segmenti relativi al comportamento degli utenti in seguito a una campagna e-mail. Al contrario, invia indicatori e attributi delle campagne e-mail consegnate da Adobe Campaign ad Adobe Analytics - Data Connector.

Utilizzando il connettore dati, Adobe Campaign ha un modo di misurare il pubblico Internet (Web Analytics). Grazie a queste integrazioni, Adobe Campaign può recuperare i dati sul comportamento dei visitatori per uno o più siti dopo una campagna di marketing e (dopo l’analisi) può eseguire campagne di remarketing per convertirli in acquirenti. Al contrario, gli strumenti di analisi web consentono ad Adobe Campaign di inoltrare indicatori e attributi della campagna alle proprie piattaforme.

Per ulteriori informazioni sull&#39;implementazione dell&#39;integrazione Adobe Analytics con Adobe Campaign, consulta questa [documentazione](https://helpx.adobe.com/marketing-cloud/how-to/analytics-ac.html).

I campi di azione per ogni strumento sono i seguenti:

* Ruolo di analisi web:

   1. contrassegna le campagne e-mail avviate con Adobe Campaign,
   1. salva il comportamento del destinatario, sotto forma di segmenti, sul sito visualizzato dopo aver fatto clic sull’e-mail della campagna. I segmenti riguardano prodotti abbandonati (visualizzati ma non aggiunti al carrello o acquistati), acquisti o abbandono del carrello.

* Ruolo di Adobe Campaign:

   1. invia gli indicatori e gli attributi della campagna al connettore, che a sua volta li inoltra allo strumento di analisi web,
   1. recupera e analizza i segmenti,
   1. attiva una campagna di ricommercializzazione.

## Configurazione dell&#39;integrazione {#setting-up-the-integration}

Per impostare il connettore dati, è necessario connettersi all’istanza Adobe Campaign ed eseguire le operazioni seguenti:

* [Passaggio 1: Configurare l’integrazione in Analytics](#step-1--configure-integration-in-analytics)
* [Passaggio 2: Creare l’account esterno in Campaign](#step-2--create-the-external-account-in-campaign)
* [Passaggio 3: Sincronizzazione di Adobe Campaign e Adobe Analytics](#step-3--synchronize-adobe-campaign-and-adobe-analytics)

### Passaggio 1: Configurare l’integrazione in Analytics {#step-1--configure-integration-in-analytics}

I passaggi seguenti descrivono la configurazione del connettore dati utilizzando una procedura guidata.

1. Accedi a Adobe Experience Cloud utilizzando un’Enterprise ID o Adobe ID.

   ![](assets/adobe_genesis_install_001.png)

1. Dall’elenco delle soluzioni di Experience Cloud, seleziona **[!UICONTROL Analytics]**.

   ![](assets/adobe_genesis_install_013.png)

1. Dalla scheda **[!UICONTROL Admin]** , seleziona **[!UICONTROL Data Connectors]**.

   Per accedere al menu **[!UICONTROL Data Connectors]** è necessario disporre delle seguenti autorizzazioni per gli strumenti di Analytics. Per ulteriori informazioni, consulta questa [pagina](https://docs.adobe.com/content/help/en/analytics/admin/admin-console/permissions/analytics-tools.html)
   * Integrazioni (Crea)
   * Integrazioni (aggiornamento)
   * Integrazioni (Elimina)

   ![](assets/adobe_genesis_install_002.png)

1. Dall’elenco dei partner, seleziona **[!UICONTROL Adobe Campaign Classic]**.

   ![](assets/adobe_genesis_install_014.png)

1. Nella finestra di dialogo **[!UICONTROL Add integration]**, fai clic su **[!UICONTROL Activate]**.
1. Seleziona **[!UICONTROL I accept these terms and conditions]**, seleziona il **[!UICONTROL Report suite]** collegato a questa integrazione e immetti l’etichetta del connettore.

   Al termine, fai clic su **[!UICONTROL Create and configure this integration]**.

   ![](assets/adobe_genesis_install_015.png)

1. Immetti l’indirizzo e-mail che riceverà le notifiche per conto del connettore, quindi copia il **[!UICONTROL Account ID]** così come viene visualizzato nell’account Adobe Campaign esterno (per ulteriori informazioni, consulta il [Passaggio 2: Crea l’account esterno in Campaign](#step-2--create-the-external-account-in-campaign)).

   ![](assets/adobe_genesis_install_005.png)

1. Specifica gli identificatori necessari per misurare l’impatto della campagna e-mail, ovvero il nome della campagna interna (cid) e l’ID della tabella iNmsBroadlog (bid). È inoltre necessario specificare gli indicatori per gli eventi da raccogliere.
Assicurati che i **[!UICONTROL Events]** siano di tipo Numerico, altrimenti non verranno visualizzati nel menu a discesa.

   ![](assets/adobe_genesis_install_006.png)

1. Se necessario, specifica i segmenti personalizzati.

   ![](assets/adobe_genesis_install_007.png)

1. In **[!UICONTROL Data collection]**, selezionare un metodo per il recupero dei dati, in questo caso gli identificatori **[!UICONTROL cid]** e **[!UICONTROL bid]** specificati al punto 6.

   ![](assets/adobe_genesis_install_009.png)

1. Seleziona le informazioni da visualizzare nel dashboard.

   ![](assets/adobe_genesis_install_0112.png)

1. Controlla la configurazione nella pagina che riassume i passaggi precedenti.

   ![](assets/adobe_genesis_install_011.png)

1. Fai clic su **[!UICONTROL Activate Now]** per approvare la configurazione e attivare il connettore.

   ![](assets/adobe_genesis_install_012.png)

   Il connettore dati è ora configurato.

### Passaggio 2: Crea l’account esterno in Campaign {#step-2--create-the-external-account-in-campaign}

L’integrazione di Adobe Campaign nelle piattaforme Analytics viene eseguita utilizzando un connettore. Per sincronizzare le applicazioni, applicare il seguente processo:

1. Installa il pacchetto **Connettori di Web Analytics** in Adobe Campaign.
1. Vai alla cartella **[!UICONTROL Administration > Platform > External accounts]** della struttura Adobe Campaign.
1. Fai clic con il pulsante destro del mouse sull’elenco degli account esterni e seleziona **[!UICONTROL New]** nel menu a discesa (oppure fai clic sul pulsante **[!UICONTROL New]** sopra l’elenco degli account esterni).
1. Utilizza l’elenco a discesa per selezionare il tipo **[!UICONTROL Web Analytics]**.
1. Selezionare il provider del connettore, ovvero **[!UICONTROL Adobe Analytics - Data Connector]** in questo caso.

   ![](assets/webanalytics_ext_account_create_001.png)

1. Fai clic sul collegamento **[!UICONTROL Enrich the formula...]** per modificare la formula di calcolo dell’URL per specificare le informazioni sull’integrazione dello strumento di analisi web (ID campagna) e i domini dei siti di cui è necessario tenere traccia dell’attività.
1. Specifica i nomi di dominio dei siti.

   ![](assets/webanalytics_tracking_001.png)

1. Fai clic su **[!UICONTROL Next]** e assicurati che i nomi di dominio siano stati salvati.

   ![](assets/webanalytics_tracking_002.png)

1. Se necessario, è necessario sovraccaricare la formula di calcolo. A questo scopo, seleziona la casella e modifica la formula direttamente nella finestra.

   ![](assets/webanalytics_tracking_003.png)

   >[!IMPORTANT]
   >
   >Questa modalità di configurazione è riservata agli utenti esperti: eventuali errori in questa formula potrebbero causare l’arresto delle consegne e-mail.

1. La scheda **[!UICONTROL Advanced]** ti consente di configurare o modificare le impostazioni tecniche.

   * **[!UICONTROL Lifespan]**: consente di specificare il ritardo (in giorni_ dopo il quale gli eventi web vengono recuperati in Adobe Campaign dai flussi di lavoro tecnici. Predefinito: 180 giorni.
   * **[!UICONTROL Persistence]**: consente di specificare il periodo durante il quale tutti gli eventi web (ad esempio, un acquisto) possono essere attribuiti a una campagna di remarketing, Predefinito: 7 giorni.

>[!NOTE]
>
>Se utilizzi diversi strumenti di misurazione del pubblico, puoi selezionare **[!UICONTROL Other]** nell’elenco a discesa **[!UICONTROL Partners]** durante la creazione dell’account esterno. Puoi fare riferimento a un solo account esterno nelle proprietà di consegna: sarà quindi necessario adattare la formula degli URL tracciati aggiungendo i parametri previsti dall’Adobe e tutti gli altri strumenti di misurazione utilizzati.

### Passaggio 3: Sincronizzazione di Adobe Campaign e Adobe Analytics {#step-3--synchronize-adobe-campaign-and-adobe-analytics}

Dopo aver creato l’account esterno, devi sincronizzare entrambe le applicazioni.

1. Passa all’account esterno creato in precedenza.
1. Modifica l’account **[!UICONTROL Label]** in base alle esigenze.
1. Modifica il **[!UICONTROL Internal name]** in modo che corrisponda al **[!UICONTROL Name]** scelto durante la configurazione del connettore dati.

   ![](assets/webanalytics_ext_account_setting_001.png)

1. Fai clic sul collegamento **[!UICONTROL Approve connection]** .

   ![](assets/webanalytics_ext_account_setting_002.png)

   Assicurati che il **[!UICONTROL Internal name]** corrisponda al **[!UICONTROL Name]** specificato nella procedura guidata di configurazione del connettore dati.

1. Immetti **[!UICONTROL Account ID]** nella procedura guidata di configurazione del Connettore dati.

   ![](assets/webanalytics_ext_account_setting_003.png)

1. Segui i passaggi descritti nella guida alla procedura guidata Connettore dati , quindi torna all’account esterno in Adobe Campaign.
1. Fai clic su **[!UICONTROL Next]** per lo scambio di dati tra Adobe Campaign e Adobe Analytics - Data Connector.

   Al termine della sincronizzazione, viene visualizzato l’elenco dei segmenti.

   ![](assets/webanalytics_ext_account_setting_004.png)

Quando la sincronizzazione dei dati tra Adobe Campaign e Adobe Analytics - Connettore dati è effettiva, i tre segmenti predefiniti definiti nella procedura guidata Connettore dati vengono recuperati da Adobe Campaign e diventano accessibili nella scheda **[!UICONTROL Segments]** dell’account esterno Adobe Campaign.

![](assets/webanalytics_segments.png)

Se nella procedura guidata Connettore dati sono stati configurati altri segmenti, puoi aggiungerli ad Adobe Campaign. A questo scopo, fai clic sul collegamento **[!UICONTROL Update segment list]** e segui i passaggi descritti nella procedura guidata dell’account esterno. Una volta effettuata l’operazione, i nuovi segmenti vengono visualizzati nell’elenco.

![](assets/webanalytics_segments_update.png)

### Flussi di lavoro tecnici dei processi di analisi web {#technical-workflows-of-web-analytics-processes}

Scambio di dati tra Adobe Campaign e Adobe Analytics: il connettore dati è gestito da quattro flussi di lavoro tecnici che vengono eseguiti come attività in background.

Sono disponibili nella struttura Adobe Campaign, nella cartella **[!UICONTROL Administration > Production > Technical workflows > Web analytics process]** .

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**: una volta all’ora, questo flusso di lavoro scarica segmenti sul comportamento degli utenti su un dato sito, li include nel database di Adobe Campaign e avvia il flusso di lavoro di remarketing.
* **[!UICONTROL Event purge]**: questo flusso di lavoro ti consente di eliminare tutti gli eventi dal database a seconda del periodo configurato nel  **[!UICONTROL Lifespan]** campo . Per ulteriori informazioni, consulta [Passaggio 2: Crea l’account esterno in Campaign](#step-2--create-the-external-account-in-campaign).
* **[!UICONTROL Identification of converted contacts]**: della directory dei visitatori che hanno effettuato un acquisto in seguito a una campagna di remarketing. I dati raccolti da questo flusso di lavoro sono accessibili nel rapporto **[!UICONTROL Re-marketing efficiency]** , fai riferimento a questa [pagina](#creating-a-re-marketing-campaign).
* **[!UICONTROL Sending of indicators and campaign attributes]**: consente di inviare gli indicatori della campagna e-mail tramite Adobe Campaign a Adobe Experience Cloud utilizzando Adobe Analytics - Data Connector. Questo flusso di lavoro viene attivato alle 4 del mattino ogni giorno e può essere necessario 24 ore per l’invio dei dati ad Analytics.

   Tieni presente che questo flusso di lavoro non deve essere riavviato altrimenti invierà nuovamente tutti i dati precedenti che possono distorcere i risultati di Analytics.

   Gli indicatori interessati sono i seguenti:

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@elaborati)
   * **[!UICONTROL Success]** (@success)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@recipientOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personClick)
   * **[!UICONTROL Number of distinct clicks]** (@recipientClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@error)

   >[!NOTE]
   >
   >I dati inviati sono il delta basato sull’ultima istantanea che può portare a un valore negativo nei dati della metrica.

   Gli attributi inviati sono i seguenti:

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label): solo se il pacchetto  **** Campaign è installato
   * **[!UICONTROL Nature]** (operation/@nature): solo se il pacchetto  **** Campaign è installato
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (programmazione/@contactDate)



## Tracciamento delle consegne in Adobe Campaign {#tracking-deliveries-in-adobe-campaign}

Affinché Adobe Experience Cloud sia in grado di monitorare l’attività sui siti una volta inviata la consegna da Adobe Campaign, è necessario fare riferimento al connettore corrispondente nelle proprietà di consegna. A questo scopo, esegui i seguenti passaggi:

1. Apri la consegna della campagna da tracciare.

   ![](assets/webanalytics_delivery_properties_003.png)

1. Apri le proprietà di consegna.
1. Vai alla scheda **[!UICONTROL Web Analytics]** e seleziona l’account esterno creato in precedenza. Fare riferimento a [Passaggio 2: Crea l’account esterno in Campaign](#step-2--create-the-external-account-in-campaign).

   ![](assets/webanalytics_delivery_properties_002.png)

1. Ora puoi inviare la consegna e accedere al rapporto in Adobe Analytics.

## Creazione di una campagna di remarketing {#creating-a-re-marketing-campaign}

Per preparare la campagna di remarketing, è sufficiente creare modelli di consegna da utilizzare per campagne di tipo remarketing. Quindi configura la tua campagna di remarketing e collegala a un segmento. Ogni segmento deve avere una campagna di remarketing diversa.

Le campagne di ricommercializzazione vengono avviate automaticamente una volta che Adobe Campaign ha completato il recupero dei segmenti analizzando il comportamento delle persone target della campagna iniziale. In caso di abbandono del carrello o di visualizzazione del prodotto senza acquisto, viene inviata una consegna ai destinatari interessati affinché la loro navigazione sul sito finisca in un acquisto.

Adobe Campaign fornisce modelli di consegna personalizzati su cui puoi utilizzare o creare un database per preparare le campagne.

1. Dalla cartella **[!UICONTROL Explorer]**, vai alla cartella **[!UICONTROL Resources > Templates > Delivery templates]** della struttura Adobe Campaign.
1. Duplica il modello **[!UICONTROL Email delivery (re-marketing)]** o gli esempi di modelli di remarketing offerti da Adobe Campaign.
1. Personalizza il modello in base alle tue esigenze e salvalo.

   ![](assets/webanalytics_delivery_model.png)

1. Crea una nuova campagna e seleziona il modello **[!UICONTROL Re-marketing campaign]** dall’elenco a discesa.

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. Fai clic sul collegamento **[!UICONTROL Configure...]** per specificare il segmento e il modello di consegna collegati alla campagna.
1. Seleziona l’account esterno configurato in precedenza.

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. Seleziona il segmento interessato.

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. Seleziona il modello di consegna da utilizzare per la campagna di remarketing, quindi fai clic su **[!UICONTROL Finish]** per chiudere la finestra.

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. Fai clic su **[!UICONTROL OK]** per chiudere la finestra della campagna.

Il rapporto **[!UICONTROL Re-marketing efficiency]** è accessibile tramite la pagina dei report globali. Ti consente di visualizzare il numero di contatti convertiti (ovvero che hai acquistato qualcosa) in relazione al numero di abbandoni del carrello a seguito della campagna di remarketing Adobe Campaign. Il tasso di conversione viene calcolato per settimana, mese o dall’inizio della sincronizzazione tra gli strumenti di Adobe Campaign e Web analytics.

![](assets/webanalytics_reporting.png)

