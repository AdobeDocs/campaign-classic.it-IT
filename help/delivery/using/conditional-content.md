---
product: campaign
title: Contenuto condizionale
description: Contenuto condizionale
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 7%

---

# Contenuto condizionale{#conditional-content}

![](../../assets/common.svg)

Configurando i campi di contenuto condizionale, puoi creare una personalizzazione dinamica basata, ad esempio, sul profilo del destinatario. I blocchi di testo e/o le immagini vengono sostituiti quando viene soddisfatta una particolare condizione.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#conditionnal-content-video)


## Utilizzo delle condizioni in un messaggio e-mail {#using-conditions-in-an-email}

Nell’esempio seguente, imparerai a creare un messaggio personalizzato in modo dinamico in base al genere e agli interessi del destinatario.

* Visualizzazione che mostra &quot;Mr&quot; o &quot;Ms&quot; in base al valore del campo **[!UICONTROL Gender]** (M o F) nell&#39;origine dati,
* Assemblaggio personalizzato di newsletter o offerte promozionali in base agli interessi indicati o rilevati:

   * Interesse 1 — > Blocco 1
   * Interesse 2 — > Blocco 2
   * Interesse 3 — > Blocco 3
   * Interesse 4 — > Blocco 4

Per creare contenuto condizionale in base al valore di un campo, procedi come segue:

1. Fai clic sull’icona della personalizzazione e seleziona **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Gli elementi di personalizzazione vengono inseriti nel corpo del messaggio. È ora necessario configurarli.

1. Quindi, compila i parametri dell&#39;espressione **if** .

   Per eseguire questa operazione:

   * Seleziona il primo elemento dell’espressione, **`<field>`** (per impostazione predefinita, questo elemento viene evidenziato durante l’inserimento dell’espressione **if**), quindi fai clic sull’icona di personalizzazione per sostituirlo con il campo di test.

      ![](assets/s_ncs_user_conditional_content03.png)

   * Sostituisci **`<value>`** con il valore del campo per il quale la condizione verrà soddisfatta. Questo valore deve essere racchiuso tra virgolette.
   * Specifica il contenuto da inserire quando la condizione viene soddisfatta. Può essere costituito da testo, un’immagine, un modulo, un collegamento ipertestuale, ecc.

      ![](assets/s_ncs_user_conditional_content04.png)

1. Fai clic sulla scheda **[!UICONTROL Preview]** per visualizzare il contenuto del messaggio in base al destinatario della consegna:

   * Selezione di un destinatario per il quale la condizione è vera:

      ![](assets/s_ncs_user_conditional_content05.png)

   * Selezione di un destinatario per il quale la condizione non è vera:

      ![](assets/s_ncs_user_conditional_content06.png)

Puoi aggiungere altri casi e definire contenuti diversi in base ai valori di uno o più campi. A questo scopo, utilizza **[!UICONTROL Conditional content > Else]** e **[!UICONTROL Conditional content > Else if]**. Queste espressioni sono configurate nello stesso modo dell&#39;espressione **if**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Per rispettare la sintassi JavaScript, i caratteri **%> &lt;%** devono essere eliminati dopo l&#39;aggiunta delle condizioni **Else** e **Else** .

Fai clic su **[!UICONTROL Preview]** e seleziona un destinatario per visualizzare il contenuto condizionale.

![](assets/s_ncs_user_conditional_content08.png)

## Creazione di e-mail multilingue {#creating-multilingual-email}

Nell’esempio seguente, imparerai a creare un’e-mail multilingue. Il contenuto verrà visualizzato in una lingua o nell’altra a seconda della lingua preferita del destinatario.

1. Crea un’e-mail e seleziona la popolazione target. In questo esempio, la condizione per visualizzare una versione o l&#39;altra sarà basata sul valore **Language** del profilo del destinatario. In questo esempio, questi valori sono impostati su **EN**, **FR**, **ES**.
1. Nel contenuto HTML dell’e-mail, fai clic sulla scheda **[!UICONTROL Source]** e incolla il seguente codice:

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

1. Verifica il contenuto delle e-mail nella scheda **[!UICONTROL Preview]** selezionando i destinatari con diverse lingue preferite.

   >[!NOTE]
   >
   >Poiché non è stata definita alcuna versione alternativa nel contenuto dell’e-mail, assicurati di filtrare la popolazione target prima di inviare l’e-mail.

## Video tutorial {#conditionnal-content-video}

Scopri come aggiungere contenuti condizionali a una consegna sull’esempio di una newsletter multilingue.

>[!VIDEO](https://video.tv.adobe.com/v/24926?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
