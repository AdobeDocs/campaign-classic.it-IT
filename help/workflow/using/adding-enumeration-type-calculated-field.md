---
solution: Campaign Classic
product: campaign
title: Aggiunta di un campo calcolato di tipo enumerazione
description: Scopri come aggiungere un campo calcolato di tipo enumerazione
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---


# Adding an Enumeration type calculated field {#adding-an-enumeration-type-calculated-field}

Qui si desidera creare una query con un campo calcolato di **[!UICONTROL Enumerations]** tipo. Questo campo genererà una colonna aggiuntiva nella finestra di anteprima dei dati. Questa colonna specifica i valori numerici restituiti come risultato per ciascun destinatario (0, 1 e 2). A ogni valore della nuova colonna verrà assegnato un genere: &quot;Maschio&quot; per &quot;1&quot;, &quot;Femmina&quot; per &quot;2&quot; o &quot;Non indicato&quot; se il valore è uguale a &quot;0&quot;.

* Quale tabella deve essere selezionata?

   Tabella destinatari (nms:destinatario)

* Campi da selezionare nella colonna di output?

   Cognome, Nome, Genere

* Criteri su cui verranno filtrate le informazioni?

   La lingua del destinatario

Effettuate le seguenti operazioni:

1. Aprite l’editor di query generico e selezionate la tabella Destinatario (**[!UICONTROL nms:recipient]**).
1. Nella **[!UICONTROL Data to extract]** finestra selezionare **[!UICONTROL Last name]**, **[!UICONTROL First name]** e **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. Nella **[!UICONTROL Sorting]** finestra, fate clic su **[!UICONTROL Next]**: non è necessario alcun ordinamento per questo esempio.
1. In **[!UICONTROL Data filtering]**, seleziona **[!UICONTROL Filtering conditions]**.
1. Nella **[!UICONTROL Target element]** finestra, impostate una condizione di filtro per raccogliere i destinatari che parlano inglese.

   ![](assets/query_editor_nveau_74.png)

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Passare alla **[!UICONTROL Type]** finestra della **[!UICONTROL Export calculated field definition]** finestra e selezionare **[!UICONTROL Enumerations]**.

   Definire la colonna a cui deve fare riferimento il nuovo campo calcolato. A questo scopo, selezionate la **[!UICONTROL Gender]** colonna nel menu a discesa del **[!UICONTROL Source column]** campo: i valori di destinazione coincideranno con la **[!UICONTROL Gender]** colonna.

   ![](assets/query_editor_nveau_76.png)

   Definire i valori **Origine** e **Destinazione** : il valore di destinazione semplifica la lettura del risultato della query. Questa query deve restituire il genere del destinatario e il risultato sarà 0, 1 o 2.

   Per ogni riga di &quot;destinazione di origine&quot; da inserire, fate clic **[!UICONTROL Add]** in **[!UICONTROL List of enumeration values]**:

   * Nella **[!UICONTROL Source]** colonna, immettere il valore di origine per ogni genere (0,1,2) in una nuova riga.
   * Nella **[!UICONTROL Destination]** colonna, inserite i valori: &quot;Non indicato&quot; per la riga &quot;0&quot;, &quot;Maschio&quot; per la riga &quot;1&quot; e &quot;Donna&quot; per la riga &quot;2&quot;.

   Selezionare la **[!UICONTROL Keep the source value]** funzione.

   Fare clic **[!UICONTROL OK]** per approvare il campo calcolato.

   ![](assets/query_editor_nveau_77.png)

1. In the **[!UICONTROL Data formatting]** window, click **[!UICONTROL Next]**.
1. Nella finestra di anteprima, **[!UICONTROL start the preview of the data]**.

   La colonna aggiuntiva definisce il genere di 0, 1 e 2:

   * 0 per &quot;Non indicato&quot;
   * 1 for &quot;Maschio&quot;
   * 2 for &quot;Femmina&quot;

   ![](assets/query_editor_nveau_78.png)

   Ad esempio, se non si inserisce il genere &quot;2&quot; nel campo **[!UICONTROL List of enumeration values]**, e la **[!UICONTROL Generate a warning and continue]** funzione del **[!UICONTROL In other cases]** campo è selezionata, verrà visualizzato un registro di avvisi. Questo registro indica che il genere &quot;2&quot; (femmina) non è stato immesso. Viene visualizzato nel **[!UICONTROL Logs generated during export]** campo della finestra di anteprima dei dati.

   ![](assets/query_editor_nveau_79.png)

   Prendiamo un altro esempio e diciamo che il valore di enumerazione &quot;2&quot; non è immesso. Selezionare la **[!UICONTROL Generate an error and reject the line]** funzione: tutti i destinatari &quot;2&quot; di genere segnaleranno anomalie e altre informazioni nella riga (nome e cognome, ecc.) non verranno esportati. Nel **[!UICONTROL Logs generated during export]** campo della finestra di anteprima dei dati viene visualizzato un registro degli errori. Questo registro indica che il valore di enumerazione &quot;2&quot; non è stato immesso.

   ![](assets/query_editor_nveau_80.png)
