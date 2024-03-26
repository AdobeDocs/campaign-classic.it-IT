---
product: campaign
title: Arricchire i dati
description: Ulteriori informazioni sull’attività del flusso di lavoro Arricchimento
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Workflows, Enrichment Activity
exl-id: ab786cf1-74a4-4185-a63d-84e776a2f776
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 1%

---

# Arricchire i dati{#enriching-data}



## Informazioni sull’arricchimento dei dati {#about-enriching-data}

Questo caso d’uso descrive i possibili utilizzi di **[!UICONTROL Enrichment]** attività in un flusso di lavoro di targeting. Per ulteriori informazioni sull&#39;utilizzo di **[!UICONTROL Enrichment]** attività, consulta: [Arricchimento](enrichment.md).

Un caso di utilizzo su come arricchire una consegna e-mail con date personalizzate è disponibile anche in [questa sezione](email-enrichment-with-custom-date-fields.md).

I contatti della banca dati di marketing ricevono un invito a partecipare a un concorso tramite un’applicazione web. I risultati della concorrenza sono recuperati nel **[!UICONTROL Competition results]** tabella. Questa tabella è collegata alla tabella dei contatti (**[!UICONTROL Recipients]**). Il **[!UICONTROL Competition results]** la tabella contiene i campi seguenti:

* Nome concorrenza (@game)
* Numero della prova (@trial)
* Punteggio (@score)

![](assets/uc1_enrich_1.png)

Un contatto trovato in **[!UICONTROL Recipients]** la tabella può essere collegata a più righe nella **[!UICONTROL Competition results]** tabella. La relazione tra queste due tabelle è di tipo 1-n. Ecco un esempio dei registri dei risultati per un destinatario:

![](assets/uc1_enrich_2.png)

Lo scopo di questo caso d’uso è quello di inviare consegne personalizzate a persone che hanno partecipato all’ultimo concorso a seconda dei punteggi più elevati. Il destinatario con il punteggio più alto ottiene il primo premio, il destinatario con il secondo punteggio più alto riceve un premio di consolazione e tutti gli altri ricevono un messaggio augurando loro maggiore fortuna la prossima volta.

Per impostare questo caso d’uso, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/uc1_enrich_3.png)

Per creare il flusso di lavoro, effettua le seguenti operazioni:

1. Due **[!UICONTROL Query]** attività e uno **[!UICONTROL Intersection]** L&#39;attività viene aggiunta ai nuovi abbonati che hanno partecipato per ultimi al concorso.
1. Il **[!UICONTROL Enrichment]** l&#39;attività ci consente di aggiungere i dati memorizzati nel **[!UICONTROL Competition results]** tabella. Il **[!UICONTROL Score]** il campo in cui avverrà la personalizzazione della consegna viene aggiunto alla tabella di lavoro del flusso di lavoro.
1. Il **[!UICONTROL Split]** l’attività di tipo consente di creare sottoinsiemi di destinatari in base a punteggi.
1. Per ogni sottoinsieme, un **[!UICONTROL Delivery]** viene aggiunta l’attività di tipo.

## Passaggio 1: targeting {#step-1--targeting}

La prima query consente di eseguire il targeting dei destinatari aggiunti al database negli ultimi sei mesi.

![](assets/uc1_enrich_4.png)

La seconda query consente di eseguire il targeting dei destinatari che hanno partecipato all’ultimo concorso.

![](assets/uc1_enrich_5.png)

Un **[!UICONTROL Intersection]** L’attività di tipo viene quindi aggiunta per individuare i destinatari aggiunti al database negli ultimi sei mesi e che hanno partecipato all’ultimo concorso.

## Passaggio 2: Arricchimento {#step-2--enrichment}

In questo esempio, vogliamo personalizzare le consegne in base al **[!UICONTROL Score]** campo memorizzato in **[!UICONTROL Competition results]** tabella. Questa tabella ha una relazione di tipo 1-n con la tabella dei destinatari. Il **[!UICONTROL Enrichment]** activity (attività) consente di aggiungere i dati di una tabella collegata alla dimensione di filtro alla tabella di lavoro del flusso di lavoro.

1. Nella schermata di modifica dell’attività di arricchimento, seleziona **[!UICONTROL Add data]**, quindi **[!UICONTROL Data linked to the filtering dimension]** e fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. Quindi seleziona la **[!UICONTROL Data linked to the filtering dimension]** , seleziona l&#39;opzione **[!UICONTROL Competition results]** tabella e fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Immetti un ID e un’etichetta e seleziona la **[!UICONTROL Limit the line count]** opzione in **[!UICONTROL Data collected]** campo. In **[!UICONTROL Lines to retrieve]** , seleziona &quot;1&quot; come valore. Per ogni destinatario, l’attività di arricchimento aggiungerà una singola riga dalla **[!UICONTROL Competition results]** nella tabella di lavoro del flusso di lavoro. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. In questo esempio, vogliamo recuperare il punteggio più alto del destinatario, ma solo per l’ultimo concorso. A questo scopo, aggiungi un filtro al **[!UICONTROL Competition name]** campo per escludere tutte le righe relative ai concorsi precedenti. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Vai a **[!UICONTROL Sort]** e fai clic su **[!UICONTROL Add]** , selezionare il **[!UICONTROL Score]** e seleziona la casella nella sezione **[!UICONTROL descending]** colonna per ordinare gli elementi del **[!UICONTROL Score]** campi in ordine decrescente. Per ogni destinatario, l’attività di arricchimento aggiunge una riga che corrisponde al punteggio più alto dell’ultima partita. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. In **[!UICONTROL Data to add]** fare doppio clic sulla **[!UICONTROL Score]** campo. Per ogni destinatario, l’attività di arricchimento aggiungerà solo il **[!UICONTROL Score]** campo. Fai clic su **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Fai clic con il pulsante destro del mouse sulla transizione in entrata dell’attività di arricchimento e seleziona **[!UICONTROL Display the target]**. La tabella di lavoro contiene i dati seguenti:

![](assets/uc1_enrich_13.png)

Schema collegato:

![](assets/uc1_enrich_15.png)

Rinnova questa operazione nella transizione in uscita dell’attività di arricchimento. Possiamo vedere che sono stati aggiunti i dati collegati ai punteggi dei destinatari. È stato recuperato il punteggio più alto di ciascun destinatario.

![](assets/uc1_enrich_12.png)

Anche lo schema corrispondente è stato arricchito.

![](assets/uc1_enrich_14.png)

## Passaggio 3: suddivisione e consegna {#step-3--split-and-delivery}

Per ordinare i destinatari in base ai loro punteggi, è necessario **[!UICONTROL Split]** l’attività viene aggiunta dopo l’arricchimento.

![](assets/uc1_enrich_18.png)

1. Una prima (**Vincitore**) è stato definito un sottoinsieme per includere il destinatario con il punteggio più alto. A questo scopo, definisci un limite del numero di record, applica un ordinamento decrescente al punteggio e limita il numero di record a 1.

   ![](assets/uc1_enrich_16.png)

1. La seconda (**Secondo posto**) include il destinatario con il secondo punteggio più alto. La configurazione è la stessa del primo sottoinsieme.

   ![](assets/uc1_enrich_17.png)

1. La terza (**perdenti**) contiene tutti gli altri destinatari. Vai a **[!UICONTROL General]** e controllare la **[!UICONTROL Generate complement]** per eseguire il targeting di tutti i destinatari che non hanno raggiunto i due punteggi più alti.

   ![](assets/uc1_enrich_19.png)

1. Aggiungi un **[!UICONTROL Delivery]** digita l’attività per ogni sottoinsieme, utilizzando un modello di consegna diverso per ciascuno di essi.

   ![](assets/uc1_enrich_20.png)
