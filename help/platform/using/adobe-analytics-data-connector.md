---
solution: Campaign Classic
product: campaign
title: Adobe Analytics Data Connector
description: ' Adobe Analytics Data Connector'
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1657'
ht-degree: 1%

---


# Adobe Analytics Data Connector{#adobe-analytics-data-connector}

## Informazioni sull&#39;integrazione del connettore dati {#about-data-connector-integration}

>[!IMPORTANT]
>
> Connettore dati Adobe Analytics non è compatibile con i messaggi transazionali (Centro messaggi).

Il Connettore dati (precedentemente noto come  Adobe Genesis) consente  Adobe Campaign e  Adobe Analytics di interagire attraverso il pacchetto **Connettori di analisi Web**. Invia dati a  Adobe Campaign sotto forma di segmenti relativi al comportamento degli utenti in seguito a una campagna e-mail. Al contrario, invia indicatori e attributi delle campagne e-mail distribuite da  Adobe Campaign a  Adobe Analytics - Connettore dati.

Utilizzando il connettore dati,  Adobe Campaign ha un modo di misurare il pubblico Internet (Web Analytics). Grazie a queste integrazioni,  Adobe Campaign può recuperare i dati sul comportamento dei visitatori per uno o più siti a seguito di una campagna di marketing e (dopo l&#39;analisi) eseguire campagne di ricommercializzazione per convertirli in acquirenti. Al contrario, gli strumenti di analisi Web consentono  Adobe Campaign di inoltrare indicatori e attributi della campagna alle proprie piattaforme.

Per ulteriori informazioni sull&#39;implementazione dell&#39;integrazione  Adobe Analytics con  Adobe Campaign, fare riferimento a questa [documentazione](https://helpx.adobe.com/marketing-cloud/how-to/analytics-ac.html).

I campi di azione per ciascuno strumento sono i seguenti:

* Ruolo dell&#39;analisi Web:

   1. contrassegna le campagne e-mail avviate con  Adobe Campaign,
   1. salva il comportamento del destinatario, sul sito visualizzato dopo aver fatto clic sul messaggio e-mail della campagna, sotto forma di segmenti. I segmenti riguardano prodotti abbandonati (visualizzati ma non aggiunti al carrello o acquistati), acquisti o abbandono del carrello.

* Ruolo  Adobe Campaign:

   1. invia gli indicatori e gli attributi della campagna al connettore, che a sua volta li inoltra allo strumento di analisi Web,
   1. recupera e analizza i segmenti,
   1. attiva una campagna di ricommercializzazione.

## Configurazione dell&#39;integrazione {#setting-up-the-integration}

Per configurare il connettore dati, è necessario connettersi all&#39;istanza di Adobe Campaign  ed eseguire le operazioni seguenti:

* [Passaggio 1: Configurare l&#39;integrazione in Analytics](#step-1--configure-integration-in-analytics)
* [Passaggio 2: Creazione di un account esterno in Campaign](#step-2--create-the-external-account-in-campaign)
* [Passaggio 3: Sincronizzazione  Adobe Campaign e  Adobe Analytics](#step-3--synchronize-adobe-campaign-and-adobe-analytics)

### Passaggio 1: Configurare l&#39;integrazione in Analytics {#step-1--configure-integration-in-analytics}

I passaggi seguenti descrivono la configurazione del connettore dati utilizzando una procedura guidata.

1. Effettuate l&#39;accesso all&#39;Adobe Experience Cloud utilizzando un&#39; Adobe ID o  Enterprise ID.

   ![](assets/adobe_genesis_install_001.png)

1. Dall&#39;elenco delle soluzioni  Experience Cloud, selezionare **[!UICONTROL Analytics]**.

   ![](assets/adobe_genesis_install_013.png)

1. Dalla scheda **[!UICONTROL Admin]**, selezionare **[!UICONTROL Data Connectors]**.

   Per accedere al menu **[!UICONTROL Data Connectors]** è necessario disporre delle seguenti autorizzazioni per gli strumenti di Analytics. Per ulteriori informazioni, consulta questa [pagina](https://docs.adobe.com/content/help/en/analytics/admin/admin-console/permissions/analytics-tools.html)
   * Integrazioni (Crea)
   * Integrazioni (aggiornamento)
   * Integrazioni (Elimina)

   ![](assets/adobe_genesis_install_002.png)

1. Dall&#39;elenco dei partner, selezionare **[!UICONTROL Adobe Campaign Classic]**.

   ![](assets/adobe_genesis_install_014.png)

1. Nella finestra di dialogo **[!UICONTROL Add integration]**, fare clic su **[!UICONTROL Activate]**.
1. Selezionare **[!UICONTROL I accept these terms and conditions]**, selezionare il **[!UICONTROL Report suite]** collegato a questa integrazione e immettere l&#39;etichetta del connettore.

   Al termine, fare clic su **[!UICONTROL Create and configure this integration]**.

   ![](assets/adobe_genesis_install_015.png)

1. Immettere l&#39;indirizzo e-mail che riceverà le notifiche per conto del connettore, quindi copiare l&#39; **[!UICONTROL Account ID]** così come appare nell&#39;account Adobe Campaign  esterno (per ulteriori informazioni, fare riferimento al [Passaggio 2: Create l&#39;account esterno in Campaign](#step-2--create-the-external-account-in-campaign).

   ![](assets/adobe_genesis_install_005.png)

1. Specificate gli identificatori necessari per misurare l’impatto della campagna e-mail, ad esempio il nome della campagna interna (cid) e l’ID tabella iNmsBroadlog (bid). È inoltre necessario specificare gli indicatori per gli eventi da raccogliere.
Assicurarsi che il tipo **[!UICONTROL Events]** sia numerico, altrimenti non verrà visualizzato nel menu a discesa.

   ![](assets/adobe_genesis_install_006.png)

1. Se necessario, specificate i segmenti personalizzati.

   ![](assets/adobe_genesis_install_007.png)

1. In **[!UICONTROL Data collection]**, selezionare un metodo per il recupero dei dati, in questo caso gli identificatori **[!UICONTROL cid]** e **[!UICONTROL bid]** specificati al punto 6.

   ![](assets/adobe_genesis_install_009.png)

1. Selezionate le informazioni da visualizzare nel dashboard.

   ![](assets/adobe_genesis_install_0112.png)

1. Controllare la configurazione nella pagina che riassume i passaggi precedenti.

   ![](assets/adobe_genesis_install_011.png)

1. Fare clic su **[!UICONTROL Activate Now]** per approvare la configurazione e attivare il connettore.

   ![](assets/adobe_genesis_install_012.png)

   Il connettore dati è ora configurato.

### Passaggio 2: Crea account esterno in Campaign {#step-2--create-the-external-account-in-campaign}

L&#39;integrazione di  Adobe Campaign nelle piattaforme Analytics viene realizzata utilizzando un connettore. Per sincronizzare le applicazioni, eseguite il seguente processo:

1. Installate il pacchetto **Connettori di analisi Web** in  Adobe Campaign.
1. Passate alla cartella **[!UICONTROL Administration > Platform > External accounts]** della struttura di Adobe Campaign .
1. Fare clic con il pulsante destro del mouse sull&#39;elenco degli account esterni e selezionare **[!UICONTROL New]** nel menu a discesa (oppure fare clic sul pulsante **[!UICONTROL New]** sopra l&#39;elenco degli account esterni).
1. Utilizzare l&#39;elenco a discesa per selezionare il tipo **[!UICONTROL Web Analytics]**.
1. Selezionare il fornitore del connettore, ovvero **[!UICONTROL Adobe Analytics - Data Connector]** in questo caso.

   ![](assets/webanalytics_ext_account_create_001.png)

1. Fate clic sul collegamento **[!UICONTROL Enrich the formula...]** per modificare la formula di calcolo degli URL per specificare le informazioni di integrazione dello strumento di analisi Web (ID campagna) e i domini dei siti di cui è necessario tenere traccia dell&#39;attività.
1. Specificate i nomi di dominio dei siti.

   ![](assets/webanalytics_tracking_001.png)

1. Fare clic su **[!UICONTROL Next]** e assicurarsi che i nomi di dominio siano stati salvati.

   ![](assets/webanalytics_tracking_002.png)

1. Se necessario, è necessario sovraccaricare la formula di calcolo. A questo scopo, selezionare la casella e modificare la formula direttamente nella finestra.

   ![](assets/webanalytics_tracking_003.png)

   >[!IMPORTANT]
   >
   >Questa modalità di configurazione è riservata agli utenti esperti: eventuali errori nella formula potrebbero causare l&#39;interruzione delle consegne tramite e-mail.

1. La scheda **[!UICONTROL Advanced]** consente di configurare o modificare altre impostazioni tecniche.

   * **[!UICONTROL Lifespan]**: consente di specificare il ritardo (in giorni_ dopo il quale gli eventi Web recuperati in  Adobe Campaign dai flussi di lavoro tecnici. Predefinito: 180 giorni.
   * **[!UICONTROL Persistence]**: consente di specificare il periodo durante il quale tutti gli eventi Web (ad esempio un acquisto) possono essere attribuiti a una campagna di ricommercializzazione, Default: 7 giorni.

>[!NOTE]
>
>Se utilizzate diversi strumenti di misurazione del pubblico, potete selezionare **[!UICONTROL Other]** nell&#39;elenco a discesa **[!UICONTROL Partners]** al momento della creazione dell&#39;account esterno. È possibile fare riferimento a un solo account esterno nelle proprietà di consegna: sarà quindi necessario adattare la formula degli URL tracciati aggiungendo i parametri previsti dal Adobe  e da tutti gli altri strumenti di misurazione utilizzati.

### Passaggio 3: Sincronizzare  Adobe Campaign e  Adobe Analytics {#step-3--synchronize-adobe-campaign-and-adobe-analytics}

Dopo aver creato l&#39;account esterno, è necessario sincronizzare entrambe le applicazioni.

1. Passate all&#39;account esterno creato in precedenza.
1. Modificate l&#39;account **[!UICONTROL Label]** come necessario.
1. Modificare la **[!UICONTROL Internal name]** in modo che corrisponda alla **[!UICONTROL Name]** scelta durante la configurazione del connettore dati.

   ![](assets/webanalytics_ext_account_setting_001.png)

1. Fare clic sul collegamento **[!UICONTROL Approve connection]**.

   ![](assets/webanalytics_ext_account_setting_002.png)

   Assicurarsi che la **[!UICONTROL Internal name]** corrisponda alla **[!UICONTROL Name]** specificata nella procedura guidata di configurazione del connettore dati.

1. Immettere **[!UICONTROL Account ID]** nella procedura guidata di configurazione del connettore dati.

   ![](assets/webanalytics_ext_account_setting_003.png)

1. Seguire i passaggi descritti nella guida alla procedura guidata Connettore dati, quindi tornare all&#39;account esterno in  Adobe Campaign.
1. Fare clic su **[!UICONTROL Next]** per lo scambio di dati tra  Adobe Campaign e  Adobe Analytics - Connettore dati.

   L&#39;elenco dei segmenti viene visualizzato al termine della sincronizzazione.

   ![](assets/webanalytics_ext_account_setting_004.png)

Quando la sincronizzazione dei dati tra  Adobe Campaign e  Adobe Analytics - Connettore dati è effettiva, i tre segmenti predefiniti definiti nella procedura guidata Connettore dati vengono recuperati da  Adobe Campaign e diventano accessibili nella scheda **[!UICONTROL Segments]** dell&#39;account esterno  Adobe Campaign.

![](assets/webanalytics_segments.png)

Se nella procedura guidata Connettore dati sono stati configurati altri segmenti, puoi aggiungerli ad  Adobe Campaign. A questo scopo, fate clic sul collegamento **[!UICONTROL Update segment list]** e seguite i passaggi descritti nella procedura guidata dell&#39;account esterno. Una volta eseguita l&#39;operazione, i nuovi segmenti saranno visualizzati nell&#39;elenco.

![](assets/webanalytics_segments_update.png)

### Flussi di lavoro tecnici dei processi di analisi Web {#technical-workflows-of-web-analytics-processes}

Scambio di dati tra  Adobe Campaign e  Adobe Analytics - Connettore dati è gestito da quattro flussi di lavoro tecnici che vengono eseguiti come attività in background.

Sono disponibili nella struttura  Adobe Campaign, nella cartella **[!UICONTROL Administration > Production > Technical workflows > Web analytics process]**.

![](assets/webanalytics_workflows.png)

* **[!UICONTROL Recovering of web events]**: una volta all’ora, questo flusso di lavoro scarica i segmenti sul comportamento degli utenti in un dato sito, li include nel database Adobe Campaign  e avvia il flusso di lavoro di remarketing.
* **[!UICONTROL Event purge]**: questo flusso di lavoro consente di eliminare tutti gli eventi dal database a seconda del periodo configurato nel  **[!UICONTROL Lifespan]** campo. Per ulteriori informazioni, vedere [Passaggio 2: Crea l&#39;account esterno in Campaign](#step-2--create-the-external-account-in-campaign).
* **[!UICONTROL Identification of converted contacts]**: directory dei visitatori che hanno effettuato un acquisto in seguito a una campagna di remarketing. I dati raccolti da questo flusso di lavoro sono accessibili nel report **[!UICONTROL Re-marketing efficiency]**, fare riferimento a [page](#creating-a-re-marketing-campaign).
* **[!UICONTROL Sending of indicators and campaign attributes]**: consente di inviare gli indicatori delle campagne e-mail tramite  Adobe Campaign all&#39;Adobe Experience Cloud utilizzando  Adobe Analytics - Connettore dati. Questo flusso di lavoro viene attivato ogni giorno alle 4 del mattino e potrebbe essere necessario attendere 24 ore prima che i dati vengano inviati ad Analytics.

   Il flusso di lavoro non deve essere riavviato oppure tutti i dati precedenti che possono distorcere i risultati di Analytics verranno inviati di nuovo.

   Gli indicatori interessati sono:

   * **[!UICONTROL Messages to deliver]** (@toDeliver)
   * **[!UICONTROL Processed]** (@processed)
   * **[!UICONTROL Success]** (@success)
   * **[!UICONTROL Total count of opens]** (@totalRecipientOpen)
   * **[!UICONTROL Recipients who have opened]** (@destinatarioOpen)
   * **[!UICONTROL Total number of recipients who clicked]** (@totalRecipientClick)
   * **[!UICONTROL People who clicked]** (@personaClic)
   * **[!UICONTROL Number of distinct clicks]** (@destinatarioClick)
   * **[!UICONTROL Opt-Out]** (@optOut)
   * **[!UICONTROL Errors]** (@error)

   >[!NOTE]
   >
   >I dati inviati sono il delta basato sull&#39;ultima istantanea che potrebbe portare a un valore negativo nei dati delle metriche.

   Gli attributi inviati sono i seguenti:

   * **[!UICONTROL Internal name]** (@internalName)
   * **[!UICONTROL Label]** (@label)
   * **[!UICONTROL Label]** (operation/@label): solo se il pacchetto  **** Campagna è installato
   * **[!UICONTROL Nature]** (operation/@nature): solo se il pacchetto  **** Campagna è installato
   * **[!UICONTROL Tag 1]** (webAnalytics/@tag1)
   * **[!UICONTROL Tag 2]** (webAnalytics/@tag2)
   * **[!UICONTROL Tag 3]** (webAnalytics/@tag3)
   * **[!UICONTROL Contact date]** (Pianificazione/@contactDate)



## Tracciamento delle consegne in  Adobe Campaign {#tracking-deliveries-in-adobe-campaign}

Affinché Adobe Experience Cloud possa monitorare l&#39;attività sui siti una volta che la consegna viene inviata da  Adobe Campaign, è necessario fare riferimento al connettore corrispondente nelle proprietà di consegna. A questo scopo, eseguire i seguenti passaggi:

1. Aprite la distribuzione della campagna da monitorare.

   ![](assets/webanalytics_delivery_properties_003.png)

1. Aprite le proprietà di consegna.
1. Fare clic sulla scheda **[!UICONTROL Web Analytics]** e selezionare l&#39;account esterno creato in precedenza. Fare riferimento a [Passaggio 2: Crea l&#39;account esterno in Campaign](#step-2--create-the-external-account-in-campaign).

   ![](assets/webanalytics_delivery_properties_002.png)

1. Ora puoi inviare la consegna e accedere al report in  Adobe Analytics.

## Creazione di una campagna di ricommercializzazione {#creating-a-re-marketing-campaign}

Per preparare la campagna di ricommercializzazione, è sufficiente creare dei modelli di consegna da utilizzare per campagne di tipo remarketing. Quindi configura la tua campagna di ricommercializzazione e collegala a un segmento. Ogni segmento deve avere una campagna di ricommercializzazione diversa.

Le campagne di ricommercializzazione vengono avviate automaticamente una volta che  Adobe Campaign ha completato il recupero dei segmenti analizzando il comportamento delle persone a cui è destinato il targeting della campagna iniziale. In caso di abbandono del carrello o di visualizzazione del prodotto senza acquisto, viene inviata una consegna ai destinatari interessati affinché la loro navigazione sul sito finisca in un acquisto.

 Adobe Campaign offre modelli personalizzati per la distribuzione che potete utilizzare come database per preparare le campagne.

1. Dalla cartella **[!UICONTROL Explorer]**, passare alla cartella **[!UICONTROL Resources > Templates > Delivery templates]** della struttura  Adobe Campaign.
1. Duplica il modello **[!UICONTROL Email delivery (re-marketing)]** o gli esempi di modelli di remarketing offerti da  Adobe Campaign.
1. Personalizzate il modello in base alle vostre esigenze e salvatelo.

   ![](assets/webanalytics_delivery_model.png)

1. Create una nuova campagna e selezionate il modello **[!UICONTROL Re-marketing campaign]** dall&#39;elenco a discesa.

   ![](assets/webanalytics_remarketing_campaign_002.png)

1. Fate clic sul collegamento **[!UICONTROL Configure...]** per specificare il segmento e il modello di consegna collegati alla campagna.
1. Selezionate l&#39;account esterno configurato in precedenza.

   ![](assets/webanalytics_remarketing_campaign_003.png)

1. Selezionare il segmento interessato.

   ![](assets/webanalytics_remarketing_campaign_005.png)

1. Selezionate il modello di consegna da utilizzare per la campagna di remarketing, quindi fate clic su **[!UICONTROL Finish]** per chiudere la finestra.

   ![](assets/webanalytics_remarketing_campaign_006.png)

1. Fate clic su **[!UICONTROL OK]** per chiudere la finestra della campagna.

Il report **[!UICONTROL Re-marketing efficiency]** è accessibile dalla pagina dei report globali. Consente di visualizzare il numero di contatti convertiti (ovvero che hanno acquistato qualcosa) in relazione al numero di abbandoni del carrello a seguito della campagna di ricommercializzazione  Adobe Campaign. Il tasso di conversione è calcolato ogni settimana, mese o dall&#39;inizio della sincronizzazione tra  strumenti di analisi Adobe Campaign e Web.

![](assets/webanalytics_reporting.png)

