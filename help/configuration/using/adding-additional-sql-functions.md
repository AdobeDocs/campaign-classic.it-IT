---
product: campaign
title: Aggiunta di ulteriori funzioni SQL
description: Scopri come definire una funzione SQL aggiuntiva
feature: Configuration, Instance Settings
role: Data Engineer, Developer
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 0%

---

# Definire ulteriori funzioni SQL{#adding-additional-sql-functions}

Adobe Campaign consente all’utente di definire **le proprie funzioni** che possono accedere alle funzioni SQL, sia quelle offerte dal database che quelle non già disponibili nella console. Questo è utile per le funzioni di aggregazione (media, massima, somma), ad esempio, che possono essere calcolate solo sul server o quando il database fornisce un modo più semplice per implementare determinate funzioni, anziché scrivere &quot;manualmente&quot; l’espressione nella console (ad esempio, gestione delle date).

Questo meccanismo può essere utilizzato anche se desideri utilizzare una funzione SQL recente o non comune del motore di database, non ancora disponibile nella console Adobe Campaign.

Una volta aggiunte, queste funzioni verranno visualizzate nell’editor espressioni come altre funzioni predefinite.

>[!IMPORTANT]
>
>Le chiamate di funzione SQL nella console non vengono più inviate naturalmente al server. Il meccanismo qui descritto diventa quindi **l&#39;unico modo per chiamare** sul server delle funzioni SQL non pianificato.

## Installazione {#installation}

Le funzioni da aggiungere si trovano in una **file &quot;package&quot; in formato XML**, la cui struttura è illustrata nel paragrafo seguente.

Per installarlo dalla console, seleziona la **Strumenti/Avanzate/Importa pacchetto** dal menu, quindi dal menu **[!UICONTROL Install from file]** e seguire le istruzioni della procedura guidata di importazione.

>[!IMPORTANT]
>
>Avvertenza: anche se l’elenco delle funzioni importate viene visualizzato immediatamente nell’editor funzioni, non saranno utilizzabili fino al riavvio di Adobe Campaign.

## Struttura generale del pacchetto da importare {#general-structure-of-package-to-import}

Le funzioni da aggiungere si trovano nella sezione **file &quot;package&quot;** in formato XML. Ecco un esempio:

```
<?xml version="1.0" encoding='ISO-8859-1' ?>
<!-- ===========================================================================
  Additional SQL functions for Adobe Campaign
  ========================================================================== -->
<package
  namespace   = "nms"
  name        = "package-additional-funclist"
  label       = "Additional functions"
  buildVersion= "7.1"
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

* Il **nome**, **namespace** e **etichetta** sono solo a scopo informativo. Consentono di visualizzare un riepilogo del pacchetto nell&#39;elenco dei pacchetti installati (Explorer/Administration/Package management/Installed packages).
* Il **buildVersion** e **buildNumber** I campi sono obbligatori. Devono corrispondere al numero del server a cui è connessa la console. Queste informazioni sono disponibili nella casella &quot;Help/About&quot; (Guida/Informazioni).
* I seguenti blocchi: **entità** e **funclist** sono obbligatori. In funcList, i campi &quot;name&quot; e &quot;namespace&quot; sono obbligatori, ma il loro nome è lasciato alla scelta dell’utente e designano in modo univoco l’elenco delle funzioni.

  Ciò significa che se viene importato un altro elenco di funzioni con la stessa coppia spazio dei nomi/nome (in questo caso &quot;cus::myList&quot;), le funzioni precedentemente importate verranno eliminate. Viceversa, se si modifica questa coppia spazio dei nomi/nome, la nuova serie di funzioni importate verrà aggiunta a quella precedente.

* Il **gruppo** consente di specificare il gruppo di funzioni in cui le funzioni importate verranno visualizzate nell&#39;editor di funzioni. L’attributo @name può essere un nome già esistente (nel qual caso le funzioni verranno aggiunte al gruppo considerato) o un nuovo nome (nel qual caso verrà visualizzato in un nuovo gruppo).
* Promemoria: valori possibili per l’attributo @name nel `<group>` gli elementi sono:

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
>Assicurati di completare l’attributo @label: questo è il nome che verrà visualizzato nell’elenco delle funzioni disponibili. Se non si immette nulla, il gruppo non avrà un nome. Tuttavia, se si immette un nome diverso da quello esistente, il nome dell&#39;intero gruppo verrà modificato.

Se desideri aggiungere funzioni a diversi gruppi, puoi creare diversi `<group>`  vengono tracciati nello stesso elenco.

Infine, un’ `<group>` può contenere la definizione di una o più funzioni, ovvero lo scopo del file del pacchetto. Il  `<function>`   è descritto nel paragrafo seguente.

## Descrittore di funzione &lt;function>&lt;/function> {#function-descriptor--function-}

Il caso in esame è un caso generale in cui si intende fornire **implementazione di funzione**.

Di seguito è riportato un esempio di funzione di &quot;maturità relativa&quot; che, utilizzando un’età, indica per quanti anni la persona è stata considerata matura.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

Il **@name** Il campo fa riferimento al nome della funzione e &quot;args&quot; è l’elenco dei parametri che verranno visualizzati nella descrizione. In questo caso, la funzione verrà visualizzata come &quot;relativeMaturity ( `<age>` )&quot; nella finestra di selezione della funzione.

* **aiuto** è il campo visualizzato nella parte inferiore della finestra dell’editor di espressioni.
* **@display** è un messaggio informativo.

  >[!NOTE]
  >
  >Negli attributi @help e @display, la stringa &quot;$1&quot; rappresenta il nome specificato nel primo parametro della funzione (in questo caso, &quot;Age&quot;). $2, $3... rappresenterebbero i seguenti parametri. Nell’attributo @body descritto di seguito, $1 indica il valore dell’argomento passato alla funzione durante la chiamata.

  >[!NOTE]
  >
  >La descrizione deve essere una stringa di caratteri XML validi: nota l’utilizzo di &quot;&lt;&quot; e &quot;>&quot; invece di &lt; e >.

* **@type** è il tipo restituito della funzione ed è un valore standard (long, string, byte, datetime...). Se viene omesso, il server determina il tipo migliore tra i tipi disponibili all’interno dell’espressione che implementa la funzione.
* **@minArgs** e **maxArgs** indica il numero di parametri (minimo e massimo) di un parametro. Ad esempio, per una funzione con 2 parametri, minArgs e maxArgs saranno 2 e 2. Per 3 parametri, più 1 facoltativo, saranno rispettivamente 3 e 4.
* Infine, la **providerPart** fornisce l&#39;implementazione della funzione.

   * Il **provider** è obbligatorio, specifica i sistemi di database per i quali viene fornita l’implementazione. Come mostrato nell’esempio, quando le sintassi delle espressioni o le funzioni sottostanti differiscono, è possibile fornire implementazioni alternative in base al database.
   * Il **@body** contiene l&#39;implementazione della funzione. Nota: questa implementazione deve essere un&#39;espressione nel linguaggio del database (non un blocco di codice). A seconda dei database, le espressioni possono essere sottoquery (&quot;(seleziona una colonna dalla tabella dove...)&quot;) che restituiscono un solo valore. Questo è il caso, ad esempio, dell’Oracle (la query deve essere scritta tra parentesi).

  >[!NOTE]
  >
  >Se è probabile che solo uno o due database vengano interrogati dalla funzione definita, è sempre possibile fornire solo le definizioni corrispondenti a tali database.

## Descrittore di funzione &quot;Pass-through&quot; {#pass-through--function-descriptor}

Un descrittore di funzione speciale è **&quot;pass-through&quot;** con un sistema di database &quot;provider&quot; non specificato. In questo caso, l’implementazione &quot;body&quot; può contenere solo una singola chiamata di funzione con una sintassi che non dipende dal database utilizzato. Nel frattempo, il blocco &quot;ProviderPart&quot; è univoco.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In questo caso, l’aggiunta di una funzione serve solo a rendere una funzione di database che non sarebbe stata disponibile per impostazione predefinita, ora visibile al client.

## Esempi {#examples}

Ulteriori esempi di funzioni sono disponibili nel pacchetto predefinito &quot;xtkdatakitfuncList.xml&quot;.
