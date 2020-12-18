---
solution: Campaign Classic
product: campaign
title: Integrazione tramite JavaScript (lato client)
description: Integrazione tramite JavaScript (lato client)
audience: interaction
content-type: reference
topic-tags: unitary-interactions
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1140'
ht-degree: 2%

---


# Integrazione tramite JavaScript (lato client){#integration-via-javascript-client-side}

Per chiamare il motore di interazione in una pagina Web, inserire una chiamata a un codice JavaScript direttamente nella pagina. Questa chiamata restituisce il contenuto dell&#39;offerta in un oggetto

element.

 Adobe consiglia di utilizzare il metodo di integrazione JavaScript.

Lo script che richiama l&#39;URL avrà l&#39;aspetto seguente:

```
<script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=" type="text/javascript"></script>
```

Il parametro &quot;**env**&quot; riceve il nome interno dell&#39;ambiente live dedicato alle interazioni anonime.

Per presentare un&#39;offerta, è necessario creare un ambiente e uno spazio di offerta in  Adobe Campaign, quindi configurare la pagina HTML.

I seguenti casi di utilizzo descrivono le possibili opzioni per l&#39;integrazione delle offerte tramite JavaScript.

## Modalità HTML {#html-mode}

### Presentazione di un&#39;offerta anonima {#presenting-an-anonymous-offer}

1. **Preparazione del motore di interazione**

   Aprite l&#39;interfaccia Adobe Campaign  e preparate un ambiente anonimo.

   Create uno spazio di offerta collegato all&#39;ambiente anonimo.

   Create un&#39;offerta e la relativa rappresentazione collegata allo spazio dell&#39;offerta.

1. **Contenuto della pagina HTML**

   La pagina HTML deve includere un

   con un attributo @id con il valore del nome interno dello spazio delle offerte creato (&quot;spazio dei nomi i_internal&quot;). L&#39;offerta verrà inserita in questo
per interazione.

   Nel nostro esempio, l&#39;attributo @id riceve il valore &quot;i_SPC12&quot;, dove &quot;SPC12&quot; è il nome interno dello spazio delle offerte creato in precedenza:

   ```
   <div id="i_SPC12"></div>
   ```

   Nel nostro esempio, l&#39;URL per la chiamata dello script è il seguente (&quot;OE3&quot; è il nome interno dell&#39;ambiente live):

   ```
   <script id="interactionProposalScript" src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" type="text/javascript"></script>
   ```

   >[!IMPORTANT]
   >
   >Il tag `<script>` non deve chiudersi automaticamente.

   Questa chiamata statica genererà automaticamente una chiamata dinamica contenente tutti i parametri richiesti dal motore di interazione.

   Questo comportamento consente di utilizzare diversi spazi di offerta sulla stessa pagina, da gestire con una singola chiamata al motore.

1. **Risultati nella pagina HTML**

   Il contenuto della rappresentazione dell&#39;offerta viene restituito alla pagina HTML dal motore di interazione:

   ```
   <div id="banner_header">
     <div id="i_SPC12">
       <table>
         <tbody>
           <tr>
             <td><h3>Fly to Japan!</h3></td>
           </tr>
           <tr>
             <td><img width="150px" src="https://instance.adobe.org/res/Track/874fdaf72ddc256b2d8260bb8ec3a104.jpg"></td>
             <td>
               <p>Discover Japan for 2 weeks at an unbelievable price!!</p>
               <p><b>2345 Dollars - All inclusive</b></p>
             </td>
           </tr>
         </tbody>
       </table>
     </div>
     <script src="https://instance.adobe.org:8080/nl/interactionProposal.js?env=OE3" id="interactionProposalScript" type="text/javascript"></script>
   </div>
   ```

### Presentazione di un&#39;offerta identificata {#presenting-an-identified-offer}

Per presentare un&#39;offerta a un contatto identificato, il processo è simile a quello descritto qui: [Presentazione di un&#39;offerta anonima](#presenting-an-anonymous-offer). Nel contenuto della pagina Web, è necessario aggiungere il seguente script che identificherà il contatto durante la chiamata al motore:

```
<script type="text/javascript">
  interactionTarget = <contact_identifier>;
</script>
```

1. Andate allo spazio delle offerte che verrà richiamato dalla pagina Web, fate clic su **[!UICONTROL Advanced parameters]** e aggiungete una o più chiavi di identificazione.

   ![](assets/interaction_htmlmode_001.png)

   In questo esempio, la chiave di identificazione è composita in quanto si basa sia sull&#39;e-mail che sul nome del destinatario.

1. Durante la visualizzazione della pagina Web, la valutazione dello script consente di trasmettere l&#39;ID destinatario al motore delle offerte. Se l’ID è composito, i tasti vengono visualizzati nella stessa sequenza utilizzata nelle impostazioni avanzate e separati da un |

   Nell&#39;esempio seguente, il contatto ha eseguito l&#39;accesso al sito Web ed è stato riconosciuto durante la chiamata al motore di interazione grazie alla propria e-mail e nome.

   ```
   <script type="text/javascript">
     interactionTarget = myEmail|myName;
   </script>
   ```

### Utilizzo di una funzione di rendering HTML {#using-an-html-rendering-function}

Per generare automaticamente la rappresentazione dell&#39;offerta HTML, potete utilizzare una funzione di rendering.

1. Andate nello spazio delle offerte e fate clic sul collegamento **[!UICONTROL Edit functions]**.
1. Seleziona **[!UICONTROL Overload the HTML rendering function]**.
1. Andate alla scheda **[!UICONTROL HTML rendering]** e inserite le variabili che corrispondono ai campi definiti per il contenuto dell&#39;offerta nello spazio dell&#39;offerta.

   ![](assets/interaction_htmlmode_002.png)

   In questo esempio, l&#39;offerta viene visualizzata sotto forma di banner in una pagina Web e comprende un&#39;immagine su cui è possibile fare clic e un titolo che corrisponde ai campi definiti nel contenuto dell&#39;offerta.

## Modalità XML {#xml-mode}

### Presentazione di un&#39;offerta {#presenting-an-offer}

L&#39;interazione consente di restituire un nodo XML alla pagina HTML che richiama il motore delle offerte. Questo nodo XML può essere elaborato da funzioni da sviluppare sul lato cliente.

La chiamata al motore di interazione si presenta così:

```
<script type="text/javascript" id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=&cb="></script>
```

Il parametro &quot;**env**&quot; riceve il nome interno dell&#39;ambiente live.

Il parametro &quot;**cb**&quot; riceve il nome della funzione che leggerà il nodo XML restituito dal motore contenente le proposizioni (callback). Questo parametro è facoltativo.

Il parametro &quot;**t**&quot; riceve il valore della destinazione, solo per un&#39;interazione identificata. Questo parametro può essere trasmesso anche con la variabile **interactiveTarget**. Questo parametro è facoltativo.

Il parametro &quot;**c**&quot; riceve l&#39;elenco dei nomi interni delle categorie. Questo parametro è facoltativo.

Il parametro &quot;**th**&quot; riceve l&#39;elenco dei temi. Questo parametro è facoltativo.

Il parametro &quot;**gctx**&quot; riceve i dati della chiamata globali (contesto) per l’intera pagina. Questo parametro è facoltativo.

Il nodo XML restituito è simile al seguente:

```
<propositions>
 <proposition id="" offer-id="" weight="" rank="" space="" div=""> //proposition identifiers
   ...XML content defined in Adobe Campaign...
 </proposition>
 ...
</propositions>
```

Il seguente caso d’uso descrive le configurazioni da eseguire in  Adobe Campaign per abilitare la modalità XML, quindi mostra il risultato della chiamata al motore nella pagina HTML.

1. **Creazione di un ambiente e di uno spazio di offerta**

   Per ulteriori informazioni sulla creazione di un ambiente, vedere [Live/Design environment](../../interaction/using/live-design-environments.md).

   Per ulteriori informazioni sulla creazione di uno spazio per le offerte, consultate [Creazione di spazi per le offerte](../../interaction/using/creating-offer-spaces.md).

1. **Estensione dello schema delle offerte per aggiungere nuovi campi**

   Questo schema definisce i campi seguenti: Titolo numero 2 e prezzo.

   Il nome dello schema nell&#39;esempio è **cus:offer**

   ```
   <srcSchema _cs="Marketing offers (cus)" created="2013-01-18 17:14:20.762Z" createdBy-id="0"
              desc="" entitySchema="xtk:srcSchema" extendedSchema="nms:offer" img="nms:offer.png"
              label="Marketing offers" labelSingular="Marketing offers" lastModified="2013-01-18 15:20:18.373Z"
              mappingType="sql" md5="F14A7AA009AE1FCE31B0611E72866AC3" modifiedBy-id="0"
              name="offer" namespace="cus" xtkschema="xtk:srcSchema">
     <createdBy _cs="Administrator (admin)"/>
     <modifiedBy _cs="Administrator (admin)"/>
     <element img="nms:offer.png" label="Marketing offers" labelSingular="Marketing offer"
              name="offer">
       <element label="Content" name="view">
         <element label="Price" name="price" type="long" xml="true"/>
         <element label="Title 2" name="title2" type="string" xml="true"/>
   
         <element advanced="true" desc="Price calculation script." label="Script price"
                  name="price_jst" type="CDATA" xml="true"/>
         <element advanced="true" desc="Title calculation script." label="Script title"
                  name="title2_jst" type="CDATA" xml="true"/>
       </element>
     </element>
   </srcSchema>
   ```

   >[!IMPORTANT]
   >
   >Ogni elemento deve essere definito due volte. Gli elementi di tipo CDATA (&quot;_jst&quot;) possono contenere campi di personalizzazione.
   >
   >Non dimenticare di aggiornare la struttura del database. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../configuration/using/updating-the-database-structure.md).

   >[!NOTE]
   >
   >Potete estendere lo schema delle offerte per aggiungere nuovi campi sia in modalità batch che unitaria, nonché in qualsiasi formato (testo, HTML e XML).

1. **Estensione della formula dell&#39;offerta per modificare nuovi campi e modificare un campo esistente**

   Modificate il modulo di input **Offer (nsm)**.

   Nella sezione &quot;Viste&quot;, inserite i due nuovi campi con il seguente contenuto:

   ```
   <input label="Title 2" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="title2_jst">
                   <form label="Edit title 2" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizeTitle2">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizeTitle2"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input nolabel="true" type="edit" xpath="title2_jst"/>
   
                 <input label="Price" margin-right="5" prebuildSubForm="false" type="subFormLink"
                        xpath="price_jst">
                   <form label="Edit price" name="editForm" nothingToSave="true">
                     <input nolabel="true" toolbarAlign="horizontal" type="jstEdit"
                            xpath="." xpathInsert="/ignored/customizePrice">
                       <container>
                         <input menuId="viewMenuBuilder" options="inbound" type="customizeBtn"
                                xpath="/ignored/customizePrice"/>
                       </container>
                     </input>
                   </form>
                 </input>
                 <input colspan="2" label="Prix" nolabel="true" type="number" xpath="price_jst"/>
   ```

   Aggiungete un commento al campo URL di destinazione:

   ![](assets/interaction_xmlmode_form_001.png)

   >[!IMPORTANT]
   >
   >I campi del modulo ( `<input>`) devono puntare agli elementi del tipo CDATA definiti nello schema creato.

   Il rendering nel modulo delle rappresentazioni delle offerte è simile al seguente:

   ![](assets/interaction_xmlmode_form.png)

   I campi **[!UICONTROL Title 2]** e **[!UICONTROL Price]** sono stati aggiunti e il campo **[!UICONTROL Destination URL]** non viene più visualizzato.

1. **Creazione di un’offerta**

   Per ulteriori informazioni sulla creazione di offerte, consultate [Creazione di un&#39;offerta](../../interaction/using/creating-an-offer.md).

   Nel caso di utilizzo seguente, l&#39;offerta è inserita come segue:

   ![](assets/interaction_xmlmode_offer.png)

1. Approvare un&#39;offerta o farla approvare da qualcun altro, quindi attivarla nello spazio dell&#39;offerta creato all&#39;ultimo passaggio in modo che sia disponibile nell&#39;ambiente live collegato.
1. **Chiamate del motore e risultati sulla pagina HTML**

   La chiamata al motore di interazione nella pagina HTML si presenta come segue:

   ```
   <script id="interactionProposalScript" src="https://<SERVER_URL>/nl/interactionProposal.js?env=OE7&cb=alert" type="text/javascript">
   ```

   Il valore del parametro &quot;**env**&quot; è il nome interno dell&#39;ambiente live.

   Il valore del parametro &quot;**cb**&quot; è il nome della funzione che deve interpretare il nodo XML restituito dal motore. Nel nostro esempio, la funzione richiamata apre una finestra modale (funzione alert()).

   Il nodo XML restituito dal motore di interazione ha l&#39;aspetto seguente:

   ```
   <propositions>
    <proposition id="a28002" offer-id="10322005" weight="1" rank="1" space="SPC14" div="i_SPC14">
     <xmlOfferView>
      <title>Travel to Russia</title>
      <price>3456</price>
      <description>Discover this vacation package!INCLUDES 10 nights. FEATURES buffet breakfast daily. BONUS 5th night free.</description>
      <image>
       <path>https://myinstance.com/res/Track/ae1d2113ed732d58a3beb441084e5960.jpg</path>
       <alt>Travel to Russia</alt>
      </image>
     </xmlOfferView>
    </proposition>
   </propositions>
   ```

### Utilizzo di una funzione di rendering {#using-a-rendering-function-}

È possibile utilizzare una funzione di rendering XML per creare una presentazione di offerta. Questa funzione modificherà il nodo XML che viene restituito alla pagina HTML durante la chiamata al motore.

1. Andate nello spazio delle offerte e fate clic sul collegamento **[!UICONTROL Edit functions]**.
1. Seleziona **[!UICONTROL Overload the XML rendering function]**.
1. Fare clic sulla scheda **[!UICONTROL XML rendering]** e inserire la funzione desiderata.

   La funzione può essere simile alla seguente:

   ```
   function (proposition) {
     delete proposition.@id;
     proposition.@newAttribute = "newValue";
   } 
   ```

![](assets/interaction_xmlmode_001.png)

