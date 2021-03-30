---
solution: Campaign Classic
product: campaign
title: Creare contenuti personalizzati
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 40edacce1812a1722e5a23e5db7da11687c44ac8
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 7%

---


# Creare contenuti personalizzati {#build-personalized-content}

Durante la progettazione del contenuto del messaggio, cerca di evitare problemi comuni che potrebbero impedire l’esecuzione della consegna. Nella maggior parte dei casi, eventuali errori sono correlati a [personalizzazione](../../delivery/using/about-personalization.md), [formattazione](../../delivery/using/defining-the-email-content.md#message-content) e [immagini](../../delivery/using/defining-the-email-content.md#adding-images).

## Ottimizzare la personalizzazione {#optimize-personalization}

Per evitare problemi comuni che potrebbero impedire l’esecuzione della consegna e migliorare l’esperienza dei destinatari, Adobe Campaign ti consente di personalizzare i messaggi.

Puoi utilizzare i dati dei destinatari memorizzati nel database di Adobe Campaign o raccolti tramite tracciamento, pagine di destinazione, abbonamenti, ecc.
Le nozioni di base sulla personalizzazione sono presentate in [questa sezione](../../delivery/using/personalization-fields.md).

Assicurati che il contenuto del messaggio sia progettato correttamente per evitare errori, generalmente correlati alla personalizzazione.

**Suggerimenti**: Nei campi di personalizzazione provenienti da file esterni forniti da fornitori terzi, il contenuto HTML esterno può essere errato. Per evitare questo problema, controlla la sintassi, l’uso di tag, caratteri, ecc. Ad esempio, un tag di personalizzazione Adobe Campaign ha sempre il seguente modulo: &lt;%=table.field%>. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/about-personalization.md).

Un problema può essere rappresentato dall’uso errato dei parametri nei blocchi di personalizzazione. Ad esempio, le variabili in JavaScript devono essere utilizzate come segue:

    &lt;>var brand = &quot;xxx&quot;
    
    %>

    
    
Per ulteriori informazioni sui blocchi di personalizzazione, consulta [questa sezione](../../delivery/using/personalization-blocks.md).

Puoi preparare i dati di personalizzazione in un flusso di lavoro per migliorare l’analisi della preparazione della consegna. Questo dovrebbe essere utilizzato specialmente se i dati di personalizzazione provengono da una tabella esterna tramite Federated Data Access (FDA). Questa opzione è descritta in questa [sezione](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Creare contenuti ottimizzati {#optimize-content}

Quando crei le e-mail, ricorda le best practice generali riportate di seguito.

* Mantieni il design semplice

* Tenere a mente gli utenti dei dispositivi mobili

* Evita e-mail interamente basate su immagini

* Utilizza font sicuri per e-mail

* Codifica caratteri speciali

### Linea oggetto

Lavora sulla [riga oggetto](../../delivery/using/defining-the-email-content.md#message-content) per migliorare i tassi di apertura:

* Evita soggetti troppo lunghi. Utilizza un massimo di 50 caratteri

* Evita di usare parole ripetitive come &quot;libero&quot; o &quot;offerta&quot;, che potrebbero essere considerate come spam

* Evitare lettere maiuscole e caratteri speciali come &quot;!&quot;, &quot; £&quot;, &quot;€&quot;, &quot;$&quot;

### Pagina speculare

Includi sempre un collegamento alla pagina speculare. La posizione preferita è la parte superiore dell’e-mail. [Ulteriori informazioni](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Collegamento di annullamento dell’abbonamento

Il collegamento di annullamento dell’abbonamento è essenziale. Deve essere visibile e valido e il modulo deve essere funzionale. Per impostazione predefinita, quando il messaggio viene analizzato, una [regola di tipologia](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) controlla se un collegamento di rinuncia è stato incluso e genera un avviso in caso di assenza.

**Suggerimento**: Poiché l’errore umano è sempre possibile, controlla che il collegamento di rinuncia funzioni correttamente prima di ogni invio. Ad esempio, quando invii la bozza, accertati che il collegamento sia valido, che il modulo sia online e che il campo Destinatario non venga più contattato sia stato modificato in Sì.

Scopri come inserire un collegamento di rinuncia [in questa sezione](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

### Dimensione e-mail

Per evitare problemi di prestazioni o recapito messaggi, la dimensione massima consigliata di un messaggio e-mail è di circa **35 KB**. Per controllare la dimensione del messaggio, vai alla scheda **[!UICONTROL Preview]** e scegli un profilo di test. Una volta generata, la dimensione del messaggio verrà visualizzata nell’angolo in alto a destra.

Per mantenere l’e-mail sotto il limite, considera quanto segue:

* Rimuovere gli stili ridondanti o inutilizzati

* Sposta parte del contenuto delle e-mail in una pagina di destinazione

* Minimizzare il codice

Verifica eventuali modifiche prima dell’invio finale

### Lunghezza SMS

Per impostazione predefinita, il numero di caratteri in un SMS soddisfa gli standard GSM (Global System for Mobile Communications). I messaggi SMS che utilizzano la codifica GSM sono limitati a 160 caratteri o 153 caratteri per SMS per messaggi inviati in più parti.

La traslitterazione consiste nel sostituire un carattere di un SMS con un altro quando quel carattere non è preso in considerazione dallo standard GSM. Tieni presente che l’inserimento di campi di personalizzazione nel contenuto del messaggio SMS può introdurre caratteri che non vengono presi in considerazione dalla codifica GSM. Puoi autorizzare la traslitterazione dei caratteri selezionando la casella corrispondente nella scheda delle impostazioni del canale SMPP della **[!UICONTROL External account]** corrispondente.
Ulteriori informazioni [in questa sezione](../../delivery/using/sms-set-up.md#creating-an-smpp-external-account).

**Suggerimenti**:

* Per mantenere tutti i caratteri nei messaggi SMS così come sono, per non modificare i nomi propri, ad esempio, non abilitare la traslitterazione.

* Tuttavia, se i messaggi SMS contengono molti caratteri che non vengono presi in considerazione dallo standard GSM, abilita la traslitterazione per limitare i costi di invio dei messaggi.

Ulteriori informazioni [in questa sezione](../../delivery/using/sms-set-up.md#about-character-transliteration).

## Lavoro sulla formattazione {#formatting}

Per evitare errori di formattazione comuni, controlla i seguenti elementi:

* Correggi **formattazione data**: Adobe Campaign fornisce funzioni di formattazione della data per i modelli JavaScript e i fogli di stile XSL. [Ulteriori informazioni](../../delivery/using/formatting.md#date-display)

* Uso di **caratteri autorizzati** nelle e-mail: l’elenco dei caratteri validi per gli indirizzi e-mail è definito nell’opzione &quot;XtkEmail_Characters&quot;. Scopri come accedere alle opzioni di Campaign [in questa sezione](../../installation/using/configuring-campaign-options.md). Per gestire correttamente i caratteri speciali, Adobe Campaign deve essere installato in Unicode.

* Configurazione di **Autenticazione e-mail**: assicurati che le intestazioni e-mail contengano la firma DKIM. L’autenticazione DKIM (Domain Keys Identified Mail) consente al server di posta elettronica ricevente di verificare che un messaggio sia stato effettivamente inviato dalla persona o dall’entità da cui asserisce di essere stato inviato e se il contenuto del messaggio sia stato modificato tra il momento dell’invio originale (e DKIM &quot;signed&quot;) e il momento in cui è stato ricevuto. In genere, questo standard utilizza il dominio nell’intestazione Da o Mittente. Per ulteriori informazioni, consulta la [Guida alle best practice per il recapito messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Progettazione e-mail reattiva

La progettazione reattiva assicura il rendering ottimale di un’e-mail per il dispositivo su cui viene aperta.

* Utilizza l’HTML dell’e-mail reattiva anziché l’HTML del web

* Utilizza la modalità anteprima e invia bozze per testare il rendering su quanti più dispositivi possibile

* Il modulo Adobe Campaign Classic Digital Content Editor (DCE) include alcuni modelli adattabili in formato design per dispositivi mobili disponibili tramite **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Ulteriori informazioni [in questo articolo](https://theblog.adobe.com/responsive-email-design-101/)

## Gestire le immagini {#manage-images}

Segui le linee guida riportate di seguito quando si tratta di utilizzare le immagini.

### Impedisci il blocco delle immagini

Alcuni client di posta elettronica bloccano le immagini per impostazione predefinita e alcuni utenti modificano le impostazioni per bloccare le immagini per il salvataggio sull’utilizzo dei dati. Pertanto, se le immagini non vengono scaricate, l&#39;intero messaggio può essere perso. Per evitare questo:

* Bilancia il contenuto con immagine e testo. Evita e-mail interamente basate su immagini.

* Se il testo deve essere contenuto in un’immagine, utilizza il testo alt e title per assicurarti che il messaggio venga trasmesso. Personalizzare lo stile del testo alt/title per migliorarne l’aspetto.

* Evita l’uso di immagini in background in quanto non sono supportate da alcuni client e-mail.

### Rendere le immagini reattive

Prova a rendere le immagini reattive e ridimensionabili. Tieni presente che questo può avere un impatto sui costi in quanto la creazione richiede più tempo.

### Usa riferimenti di immagine assoluti

Per essere accessibile dall’esterno, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server accessibile dall’esterno.

* Puoi verificare se la configurazione dell’istanza abilita la gestione delle risorse pubbliche. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Dalla procedura guidata di consegna, puoi importare una pagina HTML contenente immagini o inserire immagini direttamente utilizzando l’editor HTML tramite l’icona **[!UICONTROL Image]** . [Ulteriori informazioni](../../delivery/using/defining-the-email-content.md#adding-images)

* Se le immagini non vengono visualizzate, controlla che siano disponibili sul server. A questo scopo, fai clic sulla scheda Origine dalla consegna. Trova le immagini e copia-incolla l’URL di ciascuna immagine in un browser web. Se le immagini non vengono visualizzate, contatta l’amministratore IT o il fornitore di terze parti che fornisce il contenuto della consegna.

## Anteprima del messaggio {#preview-msg}

Adobe consiglia di visualizzare l’anteprima del messaggio per verificarne la personalizzazione e il modo in cui i destinatari visualizzeranno la consegna.

* Nella procedura guidata di consegna, la sottoscheda **[!UICONTROL Preview]** ti consente di visualizzare il rendering di ciascun contenuto per un destinatario. I campi di personalizzazione e gli elementi condizionali del contenuto vengono sostituiti con le informazioni corrispondenti per il profilo selezionato. [Ulteriori informazioni](../../delivery/using/defining-the-email-content.md#message-content)

* Durante ogni anteprima viene eseguito un controllo automatico anti-spam. Nella sottoscheda **[!UICONTROL Preview]** , controlla il punteggio [SpamAssassin](../../delivery/using/spamassassin.md) relativo allo spam.  Fai clic su **[!UICONTROL More...]** per ulteriori informazioni sull’avviso.  Prima di eseguire questa operazione, assicurati che SpamAssassin sia installato e configurato correttamente sul server dell&#39;applicazione Adobe Campaign. [Ulteriori informazioni](../../installation/using/configuring-spamassassin.md)
