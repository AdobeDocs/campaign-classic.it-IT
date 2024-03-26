---
product: campaign
title: Creare contenuti personalizzati
description: Scopri come creare contenuti personalizzati nelle consegne di Adobe Campaign
badge-v7: label="v7" type="Informative" tooltip="Applicabile a Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Email Design, Personalization
role: User
exl-id: 5bf727d2-83b1-4a99-be25-041eee8d234c
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 4%

---

# Creare contenuti personalizzati {#build-personalized-content}

Durante la progettazione del contenuto del messaggio, cerca di evitare problemi comuni che potrebbero impedirti di eseguire la consegna. Nella maggior parte dei casi, i possibili errori sono correlati a [personalizzazione](about-personalization.md), [formattazione](defining-the-email-content.md#message-content) e [immagini](defining-the-email-content.md#adding-images).

## Ottimizzare la personalizzazione {#optimize-personalization}

Per evitare problemi comuni che potrebbero impedire l’esecuzione della consegna e migliorare l’esperienza dei destinatari, Adobe Campaign consente di personalizzare i messaggi.

Puoi utilizzare i dati dei destinatari memorizzati nel database di Adobe Campaign o raccolti tramite tracciamento, pagine di destinazione, abbonamenti, ecc.
Le nozioni di base sulla personalizzazione sono presentate in [questa sezione](personalization-fields.md).

Assicurati che il contenuto del messaggio sia progettato correttamente per evitare errori, che sono generalmente correlati alla personalizzazione.

**Suggerimenti**: nei campi di personalizzazione provenienti da file esterni forniti da fornitori terzi, il contenuto HTML esterno può essere errato. Per evitare questo problema, controlla la sintassi, l’utilizzo di tag, caratteri e così via. Ad esempio, un tag di personalizzazione Adobe Campaign ha sempre il seguente formato: &lt;%=table.field%>. Per ulteriori informazioni, consulta [questa sezione](about-personalization.md).

L’utilizzo errato dei parametri nei blocchi di personalizzazione può rappresentare un problema. Ad esempio, le variabili in JavaScript devono essere utilizzate come segue:

    &lt;%
    
    var brand = &quot;xxx&quot;
    
    %>

Per ulteriori informazioni sui blocchi di personalizzazione, consulta [questa sezione](personalization-blocks.md).

Puoi preparare i dati di personalizzazione in un flusso di lavoro per migliorare l’analisi della preparazione della consegna. Questa deve essere utilizzata in modo particolare se i dati di personalizzazione provengono da una tabella esterna tramite Federated Data Access (FDA). Questa opzione è descritta in questo [questa sezione](personalization-fields.md#optimizing-personalization)

## Creare contenuti ottimizzati {#optimize-content}

Durante la creazione delle e-mail, tieni presenti le best practice generali riportate di seguito.

* Design semplice

* Tieni presente gli utenti mobili

* Evita e-mail interamente basate su immagini

* Utilizza font sicuri per le e-mail

* Codifica caratteri speciali

### Oggetto

Lavorare su [oggetto](defining-the-email-content.md#message-content) per migliorare i tassi di apertura:

* Evitare soggetti troppo lunghi. Usa massimo 50 caratteri

* Evita di usare parole ripetitive come &quot;gratuito&quot; o &quot;offerta&quot;, che potrebbero essere considerate spam

* Evita lettere maiuscole e caratteri speciali come &quot;!&quot;, &quot;£&quot;, &quot;€&quot;, &quot;$&quot;

### Pagina mirror

Includi sempre un collegamento a una pagina speculare. La posizione preferita è nella parte superiore dell’e-mail. [Ulteriori informazioni](sending-messages.md#generating-the-mirror-page)

### Collegamento Annulla iscrizione

Il collegamento di annullamento dell’abbonamento è essenziale. Deve essere visibile e valido e il modulo deve essere funzionale. Per impostazione predefinita, quando il messaggio viene analizzato, viene [regola di tipologia](steps-validating-the-delivery.md#validation-process-with-typologies) controlla se è stato incluso un collegamento di rinuncia e, in caso contrario, genera un avviso.

**Suggerimento**: poiché gli errori umani sono sempre possibili, controlla che il collegamento di rinuncia funzioni correttamente prima di ogni invio. Ad esempio, quando invii la bozza, accertati che il collegamento sia valido, che il modulo sia in linea e che il campo Non contattare più questo destinatario sia impostato su Sì.

Scopri come inserire un collegamento di rinuncia [in questa sezione](personalization-blocks.md#personalization-blocks-example).

### Dimensione e-mail

Per evitare problemi di prestazioni o recapito messaggi, la dimensione massima consigliata per un’e-mail è circa **35 KB**. Per verificare la dimensione del messaggio, vai al **[!UICONTROL Preview]** e scegli un profilo di test. Una volta generata, la dimensione del messaggio viene visualizzata nell’angolo in alto a destra.

Per mantenere l’e-mail entro il limite, considera quanto segue:

* Rimuovi stili ridondanti o inutilizzati

* Spostare parte del contenuto dell’e-mail in una pagina di destinazione

* Minimizzare il codice

Assicurati di verificare eventuali modifiche prima dell’invio finale

### Lunghezza SMS

Per impostazione predefinita, il numero di caratteri in un SMS soddisfa gli standard GSM (Global System for Mobile Communications). I messaggi SMS che utilizzano la codifica GSM sono limitati a 160 caratteri o 153 caratteri per SMS per messaggi inviati in più parti.

La traslitterazione consiste nel sostituire un carattere di un SMS con un altro quando tale carattere non è preso in considerazione dallo standard GSM. L’inserimento di campi di personalizzazione nel contenuto del messaggio SMS potrebbe introdurre caratteri che non vengono presi in considerazione dalla codifica GSM. Puoi autorizzare la traslitterazione di caratteri selezionando la casella corrispondente nella scheda delle impostazioni del canale SMPP della **[!UICONTROL External account]**.
Per ulteriori informazioni, consulta [questa sezione](sms-set-up.md#creating-an-smpp-external-account).

**Suggerimenti**:

* Per mantenere invariati tutti i caratteri nei messaggi SMS, ad esempio per non modificare i nomi propri, non abilitare la traslitterazione.

* Tuttavia, se i messaggi SMS contengono molti caratteri che non sono presi in considerazione dallo standard GSM, abilita la traslitterazione per limitare i costi di invio dei messaggi.

Per ulteriori informazioni, consulta [questa sezione](sms-set-up.md#about-character-transliteration).

## Lavorare sulla formattazione {#formatting}

Per evitare errori di formattazione comuni, controlla i seguenti elementi:

* Corretto **formattazione della data**: Adobe Campaign fornisce funzioni di formattazione della data per i modelli JavaScript e i fogli di stile XSL. [Ulteriori informazioni](formatting.md#date-display)

* Utilizzo di **caratteri autorizzati** nelle e-mail: l’elenco dei caratteri validi per gli indirizzi e-mail è definito nell’opzione &quot;XtkEmail_Characters&quot;. Scopri come accedere alle opzioni di Campaign [in questa sezione](../../installation/using/configuring-campaign-options.md). Per gestire correttamente i caratteri speciali, è necessario installare Adobe Campaign in Unicode.

* Configurazione di **Autenticazione e-mail**: accertati che le intestazioni e-mail contengano la firma DKIM. L’autenticazione DKIM (Domain Keys Identified Mail) consente al server e-mail ricevente di verificare che un messaggio sia stato effettivamente inviato dalla persona o dall’entità da cui afferma di essere stato inviato e se il contenuto del messaggio sia stato modificato tra il momento dell’invio originale (e DKIM &quot;firmato&quot;) e il momento della ricezione. Questo standard utilizza in genere il dominio nell’intestazione Da o Mittente. Per ulteriori informazioni, consulta [Guida alle procedure consigliate per la consegna dei messaggi di Adobe](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### Progettazione reattiva delle e-mail

Il design reattivo assicura che un’e-mail venga riprodotta in modo ottimale per il dispositivo su cui viene aperta.

* Utilizza e-mail HTML responsive anziché web HTML

* Utilizza la modalità anteprima e invia bozze per testare il rendering su quanti più dispositivi possibili

* Il modulo Adobe Campaign Classic Digital Content Editor (DCE) include alcuni modelli formattati per la progettazione reattiva per i dispositivi mobili disponibili tramite **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Content templates]**. Ulteriori informazioni [in questo articolo](https://theblog.adobe.com/responsive-email-design-101/)

## Gestione immagini {#manage-images}

Per l&#39;utilizzo delle immagini, attenersi alle istruzioni riportate di seguito.

### Impedisci il blocco delle immagini

Per impostazione predefinita, alcuni client di posta elettronica bloccano le immagini e alcuni utenti modificano le proprie impostazioni in modo da bloccare le immagini per il salvataggio nell’utilizzo dei dati. Pertanto, se le immagini non vengono scaricate, l’intero messaggio può andare perso. Per evitare questo problema:

* Bilancia il contenuto con immagine e testo. Evita di inviare e-mail interamente basate su immagini.

* Se il testo deve essere contenuto in un’immagine, utilizza il testo alt e il testo del titolo per assicurarti che il messaggio venga trasmesso. Personalizzate lo stile del testo alt/titolo per migliorarne l&#39;aspetto.

* Evita l’uso di immagini di sfondo, in quanto non sono supportate da alcuni client e-mail.

### Rendi le immagini dinamiche

Prova a rendere le immagini dinamiche e ridimensionabili. Tieni presente che questo può avere un impatto sui costi, poiché la generazione richiede più tempo.

### Usa riferimenti immagine assoluti

Per essere accessibili dall’esterno, le immagini utilizzate nelle e-mail e nelle risorse pubbliche collegate alle campagne devono essere presenti su un server accessibile dall’esterno.

* Puoi verificare se la configurazione dell’istanza abilita la gestione delle risorse pubbliche. [Ulteriori informazioni](../../installation/using/deploying-an-instance.md#managing-public-resources)

* Dalla procedura guidata di consegna, puoi importare una pagina di HTML contenente immagini o inserirle direttamente utilizzando l’editor di HTML tramite **[!UICONTROL Image]** icona. [Ulteriori informazioni](defining-the-email-content.md#adding-images)

* Se le immagini non vengono visualizzate, verificare che siano disponibili sul server. A questo scopo, fai clic sulla scheda Origine della consegna. Trova le tue immagini e copia-incolla l’URL di ogni immagine in un browser web. Se le immagini non vengono visualizzate, contatta l’amministratore IT o il fornitore di terze parti che fornisce i contenuti di consegna.

## Anteprima del messaggio {#preview-msg}

L’Adobe consiglia di visualizzare l’anteprima del messaggio per controllarne la personalizzazione e per vedere come i destinatari visualizzeranno la consegna.

* Nella procedura guidata di consegna, **[!UICONTROL Preview]** scheda secondaria consente di visualizzare il rendering di ciascun contenuto per un destinatario. I campi di personalizzazione e gli elementi condizionali del contenuto vengono sostituiti con le informazioni corrispondenti per il profilo selezionato. [Ulteriori informazioni](defining-the-email-content.md#message-content)

* Durante ogni anteprima viene eseguito un controllo automatico anti-spam. In **[!UICONTROL Preview]** scheda secondaria, segno di spunta [SpamAssassin](spamassassin.md) punteggio spam.  Clic **[!UICONTROL More...]** per ulteriori informazioni sull&#39;avviso.  Prima di eseguire questa operazione, verificare che SpamAssassin sia installato e configurato correttamente nel server applicazioni Adobe Campaign. [Ulteriori informazioni](../../installation/using/configuring-spamassassin.md)
