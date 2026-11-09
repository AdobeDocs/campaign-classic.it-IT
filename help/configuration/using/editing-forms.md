---
product: campaign
title: Modificare i moduli
description: Modificare i moduli
feature: Configuration
role: Developer
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: 24604dc9-f675-4e37-a848-f1911be84f3e
TQID: 'https://experienceleague.adobe.com/9HCx821ff3mVcpUhmpUziFpZdmAnPUC49ootzGDOjLQ'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
    internal-label: Schemas
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
    internal-label: PI
  - id: eff19c99-440a-4318-b319-444edc4d8d8f
    internal-label: Upgrade
  - id: a14877cc-63b1-41d9-bf0b-5f97cadd0417
    internal-label: Configuration guidelines
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 3%
---
# Modificare i moduli{#editing-forms}

## Panoramica

Gli addetti al marketing e gli operatori utilizzano i moduli di input per creare, modificare e visualizzare in anteprima i record. Forms mostra una rappresentazione visiva delle informazioni.

>[!NOTE]
>
>Nell’ambito della transizione da Campaign v7 a v8, il set di documentazione di Campaign Classic è stato razionalizzato e riorganizzato. Le funzioni comuni sono ora disponibili esclusivamente nel set di documentazione di Campaign v8. Per ulteriori informazioni sui moduli di input, consulta la [documentazione di Campaign v8](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms){target=_blank}.
>
>[![immagine](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms){target=_blank}

È possibile creare e modificare i moduli di input:

* È possibile modificare i moduli di input forniti per impostazione predefinita. I moduli di input di fabbrica si basano sugli schemi di dati di fabbrica.
* Puoi creare moduli di input personalizzati, in base agli schemi di dati definiti.

Forms sono entità di tipo `xtk:form`. È possibile visualizzare la struttura del modulo di input nello schema `xtk:form`. Per visualizzare questo schema, scegli **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Data schemas]** dal menu. Ulteriori informazioni sulla [struttura modulo](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} (documentazione di Campaign v8).

Per accedere ai moduli di input, scegliere **[!UICONTROL Administration]> [!UICONTROL Configuration] >[!UICONTROL Input forms]** dal menu:

![](assets/d_ncs_integration_form_arbo.png)

Per progettare moduli, modificare il contenuto XML nell&#39;editor XML:

![](assets/d_ncs_integration_form_edit.png)

[Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#formatting){target="_blank"} (documentazione di Campaign v8).

Per visualizzare l&#39;anteprima di un modulo, fare clic sulla scheda **[!UICONTROL Preview]**:

![](assets/d_ncs_integration_form_preview.png)

## Tipi di modulo

È possibile creare diversi tipi di moduli di input. Il tipo di modulo determina il modo in cui gli utenti si spostano nel modulo:

* Schermata console

  Questo è il tipo di modulo predefinito. Il modulo comprende una singola pagina.

  ![](assets/console_screen_form.png)

* Gestione dei contenuti

  Utilizza questo tipo di modulo per la gestione dei contenuti. Vedi questo [caso d&#39;uso](../../delivery/using/use-case-creating-content-management.md).

  ![](../../delivery/using/assets/d_ncs_content_form13.png)

* Assistente

  Questo modulo comprende più schermi mobili ordinati in una sequenza specifica. Gli utenti possono passare da una schermata all’altra. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#wizards){target="_blank"} (documentazione di Campaign v8).

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

## Riferimenti a immagini

Per trovare le immagini, scegliere **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Images]** dal menu.

Per associare un&#39;immagine a un elemento del modulo, ad esempio un&#39;icona, è possibile aggiungere un riferimento a un&#39;immagine. Utilizzare l&#39;attributo `img`, ad esempio, nell&#39;elemento `<container>`.

Sintassi: `img="`*`namespace`*`:`*`filename`*`.`*`extension`*`"`

Questo esempio mostra i riferimenti alle immagini `book.png` e `detail.png` dallo spazio dei nomi `ncm`:

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

1. Scegliere **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** dal menu.
1. Fare clic sul pulsante **[!UICONTROL New]** in alto a destra nell&#39;elenco.

   ![](assets/input-form-create-1.png)

1. Specificare le proprietà del modulo:

   * Specifica il nome del modulo e lo spazio dei nomi.

     Il nome del modulo e lo spazio dei nomi possono corrispondere allo schema di dati correlato.  Questo esempio mostra un modulo per lo schema dati `cus:order`:

     ```xml
     <form entitySchema="xtk:form" img="xtk:form.png" label="Order" name="order" namespace="cus" type="iconbox" xtkschema="xtk:form">
       […]
     </form>
     ```

     In alternativa, è possibile specificare esplicitamente lo schema dati nell&#39;attributo `entity-schema`.

     ```xml
     <form entity-schema="cus:stockLine" entitySchema="xtk:form" img="xtk:form.png" label="Stock order" name="stockOrder" namespace="cus" xtkschema="xtk:form">
       […]
     </form>
     ```

   * Specificare l&#39;etichetta da visualizzare nel modulo.
   * Facoltativamente, specificare il tipo di modulo. Se non si specifica un tipo di modulo, per impostazione predefinita viene utilizzato il tipo di schermata della console.

     ![](assets/input-form-create-2.png)

     Se si progetta un modulo multipagina, è possibile omettere il tipo di modulo nell&#39;elemento `<form>` e specificare il tipo in un contenitore.

1. Fai clic su **[!UICONTROL Save]**.

1. Inserire gli elementi del modulo.

   Ad esempio, per inserire un campo di input, utilizzare l&#39;elemento `<input>`. Impostare l&#39;attributo `xpath` sul riferimento di campo come espressione XPath. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/schema-structure#reference-with-xpath){target="_blank"} (documentazione di Campaign v8).

   Questo esempio mostra i campi di input basati sullo schema `nms:recipient`.

   ```xml
   <input xpath="@firstName"/>
   <input xpath="@lastName"/>
   ```

1. Se il modulo è basato su un tipo di schema specifico, è possibile cercare i campi per questo schema:

   1. Fare clic su **[!UICONTROL Insert]** > **[!UICONTROL Document fields]**.

      ![](assets/input-form-create-4.png)

   1. Selezionare il campo e fare clic su **[!UICONTROL OK]**.

      ![](assets/input-form-create-5.png)

1. Facoltativamente, specifica l’editor di campi.

   A ciascun tipo di dati è associato un editor di campi predefinito:
   * Per un campo di tipo data, nel modulo viene visualizzato un calendario di input.
   * Per un campo di tipo enumerazione, il modulo mostra un elenco di selezione.

   Puoi utilizzare i seguenti tipi di editor di campi:

   | Editor campo | Attributo modulo |
   | --- | --- |
   | Pulsante di scelta | `type="radiobutton"` |
   | Casella di controllo | `type="checkbox"` |
   | Modifica struttura | `type="tree"` |

   Ulteriori informazioni sui [controlli elenco memoria](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#memory-list-controls){target="_blank"} (documentazione di Campaign v8).

1. Facoltativamente, definisci l’accesso ai campi:

   | Elemento “element” | Attributo | Descrizione |
   | --- | --- | --- |
   | `<input>` | `read-only="true"` | Fornisce accesso in sola lettura a un campo |
   | `<container>` | `type="visibleGroup" visibleIf="`*modifica-espr*`"` | Visualizza un gruppo di campi in modo condizionale |
   | `<container>` | `type="enabledGroup" enabledIf="`*modifica-espr*`"` | Abilita un gruppo di campi in modo condizionale |

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

Puoi creare moduli multipagina. È inoltre possibile nidificare i moduli all&#39;interno di altri moduli. Ulteriori informazioni su [contenitori, moduli per notebook e iconbox](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#containers){target="_blank"} (documentazione di Campaign v8).

## Modificare un modulo di input di fabbrica {#modify-factory-form}

Per modificare un modulo di fabbrica, effettuare le seguenti operazioni:

1. Modificare il modulo di input di fabbrica:

   1. Scegliere **[!UICONTROL Administration]** > **[!UICONTROL Configuration]** > **[!UICONTROL Input forms]** dal menu.
   1. Selezionare un modulo di input e modificarlo.

   È possibile estendere gli schemi di dati di fabbrica, ma non i moduli di input di fabbrica. È consigliabile modificare direttamente i moduli di input di fabbrica senza ricrearli. Durante gli aggiornamenti del software, le modifiche nei moduli di input di fabbrica vengono unite agli aggiornamenti. Se l&#39;unione automatica non riesce, è possibile risolvere i conflitti. [Ulteriori informazioni](../../production/using/upgrading.md#resolving-conflicts).

   Ad esempio, se si estende uno schema di fabbrica con un campo aggiuntivo, è possibile aggiungere questo campo al relativo modulo di fabbrica.

## Convalida moduli {#validate-forms}

È possibile includere controlli di convalida nelle maschere.

### Controlla campi obbligatori

Puoi controllare le informazioni obbligatorie:

* Utilizzare l&#39;attributo `required="true"` per i campi obbligatori.
* Utilizza il nodo `<leave>` per controllare questi campi e visualizzare i messaggi di errore.

In questo esempio, l’indirizzo e-mail è obbligatorio e viene visualizzato un messaggio di errore se l’utente non ha fornito queste informazioni:

```xml
<input xpath="@email" required="true"/>
<leave>
  <check expr="@email!=''">
    <error>The email address is required.</error>
  </check>
</leave>
```

Ulteriori informazioni sui [campi espressione](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#expression-field){target="_blank"} (documentazione di Campaign v8) e sul [contesto modulo](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#context-of-forms){target="_blank"} (documentazione di Campaign v8).

### Convalida valori

Puoi utilizzare le chiamate SOAP di JavaScript per convalidare i dati del modulo dalla console. Utilizza queste chiamate per la convalida complessa, ad esempio, per confrontare un valore con un elenco di valori autorizzati. [Ulteriori informazioni](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#soap-methods){target="_blank"} (documentazione di Campaign v8).

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

   In questo esempio, la funzione è denominata `checkValue`. Questa funzione viene utilizzata per controllare il tipo di dati `recipient` nello spazio dei nomi `nms`. Il valore che viene controllato viene registrato. Se il valore non è valido, viene registrato un messaggio di errore. Se il valore è valido, viene restituito il valore 1.

   È possibile utilizzare il valore restituito per modificare il modulo.

1. Nel modulo, aggiungi l&#39;elemento `<soapCall>` all&#39;elemento `<leave>`.

   In questo esempio, viene utilizzata una chiamata SOAP per convalidare la stringa `@valueToCheck`:

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

   In questo esempio vengono utilizzati il metodo `checkValue` e il servizio `nms:recipient`:

   * Il servizio è lo spazio dei nomi e il tipo di dati.
   * Il metodo è il nome della funzione. Il nome distingue tra maiuscole e minuscole.

   La chiamata viene eseguita in modo sincrono.

   Vengono visualizzate tutte le eccezioni. Se si utilizza l&#39;elemento `<leave>`, gli utenti non potranno salvare il modulo finché le informazioni immesse non saranno convalidate.

In questo esempio viene illustrato come effettuare chiamate di servizio all&#39;interno dei moduli:

```xml
<enter>
  <soapCall name="client" service="c4:ybClient">
    <param exprIn="@id" type="string"/>
    <param type="boolean" xpathOut="/tmp/@count"/>
  </soapCall>
</enter>
```

In questo esempio, l’input è un ID, che è una chiave primaria. Quando gli utenti compilano il modulo per questo ID, viene effettuata una chiamata SOAP con questo ID come parametro di input. L&#39;output è un valore booleano scritto in questo campo: `/tmp/@count`. Puoi utilizzare questo valore booleano all’interno del modulo. Ulteriori informazioni sul [contesto del modulo](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/developer/schemas-forms/forms#context-of-forms){target="_blank"} (documentazione di Campaign v8).
