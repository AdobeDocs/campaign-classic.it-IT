---
solution: Campaign Classic
product: campaign
title: Aggiunta di ulteriori funzioni SQL
description: Aggiunta di ulteriori funzioni SQL
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1021'
ht-degree: 1%

---


# Aggiunta di ulteriori funzioni SQL{#adding-additional-sql-functions}

## Introduzione {#introduction}

 Adobe Campaign consente all&#39;utente di definire le **proprie funzioni** in grado di accedere alle funzioni SQL, sia quelle offerte dal database che quelle non già disponibili nella console. Questo è utile per le funzioni aggregate (media, massima, somma), ad esempio, che possono essere calcolate solo sul server o quando il database fornisce un modo più semplice per implementare determinate funzioni, piuttosto che scrivere l&#39;espressione &quot;manualmente&quot; nella console (ad esempio, gestione delle date).

Questo meccanismo può essere utilizzato anche se si desidera utilizzare una funzione SQL del motore di database recente o non comune, che non è ancora disponibile dalla console Adobe Campaign .

Una volta aggiunte queste funzioni, verranno visualizzate nell&#39;editor di espressioni come altre funzioni predefinite.

>[!IMPORTANT]
>
>Le chiamate delle funzioni SQL nella console non vengono più inviate al server in modo naturale. Il meccanismo descritto qui diventa quindi **l&#39;unico modo per chiamare** sul server di funzioni SQL non pianificato.

## Installazione {#installation}

Le funzioni da aggiungere si trovano in un file **&quot;package&quot; in formato** XML, la cui struttura è dettagliata nel paragrafo seguente.

Per installarlo dalla console, selezionate le opzioni **Strumenti/Avanzate/Importa pacchetto** dal menu, quindi selezionate **[!UICONTROL Install from file]** , e seguite le istruzioni della procedura guidata di importazione.

>[!IMPORTANT]
>
>Avviso: anche se l&#39;elenco delle funzioni importate viene immediatamente visualizzato nell&#39;editor delle funzioni, non saranno utilizzabili fino  riavvio di Adobe Campaign.

## Struttura generale del pacchetto da importare {#general-structure-of-package-to-import}

Le funzioni da aggiungere si trovano nel file **** &quot;package&quot; in formato XML. Esempio:

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "6.1"
  buildNumber = "10000">

  <entities schema="xtk:funcList">
    <funcList name="myList" namespace="cus">
      <group name="date" label="Personalized date">
        <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
                  minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
          <providerPart provider="MSSQL,Sybase,PostgreSQL" body="extract(year from age($1))-18"/>
        </function>
      </group>
    </funcList>
  </entities>
</package>
```

* Il **nome**, **lo spazio dei nomi** e l&#39; **etichetta** sono solo a scopo informativo. Consentono di visualizzare un riepilogo del pacchetto nell&#39;elenco dei pacchetti installati (Explorer/Amministrazione/Gestione pacchetti/Pacchetti installati).
* I campi **buildVersion** e **buildNumber** sono obbligatori. Devono corrispondere al numero del server a cui è collegata la console. Queste informazioni sono disponibili nella casella &quot;Aiuto/Informazioni su&quot;.
* I seguenti blocchi, **entità** e **funclist** sono obbligatori. In funcList, i campi &quot;name&quot; e &quot;namespace&quot; sono obbligatori, ma il loro nome è lasciato alla decisione dell&#39;utente, che designa in modo univoco l&#39;elenco delle funzioni.

   Ciò significa che se viene importato un altro elenco di funzioni con la stessa coppia di nomi/nomi (qui &quot;cus::myList&quot;), le funzioni importate in precedenza verranno eliminate. Al contrario, se si modifica questa coppia nome/spazio nomi, la nuova serie di funzioni importate verrà aggiunta a quella precedente.

* L&#39;elemento **group** consente di specificare il gruppo di funzioni nel quale verranno visualizzate le funzioni importate nell&#39;editor delle funzioni. L&#39;attributo @name può essere un nome già esistente (nel qual caso le funzioni verranno aggiunte al gruppo considerato) o un nuovo nome (nel qual caso apparirà in un nuovo gruppo).
* Promemoria: i valori possibili per l&#39;attributo @name nell&#39; `<group>` elemento sono:

   ```
     name="aggregate"      ( label="Aggregates"         )
     name="string"             ( label="String"           )
     name="date"               ( label="Date"             )
     name="numeric"          ( label="Numeric"        )
     name="geomarketing" ( label="Geomarketing"     )
     name="other"              ( label="Others"           )
     name="window"          ( label="Windowing functions" )
   ```

>[!IMPORTANT]
>
>Assicuratevi di completare l&#39;attributo @label: questo è il nome che verrà visualizzato nell&#39;elenco delle funzioni disponibili. Se non immettete nulla, il gruppo non avrà un nome. Tuttavia, se immettete un nome diverso da quello esistente, il nome dell’intero gruppo verrà modificato.

Se desiderate aggiungere funzioni a diversi gruppi diversi, potete fare in modo che diversi `<group>` elementi vengano tracciati nello stesso elenco.

Infine, un `<group>` elemento può contenere la definizione di una o più funzioni, ossia lo scopo del file del pacchetto. L’ `<function>` elemento è dettagliato nel seguente paragrafo.

## Descrittore di funzione &lt;funzione>&lt;/funzione> {#function-descriptor--function-}

Il caso qui presentato è un caso generale in cui desideriamo fornire l&#39;attuazione **della** funzione.

Di seguito è riportato un esempio di una funzione di &quot;maturità relativa&quot; che, utilizzando un&#39;età, indica per quanti anni la persona è stata considerata matura.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Il campo **@name** fa riferimento al nome della funzione, e &quot;args&quot; è l&#39;elenco di parametri che verranno visualizzati nella descrizione. In questo caso, la funzione verrà visualizzata come &quot;relativeMaturity ( `<age>` )&quot; nella finestra di selezione della funzione.

* **help** è il campo visualizzato nella parte inferiore della finestra dell&#39;editor di espressioni.
* **@display** è un messaggio informativo.

   >[!NOTE]
   >
   >Negli attributi @help e @display, la stringa &quot;$1&quot; rappresenta il nome fornito nel parametro della prima funzione (qui, &quot;Age&quot;). $2, $3... rappresentano i seguenti parametri. Nell&#39;attributo @body illustrato di seguito, $1 indica il valore dell&#39;argomento passato alla funzione durante la chiamata.

   >[!NOTE]
   >
   >La descrizione deve essere una stringa di caratteri XML validi: notare l&#39;uso di &#39;&lt;&#39; e &#39;>&#39; invece di &lt; e >.

* **@type** è il tipo restituito dalla funzione ed è un valore standard (long, string, byte, datetime...). Se viene omesso, il server determina il tipo migliore tra i tipi disponibili all&#39;interno dell&#39;espressione che implementa la funzione.
* **@minArgs** e **maxArgs** indicano il numero di parametri (minimo e massimo) per un parametro. Ad esempio, per una funzione con 2 parametri, minArgs e maxArgs saranno 2 e 2. Per 3 parametri, più 1 opzionale, saranno rispettivamente 3 e 4.
* Infine, l&#39;elemento **providerPart** fornisce l&#39;implementazione della funzione.

   * L&#39;attributo **provider** è obbligatorio, specifica i sistemi di database per i quali viene fornita l&#39;implementazione. Come illustrato nell&#39;esempio, quando le sintassi delle espressioni o le funzioni sottostanti differiscono, è possibile fornire implementazioni alternative in base al database.
   * L&#39;attributo **@body** contiene l&#39;implementazione della funzione. Nota: questa implementazione deve essere un&#39;espressione, nella lingua del database (non un blocco di codice). A seconda dei database, le espressioni possono essere sottoquery (&quot;(selezionare la colonna dalla tabella dove...)&quot;) che restituiscono solo un singolo valore. Ad esempio, questo è il caso in  Oracle (la query deve essere scritta tra parentesi).

   >[!NOTE]
   >
   >Se solo uno o due database verranno probabilmente interrogati dalla funzione definita, sarà sempre possibile fornire solo le definizioni corrispondenti a tali database.

## Descrittore di funzione &#39;Pass-through&#39; {#pass-through--function-descriptor}

Un descrittore di funzione speciale è il blocco **&quot;pass-through&quot;** , con un sistema di database &quot;provider&quot; non specificato. In questo caso, l&#39;implementazione &quot;body&quot; può contenere solo una singola chiamata di funzione con una sintassi che non dipende dal database utilizzato. Nel frattempo, il blocco &quot;ProviderPart&quot; è univoco.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In questo caso, l&#39;aggiunta di una funzione serve solo a rendere visibile al client una funzione del database che non sarebbe stata disponibile per impostazione predefinita.

## Esempi {#examples}

Ulteriori esempi di funzioni sono disponibili nel pacchetto predefinito &quot;xtkdatakitfuncList.xml&quot;.
