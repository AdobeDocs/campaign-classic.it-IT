---
product: campaign
title: Blocchi di personalizzazione
description: Scopri come utilizzare i blocchi di personalizzazione
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Personalization
role: User
exl-id: 8d155844-d18a-4165-9886-c3b144109f6e
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 5%

---

# Blocchi di personalizzazione{#personalization-blocks}

I blocchi di personalizzazione sono dinamici, personalizzati e contengono un rendering specifico che puoi inserire nelle consegne. Ad esempio, puoi aggiungere un logo, un messaggio di auguri o un collegamento alla pagina mirror. Consulta [Inserire blocchi di personalizzazione](#inserting-personalization-blocks).

![](assets/do-not-localize/how-to-video.png)[ Scopri questa funzione nel video](#personalization-blocks-video)

I blocchi di personalizzazione sono accessibili tramite **[!UICONTROL Resources > Campaign Management > Personalization blocks]** nodo di Adobe Campaign explorer. Per impostazione predefinita sono disponibili diversi blocchi (vedi [Blocchi di personalizzazione predefiniti](#out-of-the-box-personalization-blocks)).

Puoi definire nuovi blocchi per ottimizzare la personalizzazione delle consegne. Per ulteriori informazioni, consulta [Definire i blocchi di personalizzazione personalizzati](#defining-custom-personalization-blocks).

>[!NOTE]
>
>I blocchi di personalizzazione sono disponibili anche dal **[!UICONTROL Digital Content Editor (DCE)]** . Per ulteriori informazioni, consulta [questa pagina](../../web/using/editing-content.md#inserting-a-personalization-block).

## Inserire blocchi di personalizzazione {#inserting-personalization-blocks}

Per inserire un blocco di personalizzazione in un messaggio, effettua le seguenti operazioni:

1. Nell’editor dei contenuti della consegna guidata, fai clic sull’icona del campo personalizzato e seleziona la **[!UICONTROL Include]** menu.
1. Seleziona un blocco di personalizzazione dall’elenco (l’elenco mostra gli ultimi 10 blocchi utilizzati), oppure fai clic su **[!UICONTROL Other...]** per accedere all’elenco completo.

   ![](assets/s_ncs_user_personalized_block01.png)

1. Il **[!UICONTROL Other...]** offre l’accesso a tutti i blocchi di personalizzazione predefiniti e personalizzati (consulta [Blocchi di personalizzazione predefiniti](#out-of-the-box-personalization-blocks) e [Definire i blocchi di personalizzazione personalizzati](#defining-custom-personalization-blocks)).

   ![](assets/s_ncs_user_personalized_block02.png)

1. Il blocco di personalizzazione viene quindi inserito come script. Viene adattato automaticamente al profilo del destinatario quando viene generata la personalizzazione.

   ![](assets/s_ncs_user_personalized_block03.png)

1. Fai clic su **[!UICONTROL Preview]** e seleziona un destinatario per visualizzare la personalizzazione.

   ![](assets/s_ncs_user_personalized_block04.png)

Puoi includere il codice sorgente di un blocco di personalizzazione nel contenuto della consegna. A questo scopo, seleziona **[!UICONTROL Include the HTML source code of the block]** quando la selezioni.

![](assets/s_ncs_user_personalized_block05.png)

Il codice sorgente HTML viene inserito nel contenuto della consegna. Ad esempio, il **[!UICONTROL Greetings]** il blocco di personalizzazione viene visualizzato come segue:

![](assets/s_ncs_user_personalized_block06.png)

## Esempio di blocchi di personalizzazione {#personalization-blocks-example}

In questo esempio, creiamo un’e-mail in cui utilizziamo blocchi di personalizzazione per consentire al destinatario di visualizzare la pagina speculare, condividere la newsletter sui social network e annullare l’abbonamento a consegne future.

A questo scopo, è necessario inserire i seguenti blocchi di personalizzazione:

* **[!UICONTROL Link to mirror page]** .
* **[!UICONTROL Social network sharing links]** .
* **[!UICONTROL Unsubscription link]** .

>[!NOTE]
>
>Per ulteriori informazioni sulla generazione della pagina speculare, consulta [Genera la pagina mirror](sending-messages.md#generating-the-mirror-page).

1. Crea una nuova consegna o apri una consegna di tipo e-mail esistente.
1. Nella consegna guidata, fai clic su **[!UICONTROL Subject]** per modificare l&#39;oggetto del messaggio e immettere un oggetto.
1. Inserisci i blocchi di personalizzazione nel corpo del messaggio. A questo scopo, fai clic sul contenuto del messaggio, fai clic sull’icona del campo personalizzato e seleziona la **[!UICONTROL Include]** menu.
1. Selezionare il primo blocco da inserire. Rinnovare la procedura per includere gli altri due blocchi.

   ![](assets/s_ncs_user_personalized_block_example.png)

1. Fai clic su **[!UICONTROL Preview]** per visualizzare il risultato della personalizzazione. È necessario selezionare un destinatario per visualizzarne il messaggio.

   ![](assets/s_ncs_user_personalized_block_example2.png)

1. Verifica che il contenuto del blocco sia visualizzato correttamente.

## Blocchi di personalizzazione predefiniti {#out-of-the-box-personalization-blocks}

Per impostazione predefinita, è disponibile un elenco di blocchi di personalizzazione che consentono di personalizzare il contenuto del messaggio.

>[!NOTE]
>
>L’elenco dei blocchi di personalizzazione dipende dai moduli e dalle opzioni installati nell’istanza.

![](assets/s_ncs_user_personalized_block_list.png)

* **[!UICONTROL Greetings]** : inserisce i saluti con il nome del destinatario. Esempio: “Ciao John Doe,” 
* **[!UICONTROL Insert logo]** : inserisce un logo predefinito definito durante la configurazione dell’istanza.
* **[!UICONTROL Powered by Adobe Campaign]** : inserisce il logo &quot;Powered by Adobe Campaign&quot;.
* **[!UICONTROL Mirror page URL]** : inserisce l’URL della pagina speculare, consentendo ai designer della consegna di controllare il collegamento.

  >[!NOTE]
  >
  >Per ulteriori informazioni sulla generazione della pagina speculare, consulta [Genera la pagina mirror](sending-messages.md#generating-the-mirror-page).

* **[!UICONTROL Link to mirror page]** : inserisce un collegamento alla pagina speculare: &quot;Se non riesci a visualizzare correttamente questo messaggio, fai clic qui&quot;.
* **[!UICONTROL Unsubscription link]** : inserisce un collegamento che consente di annullare l’abbonamento a tutte le consegne (inserisco nell&#39;elenco Bloccati di annullamento dell’abbonamento).
* **[!UICONTROL Formatting function for proper nouns]** : genera il **[!UICONTROL toSmartCase]** Funzione JavaScript, che trasforma la prima lettera di ogni parola in maiuscolo.
* **[!UICONTROL Registration page URL]** : inserisce un URL di abbonamento (consulta [Informazioni su servizi e abbonamenti](about-services-and-subscriptions.md)).
* **[!UICONTROL Registration link]** : inserisce un collegamento di abbonamento. che è stato definito durante la configurazione dell’istanza.
* **[!UICONTROL Registration link (with referrer)]** : inserisce un collegamento di abbonamento, che consente di identificare il visitatore e la consegna. Il collegamento è stato definito durante la configurazione dell’istanza.

  >[!NOTE]
  >
  >Questo blocco può essere utilizzato nelle consegne indirizzate solo ai visitatori.

* **[!UICONTROL Registration confirmation]** : inserisce un collegamento che consente di confermare la sottoscrizione.
* **[!UICONTROL Social network sharing links]** : inserisce pulsanti che consentono al destinatario di condividere un collegamento al contenuto della pagina speculare con il client e-mail, il Facebook, il Twitter e il LinkedIn (consulta [Marketing virale: inoltro a un amico](viral-and-social-marketing.md#viral-marketing--forward-to-a-friend)).
* **[!UICONTROL Style of content emails]** e **[!UICONTROL Notification style]** : genera un codice che formatta un’e-mail con stili HTML predefiniti. Questi blocchi devono essere inseriti nel codice sorgente della consegna, nel **[!UICONTROL ...]** sezione, in **`<style>...</style>`** tag.
* **[!UICONTROL Offer acceptance URL in unitary mode]** : inserisce un URL che consente di impostare un’offerta di interazione su **[!UICONTROL Accepted]** (vedere [questa sezione](../../interaction/using/offer-analysis-report.md)).

## Definire i blocchi di personalizzazione personalizzati {#defining-custom-personalization-blocks}

Puoi definire nuovi campi di personalizzazione da inserire dall’icona del campo personalizzato tramite **[!UICONTROL Include...]** menu. Questi campi sono definiti in blocchi di personalizzazione.

Per creare un blocco di personalizzazione, passa a Esplora e applica i seguenti passaggi:

1. Fai clic su **[!UICONTROL Resources > Campaign Management > Personalization blocks]** nodo.
1. Fai clic con il pulsante destro del mouse sull’elenco dei blocchi e seleziona (Aggiungi blocco) **[!UICONTROL New]** .
1. Compila le impostazioni del blocco di personalizzazione:

   ![](assets/s_ncs_user_personalized_block.png)

   * Inserisci l’etichetta del blocco. Questa etichetta verrà visualizzata nella finestra di inserimento del campo di personalizzazione.
   * Seleziona **[!UICONTROL Visible in the customization menus]** per rendere accessibile questo blocco dall’icona di inserimento del campo di personalizzazione.
   * Se necessario, selezionare **[!UICONTROL The content of the personalization block depends upon the format]** per definire due blocchi separati per le e-mail in formato HTML e quelli in formato testo.

     Nella sezione inferiore di questo editor (Contenuto HTML e Contenuto testo) vengono quindi visualizzate due schede per definire il contenuto corrispondente.

     ![](assets/s_ncs_user_personalized_block_b.png)

   * Inserisci il contenuto (in HTML, testo, JavaScript, ecc.) dei blocchi di personalizzazione e fai clic su **[!UICONTROL Save]**.

## Video tutorial {#personalization-blocks-video}

Scopri come creare blocchi di contenuto dinamici e come utilizzarli per personalizzare il contenuto della consegna e-mail.

>[!VIDEO](https://video.tv.adobe.com/v/24924?quality=12)

Sono disponibili altri video dimostrativi sui Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
