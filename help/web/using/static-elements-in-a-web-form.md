---
product: campaign
title: Elementi statici in un modulo web
description: Elementi statici in un modulo web
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 364d90af-4b18-4104-8b6a-be80cfde3b0b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1034'
ht-degree: 3%

---

# Elementi statici in un modulo web{#static-elements-in-a-web-form}

![](../../assets/common.svg)

Nelle pagine del modulo è possibile includere elementi con i quali l’utente non interagisce; si tratta di elementi statici quali immagini, contenuto HTML, barra orizzontale o collegamento ipertestuale. Questi elementi vengono creati tramite il primo pulsante nella barra degli strumenti, selezionando **[!UICONTROL Static elements]**.

![](assets/s_ncs_admin_survey_add_static_element.png)

Sono disponibili i seguenti tipi di campi:

* Valore basato su risposte fornite in precedenza (nel contesto del modulo) o sul database.
* Collegamento ipertestuale, HTML, barra orizzontale. Consulta [Inserimento di contenuto HTML](#inserting-html-content).
* Immagine salvata nella libreria delle risorse o su un server accessibile dagli utenti. Consulta [Inserimento di immagini](#inserting-images).
* Script eseguito sul lato client e/o sul lato server. Deve essere scritto in JavaScript ed essere compatibile con la maggior parte dei browser per garantire la corretta esecuzione sul lato client.

   >[!NOTE]
   >
   >Sul lato server, lo script può utilizzare le funzioni definite nella [documentazione JSAPI di Campaign](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html).

## Inserisci contenuto HTML {#inserting-html-content}

È possibile includere il contenuto HTML in una pagina del modulo: collegamenti ipertestuali, immagini, paragrafi formattati, video e così via

L’editor HTML consente di inserire il contenuto da inserire nella pagina del modulo. Per aprire l’editor, fai clic su **[!UICONTROL Static elements]** > **[!UICONTROL HTML]** .

È possibile immettere e formattare il contenuto direttamente o visualizzare la finestra del codice sorgente da incollare in alcuni contenuti esterni. Per passare alla modalità &quot;codice sorgente&quot;, fai clic sulla prima icona nella barra degli strumenti:

![](assets/s_ncs_admin_survey_html_editor.png)

Per inserire un campo di database, utilizza il pulsante di personalizzazione.

![](assets/webapp_perso_button_in_html.png)

>[!NOTE]
>
>Le stringhe immesse nell’editor HTML vengono tradotte solo se sono definite nella sottoscheda **[!UICONTROL Texts]** . Altrimenti non saranno raccolti. Per ulteriori informazioni, consulta [Traduzione di un modulo web](translating-a-web-form.md).

### Inserire un collegamento {#inserting-a-link}

Compila i campi nella finestra di modifica come mostrato nell’esempio seguente:

Per aggiungere un collegamento ipertestuale, vai a **[!UICONTROL Static elements]** > **[!UICONTROL Link]**.

![](assets/s_ncs_admin_survey_add_link.png)

* Il **[!UICONTROL Label]** è il contenuto del collegamento ipertestuale così come verrà visualizzato nella pagina del modulo.
* L’ **[!UICONTROL URL]** è l’indirizzo desiderato, ad esempio: [https://www.adobe.com](https://www.adobe.com) per un sito web o [info@adobe.com](mailto:info@adobe.com) per inviare un messaggio.
* Il campo **[!UICONTROL Window]** ti consente di selezionare la modalità di visualizzazione del collegamento nel caso di un sito. Puoi decidere di aprire il collegamento in una nuova finestra, nella finestra corrente o in un’altra finestra.
* È possibile aggiungere una descrizione comandi, come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_send_an_email.png)

* Puoi scegliere di visualizzare il collegamento come pulsante o immagine. A questo scopo, seleziona il tipo di visualizzazione nel campo **[!UICONTROL Type]** .

### Tipi di collegamenti {#types-of-links}

Per impostazione predefinita, i collegamenti sono associati a un’azione di tipo URL, in modo che un indirizzo di destinazione di collegamento possa essere inserito nel campo URL.

![](assets/s_ncs_admin_survey_link_url.png)

Puoi definire altre azioni per il collegamento, in modo che l’utente possa fare clic sul collegamento per effettuare le seguenti operazioni:

* Aggiorna la pagina

   A questo scopo, seleziona l’opzione **[!UICONTROL Refresh page]** nella casella a discesa del campo **[!UICONTROL Action]** .

   ![](assets/s_ncs_admin_survey_link_refresh.png)

* Visualizzare la pagina successiva/precedente

   A questo scopo, seleziona l’opzione **[!UICONTROL Next page]** o **[!UICONTROL Previous page]** nella casella a discesa del campo **[!UICONTROL Action]** .

   ![](assets/s_ncs_admin_survey_link_next.png)

   È possibile nascondere i pulsanti **[!UICONTROL Next]** e/o **[!UICONTROL Back]** se devono essere sostituiti da un collegamento. Fai riferimento a questa [pagina](defining-web-forms-page-sequencing.md).

   Il collegamento sostituirà il pulsante **[!UICONTROL Next]** utilizzato per impostazione predefinita.

   ![](assets/s_ncs_admin_survey_link_next_ex.png)

* Visualizzare un’altra pagina

   L’opzione **[!UICONTROL Enable a transition]** ti consente di visualizzare una pagina specifica associata alla transizione in uscita selezionata nel campo **[!UICONTROL Transition]** .

   ![](assets/s_ncs_admin_survey_link_viral.png)

   Per impostazione predefinita, una pagina dispone di una sola transizione di output. Per creare nuove transizioni, seleziona la pagina e fai clic sul pulsante **[!UICONTROL Add]** nella sezione **[!UICONTROL Output transitions]** , come illustrato di seguito:

   ![](assets/s_ncs_admin_survey_add_transition.png)

   Nel diagramma, questa aggiunta avrà un aspetto simile al seguente:

   ![](assets/s_ncs_admin_survey_add_transition_graph.png)

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla sequenza di pagine in un modulo web, consulta [Definizione della sequenza di pagine dei moduli web](defining-web-forms-page-sequencing.md).

### Personalizzare il contenuto HTML {#personalizing-html-content}

È possibile personalizzare il contenuto HTML di una pagina del modulo con i dati registrati in una pagina precedente. Ad esempio, è possibile creare un modulo Web di assicurazione auto la cui prima pagina consente di fornire informazioni di contatto e il marchio dell&#39;auto.

![](assets/s_ncs_admin_survey_tag_ctx_1.png)

Utilizza i campi di personalizzazione per inserire nuovamente il nome utente e il marchio selezionato nella pagina successiva. La sintassi da utilizzare dipende dalla modalità di archiviazione delle informazioni. Per ulteriori informazioni, consulta [Utilizzo delle informazioni raccolte](web-forms-answers.md#using-collected-information).

>[!NOTE]
>
>Per motivi di sicurezza, il valore immesso nella formula **`<%=`** viene sostituito con caratteri di escape.

Nel nostro esempio, il nome e il cognome del destinatario sono memorizzati in un campo del database, mentre il marchio della propria auto è memorizzato in una variabile. La sintassi del messaggio personalizzato a pagina 2 sarà la seguente:

![](assets/webapp_perso_vars_include.png)

```
<P>Welcome <%= ctx.recipient.@firstName %> <%= ctx.recipient.@lastName %>,</P>
<P>To start your customized study, please select your car <%=ctx.vars.marque%> and its year of purchase.</P>
```

Questo produce il seguente risultato:

![](assets/s_ncs_admin_survey_tag_ctx_2.png)

### Usa variabili di testo {#using-text-variables}

La scheda **[!UICONTROL Text]** ti consente di creare campi variabili che possono essere utilizzati nell’HTML tra i caratteri &lt;%= e %> con la seguente sintassi: **$(IDENTIFIER)**.

Utilizza questo metodo per localizzare facilmente le stringhe. Vedere [Traduzione di un modulo web](translating-a-web-form.md)

Ad esempio, puoi creare un campo **Contact** che ti consente di visualizzare la stringa &quot;Data dell’ultimo contatto:&quot; nel contenuto HTML. Per farlo, segui la procedura indicata di seguito:

1. Fai clic sulla scheda **[!UICONTROL Text]** del testo HTML.
1. Fai clic sull&#39;icona **[!UICONTROL Add]** .
1. Nella colonna **[!UICONTROL Identifier]** , immetti il nome della variabile
1. Nella colonna **[!UICONTROL Text]**, immetti il valore predefinito.

   ![](assets/s_ncs_admin_survey_html_text.png)

1. Nel contenuto HTML, inserisci questa variabile di testo tramite la sintassi **&lt;%= $(Contact) %>**.

   ![](assets/s_ncs_admin_survey_html_content.png)

   >[!CAUTION]
   >
   >Se immetti questi caratteri nell’editor HTML, i campi **&lt;** e **** verranno sostituiti con i relativi caratteri di escape. In questo caso, è necessario correggere il codice sorgente facendo clic sull’ icona **[!UICONTROL Display source code]** dell’editor di testo HTML.

1. Apri l’etichetta **[!UICONTROL Preview]** del modulo per visualizzare il valore immesso nel codice HTML:

   ![](assets/s_ncs_admin_survey_html_content_preview.png)

Questa modalità operativa consente di definire il testo dei moduli web una sola volta e di gestire le traduzioni utilizzando lo strumento di traduzione integrato. Per ulteriori informazioni, consulta [Traduzione di un modulo web](translating-a-web-form.md).

## Inserisci immagini {#inserting-images}

Affinché le immagini possano essere incluse nei moduli, è necessario salvarle su un server accessibile dall’esterno.

Selezionare il menu **[!UICONTROL Static elements]** > **[!UICONTROL Image]**.

Seleziona l’origine dell’immagine da inserire: può provenire dalla libreria delle risorse pubbliche o essere memorizzato in un server esterno accessibile dall’esterno.

![](assets/s_ncs_admin_survey_add_img.png)

Se si tratta di un’immagine dalla libreria, selezionarla nella casella combinata del campo; se si trova in un file esterno, immetti il percorso di accesso. L’etichetta viene visualizzata passando il cursore sull’immagine (coincide con un campo ALT in HTML) o quando l’immagine non viene visualizzata.

L’immagine può essere visualizzata nella sezione centrale dell’editor.
