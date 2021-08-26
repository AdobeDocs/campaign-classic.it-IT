---
product: campaign
title: Arricchimento dei dati
description: Ulteriori informazioni sull’attività del flusso di lavoro Arricchimento
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# Arricchimento dei dati{#enriching-data}

![](../../assets/common.svg)

## Informazioni sull’arricchimento dei dati {#about-enriching-data}

Questo caso d’uso descrive i possibili utilizzi dell’attività **[!UICONTROL Enrichment]** in un flusso di lavoro di targeting. Per ulteriori informazioni sull&#39;utilizzo dell&#39;attività **[!UICONTROL Enrichment]**, consulta: [Arricchimento](enrichment.md).

Un caso d’uso su come arricchire una consegna e-mail con date personalizzate è disponibile anche in [questa sezione](email-enrichment-with-custom-date-fields.md).

I contatti nel database marketing vengono inviati un invito a partecipare a un concorso tramite un&#39;applicazione web. I risultati del concorso sono recuperati nella tabella **[!UICONTROL Competition results]**. Questa tabella è collegata alla tabella dei contatti (**[!UICONTROL Recipients]**). La tabella **[!UICONTROL Competition results]** contiene i campi seguenti:

* Nome della concorrenza (@game)
* Numero della prova (@prova)
* Punteggio (@punteggio)

![](assets/uc1_enrich_1.png)

Un contatto trovato nella tabella **[!UICONTROL Recipients]** può essere collegato a più righe nella tabella **[!UICONTROL Competition results]**. La relazione tra queste due tabelle è di tipo 1-n. Di seguito è riportato un esempio dei registri dei risultati per un destinatario:

![](assets/uc1_enrich_2.png)

Lo scopo di questo caso d’uso è quello di inviare consegne personalizzate a persone che hanno partecipato all’ultimo concorso a seconda dei punteggi più elevati ottenuti. Il destinatario con il punteggio più alto ottiene il primo premio, il destinatario con il secondo punteggio più alto ottiene un premio di consolazione e tutti gli altri ricevono un messaggio che augura loro migliore fortuna la prossima volta.

Per impostare questo caso d’uso, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/uc1_enrich_3.png)

Per creare il flusso di lavoro, esegui i seguenti passaggi:

1. Per eseguire il targeting dei nuovi abbonati che sono entrati per ultimi, vengono aggiunte due attività **[!UICONTROL Query]** e un’attività **[!UICONTROL Intersection]** .
1. L’attività **[!UICONTROL Enrichment]** ci consente di aggiungere i dati memorizzati nella tabella **[!UICONTROL Competition results]**. Il campo **[!UICONTROL Score]** sul quale avrà luogo la personalizzazione della consegna viene aggiunto alla tabella di lavoro del flusso di lavoro.
1. L’attività di tipo **[!UICONTROL Split]** ci consente di creare sottoinsiemi di destinatari in base ai punteggi.
1. Per ciascun sottoinsieme, viene aggiunta un’attività di tipo **[!UICONTROL Delivery]**.

## Passaggio 1: Targeting {#step-1--targeting}

La prima query consente di eseguire il targeting dei destinatari aggiunti al database negli ultimi sei mesi.

![](assets/uc1_enrich_4.png)

La seconda query consente di eseguire il targeting dei destinatari che hanno partecipato all’ultima gara.

![](assets/uc1_enrich_5.png)

Viene quindi aggiunta un’attività di tipo **[!UICONTROL Intersection]** per eseguire il targeting dei destinatari aggiunti al database negli ultimi sei mesi e che sono entrati nell’ultima concorrenza.

## Passaggio 2: Arricchimento {#step-2--enrichment}

In questo esempio, vogliamo personalizzare le consegne in base al campo **[!UICONTROL Score]** memorizzato nella tabella **[!UICONTROL Competition results]** . Questa tabella presenta una relazione di tipo 1-n con la tabella dei destinatari. L’attività **[!UICONTROL Enrichment]** ci consente di aggiungere dati da una tabella collegata alla dimensione di filtro alla tabella di lavoro del flusso di lavoro.

1. Nella schermata di modifica dell’attività di arricchimento, seleziona **[!UICONTROL Add data]**, quindi **[!UICONTROL Data linked to the filtering dimension]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. Quindi seleziona l’opzione **[!UICONTROL Data linked to the filtering dimension]**, seleziona la tabella **[!UICONTROL Competition results]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Immetti un ID e un’etichetta e seleziona l’opzione **[!UICONTROL Limit the line count]** nel campo **[!UICONTROL Data collected]** . Nel campo **[!UICONTROL Lines to retrieve]** , seleziona &quot;1&quot; come valore. Per ciascun destinatario, l’attività di arricchimento aggiunge una singola riga dalla tabella **[!UICONTROL Competition results]** alla tabella di lavoro del flusso di lavoro. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. In questo esempio, vogliamo recuperare il punteggio più alto del destinatario, ma solo per l&#39;ultima competizione. A questo scopo, aggiungi un filtro al campo **[!UICONTROL Competition name]** per escludere tutte le righe relative ai concorsi precedenti. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Vai alla schermata **[!UICONTROL Sort]** e fai clic sul pulsante **[!UICONTROL Add]** , seleziona il campo **[!UICONTROL Score]** e spunta la casella nella colonna **[!UICONTROL descending]** per ordinare in ordine decrescente gli elementi dei campi **[!UICONTROL Score]**. Per ogni destinatario, l’attività di arricchimento aggiunge una riga che corrisponde al punteggio più alto per l’ultimo gioco. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. Nella finestra **[!UICONTROL Data to add]** fare doppio clic sul campo **[!UICONTROL Score]**. Per ciascun destinatario, l’attività di arricchimento aggiungerà solo il campo **[!UICONTROL Score]** . Fai clic su **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Fai clic con il pulsante destro del mouse sulla transizione in entrata dell’attività di arricchimento e seleziona **[!UICONTROL Display the target]**. La tabella di lavoro contiene i dati seguenti:

![](assets/uc1_enrich_13.png)

Lo schema collegato è:

![](assets/uc1_enrich_15.png)

Rinnova questa operazione sulla transizione in uscita dell’attività di arricchimento. Notiamo che sono stati aggiunti i dati collegati ai punteggi dei destinatari. Il punteggio più alto di ciascun destinatario è stato recuperato.

![](assets/uc1_enrich_12.png)

Anche lo schema corrispondente è stato arricchito.

![](assets/uc1_enrich_14.png)

## Passaggio 3: Divisione e consegna {#step-3--split-and-delivery}

Per ordinare i destinatari in base ai loro punteggi, dopo l’arricchimento viene aggiunta un’attività **[!UICONTROL Split]** .

![](assets/uc1_enrich_18.png)

1. È stato definito un primo sottoinsieme (**Vincitore**) per includere il destinatario con il punteggio più alto. A questo scopo, definisci una limitazione del numero di record, applica un ordinamento decrescente al punteggio e limita il numero di record a 1.

   ![](assets/uc1_enrich_16.png)

1. Il secondo sottoinsieme (**Secondo posto**) include il destinatario con il secondo punteggio più alto. La configurazione è la stessa del primo sottoinsieme.

   ![](assets/uc1_enrich_17.png)

1. Il terzo sottoinsieme (**perdenti**) contiene tutti gli altri destinatari. Vai alla scheda **[!UICONTROL General]** e seleziona la casella **[!UICONTROL Generate complement]** per eseguire il targeting di tutti i destinatari che non hanno raggiunto i due punteggi più elevati.

   ![](assets/uc1_enrich_19.png)

1. Aggiungi un’attività di tipo **[!UICONTROL Delivery]** per ciascun sottoinsieme, utilizzando un modello di consegna diverso per ciascun sottoinsieme.

   ![](assets/uc1_enrich_20.png)
