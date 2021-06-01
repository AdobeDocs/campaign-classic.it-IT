---
product: campaign
title: Aggiunta di un campo calcolato di tipo Enumerazione
description: Scopri come aggiungere un campo calcolato di tipo Enumerazione
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 0%

---

# Aggiunta di un campo calcolato di tipo Enumerazione {#adding-an-enumeration-type-calculated-field}

Qui si desidera creare una query con un campo calcolato di tipo **[!UICONTROL Enumerations]**. Questo campo genera una colonna aggiuntiva nella finestra di anteprima dati. Questa colonna specifica i valori numerici restituiti come risultato per ciascun destinatario (0, 1 e 2). A ogni valore della nuova colonna verrà assegnato un genere: &quot;Uomo&quot; per &quot;1&quot;, &quot;Donna&quot; per &quot;2&quot; o &quot;Non indicato&quot; se il valore è uguale a &quot;0&quot;.

* Quale tabella deve essere selezionata?

   Tabella dei destinatari (nms:recipient)

* Campi da selezionare nella colonna di output?

   Cognome, Nome, Genere

* Criteri su cui verranno filtrate le informazioni?

   Lingua di destinazione

Applica i seguenti passaggi:

1. Apri l’editor di query generico e seleziona la tabella Destinatario (**[!UICONTROL nms:recipient]**).
1. Nella finestra **[!UICONTROL Data to extract]**, selezionare **[!UICONTROL Last name]**, **[!UICONTROL First name]** e **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. Nella finestra **[!UICONTROL Sorting]**, fai clic su **[!UICONTROL Next]**: non è necessario alcun tipo di ordinamento per questo esempio.
1. In **[!UICONTROL Data filtering]**, seleziona **[!UICONTROL Filtering conditions]**.
1. Nella finestra **[!UICONTROL Target element]** , imposta una condizione di filtro per raccogliere i destinatari che parlano inglese.

   ![](assets/query_editor_nveau_74.png)

1. Nella finestra **[!UICONTROL Data formatting]**, fai clic su **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. Vai alla finestra **[!UICONTROL Type]** della finestra **[!UICONTROL Export calculated field definition]** e seleziona **[!UICONTROL Enumerations]**.

   Definire la colonna a cui deve fare riferimento il nuovo campo calcolato. A questo scopo, seleziona la colonna **[!UICONTROL Gender]** nel menu a discesa del campo **[!UICONTROL Source column]** : i valori di destinazione coincideranno con la colonna **[!UICONTROL Gender]** .

   ![](assets/query_editor_nveau_76.png)

   Definisci i valori **Origine** e **Destinazione**: il valore di destinazione facilita la lettura del risultato della query. Questa query deve restituire il genere del destinatario e il risultato sarà 0, 1 o 2.

   Per ogni riga di &quot;destinazione di origine&quot; da immettere, fai clic su **[!UICONTROL Add]** in **[!UICONTROL List of enumeration values]**:

   * Nella colonna **[!UICONTROL Source]**, immetti il valore sorgente per ogni genere (0,1,2) in una nuova riga.
   * Nella colonna **[!UICONTROL Destination]** , immetti i valori seguenti: &quot;Non indicato&quot; per la riga &quot;0&quot;, &quot;Uomo&quot; per la riga &quot;1&quot; e &quot;Donna&quot; per la riga &quot;2&quot;.

   Selezionare la funzione **[!UICONTROL Keep the source value]**.

   Fai clic su **[!UICONTROL OK]** per approvare il campo calcolato.

   ![](assets/query_editor_nveau_77.png)

1. Nella finestra **[!UICONTROL Data formatting]**, fai clic su **[!UICONTROL Next]**.
1. Nella finestra di anteprima, **[!UICONTROL start the preview of the data]**.

   La colonna aggiuntiva definisce il genere di 0, 1 e 2:

   * 0 per &quot;Non indicato&quot;
   * 1 per &quot;Uomo&quot;
   * 2 per &quot;Femmina&quot;

   ![](assets/query_editor_nveau_78.png)

   Ad esempio, se non immetti gender &quot;2&quot; nel campo **[!UICONTROL List of enumeration values]** e la funzione **[!UICONTROL Generate a warning and continue]** del campo **[!UICONTROL In other cases]** è selezionata, riceverai un registro di avviso. Questo registro indica che il genere &quot;2&quot; (Femmina) non è stato inserito. Viene visualizzato nel campo **[!UICONTROL Logs generated during export]** della finestra di anteprima dati.

   ![](assets/query_editor_nveau_79.png)

   Prendiamo un altro esempio e diciamo che il valore di enumerazione &quot;2&quot; non è inserito. Seleziona la funzione **[!UICONTROL Generate an error and reject the line]**: tutti i destinatari &quot;2&quot; di genere genereranno anomalie e altre informazioni nella riga (nome e cognome, ecc.) non verranno esportati. Nel campo **[!UICONTROL Logs generated during export]** della finestra di anteprima dati viene visualizzato un registro degli errori. Questo registro indica che il valore di enumerazione &quot;2&quot; non è inserito.

   ![](assets/query_editor_nveau_80.png)
