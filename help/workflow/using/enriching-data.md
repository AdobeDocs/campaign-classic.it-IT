---
solution: Campaign Classic
product: campaign
title: Arricchimento dei dati
description: Ulteriori informazioni sull'attività del flusso di lavoro Arricchimento
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---


# Arricchimento dei dati{#enriching-data}

## Informazioni sull&#39;arricchimento dei dati {#about-enriching-data}

Questo caso di utilizzo descrive i possibili usi dell&#39;attività **[!UICONTROL Enrichment]** in un flusso di lavoro di targeting. Per ulteriori informazioni sull&#39;utilizzo dell&#39;attività **[!UICONTROL Enrichment]**, fare riferimento a: [Arricchimento](../../workflow/using/enrichment.md).

In [questa sezione](../../workflow/using/email-enrichment-with-custom-date-fields.md) è disponibile anche un esempio di utilizzo per arricchire la consegna di un&#39;e-mail con date personalizzate.

I contatti presenti nel database marketing vengono inviati tramite un&#39;applicazione Web, invitandoli a partecipare a un concorso. I risultati della gara sono riportati nella tabella **[!UICONTROL Competition results]**. Questa tabella è collegata alla tabella dei contatti (**[!UICONTROL Recipients]**). La tabella **[!UICONTROL Competition results]** contiene i campi seguenti:

* Nome concorrenza (@game)
* Numero di prova (@trial)
* Punteggio (@score)

![](assets/uc1_enrich_1.png)

Un contatto trovato nella tabella **[!UICONTROL Recipients]** può essere collegato a più righe nella tabella **[!UICONTROL Competition results]**. La relazione tra queste due tabelle è di tipo 1-n. Di seguito è riportato un esempio dei log dei risultati per un destinatario:

![](assets/uc1_enrich_2.png)

Lo scopo di questo caso d&#39;uso è quello di inviare consegne personalizzate alle persone che hanno partecipato all&#39;ultimo concorso in base ai loro punteggi più alti. Il vincitore con il punteggio più alto ottiene il primo premio, il destinatario con il secondo punteggio più alto ottiene un premio di consolazione e tutti gli altri ricevono un messaggio che augura loro migliore fortuna la prossima volta.

Per impostare questo caso di utilizzo, abbiamo creato il seguente flusso di lavoro di targeting:

![](assets/uc1_enrich_3.png)

Per creare il flusso di lavoro, effettuate le seguenti operazioni:

1. Due attività **[!UICONTROL Query]** e una **[!UICONTROL Intersection]** vengono aggiunte ai nuovi sottoscrittori che hanno partecipato per ultimo al concorso.
1. L&#39;attività **[!UICONTROL Enrichment]** ci consente di aggiungere i dati memorizzati nella tabella **[!UICONTROL Competition results]**. Il campo **[!UICONTROL Score]** sul quale verrà realizzata la personalizzazione per la distribuzione viene aggiunto al tavolo di lavoro del flusso di lavoro.
1. L&#39;attività di tipo **[!UICONTROL Split]** ci consente di creare sottoinsiemi di destinatari in base ai punteggi.
1. Per ciascun sottoinsieme, viene aggiunta un&#39;attività di tipo **[!UICONTROL Delivery]**.

## Passaggio 1: Targeting {#step-1--targeting}

La prima query consente di eseguire il targeting dei destinatari aggiunti al database negli ultimi sei mesi.

![](assets/uc1_enrich_4.png)

La seconda query consente di individuare i destinatari che hanno partecipato all&#39;ultima gara.

![](assets/uc1_enrich_5.png)

Un&#39;attività di tipo **[!UICONTROL Intersection]** viene quindi aggiunta al target dei destinatari aggiunti al database negli ultimi sei mesi e che sono entrati nell&#39;ultimo concorso.

## Passaggio 2: Arricchimento {#step-2--enrichment}

In questo esempio, vogliamo personalizzare le consegne in base al campo **[!UICONTROL Score]** memorizzato nella tabella **[!UICONTROL Competition results]**. Questa tabella ha una relazione di tipo 1-n con la tabella dei destinatari. L&#39;attività **[!UICONTROL Enrichment]** consente di aggiungere dati da una tabella collegata alla dimensione di filtro alla tabella di lavoro del flusso di lavoro.

1. Nella schermata di modifica dell&#39;attività di arricchimento, selezionare **[!UICONTROL Add data]**, quindi **[!UICONTROL Data linked to the filtering dimension]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_6.png)

1. Selezionare quindi l&#39;opzione **[!UICONTROL Data linked to the filtering dimension]**, selezionare la tabella **[!UICONTROL Competition results]** e fare clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_7.png)

1. Immettete un ID e un&#39;etichetta, quindi selezionate l&#39;opzione **[!UICONTROL Limit the line count]** nel campo **[!UICONTROL Data collected]**. Nel campo **[!UICONTROL Lines to retrieve]**, selezionare &#39;1&#39; come valore. Per ciascun destinatario, l&#39;attività di arricchimento aggiungerà una sola riga dalla tabella **[!UICONTROL Competition results]** alla tabella di lavoro del flusso di lavoro. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_8.png)

1. In questo esempio, vogliamo recuperare il punteggio più alto del destinatario, ma solo per l&#39;ultima competizione. A tal fine, aggiungere un filtro al campo **[!UICONTROL Competition name]** per escludere tutte le righe relative ai concorsi precedenti. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_9.png)

1. Passate alla schermata **[!UICONTROL Sort]** e fate clic sul pulsante **[!UICONTROL Add]**, selezionate il campo **[!UICONTROL Score]** e selezionate la casella nella colonna **[!UICONTROL descending]** per ordinare gli elementi dei campi **[!UICONTROL Score]** in ordine decrescente. Per ciascun destinatario, l&#39;attività di arricchimento aggiunge una linea che corrisponde al punteggio più alto dell&#39;ultima partita. Fai clic su **[!UICONTROL Next]**.

   ![](assets/uc1_enrich_10.png)

1. Nella finestra **[!UICONTROL Data to add]**, fare doppio clic sul campo **[!UICONTROL Score]**. Per ciascun destinatario, l&#39;attività di arricchimento aggiungerà solo il campo **[!UICONTROL Score]**. Fai clic su **[!UICONTROL Finish]**.

   ![](assets/uc1_enrich_11.png)

Fare clic con il pulsante destro del mouse sulla transizione in entrata dell&#39;attività di arricchimento e selezionare **[!UICONTROL Display the target]**. La tabella di lavoro contiene i dati seguenti:

![](assets/uc1_enrich_13.png)

Lo schema collegato è:

![](assets/uc1_enrich_15.png)

Rinnovare questa operazione sulla transizione in uscita dell&#39;attività di arricchimento. Possiamo vedere che i dati collegati ai punteggi dei destinatari sono stati aggiunti. Il punteggio più alto di ciascun destinatario è stato recuperato.

![](assets/uc1_enrich_12.png)

Anche lo schema corrispondente è stato arricchito.

![](assets/uc1_enrich_14.png)

## Passaggio 3: Dividi e consegna {#step-3--split-and-delivery}

Per ordinare i destinatari in base ai loro punteggi, dopo l&#39;arricchimento viene aggiunta un&#39;attività **[!UICONTROL Split]**.

![](assets/uc1_enrich_18.png)

1. È stato definito un primo sottoinsieme (**Winner**) per includere il destinatario con il punteggio più alto. A tal fine, definire una limitazione del numero di record, applicare un ordinamento decrescente alla valutazione e limitare il numero di record a 1.

   ![](assets/uc1_enrich_16.png)

1. Il secondo sottoinsieme (**Second place**) include il destinatario con il secondo punteggio più alto. La configurazione è la stessa del primo sottoinsieme.

   ![](assets/uc1_enrich_17.png)

1. Il terzo sottoinsieme (**perdenti**) contiene tutti gli altri destinatari. Vai alla scheda **[!UICONTROL General]** e seleziona la casella **[!UICONTROL Generate complement]** per eseguire il targeting di tutti i destinatari che non hanno raggiunto i due punteggi più alti.

   ![](assets/uc1_enrich_19.png)

1. Aggiungete un&#39;attività di tipo **[!UICONTROL Delivery]** per ciascun sottoinsieme, utilizzando un modello di consegna diverso per ciascun sottoinsieme.

   ![](assets/uc1_enrich_20.png)

