---
product: campaign
title: Modificare i moduli
description: Modificare i moduli
feature: Configuration
role: Data Engineer, Developer
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 2%

---


# Modificare i moduli{#editing-forms}

## Panoramica

Gli addetti al marketing e gli operatori utilizzano i moduli di input per creare, modificare e visualizzare in anteprima i record. Forms mostra una rappresentazione visiva delle informazioni.

È possibile creare e modificare i moduli di input:

* È possibile modificare i moduli di input forniti per impostazione predefinita. I moduli di input di fabbrica si basano sugli schemi di dati di fabbrica.
* Puoi creare moduli di input personalizzati, in base agli schemi di dati definiti.

Forms sono entità di `xtk:form` tipo. È possibile visualizzare la struttura del modulo di input in `xtk:form` schema. Per visualizzare questo schema, scegli **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** dal menu. Ulteriori informazioni su [struttura del modulo](form-structure.md).

Per accedere ai moduli di input, scegliere **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** dal menu:

![](assets/d_ncs_integration_form_arbo.png)

Per progettare moduli, modificare il contenuto XML nell&#39;editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Ulteriori informazioni](form-structure.md#formatting).

Per visualizzare l&#39;anteprima di un modulo, fare clic su **[!UICONTROL Preview]** scheda:

![](assets/d_ncs_integration_form_preview.png)

## Tipi di modulo

È possibile creare diversi tipi di moduli di input. Il tipo di modulo determina il modo in cui gli utenti si spostano nel modulo:

* Schermata console

  Questo è il tipo di modulo predefinito. Il modulo comprende una singola pagina.

  ![](assets/console_screen_form.png)

* Gestione dei contenuti

  Utilizza questo tipo di modulo per la gestione dei contenuti. Vedi questo [caso d’uso](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistente virtuale

  Questo modulo comprende più schermi mobili ordinati in una sequenza specifica. Gli utenti possono passare da una schermata all’altra. [Ulteriori informazioni](form-structure.md#wizards).

* Iconbox

  Questo modulo comprende più pagine. Per spostarsi nel modulo, gli utenti selezionano le icone a sinistra del modulo.

  ![](assets/iconbox_form_preview.png)

* Notebook

  Questo modulo comprende più pagine. Per spostarsi nel modulo, gli utenti selezionano le schede nella parte superiore del modulo.

  ![](assets/notebook_form_preview.png)

* Riquadro verticale

  In questo modulo viene visualizzata una struttura di spostamento.

* Riquadro orizzontale

  Questo modulo mostra un elenco di elementi.

## Contenitori

Nei moduli è possibile utilizzare i contenitori per vari scopi:

* Organizzare i contenuti nei moduli
* Definire l’accesso ai campi di input
* Nidificare i moduli in altri moduli

[Ulteriori informazioni](form-structure.md#containers).

### Organizzare i contenuti

Utilizzare i contenitori per organizzare il contenuto nei moduli:

* Puoi raggruppare i campi in sezioni.
* È possibile aggiungere pagine a moduli multipagina.

Per inserire un contenitore, utilizza `<container>` elemento. [Ulteriori informazioni](form-structure.md#containers).

#### Raggruppa campi

Utilizza i contenitori per raggruppare i campi di input in sezioni organizzate.

Per inserire una sezione in un modulo, utilizzare questo elemento: `<container type="frame">`. Facoltativamente, per aggiungere un titolo di sezione, utilizza `label` attributo.

Sintassi: `<container type="frame" label="`*section_title*`"> […] </container>`

In questo esempio, un contenitore definisce **Creazione** sezione, che comprende **[!UICONTROL Created by]** e **[!UICONTROL Name]** campi di input:

```xml
<form _cs="Coupons (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Coupons"
      name="coupon" namespace="nms" type="default" xtkschema="xtk:form">
  <input xpath="@code"/>
  <input xpath="@type"/>
  <container label="Creation" type="frame">
    <input xpath="createdBy"/>
    <input xpath="createdBy/@name"/>
  </container>
</form>
```

![](assets/console_screen_form.png)

#### Aggiungere pagine a moduli multipagina

Per i moduli multipagina, utilizza un contenitore per creare una pagina modulo.

Questo esempio mostra i contenitori per **Generale** e **Dettagli** pagine di un modulo:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

### Definire l’accesso ai campi

Utilizza i contenitori per definire ciò che è visibile e per definire l’accesso ai campi. È possibile attivare o disattivare gruppi di campi.

### Nidificare i moduli

Utilizzare i contenitori per nidificare i moduli all&#39;interno di altri moduli. [Ulteriori informazioni](#add-pages-to-multipage-forms).

## Riferimenti a immagini

Per trovare le immagini, scegliere **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** dal menu.

Per associare un&#39;immagine a un elemento del modulo, ad esempio un&#39;icona, è possibile aggiungere un riferimento a un&#39;immagine. Utilizza il `img` , ad esempio, nel `<container>` elemento.

Sintassi: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Questo esempio mostra i riferimenti al `book.png` e `detail.png` immagini da `ncm` namespace:

```xml
<container img="ncm:book.png" label="General">
[…]
</container>
<container img="ncm:detail.png" label="Details">
[…]
</container>
```

Queste immagini sono utilizzate per le icone su cui gli utenti fanno clic per spostarsi in un modulo multipagina:

![](assets/nested_forms_preview.png)


## Creare un modulo semplice {#create-simple-form}

Per creare un modulo, eseguire la procedura seguente:

1. Dal menu, scegli **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
1. Fai clic su **[!UICONTROL New]** in alto a destra nell’elenco.

   ![](assets/input-form-create-1.png)

1. Specificare le proprietà del modulo:

   * Specifica il nome del modulo e lo spazio dei nomi.

     Il nome del modulo e lo spazio dei nomi possono corrispondere allo schema di dati correlato.  Questo esempio mostra un modulo per `cus:order` schema dati:

     ```xml
     <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
       […]
     </form>
     ```

     In alternativa, è possibile specificare esplicitamente lo schema dati nel `entity-schema` attributo.

     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Specificare l&#39;etichetta da visualizzare nel modulo.
   * Facoltativamente, specificare il tipo di modulo. Se non si specifica un tipo di modulo, per impostazione predefinita viene utilizzato il tipo di schermata della console.

     ![](assets/input-form-create-2.png)

     Se si progetta un modulo multipagina, è possibile omettere il tipo di modulo nel `<form>` e specificare il tipo in un contenitore.

1. Fai clic su **[!UICONTROL Save]**.

1. Inserire gli elementi del modulo.

   Ad esempio, per inserire un campo di input, utilizza `<input>` elemento. Imposta il `xpath` attributo al riferimento di campo come espressione XPath. [Ulteriori informazioni](schema-structure.md#referencing-with-xpath).

   Questo esempio mostra i campi di input basati su `nms:recipient` schema.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Se il modulo è basato su un tipo di schema specifico, è possibile cercare i campi per questo schema:

   1. Clic **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. Seleziona il campo e fai clic su **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Facoltativamente, specifica l’editor di campi.

   A ciascun tipo di dati è associato un editor di campi predefinito:
   * Per un campo di tipo data, nel modulo viene visualizzato un calendario di input.
   * Per un campo di tipo enumerazione, il modulo mostra un elenco di selezione.

   Puoi utilizzare i seguenti tipi di editor di campi:

   | Editor campo | Attributo modulo |
   | --- | --- |
   | Pulsante di opzione | `type="radiobutton"` |
   | Casella di controllo | `type="checkbox"` |
   | Modifica struttura | `type="tree"` |

   Ulteriori informazioni su [controlli elenco memoria](form-structure.md#memory-list-controls).

1. Facoltativamente, definisci l’accesso ai campi:

   | Elemento “element” | Attributo | Descrizione |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Fornisce accesso in sola lettura a un campo |
   | `<container>` | `type="visibleGroup" visibleIf="`*edit-expr*`"` | Visualizza un gruppo di campi in modo condizionale |
   | `<container>` | `type="enabledGroup" enabledIf="`*edit-expr*`"` | Abilita un gruppo di campi in modo condizionale |

   Esempio:

   ```xml
   <container type="enabledGroup" enabledIf="@gender=1">
     […]
   </container>
   <container type="enabledGroup" enabledIf="@gender=2">
     […]
   </container>
   ```

1. Facoltativamente, utilizza i contenitori per raggruppare i campi in sezioni.

   ```xml
   <container type="frame" label="Name">
      <input xpath="@firstName"/>
      <input xpath="@lastName"/>
   </container>
   <container type="frame" label="Contact details">
      <input xpath="@email"/>
      <input xpath="@phone"/>
   </container>
   ```

   ![](assets/input-form-create-3.png)

## Creare un modulo multipagina {#create-multipage-form}

Puoi creare moduli multipagina. È inoltre possibile nidificare i moduli all&#39;interno di altri moduli.

### Creare un `iconbox` modulo

Utilizza il `iconbox` tipo di modulo per visualizzare le icone a sinistra del modulo, che portano gli utenti a pagine diverse del modulo.

![](assets/iconbox_form_preview.png)

Per modificare il tipo di un modulo esistente in `iconbox`, effettua le seguenti operazioni:

1. Modificare il `type` attributo del `<form>` elemento a `iconbox`:

   ```xml
   <form […] type="iconbox">
   ```

1. Impostare un contenitore per ogni pagina del modulo:

   1. Aggiungi un `<container>` elemento come elemento figlio di `<form>` elemento.
   1. Per definire un’etichetta e un’immagine per l’icona, utilizza `label` e `img` attributi.

      ```xml
      <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="iconbox" xtkschema="xtk:form">
          <container img="xtk:properties.png" label="General">
              <input xpath="@label"/>
              <input xpath="@name"/>
              […]
          </container>
          <container img="nms:msgfolder.png" label="Details">
              <input xpath="@address"/>
              […]
          </container>
          <container img="nms:supplier.png" label="Services">
              […]
          </container>
      </form>
      ```

   In alternativa, rimuovi il `type="frame"` attributo esistente `<container>` elementi.

### Creare un modulo per blocchi appunti

Utilizza il `notebook` tipo di modulo per visualizzare le schede nella parte superiore del modulo, che portano gli utenti a pagine diverse.

![](assets/notebook_form_preview.png)

Per modificare il tipo di un modulo esistente in `notebook`, effettua le seguenti operazioni:

1. Modificare il `type` attributo del `<form>` elemento a `notebook`:

   ```xml
   <form […] type="notebook">
   ```

1. Aggiungi un contenitore per ogni pagina modulo:

   1. Aggiungi un `<container>` elemento come elemento figlio di `<form>` elemento.
   1. Per definire l’etichetta e l’immagine dell’icona, utilizza la `label` e `img` attributi.

   ```xml
     <form entitySchema="xtk:form" name="Service provider" namespace="nms" type="notebook" xtkschema="xtk:form">
         <container label="General">
             <input xpath="@label"/>
             <input xpath="@name"/>
             […]
         </container>
         <container label="Details">
             <input xpath="@address"/>
             […]
         </container>
         <container label="Services">
             […]
         </container>
     </form>
   ```

   In alternativa, rimuovi il `type="frame"` attributo esistente `<container>` elementi.

### Nidificare i moduli

È possibile nidificare i moduli all&#39;interno di altri moduli. Ad esempio, è possibile nidificare i moduli notebook all&#39;interno dei moduli iconbox.

Il livello di nidificazione controlla la navigazione. Gli utenti possono eseguire il drill-down alle sottomaschere.

Per nidificare un modulo all&#39;interno di un altro modulo, inserire un `<container>` e impostare `type` al tipo di modulo. Per il modulo di primo livello, è possibile impostare il tipo di modulo in un contenitore esterno o nel `<form>` elemento.

### Esempio

Questo esempio mostra un modulo complesso:

* Il modulo di primo livello è un modulo iconbox. Questo modulo comprende due contenitori etichettati **Generale** e **Dettagli**.

  Di conseguenza, nella maschera esterna viene visualizzato **Generale** e **Dettagli** pagine al livello superiore. Per accedere a queste pagine, gli utenti possono fare clic sulle icone a sinistra del modulo.

* La sottomaschera è una maschera del blocco appunti nidificata all&#39;interno del **Generale** contenitore. La sottomaschera comprende due contenitori etichettati **Nome** e **Contatto**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Di conseguenza, il **Generale** nella pagina del modulo esterno viene visualizzata la **Nome** e **Contatto** schede.

![](assets/nested_forms_preview.png)

Per nidificare un modulo all&#39;interno di un altro modulo, inserire un `<container>` e impostare `type` al tipo di modulo. Per il modulo di primo livello, è possibile impostare il tipo di modulo in un contenitore esterno o nel `<form>` elemento.

### Esempio

Questo esempio mostra un modulo complesso:

* Il modulo di primo livello è un modulo iconbox. Questo modulo comprende due contenitori etichettati **Generale** e **Dettagli**.

  Di conseguenza, nella maschera esterna viene visualizzato **Generale** e **Dettagli** pagine al livello superiore. Per accedere a queste pagine, gli utenti possono fare clic sulle icone a sinistra del modulo.

* La sottomaschera è una maschera del blocco appunti nidificata all&#39;interno del **Generale** contenitore. La sottomaschera comprende due contenitori etichettati **Nome** e **Contatto**.

```xml
<form _cs="Profile (nms)" entitySchema="xtk:form" img="xtk:form.png" label="Profile" name="profile" namespace="nms" xtkschema="xtk:form">
  <container type="iconbox">
    <container img="ncm:general.png" label="General">
      <container type="notebook">
        <container label="Name">
          <input xpath="@firstName"/>
          <input xpath="@lastName"/>
        </container>
        <container label="Contact">
          <input xpath="@email"/>
        </container>
      </container>
    </container>
    <container img="ncm:detail.png" label="Details">
      <input xpath="@birthDate"/>
    </container>
  </container>
</form>
```

Di conseguenza, il **Generale** nella pagina del modulo esterno viene visualizzata la **Nome** e **Contatto** schede.

![](assets/nested_forms_preview.png)



## Modificare un modulo di input di fabbrica {#modify-factory-form}

Per modificare un modulo di fabbrica, effettuare le seguenti operazioni:

1. Modificare il modulo di input di fabbrica:

   1. Dal menu, scegli **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]**.
   1. Selezionare un modulo di input e modificarlo.

   È possibile estendere gli schemi di dati di fabbrica, ma non i moduli di input di fabbrica. È consigliabile modificare direttamente i moduli di input di fabbrica senza ricrearli. Durante gli aggiornamenti del software, le modifiche nei moduli di input di fabbrica vengono unite agli aggiornamenti. Se l&#39;unione automatica non riesce, è possibile risolvere i conflitti. [Ulteriori informazioni](../../production/using/upgrading.md#resolving-conflicts).

   Ad esempio, se si estende uno schema di fabbrica con un campo aggiuntivo, è possibile aggiungere questo campo al relativo modulo di fabbrica.

## Convalida moduli {#validate-forms}

È possibile includere controlli di convalida nelle maschere.

### Concedere l’accesso in sola lettura ai campi

Per concedere l’accesso in sola lettura a un campo, utilizza `readOnly="true"` attributo. È ad esempio possibile visualizzare la chiave primaria di un record, ma con accesso in sola lettura. [Ulteriori informazioni](form-structure.md#non-editable-fields).

In questo esempio, la chiave primaria (`iRecipientId`) del `nms:recipient` lo schema viene visualizzato in accesso in sola lettura:

```xml
<value xpath="@iRecipientId" readOnly="true"/>
```

### Controlla campi obbligatori

Puoi controllare le informazioni obbligatorie:

* Utilizza il `required="true"` per i campi obbligatori.
* Utilizza il `<leave>` per controllare questi campi e visualizzare i messaggi di errore.

In questo esempio, l’indirizzo e-mail è obbligatorio e viene visualizzato un messaggio di errore se l’utente non ha fornito queste informazioni:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Ulteriori informazioni su [campi espressione](form-structure.md#expression-field) e [contesto modulo](form-structure.md#context-of-forms).

### Convalida valori

Puoi utilizzare le chiamate SOAP JavaScript per convalidare i dati del modulo dalla console. Utilizza queste chiamate per la convalida complessa, ad esempio, per confrontare un valore con un elenco di valori autorizzati. [Ulteriori informazioni](form-structure.md#soap-methods).

1. Crea una funzione di convalida in un file JS.

   Esempio:

   ```js
   function nms_recipient_checkValue(value)
   {
     logInfo("checking value " + value)
     if (…)
     {
       logError("Value " + value + " is not valid")
     }
     return 1
   }
   ```

   In questo esempio, la funzione è denominata `checkValue`. Questa funzione viene utilizzata per controllare `recipient` tipo di dati in `nms` spazio dei nomi. Il valore che viene controllato viene registrato. Se il valore non è valido, viene registrato un messaggio di errore. Se il valore è valido, viene restituito il valore 1.

   È possibile utilizzare il valore restituito per modificare il modulo.

1. Nel modulo, aggiungi `<soapCall>` elemento al `<leave>` elemento.

   In questo esempio, viene utilizzata una chiamata SOAP per convalidare `@valueToCheck` stringa:

   ```xml
   <form name="recipient" (…)>
   (…)
     <leave>
       <soapCall name="checkValue" service="nms:recipient">
         <param exprIn="@valueToCheck" type="string"/>
       </soapCall>
     </leave>
   </form>
   ```

   In questo esempio, la proprietà `checkValue` e il `nms:recipient` servizio utilizzato:

   * Il servizio è lo spazio dei nomi e il tipo di dati.
   * Il metodo è il nome della funzione. Il nome distingue tra maiuscole e minuscole.

   La chiamata viene eseguita in modo sincrono.

   Vengono visualizzate tutte le eccezioni. Se si utilizza `<leave>` , gli utenti non potranno salvare il modulo finché le informazioni immesse non saranno convalidate.

In questo esempio viene illustrato come effettuare chiamate di servizio all&#39;interno dei moduli:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

In questo esempio, l’input è un ID, che è una chiave primaria. Quando gli utenti compilano il modulo per questo ID, viene effettuata una chiamata SOAP con questo ID come parametro di input. L’output è un valore booleano scritto in questo campo: `/tmp/@count`. Puoi utilizzare questo valore booleano all’interno del modulo. Ulteriori informazioni su [contesto modulo](form-structure.md#context-of-forms).
