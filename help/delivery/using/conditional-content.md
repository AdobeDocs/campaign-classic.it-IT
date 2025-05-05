---
product: campaign
title: Contenuto condizionale
description: Scopri come aggiungere contenuti condizionali
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Personalization, Multilingual Messages
role: User
exl-id: 12595ee4-6a52-4e06-b80d-85fe633a5a11
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 7%

---

# Contenuto condizionale{#conditional-content}

Configurando i campi di contenuto condizionale, puoi creare una personalizzazione dinamica basata, ad esempio, sul profilo del destinatario. I blocchi di testo e/o le immagini vengono sostituiti quando viene soddisfatta una particolare condizione.

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#conditionnal-content-video)


## Condizioni di utilizzo in un messaggio e-mail {#using-conditions-in-an-email}

Nell’esempio seguente, imparerai a creare un messaggio personalizzato dinamicamente sul genere e gli interessi del destinatario.

* Display che mostra &quot;Mr&quot; o &quot;Ms.&quot; in base al valore del campo **[!UICONTROL Gender]** (M o F) nell&#39;origine dati,
* Assemblaggio personalizzato di una newsletter o di offerte promozionali in base agli interessi indicati o rilevati:

   * Interesse 1 — > Blocco 1
   * Interesse 2 — > Blocco 2
   * Interesse 3 — > Blocco 3
   * Interesse 4 — > Blocco 4

Per creare contenuto condizionale in base al valore di un campo, effettua le seguenti operazioni:

1. Fare clic sull&#39;icona di personalizzazione e selezionare **[!UICONTROL Conditional content > If]**.

   ![](assets/s_ncs_user_conditional_content02.png)

   Gli elementi di personalizzazione vengono inseriti nel corpo del messaggio. Ora devi configurarli.

1. Compilare quindi i parametri dell&#39;espressione **if**.

   Per eseguire questa operazione:

   * Selezionare il primo elemento dell&#39;espressione, **`<field>`**, (per impostazione predefinita, questo elemento viene evidenziato durante l&#39;inserimento dell&#39;espressione **if**) e fare clic sull&#39;icona di personalizzazione per sostituirlo con il campo di test.

     ![](assets/s_ncs_user_conditional_content03.png)

   * Sostituire **`<value>`** con il valore del campo per il quale verrà soddisfatta la condizione. Questo valore deve essere racchiuso tra virgolette.
   * Specifica il contenuto da inserire quando la condizione viene soddisfatta. Potrebbe trattarsi di testo, immagine, modulo, collegamento ipertestuale, ecc.

     ![](assets/s_ncs_user_conditional_content04.png)

1. Fare clic sulla scheda **[!UICONTROL Preview]** per visualizzare il contenuto del messaggio in base al destinatario della consegna:

   * Selezione di un destinatario per il quale la condizione è true:

     ![](assets/s_ncs_user_conditional_content05.png)

   * Selezione di un destinatario per il quale la condizione non è true:

     ![](assets/s_ncs_user_conditional_content06.png)

Puoi aggiungere altri casi e definire contenuti diversi in base ai valori di uno o più campi. Per eseguire questa operazione, utilizzare **[!UICONTROL Conditional content > Else]** e **[!UICONTROL Conditional content > Else if]**. Queste espressioni sono configurate nello stesso modo dell&#39;espressione **if**.

![](assets/s_ncs_user_conditional_content07.png)

>[!CAUTION]
>
>Per rispettare la sintassi di JavaScript, è necessario eliminare i caratteri **%> &lt;%** dopo aver aggiunto le condizioni **Else** e **Else if**.

Fare clic su **[!UICONTROL Preview]** e selezionare un destinatario per visualizzare il contenuto condizionale.

![](assets/s_ncs_user_conditional_content08.png)

## Creare un messaggio e-mail multilingue {#creating-multilingual-email}

Nell’esempio seguente, scoprirai come creare un’e-mail multilingue. Il contenuto verrà visualizzato in una lingua o nell’altra, a seconda della lingua preferita del destinatario.

1. Crea un messaggio e-mail e seleziona la popolazione target. In questo esempio, la condizione per visualizzare una versione o l&#39;altra sarà basata sul valore **Lingua** del profilo del destinatario. In questo esempio, questi valori sono impostati su **EN**, **FR**, **ES**.
1. Nel contenuto di e-mail HTML, fare clic sulla scheda **[!UICONTROL Source]** e incollare il seguente codice:

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

1. Verificare il contenuto delle e-mail nella scheda **[!UICONTROL Preview]** selezionando i destinatari con lingue preferite diverse.

   >[!NOTE]
   >
   >Poiché nel contenuto dell’e-mail non è stata definita alcuna versione alternativa, assicurati di filtrare la popolazione target prima di inviare l’e-mail.

## Video tutorial {#conditionnal-content-video}

Scopri come aggiungere contenuti condizionali a una consegna sull’esempio di una newsletter multilingue.

>[!VIDEO](https://video.tv.adobe.com/v/329895?quality=12&captions=ita)

Ulteriori video dimostrativi di Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
