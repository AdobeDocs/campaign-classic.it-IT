---
product: campaign
title: Definizione delle condizioni del filtro
description: Definizione delle condizioni del filtro
feature: Query Editor
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
hide: true
hidefromtoc: true
exl-id: b62e23e5-f1b7-44c4-82d9-95c6b3240352
source-git-commit: 11c81e4f04b978381d3803e2b60e23ed791eee44
workflow-type: tm+mt
source-wordcount: '3304'
ht-degree: 48%

---

# Definire le condizioni del filtro{#defining-filter-conditions}



## Scegli l’operatore {#choosing-the-operator}

All’interno delle condizioni di filtro, devi collegare due valori tra loro utilizzando un operatore.

![](assets/query_editor_nveau_96.png)

Di seguito è riportato un elenco degli operatori disponibili:

<table> 
 <thead> 
  <tr> 
   <th> Operatore<br /> </th> 
   <th> Finalità<br /> </th> 
   <th> Esempio<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <span class="uicontrol">Uguale a</span> <br /> </td> 
   <td> Restituisce un risultato identico ai dati immessi nella seconda colonna Valore.<br /> </td> 
   <td> <strong>Cognome (@lastName) uguale a 'Jones'</strong>, restituirà solo i destinatari il cui cognome è Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Maggiore di</span> <br /> </td> 
   <td> Restituisce un valore maggiore del valore immesso.<br /> </td> 
   <td> <strong>L'età (@age) maggiore di 50</strong> restituirà tutti i valori maggiori di '50', ovvero '51', '52', ecc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Minore di</span> <br /> </td> 
   <td> Restituisce un valore minore del valore immesso.<br /> </td> 
   <td> <strong>La data di creazione (@created) prima di 'DaysAgo(100)'</strong>, restituirà tutti i destinatari creati meno di 100 giorni fa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Maggiore o uguale a</span> <br /> </td> 
   <td> Restituisce tutti i valori uguali o maggiori del valore immesso.<br /> </td> 
   <td> <strong>L'età (@age) maggiore o uguale a '30'</strong> restituirà tutti i destinatari di almeno 30 anni.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Minore o uguale a</span> <br /> </td> 
   <td> Restituisce tutti i valori uguali o inferiori al valore immesso.<br /> </td> 
   <td> <strong>L'età (@age) minore o uguale a '60'</strong> restituirà tutti i destinatari di età inferiore o uguale a 60 anni.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Diverso da</span> <br /> </td> 
   <td> Restituisce tutti i valori non identici al valore immesso.<br /> </td> 
   <td> <strong>Lingua (@language) uguale a 'Inglese'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Inizia con</span> <br /> </td> 
   <td> Restituisce i risultati a partire dal valore immesso.<br /> </td> 
   <td> <strong>Il numero di account (@account) inizia con "32010".</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non inizia con</span> <br /> </td> 
   <td> Restituisce i risultati che non iniziano con il valore immesso<br /> </td> 
   <td> <strong>Il numero di account (@account) non inizia con '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contiene</span> <br /> </td> 
   <td> Restituisce i risultati contenenti almeno il valore immesso.<br /> </td> 
   <td> <strong>Il dominio e-mail (@domain) contiene 'mail'</strong>, restituirà tutti i nomi di dominio che contengono 'mail'. Verrà restituito anche il dominio 'gmail.com'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non contiene</span> <br /> </td> 
   <td> Restituisce risultati che non contengono il valore immesso.<br /> </td> 
   <td> <strong>Il dominio e-mail (@domain) non contiene 'vo'</strong>. In questo caso, i nomi di dominio che contengono “vo” non verranno restituiti. Il nome di dominio 'voilà.fr' non verrà visualizzato nei risultati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Simile</span> <br /> </td> 
   <td> <span class="uicontrol">Simile</span> è molto simile all’operatore <span class="uicontrol">Contains</span>. Ti consente di inserire un carattere jolly <span class="uicontrol">%</span> nel valore.<br /> </td> 
   <td> <strong>Cognome (@lastName) come 'Jon%s'</strong>. In questo caso, il carattere jolly viene utilizzato come "jolly" per trovare il nome "Jones", qualora l'operatore avesse dimenticato la lettera mancante tra "n" e "s".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Diverso</span> <br /> </td> 
   <td> È simile a <span class="uicontrol">Like</span> . Consente di non recuperare il valore immesso. Anche in questo caso, il valore immesso deve contenere il carattere jolly <span class="uicontrol">%</span>.<br /> </td> 
   <td> <strong>Cognome (@lastName) diverso da 'Smi%h'</strong>. In questo caso, i destinatari il cui cognome è 'Smi%h' non verranno restituiti.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">È vuoto</span> <br /> </td> 
   <td> In questo caso, il risultato che si sta cercando corrisponde a un valore vuoto nella seconda colonna Valore.<br /> </td> 
   <td> <strong>Il cellulare (@mobilePhone) è vuoto</strong> restituisce tutti i destinatari che non hanno un numero di cellulare.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non è vuoto</span> <br /> </td> 
   <td> Funziona in modo inverso all'operatore <span class="uicontrol">Is empty</span>. Non è necessario immettere dati nella seconda colonna Valore.<br /> </td> 
   <td> <strong>L'indirizzo e-mail (@email) non è vuoto</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">È incluso in</span> <br /> </td> 
   <td> Restituisce i risultati inclusi nei valori indicati. Questi valori devono essere separati da una virgola.<br /> </td> 
   <td> <strong>La data di nascita (@birthDate) è inclusa in '12/10/1979,12/10/1984'</strong> e restituirà i destinatari nati tra queste date. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non è incluso in</span> <br /> </td> 
   <td> Funziona come l'operatore <span class="uicontrol">è incluso nell'operatore </span>. In questo caso, si desidera escludere i destinatari in base ai valori immessi.<br /> </td> 
   <td> <strong>La data di nascita (@birthDate) non è inclusa in '12/10/1979,12/10/1984'</strong>. A differenza dell'esempio precedente, i destinatari nati in queste date non verranno restituiti.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## Usa AND, OR, EXCEPT {#using-and--or--except}

Per le query che utilizzano diverse condizioni di filtro, è necessario definire collegamenti tra le condizioni. Sono disponibili tre collegamenti possibili:

* **[!UICONTROL And]** consente di combinare due condizioni di filtro:
* **[!UICONTROL Or]** ti consente di offrire un&#39;alternativa,
* **[!UICONTROL Except]** consente di definire un&#39;eccezione.

Fare clic su **[!UICONTROL And]** (offerta predefinita) e scegliere dall&#39;elenco a discesa.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**: aggiunge una condizione e abilita l&#39;overfilter.
* **[!UICONTROL Or]**: aggiunge una condizione e abilita l&#39;overfilter.

  L’esempio seguente consente di trovare i destinatari il cui dominio e-mail contiene &quot;orange.co.uk&quot; O il cui codice post inizia con &quot;NW&quot;.

  ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**: se si dispone di due filtri e il primo non restituisce un valore, questo tipo di collegamento crea un&#39;eccezione.

  Nell’esempio seguente, vogliamo restituire i destinatari il cui dominio e-mail contiene &quot;orange.co.uk&quot; ECCETTO se il cognome del destinatario è &quot;Smith&quot;.

  ![](assets/query_condition_modif_03.png)

Questo esempio mostra un filtro che consente di visualizzare: i destinatari che parlano spagnolo, OPPURE sono donne con numeri di cellulare, OPPURE i destinatari senza un numero di account e il cui nome azienda inizia con la lettera &quot;N&quot;.

![](assets/query_editor_nveau_31.png)

## Stabilire le priorità delle condizioni {#prioritizing-conditions}

Questa sezione spiega come assegnare la priorità alle condizioni grazie alle frecce blu nella barra degli strumenti.

* La freccia rivolta verso destra consente di aggiungere un livello di parentesi al filtro.
* La freccia rivolta a sinistra consente di eliminare un livello di parentesi selezionato dal filtro.

  ![](assets/query_condition_modif_04.png)

* Le frecce verticali consentono di spostare una condizione, modificando in tal modo la relativa sequenza di esecuzione.

Questo esempio mostra come utilizzare la freccia per eliminare un livello di parentesi. Inizia dalla seguente condizione di filtro: **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

Posizionare il cursore sulla condizione di filtro **[!UICONTROL Gender (@gender) equal to Male]** e fare clic sulla freccia **[!UICONTROL Remove a parenthesis level]**.

![](assets/query_editor_nveau_32.png)

La condizione **[!UICONTROL Gender (@gender) equal to Male]** è stata rimossa dalle parentesi. Si è spostato allo stesso livello della condizione &quot;City equal to London&quot;. Queste condizioni sono collegate (**[!UICONTROL And]**).

## Seleziona i dati da estrarre {#selecting-data-to-extract}

I campi disponibili variano da una tabella all’altra. Tutti i campi sono archiviati in un nodo principale noto come **[!UICONTROL Main element]**. Nell&#39;esempio seguente, i campi disponibili si trovano nella tabella recipient. I campi vengono sempre visualizzati in ordine alfabetico.

Il dettaglio del campo selezionato è visibile nella parte inferiore della finestra. Ad esempio, il campo **[!UICONTROL Email domain]** è un **[!UICONTROL Calculated SQL field]** e la sua estensione è **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Utilizzare lo strumento **[!UICONTROL Search]** per trovare un campo disponibile.

Fare doppio clic su un campo disponibile per aggiungerlo alle colonne di output. Alla fine della query, ogni campo selezionato crea una colonna nella finestra **[!UICONTROL Data preview]**.

![](assets/query_editor_nveau_01.png)

Per impostazione predefinita, i campi Avanzate non vengono visualizzati. Fai clic su **[!UICONTROL Display advanced fields]** nell&#39;angolo in basso a destra dei campi disponibili per visualizzare tutto. Fai di nuovo clic su per tornare alla vista precedente.

Ad esempio, nella tabella dei destinatari i campi avanzati sono **Boolean 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]** e così via.

Nell&#39;esempio seguente vengono illustrati i campi avanzati della tabella recipient.

![](assets/query_editor_nveau_53.png)

Le varie categorie di campi:

<table> 
 <thead> 
  <tr> 
   <th> Icona<br /> </th> 
   <th> Descrizione<br /> </th> 
   <th> Esempi<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_47.png" /> </td> 
   <td> Campo semplice<br /> </td> 
   <td> E-mail, genere, ecc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_48.png" /> </td> 
   <td> Chiave primaria. Questo campo SQL consente di identificare un record in una tabella.<br /> </td> 
   <td> I destinatari dell'identificatore sono chiavi primarie e gli identificatori sono univoci per definizione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Chiave esterna. Utilizzato come collegamento a un'altra tabella.<br /> </td> 
   <td> Chiave esterna destinatario, chiave esterna servizio, ecc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Campo calcolato. Questo tipo di campo viene calcolato su richiesta utilizzando i valori nel database.<br /> </td> 
   <td> Età, dominio e-mail, ecc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_49.png" /> </td> 
   <td> Campo contenente testi lunghi.<br /> </td> 
   <td> Commento, indirizzo completo, ecc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_50.png" /> </td> 
   <td> Campo SQL indicizzato. <br /> </td> 
   <td> Nome completo, codice ISO e così via <br /> </td> 
  </tr> 
 </tbody> 
</table>

Collegamento a un elemento tabella e raccolta:

<table> 
 <thead> 
  <tr> 
   <th> Icona<br /> </th> 
   <th> Descrizione<br /> </th> 
   <th> Esempio<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_51.png" /> </td> 
   <td> Collegamenti a una tabella in particolare. Queste coincidono con le associazioni di tipo 1-1. Un'occorrenza della tabella di origine può coincidere con una sola occorrenza della tabella di destinazione. Ad esempio, un solo destinatario può essere collegato a un paese.<br /> </td> 
   <td> Cartella, Stato, Paese ecc. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Elemento di raccolta in una tabella specifica. Questi coincidono con le associazioni di tipo 1-N. Una occorrenza della tabella di origine può coincidere con diverse occorrenze della tabella di destinazione, ma una occorrenza della tabella di destinazione può coincidere con una sola occorrenza della tabella di origine. Ad esempio, un destinatario può sottoscrivere 'n' lettere di abbonamento.<br /> </td> 
   <td> Sottoscrizioni, elenchi, registri di esclusione e così via<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Utilizza il pulsante **[!UICONTROL Add]** (sopra la barra delle icone laterali) per aggiungere una colonna di output in cui modificare l&#39;espressione. Per ulteriori informazioni sulla modifica di un&#39;espressione, consultare [questa sezione](#building-expressions).
>* Eliminare una colonna di output facendo clic sulla &quot;x&quot; rossa (**Elimina**).
>* Modifica l’ordine delle colonne di output utilizzando le frecce.
>* **[!UICONTROL Distribution of values]** consente di visualizzare la distribuzione dei valori del campo selezionato (ad esempio, le distribuzioni collegate alle città dei destinatari, alle lingue dei destinatari e così via).

## Creare campi calcolati {#creating-calculated-fields}

Se necessario, aggiungi una colonna durante la formattazione dei dati. Un campo calcolato aggiunge una colonna alla sezione di anteprima dei dati. Fai clic su **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

Esistono quattro tipi di campi calcolati:

* **[!UICONTROL Fixed string]**: consente di aggiungere una stringa di caratteri.

  ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**: il valore del campo calcolato combina una stringa di caratteri e direttive JavaScript.

  ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**: il valore del campo calcolato è il risultato di una valutazione della funzione JavaScript. È possibile digitare il valore restituito (numero, data, ecc.).

  ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**: questo tipo di campo consente di utilizzare o modificare il contenuto di una delle colonne di output in una nuova colonna.

  È possibile utilizzare il valore di origine di una colonna e assegnargli un valore di destinazione. Questo valore di destinazione verrà visualizzato nella nuova colonna di output.

  È disponibile un esempio di aggiunta del tipo di campo calcolato **[!UICONTROL Enumerations]**. Fare riferimento a [questa sezione](../../workflow/using/adding-enumeration-type-calculated-field.md).

  ![](assets/query_editor_nveau_63.png)

  Il campo calcolato di tipo **[!UICONTROL Enumerations]** può includere 4 condizioni:

   * **[!UICONTROL Keep the source value]** ripristina il valore di origine nella destinazione senza modificarlo.
   * **[!UICONTROL Use the following value]** consente di immettere un valore di destinazione predefinito per i valori di origine non definiti.
   * **[!UICONTROL Generate a warning and continue]** avverte l&#39;utente che il valore di origine non può essere modificato.
   * **[!UICONTROL Generate an error and reject the line]** impedisce il calcolo e l&#39;importazione della riga.

Fare clic su **[!UICONTROL Detail of calculated field]** per visualizzare i dettagli del campo inserito.

Per rimuovere questo campo calcolato, fare clic sull&#39;intersezione **[!UICONTROL Remove the calculated field]**.

![](assets/query_editor_nveau_58.png)

## Creare espressioni {#building-expressions}

Lo strumento di modifica delle espressioni consente di calcolare aggregati, generare funzioni o modificare una formula utilizzando un&#39;espressione.

Nell&#39;esempio seguente viene illustrato come eseguire un conteggio su una chiave primaria.

Applica i seguenti passaggi:

1. Fare clic su **[!UICONTROL Add]** nella finestra **[!UICONTROL Data to extract]**. Nella finestra **[!UICONTROL Formula type]**, selezionare un tipo di formula per immettere l&#39;espressione.

   Sono disponibili diversi tipi di formule: **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   Selezionare **[!UICONTROL Process on an aggregate function]** e **[!UICONTROL Count]**. Fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. Viene calcolata la chiave primaria.

   ![](assets/query_editor_nveau_88.png)

Visualizzazione dettagliata delle scelte disponibili nella finestra **[!UICONTROL Formula types]**:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** consente di tornare alla finestra **[!UICONTROL Field to select]**.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. Di seguito sono riportati alcuni esempi di utilizzo aggregato:

   * **[!UICONTROL Count]** consente di eseguire un conteggio di chiavi primarie.
   * **[!UICONTROL Sum]** consente di sommare tutti gli acquisti effettuati da un cliente in un anno.
   * **[!UICONTROL Maximum value]** consente di trovare i clienti che hanno acquistato la maggior parte dei prodotti &quot;n&quot;.
   * **[!UICONTROL Minimum value]** consente di ordinare i clienti e di trovare quelli che si sono abbonati a un&#39;offerta più di recente.
   * **[!UICONTROL Average]**. Questa funzione ti consente di calcolare l’età media dei destinatari.

     La casella **[!UICONTROL Distinct]** consente di recuperare valori univoci e diversi da zero di una colonna. Ad esempio, puoi recuperare tutti i registri di tracciamento di un destinatario e questi registri di tracciamento vengono modificati con il valore 1, in quanto riguardano tutti lo stesso destinatario.

1. **[!UICONTROL Expression]** apre la finestra **[!UICONTROL Edit the expression]**. Questo consente di rilevare numeri di telefono con troppe cifre, che potrebbero essere errori di input.

   ![](assets/query_editor_nveau_71.png)

   Per un elenco di tutte le funzioni disponibili, fare riferimento a [Elenco di funzioni](#list-of-functions).

## Elenco delle funzioni {#list-of-functions}

Se viene scelta una formula di tipo **[!UICONTROL Expression]**, verrà visualizzata la finestra &quot;Modifica espressione&quot;. Ai campi disponibili possono essere associate varie categorie di funzioni: **[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** e **[!UICONTROL Others]**.

L’editor espressioni si presenta così:

![](assets/s_ncs_user_filter_define_expression.png)

Consente di selezionare i campi nelle tabelle del database e di aggiungere funzioni avanzate. Sono disponibili le seguenti funzioni:

**Aggregati**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Avg</strong><br /> </td> 
   <td> Restituisce la media di una colonna di tipo numerico<br /> </td> 
   <td> Avg(&lt;valore&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Conteggio</strong><br /> </td> 
   <td> Conta i valori non nulli in una colonna<br /> </td> 
   <td> Count(&lt;valore&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Conta i valori restituiti (tutti i campi)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> Conta i valori distinti non nulli in una colonna<br /> </td> 
   <td> Countdistinct(&lt;valore&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Restituisce il valore massimo in una colonna numerica, stringa o data<br /> </td> 
   <td> Max(&lt;valore&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Restituisce il valore minimo in una colonna numerica, stringa o data.<br /> </td> 
   <td> Min(&lt;valore&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Restituisce la deviazione standard in una colonna numerica, stringa o data<br /> </td> 
   <td> StdDev(&lt;valore&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Somma</strong><br /> </td> 
   <td> Restituisce la somma dei valori in una colonna numerica, stringa o data<br /> </td> 
   <td> Sum(&lt;valore&gt;)<br /></td> 
  </tr> 
 </tbody> 
</table>

**Stringa**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull2</strong><br /> </td> 
   <td> Indica se tutti i parametri non sono nulli e non sono vuoti<br /> </td> 
   <td> AllNonNull2(&lt;stringa&gt;, &lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>AllNonNull3</strong><br /> </td> 
   <td> Indica se tutti i parametri non sono nulli e non sono vuoti<br /> </td> 
   <td> AllNonNull3(&lt;stringa&gt;, &lt;stringa&gt;, &lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ascii</strong><br /> </td> 
   <td> Restituisce il valore ASCII del primo carattere della stringa<br /> </td> 
   <td> Ascii(&lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Char</strong><br /> </td> 
   <td> Restituisce il carattere corrispondente al codice ASCII “n”<br /> </td> 
   <td> Char(&lt;numero&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Charindex</strong><br /> </td> 
   <td> Restituisce la posizione della stringa 2 nella stringa 1.<br /> </td> 
   <td> Charindex(&lt;stringa&gt;, &lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>GetLine</strong><br /> </td> 
   <td> Restituisce l’ennesima riga (da 1 a n) della stringa<br /> </td> 
   <td> GetLine(&lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IfEquals</strong><br /> </td> 
   <td> Restituisce il terzo parametro se i primi due parametri sono uguali. In caso contrario, restituisce l’ultimo parametro<br /> </td> 
   <td> IfEquals(&lt;stringa&gt;, &lt;stringa&gt;, &lt;stringa&gt;, &lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Indica se il promemoria passato come parametro è nullo<br /> </td> 
   <td> IsMemoNull(&lt;promemoria&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords</strong><br /> </td> 
   <td> Concatena le stringhe passate come parametri. Se necessario, aggiunge spazi tra le stringhe.<br /> </td> 
   <td> JuxtWords(&lt;stringa&gt;, &lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>JuxtWords3</strong><br /> </td> 
   <td> Concatena le stringhe passate come parametri. Se necessario, aggiunge spazi tra le stringhe<br /> </td> 
   <td> JuxtWords3(&lt;stringa&gt;, &lt;stringa&gt;, &lt;stringa&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>LPad</strong><br /> </td> 
   <td> Restituisce la stringa completata a sinistra<br /> </td> 
   <td> LPad(&lt;stringa&gt;, &lt;numero&gt;, &lt;carattere&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Left</strong><br /> </td> 
   <td> Restituisce i primi n caratteri della stringa<br /> </td> 
   <td> Left(&lt;stringa&gt;, &lt;numero&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Length</strong><br /> </td> 
   <td> Restituisce la lunghezza della stringa<br /> </td> 
   <td> Length(&lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Lower</strong><br /> </td> 
   <td> Restituisce la stringa in caratteri minuscoli<br /> </td> 
   <td> Lower(&lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Ltrim</strong><br /> </td> 
   <td> Rimuove gli spazi a sinistra della stringa<br /> </td> 
   <td> Ltrim(&lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Md5Digest</strong><br /> </td> 
   <td> Restituisce una rappresentazione esadecimale della chiave MD5 di una stringa<br /> </td> 
   <td> Md5Digest(&lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>MemoContains</strong><br /> </td> 
   <td> Specifica se il promemoria contiene la stringa passata come parametro<br /> </td> 
   <td> MemoContains(&lt;promemoria&gt;, &lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>RPad</strong><br /> </td> 
   <td> Restituisce la stringa completata a destra<br /> </td> 
   <td> RPad(&lt;stringa&gt;, &lt;numero&gt;, &lt;carattere&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Right</strong><br /> </td> 
   <td> Restituisce gli ultimi n caratteri della stringa<br /> </td> 
   <td> Right(&lt;stringa&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Rtrim</strong><br /> </td> 
   <td> Rimuove gli spazi a destra della stringa<br /> </td> 
   <td> Rtrim(&lt;stringa&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Smart</strong><br /> </td> 
   <td> Restituisce la stringa con la prima lettera di ciascuna parola in maiuscolo<br /> </td> 
   <td> Smart(&lt;stringa&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Substring</strong><br /> </td> 
   <td> Estrae la stringa secondaria a partire dal carattere n1 della stringa e con una lunghezza n2<br /> </td> 
   <td> Substring(&lt;stringa&gt;, &lt;offset&gt;, &lt;lunghezza&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Converte il numero in una stringa<br /> </td> 
   <td> ToString(&lt;numero&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Upper</strong><br /> </td> 
   <td> Restituisce la stringa in caratteri maiuscoli<br /> </td> 
   <td> Upper(&lt;stringa&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLink</strong><br /> </td> 
   <td> Restituisce la chiave esterna di un collegamento passato come parametro se gli altri due parametri sono uguali<br /> </td> 
   <td> VirtualLink(&lt;numero&gt;, &lt;numero&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>VirtualLinkStr</strong><br /> </td> 
   <td> Restituisce la chiave esterna (testo) di un collegamento passato come parametro se gli altri due parametri sono uguali<br /> </td> 
   <td> VirtualLinkStr(&lt;stringa&gt;, &lt;numero&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>dataLength</strong><br /> </td> 
   <td> Restituisce le dimensioni della stringa<br /> </td> 
   <td> dataLength(&lt;stringa&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Data**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>AddDays</strong><br /> </td> 
   <td> Aggiunge un numero di giorni a una data<br /> </td> 
   <td> AddDays(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddHours</strong><br /> </td> 
   <td> Aggiunge un numero di ore a una data<br /> </td> 
   <td> AddHours(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMinutes</strong><br /> </td> 
   <td> Aggiunge un numero di minuti a una data<br /> </td> 
   <td> AddMinutes(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddMonths</strong><br /> </td> 
   <td> Aggiunge un numero di mesi a una data<br /> </td> 
   <td> AddMonths(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddSeconds</strong><br /> </td> 
   <td> Aggiunge un numero di secondi a una data<br /> </td> 
   <td> AddSeconds(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>AddYears</strong><br /> </td> 
   <td> Aggiunge un numero di anni a una data<br /> </td> 
   <td> AddYears(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DateOnly</strong><br /> </td> 
   <td> Restituisce solo la data (con l’ora su 00.00)*<br /> </td> 
   <td> DateOnly(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Day</strong><br /> </td> 
   <td> Restituisce il numero che rappresenta il giorno della data<br /> </td> 
   <td> Day(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DayOfYear</strong><br /> </td> 
   <td> Restituisce un numero del giorno dell’anno della data<br /> </td> 
   <td> DayOfYear(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Restituisce la data corrispondente alla data corrente meno n giorni<br /> </td> 
   <td> DaysAgo(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Restituisce la data corrispondente (numero intero aaaammgg) alla data corrente meno n giorni<br /> </td> 
   <td> DaysAgoInt(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysDiff</strong><br /> </td> 
   <td> Numero di giorni tra due date<br /> </td> 
   <td> DaysDiff(&lt;data di fine&gt;, &lt;data di inizio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysOld</strong><br /> </td> 
   <td> Restituisce l’età in giorni di una data<br /> </td> 
   <td> DaysOld(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetDate</strong><br /> </td> 
   <td> Restituisce la data di sistema corrente del server<br /> </td> 
   <td> GetDate()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Hour</strong><br /> </td> 
   <td> Restituisce l’ora della data<br /> </td> 
   <td> Hour(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>HoursDiff</strong><br /> </td> 
   <td> Restituisce il numero di ore tra due date<br /> </td> 
   <td> HoursDiff(&lt;data di fine&gt;, &lt;data di inizio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Minute</strong><br /> </td> 
   <td> Restituisce i minuti della data<br /> </td> 
   <td> Minute(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MinutesDiff</strong><br /> </td> 
   <td> Restituisce il numero di minuti tra due date<br /> </td> 
   <td> MinutesDiff(&lt;data di fine&gt;, &lt;data di inizio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Month</strong><br /> </td> 
   <td> Restituisce il numero che rappresenta il mese della data<br /> </td> 
   <td> Month(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsAgo</strong><br /> </td> 
   <td> Restituisce la data corrispondente alla data corrente meno n mesi<br /> </td> 
   <td> MonthsAgo(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsDiff</strong><br /> </td> 
   <td> Restituisce il numero di mesi tra due date<br /> </td> 
   <td> MonthsDiff(&lt;data di fine&gt;, &lt;data di inizio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>MonthsOld</strong><br /> </td> 
   <td> Restituisce l’età in mesi di una data<br /> </td> 
   <td> MonthsOld(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Second</strong><br /> </td> 
   <td> Restituisce i secondi della data<br /> </td> 
   <td> Second(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SecondsDiff</strong><br /> </td> 
   <td> Restituisce il numero di secondi tra due date<br /> </td> 
   <td> SecondsDiff(&lt;data di fine&gt;, &lt;data di inizio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubDays</strong><br /> </td> 
   <td> Sottrae un numero di giorni da una data<br /> </td> 
   <td> SubDays(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubHours</strong><br /> </td> 
   <td> Sottrae un numero di ore da una data<br /> </td> 
   <td> SubHours(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMinutes</strong><br /> </td> 
   <td> Sottrae un numero di minuti da una data<br /> </td> 
   <td> SubMinutes(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubMonths</strong><br /> </td> 
   <td> Sottrae un numero di mesi da una data<br /> </td> 
   <td> SubMonths(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubSeconds</strong><br /> </td> 
   <td> Sottrae un numero di secondi da una data<br /> </td> 
   <td> SubSeconds(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>SubYears</strong><br /> </td> 
   <td> Sottrae un numero di anni da una data<br /> </td> 
   <td> SubYears(&lt;data&gt;, &lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDate</strong><br /> </td> 
   <td> Converte una data + ora in una data<br /> </td> 
   <td> ToDate(&lt;data + ora&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDateTime</strong><br /> </td> 
   <td> Converte una stringa in una data + ora<br /> </td> 
   <td> ToDateTime(&lt;stringa&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncDate</strong><br /> </td> 
   <td> Arrotonda una data+ora al secondo più vicino<br /> </td> 
   <td> TruncDate(@lastModified, &lt;numero di secondi&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncDateTZ</strong><br /> </td> 
   <td> Arrotonda una data + ora a una determinata precisione, espressa in secondi<br /> </td> 
   <td> TruncDateTZ(&lt;data&gt;, &lt;numero di secondi&gt;, &lt;fuso orario&gt;)<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>TruncQuarter</strong><br /> </td> 
   <td> Arrotonda una data al trimestre<br /> </td> 
   <td> TruncQuarter(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncTime</strong><br /> </td> 
   <td> Arrotonda la parte dell’ora al secondo più vicino<br /> </td> 
   <td> TruncTime(&lt;data&gt;, &lt;numero di secondi&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Arrotonda una data alla settimana<br /> </td> 
   <td> TruncWeek(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncYear</strong><br /> </td> 
   <td> Arrotonda una data + ora al 1° gennaio dell’anno<br /> </td> 
   <td> TruncYear(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>TruncWeek</strong><br /> </td> 
   <td> Restituisce il numero che rappresenta il giorno della settimana della data<br /> </td> 
   <td> WeekDay(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Year</strong><br /> </td> 
   <td> Restituisce il numero che rappresenta l’anno della data<br /> </td> 
   <td> Year(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearAnd Month</strong><br /> </td> 
   <td> Restituisce il numero che rappresenta l’anno e il mese della data<br /> </td> 
   <td> YearAndMonth(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsDiff</strong><br /> </td> 
   <td> Restituisce il numero di anni tra le due date<br /> </td> 
   <td> YearsDiff(&lt;data di fine&gt;, &lt;data di inizio&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>YearsOld</strong><br /> </td> 
   <td> Restituisce l’età in anni di una data<br /> </td> 
   <td> YearsOld(&lt;data&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Tieni presente che la funzione **Dateonly** tiene conto del fuso orario del server, non di quello dell’operatore.

**Numerico**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Abs</strong><br /> </td> 
   <td> Restituisce il valore assoluto di un numero<br /> </td> 
   <td> Abs(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Ceil</strong><br /> </td> 
   <td> Restituisce il numero intero più piccolo maggiore o uguale a un numero<br /> </td> 
   <td> Ceil(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Floor</strong><br /> </td> 
   <td> Restituisce il numero intero maggiore o uguale a un numero<br /> </td> 
   <td> Floor(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Greatest</strong><br /> </td> 
   <td> Restituisce il numero maggiore tra due numeri<br /> </td> 
   <td> Greatest(&lt;numero 1&gt;, &lt;numero 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Least</strong><br /> </td> 
   <td> Restituisce il minore tra due numeri<br /> </td> 
   <td> Least(&lt;numero 1&gt;, &lt;numero 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Mod</strong><br /> </td> 
   <td> Restituisce il resto della divisione del numero intero da n1 per n2<br /> </td> 
   <td> Mod(&lt;numero 1&gt;, &lt;numero 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Percent</strong><br /> </td> 
   <td> Restituisce il rapporto tra due numeri espresso come percentuale<br /> </td> 
   <td> Percent(&lt;numero 1&gt;, &lt;numero 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Random</strong><br /> </td> 
   <td> Restituisce il valore casuale<br /> </td> 
   <td> Random()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Round</strong><br /> </td> 
   <td> Arrotonda un numero a n decimali<br /> </td> 
   <td> Round(&lt;numero&gt;, &lt;numero di decimali&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Sign</strong><br /> </td> 
   <td> Restituisce il segno del numero<br /> </td> 
   <td> Sign(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToDouble</strong><br /> </td> 
   <td> Converte un numero intero in un numero in virgola mobile<br /> </td> 
   <td> ToDouble(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInt64</strong><br /> </td> 
   <td> Converte un numero in virgola mobile in un numero intero a 64 bit<br /> </td> 
   <td> ToInt64(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToInteger</strong><br /> </td> 
   <td> Converte un numero in virgola mobile in un numero intero<br /> </td> 
   <td> ToInteger(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Trunc</strong><br /> </td> 
   <td> Tronca n1 a n2 decimali<br /> </td> 
   <td> Trunc(&lt;n1&gt;, &lt;n2&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

1. Valuta

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Converti valuta</strong><br /> </td> 
   <td> Converte un importo nella valuta di origine in un importo nella valuta di destinazione<br /> </td> 
   <td> ConvertCurrency(&lt;importo&gt;, &lt;valuta di origine&gt;, &lt;valuta di destinazione&gt;, &lt;data di conversione&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatoValuta</strong><br /> </td> 
   <td> Formatta l'importo visualizzato in base alle impostazioni di valuta selezionate<br /> </td> 
   <td> FormatCurrency(&lt;importo&gt;, &lt;valuta&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Geomarketing**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Distance</strong><br /> </td> 
   <td> Restituisce la distanza tra due punti definiti da longitudine e latitudine espressa in gradi.<br /> </td> 
   <td> Distance(&lt;Longitudine A&gt;, &lt;Latitudine A&gt;, &lt;Longitudine B&gt;, &lt;Latitudine B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Altri**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Restituisce il valore 1 se la condizione è vera. In caso contrario, restituisce il valore 2.<br /> </td> 
   <td> Case(When(&lt;condizione&gt;, &lt;valore 1&gt;), Else(&lt;valore 2&gt;))<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>ClearBit</strong><br /> </td> 
   <td> Elimina il contrassegno nel valore<br /> </td> 
   <td> ClearBit(&lt;identificatore&gt;, &lt;contrassegno&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Coalesce</strong><br /> </td> 
   <td> Restituisce il valore 2 se il valore 1 è zero o nullo, altrimenti restituisce il valore 1<br /> </td> 
   <td> Coalesce(&lt;valore 1&gt;, &lt;valore 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Decode</strong><br /> </td> 
   <td> Restituisce il valore 3 se il valore 1 = al valore 2. In caso contrario, restituisce il valore 4.<br /> </td> 
   <td> Decode(&lt;valore 1&gt;, &lt;valore 2&gt;, &lt;valore 3&gt;, &lt;valore 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Restituisce il valore 1 (può essere utilizzato solo come parametro della funzione Case)<br /> </td> 
   <td> Else(&lt;valore 1&gt;, &lt;valore 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Estrae il dominio da un indirizzo e-mail<br /> </td> 
   <td> GetEmailDomain(&lt;valore&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Recupera l’URL del server della pagina mirror<br /> </td> 
   <td> GetMirrorURL(&lt;valore&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Iif</strong><br /> </td> 
   <td> Restituisce il valore 1 se l’espressione è vera. In caso contrario, restituisce il valore 2<br /> </td> 
   <td> Iif(&lt;condizione&gt;, &lt;valore 1&gt;, &lt;valore 2&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsBitSet</strong><br /> </td> 
   <td> Indica se il contrassegno si trova nel valore<br /> </td> 
   <td> IsBitSet(&lt;identificatore&gt;, &lt;contrassegno&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>IsEmptyString</strong><br /> </td> 
   <td> Restituisce il valore 2 se la stringa è vuota, altrimenti restituisce il valore 3<br /> </td> 
   <td> IsEmptyString(&lt;valore 1&gt;, &lt;valore 2&gt;, &lt;valore 3&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>NoNull</strong><br /> </td> 
   <td> Restituisce la stringa vuota se l’argomento è NULL<br /> </td> 
   <td> NoNull(&lt;valore&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>RowId</strong><br /> </td> 
   <td> Restituisce il numero di riga<br /> </td> 
   <td> RowId<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>SetBit</strong><br /> </td> 
   <td> Forza il contrassegno nel valore<br /> </td> 
   <td> SetBit(&lt;identificatore&gt;, &lt;contrassegno&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToBoolean</strong><br /> </td> 
   <td> Converte un numero in booleano<br /> </td> 
   <td> ToBoolean(&lt;numero&gt;)<br /> </td>   
  </tr> 
  <tr> 
   <td> <strong>When</strong><br /> </td> 
   <td> Restituisce il valore 1 se l’espressione è vera. In caso contrario, restituisce il valore 2 (può essere utilizzato solo come parametro della funzione Case)<br /> </td> 
   <td> When(&lt;condizione&gt;, &lt;valore 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Funzioni finestra**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Desc</strong><br /> </td> 
   <td> Applica un ordinamento decrescente<br /> </td> 
   <td> Desc(&lt;valore 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>OrderBy</strong><br /> </td> 
   <td> Ordina il risultato all’interno della partizione<br /> </td> 
   <td> OrderBy(&lt;valore 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>PartitionBy</strong><br /> </td> 
   <td> Partiziona il risultato di una query su una tabella<br /> </td> 
   <td> PartitionBy(&lt;valore 1&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>RowNum</strong><br /> </td> 
   <td> Genera un numero di riga basato sulla partizione della tabella e su una sequenza di ordinamento.<br /> </td> 
   <td> RowNum(PartitionBy(&lt;valore 1&gt;), OrderBy(&lt;valore 1&gt;))<br /> </td> 
  </tr> 
 </tbody> 
</table>
