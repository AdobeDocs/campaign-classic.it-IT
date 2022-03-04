---
product: campaign
title: Deduplica
description: Ulteriori informazioni sull’attività del flusso di lavoro Deduplication
feature: Workflows, Targeting Activity
exl-id: 38add4fe-6238-45de-863e-895ebca189b7
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 10%

---

# Deduplica{#deduplication}

![](../../assets/common.svg)

La deduplicazione elimina i duplicati dai risultati delle attività in entrata. È possibile eseguire la deduplicazione sull&#39;indirizzo e-mail, sul numero di telefono o su un altro campo.

La **[!UICONTROL Deduplication]** viene utilizzata per rimuovere righe duplicate da un set di dati. Ad esempio, i record seguenti potrebbero essere considerati duplicati in quanto hanno lo stesso indirizzo e-mail e lo stesso telefono cellulare e/o domestico.

| Data ultima modifica | Nome | Cognome | E-mail | Telefono cellulare | Telefono |
-----|------------|-----------|-------|--------------|------
| 03/02/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

La **[!UICONTROL Deduplication]** l’attività ha la capacità di mantenere un’intera riga come record univoco dopo l’identificazione dei duplicati. Ad esempio, nel caso d’uso precedente, se l’attività è configurata per mantenere solo il record con il record più vecchio **[!UICONTROL Date]**, il risultato sarebbe:

| Data | Nome | Cognome | E-mail | Telefono cellulare | Telefono |
-----|----------|------------|-------|--------------|------
| 03/02/2020 | Bob | Tisner | bob@mycompany.com | 444-444-4444 | 888-888-8888 |

Il record principale selezionato riporterà i dati senza alcuna unione dei dati di campo con altri dati pertinenti nelle righe duplicate.

Complemento:

| Data | Nome | Cognome | E-mail | Telefono cellulare | Telefono |
-----|------------|-----------|-------|--------------|------
| 19/05/2020 | Robert | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |
| 22/07/2020 | Bobby | Tisner | bob@mycompany.com | 444-444-4444 | 777-777-7777 |

## Best practice {#best-practices}

Durante la deduplicazione, i flussi in entrata vengono elaborati separatamente. Se ad esempio il destinatario A si trova nel risultato della query 1 e nel risultato della query 2, non verrà deduplicato.

Questo problema deve essere affrontato come segue:

* Crea un **Union** per unificare ogni flusso in entrata.
* Crea un **Deduplication** dopo **Union** attività.

![](assets/dedup_bonnepratique.png)

## Configurazione {#configuration}

Per configurare una deduplicazione, immetti la relativa etichetta, il metodo e i criteri di deduplicazione, nonché le opzioni relative al risultato.

1. Fai clic sul pulsante **[!UICONTROL Edit configuration...]** collegamento per definire la modalità di deduplicazione.

   ![](assets/s_user_segmentation_dedup_param.png)

1. Seleziona il tipo di target per questa attività (per impostazione predefinita, la deduplicazione è collegata ai destinatari) e il criterio da utilizzare, ovvero il campo per il quale valori identici ti consentono di identificare i duplicati.

   >[!NOTE]
   >
   >Se utilizzi dati esterni come input, ad esempio da un file esterno, assicurati di selezionare il **[!UICONTROL Temporary schema]** opzione .
   >
   >Nel passaggio successivo, la **[!UICONTROL Other]** consente di selezionare il criterio o i criteri da utilizzare:

   ![](assets/s_user_segmentation_dedup_param2.png)

1. Nel passaggio successivo, la **[!UICONTROL Other]** consente di selezionare il criterio o i criteri da utilizzare in caso di valori identici.

   ![](assets/s_user_segmentation_dedup_param3.png)

1. Dall’elenco a discesa, seleziona il metodo di deduplicazione da utilizzare e immetti il numero di duplicati da mantenere.

   ![](assets/s_user_segmentation_dedup_param4.png)

   Sono disponibili i seguenti metodi:

   * **[!UICONTROL Choose for me]**: seleziona in modo casuale il record da escludere dai duplicati.
   * **[!UICONTROL Following a list of values]**: ti consente di definire un valore di priorità per uno o più campi. Per definire i valori, seleziona un campo o crea un’espressione, quindi aggiungi i valori nella tabella appropriata. Per definire un nuovo campo, fai clic sul pulsante **[!UICONTROL Add]** situato sopra l’elenco dei valori.

      ![](assets/s_user_segmentation_dedup_param5.png)

   * **[!UICONTROL Non-empty value]**: questo ti consente di conservare i record per i quali il valore dell’espressione selezionata non è vuoto come priorità.

      ![](assets/s_user_segmentation_dedup_param6.png)

   * **[!UICONTROL Using an expression]**: consente di conservare i record con il valore più basso (o più alto) dell’espressione specificata.

      ![](assets/s_user_segmentation_dedup_param7.png)
   >[!NOTE]
   >
   >La **[!UICONTROL Merge]** accessibile tramite **[!UICONTROL Advanced parameters]** link, ti consente di configurare un set di regole per unire un campo o un gruppo di campi in un unico record di dati risultante. Per ulteriori informazioni, consulta [Unione dei campi in un singolo record](#merging-fields-into-single-record).

1. Fai clic su **[!UICONTROL Finish]** per approvare il metodo di deduplicazione selezionato.

   La sezione centrale della finestra riepiloga la configurazione definita.

   Nella sezione inferiore della finestra dell’editor attività, puoi modificare l’etichetta per la transizione in uscita dell’oggetto grafico e immettere un codice di segmento che sarà associato al risultato dell’attività. Questo codice può in seguito essere utilizzato come criterio di targeting.

   ![](assets/s_user_segmentation_dedup_param8.png)

1. Controlla la **[!UICONTROL Generate complement]** se desideri sfruttare la popolazione rimanente. Il complemento è costituito da tutti i duplicati. All’attività verrà quindi aggiunta una transizione aggiuntiva, come segue:

   ![](assets/s_user_segmentation_dedup_param9.png)

## Esempio: Identificare i duplicati prima di una consegna {#example--identify-the-duplicates-before-a-delivery}

Nell’esempio seguente, la deduplicazione riguarda l’unione di tre query.

Lo scopo del flusso di lavoro è quello di definire il target per una consegna escludendo i duplicati per evitare di inviarlo più volte allo stesso destinatario.

I duplicati identificati saranno inoltre integrati in un elenco di duplicati dedicati che potrà essere riutilizzato se necessario.

![](assets/deduplication_example.png)

1. Aggiungi e collega le varie attività necessarie per il funzionamento del flusso di lavoro come mostrato sopra.

   L’attività di unione viene utilizzata qui per &quot;unificare&quot; le tre query in un’unica transizione. Pertanto, la deduplicazione non funzionerà per ogni query singolarmente ma per l’intera query. Per ulteriori informazioni su questo argomento, consulta [Best practice](#best-practices).

1. Apri l’attività di deduplicazione, quindi fai clic su **[!UICONTROL Edit configuration...]** collegamento per definire la modalità di deduplicazione.
1. Nella nuova finestra, seleziona **[!UICONTROL Database schema]**.
1. Seleziona **Destinatari** come dimensioni di targeting e filtro.
1. Seleziona il campo ID per la **[!UICONTROL Email]** duplica, per inviare la consegna una sola volta a ogni indirizzo e-mail, quindi fai clic su **[!UICONTROL Next]**.

   Se desideri basare gli ID duplicati su un campo specifico, seleziona **[!UICONTROL Other]** per accedere all’elenco dei campi disponibili.

1. Scegli di mantenere una sola voce quando lo stesso indirizzo e-mail viene identificato per più destinatari.
1. Seleziona la **[!UICONTROL Choose for me]** modalità di deduplicazione in modo che i record salvati in caso di duplicati identificati siano scelti in modo casuale, quindi fare clic su **[!UICONTROL Finish]**.

Durante l’esecuzione del flusso di lavoro, tutti i destinatari identificati come duplicati vengono esclusi dal risultato (e quindi dalla consegna) e aggiunti all’elenco dei duplicati. Questo elenco può essere utilizzato di nuovo anziché dover reidentificare i duplicati.

## Unione dei campi in un singolo record di dati {#merging-fields-into-single-record}

La **[!UICONTROL Merge]** La funzionalità ti consente di configurare un set di regole per la deduplicazione per definire un campo o un gruppo di campi da unire in un singolo record di dati risultante.

Ad esempio, con un set di record duplicati, puoi scegliere di mantenere il numero di telefono più vecchio o il nome più recente.

È disponibile un caso d’uso che sfrutta questa funzione in [questa sezione](deduplication-merge.md).

Per farlo, esegui questi passaggi:

1. In **[!UICONTROL Deduplication method]** passaggio di selezione, fai clic sul **[!UICONTROL Advanced Parameters]** link.

   ![](assets/dedup1.png)

1. Seleziona la **[!UICONTROL Merge records]** per attivare la funzionalità.

   Se desideri raggruppare più campi di dati in ciascuna condizione di unione, attiva la **[!UICONTROL Use several record merging criteria]** opzione .

   ![](assets/dedup2.png)

1. Dopo aver attivato la funzionalità, un **[!UICONTROL Merge]** viene aggiunta alla scheda **[!UICONTROL Deduplication]** attività. Consente di definire gruppi di campi da unire e le relative regole associate.

   Per ulteriori informazioni, consulta il caso d’uso dedicato disponibile in [questa sezione](deduplication-merge.md).

   ![](assets/dedup3.png)

## Parametri di input {#input-parameters}

* tableName
* schema

Ogni evento in entrata deve specificare un target definito da questi parametri.

## Parametri di output {#output-parameters}

* tableName
* schema
* recCount

Questo insieme di tre valori identifica il target risultante dalla deduplicazione. **[!UICONTROL tableName]** è il nome della tabella che salva gli identificatori target, **[!UICONTROL schema]** è lo schema della popolazione (in genere nms:recipient) e **[!UICONTROL recCount]** è il numero di elementi nella tabella.

La transizione associata al complemento ha gli stessi parametri.
