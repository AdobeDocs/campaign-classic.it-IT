---
product: campaign
title: Eseguire una query tramite una relazione molti-a-molti
description: Scopri come eseguire query utilizzando una relazione molti-a-molti
feature: Query Editor, Workflows
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Eseguire una query tramite una relazione molti-a-molti {#querying-using-a-many-to-many-relationship}



In questo esempio, vogliamo recuperare i destinatari non contattati negli ultimi 7 giorni. Questa query riguarda tutte le consegne.

Questo esempio mostra anche come configurare un filtro correlato alla scelta di un elemento di raccolta (o nodo arancione). Gli elementi della raccolta sono disponibili nella finestra **[!UICONTROL Field to select]**.

* Quale tabella deve essere selezionata?

  Tabella dei destinatari (**nms:recipient**)

* Campi da selezionare per la colonna di output

  Chiave primaria, cognome, nome e indirizzo e-mail

* In base a quali criteri vengono filtrate le informazioni

  In base ai registri di consegna dei destinatari che risalgono a 7 giorni prima di oggi

Applica i seguenti passaggi:

1. Aprire l&#39;editor delle query generiche e selezionare la tabella Destinatario **[!UICONTROL (nms:recipient)]**.
1. Nella finestra **[!UICONTROL Data to extract]**, selezionare **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** e **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Nella finestra di ordinamento, ordinare i nomi in ordine alfabetico.

   ![](assets/query_editor_nveau_34.png)

1. Nella finestra **[!UICONTROL Data filtering]**, selezionare **[!UICONTROL Filtering conditions]**.
1. Nella finestra **[!UICONTROL Target element]**, la condizione di filtro per l&#39;estrazione dei profili senza registro di tracciamento per gli ultimi 7 giorni prevede due passaggi. L’elemento da selezionare è un collegamento da molti-a-molti.

   * Per iniziare, selezionare l&#39;elemento della raccolta **[!UICONTROL Recipient delivery logs (broadlog)]** (nodo arancione) per la prima colonna **[!UICONTROL Value]**.

     ![](assets/query_editor_nveau_67.png)

     Scegliere l&#39;operatore **[!UICONTROL do not exist as]**. Non è necessario selezionare un secondo valore in questa riga.

   * Il contenuto della seconda condizione di filtro dipende dalla prima. In questo caso, il campo **[!UICONTROL Event date]** viene offerto direttamente nella tabella **[!UICONTROL Recipient delivery logs]** poiché è presente un collegamento a questa tabella.

     ![](assets/query_editor_nveau_36.png)

     Selezionare **[!UICONTROL Event date]** con l&#39;operatore **[!UICONTROL greater than or equal to]**. Selezionare il valore **[!UICONTROL DaysAgo (7)]**. A tale scopo, fare clic su **[!UICONTROL Edit expression]** nel campo **[!UICONTROL Value]**. Nella finestra **[!UICONTROL Formula type]**, selezionare **[!UICONTROL Process on dates]** e **[!UICONTROL Current date minus n days]**, fornendo &quot;7&quot; come valore.

     ![](assets/query_editor_nveau_37.png)

     La condizione del filtro è configurata.

     ![](assets/query_editor_nveau_38.png)

1. Nella finestra **[!UICONTROL Data formatting]**, impostare i cognomi in maiuscolo. Fare clic sulla riga **[!UICONTROL Last name]** nella colonna **[!UICONTROL Transformation]** e selezionare **[!UICONTROL Switch to upper case]** nel menu a discesa.

   ![](assets/query_editor_nveau_39.png)

1. Utilizzare la funzione **[!UICONTROL Add a calculated field]** per inserire una colonna nella finestra di anteprima dei dati.

   In questo esempio, aggiungi un campo calcolato con il nome e il cognome dei destinatari in una singola colonna. Fare clic sulla funzione **[!UICONTROL Add a calculated field]**. Nella finestra **[!UICONTROL Export calculated field definition]**, immettere un&#39;etichetta e un nome interno e scegliere il tipo **[!UICONTROL JavaScript Expression]**. Quindi immetti la seguente espressione:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Fai clic su **[!UICONTROL OK]**. Finestra **[!UICONTROL Data formatting]** configurata.

   Per ulteriori informazioni sull’aggiunta di campi calcolati, consulta questa sezione.

1. Il risultato viene visualizzato nella finestra **[!UICONTROL Data preview]**. I destinatari che non sono stati contattati negli ultimi 7 giorni vengono visualizzati in ordine alfabetico. I nomi vengono visualizzati in maiuscolo ed è stata creata la colonna con nome e cognome.

   ![](assets/query_editor_nveau_41.png)
