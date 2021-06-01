---
product: campaign
title: Query tramite una relazione molti-a-molti
description: Scopri come eseguire le query utilizzando una relazione molti-a-molti
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Query tramite una relazione molti-a-molti {#querying-using-a-many-to-many-relationship}

In questo esempio, vogliamo recuperare i destinatari non contattati negli ultimi 7 giorni. Questa query riguarda tutte le consegne.

Questo esempio mostra anche come configurare un filtro correlato alla scelta di un elemento di raccolta (o nodo arancione). Gli elementi di raccolta sono disponibili nella finestra **[!UICONTROL Field to select]** .

* Quale tabella deve essere selezionata?

   Tabella dei destinatari (**nms:recipient**)

* Campi da selezionare per la colonna di output

   Chiave primaria, Cognome, Nome ed E-mail

* In base a quali criteri vengono filtrate le informazioni

   In base ai registri di consegna dei destinatari che risalgono a 7 giorni prima di oggi

Applica i seguenti passaggi:

1. Apri l’editor di query generico e seleziona la tabella Destinatario **[!UICONTROL (nms:recipient)]**.
1. Nella finestra **[!UICONTROL Data to extract]**, selezionare **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** e **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Nella finestra di ordinamento, ordinare i nomi in ordine alfabetico.

   ![](assets/query_editor_nveau_34.png)

1. Nella finestra **[!UICONTROL Data filtering]**, selezionare **[!UICONTROL Filtering conditions]**.
1. Nella finestra **[!UICONTROL Target element]** , la condizione di filtro per l’estrazione di profili senza registro di tracciamento per gli ultimi 7 giorni prevede due passaggi. L’elemento da selezionare è un collegamento molti-a-molti.

   * Inizia selezionando l&#39;elemento di raccolta **[!UICONTROL Recipient delivery logs (broadlog)]** (nodo arancione) per la prima colonna **[!UICONTROL Value]**.

      ![](assets/query_editor_nveau_67.png)

      Scegli l’operatore **[!UICONTROL do not exist as]** . Non è necessario selezionare un secondo valore in questa riga.

   * Il contenuto della seconda condizione di filtro dipende dalla prima. In questo caso, il campo **[!UICONTROL Event date]** viene offerto direttamente nella tabella **[!UICONTROL Recipient delivery logs]** in quanto è presente un collegamento a questa tabella.

      ![](assets/query_editor_nveau_36.png)

      Selezionare **[!UICONTROL Event date]** con l&#39;operatore **[!UICONTROL greater than or equal to]**. Selezionare il valore **[!UICONTROL DaysAgo (7)]**. A questo scopo, fai clic su **[!UICONTROL Edit expression]** nel campo **[!UICONTROL Value]** . Nella finestra **[!UICONTROL Formula type]**, selezionare **[!UICONTROL Process on dates]** e **[!UICONTROL Current date minus n days]**, assegnando &quot;7&quot; come valore.

      ![](assets/query_editor_nveau_37.png)

      La condizione del filtro è configurata.

      ![](assets/query_editor_nveau_38.png)

1. Nella finestra **[!UICONTROL Data formatting]**, cambiare il cognome in maiuscolo. Fai clic sulla riga **[!UICONTROL Last name]** nella colonna **[!UICONTROL Transformation]** e seleziona **[!UICONTROL Switch to upper case]** nel menu a discesa.

   ![](assets/query_editor_nveau_39.png)

1. Utilizzare la funzione **[!UICONTROL Add a calculated field]** per inserire una colonna nella finestra di anteprima dati.

   In questo esempio, aggiungi un campo calcolato con il nome e il cognome dei destinatari in un’unica colonna. Fare clic sulla funzione **[!UICONTROL Add a calculated field]**. Nella finestra **[!UICONTROL Export calculated field definition]**, immetti un’etichetta e un nome interno e scegli il tipo **[!UICONTROL JavaScript Expression]**. Quindi immetti la seguente espressione:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Fai clic su **[!UICONTROL OK]**. La finestra **[!UICONTROL Data formatting]** è configurata.

   Per ulteriori informazioni sull’aggiunta di campi calcolati, consulta questa sezione.

1. Il risultato viene visualizzato nella finestra **[!UICONTROL Data preview]**. I destinatari che non sono stati contattati negli ultimi 7 giorni vengono visualizzati in ordine alfabetico. I nomi vengono visualizzati in maiuscolo e la colonna con il nome e il cognome è stata creata.

   ![](assets/query_editor_nveau_41.png)
