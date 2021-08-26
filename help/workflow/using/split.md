---
product: campaign
title: Divisione
description: Ulteriori informazioni sull’attività del flusso di lavoro Split
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1935'
ht-degree: 0%

---

# Divisione{#split}

![](../../assets/common.svg)

Un’attività di tipo **Split** consente di dividere un target in diversi sottoinsiemi. Il target viene costruito con tutti i risultati ricevuti: tutte le attività precedenti devono pertanto essere state completate per poter eseguire questa attività.

Questa attività non attiva un’unione di popolazioni in entrata. Se più transizioni arrivano in un’attività con una suddivisione, ti consigliamo di inserire davanti a essa un’attività **[!UICONTROL Union]** .

Per un esempio dell&#39;attività divisa in uso, consulta [Creazione di sottoinsiemi tramite l&#39;attività Split](targeting-data.md#creating-subsets-using-the-split-activity).

Un esempio che illustra come utilizzare l&#39;attività Split per segmentare il target in popolazioni diverse utilizzando condizioni di filtro è descritto in [questa sezione](cross-channel-delivery-workflow.md).

Un esempio che mostra come utilizzare una variabile di istanza in un&#39;attività Split è disponibile in [questa sezione](javascript-scripts-and-templates.md).

Per configurare questa attività, definisci il contenuto e l’etichetta del sottoinsieme nella scheda **[!UICONTROL Subsets]** , quindi scegli la dimensione di destinazione nella scheda **[!UICONTROL General]** .

## Creazione di sottoinsiemi {#creating-subsets}

Per creare un sottoinsieme:

1. Fai clic sull’etichetta nel campo corrispondente e seleziona il filtro da applicare.
1. Per filtrare il gruppo in entrata, seleziona l’opzione **[!UICONTROL Add a filtering condition]** e fai clic sul collegamento **[!UICONTROL Edit...]** .

   Seleziona il tipo di filtro da applicare ai dati per includerlo in questo set.

   Il processo è lo stesso di un&#39;attività di tipo **Query**.

   >[!NOTE]
   >
   >Puoi filtrare i dati in un massimo di due database esterni (FDA).

1. È possibile specificare il numero massimo di record da estrarre dal target per creare il sottoinsieme. A questo scopo, seleziona l’opzione **[!UICONTROL Limit the selected records]** e fai clic sul collegamento **[!UICONTROL Edit...]** .

   Una procedura guidata consente di scegliere la modalità di selezione per i record di questo sottoinsieme. I passaggi si trovano in [Limitazione del numero di record di sottoinsiemi](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. Se lo desideri, puoi **aggiungere altri sottoinsiemi** utilizzando il pulsante **[!UICONTROL Add]** .

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >Se l’opzione **[!UICONTROL Enable overlapping of output populations]** non è selezionata, i sottoinsiemi vengono creati nell’ordine delle schede. Utilizzare le frecce nella parte superiore destra di questa finestra per spostarle. Se il primo sottoinsieme recupera il 70% della popolazione iniziale, ad esempio, il sottoinsieme successivo applicherà i criteri di selezione solo al restante 30%, e così via.

   Per ogni sottoinsieme creato, all’attività di suddivisione verrà aggiunta una transizione in uscita.

   ![](assets/s_user_segmentation_partage_add2.png)

   Puoi scegliere di generare una singola transizione in uscita (e di identificare i set utilizzando, ad esempio, il codice del segmento): a questo scopo, seleziona l’opzione **[!UICONTROL Generate subsets in the same table]** nella scheda **[!UICONTROL General]** .

   Se è completato, il codice del segmento di ciascun sottoinsieme viene memorizzato automaticamente in una colonna aggiuntiva. Questa colonna sarà accessibile nei campi di personalizzazione a livello di consegna.

## Limitazione del numero di record del sottoinsieme {#limiting-the-number-of-subset-records}

Se non si desidera utilizzare l&#39;intera popolazione contenuta in un sottoinsieme, è possibile limitare il numero di record che conterrà.

1. Nella finestra di modifica del sottoinsieme, seleziona l’opzione **[!UICONTROL Limit the selected records]** e fai clic sul collegamento **[!UICONTROL Edit...]** .
1. Seleziona il tipo di limite desiderato:

   * **[!UICONTROL Activate random sampling]**: questa opzione consente di prelevare un campione casuale dei record. Il tipo di campionamento casuale applicato dipende dal motore del database.
   * **[!UICONTROL Keep only the first records after sorting]**: questa opzione ti consente di definire un limite basato su uno o più ordini di ordinamento. Se selezioni il campo **[!UICONTROL Age]** come criterio di ordinamento e 100 come limite, mantieni solo i 100 destinatari più giovani.
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**: Questa opzione combina le due opzioni precedenti. Consente di definire un limite basato su uno o più ordini di ordinamento e quindi di applicare una selezione casuale sui primi record se alcuni di essi hanno gli stessi valori dei criteri definiti.

      Ad esempio, se selezioni il campo **[!UICONTROL Age]** come criterio di ordinamento e poi definisci un limite di 100, ma i 2000 destinatari più giovani nel database sono tutti 18, allora 100 destinatari verranno selezionati in modo casuale tra i 2000.
   ![](assets/s_user_segmentation_partage_wz1.png)

1. Per definire i criteri di ordinamento, è disponibile un passaggio aggiuntivo che consente di definire le colonne e l’ordine di ordinamento.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. Quindi scegli il metodo di limitazione dei dati.

   ![](assets/s_user_segmentation_partage_wz2.png)

   Ci sono diversi modi per farlo:

   * **[!UICONTROL Size (in %)]**: una percentuale di record. Ad esempio, la configurazione seguente estrae il 10% della popolazione totale.

      La percentuale si applica alla popolazione iniziale, non al risultato dell’attività.

   * **[!UICONTROL Size (as a % of the segment)]**: una percentuale di record relativi solo ai sottoinsiemi e non alla popolazione iniziale.
   * **[!UICONTROL Maximum size]**: un numero massimo di record.
   * **[!UICONTROL By data grouping]**: puoi impostare un limite al numero di record in base ai valori in un campo specifico del gruppo in entrata. Per ulteriori informazioni su questo argomento, consulta [Limitazione del numero di record di sottoinsiemi per raggruppamento di dati](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data grouping (in %)]**: puoi impostare un limite al numero di record in base ai valori in un campo specifico del gruppo in entrata utilizzando una percentuale. Per ulteriori informazioni su questo argomento, consulta [Limitazione del numero di record di sottoinsiemi per raggruppamento di dati](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data distribution]**: Se i campi di raggruppamento hanno troppi valori o se desideri evitare di immettere nuovamente i valori per ogni nuova attività di suddivisione, Adobe Campaign ti consente di configurare una  **[!UICONTROL By data distribution]** limitazione (modulo Distributed Marketing opzionale). Per ulteriori informazioni, consulta [Limitazione del numero di record di sottoinsiemi per distribuzione di dati](#limiting-the-number-of-subset-records-per-data-distribution).

1. Fai clic su **[!UICONTROL Finish]** per approvare i criteri di selezione dei record. La configurazione definita viene quindi visualizzata nella finestra centrale dell’editor.

## Limitazione del numero di record di sottoinsiemi per raggruppamento di dati {#limiting-the-number-of-subset-records-by-data-grouping}

Puoi limitare il numero di record in base al raggruppamento di dati. Questo limite può essere effettuato utilizzando un valore fisso o una percentuale.

Ad esempio, se selezioni il campo **[!UICONTROL Language]** come campo di gruppo, puoi definire un elenco di record per ogni lingua.

1. Dopo aver selezionato i valori di limitazione dei dati, selezionare **[!UICONTROL By data grouping]** o **[!UICONTROL By data grouping (as a %)]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. Quindi seleziona i campi di raggruppamento (ad esempio il campo **[!UICONTROL Language]**) e fai clic su **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. Infine, specifica le soglie di raggruppamento dei dati (utilizzando i valori fissi o le percentuali a seconda del metodo di raggruppamento selezionato in precedenza). Per impostare la stessa soglia per ogni valore, ad esempio se si desidera impostare su 10 il numero di record per ogni lingua, selezionare l&#39;opzione **[!UICONTROL All data groupings are the same size]**. Per impostare un limite diverso per ogni valore, seleziona l’opzione **[!UICONTROL Limitations by grouping value]** . Questo ti permetterà di scegliere una limitazione diversa per inglese, francese, ecc.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. Fai clic su **[!UICONTROL Finish]** per approvare il limite e tornare alla modifica dell’attività di suddivisione.

## Limitazione del numero di record di sottoinsiemi per distribuzione di dati {#limiting-the-number-of-subset-records-per-data-distribution}

Se i campi di raggruppamento contengono un numero eccessivo di valori o se desideri evitare di reimpostare valori per ogni nuova attività di suddivisione, Adobe Campaign ti consente di creare una limitazione per la distribuzione dei dati. Quando selezioni i valori di limitazione dei dati (per ulteriori informazioni sull&#39;oggetto consulta la sezione [Creazione di sottoinsiemi](#creating-subsets) ), seleziona l&#39;opzione **[!UICONTROL By data distribution]** e seleziona un modello dal menu a discesa. La creazione di un modello di distribuzione dei dati è illustrata di seguito.

Per un esempio dell&#39;attività **[!UICONTROL Local approval]** con un modello di distribuzione, fai riferimento a [Utilizzo dell&#39;attività di approvazione locale](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>Per utilizzare questa funzione, è necessario acquistare il modulo Marketing distribuito , che è un’opzione Campaign. Controlla il contratto di licenza.

Il modello di distribuzione dei dati ti consente di limitare il numero di record utilizzando un elenco di valori di raggruppamento. Per creare un modello di distribuzione dati, esegui i seguenti passaggi:

1. Per creare il modello di distribuzione dati, vai al nodo **[!UICONTROL Resources > Campaign management > Data distribution]** e fai clic su **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. La scheda **[!UICONTROL General]** ti consente di immettere l’etichetta e il contesto di esecuzione della distribuzione (dimensione di targeting, campo di distribuzione).

   ![](assets/local_validation_data_distribution_2.png)

   È necessario inserire i campi seguenti:

   * **[!UICONTROL Label]**: etichetta per il modello di distribuzione.
   * **[!UICONTROL Targeting dimension]**: immetti la dimensione di targeting a cui verrà applicata la distribuzione dei dati,  **[!UICONTROL Recipient]** ad esempio. Questo schema deve essere sempre compatibile con i dati utilizzati nel flusso di lavoro di targeting.
   * **[!UICONTROL Distribution field]**: seleziona un campo tramite la dimensione di targeting. Ad esempio, se selezioni il campo **[!UICONTROL Email domain]** , l’elenco dei destinatari verrà suddiviso per dominio.
   * **[!UICONTROL Distribution type]**: seleziona la modalità di suddivisione del valore di limitazione del target nella  **[!UICONTROL Distribution]** scheda :  **[!UICONTROL Percentage]** o  **[!UICONTROL Set]**.
   * **[!UICONTROL Assignment type]**: selezionare il tipo di assegnazione distribuzione dati. È possibile scegliere tra assegnazione per gruppo o operatore o assegnazione per entità locale. L&#39;assegnazione per entità locale viene utilizzata in **Marketing distribuito**. Per ulteriori informazioni, consulta questa [sezione](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**: se utilizzi un’ **[!UICONTROL Local approval]** attività nel flusso di lavoro di targeting (consulta Approvazione  [locale](local-approval.md)), immetti lo schema in cui verranno memorizzati i risultati dell’approvazione. È necessario specificare uno schema di archiviazione per schema di targeting. Se utilizzi lo schema di targeting **[!UICONTROL Recipients]**, immetti lo schema di archiviazione **[!UICONTROL Local approval of recipients]** predefinito.

      In caso di una semplice limitazione tramite raggruppamento di dati senza approvazione locale, non è necessario inserire il campo **[!UICONTROL Approvals storage]** .

1. Se utilizzi un&#39;attività **[!UICONTROL Local approval]** (consulta [Approvazione locale](local-approval.md)), immetti il **[!UICONTROL Advanced settings]** per il modello di distribuzione:

   ![](assets/local_validation_data_distribution_3.png)

   È necessario inserire i campi seguenti:

   * **[!UICONTROL Approve targeted messages]**: seleziona questa opzione se desideri che tutti i destinatari siano preselezionati dall’elenco dei destinatari da approvare. Se questa opzione è deselezionata, nessun destinatario sarà preselezionato.

      >[!NOTE]
      >
      >Questa opzione è selezionata per impostazione predefinita.

      ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**: ti consente di definire un’espressione per visualizzare l’etichetta di consegna nella notifica di ritorno. L’espressione predefinita fornisce informazioni sull’etichetta standard della consegna (stringa di calcolo). Puoi modificare questa espressione.

      ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**: questo campo ti consente di definire il raggruppamento utilizzato per visualizzare i destinatari nelle notifiche di approvazione e di ritorno.

      ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**: consente di collegare un’applicazione web all’elenco dei destinatari. Nella notifica di approvazione e di ritorno, ogni destinatario sarà cliccabile e si collegherà all&#39;applicazione web selezionata. Il campo **[!UICONTROL Parameters]** (ad esempio **[!UICONTROL recipientId]**) consente di configurare il parametro aggiuntivo da utilizzare nell’URL e nell’applicazione web.

      ![](assets/local_validation_notification_5.png)

1. La scheda **[!UICONTROL Breakdown]** ti consente di definire l’elenco dei valori di distribuzione.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: immettere i valori di distribuzione.
   * **[!UICONTROL Percentage / Set]**: inserire il limite record (fisso o percentuale) collegato a ciascun valore.

      Questa colonna è definita dal campo **[!UICONTROL Distribution type]** all’interno della scheda **[!UICONTROL General]** .

   * **[!UICONTROL Label]**: immetti l’etichetta collegata a ciascun valore.
   * **[!UICONTROL Group or operator]**: se utilizzi un’ **[!UICONTROL Local approval]** attività (consulta Approvazione  [locale](local-approval.md)), seleziona l’operatore o il gruppo di operatori assegnati a ciascun valore di distribuzione.

      In caso di una semplice limitazione tramite raggruppamento di dati senza approvazione locale, non è necessario inserire il campo **[!UICONTROL Group or operator]** .

      >[!IMPORTANT]
      >
      >Assicurati che agli operatori siano stati assegnati i diritti appropriati.

   * **[!UICONTROL Local entity]**: selezionare l&#39;entità locale assegnata a ciascun valore di distribuzione. Le entità locali vengono utilizzate in **Marketing distribuito**. Per ulteriori informazioni, consulta questa [sezione](../../distributed/using/about-distributed-marketing.md).

## Parametri di filtro {#filtering-parameters}

Fai clic sulla scheda **[!UICONTROL General]** per immettere l’etichetta dell’attività. Seleziona le dimensioni di destinazione e di filtro per la suddivisione. Se necessario, potete modificare queste dimensioni per un dato sottoinsieme.

![](assets/s_user_segmentation_partage_general.png)

Se desideri sfruttare la popolazione rimanente, seleziona l’opzione **[!UICONTROL Generate complement]** . Il complemento è il target in entrata meno l’unione dei sottoinsiemi. All’attività verrà quindi aggiunta una transizione in uscita aggiuntiva, come segue:

![](assets/s_user_segmentation_partage_compl.png)

Affinché questa opzione funzioni correttamente, i dati in entrata devono avere una chiave primaria.

Ad esempio, se i dati vengono letti direttamente da un database esterno come Netezza (che non supporta la nozione di indice) tramite un&#39;attività **[!UICONTROL Data loading (RDBMS)]**, il complemento generato dall&#39;attività **[!UICONTROL Split]** non sarà corretto.

Per evitare questo problema, puoi trascinare e rilasciare un’attività **[!UICONTROL Enrichment]** immediatamente prima dell’attività **[!UICONTROL Split]** . Nell’attività **[!UICONTROL Enrichment]** , seleziona **[!UICONTROL Keep all additional data from the main set]** e specifica nei dati aggiuntivi le colonne da utilizzare per configurare i filtri dell’attività **[!UICONTROL Split]**. I dati della transizione in entrata dell’attività **[!UICONTROL Split]** vengono quindi memorizzati localmente in una tabella temporanea sul server Adobe Campaign e il complemento può essere generato correttamente.

L’opzione **[!UICONTROL Enable overlapping of output populations]** consente di gestire le popolazioni appartenenti a diversi sottoinsiemi:

* Quando la casella non è selezionata, l’attività di suddivisione impedisce a un destinatario di essere presente in diverse transizioni di output, anche se soddisfa i criteri di diversi sottoinsiemi. Saranno nel target della prima scheda con criteri corrispondenti.
* Quando la casella è selezionata, i destinatari possono essere trovati in diversi sottoinsiemi se soddisfano i criteri di filtro. Adobe Campaign consiglia di utilizzare criteri esclusivi.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall’esclusione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificatori di destinazione,  **[!UICONTROL schema]** è lo schema del gruppo (in genere nms:recipient) ed  **[!UICONTROL recCount]** è il numero di elementi della tabella.

La transizione associata al complemento ha gli stessi parametri.
