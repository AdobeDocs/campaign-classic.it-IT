---
product: campaign
title: Automatizzare tramite flussi di lavoro
description: Scopri come automatizzare la gestione dei contenuti tramite flussi di lavoro
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Workflows
role: User
exl-id: bc6ebf5d-cc21-4750-9713-2bf259e7d6bf
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1197'
ht-degree: 0%

---

# Automatizzare con i flussi di lavoro{#automating-via-workflows}

## Attività di gestione dei contenuti {#content-management-activity}

La creazione, la modifica e la pubblicazione dei contenuti possono essere automatizzate mediante un flusso di lavoro configurato tramite l’interfaccia client di Adobe Campaign.

L&#39;attività **Gestione contenuto** è accessibile tramite la barra degli strumenti **[!UICONTROL Tools]** del diagramma del flusso di lavoro.

Le proprietà delle attività sono suddivise in quattro passaggi:

* **[!UICONTROL Content]** : consente di immettere contenuto esistente o crearne uno,
* **[!UICONTROL Update content]** : consente di modificare l&#39;oggetto del contenuto o di aggiornare il contenuto tramite un flusso di dati XML,
* **[!UICONTROL Action to execute]** : consente di salvare o generare contenuto,
* **[!UICONTROL Transition]** : consente di scegliere se generare o meno una transizione di output e assegnargli un nome.

![](assets/d_ncs_content_wf.png)

### Contenuto {#content}

* **Specificato dalla transizione**

  Il contenuto da utilizzare è stato creato in precedenza. I processi riguarderanno l’istanza di contenuto propagata dall’evento in ingresso. L’identificatore del contenuto è accessibile tramite la variabile &quot;contentId&quot; dell’evento.

* **Esplicito**

  Consente di scegliere il contenuto creato in precedenza.

* **Calcolato da uno script**

  Seleziona un&#39;istanza di contenuto basata su un modello di JavaScript. Il codice da valutare ti consente di recuperare l’identificatore del contenuto.

* **Nuovo, creato tramite un modello di pubblicazione**

  Crea un nuovo contenuto tramite un modello di pubblicazione. L’istanza di contenuto verrà salvata nella cartella &quot;String&quot; compilata.

### Aggiornare il contenuto {#update-the-content}

* **Oggetto**

  Consente di modificare l’oggetto dell’azione di consegna durante la pubblicazione.

* **Accesso ai dati da un feed XML**

  Il contenuto viene aggiornato da un feed XML da un’origine esterna. È necessario immettere un URL per consentire il download dei dati.

  È possibile utilizzare un foglio di stile XSL per trasformare i dati XML in ingresso.

### Azione da eseguire {#action-to-execute}

* **Salva**

  Salva il contenuto creato o modificato. L’identificatore del contenuto salvato viene propagato nella variabile &quot;contentId&quot; dell’evento in uscita.

* **Genera**

  Genera i file di output per ciascun modello di trasformazione con una pubblicazione di tipo &quot;File&quot;. La transizione in uscita viene attivata per ogni file generato, con i seguenti parametri: l’identificatore del contenuto salvato nella variabile &quot;contentId&quot; e il nome del file nella variabile &quot;filename&quot;.

### Transition {#transition}

L&#39;opzione **Genera una transizione di output** consente di aggiungere una transizione di output all&#39;attività **[!UICONTROL Content management]** per collegare una nuova attività all&#39;esecuzione del flusso di lavoro. Dopo aver selezionato questa opzione, immetti un’etichetta per la transizione.

## Esempi {#examples}

### Creazione e distribuzione automatizzate dei contenuti {#automating-content-creation-and-delivery}

L’esempio seguente automatizza la creazione e la distribuzione di un blocco di contenuto.

![](assets/d_ncs_content_workflow2.png)

Il contenuto viene configurato tramite l’attività &quot;Gestione contenuto&quot;:

![](assets/d_ncs_content_workflow3.png)

Una nuova istanza di contenuto viene creata tramite il modello di pubblicazione e la cartella della stringa di contenuto.

Nel nostro esempio, abbiamo sovraccaricato l’oggetto della consegna. Verrà preso in considerazione al posto di quello immesso nel modello **[!UICONTROL Delivery]**.

Il contenuto viene compilato automaticamente da un feed XML proveniente dall’URL inserito:

```
<?xml version='1.0' encoding='ISO-8859-1'?>
<book name="Content automation test" date="2008/06/08" language="eng" computeString="Content automation test">
  <section id="1" name="Introduction">
    <page>Introduction to input forms.</page>
  </section>
</book>
```

Il formato dati non corrisponde allo schema dati immesso nel modello di pubblicazione (**cus:book** nel nostro esempio). L&#39;elemento **`<section>`** deve essere sostituito con l&#39;elemento **`<chapter>`**. È necessario applicare il foglio di stile &quot;cus:book-workflow.xsl&quot; per apportare le modifiche necessarie.

Codice Source del foglio di stile XSLT utilizzato:

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

L’azione finale dell’attività consiste nel salvare l’istanza di contenuto e procedere all’attività successiva.

Il targeting viene eseguito tramite l&#39;attività **Query**.

È stata aggiunta un&#39;attività **AND-join** per assicurarsi che la consegna venga avviata solo una volta completate le query di destinazione e gli aggiornamenti del contenuto.

L&#39;azione di consegna è configurata tramite l&#39;attività **Delivery**:

![](assets/d_ncs_content_workflow4.png)

Viene creata una nuova azione di consegna basata su un modello.

Il modello di consegna dell’attività viene utilizzato per selezionare i modelli di trasformazione del modello di pubblicazione. La generazione del contenuto prenderà in considerazione tutti i modelli di HTML e di testo senza modelli di consegna o quelli a cui si fa riferimento con lo stesso modello dell’attività.

La destinazione da consegnare viene immessa tramite l’evento in ingresso.

Il contenuto della consegna viene popolato tramite l’evento in ingresso.

L’ultimo passaggio per completare l’attività consiste nel preparare e quindi avviare la consegna.

### Creare contenuti per una pubblicazione successiva {#creating-content-and-publishing-it-later}

In questo esempio viene creato un blocco di contenuto e viene avviata la pubblicazione del file dopo un ritardo specifico.

![](assets/d_ncs_content_workflow5.png)

La prima attività di **Gestione contenuto** crea un&#39;istanza di contenuto.

![](assets/d_ncs_content_workflow6.png)

>[!NOTE]
>
>La scheda **[!UICONTROL Publication]** della finestra dei modelli di trasformazione deve essere compilata con la posizione della destinazione da generare.

Viene aggiunta un’attività in attesa per sospendere la transizione successiva per una settimana.

![](assets/d_ncs_content_workflow7.png)

Il contenuto viene immesso manualmente durante questo periodo di tempo.

L’attività successiva avvia la generazione dei contenuti.

![](assets/d_ncs_content_workflow8.png)

Il contenuto da pubblicare viene immesso tramite la transizione in ingresso.

L’azione finale consiste nel generare questo contenuto forzando la directory di pubblicazione.

L&#39;attività **JavaScript Code** recupera il nome completo di ciascun file generato.

![](assets/d_ncs_content_workflow9.png)

### Creare la consegna e il relativo contenuto {#creating-the-delivery-and-its-content}

Questo esempio utilizza lo stesso concetto del primo esempio, ma crea solo l’azione di consegna nel primo passaggio.

![](assets/d_ncs_content_workflow10.png)

La prima attività **Crea consegna** crea l&#39;azione di consegna.

L’attività fork consente di avviare in parallelo il calcolo del target e la creazione dell’istanza di contenuto.

Una volta eseguite le attività, la casella AND-join attiva l&#39;attività **Delivery** per avviare la consegna creata in precedenza per contenuto e targeting.

![](assets/d_ncs_content_workflow11.png)

L’azione di consegna da avviare viene compilata tramite la transizione.

La destinazione da consegnare viene immessa tramite l’evento in ingresso.

Il contenuto della consegna viene popolato tramite l’evento in ingresso.

L’azione finale dell’attività consiste nel preparare e avviare la consegna.

### Importa contenuto da FTP {#importing-content-from-ftp}

Se il contenuto della consegna è disponibile in un file HTML che si trova su server FTP o SFTP, puoi facilmente caricarlo nelle consegne Adobe Campaign. Consulta [questo esempio](../../workflow/using/loading-delivery-content.md).

### Importa contenuto dal connettore Amazon Simple Storage Service (S3) {#importing-content-from-amazon-simple-storage-service--s3--connector}

Se il contenuto della consegna si trova nei bucket Amazon Simple Storage Service (S3), puoi caricarlo facilmente nelle consegne Adobe Campaign. Consulta [questo esempio](../../workflow/using/loading-delivery-content.md).

## Aggiornamento semi-automatico {#semi-automatic-update}

I dati dei contenuti possono essere aggiornati in modalità &quot;semi-automatica&quot;. I dati vengono recuperati da un feed XML tramite un URL.

L’attivazione del recupero dei dati viene eseguita manualmente tramite il modulo di input.

L&#39;obiettivo è quello di dichiarare un campo **editBtn** di tipo **`<input>`** nel modulo. Questo controllo comprende una zona di modifica e un pulsante per avviare l’elaborazione.

L&#39;area di modifica consente di popolare i dati delle variabili utilizzati per creare l&#39;URL del feed XML dei dati da recuperare.

Il pulsante esegue il metodo SOAP **GetAndTransform** popolato sotto il tag **`<input>`**.

La dichiarazione di controllo nella forma è la seguente:

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

Il metodo **GetAndTransform** deve essere dichiarato nell&#39;elemento **`<enter>`** del tag **`<input>`**. Questo tag considera come parametri l’URL di recupero dei dati XML da un’espressione creata in modo dinamico. Il secondo parametro della funzione è facoltativo e fa riferimento a un foglio di stile utilizzato per una trasformazione intermedia quando i dati XML in ingresso non sono nello stesso formato del contenuto.

L’output aggiorna il contenuto in base al percorso immesso nell’ultimo parametro.

**Esempio**: per illustrare questo esempio, partiamo dallo schema &quot;cus:book&quot;.

Viene aggiunto un modulo di input per il controllo di modifica dell&#39;aggiornamento semi-automatico:

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

La zona di modifica consente di immettere il nome del file da recuperare. L’URL è costruito in base a questo nome, ad esempio: https://myserver.adobe.com/incomin/data.xml

Il formato dei dati da recuperare è lo stesso dell’esempio 1 di automazione del flusso di lavoro. Verrà utilizzato il foglio di stile &quot;cus:book-workflow.xsl&quot; visualizzato in questo esempio.

Il risultato dell’esecuzione del processo aggiorna l’istanza del contenuto dal percorso &quot;.&quot;.
