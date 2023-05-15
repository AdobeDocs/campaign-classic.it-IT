---
product: campaign
title: Rendering della casella in entrata in Campaign
description: Scopri come acquisire i rendering delle e-mail e renderli disponibili in un rapporto dedicato
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
source-git-commit: e011333411af79b985166a4e73592a1860749cf1
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 9%

---

# Rendering della casella in entrata{#inbox-rendering}



## Informazioni sul rendering della casella in entrata {#about-inbox-rendering}

Prima di premere il pulsante **Invia** assicurati che il messaggio venga visualizzato ai destinatari in modo ottimale su diversi client web, e-mail e dispositivi web.

Per questo motivo, Adobe Campaign sfrutta la funzione [Litmo](https://litmus.com/email-testing) soluzione di test e-mail basata su web per acquisire i rendering e renderli disponibili in un rapporto dedicato. Questo consente di visualizzare in anteprima il messaggio inviato nei diversi contesti in cui potrebbe essere ricevuto e di verificare la compatibilità nei principali desktop e applicazioni.

>[!CAUTION]
>Il rendering della casella in entrata non è compatibile con [consegne ricorrenti](communication-channels.md#recurring-delivery).

Litmus è un&#39;applicazione che offre funzioni avanzate di convalida e-mail e visualizzazione dell&#39;anteprima. Consente ai creatori di contenuti e-mail di visualizzare in anteprima il contenuto del messaggio in oltre 70 moduli di rendering e-mail, ad esempio la inbox Gmail o il client Apple Mail.

Client per dispositivi mobili, di messaggistica e di posta sul web disponibili per **Rendering della casella in entrata** in Adobe Campaign sono elencati nella [Sito web Litmus](https://litmus.com/email-testing) (fai clic su **Visualizza tutti i client e-mail**).

>[!NOTE]
>
>Il rendering della casella in entrata non è necessario per testare la personalizzazione nelle consegne. La personalizzazione può essere controllata con strumenti Adobe Campaign come **[!UICONTROL Preview]** e [Bozze](steps-validating-the-delivery.md#sending-a-proof).

## Attivazione del rendering della casella in entrata {#activating-inbox-rendering}

[!BADGE On-Premise e ibrida]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=it" tooltip="Si applica solo alle distribuzioni on-premise e ibride"}

Per i client in hosting e ibridi, il rendering della casella in entrata è configurato sulla tua istanza da parte del supporto tecnico e dei consulenti Adobe. Per ulteriori informazioni, contatta il tuo Adobe Account Executive.

Per le installazioni on-premise, segui la procedura seguente per configurare il rendering della casella in entrata.

1. Installa il **[!UICONTROL Inbox rendering (IR)]** tramite **[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]** menu. Per ulteriori informazioni, consulta [Installazione dei pacchetti standard di Campaign Classic](../../installation/using/installing-campaign-standard-packages.md).
1. Configura un account esterno del tipo HTTP tramite il **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]** nodo. Per ulteriori informazioni, consulta [Creazione di un account esterno](../../installation/using/external-accounts.md#creating-an-external-account).
1. Imposta i parametri dell’account esterno come segue:
   * **[!UICONTROL Label]**: Informazioni sul server di recapito messaggi
   * **[!UICONTROL Internal name]**: deliverabilityInstance
   * **[!UICONTROL Type]**: HTTP
   * **[!UICONTROL Server]**: https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**: Nessuna
   * Seleziona l’opzione **[!UICONTROL Enabled]**.

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. Vai a **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]** nodo. Cerca il **[!UICONTROL DmRendering_cuid]** e contatta il supporto per ottenere l’identificatore dei report di consegna che deve essere copiato in **[!UICONTROL Value (text)]** campo .
1. Modifica le **serverConf.xml** per consentire una chiamata al server Litmus. Aggiungi la seguente riga al `<urlPermission>` sezione:

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. Ricarica la configurazione utilizzando il seguente comando:

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>Potrebbe essere necessario disconnettersi dalla console ed effettuare nuovamente l’accesso per poter utilizzare il rendering della casella in entrata.

## Informazioni sui token Litmus {#about-litmus-tokens}

Poiché Litmus è un servizio di terze parti, funziona su un modello di credito per uso. Ogni volta che un utente chiama la funzionalità Litmus, il credito viene detratto.

In Adobe Campaign, il credito corrisponde al numero di rendering disponibili (noti come token).

>[!NOTE]
>
>Il numero di token Litmus disponibili dipende dalla licenza Campaign acquistata. Controlla il tuo contratto di licenza.

Ogni volta che utilizzi **[!UICONTROL Inbox rendering]** in una consegna, ogni rendering generato diminuisce di un’unità i token disponibili.

>[!IMPORTANT]
>
>I token tengono conto di ogni singolo rendering e non dell’intero rapporto di rendering della casella in entrata, il che significa che:
>
>* Ogni volta che viene generato il rapporto di rendering della casella in entrata, viene detratto un token per client di messaggistica: un token per il rendering di Outlook 2000, uno per il rendering di Outlook 2010, uno per il rendering di Apple Mail 9 e così via.
>* Per la stessa consegna, se si genera nuovamente il rendering della casella in entrata, il numero di token disponibili viene nuovamente diminuito del numero di rendering generati.
>


Il numero di token disponibili rimanenti viene visualizzato nella variabile **[!UICONTROL General summary]** del [Casella in entrata - Rapporto di rendering](#inbox-rendering-report).

![](assets/s_tn_inbox_rendering_tokens.png)

In genere, la funzione di rendering della casella in entrata viene utilizzata per testare il framework HTML di un messaggio e-mail di nuova progettazione. Ogni rendering richiede circa 70 token (a seconda del numero di ambienti generalmente testati). Tuttavia, in alcuni casi potrebbe essere necessario disporre di più rapporti di rendering della casella in entrata per testare completamente la consegna. Potrebbero quindi essere necessari più token per completare diversi controlli.

## Accesso al report di rendering della casella in entrata {#accessing-the-inbox-rendering-report}

Dopo aver creato la consegna e-mail e averne definito il contenuto e la popolazione target, effettua le seguenti operazioni.

Per ulteriori informazioni sulla creazione, la progettazione e il targeting di una consegna, consulta [questa sezione](about-email-channel.md).

1. Nella barra superiore della consegna, fai clic sul pulsante **[!UICONTROL Inbox rendering]** pulsante .
1. Seleziona **[!UICONTROL Analyze]** per avviare il processo di acquisizione.

   ![](assets/s_tn_inbox_rendering_button.png)

   Viene inviata una prova. Le miniature di rendering sono accessibili in tale bozza pochi minuti dopo l’invio delle e-mail. Per ulteriori informazioni sull’invio delle bozze, consulta [questa sezione](steps-validating-the-delivery.md#sending-a-proof).

1. Dopo l’invio, la bozza viene visualizzata nell’elenco di consegna. Fai doppio clic su di esso.

   ![](assets/s_tn_inbox_rendering_delivery_list.png)

1. Vai a **Rendering della casella in entrata** scheda della bozza.

   ![](assets/s_tn_inbox_rendering_tab.png)

   Viene visualizzato il rapporto di rendering della casella in entrata.

## Casella in entrata - Rapporto di rendering {#inbox-rendering-report}

Questo rapporto visualizza i rendering della casella in entrata così come vengono visualizzati al destinatario. I rendering possono variare a seconda della modalità di apertura della consegna e-mail da parte del destinatario: in un browser, su un dispositivo mobile o tramite un’applicazione e-mail.

La **[!UICONTROL General summary]** presenta il numero di messaggi ricevuti, indesiderati (spam), non ricevuti o in attesa di ricezione, sotto forma di elenco e tramite una rappresentazione grafica a colori.

![](assets/s_tn_inbox_rendering_summary.png)

Passa il cursore del mouse sul grafico per visualizzare i dettagli di ciascun colore.

Il contenuto del rapporto è suddiviso in tre parti: **[!UICONTROL Mobile]**, **[!UICONTROL Messaging clients]** e **[!UICONTROL Webmails]**. Per visualizzare tutti i rendering raggruppati in queste tre categorie, scorri il report verso il basso.

![](assets/s_tn_inbox_rendering_report.png)

Per ottenere i dettagli di ciascun report, fai clic sulla scheda corrispondente. Viene visualizzato il rendering per il metodo di ricezione selezionato.

![](assets/s_tn_inbox_rendering_example.png)
