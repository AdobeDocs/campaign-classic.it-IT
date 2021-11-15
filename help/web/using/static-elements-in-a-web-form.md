---
product: campaign
title: Elementi statici in un modulo web
description: Elementi statici in un modulo web
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: 5d9e2f7d7cea9e6d1243b0e3a790f3990772e603
workflow-type: tm+mt
source-wordcount: '1031'
ht-degree: 2%

---

# Elementi statici in un modulo web{#static-elements-in-a-web-form}

![](../../assets/common.svg)

Nelle pagine del modulo è possibile includere elementi con i quali l’utente non interagisce; si tratta di elementi statici quali immagini, contenuto HTML, barra orizzontale o collegamento ipertestuale. Questi elementi vengono creati tramite il primo pulsante nella barra degli strumenti, selezionando **[!UICONTROL Static elements]**.

![](assets/s_ncs_admin_survey_add_static_element.png)

Sono disponibili i seguenti tipi di campi:

* Valore basato su risposte fornite in precedenza (nel contesto del modulo) o sul database.
* Collegamento ipertestuale, HTML, barra orizzontale. Vedi [Inserimento di contenuto HTML](#inserting-html-content).
* Immagine salvata nella libreria delle risorse o su un server accessibile dagli utenti. Vedi [Inserimento di immagini](#inserting-images).
* Script eseguito sul lato client e/o sul lato server. Deve essere scritto in JavaScript ed essere compatibile con la maggior parte dei browser per garantire la corretta esecuzione sul lato client.

   >[!NOTE]
   >
   >Sul lato server, lo script può utilizzare le funzioni definite in [Documentazione JSAPI per Campaign](https://experienceleague.adobe.com/developer/campaign-api/api/index.html).

## Inserisci contenuto HTML {#inserting-html-content}

È possibile includere il contenuto di HTML in una pagina del modulo: collegamenti ipertestuali, immagini, paragrafi formattati, video e così via

L’editor di HTML consente di inserire il contenuto da inserire nella pagina del modulo. Per aprire l’editor, fai clic su **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** .

È possibile immettere e formattare il contenuto direttamente o visualizzare la finestra del codice sorgente da incollare in alcuni contenuti esterni. Per passare alla modalità &quot;codice sorgente&quot;, fai clic sulla prima icona nella barra degli strumenti:

![](assets/s_ncs_admin_survey_html_editor.png)

Per inserire un campo di database, utilizza il pulsante di personalizzazione.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>Le stringhe immesse nell’editor di HTML vengono tradotte solo se sono definite nel **[!UICONTROL Texts]** sottoscheda . Altrimenti non saranno raccolti. Per ulteriori informazioni, consulta [Traduzione di un modulo web](translating-a-web-form.md).

### Inserire un collegamento {#inserting-a-link}

Compila i campi nella finestra di modifica come mostrato nell’esempio seguente:

Per aggiungere un collegamento ipertestuale, vai a **[!UICONTROL Static elements]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* La **[!UICONTROL Label]** è il contenuto del collegamento ipertestuale visualizzato nella pagina del modulo.
* La **[!UICONTROL URL]** è l’indirizzo desiderato, ad esempio: [https://www.adobe.com](https://www.adobe.com) per un sito web, oppure [info@adobe.com](mailto:info@adobe.com) per inviare un messaggio.
* La **[!UICONTROL Window]** consente di selezionare la modalità di visualizzazione del collegamento nel caso di un sito. Puoi decidere di aprire il collegamento in una nuova finestra, nella finestra corrente o in un’altra finestra.
* È possibile aggiungere una descrizione comandi, come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* Puoi scegliere di visualizzare il collegamento come pulsante o immagine. A questo scopo, seleziona il tipo di visualizzazione nel **[!UICONTROL Type]** campo .

### Tipi di collegamenti {#types-of-links}

Per impostazione predefinita, i collegamenti sono associati a un’azione di tipo URL, in modo che un indirizzo di destinazione di collegamento possa essere inserito nel campo URL.

![](assets/s_ncs_admin_survey_link_url.png)

Puoi definire altre azioni per il collegamento, in modo che l’utente possa fare clic sul collegamento per effettuare le seguenti operazioni:

* Aggiorna la pagina

   A questo scopo, seleziona la **[!UICONTROL Refresh page]** nella casella a discesa della **[!UICONTROL Action]** campo .

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* Visualizzare la pagina successiva/precedente

   A questo scopo, seleziona la **[!UICONTROL Next page]** o **[!UICONTROL Previous page]** nella casella a discesa della **[!UICONTROL Action]** campo .

   ![](assets/s_ncs_admin_survey_link_next.png)

   Puoi nascondere la **[!UICONTROL Next]** e/o **[!UICONTROL Back]** se devono essere sostituiti da un collegamento. Fai riferimento a questo [page](defining-web-forms-page-sequencing.md).

   Il collegamento sostituirà il **[!UICONTROL Next]** per impostazione predefinita.

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* Visualizzare un’altra pagina

   La **[!UICONTROL Enable a transition]** consente di visualizzare una pagina specifica associata alla transizione in uscita selezionata nel **[!UICONTROL Transition]** campo .

   ![](assets/s_ncs_admin_survey_link_viral.png)

   Per impostazione predefinita, una pagina dispone di una sola transizione di output. Per creare nuove transizioni, seleziona la pagina e fai clic sul pulsante **[!UICONTROL Add]** nel **[!UICONTROL Output transitions]** come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_add_transition.png)

   Nel diagramma, questa aggiunta avrà un aspetto simile al seguente:

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla sequenza delle pagine in un modulo Web, fare riferimento a [Definizione della sequenza di pagine dei moduli web](defining-web-forms-page-sequencing.md).

### Personalizzare il contenuto HTML {#personalizing-html-content}

È possibile personalizzare il contenuto HTML di una pagina del modulo con i dati registrati in una pagina precedente. Ad esempio, è possibile creare un modulo Web di assicurazione auto la cui prima pagina consente di fornire informazioni di contatto e il marchio dell&#39;auto.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

Utilizza i campi di personalizzazione per inserire nuovamente il nome utente e il marchio selezionato nella pagina successiva. La sintassi da utilizzare dipende dalla modalità di archiviazione delle informazioni. Per ulteriori informazioni, consulta [Utilizzo delle informazioni raccolte](web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>Per motivi di sicurezza, il valore immesso nel **`<%=`** La formula viene sostituita con caratteri di escape.

Nel nostro esempio, il nome e il cognome del destinatario sono memorizzati in un campo del database, mentre il marchio della propria auto è memorizzato in una variabile. La sintassi del messaggio personalizzato a pagina 2 sarà la seguente:

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

Questo produce il seguente risultato:

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### Usa variabili di testo {#using-text-variables}

La **[!UICONTROL Text]** tab consente di creare campi variabili che possono essere utilizzati in HTML tra i caratteri &lt;%= e %> con la sintassi seguente: **$(IDENTIFICATORE)**.

Utilizza questo metodo per localizzare facilmente le stringhe. Vedi [Traduzione di un modulo web](translating-a-web-form.md)

Ad esempio, puoi creare una **Contatto** campo che consente di visualizzare la stringa &quot;Data dell’ultimo contatto:&quot; nel contenuto di HTML. Per farlo, segui la procedura indicata di seguito:

1. Fai clic sul pulsante **[!UICONTROL Text]** scheda del testo di HTML.
1. Fai clic sul pulsante **[!UICONTROL Add]** icona.
1. In **[!UICONTROL Identifier]** , immetti il nome della variabile
1. In **[!UICONTROL Text]** , immetti il valore predefinito.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. Nel contenuto di HTML, inserisci questa variabile di testo tramite il **&lt;%= $(contatto) %>** sintassi.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >Se immetti questi caratteri nell’editor di HTML, l’ **&lt;** e **>** i campi verranno sostituiti con i relativi caratteri di escape. In questo caso, è necessario correggere il codice sorgente facendo clic sul pulsante **[!UICONTROL Display source code]** dell’editor di testo di HTML.

1. Apri **[!UICONTROL Preview]** etichetta del modulo per visualizzare il valore immesso in HTML:

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

Questa modalità operativa consente di definire il testo dei moduli web una sola volta e di gestire le traduzioni utilizzando lo strumento di traduzione integrato. Per ulteriori informazioni, consulta [Traduzione di un modulo web](translating-a-web-form.md).

## Inserisci immagini {#inserting-images}

Affinché le immagini possano essere incluse nei moduli, è necessario salvarle su un server accessibile dall’esterno.

Seleziona la **[!UICONTROL Static elements]** > **[!UICONTROL Image]** menu.

Seleziona l’origine dell’immagine da inserire: può provenire dalla libreria delle risorse pubbliche o essere memorizzato in un server esterno accessibile dall’esterno.

![](assets/s_ncs_admin_survey_add_img.png)

Se si tratta di un’immagine dalla libreria, selezionarla nella casella combinata del campo; se si trova in un file esterno, immetti il percorso di accesso. L’etichetta viene visualizzata passando il cursore sull’immagine (coincide con un campo ALT in HTML) o quando l’immagine non viene visualizzata.

L’immagine può essere visualizzata nella sezione centrale dell’editor.
