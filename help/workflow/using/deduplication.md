---
title: Deduplication
description: Ulteriori informazioni sull'attività del flusso di lavoro Deduplicazione
page-status-flag: never-activated
uuid: 90dee589-ac45-442e-89ef-1c14bb22200d
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 83b915bd-7e23-41b5-9f9a-f7eb72026376
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 10%

---


# Deduplication{#deduplication}

Deduplicazione elimina i duplicati dai risultati delle attività in entrata. È possibile eseguire la deduplicazione sull&#39;indirizzo e-mail, sul numero di telefono o su un altro campo.

## Best practice {#best-practices}

Durante la deduplicazione, i flussi in entrata vengono elaborati separatamente. Se, ad esempio, il destinatario A si trova nel risultato della query 1 e nel risultato della query 2, non verrà deduplicato.

Questo problema deve essere affrontato come segue:

* Crea un&#39;attività **dell&#39;Unione** per unificare ogni flusso in entrata.
* Create un&#39;attività di **deduplicazione** dopo l&#39;attività **dell&#39;Unione** .

![](assets/dedup_bonnepratique.png)

## Configurazione {#configuration}

Per configurare una deduplicazione, immettete l’etichetta, il metodo e i criteri di deduplicazione, nonché le opzioni relative al risultato.

Fare clic sul **[!UICONTROL Edit configuration...]** collegamento per definire la modalità di deduplicazione.

![](assets/s_user_segmentation_dedup_param.png)

1. Selezione destinazione

   Selezionare il tipo di target per questa attività (per impostazione predefinita, la deduplicazione riguarda i destinatari) e il criterio da utilizzare, ovvero il campo per il quale valori identici consentono di identificare duplicati: indirizzo e-mail, numero di cellulare o di telefono, numero di fax o indirizzo di posta diretta.

   ![](assets/s_user_segmentation_dedup_param2.png)

   >[!NOTE]
   >
   >Se si utilizzano dati esterni come input, ad esempio da un file esterno, assicurarsi di selezionare l&#39; **[!UICONTROL Temporary schema]** opzione.
   >
   >Nel passaggio successivo, l’ **[!UICONTROL Other]** opzione consente di selezionare il criterio o i criteri da utilizzare:

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Metodi di deduplicazione

   Dall’elenco a discesa, selezionate il metodo di deduplicazione da utilizzare e immettete il numero di duplicati da conservare.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Sono disponibili i seguenti metodi:

   * **[!UICONTROL Choose for me]**: seleziona in modo casuale il record da escludere dai duplicati.
   * **[!UICONTROL Following a list of values]**: ti consente di definire un valore di priorità per uno o più campi. Per definire i valori, seleziona un campo o crea un’espressione, quindi aggiungi i valori nella tabella appropriata. Per definire un nuovo campo, fai clic sul pulsante **[!UICONTROL Add]** situato sopra l’elenco dei valori.

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**: questo ti consente di conservare i record per i quali il valore dell’espressione selezionata non è vuoto come priorità.

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**: consente di conservare i record con il valore più basso (o più alto) dell&#39;espressione data.

      ![](assets/s_user_segmentation_dedup_param7.png)
   Fare clic **[!UICONTROL Finish]** per approvare il metodo di deduplicazione selezionato.

   La sezione centrale della finestra riepiloga la configurazione definita.

   Nella sezione inferiore della finestra dell&#39;editor attività, potete modificare l&#39;etichetta per la transizione in uscita dell&#39;oggetto grafico e immettere un codice di segmento che verrà associato al risultato dell&#39;attività. Questo codice può essere utilizzato successivamente come criterio di targeting.

   ![](assets/s_user_segmentation_dedup_param8.png)

   Check the **[!UICONTROL Generate complement]** option if you wish to exploit the remaining population. Il complemento è costituito da tutti i duplicati. All&#39;attività verrà quindi aggiunta un&#39;ulteriore transizione, come segue:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Esempio: Identificare i duplicati prima della consegna {#example--identify-the-duplicates-before-a-delivery}

Nell&#39;esempio seguente, la deduplicazione riguarda l&#39;unione di tre query.

Lo scopo del flusso di lavoro è definire la destinazione per la consegna escludendo i duplicati per evitare di inviarla più volte allo stesso destinatario.

I duplicati identificati saranno inoltre integrati in un elenco dedicato di duplicati, che potrà essere riutilizzato se necessario.

![](assets/deduplication_example.png)

1. Aggiungete e collegate le varie attività necessarie per il funzionamento del flusso di lavoro, come mostrato sopra.

   L&#39;attività dell&#39;unione viene utilizzata qui per &quot;unificare&quot; le tre query in un&#39;unica transizione. Di conseguenza, la deduplicazione non funziona per ogni query singolarmente ma per l’intera query. Per ulteriori informazioni su questo argomento, consulta [Best practice](#best-practices).

1. Aprite l&#39;attività di deduplicazione, quindi fate clic sul **[!UICONTROL Edit configuration...]** collegamento per definire la modalità di deduplicazione.
1. Nella nuova finestra, selezionare **[!UICONTROL Database schema]**.
1. Selezionate **Destinatari** come dimensioni di targeting e filtro.
1. Selezionate il campo ID per i **[!UICONTROL Email]** duplicati, per inviare la consegna una sola volta a ogni indirizzo e-mail, quindi fate clic su **[!UICONTROL Next]**.

   Se desiderate basare gli ID duplicati su un campo specifico, selezionate **[!UICONTROL Other]** per accedere all&#39;elenco dei campi disponibili.

1. Scegliete di mantenere una sola voce quando lo stesso indirizzo e-mail è identificato per più destinatari.
1. Selezionare la modalità di **[!UICONTROL Choose for me]** deduplicazione in modo che i record salvati in caso di duplicati identificati vengano scelti in modo casuale, quindi fare clic **[!UICONTROL Finish]**.

Durante l&#39;esecuzione del flusso di lavoro, tutti i destinatari identificati come duplicati vengono esclusi dal risultato (e quindi dalla consegna) e aggiunti all&#39;elenco dei duplicati. Questo elenco può essere utilizzato di nuovo anziché dover identificare nuovamente i duplicati.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in ingresso deve specificare una destinazione definita da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica la destinazione risultante dalla deduplicazione. **[!UICONTROL tableName]** è il nome della tabella che salva gli identificatori di destinazione, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:destinatario) ed **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.
