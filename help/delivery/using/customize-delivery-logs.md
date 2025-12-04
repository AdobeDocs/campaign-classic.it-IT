---
product: campaign
title: 'Avanzato: personalizza i registri di consegna'
description: Scopri come estendere gli schemi dei registri di consegna per aggiungere campi personalizzati in Campaign Classic v7
feature: Monitoring
role: User, Developer
exl-id: 44ecc8c6-6584-43eb-96b4-7d8463053123
source-git-commit: 2ebae2b84741bf26dd44c872702dbf3b0ebfc453
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Avanzato: personalizza i registri di consegna {#customize-delivery-logs}

>[!NOTE]
>
>La guida completa sull&#39;accesso all&#39;elenco di consegna e sull&#39;utilizzo del dashboard di consegna è documentata nella [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard). Questo contenuto si applica sia agli utenti di Campaign Classic v7 che a quelli di Campaign v8.
>
>In questa pagina sono documentate **personalizzazioni avanzate specifiche di Campaign Classic v7** per le distribuzioni ibride e on-premise.

Per il monitoraggio delle consegne nell&#39;interfaccia utente di Campaign, consulta [Campaign v8 Monitor deliveries in Campaign UI documentation](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"}.

## Personalizzare i registri di consegna {#use-case}

Per **distribuzioni ibride/on-premise di Campaign Classic v7**, puoi personalizzare i registri di consegna estendendo gli schemi. Questa sezione mostra come aggiungere gli indirizzi IP dei mittenti ai registri di consegna.

>[!NOTE]
>
>Questa personalizzazione richiede le funzionalità di estensione dello schema disponibili nelle distribuzioni on-premise. Gli utenti di Campaign v8 Managed Cloud Services devono contattare l’Assistenza clienti di Adobe per i campi del registro di consegna personalizzati.
>
>Questa modifica è diversa se utilizzi una singola istanza o un’istanza mid-sourcing. Prima di apportare la modifica, assicurati di essere connesso all’istanza di invio dell’e-mail.

### Passaggio 1: estendere lo schema

Per aggiungere **publicID** nei registri di consegna devi prima estendere lo schema. Puoi procedere come segue.

1. Creare un&#39;estensione dello schema in **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data Schemas]** > **[!UICONTROL New]**.

   Per ulteriori informazioni sulle estensioni dello schema, consulta [questa pagina](../../configuration/using/extending-a-schema.md).

1. Selezionare **[!UICONTROL broadLogRcp]** per estendere i registri di consegna dei destinatari (nms) e definire uno spazio dei nomi personalizzato. In questo caso sarà &quot;cus&quot;:

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

1. Fare clic sul menu **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Update database structure...]**.

   ![](assets/update-database-structure.png)

1. Nella finestra **[!UICONTROL Edit tables]**, viene controllata la tabella **[!UICONTROL NmsBroadLogRcp]** (o la tabella **[!UICONTROL broadLogMid]** se l&#39;utente si trova in un ambiente di mid-sourcing), come segue:

   ![](assets/edit-tables.png)

   >[!IMPORTANT]
   >
   >Assicurati sempre che non siano presenti altre modifiche, ad eccezione della tabella **[!UICONTROL NmsBroadLoGRcp]** (o della tabella **[!UICONTROL broadLogMid]** se l&#39;utente si trova in un ambiente di mid-sourcing). In tal caso, deselezionare altre tabelle.

1. Fai clic su **[!UICONTROL Next]** per confermare. Viene visualizzata la seguente schermata:

   ![](assets/update-script.png)

1. Fare clic su **[!UICONTROL Next]**, quindi su **[!UICONTROL Start]** per avviare l&#39;aggiornamento della struttura del database. Avvio della creazione dell’indice. Questo passaggio può essere lungo, a seconda del numero di righe nella tabella **[!UICONTROL NmsBroadLogRcp]**.

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
>Per informazioni su come configurare gli elenchi nell&#39;interfaccia di Campaign Classic, fare riferimento a [questa pagina](../../platform/using/adobe-campaign-workspace.md).

Di seguito sono riportati gli elementi che dovrebbero essere visualizzati nella scheda **[!UICONTROL Delivery]** dopo le modifiche:

![](assets/logs-with-ip.png)

## Argomenti correlati

* [Monitorare le consegne nell&#39;interfaccia utente di Campaign](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-dashboard){target="_blank"} (documentazione di Campaign v8)
* [Stati di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-statuses){target="_blank"} (documentazione di Campaign v8)
* [Informazioni sugli errori di consegna](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} (documentazione di Campaign v8)
* [Gestione della quarantena](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} (documentazione di Campaign v8)
* [Estensione di uno schema](../../configuration/using/extending-a-schema.md) (v7 ibrido/on-premise)

