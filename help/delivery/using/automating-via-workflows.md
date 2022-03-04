---
product: campaign
title: Automatizzare tramite flussi di lavoro
description: Scopri come automatizzare la gestione dei contenuti tramite flussi di lavoro
feature: Workflows
exl-id: bc6ebf5d-cc21-4750-9713-2bf259e7d6bf
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '1190'
ht-degree: 0%

---

# Automatizzare con i flussi di lavoro{#automating-via-workflows}

![](../../assets/common.svg)

## Attività di gestione dei contenuti {#content-management-activity}

La creazione, la modifica e la pubblicazione dei contenuti possono essere automatizzate mediante un flusso di lavoro configurato tramite l’interfaccia client di Adobe Campaign.

La **Gestione dei contenuti** l’attività è accessibile tramite **[!UICONTROL Tools]** della barra degli strumenti del diagramma del flusso di lavoro.

Le proprietà dell’attività sono suddivise in quattro passaggi:

* **[!UICONTROL Content]** : consente di immettere contenuto esistente o crearne uno,
* **[!UICONTROL Update content]** : consente di modificare l’oggetto del contenuto o di aggiornarlo tramite un flusso di dati XML,
* **[!UICONTROL Action to execute]** : consente di salvare o generare contenuti,
* **[!UICONTROL Transition]** : consente di scegliere se generare o meno una transizione di output e di assegnargli un nome.

![](assets/d_ncs_content_wf.png)

### Contenuto {#content}

* **Specificato dalla transizione**

   Il contenuto da utilizzare è stato creato in precedenza. I processi riguardano l’istanza di contenuto propagata dall’evento in arrivo. L’identificatore del contenuto è accessibile tramite la variabile &quot;contentId&quot; dell’evento.

* **Esplicito**

   Consente di scegliere il contenuto creato in precedenza.

* **Calcolato da uno script**

   Seleziona un’istanza di contenuto basata su un modello JavaScript. Il codice da valutare consente di recuperare l’identificatore del contenuto.

* **Nuovo, creato tramite un modello di pubblicazione**

   Crea un nuovo contenuto tramite un modello di pubblicazione. L’istanza di contenuto verrà salvata nella cartella &quot;String&quot; popolata.

### Aggiornare il contenuto {#update-the-content}

* **Oggetto**

   Consente di modificare l’oggetto dell’azione di consegna durante la pubblicazione.

* **Accesso ai dati da un feed XML**

   Il contenuto viene aggiornato da un feed XML da un’origine esterna. Affinché si verifichi il download dei dati, è necessario inserire un URL.

   È possibile utilizzare un foglio di stile XSL per trasformare i dati XML in arrivo.

### Azione da eseguire {#action-to-execute}

* **Salva**

   Salva il contenuto creato o modificato. L’identificatore del contenuto salvato viene propagato nella variabile &quot;contentId&quot; dell’evento in uscita.

* **Genera**

   Genera i file di output per ciascuno dei modelli di trasformazione con una pubblicazione di tipo &quot;File&quot;. La transizione in uscita viene attivata per ogni file generato, con i seguenti parametri: l’identificatore del contenuto salvato nella variabile &quot;contentId&quot; e il nome del file nella variabile &quot;filename&quot;.

### Transition {#transition}

La **Generare una transizione di output** consente di aggiungere una transizione di output al **[!UICONTROL Content management]** per collegare una nuova attività all’esecuzione di un flusso di lavoro. Dopo aver selezionato questa opzione, immetti un’etichetta per la transizione.

## Esempi {#examples}

### Creazione e distribuzione automatizzate dei contenuti {#automating-content-creation-and-delivery}

L’esempio seguente automatizza la creazione e la consegna di un blocco di contenuto.

![](assets/d_ncs_content_workflow2.png)

Il contenuto viene configurato tramite l’attività &quot;Gestione dei contenuti&quot;:

![](assets/d_ncs_content_workflow3.png)

Una nuova istanza di contenuto viene creata tramite il modello di pubblicazione e la cartella della stringa di contenuto.

Nel nostro esempio, abbiamo sovraccaricato il soggetto della consegna. Sarà preso in considerazione invece di quello inserito nel **[!UICONTROL Delivery]** modello.

Il contenuto viene compilato automaticamente da un feed XML proveniente dall’URL inserito:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

Il formato dei dati non corrisponde allo schema dei dati inserito nel modello di pubblicazione (**cus:book** nel nostro esempio); la **`<section>`** deve essere sostituito con **`<chapter>`** elemento. È necessario applicare il foglio di stile &quot;cus:book-workflow.xsl&quot; per apportare le modifiche necessarie.

Codice di origine del foglio di stile XSLT utilizzato:

```
<?xml version="1.0" encoding="utf-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
 <xsl:output indent="yes" method="xml"  encoding="ISO-8859-1"/>

 <xsl:template match="text()|@*"/>

  <xsl:template match="*">
    <xsl:variable name="element.name" select="name(.)"/>
    <xsl:element name="{$element.name}">
      <xsl:copy-of select="text()|@*"/>
      <xsl:apply-templates/>
    </xsl:element>
  </xsl:template>

  <xsl:template match="book">
  <book name="test">
     <xsl:apply-templates/>
    <book>
 </xsl:template>

  <xsl:template match="section">
    <chapter>
      <xsl:for-each select="@*">
        <xsl:copy-of select="."/>
      </xsl:for-each>
       <xsl:apply-templates/>
    </chapter>
  </xsl:template>
  
</xsl:stylesheet>
```

L’azione finale dell’attività consiste nel salvare l’istanza di contenuto e passare all’attività successiva.

Il targeting viene eseguito tramite il **Query** attività.

Un **AND-join** è stata aggiunta l’attività per assicurarsi che la consegna venga avviata solo una volta completata la query di destinazione e gli aggiornamenti dei contenuti.

L’azione di consegna è configurata tramite la **Consegna** attività:

![](assets/d_ncs_content_workflow4.png)

Viene creata una nuova azione di consegna basata su un modello.

Il modello di consegna dell’attività viene utilizzato per selezionare i modelli di trasformazione del modello di pubblicazione. La generazione di contenuti terrà conto di tutti i modelli di testo e HTML senza modelli di consegna o di quelli a cui viene fatto riferimento con lo stesso modello dell’attività.

Il target da consegnare viene immesso tramite l’evento in arrivo.

Il contenuto della consegna viene popolato tramite l’evento in entrata.

L’ultimo passaggio per completare l’attività consiste nel preparare e quindi avviare la consegna.

### Creare contenuti per una pubblicazione successiva {#creating-content-and-publishing-it-later}

In questo esempio viene creato un blocco di contenuto e viene avviata la pubblicazione del file dopo un ritardo specifico.

![](assets/d_ncs_content_workflow5.png)

Il primo **Gestione dei contenuti** crea un’istanza di contenuto.

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>La **[!UICONTROL Publication]** La scheda della finestra modelli di trasformazione deve essere compilata con la posizione della destinazione da generare.

Viene aggiunta un’attività di attesa per mettere in pausa la transizione successiva per una settimana.

![](assets/d_ncs_content_workflow7.png)

Il contenuto viene immesso manualmente durante questo periodo di tempo.

L’attività successiva avvia la generazione di contenuto.

![](assets/d_ncs_content_workflow8.png)

Il contenuto da pubblicare viene immesso tramite la transizione in entrata.

L’azione finale consiste nel generare questo contenuto forzando la directory di pubblicazione.

La **Codice JavaScript** l’attività recupera il nome completo di ciascun file generato.

![](assets/d_ncs_content_workflow9.png)

### Creare la consegna e il relativo contenuto {#creating-the-delivery-and-its-content}

In questo esempio viene utilizzato lo stesso concetto del primo esempio, ma viene creata solo l’azione di consegna nel primo passaggio.

![](assets/d_ncs_content_workflow10.png)

Il primo **Creare una consegna** crea l&#39;azione di consegna.

L’attività fork ti consente di avviare il calcolo del target e la creazione dell’istanza di contenuto in parallelo.

Una volta eseguite le attività, la casella AND-join attiva la **Consegna** per avviare la consegna creata in precedenza su contenuto e targeting.

![](assets/d_ncs_content_workflow11.png)

L’azione di consegna da avviare viene compilata tramite la transizione .

Il target da consegnare viene immesso tramite l’evento in arrivo.

Il contenuto della consegna viene popolato tramite l’evento in entrata.

L’azione finale dell’attività consiste nel preparare e avviare la consegna.

### Importare contenuti da FTP {#importing-content-from-ftp}

Se il contenuto di consegna è disponibile in un file HTML presente su server FTP o SFTP, puoi facilmente caricarlo nelle consegne Adobe Campaign. Fai riferimento a [questo esempio](../../workflow/using/loading-delivery-content.md).

### Importare contenuti dal connettore Amazon Simple Storage Service (S3) {#importing-content-from-amazon-simple-storage-service--s3--connector}

Se il contenuto di consegna si trova su bucket Amazon Simple Storage Service (S3), puoi facilmente caricare tale contenuto nelle consegne Adobe Campaign. Fai riferimento a [questo esempio](../../workflow/using/loading-delivery-content.md).

## Aggiornamento semiautomatico {#semi-automatic-update}

I dati del contenuto possono essere aggiornati in modalità &quot;semi-automatica&quot;. I dati vengono recuperati da un feed XML tramite un URL.

L’attivazione del recupero dei dati viene eseguita manualmente tramite il modulo di input.

L&#39;obiettivo è quello di dichiarare un **editBtn** type **`<input>`** nel modulo. Questo controllo comprende un’area di modifica e un pulsante per avviare l’elaborazione.

La zona di modifica ti consente di compilare i dati delle variabili utilizzati per creare l’URL del feed XML dei dati da recuperare.

Il pulsante esegue il **GetAndTransform** Metodo SOAP popolato in **`<input>`** tag .

La dichiarazione di controllo nel modulo è la seguente:

```
<input type="editbtn" xpath="<path>">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="<url>" type="string"/>
      <param exprIn="'xtk:xslt|<style sheet>'" type="string"/>
      <param type="DOMElement" xpathOut="<output path>"/>
    </soapCall>
  </enter>
</input>
```

La **GetAndTransform** deve essere dichiarato **`<enter>`** elemento **`<input>`** tag . Questo tag prende come parametri l&#39;URL di recupero dei dati XML da un&#39;espressione costruita dinamicamente. Il secondo parametro della funzione è facoltativo e fa riferimento a un foglio di stile utilizzato per una trasformazione intermedia quando i dati XML in arrivo non sono nello stesso formato del contenuto.

L’output aggiorna il contenuto in base al percorso immesso nell’ultimo parametro.

**Esempio**: Per illustrare questo esempio, partiamo dallo schema &quot;cus:book&quot;.

È stato aggiunto un modulo di input per il controllo dell’aggiornamento semiautomatico:

![](assets/d_ncs_content_exemple9.png)

```
<input label="File name" type="editbtn" xpath="/tmp/@name">
  <enter>
    <soapCall name="GetAndTransform" service="ncm:content">
      <param exprIn="'https://myserver.adobe.com/incoming/' + [/tmp/@name] + '.xml'" type="string"/>
      <param exprIn="'xtk:xslt|cus:book-workflow.xsl'" type="string"/>
      <param type="DOMElement" xpathOut="."/>
    </soapCall>
  </enter>
</input>
```

La zona di modifica consente di immettere il nome del file da recuperare. L’URL viene creato in base a questo nome, ad esempio: https://myserver.adobe.com/incomin/data.xml

Il formato dei dati da recuperare è lo stesso dell’esempio 1 dell’automazione del flusso di lavoro. Useremo il foglio di stile &quot;cus:book-workflow.xsl&quot; visualizzato in questo esempio.

Il risultato dell&#39;esecuzione del processo aggiorna l&#39;istanza di contenuto dal percorso &#39;.&#39;.
