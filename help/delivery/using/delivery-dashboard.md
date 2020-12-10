---
solution: Campaign Classic
product: campaign
title: Pannello consegna
description: Scopri come utilizzare il dashboard di distribuzione per monitorare le consegne.
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 3c82e30cdc1057be6357d48170b959fb89c79528
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 4%

---


# Pannello consegna {#delivery-dashboard}

Il **dashboard di consegna** è fondamentale per monitorare le consegne e gli eventuali problemi riscontrati durante l&#39;invio dei messaggi.

Consente di recuperare informazioni su una consegna e di modificarle, se necessario. Il contenuto della scheda non può più essere modificato dopo l&#39;invio.

Di seguito sono riportate le informazioni che è possibile monitorare utilizzando le diverse schede disponibili nel dashboard:

* [Riepilogo consegne](#delivery-summary)
* [Report di consegna](#delivery-reports)
* [Registri di consegna, pagine mirror, esclusioni](#delivery-logs-and-history)
* [Registri e cronologia di tracciamento della distribuzione](#tracking-logs)
* [Rendering della distribuzione](#delivery-rendering)
* [Controllo della consegna](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**Argomenti correlati:**

* [Informazioni sugli errori di consegna](../../delivery/using/understanding-delivery-failures.md)
* [Informazioni sulla gestione della quarantena](../../delivery/using/understanding-quarantine-management.md)
* [Best practice di consegna](../../delivery/using/delivery-best-practices.md)
* [Gestione delle consegne](../../delivery/using/about-deliverability.md)

## Riepilogo consegne {#delivery-summary}

La scheda **[!UICONTROL Summary]** contiene le caratteristiche della consegna: stato di consegna, canale utilizzato, informazioni sul mittente, oggetto, informazioni sull&#39;esecuzione.

## Report di consegna {#delivery-reports}

Il collegamento **[!UICONTROL Reports]**, accessibile dalla scheda **[!UICONTROL Summary]**, consente di esaminare una serie di rapporti relativi all&#39;azione di consegna: rapporto sulla consegna generale, rapporto dettagliato, rapporto sulla consegna, distribuzione di messaggi non riusciti, tasso di apertura, clic e transazioni, ecc.

Il contenuto di questa scheda può essere configurato in base alle tue esigenze. Per ulteriori informazioni sui report di consegna, consultare [questa sezione](../../reporting/using/delivery-reports.md).

![](assets/delivery-report.png)

## Registri di consegna, cronologia ed esclusioni {#delivery-logs-and-history}

La scheda **[!UICONTROL Delivery]** fornisce una cronologia delle occorrenze in questa consegna. Contiene i registri di consegna, ovvero l’elenco dei messaggi inviati e il relativo stato e i messaggi associati.

Per una consegna, è possibile visualizzare (ad esempio) solo i destinatari con una consegna non riuscita o un indirizzo in quarantena. A tal fine, fare clic sul pulsante **[!UICONTROL Filters]** e selezionare **[!UICONTROL By state]**. Selezionate quindi lo stato nell’elenco a discesa. Diversi stati sono elencati in [questa pagina](../../delivery/using/delivery-statuses.md).

>[!NOTE]
>
>L&#39;elenco che visualizza i registri di consegna può essere personalizzato, come qualsiasi elenco in Campaign Classic. Ad esempio, potete aggiungere una colonna per sapere quale indirizzo IP ha inviato ogni e-mail in una consegna. Per ulteriori informazioni, fare riferimento al caso di utilizzo descritto in [questa sezione](#use-case).

![](assets/s_ncs_user_delivery_delivery_tab.png)

Il collegamento **[!UICONTROL Display the mirror page for this message...]** consente di visualizzare la pagina mirror relativa al contenuto della consegna selezionata dall&#39;elenco in una nuova finestra.

La pagina mirror è disponibile solo per le consegne per le quali è stato definito il contenuto HTML. Per ulteriori informazioni, vedere [Generazione della pagina mirror](../../delivery/using/sending-messages.md#generating-the-mirror-page).

![](assets/s_ncs_user_wizard_miror_page_link.png)

## Registri e cronologia di tracciamento della distribuzione{#tracking-logs}

La scheda **[!UICONTROL Tracking]** elenca la cronologia di tracciamento per la consegna. In questa scheda vengono visualizzati i dati di tracciamento per i messaggi inviati, ovvero tutti gli URL soggetti al tracciamento da parte  Adobe Campaign. I dati di tracciamento vengono aggiornati ogni ora.

>[!NOTE]
>
>Se il tracciamento non è abilitato per una consegna, questa scheda non viene visualizzata.

La configurazione del tracciamento viene eseguita nella fase appropriata della procedura guidata di consegna. Vedere [Come configurare i collegamenti tracciati](../../delivery/using/how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** i dati vengono interpretati nei rapporti di consegna. Vedi [questa sezione](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

## Rendering della casella in entrata {#delivery-rendering}

La scheda **[!UICONTROL Inbox rendering]** consente di visualizzare l&#39;anteprima del messaggio nei diversi contesti in cui può essere ricevuto e di verificare la compatibilità nei principali desktop e applicazioni.

In questo modo, potete essere certi che il messaggio verrà visualizzato ai destinatari in modo ottimale su diversi client Web, e-mail e dispositivi.

Per ulteriori informazioni sul rendering della inbox, fare riferimento a [questa pagina](../../delivery/using/inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## Controllo consegna {#delivery-audit-}

La scheda **[!UICONTROL Audit]** contiene il registro di consegna e tutti i messaggi relativi alle prove.

Il pulsante **[!UICONTROL Refresh]** consente di aggiornare i dati. Utilizzare il pulsante **[!UICONTROL Filters]** per definire un filtro per i dati.

Le icone speciali consentono di identificare errori o avvisi. Vedere [Analisi della consegna](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).

La sottoscheda **[!UICONTROL Proofs]** consente di visualizzare l&#39;elenco delle prove che sono state inviate.

![](assets/s_ncs_user_delivery_log_tab.png)

È possibile modificare le informazioni visualizzate in questa finestra (e quelle delle schede **[!UICONTROL Delivery]** e **[!UICONTROL Tracking]**) selezionando le colonne da visualizzare. A tal fine, fate clic sull&#39;icona **[!UICONTROL Configure list]** situata nell&#39;angolo inferiore destro. Per ulteriori informazioni sulla configurazione della visualizzazione dell&#39;elenco, fare riferimento a [questa sezione](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Sincronizzazione dashboard di distribuzione {#delivery-dashboard-synchronization}

Dal dashboard di distribuzione, è necessario controllare i messaggi elaborati e i registri di consegna per verificare che la consegna sia stata inviata correttamente.

Alcuni indicatori o lo stato possono essere errati o non aggiornati. Questo problema può essere risolto con le seguenti soluzioni:

* Se lo stato di consegna non è corretto, verifica che siano state effettuate tutte le approvazioni necessarie per la consegna oppure che i flussi di lavoro **[!UICONTROL operationMgt]** e **[!UICONTROL deliveryMgt]** siano in esecuzione senza errori. Ciò può anche essere dovuto al recapito tramite un&#39;affinità non configurata nell&#39;istanza di invio.

* Se gli indicatori di consegna sono ancora a zero e se siete in una configurazione mid-sourcing, controllate il flusso di lavoro tecnico **[!UICONTROL Mid-sourcing (delivery counters)]**. Avviatela se il suo stato non è **[!UICONTROL Started]**. È quindi possibile provare a calcolare gli indicatori facendo clic con il pulsante destro del mouse sulla consegna desiderata nell&#39; di Adobe Campaign Explorer e selezionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Per ulteriori informazioni sugli indicatori di tracciamento, consultare la sezione [sezione](../../reporting/using/delivery-reports.md#tracking-indicators).

* Se il contatore di consegna non corrisponde alla consegna, provare a calcolare gli indicatori facendo clic con il pulsante destro del mouse sulla consegna desiderata in  Adobe Campaign Explorer e selezionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** per eseguire nuovamente la sincronizzazione. Per ulteriori informazioni sugli indicatori di tracciamento, consultare la sezione [sezione](../../reporting/using/delivery-reports.md#tracking-indicators).

* Se il contatore di distribuzione non è aggiornato per le distribuzioni di mid-sourcing, verificare che il flusso di lavoro tecnico **[!UICONTROL Mid-Sourcing (Delivery counters)]** sia in esecuzione. Per ulteriori informazioni, consulta questa [pagina](../../installation/using/mid-sourcing-deployment.md).

Puoi anche tenere traccia delle consegne con diversi rapporti tramite la dashboard di distribuzione. Per ulteriori informazioni, consulta questa [sezione](../../reporting/using/delivery-reports.md).

## Caso di utilizzo: Aggiunta di indirizzi IP dei mittenti ai registri {#use-case}

In questa sezione verrà illustrato come aggiungere ai registri di consegna informazioni relative all&#39;indirizzo IP che ha inviato ogni e-mail in una consegna.

>[!NOTE]
>
>Questa modifica è diversa se si utilizza una singola istanza o un&#39;istanza mid-sourcing. Prima di apportare la modifica, assicurarsi di essere connessi all’istanza di invio tramite e-mail.

### Passaggio 1: Estendere lo schema

Per aggiungere **publicID** nei registri di consegna, è necessario estendere prima lo schema. Puoi procedere come segue.

1. Create un&#39;estensione dello schema, in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Per ulteriori informazioni sulle estensioni dello schema, fare riferimento a [questa pagina](../../configuration/using/extending-a-schema.md).

1. Selezionare **[!UICONTROL broadLogRcp]** per estendere i log di consegna dei destinatari (nms) e definire uno spazio dei nomi personalizzato. In questo caso sarà &quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Se l’istanza è in mid-sourcing, è necessario utilizzare lo schema wideLogMid.

1. Aggiungete il nuovo campo nell’estensione. In questo esempio, è necessario sostituire:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp"/>
   ```

   da:

   ```
   <element img="nms:broadLog.png" label="Recipient delivery logs" labelSingular="Recipient delivery log" name="broadLogRcp">
   <attribute desc="Outbound IP identifier" label="IP identifier"
   name="publicId" type="long"/>
   </element>
   ```

   ![](assets/edit-schema.png)

### Passaggio 2: Aggiorna struttura del database

Una volta apportate le modifiche, è necessario aggiornare la struttura del database in modo che sia allineata con la relativa descrizione logica.

Per farlo, segui la procedura indicata di seguito:

1. Fare clic sul menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**.

   ![](assets/update-database-structure.png)

1. Nella finestra **[!UICONTROL Edit tables]**, la tabella **[!UICONTROL NmsBroadLogRcp]** è selezionata (o la tabella **[!UICONTROL broadLogMid]** se l&#39;utente si trova in un ambiente mid-sourcing), come segue:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Assicurarsi sempre che non vi siano altre modifiche, ad eccezione della tabella **[!UICONTROL NmsBroadLoGRcp]** (o della tabella **[!UICONTROL broadLogMid]** se l&#39;utente si trova in un ambiente mid-sourcing). In tal caso, deselezionare le altre tabelle.

1. Fare clic su **[!UICONTROL Next]** per eseguire la convalida. Viene visualizzata la schermata seguente:

   ![](assets/update-script.png)

1. Fare clic su **[!UICONTROL Next]**, quindi su **[!UICONTROL Start]** per avviare l&#39;aggiornamento della struttura del database. Avvio della creazione dell&#39;indice. Questo passaggio può essere lungo, a seconda del numero di righe nella tabella **[!UICONTROL NmsBroadLogRcp]**.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>Una volta completato l&#39;aggiornamento della struttura fisica del database, è necessario disconnettersi e riconnettersi in modo da tenere conto delle modifiche.

### Passaggio 3: Convalida della modifica

Per confermare che tutto ha funzionato correttamente, è necessario aggiornare la schermata dei registri di consegna.

A tal fine, accedete ai registri di consegna e aggiungete la colonna &quot;ID IP&quot;.

![](assets/list-config.png)

>[!NOTE]
>
>Per informazioni su come configurare gli elenchi nell&#39;interfaccia Campaign Classic, fare riferimento a [questa pagina](../../platform/using/adobe-campaign-workspace.md).

Di seguito è riportato il contenuto della scheda **[!UICONTROL Delivery]** dopo le modifiche:

![](assets/logs-with-ip.png)
