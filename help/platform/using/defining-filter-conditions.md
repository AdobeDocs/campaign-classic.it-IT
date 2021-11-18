---
product: campaign
title: Definizione delle condizioni di filtro
description: Definizione delle condizioni di filtro
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: b62e23e5-f1b7-44c4-82d9-95c6b3240352
source-git-commit: f000cb8bae164c22d1ede15db4e763cf50530674
workflow-type: tm+mt
source-wordcount: '3229'
ht-degree: 37%

---

# Definire le condizioni del filtro{#defining-filter-conditions}

![](../../assets/common.svg)

## Scegli l’operatore {#choosing-the-operator}

All’interno delle condizioni di filtro, è necessario collegare due valori utilizzando un operatore .

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
   <td> <strong>Cognome (@lastName) uguale a "Jones"</strong>, restituirà solo i destinatari il cui cognome è Jones.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Maggiore di</span> <br /> </td> 
   <td> Restituisce un valore maggiore del valore inserito.<br /> </td> 
   <td> <strong>Età (@età) superiore a 50</strong>, restituirà tutti i valori maggiori di "50", ovvero "51", "52", ecc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Minore di</span> <br /> </td> 
   <td> Restituisce un valore inferiore al valore inserito.<br /> </td> 
   <td> <strong>Data di creazione (@created) prima di 'DaysAgo(100)'</strong>, restituirà tutti i destinatari creati meno di 100 giorni fa.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Maggiore o uguale a</span> <br /> </td> 
   <td> Restituisce tutti i valori uguali o maggiori del valore inserito.<br /> </td> 
   <td> <strong>Età (@età) maggiore o uguale a '30'</strong>, restituirà tutti i destinatari di età pari o superiore a 30 anni.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Minore o uguale a</span> <br /> </td> 
   <td> Restituisce tutti i valori uguali o inferiori al valore inserito.<br /> </td> 
   <td> <strong>Età (@età) inferiore o uguale a '60'</strong>, restituirà tutti i destinatari di età non superiore a 60 anni.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non uguale a</span> <br /> </td> 
   <td> Restituisce tutti i valori non identici al valore inserito.<br /> </td> 
   <td> <strong>Lingua (@lingua) uguale a "Inglese"</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Inizia con</span> <br /> </td> 
   <td> Restituisce i risultati che iniziano con il valore inserito.<br /> </td> 
   <td> <strong>L'account # (@account) inizia con '32010'.</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non inizia con</span> <br /> </td> 
   <td> Restituisce i risultati che non iniziano con il valore inserito<br /> </td> 
   <td> <strong>L'account # (@account) non inizia con '20'</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Contiene</span> <br /> </td> 
   <td> Restituisce i risultati contenenti almeno il valore inserito.<br /> </td> 
   <td> <strong>Il dominio e-mail (@dominio) contiene 'mail'</strong>, restituirà tutti i nomi di dominio contenenti "mail". Quindi verrà restituito anche il dominio "gmail.com".<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non contiene</span> <br /> </td> 
   <td> Restituisce risultati che non contengono il valore inserito.<br /> </td> 
   <td> <strong>Il dominio e-mail (@dominio) non contiene 'vo'</strong>. In questo caso, i nomi di dominio contenenti "vo" non verranno restituiti. Il nome di dominio 'voila.fr' non verrà visualizzato nei risultati.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Simile</span> <br /> </td> 
   <td> <span class="uicontrol">Simile</span> è molto simile all’operatore <span class="uicontrol">Contains</span>. Consente di inserire un <span class="uicontrol">%</span> carattere jolly nel valore .<br /> </td> 
   <td> <strong>Cognome (@lastName) simile a 'Jon%s'</strong>. Qui, il carattere jolly è usato come un "jolly" per trovare il nome "Jones", se l'operatore ha dimenticato la lettera mancante tra il 'n' e il 's'.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Diverso</span> <br /> </td> 
   <td> È simile a <span class="uicontrol">Simile</span> . Consente di non recuperare il valore immesso. Anche in questo caso, il valore immesso deve contenere il carattere jolly <span class="uicontrol">%</span>.<br /> </td> 
   <td> <strong>Cognome (@lastName) non simile a 'Smi%h'</strong>. In questo caso, i destinatari il cui cognome è "Smi%h" non verranno restituiti.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">È vuoto</span> <br /> </td> 
   <td> In questo caso, il risultato che stiamo cercando corrisponde a un valore vuoto nella seconda colonna Valore .<br /> </td> 
   <td> <strong>Mobile (@mobilePhone) è vuoto</strong> restituisce tutti i destinatari che non dispongono di un numero mobile.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non è vuoto</span> <br /> </td> 
   <td> Opere al contrario <span class="uicontrol">È vuoto</span> operatore. Non è necessario inserire dati nella seconda colonna Valore.<br /> </td> 
   <td> <strong>E-mail (@email) non è vuota</strong>.<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">È incluso in</span> <br /> </td> 
   <td> Restituisce i risultati inclusi nei valori indicati. Questi valori devono essere separati da una virgola.<br /> </td> 
   <td> <strong>La data di nascita (@datadinascita) è inclusa in '12/10/1979,12/10/1984'</strong>, restituirà i destinatari nati tra queste date. <br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">Non è incluso in</span> <br /> </td> 
   <td> Funziona come <span class="uicontrol">È incluso in</span> operatore. In questo caso, vogliamo escludere i destinatari in base ai valori inseriti.<br /> </td> 
   <td> <strong>La data di nascita (@datadinascita) non è inclusa in '12/10/1979,12/10/1984'</strong>. A differenza dell’esempio precedente, i destinatari nati entro queste date non verranno restituiti.<br /> </td> 
  </tr> 
 </tbody> 
</table>

## UTILIZZARE E, O, ECCETTO {#using-and--or--except}

Per le query che utilizzano diverse condizioni di filtro, è necessario definire collegamenti tra le condizioni. Esistono tre possibili collegamenti:

* **[!UICONTROL And]** consente di combinare due condizioni di filtro,
* **[!UICONTROL Or]** consente di offrire un’alternativa,
* **[!UICONTROL Except]** ti consente di definire un’eccezione.

Fai clic su **[!UICONTROL And]** (offerta per impostazione predefinita) e scegli dall’elenco a discesa.

![](assets/query_condition_modif_01.png)

* **[!UICONTROL And]**: aggiunge una condizione e abilita il filtro eccessivo.
* **[!UICONTROL Or]**: aggiunge una condizione e abilita il filtro eccessivo.

   L’esempio seguente ti consente di trovare i destinatari il cui dominio e-mail contiene &quot;orange.co.uk&quot; O il cui codice postale inizia con &quot;NW&quot;.

   ![](assets/query_condition_modif_02.png)

* **[!UICONTROL Except]**: se disponi di due filtri e il primo non restituisce un valore, questo tipo di collegamento crea un’eccezione.

   Nell’esempio seguente, vogliamo restituire i destinatari il cui dominio e-mail contiene &quot;orange.co.uk&quot; ECCETTO se il cognome del destinatario è &quot;Smith&quot;.

   ![](assets/query_condition_modif_03.png)

Questo esempio mostra un filtro che consente di visualizzare: destinatari che parlano spagnolo, OPPURE sono donne con numeri di cellulare, OPPURE destinatari senza un numero di conto e il cui nome dell&#39;azienda inizia con la lettera &quot;N&quot;.

![](assets/query_editor_nveau_31.png)

## Dare priorità alle condizioni {#prioritizing-conditions}

Questa sezione spiega come assegnare priorità alle condizioni grazie alle frecce blu nella barra degli strumenti.

* La freccia rivolta a destra consente di aggiungere al filtro un livello di parentesi.
* La freccia rivolta a sinistra consente di eliminare un livello di parentesi selezionato dal filtro.

   ![](assets/query_condition_modif_04.png)

* Le frecce verticali consentono di spostare una condizione, cambiandone la sequenza di esecuzione.

In questo esempio viene illustrato come utilizzare la freccia per eliminare un livello di parentesi. Inizia dalla seguente condizione di filtro: **[!UICONTROL City equal to London OR gender equal to male and mobile not indicated OR account # starts with "95" and company name starts with "A"]**.

Posizionare il cursore sul **[!UICONTROL Gender (@gender) equal to Male]** condizione di filtro e fai clic su **[!UICONTROL Remove a parenthesis level]** freccia.

![](assets/query_editor_nveau_32.png)

La **[!UICONTROL Gender (@gender) equal to Male]** condizione estratta dalla sua parentesi. Si è spostata allo stesso livello della condizione &quot;City equal to London&quot;. Tali condizioni sono collegate tra loro (**[!UICONTROL And]**).

## Selezionare i dati da estrarre {#selecting-data-to-extract}

I campi disponibili variano da una tabella all’altra. Tutti i campi sono memorizzati in un nodo principale noto come **[!UICONTROL Main element]**. Nell’esempio seguente, i campi disponibili si trovano nella tabella dei destinatari. I campi vengono sempre visualizzati in ordine alfabetico.

Il dettaglio del campo selezionato è visibile nella parte inferiore della finestra. Ad esempio, il **[!UICONTROL Email domain]** è un campo **[!UICONTROL Calculated SQL field]** e la sua estensione **[!UICONTROL (@domain)]**.

![](assets/query_editor_nveau_59.png)

>[!NOTE]
>
>Utilizza la **[!UICONTROL Search]** strumento per trovare un campo disponibile.

Fare doppio clic su un campo disponibile per aggiungerlo alle colonne di output. Alla fine della query, ogni campo selezionato crea una colonna nel **[!UICONTROL Data preview]** finestra.

![](assets/query_editor_nveau_01.png)

I campi avanzati non vengono visualizzati per impostazione predefinita. Fai clic su **[!UICONTROL Display advanced fields]** nell’angolo in basso a destra dei campi disponibili per visualizzare tutti gli elementi. Fai di nuovo clic su per tornare alla visualizzazione precedente.

Ad esempio, nella tabella dei destinatari, i campi avanzati sono **Booleano 1**, **[!UICONTROL Boolean 2]**, **[!UICONTROL Boolean 3]**, **[!UICONTROL Foreign key of "Folder" link]**, ecc.

L’esempio seguente mostra i campi avanzati della tabella dei destinatari.

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
   <td> Chiave primaria. Questo campo SQL è un modo per identificare un record in una tabella.<br /> </td> 
   <td> I destinatari degli identificatori sono chiavi primarie e gli identificatori sono univoci per definizione.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_02.png" /> </td> 
   <td> Chiave esterna. Utilizzato come collegamento a un’altra tabella.<br /> </td> 
   <td> Chiave esterna del destinatario, chiave esterna del servizio, ecc.<br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_46.png" /> </td> 
   <td> Campo calcolato. Questo tipo di campo viene calcolato su richiesta utilizzando i valori del database.<br /> </td> 
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
   <td> Nome completo, codice ISO, ecc. <br /> </td> 
  </tr> 
 </tbody> 
</table>

Collegamento a una tabella e a un elemento di raccolta:

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
   <td> Collegamenti a una tabella in particolare. Questi coincidono con associazioni di tipo 1-1. Una occorrenza della tabella sorgente può coincidere con una sola occorrenza della tabella di destinazione. Ad esempio, un solo destinatario può essere collegato a un paese.<br /> </td> 
   <td> Cartella, Stato, Paese, ecc. <br /> </td> 
  </tr> 
  <tr> 
   <td> <img height="21px" src="assets/query_editor_nveau_52.png" /> </td> 
   <td> Elemento di raccolta in una tabella specifica. Queste coincidono con le associazioni di tipo 1-N. Una occorrenza della tabella sorgente può coincidere con diverse occorrenze della tabella di destinazione, ma una occorrenza della tabella di destinazione può coincidere con una sola occorrenza della tabella sorgente. Ad esempio, un destinatario può abbonarsi alle lettere di abbonamento "n".<br /> </td> 
   <td> Abbonamenti, elenchi, registri di esclusione, ecc.<br /> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Utilizza la **[!UICONTROL Add]** pulsante (sopra la barra delle icone laterali) per aggiungere una colonna di output in cui modificare l’espressione. Per ulteriori informazioni sulla modifica di un’espressione, consulta [questa sezione](#building-expressions).
>* Elimina una colonna di output facendo clic sulla &quot;x&quot; rossa (**Elimina**).
>* Modificare l’ordine delle colonne di output utilizzando le frecce.
>* La **[!UICONTROL Distribution of values]** consente di visualizzare la distribuzione dei valori del campo selezionato (ad esempio, le distribuzioni collegate alle città destinatarie, alle lingue dei destinatari, ecc.).


## Creazione di campi calcolati {#creating-calculated-fields}

Se necessario, aggiungere una colonna durante la formattazione dei dati. Un campo calcolato aggiunge una colonna alla sezione di anteprima dati. Fai clic su **[!UICONTROL Add a calculated field]**.

![](assets/query_editor_nveau_43.png)

Esistono quattro tipi di campi calcolati:

* **[!UICONTROL Fixed string]**: consente di aggiungere una stringa di caratteri.

   ![](assets/query_editor_nveau_60.png)

* **[!UICONTROL String with JavaScript tags]**: il valore del campo calcolato combina una stringa di caratteri e direttive JavaScript.

   ![](assets/query_editor_nveau_61.png)

* **[!UICONTROL JavaScript expression]**: il valore del campo calcolato è il risultato di una valutazione della funzione JavaScript. Il valore restituito può essere digitato (numero, data, ecc.).

   ![](assets/query_editor_nveau_62.png)

* **[!UICONTROL Enumerations]**: Questo tipo di campo consente di utilizzare/modificare il contenuto di una delle colonne di output in una nuova colonna.

   È possibile utilizzare il valore sorgente di una colonna e assegnargli un valore di destinazione. Questo valore di destinazione verrà visualizzato nella nuova colonna di output.

   Esempio di aggiunta del tipo di campo calcolato **[!UICONTROL Enumerations]** è disponibile, fai riferimento a [questa sezione](../../workflow/using/adding-enumeration-type-calculated-field.md).

   ![](assets/query_editor_nveau_63.png)

   La **[!UICONTROL Enumerations]** il campo calcolato di tipo può includere 4 condizioni:

   * **[!UICONTROL Keep the source value]** ripristina il valore sorgente nel target senza modificarlo.
   * **[!UICONTROL Use the following value]** consente di immettere un valore di destinazione predefinito per i valori di origine non definiti.
   * **[!UICONTROL Generate a warning and continue]** avverte l&#39;utente che il valore sorgente non può essere modificato.
   * **[!UICONTROL Generate an error and reject the line]** impedisce il calcolo e l’importazione della riga.

Fai clic sul pulsante **[!UICONTROL Detail of calculated field]** per visualizzare i dettagli del campo inserito.

Per rimuovere questo campo calcolato, fai clic sul pulsante **[!UICONTROL Remove the calculated field]** croce.

![](assets/query_editor_nveau_58.png)

## Creare espressioni {#building-expressions}

Lo strumento di modifica delle espressioni consente di calcolare gli aggregati, generare una funzione o modificare una formula utilizzando un’espressione.

L&#39;esempio seguente mostra come eseguire un conteggio su una chiave primaria.

Applica i seguenti passaggi:

1. Fai clic su **[!UICONTROL Add]** in **[!UICONTROL Data to extract]** finestra. In **[!UICONTROL Formula type]** selezionare un tipo di formula per immettere l&#39;espressione.

   Sono disponibili diversi tipi di formule: **[!UICONTROL Field only]**, **[!UICONTROL Aggregate]**, **[!UICONTROL Expression]**.

   Seleziona **[!UICONTROL Process on an aggregate function]** e **[!UICONTROL Count]**. Fai clic su **[!UICONTROL Next]**.

   ![](assets/query_editor_nveau_54.png)

1. Viene calcolata la chiave primaria.

   ![](assets/query_editor_nveau_88.png)

Di seguito è riportata una visualizzazione dettagliata delle scelte disponibili nel **[!UICONTROL Formula types]** finestra:

![](assets/query_editor_nveau_05.png)

1. **[!UICONTROL Field only]** consente di tornare alla sezione **[!UICONTROL Field to select]** finestra.
1. **[!UICONTROL Aggregate (Process on an aggregate function)]**. Di seguito sono riportati alcuni esempi di utilizzo aggregato:

   * **[!UICONTROL Count]** consente di eseguire un conteggio delle chiavi primarie.
   * **[!UICONTROL Sum]** consente di sommare tutti gli acquisti effettuati da un cliente su un anno.
   * **[!UICONTROL Maximum value]** consente di trovare i clienti che hanno acquistato il maggior numero di prodotti &quot;n&quot;.
   * **[!UICONTROL Minimum value]** ti consente di ordinare in base ai clienti e individuare quelli che si sono abbonati a un’offerta più di recente.
   * **[!UICONTROL Average]**. Questa funzione ti consente di calcolare l’età media dei destinatari.

      La **[!UICONTROL Distinct]** consente di recuperare valori univoci e diversi da zero di una colonna. Ad esempio, puoi recuperare tutti i registri di tracciamento di un destinatario e questi vengono modificati nel valore 1 in quanto riguardano tutti lo stesso destinatario.

1. **[!UICONTROL Expression]** apre **[!UICONTROL Edit the expression]** finestra. Questo consente di rilevare i numeri telefonici con troppe cifre, che potrebbero essere errori di inserimento.

   ![](assets/query_editor_nveau_71.png)

   Per un elenco di tutte le funzioni disponibili, consulta [Elenco delle funzioni](#list-of-functions).

## Elenco delle funzioni {#list-of-functions}

Se **[!UICONTROL Expression]** viene scelta la formula del tipo, verrà visualizzata la finestra &quot;modifica l&#39;espressione&quot;. Ai campi disponibili possono essere associate diverse categorie di funzioni: **[!UICONTROL Aggregates]**, **[!UICONTROL String]**, **[!UICONTROL Date]**, **[!UICONTROL Numerical]**, **[!UICONTROL Currency]**, **[!UICONTROL Geomarketing]**, **[!UICONTROL Windowing function]** e **[!UICONTROL Others]**.

L’editor di espressioni si presenta così:

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
   <td> Restituisce la media di una colonna del tipo di numero<br /> </td> 
   <td> Avg(&lt;valore&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Conteggio</strong><br /> </td> 
   <td> Conta i valori non nulli di una colonna<br /> </td> 
   <td> Count(&lt;valore&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>CountAll</strong><br /> </td> 
   <td> Conta i valori restituiti (tutti i campi)<br /> </td> 
   <td> CountAll()<br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Countdistinct</strong><br /> </td> 
   <td> Conta i valori distinti non nulli di una colonna<br /> </td> 
   <td> Countdistinct(&lt;valore&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Max</strong><br /> </td> 
   <td> Restituisce il valore massimo di una colonna numero, stringa o tipo di data<br /> </td> 
   <td> Max(&lt;valore&gt;)<br /></td>  
  </tr> 
  <tr> 
   <td> <strong>Min</strong><br /> </td> 
   <td> Restituisce il valore minimo di una colonna numero, stringa o tipo di data<br /> </td> 
   <td> Min(&lt;valore&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>StdDev</strong><br /> </td> 
   <td> Restituisce la deviazione standard di un numero, una stringa o una colonna di data<br /> </td> 
   <td> StdDev(&lt;value&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>Somma</strong><br /> </td> 
   <td> Restituisce la somma dei valori di una colonna numero, stringa o tipo di data<br /> </td> 
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
   <td> Restituisce il valore ASCII del primo carattere della stringa.<br /> </td> 
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
   <td> Restituisce il terzo parametro se i primi due parametri sono uguali. In caso contrario, restituisce l'ultimo parametro<br /> </td> 
   <td> IfEquals(&lt;stringa&gt;, &lt;stringa&gt;, &lt;stringa&gt;, &lt;stringa&gt;)<br /></td> 
  </tr> 
  <tr> 
   <td> <strong>IsMemoNull</strong><br /> </td> 
   <td> Indica se il promemoria passato come parametro è nullo<br /> </td> 
   <td> IsMemoNull(&lt;memo&gt;)<br /></td> 
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
   <td> LPad(&lt;string&gt;, &lt;number&gt;, &lt;character&gt;)<br /></td> 
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
   <td> Estrae la sottostringa a partire dal carattere n1 della stringa e di lunghezza n2<br /> </td> 
   <td> Substring(&lt;stringa&gt;, &lt;offset&gt;, &lt;lunghezza&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>ToString</strong><br /> </td> 
   <td> Converte il numero in una stringa<br /> </td> 
   <td> ToString(&lt;number&gt;, &lt;number&gt;)<br /> </td>  
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
   <td> Restituisce la dimensione della stringa<br /> </td> 
   <td> dataLength(&lt;string&gt;)<br /> </td>  
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
   <td> Restituisce il numero del giorno dell’anno della data<br /> </td> 
   <td> DayOfYear(&lt;data&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgo</strong><br /> </td> 
   <td> Restituisce la data corrispondente alla data corrente meno n giorni<br /> </td> 
   <td> DaysAgo(&lt;numero&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>DaysAgoInt</strong><br /> </td> 
   <td> Restituisce la data (numero intero aaaammgg) corrispondente alla data corrente meno n giorni<br /> </td> 
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
   <td> TruncTim(e&lt;date&gt;, &lt;number of="" seconds=""&gt;)<br /> </td>  
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
>Tieni presente che **Solo dati** prende in considerazione il fuso orario del server, non quello dell&#39;operatore.

**Numeriche**

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
   <td> Restituisce il numero intero più grande maggiore o uguale a un numero<br /> </td> 
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
   <td> Restituisce il resto della divisione del numero intero di n1 per n2<br /> </td> 
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
   <td> <strong>ConvertCurrency</strong><br /> </td> 
   <td> Converte un importo in una valuta di origine in un importo in una valuta di destinazione<br /> </td> 
   <td> ConvertCurrency(&lt;amount&gt;, &lt;source currency=""&gt;, &lt;target currency=""&gt;, &lt;conversion date=""&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>FormatoValuta</strong><br /> </td> 
   <td> Formatta l'importo visualizzato in base alle impostazioni di valuta selezionate<br /> </td> 
   <td> FormatCurrency(&lt;amount&gt;, &lt;currency&gt;)<br /> </td>  
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
   <td> Restituisce la distanza tra due punti definiti da longitudine e latitudine, espressa in gradi.<br /> </td> 
   <td> Distance(&lt;Longitudine A&gt;, &lt;Latitudine A&gt;, &lt;Longitudine B&gt;, &lt;Latitudine B&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Altro**

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Nome</strong><br /> </td> 
   <td> <strong>Descrizione</strong><br /> </td> 
   <td> <strong>Sintassi</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <strong>Case</strong><br /> </td> 
   <td> Restituisce il valore 1 se la condizione è true. In caso contrario restituisce il valore 2.<br /> </td> 
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
   <td> Restituisce il valore 3 se valore 1 = valore 2. Se non restituisce il valore 4.<br /> </td> 
   <td> Decode(&lt;valore 1&gt;, &lt;valore 2&gt;, &lt;valore 3&gt;, &lt;valore 4&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>Else</strong><br /> </td> 
   <td> Restituisce il valore 1 (può essere utilizzato solo come parametro della funzione Case)<br /> </td> 
   <td> Else(&lt;value&gt;, &lt;value&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetEmailDomain</strong><br /> </td> 
   <td> Estrae il dominio da un indirizzo e-mail<br /> </td> 
   <td> GetEmailDomain(&lt;valore&gt;)<br /> </td>  
  </tr> 
  <tr> 
   <td> <strong>GetMirrorURL</strong><br /> </td> 
   <td> Recupera l’URL del server della pagina speculare<br /> </td> 
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
   <td> Restituisce il valore 2 se la stringa 1 è vuota, altrimenti restituisce il valore 3<br /> </td> 
   <td> IsEmptyString(&lt;value&gt;, &lt;value&gt;, &lt;value&gt;)<br /> </td>  
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
   <td> Restituisce il valore 1 se l’espressione è vera. In caso contrario restituisce il valore 2 (può essere utilizzato solo come parametro della funzione Case)<br /> </td> 
   <td> When(&lt;condizione&gt;, &lt;valore 1&gt;)<br /> </td>  
  </tr> 
 </tbody> 
</table>

**Funzioni di Windows**

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
