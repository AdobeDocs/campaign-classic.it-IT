---
title: Modelli di pubblicazione
seo-title: Modelli di pubblicazione
description: Modelli di pubblicazione
seo-description: null
page-status-flag: never-activated
uuid: 1976f70c-b2d8-44ca-8fc3-6451fb67d18b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 279b0ae6-2578-4f1f-af59-13a1a9c80b32
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ced6c73961e949c421e9dfb638b40a06dcad4614
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---


# Modelli di pubblicazione{#publication-templates}

## Informazioni sui modelli di pubblicazione {#about-publication-templates}

Il modello di pubblicazione è la carta di identità del contenuto da pubblicare. Fa riferimento alle risorse utilizzate nel processo di pubblicazione, ovvero:

* lo schema di dati,
* il modulo di input,
* i modelli di trasformazione per ciascun documento di output.

## Identificazione di un modello di pubblicazione {#identification-of-a-publication-template}

Un modello di pubblicazione è identificato dal nome e dallo spazio dei nomi.

La chiave di identificazione di un foglio di stile è una stringa costituita dallo spazio dei nomi e dal nome separati da due punti; ad esempio: **cus:newsletter**.

>[!NOTE]
>
>In pratica, si consiglia di utilizzare la stessa chiave per lo schema, il modulo e il modello di pubblicazione.

## Creating and configuring the template {#creating-and-configuring-the-template}

I modelli di pubblicazione sono memorizzati per impostazione predefinita nel **[!UICONTROL Administration > Configuration > Publication templates]** nodo. Per creare un nuovo modello, fate clic sul **[!UICONTROL New]** pulsante sopra l’elenco dei modelli.

Per configurare il modello di pubblicazione, compilare il nome del modello (ovvero la chiave di identificazione costituita dal nome e dallo spazio dei nomi), la relativa etichetta, lo schema di dati e il modulo di input a cui è collegato.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>L&#39;etichetta viene visualizzata ogni volta che viene creato il contenuto in base a questo modello di pubblicazione.

L&#39;opzione **Controlla stato per convalidare la generazione** di contenuto forza un controllo sullo stato &quot;Convalida&quot; delle istanze di contenuto per autorizzare la generazione di file. For more on this, refer to [Publication](#publication).

È necessario aggiungere un modello di trasformazione per ciascun documento di output. Potete creare tutti i modelli di trasformazione necessari.

Il **[!UICONTROL Name of template]** campo è un&#39;etichetta libera che descrive il tipo di rendering nell&#39;output. Per ciascun modello di trasformazione, le impostazioni di pubblicazione sono disponibili nelle schede.

### Rendering {#rendering}

Nella **[!UICONTROL Rendering]** scheda, scegliete:

* il tipo di rendering utilizzato per proiettare il documento di output: foglio di stile XSL o modello JavaScript,
* il formato del documento di output: HTML, testo, XML o RTF,
* il modello che contiene i dati di costruzione, ad esempio il foglio di stile o il modello JavaScript da utilizzare.

### Pubblicazione {#publication}

La pubblicazione comporta la generazione del documento di output sotto forma di file, se il tipo selezionato è **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

Sono disponibili le seguenti opzioni di pubblicazione:

* Il set di caratteri di codifica del file di output può essere forzato tramite il **[!UICONTROL Encoding]** campo. Per impostazione predefinita viene utilizzato il set di caratteri Latin 1 (1252).
* L&#39; **[!UICONTROL Multi-file generation]** opzione attiva una modalità speciale di pubblicazione del documento. Questa opzione consiste nella compilazione di un tag di partizionamento all&#39;inizio di ogni pagina del documento di output. La generazione del contenuto genererà un file per ciascun tag di partizionamento popolato. Questa modalità viene utilizzata per generare mini-siti da un blocco di contenuto. for more on this, refer to [Multi-file generation](#multi-file-generation).
* Il **[!UICONTROL Location]** campo contiene il nome del file di output. Il nome può essere composto da variabili per generare un nome di file automatico.

   Una variabile viene compilata con il formato seguente: **`$(<xpath>)`**, dove **`<xpath>`** è il percorso di un campo dello schema dati del modello di pubblicazione.

   Il nome di un file può essere costituito da un campo di tipo data. Per formattare correttamente questo campo, utilizzare la funzione **$date-format** , utilizzando come parametri il percorso del campo e il formato di output.

   Per impostazione predefinita, il formato di costruzione del nome del file utilizza le variabili nei campi &quot;@name&quot; e &quot;@date&quot;:

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   Il nome del file generato sarà simile al seguente: ct_news12_20110901.htm.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla generazione di contenuto, consultate [Creazione di un&#39;istanza](../../delivery/using/using-a-content-template.md#creating-a-content-instance)di contenuto.

### Consegna {#delivery}

Questa scheda consente di selezionare uno scenario per avviare una distribuzione direttamente sul contenuto. Il contenuto del messaggio e-mail verrà popolato automaticamente in base al formato di output (HTML o Testo).

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>Per un esempio di creazione della distribuzione basata su un contenuto, vedere [Distribuzione di un&#39;istanza](../../delivery/using/using-a-content-template.md#delivering-a-content-instance)di contenuto.

### Aggregator {#aggregator}

L&#39;aggregazione dei dati da un elenco di script o query consente di arricchire il documento XML con i dati del contenuto. L&#39;obiettivo è quello di completare alcune informazioni cui fanno riferimento i collegamenti o di aggiungere elementi dal database.

### Generazione di più file {#multi-file-generation}

Per attivare la generazione di più file, selezionare l&#39; **[!UICONTROL Multi-file generation]** opzione nel modello di pubblicazione. Questa opzione consente di specificare i tag di partizionamento nel foglio di stile per l&#39;inizio di ogni pagina del documento di output. La generazione del contenuto produrrà un file per ciascun tag di partizionamento rilevato.

Il tag di partizionamento da integrare nel foglio di stile è il seguente:

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** dove **`<name_of_file>`** è il nome del file della pagina da generare.

**Esempio:** Generazione multipla di file utilizzando lo schema &quot;cus:book&quot;.

Il principio consiste nel generare una pagina principale in cui siano elencati i capitoli, con la possibilità di visualizzare i dettagli del capitolo in una pagina esterna.

![](assets/d_ncs_content_chunk.png)

Il foglio di stile corrispondente (&quot;cus:book.xsl&quot;) è il seguente:

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <lu>
          <xsl:for-each select="chapter">
            <li><a target="_blank" href="chapter{@id}.htm"><xsl:value-of select="@name"/></a></li>  
          </xsl:for-each>
       </lu>
      </body>
    </html>
   </xsl:template>
</xsl:stylesheet>
```

Per generare i dettagli dei capitoli è necessario un secondo foglio di stile (&quot;cus:Chapter.xsl&quot;):

```
<?xml version="1.0" encoding="ISO-8859-1" ?>
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
  <xsl:output encoding="ISO-8859-1" method="html"/>

  <!-- Detail of a chapter -->
  <xsl:template match="chapter">
    <!-- Cut tag -->   
    <xsl:comment> #nl:output_replace($(path)/chapter<xsl:value-of select="@id"/>.htm)</xsl:comment>
    
    <html>
      <body>
        <h1><xsl:value-of select="@name"/></h1>
        <xsl:value-of select="page" disable-output-escaping="yes"/>
      </body>
    </html>
  </xsl:template>

  <!-- Style sheet entry point -->
  <xsl:template match="/book">
    <xsl:apply-templates/>
   </xsl:template>
</xsl:stylesheet>
```

Il tag di partizionamento viene popolato all’inizio della pagina da includere nel file da generare.

```
<xsl:comment> #nl:output_replace($(path)/<xsl:value-of select="@id"/>.htm)</xsl:comment>
```

Il nome del file è costruito con la variabile **$(percorso)** contenente il percorso di pubblicazione e **`<xsl:value-of select="@id" />`**, che corrisponde all&#39;identificatore del capitolo nel documento di input.

Il modello di pubblicazione deve essere compilato con i due fogli di stile &quot;cus:book.xsl&quot; e &quot;cus:Chapter.xsl&quot;.

L&#39; **[!UICONTROL Multi-file generation]** opzione deve essere attiva nel modello di trasformazione del capitolo:

![](assets/d_ncs_content_chunk2.png)

Il **[!UICONTROL Location]** campo non viene utilizzato nella generazione di più file, ma è comunque necessario compilare il campo per evitare un errore durante la pubblicazione.
