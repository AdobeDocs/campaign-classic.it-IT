---
product: campaign
title: Aggiunta di ulteriori funzioni SQL
description: Scopri come definire funzioni SQL aggiuntive
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 04b0a0e5-d6df-447c-ac67-66adb1bdf717
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 0%

---

# Definire ulteriori funzioni SQL{#adding-additional-sql-functions}

Adobe Campaign consente all’utente di definire **le proprie funzioni** che possono accedere alle funzioni SQL, sia quelle offerte dal database che quelle non già disponibili nella console. Questa funzione è utile per le funzioni di aggregazione (media, massima, somma), ad esempio, che possono essere calcolate solo sul server o quando il database fornisce un modo più semplice per implementare determinate funzioni, anziché scrivere l’espressione &quot;manualmente&quot; nella console (ad esempio gestione delle date).

Questo meccanismo può essere utilizzato anche se si desidera utilizzare una funzione SQL del motore di database recente o non comune, che non è ancora disponibile dalla console Adobe Campaign.

Una volta aggiunte queste funzioni, verranno visualizzate nell’editor espressioni come altre funzioni predefinite.

>[!IMPORTANT]
>
>Le chiamate alla funzione SQL nella console non vengono più inviate naturalmente al server. Il meccanismo qui descritto diventa quindi **l&#39;unico modo per chiamare** sul server di funzioni SQL non pianificato.

## Installazione {#installation}

Le funzioni da aggiungere si trovano in una **file &quot;package&quot; in formato XML**, la cui struttura è descritta nel paragrafo seguente.

Per installarlo dalla console, seleziona la **Strumenti/pacchetto di importazione/avanzata** dal menu, quindi **[!UICONTROL Install from file]** e segui le istruzioni della procedura guidata di importazione.

>[!IMPORTANT]
>
>Avviso: anche se l’elenco delle funzioni importate viene immediatamente visualizzato nell’editor funzioni, non sarà utilizzabile fino al riavvio di Adobe Campaign.

## Struttura generale del pacchetto da importare {#general-structure-of-package-to-import}

Le funzioni da aggiungere si trovano nella **file &quot;package&quot;** in formato XML. Ecco un esempio:

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

* La **name**, **namespace** e **etichetta** sono a scopo puramente informativo. Consentono di visualizzare un riepilogo del pacchetto nell&#39;elenco dei pacchetti installati (Explorer/Administration/Package Management/Installed packages).
* La **buildVersion** e **buildNumber** i campi sono obbligatori. Devono corrispondere al numero del server a cui è connessa la console. Queste informazioni sono disponibili nella casella &quot;Help/About&quot;.
* i seguenti blocchi, **entità** e **fungoso** sono obbligatori. In funcList, i campi &quot;name&quot; e &quot;namespace&quot; sono obbligatori, ma il loro nome è lasciato all&#39;utente a decidere e designano in modo univoco l&#39;elenco delle funzioni.

   Ciò significa che se viene importato un altro elenco di funzioni con la stessa coppia di nomi/nomi (qui &quot;cus::myList&quot;), le funzioni importate in precedenza verranno eliminate. Viceversa, se modificate questa coppia di nomi/nomi, la nuova serie di funzioni importate verrà aggiunta a quella precedente.

* La **gruppo** consente di specificare il gruppo di funzioni in cui verranno visualizzate le funzioni importate nell’editor di funzioni. L&#39;attributo @name può essere un nome già esistente (nel qual caso le funzioni verranno aggiunte al gruppo considerato) o un nuovo nome (nel qual caso apparirà in un nuovo gruppo).
* Promemoria: valori possibili per l&#39;attributo @name nel `<group>` sono:

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
>Assicurati di completare l&#39;attributo @label: questo è il nome che verrà visualizzato nell’elenco delle funzioni disponibili. Se non si immette nulla, il gruppo non avrà un nome. Tuttavia, se si immette un nome diverso da quello esistente, il nome dell’intero gruppo verrà modificato.

Se desideri aggiungere funzioni a diversi gruppi, puoi effettuare diverse operazioni `<group>`  gli elementi vengono tracciati nello stesso elenco.

Infine, un `<group>` può contenere la definizione di una o più funzioni, cioè lo scopo del file del pacchetto. La  `<function>`   è descritto nel paragrafo seguente.

## Descrittore della funzione &lt;function>&lt;/function> {#function-descriptor--function-}

Il caso presentato in questa sede è un caso generale in cui desideriamo fornire **implementazione delle funzioni**.

Di seguito è riportato un esempio di una funzione di &quot;maturità relativa&quot; che, utilizzando un&#39;età, indica per quanti anni la persona è stata considerata matura.

```
 <function name="relativeMaturity" type="long" args="(<Âge>)" help="Returns the difference between a date and 18 years"
              minArgs="1" maxArgs="1" display="Relative maturity of the person born on the date $1">
       <providerPart provider="PostgreSQL" body="extract(year from age($1))-18"/>
       <providerPart provider="MSSQL,Sybase,Teradata" body="[Other implementation]"/>
    </function>
```

La **@name** Il campo fa riferimento al nome della funzione e &quot;args&quot; è l’elenco dei parametri che verranno visualizzati nella descrizione. In questo caso, la funzione apparirà come &quot;relativaMaturezza ( `<age>` )&quot; nella finestra di selezione della funzione.

* **help** è il campo visualizzato nella parte inferiore della finestra dell’editor di espressioni.
* **@display** è un messaggio informativo.

   >[!NOTE]
   >
   >Negli attributi @help e @display , la stringa &quot;$1&quot; rappresenta il nome fornito nel primo parametro della funzione (qui, &quot;Age&quot;). $2, $3.. rappresentano i seguenti parametri. Nell&#39;attributo @body descritto di seguito, $1 indica il valore dell&#39;argomento passato alla funzione durante la chiamata .

   >[!NOTE]
   >
   >La descrizione deve essere una stringa di caratteri XML validi: notare l&#39;uso di &#39;&lt;&#39; e &#39;>&#39; invece di &lt; e >.

* **@type** è il tipo restituito dalla funzione ed è un valore standard (long, string, byte, datetime...). Se viene omesso, il server determina il tipo migliore tra i tipi disponibili all&#39;interno dell&#39;espressione che implementa la funzione.
* **@minArgs** e **maxArgs** designa il numero di parametri (minimo e massimo) per un parametro. Ad esempio, per una funzione con 2 parametri, minArgs e maxArgs saranno 2 e 2. Per 3 parametri, più 1 opzionale, saranno rispettivamente 3 e 4.
* Infine, la **providerPart** fornisce l’implementazione della funzione .

   * La **fornitore** attributo obbligatorio, specifica i sistemi di database per i quali viene fornita l&#39;implementazione. Come mostrato nell’esempio, quando le sintassi delle espressioni o le funzioni sottostanti differiscono, è possibile fornire implementazioni alternative in base al database.
   * La **@body** l&#39;attributo contiene l&#39;implementazione della funzione. Nota: questa implementazione deve essere un&#39;espressione, nel linguaggio del database (non un blocco di codice). A seconda dei database, le espressioni possono essere sottoquery (&quot;(selezionare la colonna dalla tabella in cui..)&quot;) che restituiscono un solo valore. Ad Oracle, questo è il caso (la query deve essere scritta tra parentesi).

   >[!NOTE]
   >
   >Se la funzione definita richiede solo uno o due database, è sempre possibile fornire solo le definizioni corrispondenti a tali database.

## Descrittore della funzione &#39;Pass-through&#39; {#pass-through--function-descriptor}

Un descrittore di funzione speciale è il **&quot;pass-through&quot;** blocco, con un sistema di database &quot;provider&quot; non specificato. In questo caso, l&#39;implementazione &quot;body&quot; può contenere solo una singola chiamata di funzione con una sintassi non dipendente dal database utilizzato. Nel frattempo, il blocco &quot;ProviderPart&quot; è univoco.

```
    <function name="CountAll" args="()" help="Counts the values returned (all fields together)"
              type="long" minArgs="0" maxArgs="0">
      <providerPart body="Count(*)"/>
    </function>
```

In questo caso, l&#39;aggiunta di una funzione serve solo a creare una funzione di database che non sarebbe stata disponibile per impostazione predefinita, ora visibile al client.

## Esempi {#examples}

Ulteriori esempi di funzioni sono disponibili nel pacchetto predefinito &quot;xtkdatakitfuncList.xml&quot;.
