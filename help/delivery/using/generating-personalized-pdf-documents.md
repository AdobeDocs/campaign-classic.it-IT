---
title: Generazione di documenti PDF personalizzati
seo-title: Generazione di documenti PDF personalizzati
description: Generazione di documenti PDF personalizzati
seo-description: null
page-status-flag: never-activated
uuid: d4c27523-bff3-457a-ba60-e2747a2b3166
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 8dfc5e7c-c762-46ba-bbda-a7251354cb47
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 3%

---


# Generazione di documenti PDF personalizzati{#generating-personalized-pdf-documents}

## Informazioni sui documenti PDF variabili {#about-variable-pdf-documents}

 Adobe Campaign consente di generare documenti PDF variabili (per allegati e-mail, consegna diretta tramite posta) da documenti di LibreOffice o Microsoft Word.

Sono supportate le seguenti estensioni: &quot;.docx&quot;, &quot;.doc&quot; e &quot;.odt&quot;.

Per personalizzare i documenti, sono disponibili le stesse funzionalità JavaScript utilizzate per la personalizzazione delle e-mail.

È necessario attivare l’ **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** opzione. Questa opzione è accessibile quando allegate il file all’e-mail di consegna. Per ulteriori informazioni sull&#39;associazione di un file calcolato, vedere la sezione [Allegati file](../../delivery/using/attaching-files.md) .

Esempio di personalizzazione dell&#39;intestazione di una fattura:

![](assets/s_ncs_pdf_simple.png)

Per generare tabelle dinamiche o includere immagini tramite un URL, è necessario seguire un processo specifico.

## Generazione di tabelle dinamiche {#generating-dynamic-tables}

La procedura per la generazione di tabelle dinamiche è la seguente:

* Creare una tabella con tre righe e tutte le colonne necessarie, quindi configurarne il layout (bordi, ecc.).
* Posizionare il cursore sulla tabella e fare clic sul **[!UICONTROL Table > Table properties]** menu. Vai alla **[!UICONTROL Table]** scheda e immetti un nome che inizia con **NlJsTable**.
* Nella prima cella della prima riga, definire un ciclo (&quot;for&quot;, ad esempio) che consenta l&#39;iterazione sui valori che si desidera visualizzare nella tabella.
* In ogni cella della seconda riga della tabella, inserire gli script che restituiscono i valori da visualizzare.
* Chiudere il ciclo nella terza e ultima riga della tabella.

   Esempio di definizione di tabella dinamica:

   ![](assets/s_ncs_pdf_table.png)

## Inserimento di immagini esterne {#inserting-external-images}

L&#39;inserimento di immagini esterne è utile se, ad esempio, desiderate personalizzare un documento con un&#39;immagine il cui URL viene immesso in un campo del destinatario.

A tal fine, devi configurare un blocco di personalizzazione, quindi includere nell’allegato una chiamata al blocco di personalizzazione.

**Esempio: inserimento di un logo personalizzato in base al paese del destinatario**

**Passaggio 1: creare l&#39;allegato:**

* Inserire la chiamata al blocco di personalizzazione: **&lt;%@ include view=&quot;blockname&quot; %>**.
* Inserite il contenuto (personalizzato o meno) nel corpo del file.

![](assets/s_ncs_open_office_blocdeperso.png)

**Passaggio 2: create il blocco di personalizzazione:**

* Dal **[!UICONTROL Resources > Campaign management > Personalization blocks]** menu della console Adobe Campaign .
* Create un nuovo blocco di personalizzazione &quot;My Logo&quot; con &quot;My_Logo&quot; come nome interno.
* Fate clic sul **[!UICONTROL Advanced parameters...]** collegamento, quindi selezionate l&#39; **[!UICONTROL "The content of the block is included in an attachment"]** opzione. Questo consente di copiare la definizione del blocco di personalizzazione direttamente nel contenuto del file OpenOffice.

   ![](assets/s_ncs_pdf_bloc_option.png)

   È necessario distinguere due tipi di dichiarazioni all&#39;interno del blocco di personalizzazione:

   * Il codice Adobe Campaign  dei campi di personalizzazione per i quali i caratteri &quot;open&quot; e &quot;closed&quot; devono essere sostituiti con caratteri escape (rispettivamente `&lt;` e `&gt;`).
   * L&#39;intero codice XML di OpenOffice verrà copiato nel documento OpenOffice.

Nell’esempio, il blocco di personalizzazione si presenta come segue:

```
<% if (recipient.country.label == "Germany") { %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_germany.png />
</draw:frame>
<% } else
if (recipient.country.label == "USA")
{ %>
<draw:frame svg:width="4cm" svg:height="3cm">
<draw:image xlink:href=https://..../logo_USA.png />
</draw:frame>
<% } %>
```

A seconda del paese del destinatario, la personalizzazione è visibile nel documento collegato alla consegna:

![](assets/s_ncs_pdf_result.png)
