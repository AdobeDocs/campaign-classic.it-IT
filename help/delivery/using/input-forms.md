---
solution: Campaign Classic
product: campaign
title: Moduli di input
description: Moduli di input
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 2%

---


# Moduli di input{#input-forms}

Di seguito sono riportati alcuni principi generali relativi all&#39;uso dei moduli di input in  Adobe Campaign.

Forms è descritto in [questa sezione](../../configuration/using/identifying-a-form.md).

## Struttura di un modulo {#form-structure}

Il documento XML di un modulo di input deve contenere gli attributi **`<form>`** root con gli attributi **name** e **namespace** rispettivamente per compilare il nome del modulo e il relativo spazio dei nomi.

```
<form name="form_name" namespace="name_space">
...
</form>
```

Per impostazione predefinita, un modulo è associato allo schema dati con lo stesso nome e lo stesso spazio nomi. Per associare un modulo con un nome diverso, immettere la chiave dello schema nell&#39;attributo **entity-schema** dell&#39;elemento **`<form>`**.

Per illustrare la struttura di un modulo di input, viene descritta un&#39;interfaccia basata sullo schema di esempio &quot;cus:book&quot;:

![](assets/d_ncs_content_form1.png)

Questo è il modulo di input corrispondente:

```
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

La descrizione degli elementi di modifica inizia con l&#39;elemento **`<form>`** principale.

Un controllo di modifica viene immesso in un elemento **`<input>`** con l&#39;attributo **xpath** contenente il percorso del campo nello schema.

**Promemoria relativa alla sintassi XPath:**

Il linguaggio XPath viene utilizzato in  Adobe Campaign per fare riferimento a un elemento o attributo appartenente a uno schema di dati.

XPath è una sintassi che consente di individuare un nodo nella struttura di un documento XML.

Gli elementi sono indicati dal nome e gli attributi sono designati dal nome preceduto dal carattere &quot;@&quot;.

Esempi:

* **@date**: seleziona l&#39;attributo con il nome &quot;date&quot;
* **capitolo/@title**: seleziona l&#39;attributo &quot;title&quot; sotto l&#39; `<chapter>` elemento
* **../@date**: seleziona la data dall&#39;elemento padre dell&#39;elemento corrente

Il controllo edit si adatta automaticamente al tipo di dati corrispondente e utilizza l&#39;etichetta definita nello schema.

Per impostazione predefinita, ogni campo viene visualizzato su una sola riga e occupa tutto lo spazio disponibile, a seconda del tipo di dati.

>[!CAUTION]
>
>Il modulo di input deve fare riferimento a un attributo **type=&quot;contentForm&quot;** sull&#39;elemento **`<form>`** per aggiungere automaticamente il frame necessario per l&#39;immissione del contenuto.

## Formattazione {#formatting}

La disposizione dei controlli è simile a quella utilizzata nelle tabelle HTML, con la possibilità di dividere un controllo in più colonne, di elementi di interlacciamento o di specificare l&#39;occupazione dello spazio disponibile. Tenere presente, tuttavia, che la formattazione autorizza solo la distribuzione delle proporzioni; non è possibile specificare dimensioni fisse per un oggetto.

Per ulteriori informazioni al riguardo, consulta [questa sezione](../../configuration/using/form-structure.md#formatting).

## Controlli del tipo di elenco {#list-type-controls}

Per modificare un elemento raccolta, è necessario utilizzare un controllo tipo elenco.

### Elenco colonne {#column-list}

Questo controllo visualizza un elenco di colonne modificabili con una barra degli strumenti contenente i pulsanti Aggiungi ed Elimina.

![](assets/d_ncs_content_form4.png)

```
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

Il controllo elenco deve essere compilato con l&#39;attributo **type=&quot;list&quot;** e il percorso dell&#39;elenco deve fare riferimento all&#39;elemento della raccolta.

Le colonne sono dichiarate dagli elementi secondari **`<input>`** dell&#39;elenco.

>[!NOTE]
>
>Le frecce di ordinamento verso l&#39;alto e il basso vengono aggiunte automaticamente quando l&#39;attributo **ordered=&quot;true&quot;** viene completato per l&#39;elemento di raccolta nello schema di dati.

Per impostazione predefinita, i pulsanti della barra degli strumenti sono allineati verticalmente. Possono anche essere allineati orizzontalmente:

![](assets/d_ncs_content_form5.png)

```
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

L&#39;attributo **toolbarCaption** forza l&#39;allineamento orizzontale della barra degli strumenti e compila il titolo sopra l&#39;elenco.

>[!NOTE]
>
>Per evitare che l&#39;etichetta dell&#39;elemento di raccolta venga visualizzata a sinistra del controllo, aggiungere l&#39;attributo **nolabel=&quot;true&quot;**.

#### Zoom in un elenco {#zoom-in-a-list}

L&#39;inserimento e la modifica dei dati dell&#39;elenco possono essere eseguiti in un modulo di modifica separato.

I moduli di modifica negli elenchi vengono utilizzati nei casi seguenti:

* Per semplificare l&#39;immissione delle informazioni,
* Presenza di un controllo a più linee,
* Le colonne nell&#39;elenco contengono solo i campi principali e il modulo visualizza tutti i campi dell&#39;elemento raccolta.

![](assets/d_ncs_content_form7.png)

```
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter" zoom="true" zoomOnAdd="true">
  <input xpath="@name"/>
  <input xpath="@number"/>

  <form colcount="2" label="Editing a chapter">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </form>
</input>
```

La definizione del modulo di modifica viene specificata tramite l&#39;elemento **`<form>`** sotto l&#39;elemento elenco. La sua struttura è identica alla struttura di un modulo di input.

Un pulsante **[!UICONTROL Detail]** viene aggiunto automaticamente quando l&#39;attributo **zoom=&quot;true&quot;** viene immesso nella definizione dell&#39;elenco. Questo consente di aprire il modulo di modifica sulla riga selezionata.

>[!NOTE]
>
>Se si aggiunge l&#39;attributo **zoomOnAdd=&quot;true&quot;**, il modulo di modifica viene chiamato all&#39;inserimento di un elemento dell&#39;elenco.

### Elenco tabulazioni {#tab-list}

Questo elenco presenta la modifica degli elementi della raccolta sotto forma di schede.

![](assets/d_ncs_content_form6.png)

```
<container toolbarCaption="List of chapters" type="notebooklist" xpath="chapter" xpath-label="@name">
  <container colcount="2">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </container>
</container>
```

Il controllo elenco deve essere compilato con l&#39;attributo **type=&quot;blocco appunti&quot;** e il percorso dell&#39;elenco deve fare riferimento all&#39;elemento della raccolta.

Il titolo della scheda contiene il valore dei dati immessi tramite l&#39;attributo **xpath-label**.

I controlli di modifica devono essere dichiarati sotto un elemento **`<container>`** secondario del controllo elenco.

Utilizzare i pulsanti della barra degli strumenti per aggiungere o eliminare elementi dell&#39;elenco.

>[!NOTE]
>
>Le frecce di ordinamento a sinistra e a destra vengono aggiunte automaticamente quando l&#39;attributo **ordered=&quot;true&quot;** viene popolato per l&#39;elemento di raccolta nello schema dati.

## Contenitori {#containers}

I contenitori consentono di raggruppare un set di controlli. Esistono tramite l&#39;elemento **`<container>`**. Sono già stati utilizzati per formattare i controlli in più colonne e per controllare l&#39;elenco delle schede.

Per ulteriori informazioni sui contenitori e su come utilizzarli nei moduli di input, consultare [questa sezione](../../configuration/using/form-structure.md#containers).

## Modifica dei moduli {#editing-forms}

La zona di modifica consente di inserire il contenuto XML del modulo di input:

![](assets/d_ncs_content_form12.png)

La scheda **[!UICONTROL Preview]** consente di visualizzare il modulo di input:

![](assets/d_ncs_content_form13.png)
