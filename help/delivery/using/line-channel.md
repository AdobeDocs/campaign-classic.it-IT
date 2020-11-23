---
solution: Campaign Classic
product: campaign
title: Canale LINE
description: Canale LINE
audience: delivery
content-type: reference
topic-tags: sending-messages-on-mobiles
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1100'
ht-degree: 3%

---


# Canale LINE{#line-channel}

LINE è un&#39;applicazione per la messaggistica istantanea gratuita, chiamate vocali e video, disponibile su tutti gli smartphone (iPhone, Android, Windows Phone, Blackberry, Nokia) e su PC.  Adobe Campaign consente di inviare messaggi LINE.

LINE è disponibile solo per le installazioni di servizi locali o gestiti.

LINE può anche essere combinato con il modulo di messaggi transazionali per inviare messaggi in tempo reale sull&#39;app LINE installata nei dispositivi mobili consumer. Per ulteriori informazioni, consulta questa [pagina](../../message-center/using/transactional-messaging-architecture.md#transactional-messaging-and-line).

![](assets/line_message.png)

Le sezioni seguenti forniscono informazioni specifiche per il canale LINE. Per informazioni globali su come creare una consegna, consulta[questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md).

I passaggi per utilizzare il canale LINE sono:

1. Creazione di una consegna
1. Configurazione del contenuto del messaggio
1. Selezione della popolazione di destinazione
1. Invio dei messaggi
1. Monitoraggio della consegna (tracciamento, quarantena, rapporti ecc.).

## Impostazione del canale LINE {#setting-up-line-channel}

### Creazione di un account LINE e di un account esterno {#creating-a-line-account-and-an-external-account-}

>[!NOTE]
>
>Prima di creare un account LINE e un account esterno, è necessario installare il pacchetto LINE sull&#39;istanza. Per ulteriori informazioni, consulta la sezione [LINE](../../installation/using/installing-campaign-standard-packages.md#line-package) nella guida all’installazione.

È innanzitutto necessario creare un account LINE, in modo da collegarlo a  Adobe Campaign. Quindi, puoi inviare messaggi LINE agli utenti che hanno aggiunto il tuo account LINE nella loro applicazione mobile. Gli account esterni e gli account LINE possono essere gestiti solo dall&#39;amministratore funzionale della piattaforma.

Per creare e configurare un account LINE, vedi [https://developers.line.me/](https://developers.line.me/).

Per creare e configurare un servizio LINE, consulta [Gestione delle sottoscrizioni](../../delivery/using/managing-subscriptions.md).

![](assets/line_service.png)

Infine, per creare un account esterno su  Adobe Campaign:

1. Nella struttura ad albero **Amministrazione** > **Piattaforma** , fate clic sulla scheda Account **** esterni.
1. Fate clic sull’icona **Nuovo** .

   ![](assets/line_config.png)

1. Completare i campi **Etichetta** e Nome **** interno.
1. Nel **[!UICONTROL Type]** campo selezionare Routing e nel campo **Canale** selezionare LINE.
1. Fare clic **[!UICONTROL Save]** per creare il proprio account esterno LINE.
1. Un campo di personalizzazione **LINE** viene visualizzato sotto l&#39;icona **Generale** e compila i campi seguenti:

   ![](assets/line_config_2.png)

   * **Alias** canale: viene fornito tramite il tuo account LINE nella scheda **[!UICONTROL Channels]** > **[!UICONTROL Technical configuration]** .
   * **ID** canale: viene fornito tramite il vostro account LINE nella scheda **Canali** > Informazioni di **base del pannello** .
   * **Chiave** segreta canale: viene fornito tramite il vostro account LINE nella scheda **Canali** > Informazioni di **base del pannello** .
   * **Token** di accesso: viene fornito tramite il vostro account LINE nel portale per sviluppatori o facendo clic sul **[!UICONTROL Get access token]** pulsante.
   * **Data** di scadenza token di accesso: consente di specificare la data di scadenza del token di accesso.
   * **Servizio** di iscrizione LINE: consente di specificare i servizi ai quali gli utenti verranno sottoscritti.

>[!NOTE]
>
>È necessario verificare che i flussi di lavoro **[!UICONTROL LINE access token update (updateLineAccessToken)]** e quelli **[!UICONTROL Delete blocked LINE users (deleteBlockedLineUsers)]** siano iniziati. In Esplora risorse, fate clic **[!UICONTROL Administration > Production > Technical workflows > LINE workflows]** per verificare lo stato dei flussi di lavoro.

## Creazione della consegna {#creating-the-delivery}

Per creare una consegna **LINE** è necessario eseguire la procedura seguente:

>[!NOTE]
>
>In [questa sezione](../../delivery/using/steps-about-delivery-creation-steps.md)vengono illustrati i concetti globali relativi alla creazione dei contenuti.

1. Dalla **[!UICONTROL Campaigns]** scheda, selezionare **[!UICONTROL Deliveries]** quindi fare clic sul **[!UICONTROL Create]** pulsante.
1. Nella finestra visualizzata, selezionate il modello di **[!UICONTROL LINE V2 delivery]** consegna.

   ![](assets/line_message_01.png)

1. Identifica la consegna con un&#39;etichetta, un codice e una descrizione. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/steps-create-and-identify-the-delivery.md#identifying-the-delivery).
1. Fate clic **[!UICONTROL Continue]** per creare la consegna.

## Definizione del contenuto {#defining-the-content}

Per definire il contenuto di una consegna LINE, devi prima aggiungere il tipo di messaggio alla consegna. Ogni consegna LINE può contenere fino a 5 messaggi.

Puoi scegliere tra due tipi di messaggi:

* Messaggio di testo
* Immagine e collegamento

### Configurazione della consegna di un messaggio di testo {#configuring-a-text-message-delivery}

Un messaggio **di testo** Consegna linea è un messaggio inviato ai destinatari in forma di testo.

![](assets/line_message_02.png)

La configurazione di questo tipo di messaggio è simile alla configurazione del **testo** in un messaggio e-mail. For more information, refer to this [page](../../delivery/using/defining-the-email-content.md#message-content).

### Configurazione della distribuzione di un’immagine e collegamento {#configuring-an-image-and-link-delivery}

Per **Immagine e linea di collegamento** si intende un messaggio inviato ai destinatari sotto forma di immagine che può contenere uno o più URL.

È possibile utilizzare:

* un&#39;immagine **** personalizzata,

   >[!NOTE]
   >
   >È possibile utilizzare la variabile **%SIZE%** : questa variabile consente di ottimizzare la visualizzazione delle immagini in base alle dimensioni dello schermo del dispositivo mobile del destinatario.

   ![](assets/line_message_04.png)

* un URL **** immagine,

   ![](assets/line_message_03.png)

   Gli URL immagine consentono di usare diverse risoluzioni immagine per ottimizzare la visibilità della distribuzione sui dispositivi mobili. Sono supportate solo le immagini con la stessa altezza e larghezza.

   Le immagini possono essere definite in base alle dimensioni dello schermo:

   * 1040px
   * 700px
   * 460px
   * 300px
   * 240px

   >[!NOTE]
   >
   >La dimensione 1040x1040 px è obbligatoria per ogni immagine LINE con collegamento.

   È quindi necessario aggiungere del testo alternativo che verrà visualizzato sul dispositivo mobile del destinatario.

* e **[!UICONTROL Links]**.

   ![](assets/line_message_05.png)

   La **[!UICONTROL Links]** sezione consente di scegliere tra diversi layout che dividono l’immagine in più aree selezionabili. Potete quindi assegnare a ciascuno di essi un collegamento dedicato.

>[!NOTE]
>
>La sintassi &lt;%@ include option=&#39;NmsServer_URL&#39; %>/webApp/APP3?id=&lt;%=escapeUrl(cryptString(visitor.id))%> consente di includere in un messaggio LINE un collegamento a un&#39;app Web.

### Raccomandazioni {#recommendations}

* Quando si invia una consegna LINE a un nuovo destinatario per la prima volta, è necessario aggiungere il messaggio LINE ufficiale relativo ai termini di utilizzo e consenso alla consegna. Il messaggio ufficiale è disponibile al seguente link: [https://terms.line.me/OA_privacy/](https://terms.line.me/OA_privacy/sp?lang=fr).

## Selezione della popolazione di destinazione {#selecting-the-target-population}

La selezione dei destinatari di una consegna LINE è simile alla definizione dei destinatari della consegna tramite e-mail. Per ulteriori informazioni, vedere [Identificazione delle popolazioni](../../delivery/using/steps-defining-the-target-population.md)di destinazione.

Il targeting viene eseguito sui **visitatori**.

## Invio di messaggi {#sending-messages}

Quando la consegna viene creata e configurata correttamente, potete inviarla alla destinazione definita in precedenza.

L&#39;invio di consegne LINE è simile all&#39;invio di un&#39;e-mail. Per ulteriori informazioni sull&#39;invio di una consegna, vedere [Invio di messaggi](../../delivery/using/sending-messages.md).

## Accesso ai rapporti {#accessing-reports}

Per visualizzare i rapporti sul servizio LINE, fai clic su **[!UICONTROL Profiles and Targets > Services and Subscriptions > LINE]** in Esplora risorse. Fate clic sull&#39; **[!UICONTROL Reports]** icona nel servizio LINE.

![](assets/line_reports.png)

Per visualizzare i rapporti sulle consegne LINE, fai clic **[!UICONTROL Campaign Management > Deliveries]** quindi sulla consegna desiderata. I rapporti di tracciamento indicano la frequenza di click-through. LINE non tiene conto della tariffa aperta.

![](assets/line_reports_01.png)

## Esempio: creazione e invio di un messaggio LINE personalizzato {#example--create-and-send-a-personalized-line-message}

In questo esempio, creeremo e configureremo un messaggio di testo e un&#39;immagine contenente dati che verranno personalizzati in base al destinatario.

1. Crea la consegna LINE facendo clic sul **[!UICONTROL Create]** pulsante dalla **[!UICONTROL Campaign]** scheda.

   ![](assets/line_usecase.png)

1. Selezionate il modello di **[!UICONTROL LINE V2 delivery]** consegna e assegnate un nome alla consegna.

   ![](assets/line_usecase_01.png)

1. Nella finestra di configurazione della consegna, selezionate la popolazione di destinazione.

   ![](assets/line_usecase_02.png)

1. Fai clic **[!UICONTROL Add]** per creare il messaggio e seleziona il **[!UICONTROL Message type]**.

   In questo caso, prima di tutto desideriamo creare un messaggio di testo.

   ![](assets/line_usecase_03.png)

1. Posizionare il cursore nel punto in cui si desidera inserire il testo personalizzato e fare clic sull&#39;icona a discesa, quindi selezionare **[!UICONTROL Visitor > First name]**.

   ![](assets/line_usecase_05.png)

1. Seguite la stessa procedura per aggiungere un’immagine, selezionandola **[!UICONTROL Image and links]** nell’ **[!UICONTROL Message type]** elenco a discesa.

   Aggiungete l’URL dell’immagine.

   ![](assets/line_usecase_07.png)

1. Nella **[!UICONTROL Links]** sezione, selezionate il layout che consente di dividere l’immagine in più aree selezionabili.
1. Assegnate un URL a ciascuna area dell’immagine.

   ![](assets/line_usecase_08.png)

1. Salva la consegna, quindi fai clic **[!UICONTROL Send]** per analizzarla e inviarla alla destinazione.

   La consegna viene inviata alla destinazione.

   ![](assets/line_usecase_06.png)
