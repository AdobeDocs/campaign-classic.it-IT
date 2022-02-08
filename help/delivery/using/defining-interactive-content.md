---
product: campaign
title: Definire il contenuto interattivo in Adobe Campaign Classic
description: Scopri come definire il contenuto delle e-mail interattive e dinamiche con AMP in Adobe Campaign
feature: Email Design, Dynamic Content
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 3%

---

# Definire il contenuto interattivo{#defining-interactive-content}

![](../../assets/common.svg)

Adobe Campaign consente di utilizzare la nuova interfaccia interattiva [AMP per e-mail](https://amp.dev/about/email/) , che consente di inviare e-mail dinamiche in determinate condizioni.

Con AMP per e-mail puoi:
* Verifica la consegna di e-mail AMP a indirizzi specifici configurati in modo appropriato.
* Consegnare e-mail AMP agli indirizzi Gmail, Outlook o Mail.ru dopo la registrazione con i provider corrispondenti.

Per ulteriori informazioni sul test e l’invio di e-mail AMP, consulta [questa sezione](#targeting-amp-email).

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. A seconda delle autorizzazioni e del modello di distribuzione, puoi installare questo pacchetto o contattare Adobe per installarlo autonomamente.

>[!NOTE]
>
> Per le architetture ibride e in hosting, il pacchetto deve essere installato su tutti i server, compresi i [server di mid-sourcing](../../installation/using/mid-sourcing-server.md) e [istanza di esecuzione](../../message-center/using/configuring-instances.md#execution-instance).


## Informazioni su AMP per e-mail {#about-amp-for-email}

Utilizza la **AMP per e-mail** nuovo formato per includere i componenti AMP nei messaggi e migliorare l’esperienza e-mail con un contenuto ricco e fruibile. Integrando direttamente nelle e-mail le funzionalità tipiche delle app, i destinatari possono interagire in modo dinamico con il contenuto stesso del messaggio.

Ad esempio:
* Le e-mail scritte con AMP possono contenere elementi interattivi quali caroselli di immagini.
* Il contenuto del messaggio rimane aggiornato.
* I destinatari possono rispondere a un modulo senza uscire dalla casella in entrata.

AMP per e-mail è compatibile con le e-mail esistenti. La versione AMP del messaggio è incorporata nell’e-mail come nuova parte MIME, oltre al testo HTML e/o normale, garantendo la compatibilità tra tutti i client e-mail.

Per ulteriori informazioni su formato, specifiche e requisiti dell’AMP per l’e-mail, consulta la [Documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#amp-email-video)

## Passaggi chiave per l’utilizzo di AMP per l’e-mail con Adobe Campaign {#key-steps-to-use-amp}

Per testare e inviare correttamente un’e-mail AMP con Adobe Campaign, segui la procedura seguente:
1. Installa il **[!UICONTROL AMP support]** pacchetto. Vedi [Installazione dei pacchetti incorporati di Campaign](../../installation/using/installing-campaign-standard-packages.md).
1. Crea un’e-mail e crea il contenuto AMP all’interno di Adobe Campaign. Vedi [Creare contenuti e-mail AMP con Adobe Campaign](#build-amp-email-content).
1. Assicurati di rispettare tutti i requisiti di consegna dai provider di posta elettronica che supportano il formato AMP. Vedi [AMP per i requisiti di consegna e-mail](#amp-for-email-delivery-requirements).
1. Quando definisci il target, assicurati di selezionare i destinatari che saranno in grado di visualizzare il formato AMP. Vedi [Targeting di un’e-mail AMP](#targeting-amp-email).

   >[!NOTE]
   >
   >Attualmente puoi inviare solo e-mail AMP a [indirizzi e-mail specifici](#testing-amp-delivery-for-selected-addresses) (a scopo di prova) o dopo [registrazione](#delivering-amp-emails-by-registering) con i client e-mail supportati.

1. Invia la tua e-mail come faresti di solito. Vedi [Invio di un’e-mail AMP](#sending-amp-email).

## Creare contenuti e-mail AMP in Adobe Campaign {#build-amp-email-content}

Per creare un’e-mail utilizzando il formato AMP, segui la procedura seguente.

>[!IMPORTANT]
>
>Assicurati di seguire l’AMP per i requisiti e le specifiche e-mail descritti in [Documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). È inoltre possibile consultare [Best practice per AMP per e-mail](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. Quando crei la consegna e-mail, seleziona un modello qualsiasi.

   >[!NOTE]
   >
   >Un modello AMP specifico contiene un esempio delle capacità principali che puoi utilizzare: elenco prodotti, carosello, doppio consenso, sondaggio e richiesta avanzata del server.

1. Fai clic sul pulsante **[!UICONTROL AMP content]** scheda .

   ![](assets/amp_tab.png)

1. Modifica il contenuto AMP in base alle tue esigenze.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione della tua prima e-mail AMP, consulta la sezione [Documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   Ad esempio, puoi utilizzare il componente elenco prodotti del modello AMP e mantenere un elenco di prodotti da un sistema di terze parti o anche all’interno di Adobe Campaign. Ogni volta che regoli un prezzo o un altro elemento, questo si riflette automaticamente quando i destinatari aprono l’e-mail dalla propria casella di posta.

1. Personalizza il contenuto AMP in base alle esigenze, come faresti solitamente con il formato HTML in Adobe Campaign, con campi di personalizzazione e blocchi di personalizzazione.

   ![](assets/amp_tab_perso.png)

1. Una volta completata la modifica, seleziona l’intero contenuto AMP e copialo e incollalo nella [Convalida basata su Web AMP](https://validator.ampproject.org) o un sito web simile.

   >[!NOTE]
   >
   >Assicurati di selezionare **E-MAIL AMP4** dall’elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_validator.png)

   Gli errori vengono contrassegnati in linea.

   >[!NOTE]
   >
   >L’editor AMP di Adobe Campaign non è progettato per la convalida del contenuto. Utilizza un sito web esterno come [Convalida basata su Web AMP](https://validator.ampproject.org) per verificare che il contenuto sia corretto.

1. Apporta le modifiche necessarie finché il contenuto AMP non supera la convalida.

   ![](assets/amp_validator_pass.png)

1. Per visualizzare in anteprima il contenuto, copia e incolla il contenuto convalidato in [AMP Playground](https://playground.amp.dev) o un sito web simile.

   >[!NOTE]
   >
   >Assicurati di selezionare **AMP per e-mail** dall’elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Non puoi visualizzare in anteprima il contenuto AMP direttamente in Adobe Campaign. Utilizzare un sito web esterno come [AMP Playground](https://playground.amp.dev).

1. Torna ad Adobe Campaign e copia-incolla il contenuto convalidato in **[!UICONTROL AMP content]** scheda .

1. Passa alla **[!UICONTROL HTML content]** o **[!UICONTROL Text content]** e definire il contenuto per almeno uno di questi due formati.

   >[!IMPORTANT]
   >
   >Se l’e-mail non contiene una versione di testo HTML o normale oltre al contenuto AMP, non può essere inviata.

## AMP per i requisiti di consegna e-mail {#amp-for-email-delivery-requirements}

Quando crei il contenuto AMP in Adobe Campaign, devi soddisfare le condizioni per la consegna di un’e-mail dinamica, specifiche per i provider di posta elettronica dei destinatari.

Attualmente tre provider di posta elettronica supportano il test di questo formato: Gmail, Outlook e Mail.ru.

Tutti i passaggi e le specifiche necessari per testare la consegna con il formato AMP sugli account Gmail sono descritti nel corrispondente [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/)e [Mail.ru](https://postmaster.mail.ru/amp) documentazione per sviluppatori.

In particolare, devono essere soddisfatti i seguenti requisiti:
* Segui i requisiti di sicurezza AMP specifici per [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements)e [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* La parte MIME AMP deve contenere un [documento AMP valido](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* La parte MIME AMP deve essere inferiore a 100 KB.

È inoltre possibile consultare [Suggerimenti e limitazioni note per Gmail](https://developers.google.com/gmail/ampemail/tips) e [Best practice AMP per Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## Indirizzare un’e-mail AMP {#targeting-amp-email}

Attualmente puoi provare a inviare un’e-mail AMP in due passaggi:

1. Adobe Campaign consente di testare la distribuzione di un’e-mail dinamica basata su AMP a indirizzi e-mail selezionati configurati in modo appropriato, al fine di verificarne il contenuto e il comportamento. Vedi [Verifica della consegna e-mail AMP per gli indirizzi selezionati](#testing-amp-delivery-for-selected-addresses).

1. Una volta effettuato il test, puoi inviare una consegna o una campagna come parte del programma AMP for Email registrandoti con i provider di posta elettronica pertinenti per far sì che il dominio del mittente venga aggiunto all’inserire nell&#39;elenco Consentiti. Vedi [Invio di e-mail AMP tramite registrazione con un provider di posta elettronica](#delivering-amp-emails-by-registering).

### Verifica della consegna e-mail AMP per gli indirizzi selezionati {#testing-amp-delivery-for-selected-addresses}

Puoi verificare l’invio di messaggi dinamici da Adobe Campaign agli indirizzi e-mail selezionati.

>[!NOTE]
>
>Attualmente solo Gmail, Outlook e Mail.ru supportano il test del formato AMP.

Per Gmail e Outlook, è innanzitutto necessario aggiungere gli indirizzi del mittente utilizzati nell&#39;inserire nell&#39;elenco Consentiti per la consegna da Adobe Campaign per gli account Gmail e Outlook di cui si sta eseguendo il targeting.

Per eseguire questa operazione:
1. Assicurati che l’opzione che attiva l’e-mail dinamica sia selezionata per i provider e-mail pertinenti.
1. Copia l’indirizzo del mittente visualizzato nel **[!UICONTROL From]** e incollalo nella sezione appropriata delle impostazioni dell’account del provider di posta elettronica.

Per ulteriori dettagli, consulta la [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) e [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) documentazione per sviluppatori.

![](assets/amp_from_field.png)

Per verificare l’invio di un’e-mail AMP a un indirizzo Mail.ru, segui i passaggi descritti nella sezione [Documentazione per gli sviluppatori di Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto) (**Se sei un utente** sezione).

### Invio di e-mail AMP tramite registrazione con un provider di posta elettronica {#delivering-amp-emails-by-registering}

Puoi sperimentare la distribuzione di e-mail dinamiche registrandoti con i provider di posta elettronica supportati in modo da aggiungere il dominio del mittente all’inserire nell&#39;elenco Consentiti.

>[!NOTE]
>
>Attualmente solo Gmail, Outlook e Mail.ru supportano il formato AMP.

Una volta testato con alcuni indirizzi, è possibile inviare e-mail AMP a qualsiasi indirizzo Gmail o Outlook. Per fare questo, è necessario registrarsi rispettosamente con Google o Microsoft e attendere la loro risposta. Segui i passaggi descritti nella [Gmail](https://developers.google.com/gmail/ampemail/register) e [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) documentazione per sviluppatori. Dopo la registrazione, diventerai un mittente autorizzato.

Per inviare e-mail AMP agli indirizzi Mail.ru, segui i requisiti e i passaggi elencati in [Documentazione per gli sviluppatori di Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto) (**Se sei un mittente e-mail** sezione).

## Invia un messaggio e-mail AMP {#sending-amp-email}

Una volta che il contenuto e il fallback AMP sono pronti e una volta definito un target compatibile, puoi inviare l’e-mail come faresti normalmente.

Attualmente solo Gmail, Outlook e Mail.ru supportano il formato AMP, in determinate condizioni. Puoi eseguire il targeting degli indirizzi di altri provider di posta elettronica, ma questi riceveranno la versione HTML o testo normale della tua e-mail.

>[!IMPORTANT]
>
>Se l’e-mail non contiene una versione di testo HTML o normale oltre al contenuto AMP, non può essere inviata.

I destinatari corrispondenti avranno la versione AMP dell’e-mail visualizzata nella loro casella di posta.

Ad esempio, se includi un elenco di prodotti nell’e-mail, quando modifichi i prezzi in un sistema di terze parti i prezzi verranno automaticamente modificati ogni volta che i destinatari aprono nuovamente l’e-mail nella propria casella di posta.

>[!NOTE]
>
>Puoi creare una regola di elaborazione della posta per impedire a domini specifici di ricevere e-mail AMP. Vedi [Gestione dei formati e-mail](../../installation/using/email-deliverability.md#managing-email-formats).
>
>Per impostazione predefinita, **[!UICONTROL AMP inclusion]** è impostata su **[!UICONTROL No]**.

## Video tutorial {#amp-email-video}

Il video seguente spiega come attivare AMP in Adobe Campaign e ne illustra l’utilizzo.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

Sono disponibili ulteriori video dimostrativi relativi a Campaign [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
