---
product: campaign
title: Generare documenti PDF personalizzati
description: Scopri come generare documenti PDF personalizzati
feature: Personalization
exl-id: e5239d99-256b-412b-be20-f64f822da9c3
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---

# Generare documenti PDF personalizzati{#generating-personalized-pdf-documents}

![](../../assets/common.svg)

## Informazioni sui documenti variabili di PDF {#about-variable-pdf-documents}

Adobe Campaign consente di generare documenti PDF variabili per gli allegati e-mail da documenti LibreOffice o Microsoft Word.

Sono supportate le seguenti estensioni: &quot;.docx&quot;, &quot;.doc&quot; e &quot;.odt&quot;.

Per personalizzare i documenti, sono disponibili le stesse funzionalità JavaScript utilizzate per la personalizzazione delle e-mail.

È necessario attivare la **[!UICONTROL "The content of the file is personalized and converted to PDF during the delivery of each message"]** opzione . Questa opzione è accessibile quando alleghi il file all’e-mail di consegna. Per ulteriori informazioni sull’associazione di un file calcolato, consulta la [Allega file](attaching-files.md) sezione .

Esempio di personalizzazione dell&#39;intestazione di una fattura:

![](assets/s_ncs_pdf_simple.png)

Per generare tabelle dinamiche o includere immagini tramite un URL, è necessario seguire un processo specifico.

## Genera tabelle dinamiche {#generating-dynamic-tables}

La procedura per la generazione di tabelle dinamiche è la seguente:

* Crea una tabella con tre righe e tutte le colonne necessarie, quindi configurane il layout (bordi, ecc.).
* Posiziona il cursore sulla tabella e fai clic sul pulsante **[!UICONTROL Table > Table properties]** menu. Vai a **[!UICONTROL Table]** e immetti un nome che inizia con **NlJsTable**.
* Nella prima cella della prima riga, definire un ciclo (&quot;for&quot;, ad esempio) che abilita l’iterazione sui valori che si desidera visualizzare nella tabella.
* In ogni cella della seconda riga della tabella, inserire gli script che restituiscono i valori da visualizzare.
* Chiudere il loop nella terza e ultima riga della tabella.

   Esempio di definizione di una tabella dinamica:

   ![](assets/s_ncs_pdf_table.png)

## Inserire immagini esterne {#inserting-external-images}

L’inserimento di immagini esterne è utile se, ad esempio, desideri personalizzare un documento con un’immagine il cui URL è inserito in un campo del destinatario.

A questo scopo, devi configurare un blocco di personalizzazione, quindi includere una chiamata al blocco di personalizzazione nell’allegato.

**Esempio: inserire un logo personalizzato in base al paese del destinatario**

**Passaggio 1: creare l&#39;allegato:**

* Inserisci la chiamata al blocco di personalizzazione: **&lt;%@ include view=&quot;blockname&quot; %>**.
* Inserisci il contenuto (personalizzato o meno) nel corpo del file.

![](assets/s_ncs_open_office_blocdeperso.png)

**Passaggio 2: crea il blocco di personalizzazione:**

* Vai a **[!UICONTROL Resources > Campaign management > Personalization blocks]** del menu della console Adobe Campaign.
* Crea un nuovo blocco di personalizzazione &quot;My Logo&quot; con &quot;My_Logo&quot; come nome interno.
* Fai clic sul pulsante **[!UICONTROL Advanced parameters...]** quindi controlla il **[!UICONTROL "The content of the block is included in an attachment"]** opzione . Questo consente di copiare la definizione del blocco di personalizzazione direttamente nel contenuto del file OpenOffice.

   ![](assets/s_ncs_pdf_bloc_option.png)

   È necessario differenziare due tipi di dichiarazioni all’interno del blocco di personalizzazione:

   * Il codice Adobe Campaign dei campi di personalizzazione per i quali i caratteri &quot;open&quot; e &quot;closed&quot; devono essere sostituiti da caratteri di escape (rispettivamente `&lt;` e `&gt;`).
   * L&#39;intero codice XML di OpenOffice verrà copiato nel documento di OpenOffice.

Nell’esempio, il blocco di personalizzazione si presenta così:

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
