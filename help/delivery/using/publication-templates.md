---
product: campaign
title: Modelli di pubblicazione
description: Modelli di pubblicazione
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Templates
exl-id: 3b6e4974-4551-4da2-8eca-577c4f9cbd91
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 1%

---

# Modelli di pubblicazione{#publication-templates}



## Informazioni sui modelli di pubblicazione {#about-publication-templates}

Il modello di pubblicazione è la carta di identità del contenuto da pubblicare. Fa riferimento alle risorse utilizzate nel processo di pubblicazione, ovvero:

* lo schema dei dati,
* il modulo di input,
* i modelli di trasformazione per ciascun documento di output.

## Identificazione di un modello di pubblicazione {#identification-of-a-publication-template}

Un modello di pubblicazione è identificato dal nome e dallo spazio dei nomi.

La chiave di identificazione di un foglio di stile è una stringa costituita dallo spazio dei nomi e dal nome separati da due punti; ad esempio: **cus:newsletter**.

>[!NOTE]
>
>In pratica, si consiglia di utilizzare la stessa chiave per lo schema, il modulo e il modello di pubblicazione.

## Creare e configurare il modello {#creating-and-configuring-the-template}

I modelli di pubblicazione sono memorizzati per impostazione predefinita in **[!UICONTROL Administration > Configuration > Publication templates]** nodo. Per creare un nuovo modello, fai clic sul pulsante **[!UICONTROL New]** , sopra l’elenco dei modelli.

Per configurare il modello di pubblicazione, compilare il nome del modello (ovvero la chiave di identificazione costituita dal nome e dallo spazio dei nomi), l’etichetta, lo schema dei dati e il modulo di input a cui è collegato.

![](assets/d_ncs_content_model.png)

>[!NOTE]
>
>L’etichetta viene visualizzata ogni volta che il contenuto viene creato in base a questo modello di pubblicazione.

La **Controllare lo stato per convalidare la generazione di contenuto** forza un controllo sullo stato &quot;Convalidato&quot; delle istanze di contenuto per autorizzare la generazione di file. Per ulteriori informazioni, consulta [Pubblicazione](#publication).

È necessario aggiungere un modello di trasformazione per ciascun documento di output. Puoi creare tutti i modelli di trasformazione necessari.

La **[!UICONTROL Name of template]** field è un’etichetta gratuita che descrive il tipo di rendering nell’output. Per ogni modello di trasformazione, le impostazioni di pubblicazione sono disponibili nelle schede .

### Rendering {#rendering}

La **[!UICONTROL Rendering]** scheda , scegli:

* tipo di rendering utilizzato per la proiezione del documento di output: modello di foglio di stile XSL o JavaScript,
* il formato del documento di output: HTML, testo, XML o RTF,
* il modello che contiene i dati di costruzione, ovvero il modello foglio di stile o JavaScript da utilizzare.

### Pubblicazione {#publication}

La pubblicazione comporta la generazione del documento di output sotto forma di file, se il tipo selezionato è **[!UICONTROL File]**.

![](assets/d_ncs_content_model2.png)

Sono disponibili le seguenti opzioni di pubblicazione:

* Il set di caratteri di codifica del file di output può essere forzato tramite il **[!UICONTROL Encoding]** campo . Per impostazione predefinita viene utilizzato il set di caratteri Latin 1 (1252).
* La **[!UICONTROL Multi-file generation]** attiva una modalità speciale di pubblicazione del documento. Questa opzione consiste nel popolare un tag di partizionamento all&#39;inizio di ogni pagina del documento di output. La generazione del contenuto genera un file per ciascun tag di partizionamento popolato. Questa modalità viene utilizzata per generare mini-siti da un blocco di contenuto. per ulteriori informazioni, consulta [Generazione di più file](#multi-file-generation).
* La **[!UICONTROL Location]** contiene il nome del file di output. Il nome può essere composto da variabili per generare un nome di file automatico.

   Una variabile viene compilata con il seguente formato: **`$(<xpath>)`**, dove **`<xpath>`** è il percorso di un campo dello schema dati del modello di pubblicazione.

   Il nome di un file può essere costituito da un campo di tipo data. Per formattare correttamente questo campo, utilizza il **Formato $date** utilizzando come parametri il percorso del campo e il formato di output.

   Per impostazione predefinita, il formato di costruzione del nome del file utilizza le variabili nei campi &quot;@name&quot; e &quot;@date&quot;:

   ```
   ct_$(@name)_$date-format(@date,'%4Y%2M%2D').htm
   ```

   Il nome del file generato sarà simile al seguente: ct_news12_20110901.htm.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla generazione dei contenuti, consulta [Creare un’istanza di contenuto](using-a-content-template.md#creating-a-content-instance).

### Consegna {#delivery}

Questa scheda ti consente di selezionare uno scenario per avviare una consegna direttamente sul contenuto. Il contenuto dell’e-mail verrà compilato automaticamente in base al formato di output (HTML o Testo).

![](assets/d_ncs_content_model3.png)

>[!NOTE]
>
>Ad esempio, per creare una consegna basata su un contenuto, consulta [Fornire un’istanza di contenuto](using-a-content-template.md#delivering-a-content-instance).

### Aggregatore {#aggregator}

L&#39;aggregazione dei dati da uno script o da un elenco di query consente di arricchire il documento XML con i dati del contenuto. L&#39;obiettivo è quello di integrare alcune informazioni a cui fanno riferimento i collegamenti o di aggiungere elementi dal database.

### Generazione di più file {#multi-file-generation}

Per attivare la generazione di più file, seleziona la **[!UICONTROL Multi-file generation]** nel modello di pubblicazione. Questa opzione consente di specificare i tag di partizionamento nel foglio di stile per l&#39;inizio di ogni pagina del documento di output. La generazione del contenuto produrrà un file per ogni tag di partizionamento rilevato.

Il tag di partizionamento da integrare nel foglio di stile è il seguente:

**`<xsl:comment> #nl:output_replace(<name_of_file>) </xsl:comment>`** dove **`<name_of_file>`** è il nome file della pagina da generare.

**Esempio:** Generazione multipla di file utilizzando lo schema &quot;cus:book&quot;.

Il principio consiste nel generare una pagina principale in cui sono elencati i capitoli, con la possibilità di visualizzare i dettagli del capitolo in una pagina esterna.

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

È necessario un secondo foglio di stile (&quot;cus:capitolo.xsl&quot;) per generare i dettagli dei capitoli:

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

Il nome del file viene costruito con il **$(path)** contenente il percorso della pubblicazione e **`<xsl:value-of select="@id" />`**, che corrisponde all’identificatore del capitolo nel documento di input.

Il modello di pubblicazione deve essere compilato con i due fogli di stile &quot;cus:book.xsl&quot; e &quot;cus:capitolo.xsl&quot;.

La **[!UICONTROL Multi-file generation]** l&#39;opzione deve essere attiva sul modello di trasformazione del capitolo:

![](assets/d_ncs_content_chunk2.png)

La **[!UICONTROL Location]** campo non utilizzato nella generazione di più file, ma devi comunque compilare il campo per evitare un errore durante la pubblicazione.
