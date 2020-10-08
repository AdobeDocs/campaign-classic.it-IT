---
title: Contenuto condizionale
seo-title: Contenuto condizionale
description: Contenuto condizionale
seo-description: null
page-status-flag: never-activated
uuid: d1c38263-a163-448c-8822-8b3e776e45cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
discoiquuid: 167cc61a-fbc7-48cb-89ff-fbdbf9321c01
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 2%

---


# Contenuto condizionale{#conditional-content}

Configurando i campi di contenuto condizionale, puoi creare una personalizzazione dinamica in base, ad esempio, al profilo del destinatario. I blocchi di testo e/o le immagini vengono sostituiti quando una particolare condizione è soddisfatta.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#conditionnal-content-video)


## Utilizzo delle condizioni in un messaggio e-mail {#using-conditions-in-an-email}

Nell&#39;esempio seguente verrà illustrato come creare un messaggio, personalizzato in modo dinamico in base al genere e agli interessi del destinatario.

* Display che mostra &quot;Mr&quot; o &quot;Ms.&quot; in base al valore del **[!UICONTROL Gender]** campo (M o F) nell&#39;origine dati,
* Assemblaggio personalizzato di una newsletter o di offerte promozionali in base agli interessi indicati o rilevati:

   * Interesse 1 — > Blocco 1
   * Interesse 2 — > Blocco 2
   * Interesse 3 — > Blocco 3
   * Interesse 4 — > Blocco 4

Per creare contenuto condizionale in base al valore di un campo, procedere come segue:

1. Fate clic sull&#39;icona della personalizzazione e selezionate **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Gli elementi di personalizzazione vengono inseriti nel corpo del messaggio. È ora necessario configurarli.

1. Quindi, inserite i parametri dell&#39;espressione **if** .

   Per eseguire questa operazione:

   * Selezionate il primo elemento dell&#39;espressione **`<field>`**(per impostazione predefinita, questo elemento viene evidenziato durante l&#39;inserimento dell&#39;espressione **if** ) e fate clic sull&#39;icona di personalizzazione per sostituirlo con il campo di prova.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Sostituire **`<value>`** con il valore del campo per il quale verrà soddisfatta la condizione. Questo valore deve essere racchiuso tra virgolette.
   * Specificate il contenuto da inserire quando la condizione è soddisfatta. Può trattarsi di testo, immagine, modulo, collegamento ipertestuale e così via.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Fai clic sulla **[!UICONTROL Preview]** scheda per visualizzare il contenuto del messaggio in base al destinatario:

   * Selezione di un destinatario per il quale la condizione è vera:

      ![](assets/s_ncs_user_conditional_content05.png)

   * Selezione di un destinatario per il quale la condizione non è vera:

      ![](assets/s_ncs_user_conditional_content06.png)

È possibile aggiungere altri casi e definire contenuti diversi in base ai valori di uno o più campi. Per fare ciò, utilizzare **[!UICONTROL Conditional content > Else]** e **[!UICONTROL Conditional content > Else if]**. Queste espressioni sono configurate nello stesso modo dell&#39;espressione **if** .

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Per rispettare la sintassi JavaScript, i caratteri **%> &lt;%** devono essere eliminati dopo l&#39;aggiunta di condizioni **Else** e **Else if** .

Fate clic su **[!UICONTROL Preview]** e selezionate un destinatario per visualizzare il contenuto condizionale.

![](assets/s_ncs_user_conditional_content08.png)

## Creazione di e-mail in più lingue {#creating-multilingual-email}

Nell’esempio seguente, verrà illustrato come creare un’e-mail in più lingue. Il contenuto verrà visualizzato in una lingua o nell&#39;altra a seconda della lingua preferita del destinatario.

1. Create un messaggio e-mail e selezionate la popolazione di destinazione. In questo esempio, la condizione per visualizzare una versione o l&#39;altra sarà basata sul valore **Lingua** del profilo del destinatario. In questo esempio, questi valori sono impostati su **EN**, **FR**, **ES**.
1. Nel contenuto HTML dell&#39;e-mail, fate clic sulla **[!UICONTROL Source]** scheda e incollate il seguente codice:

   ```
   <% if (language == "EN" ) { %>
   <DIV id=en-version>Hello <%= recipient.firstName %>,</DIV>
   <DIV>Discover your new offers!</DIV>
   <DIV><a href="https://www.adobe.com/products/en">www.adobe.com/products/en</A></FONT></DIV><%
    } %>
   <% if (language == "FR" ) { %>
   <DIV id=fr-version>Bonjour <%= recipient.firstName %>,</DIV>
   <DIV>Découvrez nos nouvelles offres !</DIV>
   <DIV><a href="https://www.adobe.com/products/fr">www.adobe.com/products/fr</A></DIV><%
    } %>
    <% if (language == "ES" ) { %>
   <DIV id=es-version><FONT face=Arial>
   <DIV>Olà <%= recipient.firstName %>,</DIV>
   <DIV>Descubra nuestros nuevas ofertas !</DIV>
   <DIV><a href="https://www.adobe.com/products/es">www.adobe.com/products/es</A></DIV>
   <% } %>
   ```

1. Verifica il contenuto delle e-mail nella **[!UICONTROL Preview]** scheda selezionando i destinatari con lingue diverse tra loro preferite.

   >[!NOTE]
   >
   >Poiché nel contenuto dell’e-mail non è stata definita alcuna versione alternativa, accertatevi di filtrare la popolazione di destinazione prima di inviare l’e-mail.

## Come creare una newsletter multilingue con contenuti condizionali {#conditionnal-content-video}

Scoprite come aggiungere contenuti condizionali a una distribuzione, ad esempio una newsletter multilingue.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)
