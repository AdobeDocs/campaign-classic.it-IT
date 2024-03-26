---
product: campaign
title: Dashboard delle consegne
description: Scopri come utilizzare il dashboard di consegna per monitorare le consegne
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Monitoring
role: User, Data Engineer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1189'
ht-degree: 4%

---

# Dashboard delle consegne {#delivery-dashboard}


Il **dashboard di consegna** è fondamentale per monitorare le consegne e gli eventuali problemi riscontrati durante l’invio dei messaggi.

Ti consente di recuperare informazioni su una consegna e modificarle, se necessario. Tieni presente che il contenuto delle schede non può più essere modificato una volta inviata la consegna.

Di seguito sono riportate le informazioni che è possibile monitorare utilizzando le diverse schede disponibili nel dashboard:

* [Riepilogo della consegna](#delivery-summary)
* [Rapporti sulle consegne](#delivery-reports)
* [Registri di consegna, pagine mirror, esclusioni](#delivery-logs-and-history)
* [Registri e cronologia di tracciamento delle consegne](#tracking-logs)
* [Rendering consegna](#delivery-rendering)
* [Audit della consegna](#delivery-audit-)

![](assets/s_ncs_user_del_details.png)

**Argomenti correlati:**

* [Informazioni sugli errori di consegna](understanding-delivery-failures.md)
* [Informazioni sulla gestione della quarantena](understanding-quarantine-management.md)
* [Best practice per la consegna](delivery-best-practices.md)
* [Gestione del recapito messaggi](about-deliverability.md)

## Riepilogo della consegna {#delivery-summary}

Il **[!UICONTROL Summary]** La scheda contiene le caratteristiche della consegna: stato della consegna, canale utilizzato, informazioni sul mittente, oggetto, informazioni sull’esecuzione.

## Rapporti sulle consegne {#delivery-reports}

Il **[!UICONTROL Reports]** , accessibile dal **[!UICONTROL Summary]** , ti consente di esaminare una serie di rapporti relativi all’azione di consegna: rapporto generale di consegna, rapporto dettagliato, rapporto di consegna, distribuzione dei messaggi non riusciti, tasso di apertura, clic e transazioni, ecc.

Il contenuto di questa scheda può essere configurato in base alle tue esigenze. Per ulteriori informazioni sui rapporti di consegna, consulta [questa sezione](../../reporting/using/delivery-reports.md).

![](assets/delivery-report.png)

## Registri di consegna, cronologia ed esclusioni {#delivery-logs-and-history}

Il **[!UICONTROL Delivery]** fornisce una cronologia delle occorrenze della consegna. Contiene i registri di consegna, ovvero l’elenco dei messaggi inviati e il loro stato e i messaggi associati.

Per una consegna, puoi visualizzare (ad esempio) solo i destinatari con una consegna non riuscita o un indirizzo in quarantena. A questo scopo, fai clic su **[!UICONTROL Filters]** e seleziona **[!UICONTROL By state]**. Quindi seleziona lo stato nell’elenco a discesa. Diversi stati sono elencati in [questa pagina](delivery-statuses.md).

>[!NOTE]
>
>L’elenco con i registri di consegna può essere personalizzato, come qualsiasi altro elenco in Campaign Classic. Ad esempio, puoi aggiungere una colonna per individuare l’indirizzo IP che ha inviato ogni e-mail di una consegna. Per ulteriori informazioni, consulta il caso d’uso descritto in [questa sezione](#use-case).

![](assets/s_ncs_user_delivery_delivery_tab.png)

Il **[!UICONTROL Display the mirror page for this message...]** consente di visualizzare in una nuova finestra la pagina speculare per il contenuto della consegna selezionata dall’elenco.

La pagina speculare è disponibile solo per le consegne per le quali è stato definito il contenuto HTML. Per ulteriori informazioni, consulta [Generazione della pagina mirror](sending-messages.md#generating-the-mirror-page).

![](assets/s_ncs_user_wizard_miror_page_link.png)

## Registri e cronologia di tracciamento delle consegne {#tracking-logs}

Il **[!UICONTROL Tracking]** Questa scheda elenca la cronologia di tracciamento per questa consegna. In questa scheda vengono visualizzati i dati di tracciamento per i messaggi inviati, ovvero tutti gli URL soggetti a tracciamento da parte di Adobe Campaign. I dati di tracciamento vengono aggiornati ogni ora.

>[!NOTE]
>
>Se il tracciamento non è abilitato per una consegna, questa scheda non viene visualizzata.

La configurazione del tracciamento viene eseguita nella fase appropriata della procedura guidata di consegna. Consulta [Come configurare collegamenti tracciati](how-to-configure-tracked-links.md).

**[!UICONTROL Tracking]** I dati di vengono interpretati nei rapporti di consegna. Consulta [questa sezione](../../reporting/using/delivery-reports.md).

![](assets/s_ncs_user_delivery_tracking_tab.png)

## Rendering della casella in entrata {#delivery-rendering}

Il **[!UICONTROL Inbox rendering]** Questa scheda consente di visualizzare in anteprima il messaggio nei diversi contesti in cui può essere ricevuto e di verificarne la compatibilità nei desktop e nelle applicazioni principali.

In questo modo, puoi assicurarti che il messaggio venga visualizzato ai destinatari in modo ottimale su diversi client web, servizi di posta sul web e dispositivi.

Per ulteriori informazioni sul rendering della casella in entrata, consulta [questa pagina](inbox-rendering.md)

![](assets/s_tn_inbox_rendering_tokens.png)

## Audit della consegna {#delivery-audit-}

Il **[!UICONTROL Audit]** La scheda contiene il registro di consegna e tutti i messaggi relativi alle bozze.

Il **[!UICONTROL Refresh]** consente di aggiornare i dati. Utilizza il **[!UICONTROL Filters]** per definire un filtro per i dati.

Icone speciali consentono di identificare errori o avvisi. Consulta [Analisi della consegna](steps-validating-the-delivery.md#analyzing-the-delivery).

Il **[!UICONTROL Proofs]** scheda secondaria consente di visualizzare l’elenco delle bozze inviate.

![](assets/s_ncs_user_delivery_log_tab.png)

È possibile modificare le informazioni visualizzate in questa finestra (e quelle del **[!UICONTROL Delivery]** e **[!UICONTROL Tracking]** ) selezionando le colonne da visualizzare. A questo scopo, fai clic su **[!UICONTROL Configure list]** nell’angolo in basso a destra. Per ulteriori informazioni sulla configurazione della visualizzazione degli elenchi, consulta [questa sezione](../../platform/using/adobe-campaign-workspace.md#configuring-lists).

## Sincronizzazione del dashboard di consegna {#delivery-dashboard-synchronization}

Dal dashboard di consegna, controlla i messaggi elaborati e i registri di consegna per assicurarti che la consegna sia stata inviata correttamente.

Alcuni indicatori o stato possono essere errati o non aggiornati, e questo problema può essere risolto con le seguenti soluzioni:

* Se lo stato della consegna non è corretto, verifica che tutte le approvazioni necessarie siano state effettuate per questa consegna o che **[!UICONTROL operationMgt]** e **[!UICONTROL deliveryMgt]** i flussi di lavoro vengono eseguiti senza errori. Questo può essere dovuto anche alla consegna che utilizza un’affinità non configurata sull’istanza di invio.

* Se gli indicatori di consegna sono ancora pari a zero e ti trovi in una configurazione di mid-sourcing, controlla **[!UICONTROL Mid-sourcing (delivery counters)]** flusso di lavoro tecnico. Avviala se il suo stato non è **[!UICONTROL Started]**. Puoi quindi provare a ricalcolare gli indicatori facendo clic con il pulsante destro del mouse sulla consegna pertinente in Adobe Campaign Explorer e selezionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]**. Per ulteriori informazioni sugli indicatori di tracciamento, consulta questa [sezione](../../reporting/using/delivery-reports.md#tracking-indicators).

* Se il contatore di consegna non corrisponde alla consegna, prova a ricalcolare gli indicatori facendo clic con il pulsante destro del mouse sulla consegna pertinente in Adobe Campaign Explorer e selezionando **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** per risincronizzare. Per ulteriori informazioni sugli indicatori di tracciamento, consulta questa [sezione](../../reporting/using/delivery-reports.md#tracking-indicators).

* Se il contatore di consegna non è aggiornato per le distribuzioni mid-sourcing, verifica che **[!UICONTROL Mid-Sourcing (Delivery counters)]** il flusso di lavoro tecnico è in esecuzione. Per ulteriori informazioni, consulta questa [pagina](../../installation/using/mid-sourcing-deployment.md).

Puoi anche tenere traccia delle consegne con diversi rapporti tramite il dashboard di consegna. Per ulteriori informazioni, consulta questa [sezione](../../reporting/using/delivery-reports.md).

## Caso di utilizzo: aggiunta degli indirizzi IP dei mittenti ai registri {#use-case}

In questa sezione scoprirai come aggiungere ai registri di consegna informazioni relative all’indirizzo IP che ha inviato ogni e-mail di una consegna.

>[!NOTE]
>
>Questa modifica è diversa se utilizzi una singola istanza o un’istanza mid-sourcing. Prima di apportare la modifica, assicurati di essere connesso all’istanza di invio dell’e-mail.

### Passaggio 1: estendere lo schema

Da aggiungere **publicID** nei registri di consegna devi prima estendere lo schema. Puoi procedere come segue.

1. Creare un’estensione dello schema, in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Per ulteriori informazioni sulle estensioni dello schema, consulta [questa pagina](../../configuration/using/extending-a-schema.md).

1. Seleziona **[!UICONTROL broadLogRcp]** estendere i registri di consegna dei destinatari (nms) e definire uno spazio dei nomi personalizzato. In questo caso sarà &quot;cus&quot;:

   ![](assets/schema-parameters.png)

   >[!NOTE]
   >
   >Se l’istanza è in mid-sourcing, è necessario utilizzare lo schema broadLogMid.

1. Aggiungi il nuovo campo nell’estensione. In questo esempio, devi sostituire:

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

### Passaggio 2: aggiornare la struttura del database

Dopo aver apportato le modifiche, è necessario aggiornare la struttura del database in modo che sia allineata alla relativa descrizione logica.

A questo scopo, segui la procedura indicata di seguito:

1. Fai clic su **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]** menu.

   ![](assets/update-database-structure.png)

1. In **[!UICONTROL Edit tables]** finestra, il **[!UICONTROL NmsBroadLogRcp]** la tabella è selezionata (oppure **[!UICONTROL broadLogMid]** tabella (se si trova in un ambiente di mid-sourcing), come segue:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Assicurati sempre che non vi siano altre modifiche, ad eccezione della **[!UICONTROL NmsBroadLoGRcp]** tabella (o **[!UICONTROL broadLogMid]** se il si trova in un ambiente di mid-sourcing). In tal caso, deselezionare altre tabelle.

1. Clic **[!UICONTROL Next]** da convalidare. Viene visualizzata la seguente schermata:

   ![](assets/update-script.png)

1. Clic **[!UICONTROL Next]**, quindi **[!UICONTROL Start]** per avviare l&#39;aggiornamento della struttura del database. Avvio della creazione dell’indice. Questo passaggio può essere lungo, a seconda del numero di righe nel **[!UICONTROL NmsBroadLogRcp]** tabella.

   ![](assets/start-database-update.png)

>[!NOTE]
>
>Una volta completato l’aggiornamento della struttura fisica del database, è necessario disconnettersi e riconnettersi in modo da tenere conto delle modifiche.

### Passaggio 3: Convalidare la modifica

Per verificare che tutto funzioni correttamente, devi aggiornare la schermata dei registri di consegna.

A questo scopo, accedi ai registri di consegna e aggiungi la colonna &quot;Identificatore IP&quot;.

![](assets/list-config.png)

>[!NOTE]
>
>Per informazioni su come configurare gli elenchi nell’interfaccia di Campaign Classic, consulta [questa pagina](../../platform/using/adobe-campaign-workspace.md).

Di seguito è riportato ciò che si dovrebbe vedere nel **[!UICONTROL Delivery]** dopo le modifiche:

![](assets/logs-with-ip.png)
