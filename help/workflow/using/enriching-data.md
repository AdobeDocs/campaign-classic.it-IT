---
product: campaign
title: Arricchire i dati
description: Ulteriori informazioni sull’attività del flusso di lavoro Arricchimento
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Enrichment Activity
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# Arricchire i dati{#enriching-data}



## Informazioni sull’arricchimento dei dati {#about-enriching-data}

Questo caso d&#39;uso descrive gli usi possibili **[!UICONTROL Enrichment]** in un flusso di lavoro di targeting. Per ulteriori informazioni sull’utilizzo di **[!UICONTROL Enrichment]** attività, fai riferimento a: [Arricchimento](enrichment.md).

È disponibile anche un caso d’uso su come arricchire una consegna e-mail con date personalizzate in [questa sezione](email-enrichment-with-custom-date-fields.md).

I contatti nel database marketing vengono inviati un invito a partecipare a un concorso tramite un&#39;applicazione web. I risultati della concorrenza sono recuperati nella **[!UICONTROL Competition results]** tabella. Questa tabella è collegata alla tabella dei contatti (**[!UICONTROL Recipients]**). La **[!UICONTROL Competition results]** La tabella contiene i campi seguenti:

* Nome della concorrenza (@game)
* Numero della prova (@prova)
* Punteggio (@punteggio)

![](assets/uc1_enrich_1.png)

Un contatto trovato nel **[!UICONTROL Recipients]** può essere collegata a più righe nel **[!UICONTROL Competition results]** tabella. La relazione tra queste due tabelle è di tipo 1-n. Di seguito è riportato un esempio dei registri dei risultati per un destinatario:

![](assets/uc1_enrich_2.png)

Lo scopo di questo caso d’uso è quello di inviare consegne personalizzate a persone che hanno partecipato all’ultimo concorso a seconda dei punteggi più elevati ottenuti. Il destinatario con il punteggio più alto ottiene il primo premio, il destinatario con il secondo punteggio più alto ottiene un premio di consolazione e tutti gli altri ricevono un messaggio che augura loro migliore fortuna la prossima volta.

Per impostare questo caso d’uso, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/uc1_enrich_3.png)

Per creare il flusso di lavoro, esegui i seguenti passaggi:

1. Due **[!UICONTROL Query]** attività e una **[!UICONTROL Intersection]** vengono aggiunte le attività per eseguire il targeting dei nuovi abbonati che sono entrati per ultimi nel concorso.
1. La **[!UICONTROL Enrichment]** consente di aggiungere i dati memorizzati nel **[!UICONTROL Competition results]** tabella. La **[!UICONTROL Score]** il campo sul quale avrà luogo la personalizzazione della consegna viene aggiunto alla tabella di lavoro del flusso di lavoro.
1. La **[!UICONTROL Split]** l’attività di tipo ci consente di creare sottoinsiemi di destinatari in base ai punteggi.
1. Per ogni sottoinsieme, un **[!UICONTROL Delivery]** viene aggiunta l’attività di tipo .

## Passaggio 1: Targeting {#step-1--targeting}

La prima query consente di eseguire il targeting dei destinatari aggiunti al database negli ultimi sei mesi.

![](assets/uc1_enrich_4.png)

La seconda query consente di eseguire il targeting dei destinatari che hanno partecipato all’ultima gara.

![](assets/uc1_enrich_5.png)

Un **[!UICONTROL Intersection]** L’attività di tipo viene quindi aggiunta per eseguire il targeting dei destinatari aggiunti al database negli ultimi sei mesi e che sono entrati nell’ultima concorrenza.

## Passaggio 2: Arricchimento {#step-2--enrichment}

In questo esempio, vogliamo personalizzare le consegne in base alla **[!UICONTROL Score]** campo memorizzato in **[!UICONTROL Competition results]** tabella. Questa tabella presenta una relazione di tipo 1-n con la tabella dei destinatari. La **[!UICONTROL Enrichment]** l’attività ci consente di aggiungere dati da una tabella collegata alla dimensione di filtro alla tabella di lavoro del flusso di lavoro.

1. Nella schermata di modifica dell’attività di arricchimento, seleziona **[!UICONTROL Add data]**, quindi **[!UICONTROL Data linked to the filtering dimension]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. Quindi seleziona la **[!UICONTROL Data linked to the filtering dimension]** seleziona l’opzione **[!UICONTROL Competition results]** tabella e fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Immetti un ID e un’etichetta e seleziona la **[!UICONTROL Limit the line count]** in **[!UICONTROL Data collected]** campo . In **[!UICONTROL Lines to retrieve]** selezionare &quot;1&quot; come valore. Per ciascun destinatario, l’attività di arricchimento aggiunge una riga singola dal **[!UICONTROL Competition results]** alla tabella di lavoro del flusso di lavoro. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. In questo esempio, vogliamo recuperare il punteggio più alto del destinatario, ma solo per l&#39;ultima competizione. A questo scopo, aggiungi un filtro al **[!UICONTROL Competition name]** campo per escludere tutte le linee relative ai concorsi precedenti. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Vai a **[!UICONTROL Sort]** e fai clic su **[!UICONTROL Add]** seleziona il pulsante **[!UICONTROL Score]** e seleziona la casella in **[!UICONTROL descending]** per ordinare gli elementi **[!UICONTROL Score]** campi in ordine decrescente. Per ogni destinatario, l’attività di arricchimento aggiunge una riga che corrisponde al punteggio più alto per l’ultimo gioco. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. In **[!UICONTROL Data to add]** finestra, fare doppio clic sul pulsante **[!UICONTROL Score]** campo . Per ciascun destinatario, l’attività di arricchimento aggiungerà solo il **[!UICONTROL Score]** campo . Fai clic su **[!UICONTROL Finish]**.

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

Per ordinare i destinatari in base ai loro punteggi, **[!UICONTROL Split]** l’attività viene aggiunta dopo l’arricchimento.

![](assets/uc1_enrich_18.png)

1. Prima (**Vincitore**) è stato definito un sottoinsieme per includere il destinatario con il punteggio più alto. A questo scopo, definisci una limitazione del numero di record, applica un ordinamento decrescente al punteggio e limita il numero di record a 1.

   ![](assets/uc1_enrich_16.png)

1. La seconda (**Secondo posto**) include il destinatario con il secondo punteggio più alto. La configurazione è la stessa del primo sottoinsieme.

   ![](assets/uc1_enrich_17.png)

1. La terza (**perdenti**) contiene tutti gli altri destinatari. Vai a **[!UICONTROL General]** e controlla la **[!UICONTROL Generate complement]** per eseguire il targeting di tutti i destinatari che non hanno raggiunto i due punteggi più elevati.

   ![](assets/uc1_enrich_19.png)

1. Aggiungi un **[!UICONTROL Delivery]** digita l’attività per ciascun sottoinsieme, utilizzando un modello di consegna diverso per ciascun sottoinsieme.

   ![](assets/uc1_enrich_20.png)
