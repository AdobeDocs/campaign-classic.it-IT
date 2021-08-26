---
product: campaign
title: Blocchi di personalizzazione
description: Blocchi di personalizzazione
audience: delivery
content-type: reference
topic-tags: personalizing-deliveries
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 2%

---

# Blocchi di personalizzazione{#personalization-blocks}

![](../../assets/common.svg)

I blocchi di personalizzazione sono dinamici, personalizzati e contengono un rendering specifico che puoi inserire nelle consegne. Ad esempio, puoi aggiungere un logo, un messaggio di auguri o un collegamento a una pagina speculare. Consulta [Inserimento di blocchi di personalizzazione](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png)[ Scopri questa funzione nel video](#personalization-blocks-video)

I blocchi di personalizzazione sono accessibili tramite il nodo **[!UICONTROL Resources > Campaign Management > Personalization blocks]** di Adobe Campaign explorer. Per impostazione predefinita sono disponibili diversi blocchi (consulta [Blocchi di personalizzazione preconfigurati](#out-of-the-box-personalization-blocks)).

Puoi definire nuovi blocchi che ti consentono di ottimizzare la personalizzazione delle consegne. Per ulteriori informazioni, consulta [Definizione dei blocchi di personalizzazione personalizzati](#defining-custom-personalization-blocks).

>[!NOTE]
>
>I blocchi di personalizzazione sono disponibili anche da **[!UICONTROL Digital Content Editor (DCE)]** . Per ulteriori informazioni, consulta [questa pagina](../../web/using/editing-content.md#inserting-a-personalization-block).

## Inserimento di blocchi di personalizzazione {#inserting-personalization-blocks}

Per inserire un blocco di personalizzazione in un messaggio, segui i passaggi seguenti:

1. Nell’editor dei contenuti della procedura guidata di consegna, fai clic sull’icona del campo personalizzato e seleziona il menu **[!UICONTROL Include]** .
1. Seleziona un blocco di personalizzazione dall’elenco (l’elenco visualizza gli ultimi 10 blocchi utilizzati) oppure fai clic sul menu **[!UICONTROL Other...]** per accedere all’elenco completo.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Il menu **[!UICONTROL Other...]** consente di accedere a tutti i blocchi predefiniti e di personalizzazione personalizzata (consulta [Blocchi di personalizzazione preconfigurati](#out-of-the-box-personalization-blocks) e [Definizione dei blocchi di personalizzazione personalizzati](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Il blocco di personalizzazione viene quindi inserito come script. Viene automaticamente adattato al profilo del destinatario quando viene generata la personalizzazione.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Fai clic sulla scheda **[!UICONTROL Preview]** e seleziona un destinatario per visualizzare la personalizzazione.

   ![](assets/s_ncs_user_personalized_block04.png)

Puoi includere il codice sorgente di un blocco di personalizzazione nel contenuto della consegna. A questo scopo, seleziona **[!UICONTROL Include the HTML source code of the block]** quando lo selezioni.

![](assets/s_ncs_user_personalized_block05.png)

Il codice sorgente HTML viene inserito nel contenuto della consegna. Ad esempio, il blocco di personalizzazione **[!UICONTROL Greetings]** viene visualizzato come segue:

![](assets/s_ncs_user_personalized_block06.png)

## Esempio di blocchi di personalizzazione {#personalization-blocks-example}

In questo esempio, creiamo un’e-mail in cui utilizziamo blocchi di personalizzazione per consentire al destinatario di visualizzare la pagina speculare, condividere la newsletter sui social network e annullare l’iscrizione alle consegne future.

A questo scopo, è necessario inserire i seguenti blocchi di personalizzazione:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Per ulteriori informazioni sulla generazione della pagina speculare, consulta [Generazione della pagina speculare](sending-messages.md#generating-the-mirror-page).

1. Crea una nuova consegna o apri una consegna di tipo e-mail esistente.
1. Nella procedura guidata di consegna, fai clic su **[!UICONTROL Subject]** per modificare l’oggetto del messaggio e inserire un oggetto.
1. Inserisci i blocchi di personalizzazione nel corpo del messaggio. A questo scopo, fai clic sul contenuto del messaggio, fai clic sull’icona del campo personalizzato e seleziona il menu **[!UICONTROL Include]** .
1. Selezionare il primo blocco da inserire. Rinnova la procedura per includere gli altri due blocchi.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Fai clic sulla scheda **[!UICONTROL Preview]** per visualizzare il risultato della personalizzazione. Devi selezionare un destinatario per visualizzare il messaggio del destinatario.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Conferma che il contenuto del blocco sia visualizzato correttamente.

## Blocchi di personalizzazione preconfigurati {#out-of-the-box-personalization-blocks}

Per impostazione predefinita, è disponibile un elenco di blocchi di personalizzazione per consentirti di personalizzare il contenuto del messaggio.

>[!NOTE]
>
>L’elenco dei blocchi di personalizzazione dipende dai moduli e dalle opzioni installati nell’istanza.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : inserisce i saluti con il nome del destinatario. Esempio: &quot;Ciao John Doe.&quot;
* **[!UICONTROL Insert logo]** : inserisce un logo predefinito definito durante la configurazione dell’istanza.
* **[!UICONTROL Powered by Adobe Campaign]** : inserisce il logo &quot;Powered by Adobe Campaign&quot; (Alimentato da).
* **[!UICONTROL Mirror page URL]** : inserisce l’URL della pagina speculare, consentendo a Progettazione consegne di controllare il collegamento.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla generazione della pagina speculare, consulta [Generazione della pagina speculare](sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : inserisce un collegamento alla pagina speculare: &quot;Se non riesci a visualizzare correttamente questo messaggio, fai clic qui&quot;.
* **[!UICONTROL Unsubscription link]** : inserisce un collegamento che consente di annullare l’iscrizione a tutte le consegne (elenco Bloccati).
* **[!UICONTROL Formatting function for proper nouns]** : genera la funzione  **[!UICONTROL toSmartCase]** Javascript, che cambia la prima lettera di ogni parola in maiuscolo.
* **[!UICONTROL Registration page URL]** : inserisce un URL di abbonamento (consulta  [Informazioni su servizi e abbonamenti](about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : inserisce un collegamento di abbonamento. che è stato definito durante la configurazione dell’istanza.
* **[!UICONTROL Registration link (with referrer)]** : inserisce un collegamento di abbonamento, che consente di identificare il visitatore e la consegna. Il collegamento è stato definito durante la configurazione dell’istanza.

   >[!NOTE]
   >
   >Questo blocco può essere utilizzato solo nelle consegne che hanno come target i visitatori.

* **[!UICONTROL Registration confirmation]** : inserisce un collegamento che consente di confermare l’abbonamento.
* **[!UICONTROL Social network sharing links]** : inserisce dei pulsanti che consentono al destinatario di condividere un collegamento al contenuto della pagina speculare con il client e-mail, Facebook, Twitter e LinkedIn (consulta  [Marketing virale: inoltrare ad un amico](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** e  **[!UICONTROL Notification style]** : genera codice che formatta un’e-mail con stili HTML predefiniti. Questi blocchi devono essere inseriti nel codice sorgente della consegna, nella sezione **[!UICONTROL ...]**, nei tag **`<style>...</style>`** .
* **[!UICONTROL Offer acceptance URL in unitary mode]** : inserisce un URL che consente di impostare un’offerta di interazione su  **[!UICONTROL Accepted]** (consulta  [questa sezione](../../interaction/using/offer-analysis-report.md)).

## Definizione dei blocchi di personalizzazione personalizzati {#defining-custom-personalization-blocks}

Puoi definire nuovi campi di personalizzazione da inserire dall’icona del campo personalizzato tramite il menu **[!UICONTROL Include...]** . Questi campi sono definiti nei blocchi di personalizzazione.

Per creare un blocco di personalizzazione, passa a explorer e applica i seguenti passaggi:

1. Fai clic sul nodo **[!UICONTROL Resources > Campaign Management > Personalization blocks]** .
1. Fai clic con il pulsante destro del mouse sull’elenco dei blocchi e seleziona **[!UICONTROL New]** .
1. Compila le impostazioni del blocco di personalizzazione:

   ![](assets/s_ncs_user_personalized_block.png)

   * Inserisci l’etichetta del blocco. Questa etichetta verrà visualizzata nella finestra di inserimento del campo di personalizzazione.
   * Seleziona **[!UICONTROL Visible in the customization menus]** per rendere questo blocco accessibile dall’icona di inserimento del campo di personalizzazione.
   * Se necessario, seleziona **[!UICONTROL The content of the personalization block depends upon the format]** per definire due blocchi separati per le e-mail in formato HTML e per quelle in formato testo.

      Nella sezione inferiore di questo editor (contenuto HTML e contenuto di testo) sono quindi visualizzate due schede per definire il contenuto corrispondente.

      ![](assets/s_ncs_user_personalized_block_b.png)

   * Immetti il contenuto (in HTML, testo, JavaScript, ecc.) dei blocchi di personalizzazione e fai clic su **[!UICONTROL Save]**.

## Video tutorial {#personalization-blocks-video}

Scopri come creare blocchi di contenuto dinamici e come utilizzarli per personalizzare il contenuto della consegna e-mail.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
