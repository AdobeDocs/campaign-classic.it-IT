---
solution: Campaign Classic
product: campaign
title: Creare contenuti personalizzati
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1266'
ht-degree: 7%

---


# Creare contenuti personalizzati {#build-personalized-content}

Durante la progettazione del contenuto del messaggio, cercate di evitare problemi comuni che potrebbero impedire l&#39;esecuzione della distribuzione. Nella maggior parte dei casi, eventuali errori sono correlati a [personalizzazione](../../delivery/using/about-personalization.md), [formattazione](../../delivery/using/defining-the-email-content.md#message-content) e [immagini](../../delivery/using/defining-the-email-content.md#adding-images).

## Ottimizzazione della personalizzazione {#optimize-personalization}

Per evitare problemi comuni che potrebbero impedire l’esecuzione della consegna e migliorare l’esperienza dei destinatari,  Adobe Campaign consente di personalizzare i messaggi.

È possibile utilizzare i dati dei destinatari memorizzati nel database Adobe Campaign  oppure raccolti tramite tracciamento, pagine di destinazione, iscrizioni ecc.
Le nozioni di base sulla personalizzazione sono presentate in [questa sezione](../../delivery/using/personalization-fields.md).

Assicurati che il contenuto del messaggio sia progettato correttamente per evitare errori, generalmente correlati alla personalizzazione.

**Suggerimenti**: Nei campi di personalizzazione provenienti da file esterni forniti da fornitori di terze parti, il contenuto HTML esterno può essere errato. Per evitare questo problema, controllare la sintassi, l&#39;uso di tag, caratteri e così via. Ad esempio, un tag di personalizzazione Adobe Campaign  ha sempre il seguente modulo: &lt;%=table.field%>. Per ulteriori informazioni, consulta [questa sezione](../../delivery/using/about-personalization.md).

L’uso non corretto dei parametri nei blocchi di personalizzazione può rappresentare un problema. Ad esempio, le variabili in JavaScript devono essere utilizzate come segue:

    &lt;>var brand = &quot;xxx&quot;
    
    %>

    
    
Per ulteriori informazioni sui blocchi di personalizzazione, consultare la sezione [this](../../delivery/using/personalization-blocks.md).

Puoi preparare i dati di personalizzazione in un flusso di lavoro per migliorare l’analisi della preparazione della distribuzione. Questo dovrebbe essere utilizzato specialmente se i dati di personalizzazione provengono da una tabella esterna tramite Federated Data Access (FDA). Questa opzione è descritta in questa [sezione](../../delivery/using/personalization-fields.md#optimizing-personalization)

## Creazione di contenuto ottimizzato {#optimize-content}

Durante la creazione delle e-mail, tieni presente le best practice generali riportate di seguito.

* Design semplice

* Ricordate gli utenti dei dispositivi mobili

* Evita e-mail basate interamente su immagini

* Utilizzo di font sicuri per le e-mail

* Codifica di caratteri speciali

### Riga oggetto

Lavorare sulla [linea oggetto](../../delivery/using/defining-the-email-content.md#message-content) per migliorare le tariffe aperte:

* Evitare soggetti troppo lunghi. Utilizza un massimo di 50 caratteri

* Evitare di usare parole ripetitive come &quot;free&quot; o &quot;offer&quot;, che potrebbero essere considerate spam

* Evitare lettere maiuscole e caratteri speciali come &quot;!&quot;, &quot;€&quot;, &quot;€&quot;, &quot;$&quot;

### Mirror, pagina

Includi sempre un collegamento della pagina mirror. La posizione preferita è la parte superiore dell’e-mail. [Ulteriori informazioni](../../delivery/using/sending-messages.md#generating-the-mirror-page)

### Collegamento di annullamento dell’abbonamento

Il collegamento di annullamento della sottoscrizione è essenziale. Deve essere visibile e valido e il modulo deve essere funzionale. Per impostazione predefinita, quando il messaggio viene analizzato, una [regola di tipologia](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies) controlla se è stato incluso un collegamento di rinuncia e genera un avviso se risulta mancante.

**Suggerimento**: Poiché l’errore umano è sempre possibile, verificate che il collegamento di rinuncia funzioni correttamente prima di ogni invio. Ad esempio, al momento dell&#39;invio della prova, verificare che il collegamento sia valido, che il modulo sia online e che il campo Destinatario non contatta più sia cambiato in Sì.

Scoprite come inserire un collegamento di rinuncia [in questa sezione](../../delivery/using/personalization-blocks.md#personalization-blocks-example).

### Dimensione e-mail

Per evitare problemi di prestazioni o di recapito, la dimensione massima consigliata per un messaggio e-mail è di circa **35 KB**. Per verificare la dimensione del messaggio, andate alla scheda **[!UICONTROL Preview]** e scegliete un profilo di prova. Una volta generata, la dimensione del messaggio verrà visualizzata nell&#39;angolo superiore destro.

Per mantenere l’e-mail al di sotto del limite, tenete presente quanto segue:

* Rimuovere stili ridondanti o inutilizzati

* Spostare parte del contenuto dell’e-mail in una pagina di destinazione

* Riduzione del codice

Verificare eventuali modifiche prima dell&#39;invio finale

### Lunghezza SMS

Per impostazione predefinita, il numero di caratteri in un SMS soddisfa gli standard GSM (Global System for Mobile Communications). I messaggi SMS che utilizzano la codifica GSM sono limitati a 160 caratteri o 153 caratteri per SMS per messaggi inviati in più parti.

La traslitterazione consiste nel sostituire un carattere di un SMS con un altro quando quel carattere non è preso in considerazione dallo standard GSM. L&#39;inserimento di campi di personalizzazione nel contenuto del messaggio SMS potrebbe introdurre caratteri che non vengono presi in considerazione dalla codifica GSM. È possibile autorizzare la traslazione dei caratteri selezionando la casella corrispondente nella scheda delle impostazioni del canale SMPP della **[!UICONTROL External account]** corrispondente.
Ulteriori informazioni [in questa sezione](../../delivery/using/sms-channel.md#creating-an-smpp-external-account).

**Suggerimenti**:

* Per mantenere tutti i caratteri nei messaggi SMS così come sono, per non alterare i nomi propri, ad esempio, non abilitare la traslazione.

* Tuttavia, se i vostri messaggi SMS contengono molti caratteri che non sono presi in considerazione dallo standard GSM, abilitate la traslazione per limitare i costi di invio dei vostri messaggi.

Ulteriori informazioni [in questa sezione](../../delivery/using/sms-channel.md#about-character-transliteration).

## Operazioni per la formattazione {#formatting}

Per evitare errori di formattazione comuni, verificare quanto segue:

* Correggi **formattazione data**:  Adobe Campaign fornisce funzioni di formattazione delle date per i modelli JavaScript e i fogli di stile XSL. [Ulteriori informazioni](../../delivery/using/formatting.md#date-display)

* Uso di **caratteri autorizzati** nelle e-mail: l&#39;elenco di caratteri validi per gli indirizzi e-mail è definito nell&#39;opzione &quot;XtkEmail_Characters&quot;. Scopri come accedere alle opzioni Campagna [in questa sezione](../../installation/using/configuring-campaign-options.md). Per gestire correttamente i caratteri speciali,  Adobe Campaign deve essere installato in Unicode.

* Configurazione di **Autenticazione e-mail**: accertatevi che le intestazioni e-mail contengano la firma DKIM. L&#39;autenticazione DKIM (Domain Keys Identified Mail) consente al server di posta elettronica ricevente di verificare che un messaggio sia stato effettivamente inviato dalla persona o dall&#39;entità da cui sostiene di essere stato inviato, e se il contenuto del messaggio sia stato modificato tra il momento dell&#39;invio originale (e DKIM &quot;signed&quot;) e l&#39;ora in cui è stato ricevuto. In genere, questo standard utilizza il dominio nell’intestazione Da o Mittente. Per ulteriori informazioni al riguardo, consulta [questa sezione](../../delivery/using/technical-recommendations.md#dkim).

### Progettazione e-mail reattiva

La progettazione reattiva assicura il rendering ottimale dell’e-mail per il dispositivo su cui viene aperto.

* Utilizzate HTML e-mail reattive invece di HTML Web

* Utilizzate la modalità di anteprima e inviate le prove di stampa per testare il rendering su quanti più dispositivi possibile

* Il modulo Adobe Campaign Classic Digital Content Editor (DCE) include alcuni modelli di progettazione reattiva per dispositivi mobili disponibili tramite **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Ulteriori informazioni [in questo articolo](https://theblog.adobe.com/responsive-email-design-101/)

## Gestire le immagini {#manage-images}

Seguite le linee guida riportate di seguito quando si tratta di usare le immagini.

### Impedire il blocco delle immagini

Per impostazione predefinita, alcuni client e-mail bloccano le immagini e alcuni utenti modificano le proprie impostazioni per bloccare le immagini da salvare in base all’utilizzo dei dati. Pertanto, se le immagini non vengono scaricate, l&#39;intero messaggio può andare perso. Per evitare ciò:

* Bilancia i contenuti con immagini e testo. Evitate e-mail basate interamente su immagini.

* Se il testo deve essere contenuto in un’immagine, usate il testo alternativo e del titolo per essere certi che il messaggio possa essere trasmesso. Applicate uno stile al testo alt/title per migliorarne l’aspetto.

* Evitate l’utilizzo di immagini di sfondo poiché non sono supportate da alcuni client e-mail.

### Rendere le immagini reattive

Cercate di rendere le immagini reattive e ridimensionabili. Questo può avere un impatto sui costi in quanto la creazione richiede più tempo.

### Utilizzare riferimenti di immagine assoluti

Per essere accessibili dall&#39;esterno, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server esterno accessibile.

* È possibile verificare se la configurazione dell&#39;istanza abilita la gestione delle risorse pubbliche. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Dalla procedura guidata di distribuzione, potete importare una pagina HTML contenente immagini o inserire immagini direttamente mediante l&#39;editor HTML tramite l&#39;icona **[!UICONTROL Image]**. [Ulteriori informazioni](../../delivery/using/defining-the-email-content.md#adding-images)

* Se le immagini non sono visualizzate, controllate che siano disponibili sul server. A questo scopo, fate clic sulla scheda Sorgente dalla consegna. Trovate le immagini e copiate l’URL di ciascuna immagine in un browser Web. Se le immagini non vengono visualizzate, contattate l’amministratore IT o il fornitore di terze parti che fornisce il contenuto per la distribuzione.

## Visualizza in anteprima il messaggio {#preview-msg}

 Adobe consiglia di visualizzare in anteprima il messaggio per verificarne la personalizzazione e vedere in che modo i destinatari vedranno la consegna.

* Nella scheda della distribuzione, la scheda secondaria **[!UICONTROL Preview]** consente di visualizzare il rendering di ciascun contenuto per un destinatario. I campi di personalizzazione e gli elementi condizionali del contenuto vengono sostituiti con le informazioni corrispondenti per il profilo selezionato. [Ulteriori informazioni](../../delivery/using/defining-the-email-content.md#message-content)

* Durante ogni anteprima viene eseguito un controllo automatico dello spam. Nella scheda secondaria **[!UICONTROL Preview]**, selezionare [SpamAssassin](../../delivery/using/spamassassin.md) punteggio spam.  Fare clic su **[!UICONTROL More...]** per ulteriori informazioni sull&#39;avviso.  Prima di eseguire questa operazione, assicurarsi che SpamAssassin sia correttamente installato e configurato sul server  applicazione Adobe Campaign. [Ulteriori informazioni](../../installation/using/configuring-spamassassin.md)
