---
product: campaign
title: Dividi
description: Ulteriori informazioni sull’attività Dividi flusso di lavoro
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Targeting Activity
exl-id: 4204350a-c2d2-4033-9bdf-87b49d8211b9
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1953'
ht-degree: 0%

---

# Dividi{#split}



A **Dividi** L’attività di tipo -type consente di suddividere un target in diversi sottoinsiemi. Il target viene costruito con tutti i risultati ricevuti: affinché questa attività possa essere eseguita, tutte le attività precedenti devono essere state completate.

Questa attività non attiva un’unione di popolazioni in entrata. Se nell’ambito di un’attività divisa si verificano più transizioni, si consiglia di inserire un’ **[!UICONTROL Union]** attività di fronte a esso.

Per un esempio dell’attività divisa in uso, fai riferimento a [Creazione di sottoinsiemi tramite l’attività Dividi](targeting-data.md#creating-subsets-using-the-split-activity).

Un esempio che illustra come utilizzare l’attività Split per segmentare il target in popolazioni diverse utilizzando condizioni di filtro è descritto in [questa sezione](cross-channel-delivery-workflow.md).

Un esempio che mostra come utilizzare una variabile di istanza in un’attività Split è disponibile in [questa sezione](javascript-scripts-and-templates.md).

Per configurare questa attività, definisci il contenuto e l’etichetta del sottoinsieme in **[!UICONTROL Subsets]** , quindi scegliere la dimensione di destinazione nella scheda **[!UICONTROL General]** scheda.

## Creazione di sottoinsiemi {#creating-subsets}

Per creare un sottoinsieme:

1. Fai clic sull’etichetta nel campo corrispondente e seleziona il filtro da applicare.
1. Per filtrare il gruppo in entrata, seleziona la **[!UICONTROL Add a filtering condition]** e fare clic sul pulsante **[!UICONTROL Edit...]** collegamento.

   Selezionare il tipo di filtro da applicare ai dati da includere nel set.

   Il processo è lo stesso di un **Query** attività di tipo.

   >[!NOTE]
   >
   >Puoi filtrare i dati in un massimo di due database esterni (FDA).

1. È possibile specificare il numero massimo di record da estrarre dalla destinazione per creare il sottoinsieme. A questo scopo, seleziona la **[!UICONTROL Limit the selected records]** e fare clic sul pulsante **[!UICONTROL Edit...]** collegamento.

   Una procedura guidata consente di scegliere la modalità di selezione per i record di questo sottoinsieme. I passaggi si trovano in [Limitazione del numero di record del sottoinsieme](#limiting-the-number-of-subset-records).

   ![](assets/s_user_segmentation_partage4.png)

1. Se lo desideri, puoi **aggiungi altri sottoinsiemi** utilizzando **[!UICONTROL Add]** pulsante.

   ![](assets/s_user_segmentation_partage_add.png)

   >[!NOTE]
   >
   >Se il **[!UICONTROL Enable overlapping of output populations]** L&#39;opzione non è selezionata, i sottoinsiemi vengono creati nell&#39;ordine delle schede. Utilizzare le frecce nella parte superiore destra della finestra per spostarle. Se, ad esempio, il primo sottoinsieme recupera il 70% della popolazione iniziale, il sottoinsieme successivo applicherà i propri criteri di selezione solo al restante 30% e così via.

   Per ogni sottoinsieme creato, all’attività divisa verrà aggiunta una transizione in uscita.

   ![](assets/s_user_segmentation_partage_add2.png)

   Puoi scegliere di generare una singola transizione in uscita (e identificare i set utilizzando, ad esempio, il codice di segmento): a questo scopo, seleziona la **[!UICONTROL Generate subsets in the same table]** opzione in **[!UICONTROL General]** scheda.

   Se è completato, il codice del segmento di ciascun sottoinsieme viene memorizzato automaticamente in una colonna aggiuntiva. Questa colonna sarà accessibile nei campi di personalizzazione a livello di consegna.

## Limitazione del numero di record del sottoinsieme {#limiting-the-number-of-subset-records}

Se non si desidera utilizzare l&#39;intera popolazione contenuta in un sottoinsieme, è possibile limitare il numero di record in esso contenuti.

1. Nella finestra di modifica del sottoinsieme, selezionare **[!UICONTROL Limit the selected records]** e fare clic sul pulsante **[!UICONTROL Edit...]** collegamento.
1. Selezionare il tipo di limite desiderato:

   * **[!UICONTROL Activate random sampling]**: questa opzione accetta un campione casuale dei record. Il tipo di campionamento casuale applicato dipende dal motore del database.
   * **[!UICONTROL Keep only the first records after sorting]**: questa opzione consente di definire un limite basato su uno o più ordini di ordinamento. Se si seleziona la **[!UICONTROL Age]** come criterio di ordinamento e 100 come limite, verranno mantenuti solo i 100 destinatari più giovani.
   * **[!UICONTROL Keep the first ones after sorting (criteria, random)]**: questa opzione combina le due opzioni precedenti. Consente di definire un limite basato su uno o più criteri di ordinamento e quindi di applicare una selezione casuale ai primi record se alcuni di essi hanno gli stessi valori dei criteri definiti.

     Ad esempio, se selezioni il **[!UICONTROL Age]** come criterio di ordinamento, si definisce quindi un limite di 100, ma i 2.000 destinatari più giovani nel database sono tutti 18, quindi verranno selezionati in modo casuale 100 di questi 2.000.

   ![](assets/s_user_segmentation_partage_wz1.png)

1. Se si desidera definire i criteri di ordinamento, è possibile definire le colonne e l&#39;ordine di ordinamento in un passaggio aggiuntivo.

   ![](assets/s_user_segmentation_partage_wz1.1.png)

1. Quindi scegli il metodo di limitazione dei dati.

   ![](assets/s_user_segmentation_partage_wz2.png)

   Esistono diversi modi per farlo:

   * **[!UICONTROL Size (in %)]**: una percentuale di record. Ad esempio, la configurazione seguente estrae il 10% della popolazione totale.

     La percentuale si applica alla popolazione iniziale, non al risultato dell’attività.

   * **[!UICONTROL Size (as a % of the segment)]**: una percentuale di record relativi solo ai sottoinsiemi e non alla popolazione iniziale.
   * **[!UICONTROL Maximum size]**: numero massimo di record.
   * **[!UICONTROL By data grouping]**: puoi impostare un limite al numero di record in base ai valori in un campo specifico del gruppo in entrata. Per ulteriori informazioni su questo argomento, consulta [Limitazione del numero di record di sottoinsiemi per raggruppamento di dati](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data grouping (in %)]**: puoi impostare un limite al numero di record in base ai valori in un campo specifico del gruppo in entrata utilizzando una percentuale. Per ulteriori informazioni su questo argomento, consulta [Limitazione del numero di record di sottoinsiemi per raggruppamento di dati](#limiting-the-number-of-subset-records-by-data-grouping).
   * **[!UICONTROL By data distribution]**: se i campi di raggruppamento hanno troppi valori o se desideri evitare di immetterli nuovamente per ogni nuova attività di suddivisione, Adobe Campaign ti consente di configurare un’ **[!UICONTROL By data distribution]** limitazione (modulo facoltativo di Marketing distribuito). Per ulteriori informazioni, consulta [Limitazione del numero di record di sottoinsiemi per distribuzione dei dati](#limiting-the-number-of-subset-records-per-data-distribution).

1. Clic **[!UICONTROL Finish]** per approvare i criteri di selezione dei record. La configurazione definita viene quindi visualizzata nella finestra centrale dell’editor.

## Limitazione del numero di record di sottoinsiemi per raggruppamento di dati {#limiting-the-number-of-subset-records-by-data-grouping}

È possibile limitare il numero di record per raggruppamento di dati. Questo limite può essere applicato utilizzando un valore fisso o una percentuale.

Ad esempio, se selezioni il **[!UICONTROL Language]** come campo di gruppo, è possibile definire un elenco di record per ogni lingua.

1. Dopo aver selezionato i valori di limitazione dei dati, seleziona **[!UICONTROL By data grouping]** o **[!UICONTROL By data grouping (as a %)]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz3.png)

1. Quindi seleziona i campi di raggruppamento (il **[!UICONTROL Language]** ad esempio) e fare clic su **[!UICONTROL Next]**.

   ![](assets/s_user_segmentation_partage_wz4.png)

1. Infine, specifica le soglie di raggruppamento dei dati (utilizzando valori fissi o percentuali a seconda del metodo di raggruppamento selezionato in precedenza). Per impostare la stessa soglia per ogni valore, ad esempio se si desidera impostare su 10 il numero di record per ogni lingua, selezionare **[!UICONTROL All data groupings are the same size]** opzione. Per impostare un limite diverso per ogni valore, selezionare **[!UICONTROL Limitations by grouping value]** opzione. Questo ti consentirà di scegliere un limite diverso per inglese, francese, ecc.

   ![](assets/s_user_segmentation_partage_wz5.png)

1. Clic **[!UICONTROL Finish]** per approvare la limitazione e tornare a modificare l’attività divisa.

## Limitazione del numero di record di sottoinsiemi per distribuzione dei dati {#limiting-the-number-of-subset-records-per-data-distribution}

Se i campi di raggruppamento contengono un numero eccessivo di valori o se desideri evitare di reimpostare i valori per ogni nuova attività di suddivisione, Adobe Campaign ti consente di creare un limite per la distribuzione dei dati. Quando selezioni i valori di limitazione dei dati (per ulteriori informazioni su questo argomento consulta la [Creazione di sottoinsiemi](#creating-subsets) sezione ), seleziona la **[!UICONTROL By data distribution]** e selezionare un modello dal menu a discesa. La creazione di un modello di distribuzione dei dati è illustrata di seguito.

Per un esempio di **[!UICONTROL Local approval]** con un modello di distribuzione, fare riferimento a [Utilizzo dell’attività di approvazione locale](using-the-local-approval-activity.md).

![](assets/s_user_segmentation_partage_wz6.png)

>[!IMPORTANT]
>
>Per utilizzare questa funzione, devi acquistare il modulo Marketing distribuito, che è un’opzione di Campaign. Controlla il contratto di licenza.

Il modello di distribuzione dati consente di limitare il numero di record utilizzando un elenco di valori di raggruppamento. Per creare un modello di distribuzione dati, attieniti alla seguente procedura:

1. Per creare il modello di distribuzione dei dati, passare alla **[!UICONTROL Resources > Campaign management > Data distribution]** e fai clic su **[!UICONTROL New]**.

   ![](assets/local_validation_data_distribution_1.png)

1. Il **[!UICONTROL General]** Questa scheda ti consente di immettere l’etichetta e il contesto di esecuzione della distribuzione (dimensione di targeting, campo di distribuzione).

   ![](assets/local_validation_data_distribution_2.png)

   È necessario inserire i campi seguenti:

   * **[!UICONTROL Label]**: etichetta per il modello di distribuzione.
   * **[!UICONTROL Targeting dimension]**: inserisci la dimensione di targeting a cui verrà applicata la distribuzione dei dati, **[!UICONTROL Recipient]** ad esempio. Questo schema deve sempre essere compatibile con i dati utilizzati nel flusso di lavoro di targeting.
   * **[!UICONTROL Distribution field]**: seleziona un campo tramite la dimensione di targeting. Ad esempio, se selezioni il **[!UICONTROL Email domain]** l&#39;elenco dei destinatari verrà suddiviso per dominio.
   * **[!UICONTROL Distribution type]**: seleziona il modo in cui il valore di limitazione del target verrà suddiviso nel **[!UICONTROL Distribution]** scheda: **[!UICONTROL Percentage]** o **[!UICONTROL Set]**.
   * **[!UICONTROL Assignment type]**: seleziona il tipo di assegnazione della distribuzione dati. È possibile scegliere tra l&#39;assegnazione per gruppo o operatore o l&#39;assegnazione per entità locale. L’assegnazione per entità locale viene utilizzata in **Marketing distribuito**. Per ulteriori informazioni, consulta questa [sezione](../../distributed/using/about-distributed-marketing.md).
   * **[!UICONTROL Approval storage]**: se utilizzi un’ **[!UICONTROL Local approval]** attività nel flusso di lavoro di targeting (consulta [Approvazione locale](local-approval.md)), inserisci lo schema in cui verranno memorizzati i risultati dell&#39;approvazione. È necessario specificare uno schema di archiviazione per ogni schema di destinazione. Se si utilizza **[!UICONTROL Recipients]** schema di targeting, immetti il valore predefinito **[!UICONTROL Local approval of recipients]** schema di archiviazione.

     In caso di una semplice limitazione per raggruppamento di dati senza approvazione locale, non è necessario immettere **[!UICONTROL Approvals storage]** campo.

1. Se si utilizza un **[!UICONTROL Local approval]** attività (fare riferimento a [Approvazione locale](local-approval.md)), immetti il **[!UICONTROL Advanced settings]** per il modello di distribuzione:

   ![](assets/local_validation_data_distribution_3.png)

   È necessario inserire i campi seguenti:

   * **[!UICONTROL Approve targeted messages]**: seleziona questa opzione se desideri che tutti i destinatari siano preselezionati dall’elenco di destinatari da approvare. Se questa opzione è deselezionata, nessun destinatario sarà preselezionato.

     >[!NOTE]
     >
     >Questa opzione è selezionata per impostazione predefinita.

     ![](assets/local_validation_notification.png)

   * **[!UICONTROL Delivery label]**: ti consente di definire un’espressione per visualizzare l’etichetta di consegna nella notifica di ritorno. L’espressione predefinita fornisce informazioni sull’etichetta standard della consegna (stringa di calcolo). È possibile modificare questa espressione.

     ![](assets/local_validation_notification_3.png)

   * **[!UICONTROL Grouping field]**: questo campo ti consente di definire il raggruppamento utilizzato per visualizzare i destinatari nelle notifiche di approvazione e di ritorno.

     ![](assets/local_validation_notification_4.png)

   * **[!UICONTROL Web Interface]**: consente di collegare un’applicazione web all’elenco dei destinatari. Nella notifica di approvazione e di ritorno, ogni destinatario sarà cliccabile e si collegherà all’applicazione web selezionata. Il **[!UICONTROL Parameters]** campo (ad esempio **[!UICONTROL recipientId]**) consente di configurare il parametro aggiuntivo da utilizzare nell’URL e nell’applicazione web.

     ![](assets/local_validation_notification_5.png)

1. Il **[!UICONTROL Breakdown]** Questa scheda ti consente di definire l’elenco dei valori di distribuzione.

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**: inserisci i valori di distribuzione.
   * **[!UICONTROL Percentage / Set]**: inserisci il limite del record (fisso o percentuale) collegato a ciascun valore.

     Questa colonna è definita da **[!UICONTROL Distribution type]** campo all&#39;interno del **[!UICONTROL General]** scheda.

   * **[!UICONTROL Label]**: inserisci l’etichetta collegata a ciascun valore.
   * **[!UICONTROL Group or operator]**: se utilizzi una **[!UICONTROL Local approval]** attività (fare riferimento a [Approvazione locale](local-approval.md)), seleziona l’operatore o il gruppo di operatori assegnati a ciascun valore di distribuzione.

     In caso di una semplice limitazione per raggruppamento di dati senza approvazione locale, non è necessario immettere **[!UICONTROL Group or operator]** campo.

     >[!IMPORTANT]
     >
     >Assicurati che agli operatori siano stati assegnati i diritti appropriati.

   * **[!UICONTROL Local entity]**: seleziona l’entità locale assegnata a ciascun valore di distribuzione. Le entità locali vengono utilizzate in **Marketing distribuito**. Per ulteriori informazioni, consulta questa [sezione](../../distributed/using/about-distributed-marketing.md).

## Parametri di filtro {#filtering-parameters}

Fai clic su **[!UICONTROL General]** per inserire l’etichetta dell’attività. Selezionare le dimensioni di destinazione e filtro per la suddivisione. Se necessario, potete modificare queste dimensioni per un determinato sottoinsieme.

![](assets/s_user_segmentation_partage_general.png)

Controlla la **[!UICONTROL Generate complement]** se desideri sfruttare il gruppo rimanente. Il complemento è il target in entrata meno l’unione dei sottoinsiemi. Verrà quindi aggiunta all’attività un’ulteriore transizione in uscita, come segue:

![](assets/s_user_segmentation_partage_compl.png)

Affinché questa opzione funzioni correttamente, i dati in entrata devono avere una chiave primaria.

Ad esempio, se i dati vengono letti direttamente da un database esterno come Netezza (che non supporta la nozione di indice) tramite un **[!UICONTROL Data loading (RDBMS)]** attività, il complemento generato dalla **[!UICONTROL Split]** l&#39;attività non sarà corretta.

Per evitare questo problema, puoi trascinare e rilasciare una **[!UICONTROL Enrichment]** attività subito prima del **[!UICONTROL Split]** attività. In **[!UICONTROL Enrichment]** attività, controlla **[!UICONTROL Keep all additional data from the main set]** e specificare nei dati aggiuntivi le colonne da utilizzare per la configurazione dei filtri del **[!UICONTROL Split]** attività. I dati della transizione in entrata del **[!UICONTROL Split]** Le attività vengono quindi memorizzate localmente in una tabella temporanea sul server Adobe Campaign e il complemento può essere generato correttamente.

Il **[!UICONTROL Enable overlapping of output populations]** consente di gestire le popolazioni appartenenti a diversi sottoinsiemi:

* Quando la casella non è selezionata, l’attività di suddivisione si assicura che un destinatario non possa essere presente in diverse transizioni di output, anche se soddisfa i criteri di diversi sottoinsiemi. Saranno nel target della prima scheda con criteri corrispondenti.
* Quando la casella è selezionata, i destinatari possono essere trovati in diversi sottoinsiemi se soddisfano i propri criteri di filtro. Adobe Campaign consiglia di utilizzare criteri esclusivi.

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare una destinazione definita da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dall’esclusione. **[!UICONTROL tableName]** è il nome della tabella che registra gli identificativi target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.
