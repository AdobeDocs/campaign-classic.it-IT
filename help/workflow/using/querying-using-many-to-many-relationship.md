---
solution: Campaign Classic
product: campaign
title: Query mediante una relazione molti-a-molti
description: Scopri come eseguire query utilizzando una relazione molti-a-molti
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# Query mediante una relazione molti-a-molti {#querying-using-a-many-to-many-relationship}

In questo esempio, vogliamo recuperare i destinatari non contattati negli ultimi 7 giorni. Questa query riguarda tutte le consegne.

Questo esempio mostra anche come configurare un filtro correlato alla scelta di un elemento raccolta (o nodo arancione). Gli elementi della raccolta sono disponibili nella finestra **[!UICONTROL Field to select]**.

* Quale tabella deve essere selezionata?

   Tabella destinatari (**nms:destinatario**)

* Campi da selezionare per la colonna di output

   Chiave primaria, Cognome, Nome e E-mail

* In base a quali criteri vengono filtrate le informazioni

   In base ai registri di consegna dei destinatari che risalgono a 7 giorni prima di oggi

Effettuate le seguenti operazioni:

1. Aprite l&#39;editor di query generico e selezionate la tabella Destinatario **[!UICONTROL (nms:recipient)]**.
1. Nella finestra **[!UICONTROL Data to extract]**, selezionare **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** e **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Nella finestra di ordinamento, ordinate i nomi in ordine alfabetico.

   ![](assets/query_editor_nveau_34.png)

1. Nella finestra **[!UICONTROL Data filtering]**, selezionare **[!UICONTROL Filtering conditions]**.
1. Nella finestra **[!UICONTROL Target element]**, la condizione di filtro per l&#39;estrazione di profili senza registro di tracciamento per gli ultimi 7 giorni prevede due passaggi. L’elemento da selezionare è un collegamento molti-molti.

   * Per iniziare, selezionate l&#39;elemento della raccolta **[!UICONTROL Recipient delivery logs (broadlog)]** (nodo arancione) per la prima **[!UICONTROL Value]** colonna.

      ![](assets/query_editor_nveau_67.png)

      Scegliere l&#39;operatore **[!UICONTROL do not exist as]**. Non è necessario selezionare un secondo valore in questa riga.

   * Il contenuto della seconda condizione di filtro dipende dalla prima. Qui, il campo **[!UICONTROL Event date]** viene offerto direttamente nella tabella **[!UICONTROL Recipient delivery logs]**, in quanto è presente un collegamento a questa tabella.

      ![](assets/query_editor_nveau_36.png)

      Selezionare **[!UICONTROL Event date]** con l&#39;operatore **[!UICONTROL greater than or equal to]**. Selezionare il valore **[!UICONTROL DaysAgo (7)]**. A tal fine, fare clic su **[!UICONTROL Edit expression]** nel campo **[!UICONTROL Value]**. Nella finestra **[!UICONTROL Formula type]**, selezionare **[!UICONTROL Process on dates]** e **[!UICONTROL Current date minus n days]**, indicando &quot;7&quot; come valore.

      ![](assets/query_editor_nveau_37.png)

      La condizione del filtro è configurata.

      ![](assets/query_editor_nveau_38.png)

1. Nella finestra **[!UICONTROL Data formatting]**, cambiare il cognome in maiuscolo. Fare clic sulla riga **[!UICONTROL Last name]** nella colonna **[!UICONTROL Transformation]** e selezionare **[!UICONTROL Switch to upper case]** nel menu a discesa.

   ![](assets/query_editor_nveau_39.png)

1. Utilizzare la funzione **[!UICONTROL Add a calculated field]** per inserire una colonna nella finestra di anteprima dei dati.

   In questo esempio, aggiungere un campo calcolato con i nomi e i cognomi dei destinatari in un&#39;unica colonna. Fare clic sulla funzione **[!UICONTROL Add a calculated field]**. Nella finestra **[!UICONTROL Export calculated field definition]**, immettete un&#39;etichetta e un nome interno e scegliete il tipo **[!UICONTROL JavaScript Expression]**. Quindi immettete la seguente espressione:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Fai clic su **[!UICONTROL OK]**. La finestra **[!UICONTROL Data formatting]** è configurata.

   Per ulteriori informazioni sull&#39;aggiunta di campi calcolati, consultare questa sezione.

1. Il risultato viene visualizzato nella finestra **[!UICONTROL Data preview]**. I destinatari che non sono stati contattati negli ultimi 7 giorni vengono visualizzati in ordine alfabetico. I nomi vengono visualizzati in lettere maiuscole e la colonna con il nome e il cognome è stata creata.

   ![](assets/query_editor_nveau_41.png)
