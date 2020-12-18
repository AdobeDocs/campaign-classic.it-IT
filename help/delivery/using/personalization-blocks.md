---
solution: Campaign Classic
product: campaign
title: Blocchi di personalizzazione
description: Blocchi di personalizzazione
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 2%

---


# Blocchi di personalizzazione{#personalization-blocks}

I blocchi di personalizzazione sono dinamici, personalizzati e contengono un rendering specifico che potete inserire nelle consegne. Ad esempio, potete aggiungere un logo, un messaggio di saluto o un collegamento a una pagina mirror. Consultate [Inserimento di blocchi di personalizzazione](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png)[ Scopri questa funzione nel video](#personalization-blocks-video)

I blocchi di personalizzazione sono accessibili tramite il nodo **[!UICONTROL Resources > Campaign Management > Personalization blocks]** di Adobe Campaign Explorer . Per impostazione predefinita sono disponibili diversi blocchi (consultate [Blocchi di personalizzazione forniti con il prodotto](#out-of-the-box-personalization-blocks)).

Puoi definire nuovi blocchi che ti consentiranno di ottimizzare la personalizzazione delle consegne. Per ulteriori informazioni, vedere [Definizione di blocchi di personalizzazione personalizzati](#defining-custom-personalization-blocks).

>[!NOTE]
>
>I blocchi di personalizzazione sono disponibili anche da **[!UICONTROL Digital Content Editor (DCE)]** . Per ulteriori informazioni, consulta [questa pagina](../../web/using/editing-content.md#inserting-a-personalization-block).

## Inserimento di blocchi di personalizzazione {#inserting-personalization-blocks}

Per inserire un blocco di personalizzazione in un messaggio, effettua le operazioni seguenti:

1. Nell&#39;editor contenuti della procedura guidata di distribuzione, fai clic sull&#39;icona del campo personalizzato e seleziona il menu **[!UICONTROL Include]**.
1. Selezionate un blocco di personalizzazione dall&#39;elenco (l&#39;elenco visualizza gli ultimi 10 blocchi utilizzati) oppure fate clic sul menu **[!UICONTROL Other...]** per accedere all&#39;elenco completo.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Il menu **[!UICONTROL Other...]** consente di accedere a tutti i blocchi predefiniti e personalizzati di personalizzazione (consultate [Blocchi predefiniti di personalizzazione](#out-of-the-box-personalization-blocks) e [Definizione di blocchi personalizzati](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Il blocco di personalizzazione viene quindi inserito come script. Viene adattata automaticamente al profilo del destinatario quando viene generata la personalizzazione.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Fate clic sulla scheda **[!UICONTROL Preview]** e selezionate un destinatario per visualizzare la personalizzazione.

   ![](assets/s_ncs_user_personalized_block04.png)

Puoi includere il codice sorgente di un blocco di personalizzazione nel contenuto della distribuzione. A questo scopo, selezionare **[!UICONTROL Include the HTML source code of the block]** quando si seleziona.

![](assets/s_ncs_user_personalized_block05.png)

Il codice sorgente HTML viene inserito nel contenuto di consegna. Ad esempio, il blocco di personalizzazione **[!UICONTROL Greetings]** viene visualizzato come segue:

![](assets/s_ncs_user_personalized_block06.png)

## Esempio di blocchi di personalizzazione {#personalization-blocks-example}

In questo esempio, creiamo un&#39;e-mail in cui utilizziamo blocchi di personalizzazione per consentire al destinatario di visualizzare la pagina mirror, condividere la newsletter sui social network e annullare l&#39;iscrizione alle consegne future.

A tal fine, è necessario inserire i seguenti blocchi di personalizzazione:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Per ulteriori informazioni sulla generazione della pagina mirror, fare riferimento a [Generazione della pagina mirror](../../delivery/using/sending-messages.md#generating-the-mirror-page).

1. Create una nuova consegna o aprite una consegna di tipo e-mail esistente.
1. Nella procedura guidata di consegna, fare clic su **[!UICONTROL Subject]** per modificare l&#39;oggetto del messaggio e immettere un oggetto.
1. Inserisci i blocchi di personalizzazione nel corpo del messaggio. A tal fine, fai clic sul contenuto del messaggio, fai clic sull&#39;icona del campo personalizzato e seleziona il menu **[!UICONTROL Include]**.
1. Selezionare il primo blocco da inserire. Rinnovare la procedura per includere gli altri due blocchi.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Fate clic sulla scheda **[!UICONTROL Preview]** per visualizzare il risultato della personalizzazione. È necessario selezionare un destinatario per visualizzare il messaggio del destinatario.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Verificare che il contenuto del blocco sia visualizzato correttamente.

## Blocchi di personalizzazione standard {#out-of-the-box-personalization-blocks}

Per impostazione predefinita è disponibile un elenco di blocchi di personalizzazione per personalizzare il contenuto del messaggio.

>[!NOTE]
>
>L’elenco dei blocchi di personalizzazione dipende dai moduli e dalle opzioni installati nell’istanza.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : inserisce i saluti con il nome del destinatario. Esempio: &quot;Ciao John Doe,&quot;
* **[!UICONTROL Insert logo]** : inserisce un logo out-of-the-box definito durante la configurazione dell’istanza.
* **[!UICONTROL Powered by Adobe Campaign]** : inserisce il logo &quot;Powered by  Adobe Campaign&quot;.
* **[!UICONTROL Mirror page URL]** : inserisce l&#39;URL della pagina speculare, consentendo agli sviluppatori di distribuzione di controllare il collegamento.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla generazione della pagina mirror, fare riferimento a [Generazione della pagina mirror](../../delivery/using/sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : inserisce un collegamento alla pagina mirror: &quot;Se non riesci a visualizzare correttamente questo messaggio, fai clic qui&quot;.
* **[!UICONTROL Unsubscription link]** : inserisce un collegamento che consente di annullare l’iscrizione a tutte le consegne (elenco Bloccati).
* **[!UICONTROL Formatting function for proper nouns]** : genera la funzione  **[!UICONTROL toSmartCase]** Javascript, che modifica la prima lettera di ogni parola in maiuscolo. Questo blocco deve essere inserito nel codice sorgente del recapito, nei tag **`<script>...</script>`**.

   Nell&#39;esempio seguente, la funzione viene utilizzata per sostituire l&#39;elemento &quot;Intestazione personale&quot; con &quot;Nuova intestazione&quot; con lettere maiuscole a ogni parola:

   ```
   <h1 id="sample">My header</h1>
   <script><%@ include view='toSmartCase'%>;
   document.getElementById("sample").innerHTML = toSmartCase("My new header");
   </script>
   ```

   ![](assets/s_ncs_user_personalized_block_uppercasefunction.png)

* **[!UICONTROL Registration page URL]** : inserisce un URL di iscrizione (consultate  [Informazioni su servizi e iscrizioni](../../delivery/using/about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : inserisce un collegamento di iscrizione. che è stato definito durante la configurazione dell&#39;istanza.
* **[!UICONTROL Registration link (with referrer)]** : inserisce un collegamento di iscrizione che consente di identificare il visitatore e la consegna. Il collegamento è stato definito durante la configurazione dell&#39;istanza.

   >[!NOTE]
   >
   >Questo blocco può essere utilizzato solo per i visitatori di destinazione delle consegne.

* **[!UICONTROL Registration confirmation]** : inserisce un collegamento che consente di confermare l’iscrizione.
* **[!UICONTROL Social network sharing links]** : inserisce pulsanti che consentono al destinatario di condividere un collegamento al contenuto della pagina mirror con il client e-mail, Facebook, Twitter, Google + e LinkedIn (consultate  [Viral marketing: inoltrare a un amico](../../delivery/using/viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** e  **[!UICONTROL Notification style]** : generate codice che formatta un&#39;e-mail con stili HTML predefiniti. Questi blocchi devono essere inseriti nel codice sorgente del recapito, nella sezione **[!UICONTROL ...]**, nei tag **`<style>...</style>`**.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : inserisce un URL che consente di impostare un&#39;offerta di interazione su  **[!UICONTROL Accepted]** (consultate  [questa sezione](../../interaction/using/offer-analysis-report.md)).

## Definizione di blocchi personalizzati di personalizzazione {#defining-custom-personalization-blocks}

Puoi definire nuovi campi di personalizzazione da inserire dall&#39;icona del campo personalizzato tramite il menu **[!UICONTROL Include...]**. Questi campi sono definiti in blocchi di personalizzazione.

Per creare un blocco di personalizzazione, accedete a Esplora risorse e eseguite i seguenti passaggi:

1. Fare clic sul nodo **[!UICONTROL Resources > Campaign Management > Personalization blocks]**.
1. Fare clic con il pulsante destro del mouse sull&#39;elenco dei blocchi e selezionare **[!UICONTROL New]** .
1. Compila le impostazioni del blocco di personalizzazione:

   ![](assets/s_ncs_user_personalized_block.png)

   * Immettere l&#39;etichetta del blocco. Questa etichetta verrà visualizzata nella finestra di inserimento del campo di personalizzazione.
   * Selezionare **[!UICONTROL Visible in the customization menus]** per rendere questo blocco accessibile dall&#39;icona di inserimento del campo di personalizzazione.
   * Se necessario, selezionate **[!UICONTROL The content of the personalization block depends upon the format]** per definire due blocchi distinti per le e-mail in formato HTML e per quelle in formato testo.

      Nella sezione inferiore di questo editor (contenuto HTML e contenuto di testo) vengono quindi visualizzate due schede per definire il contenuto corrispondente.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Immettete il contenuto (in HTML, testo, JavaScript, ecc.) dei blocchi di personalizzazione e fate clic su **[!UICONTROL Save]**.

## Video di esercitazione {#personalization-blocks-video}

Scoprite come creare blocchi di contenuto dinamici e come utilizzarli per personalizzare il contenuto della distribuzione delle e-mail.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
