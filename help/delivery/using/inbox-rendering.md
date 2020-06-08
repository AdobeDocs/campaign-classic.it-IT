---
title: Rendering in entrata
seo-title: Rendering in entrata
description: Rendering in entrata
seo-description: null
page-status-flag: never-activated
uuid: 2025f5e9-8a19-407c-9e0a-378ba5a76208
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: deliverability-management
discoiquuid: 72e974b8-415a-47ab-9804-b15957787198
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: aef56860d6e4558a7f4833066ab3d83733591522
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 0%

---


# Rendering in entrata{#inbox-rendering}

## Il rendering in inbox {#about-inbox-rendering}

Prima di premere il pulsante **Invia** , accertatevi che il messaggio venga visualizzato ai destinatari in modo ottimale su diversi client Web, e-mail e dispositivi.

A tal fine, Adobe Campaign sfrutta la soluzione di verifica e-mail basata sul [Web Litmus](https://litmus.com/email-testing) per acquisire i rendering e renderli disponibili in un rapporto dedicato. Questo consente di visualizzare l&#39;anteprima del messaggio inviato nei diversi contesti in cui potrebbe essere ricevuto e di verificare la compatibilità nei principali desktop e applicazioni.

Litmus è un&#39;applicazione di convalida e anteprima delle e-mail ricca di funzioni. Consente agli autori dei contenuti e-mail di visualizzare in anteprima il contenuto del messaggio in oltre 70 renderer di posta elettronica, ad esempio la inbox Gmail o il client Apple Mail.

I client per dispositivi mobili, messaggi e webmail disponibili per il rendering **della** inbox in Adobe Campaign sono elencati nel sito Web [di](https://litmus.com/email-testing) Litmus (fate clic su **Visualizza tutti i client** e-mail).

>[!NOTE]
>
>Il rendering della inbox non è necessario per testare la personalizzazione nelle consegne. La personalizzazione può essere verificata con gli strumenti di Adobe Campaign come **[!UICONTROL Preview]** e [le prove](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

## Attivazione del rendering in entrata {#activating-inbox-rendering}

Per i client ospitati e ibridi, il rendering in entrata è configurato nell’istanza dal supporto tecnico e dai consulenti Adobe. Per ulteriori informazioni, contattate il vostro responsabile commerciale di Adobe.

Per le installazioni locali, seguite i passaggi descritti di seguito per configurare il rendering Inbox.

1. Installate il **[!UICONTROL Inbox rendering (IR)]** pacchetto dal **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Per ulteriori informazioni, consulta [Installazione dei pacchetti](../../installation/using/installing-campaign-standard-packages.md)standard di Campaign Classic.
1. Configurate un account esterno del tipo HTTP tramite il nodo **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** . Per ulteriori informazioni, consultate [Creazione di un account](../../platform/using/external-accounts.md#creating-an-external-account)esterno.
1. Impostate i parametri del conto esterno come segue:
   * **[!UICONTROL Label]**: Informazioni sul server di distribuzione
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: None
   * Selezionare l&#39; **[!UICONTROL Enabled]** opzione.
   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Vai al **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** nodo. Cercate l&#39; **[!UICONTROL DmRendering_cuid]** opzione e contattate il supporto per ottenere l&#39;identificatore dei rapporti di consegna che deve essere copiato nel **[!UICONTROL Value (text)]** campo.
1. Modificate il file **serverConf.xml** per consentire una chiamata al server Litmus. Aggiungere la riga seguente alla `<urlPermission>` sezione:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Ricarica la configurazione con il seguente comando:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Potrebbe essere necessario disconnettersi dalla console ed eseguire nuovamente l&#39;accesso per poter utilizzare il rendering Inbox.

## Informazioni sui token Litmus {#about-litmus-tokens}

Poiché Litmus è un servizio di terze parti, funziona su un modello di credito per uso. Ogni volta che un utente chiama la funzionalità Litmus, il credito viene detratto.

In Adobe Campaign, il credito corrisponde al numero di rendering disponibili (denominati token).

>[!NOTE]
>
>Il numero di token Litmus disponibili dipende dalla licenza Campaign acquistata. Controlla il contratto di licenza.

Ogni volta che utilizzate la **[!UICONTROL Inbox rendering]** funzione in una distribuzione, ogni rendering generato diminuisce di uno i token disponibili.

>[!IMPORTANT]
>
>Account Token per ogni singolo rendering e non per l&#39;intero rapporto di rendering Inbox, il che significa che:
>
>* Ogni volta che viene generato il rapporto di rendering Inbox, viene detratto un token per client di messaggistica: un token per il rendering di Outlook 2000, uno per il rendering di Outlook 2010, uno per il rendering di Apple Mail 9 e così via.
>* Per la stessa consegna, se generate di nuovo il rendering in entrata, il numero di token disponibili viene nuovamente diminuito in base al numero di rendering generati.
>



Il numero di token rimanenti disponibili viene visualizzato nel rapporto **[!UICONTROL General summary]** [di rendering](#inbox-rendering-report)Inbox.

![](assets/s_tn_inbox_rendering_tokens.png)

In genere, la funzione di rendering Inbox viene utilizzata per testare il framework HTML di un messaggio e-mail di nuova progettazione. Ciascun rendering richiede circa 70 token (a seconda del numero di ambienti generalmente testati). Tuttavia, in alcuni casi potrebbe essere necessario disporre di più rapporti di rendering per verificare completamente la consegna. Potrebbero quindi essere necessari più token per completare diversi controlli.

## Accesso al rapporto di rendering della inbox {#accessing-the-inbox-rendering-report}

Dopo aver creato la consegna dell’e-mail e definito il contenuto e la popolazione di destinazione, effettuate le seguenti operazioni.

Per ulteriori informazioni sulla creazione, la progettazione e il targeting di una consegna, consulta [questa sezione](../../delivery/using/about-email-channel.md).

1. Nella barra superiore della consegna, fate clic sul **[!UICONTROL Inbox rendering]** pulsante.
1. Selezionate **[!UICONTROL Analyze]** per avviare il processo di acquisizione.

   ![](assets/s_tn_inbox_rendering_button.png)

   Viene inviata una prova. Le miniature di rendering sono accessibili solo alcuni minuti dopo l’invio delle e-mail. For more on sending proofs, refer to [this section](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof).

1. Dopo l&#39;invio, la prova viene visualizzata nell&#39;elenco di consegna. Fate doppio clic su di esso.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Passate alla scheda Rendering **della** casella in entrata della prova.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Viene visualizzato il rapporto di rendering Inbox.

## Report rendering in entrata {#inbox-rendering-report}

Questo rapporto visualizza i rendering della inbox così come appaiono al destinatario. I rendering possono essere diversi a seconda del modo in cui il destinatario apre la consegna dell&#39;e-mail: in un browser, su un dispositivo mobile o tramite un&#39;applicazione e-mail.

Il **[!UICONTROL General summary]** numero di messaggi ricevuti, indesiderati (spam), non ricevuti o in attesa di ricezione viene presentato come elenco e attraverso una rappresentazione grafica con colori codificati.

![](assets/s_tn_inbox_rendering_summary.png)

Passate il mouse sul grafico per visualizzare i dettagli di ciascun colore.

Il contenuto della relazione è diviso in tre parti: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** e **[!UICONTROL Webmails]**. Scorrete il rapporto verso il basso per visualizzare tutti i rendering raggruppati in queste tre categorie.

![](assets/s_tn_inbox_rendering_report.png)

Per ottenere i dettagli per ciascun rapporto, fate clic sulla scheda corrispondente. Il rendering viene visualizzato per il metodo di ricezione selezionato.

![](assets/s_tn_inbox_rendering_example.png)
