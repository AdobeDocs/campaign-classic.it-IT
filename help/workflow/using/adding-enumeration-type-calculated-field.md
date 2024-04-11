---
product: campaign
title: Aggiungere un campo calcolato di tipo enumerazione
description: Scopri come aggiungere un campo calcolato di tipo enumerazione
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Aggiungere un campo calcolato di tipo enumerazione {#adding-an-enumeration-type-calculated-field}



In questo caso vogliamo creare una query con un **[!UICONTROL Enumerations]** digita il campo calcolato. Questo campo genera una colonna aggiuntiva nella finestra di anteprima dati. Questa colonna specifica i valori numerici restituiti come risultato per ciascun destinatario (0, 1 e 2). A ciascun valore della nuova colonna verrà assegnato un genere: &quot;Maschio&quot; per &quot;1&quot;, &quot;Femmina&quot; per &quot;2&quot; oppure &quot;Non indicato&quot; se il valore è uguale a &quot;0&quot;.

* Quale tabella deve essere selezionata?

  Tabella dei destinatari (nms:recipient)

* Campi da selezionare nella colonna di output?

  Cognome, Nome, Genere

* Criteri in base ai quali le informazioni verranno filtrate?

  La lingua del destinatario

Applica i seguenti passaggi:

1. Apri l’editor delle query generiche e seleziona la tabella Destinatario (**[!UICONTROL nms:recipient]**).
1. In **[!UICONTROL Data to extract]** finestra, seleziona **[!UICONTROL Last name]**, **[!UICONTROL First name]** e **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. In **[!UICONTROL Sorting]** finestra, fai clic su **[!UICONTROL Next]**: per questo esempio non è necessario alcun ordinamento.
1. In **[!UICONTROL Data filtering]**, seleziona **[!UICONTROL Filtering conditions]**.
1. In **[!UICONTROL Target element]** , impostare una condizione di filtro per raccogliere i destinatari che parlano inglese.

   ![](assets/query_editor_nveau_74.png)

1. In **[!UICONTROL Data formatting]** finestra, fai clic su **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Vai a **[!UICONTROL Type]** finestra del **[!UICONTROL Export calculated field definition]** finestra e seleziona **[!UICONTROL Enumerations]**.

   Definisci la colonna a cui deve fare riferimento il nuovo campo calcolato. A questo scopo, seleziona la **[!UICONTROL Gender]** nel menu a discesa del **[!UICONTROL Source column]** campo: i valori di destinazione coincidono con **[!UICONTROL Gender]** colonna.

   ![](assets/query_editor_nveau_76.png)

   Definisci il **Sorgente** e **Destinazione** valori: il valore di destinazione facilita la lettura del risultato della query. Questa query deve restituire il genere del destinatario e il risultato sarà 0, 1 o 2.

   Per ogni riga &quot;sorgente-destinazione&quot; da inserire, fai clic su **[!UICONTROL Add]** nel **[!UICONTROL List of enumeration values]**:

   * In **[!UICONTROL Source]** , immettere il valore di origine per ogni genere (0,1,2) in una nuova riga.
   * In **[!UICONTROL Destination]** , immettere i valori: &quot;Non indicato&quot; per la riga &quot;0&quot;, &quot;Maschio&quot; per la riga &quot;1&quot; e &quot;Femmina&quot; per la riga &quot;2&quot;.

   Seleziona la **[!UICONTROL Keep the source value]** funzione.

   Clic **[!UICONTROL OK]** per approvare il campo calcolato.

   ![](assets/query_editor_nveau_77.png)

1. In **[!UICONTROL Data formatting]** finestra, fai clic su **[!UICONTROL Next]**.
1. Nella finestra di anteprima, **[!UICONTROL start the preview of the data]**.

   La colonna aggiuntiva definisce il genere 0, 1 e 2:

   * 0 per &quot;Non indicato&quot;
   * 1 per &quot;Maschio&quot;
   * 2 per &quot;Femmina&quot;

   ![](assets/query_editor_nveau_78.png)

   Ad esempio, se non immetti il genere &quot;2&quot; nel campo **[!UICONTROL List of enumeration values]** e **[!UICONTROL Generate a warning and continue]** funzione del **[!UICONTROL In other cases]** è selezionato, verrà visualizzato un registro di avvisi. Questo registro indica che non è stato immesso il genere &quot;2&quot; (Femmina). Viene visualizzato nel **[!UICONTROL Logs generated during export]** della finestra di anteprima dei dati.

   ![](assets/query_editor_nveau_79.png)

   Prendiamo un altro esempio e diciamo che il valore di enumerazione &quot;2&quot; non è inserito. Seleziona la **[!UICONTROL Generate an error and reject the line]** funzione: tutti i destinatari di genere &quot;2&quot; solleveranno anomalie e le altre informazioni nella riga (nome e cognome, ecc.) non verrà esportato. Un registro degli errori viene visualizzato in **[!UICONTROL Logs generated during export]** della finestra di anteprima dei dati. Questo registro indica che non è stato immesso il valore di enumerazione &quot;2&quot;.

   ![](assets/query_editor_nveau_80.png)
