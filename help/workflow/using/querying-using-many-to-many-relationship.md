---
product: campaign
title: Eseguire una query tramite una relazione molti-a-molti
description: Scopri come eseguire query utilizzando una relazione molti-a-molti
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 2%

---

# Eseguire una query tramite una relazione molti-a-molti {#querying-using-a-many-to-many-relationship}



In questo esempio, vogliamo recuperare i destinatari non contattati negli ultimi 7 giorni. Questa query riguarda tutte le consegne.

Questo esempio mostra anche come configurare un filtro correlato alla scelta di un elemento di raccolta (o nodo arancione). Gli elementi della raccolta sono disponibili nel **[!UICONTROL Field to select]** finestra.

* Quale tabella deve essere selezionata?

  Tabella dei destinatari (**nms:destinatario**)

* Campi da selezionare per la colonna di output

  Chiave primaria, cognome, nome e indirizzo e-mail

* In base a quali criteri vengono filtrate le informazioni

  In base ai registri di consegna dei destinatari che risalgono a 7 giorni prima di oggi

Applica i seguenti passaggi:

1. Apri l’editor delle query generiche e seleziona la tabella Destinatario. **[!UICONTROL (nms:recipient)]**.
1. In **[!UICONTROL Data to extract]** finestra, seleziona **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** e **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. Nella finestra di ordinamento, ordinare i nomi in ordine alfabetico.

   ![](assets/query_editor_nveau_34.png)

1. In **[!UICONTROL Data filtering]** finestra, seleziona **[!UICONTROL Filtering conditions]**.
1. In **[!UICONTROL Target element]** finestra, la condizione di filtro per l’estrazione di profili senza registro di tracciamento per gli ultimi 7 giorni prevede due passaggi. L’elemento da selezionare è un collegamento da molti-a-molti.

   * Per iniziare, seleziona la **[!UICONTROL Recipient delivery logs (broadlog)]** elemento di raccolta (nodo arancione) per il primo **[!UICONTROL Value]** colonna.

     ![](assets/query_editor_nveau_67.png)

     Scegli la **[!UICONTROL do not exist as]** operatore. Non è necessario selezionare un secondo valore in questa riga.

   * Il contenuto della seconda condizione di filtro dipende dalla prima. Ecco, il **[!UICONTROL Event date]** il campo è offerto direttamente nel **[!UICONTROL Recipient delivery logs]** perché è presente un collegamento a questa tabella.

     ![](assets/query_editor_nveau_36.png)

     Seleziona **[!UICONTROL Event date]** con **[!UICONTROL greater than or equal to]** operatore. Seleziona la **[!UICONTROL DaysAgo (7)]** valore. A questo scopo, fai clic su **[!UICONTROL Edit expression]** nel **[!UICONTROL Value]** campo. In **[!UICONTROL Formula type]** finestra, seleziona **[!UICONTROL Process on dates]** e **[!UICONTROL Current date minus n days]**, specificando &quot;7&quot; come valore.

     ![](assets/query_editor_nveau_37.png)

     La condizione del filtro è configurata.

     ![](assets/query_editor_nveau_38.png)

1. In **[!UICONTROL Data formatting]** , impostare i cognomi in maiuscolo. Fai clic su **[!UICONTROL Last name]** riga in **[!UICONTROL Transformation]** e seleziona **[!UICONTROL Switch to upper case]** nel menu a discesa.

   ![](assets/query_editor_nveau_39.png)

1. Utilizza il **[!UICONTROL Add a calculated field]** per inserire una colonna nella finestra di anteprima dei dati.

   In questo esempio, aggiungi un campo calcolato con il nome e il cognome dei destinatari in una singola colonna. Fai clic su **[!UICONTROL Add a calculated field]** funzione. In **[!UICONTROL Export calculated field definition]** , inserire un&#39;etichetta e un nome interno e scegliere **[!UICONTROL JavaScript Expression]** tipo. Quindi immetti la seguente espressione:

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   Fai clic su **[!UICONTROL OK]**. Il **[!UICONTROL Data formatting]** è configurata.

   Per ulteriori informazioni sull’aggiunta di campi calcolati, consulta questa sezione.

1. Il risultato è mostrato nella **[!UICONTROL Data preview]** finestra. I destinatari che non sono stati contattati negli ultimi 7 giorni vengono visualizzati in ordine alfabetico. I nomi vengono visualizzati in maiuscolo ed è stata creata la colonna con nome e cognome.

   ![](assets/query_editor_nveau_41.png)
