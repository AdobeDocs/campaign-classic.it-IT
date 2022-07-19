---
product: campaign
title: Query tramite una relazione molti-a-molti
description: Scopri come eseguire le query utilizzando una relazione molti-a-molti
feature: Query Editor
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Query tramite una relazione molti-a-molti {#querying-using-a-many-to-many-relationship}

![](../../assets/v7-only.svg)

In questo esempio, vogliamo recuperare i destinatari non contattati negli ultimi 7 giorni. Questa query riguarda tutte le consegne.

Questo esempio mostra anche come configurare un filtro correlato alla scelta di un elemento di raccolta (o nodo arancione). Gli elementi di raccolta sono disponibili nel **[!UICONTROL Field to select]** finestra.

* Quale tabella deve essere selezionata?

   La tabella dei destinatari (**nms:recipient**)

* Campi da selezionare per la colonna di output

   Chiave primaria, Cognome, Nome ed E-mail

* In base a quali criteri vengono filtrate le informazioni

   In base ai registri di consegna dei destinatari che risalgono a 7 giorni prima di oggi

Applica i seguenti passaggi:

1. Apri l’editor di query generico e seleziona la tabella Destinatario **[!UICONTROL (nms:recipient)]**.
1. In **[!UICONTROL Data to extract]** finestra, seleziona **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** e **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Nella finestra di ordinamento, ordinare i nomi in ordine alfabetico.

   ![](assets/query_editor_nveau_34.png)

1. In **[!UICONTROL Data filtering]** finestra, seleziona **[!UICONTROL Filtering conditions]**.
1. In **[!UICONTROL Target element]** La condizione di filtro per l’estrazione di profili senza registro di tracciamento per gli ultimi 7 giorni prevede due passaggi. L’elemento da selezionare è un collegamento molti-a-molti.

   * Inizia selezionando la **[!UICONTROL Recipient delivery logs (broadlog)]** elemento di raccolta (nodo arancione) per il primo **[!UICONTROL Value]** colonna.

      ![](assets/query_editor_nveau_67.png)

      Scegli la **[!UICONTROL do not exist as]** operatore. Non è necessario selezionare un secondo valore in questa riga.

   * Il contenuto della seconda condizione di filtro dipende dalla prima. Qui, il **[!UICONTROL Event date]** viene offerto direttamente nel **[!UICONTROL Recipient delivery logs]** tabella poiché è presente un collegamento a questa tabella.

      ![](assets/query_editor_nveau_36.png)

      Seleziona **[!UICONTROL Event date]** con **[!UICONTROL greater than or equal to]** operatore. Seleziona la **[!UICONTROL DaysAgo (7)]** valore. A questo scopo, fai clic su **[!UICONTROL Edit expression]** in **[!UICONTROL Value]** campo . In **[!UICONTROL Formula type]** finestra, seleziona **[!UICONTROL Process on dates]** e **[!UICONTROL Current date minus n days]**, dando come valore &quot;7&quot;.

      ![](assets/query_editor_nveau_37.png)

      La condizione del filtro è configurata.

      ![](assets/query_editor_nveau_38.png)

1. In **[!UICONTROL Data formatting]** finestra, cambiare i cognomi in maiuscolo. Fai clic sul pulsante **[!UICONTROL Last name]** nella **[!UICONTROL Transformation]** e seleziona **[!UICONTROL Switch to upper case]** nel menu a discesa .

   ![](assets/query_editor_nveau_39.png)

1. Utilizza la **[!UICONTROL Add a calculated field]** per inserire una colonna nella finestra di anteprima dati.

   In questo esempio, aggiungi un campo calcolato con il nome e il cognome dei destinatari in un’unica colonna. Fai clic sul pulsante **[!UICONTROL Add a calculated field]** funzione . In **[!UICONTROL Export calculated field definition]** , immetti un&#39;etichetta e un nome interno e scegli la **[!UICONTROL JavaScript Expression]** digitare. Quindi immetti la seguente espressione:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Fai clic su **[!UICONTROL OK]**. La **[!UICONTROL Data formatting]** finestra configurata.

   Per ulteriori informazioni sull’aggiunta di campi calcolati, consulta questa sezione.

1. Il risultato viene visualizzato nella **[!UICONTROL Data preview]** finestra. I destinatari che non sono stati contattati negli ultimi 7 giorni vengono visualizzati in ordine alfabetico. I nomi vengono visualizzati in maiuscolo e la colonna con il nome e il cognome è stata creata.

   ![](assets/query_editor_nveau_41.png)
