---
title: Definizione di contenuti interattivi in Adobe Campaign Classic
description: Scoprite come definire contenuti e-mail interattivi e dinamici con AMP in Adobe Campaign Classic.
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a5711c4478f8378c079fec4792ecbb95266ad4b
workflow-type: tm+mt
source-wordcount: '1616'
ht-degree: 0%

---


# Definizione del contenuto interattivo{#defining-interactive-content}

 Adobe Campaign consente di provare il nuovo formato [AMP per e-mail](https://amp.dev/about/email/) interattivo, che consente di inviare e-mail dinamiche, a determinate condizioni.

In questa versione è possibile:
* Test della distribuzione di e-mail AMP a indirizzi specifici configurati in modo appropriato.
* Dopo la registrazione con i provider corrispondenti, inviate e-mail AMP agli indirizzi Gmail, Outlook o Mail.ru.

Per ulteriori informazioni sul test e l&#39;invio di e-mail AMP, consultate [Targeting an AMP email](#targeting-amp-email)(Impostazione del targeting di un&#39;e-mail AMP).

Questa funzione è disponibile tramite un pacchetto dedicato in  Adobe Campaign. Per utilizzarlo, il pacchetto deve essere installato. Al termine, riavviate il server per prendere in considerazione il pacchetto.

>[!NOTE]
>>Per le architetture ibride e ospitate, il pacchetto deve essere installato su tutti i server, incluso il server [](../../installation/using/mid-sourcing-server.md) mid-sourcing e l&#39;istanza [di](../../message-center/using/creating-a-shared-connection.md#execution-instance)esecuzione. Contattate il vostro responsabile commerciale.


## Informazioni su AMP per e-mail {#about-amp-for-email}

Il nuovo formato **AMP per e-mail** consente di includere componenti AMP nei messaggi per migliorare l&#39;esperienza e-mail con contenuti avanzati e fruibili. Grazie alle moderne funzionalità delle app disponibili direttamente nelle e-mail, i destinatari possono interagire in modo dinamico con il contenuto del messaggio stesso.

Ad esempio:
* Le e-mail scritte con AMP possono contenere elementi interattivi quali caroselli di immagini.
* Il contenuto rimane aggiornato nel messaggio.
* I destinatari possono intervenire come se rispondessero a un modulo senza uscire dalla casella in entrata.

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#amp-email-video)

AMP per e-mail è compatibile con le e-mail esistenti. La versione AMP del messaggio viene incorporata nell&#39;e-mail come nuova parte MIME, oltre all&#39;HTML e/o al testo normale, garantendo la compatibilità tra tutti i client e-mail.

Per ulteriori informazioni su formato e specifiche dell&#39;e-mail AMP, consultate la documentazione [per gli sviluppatori](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)AMP.

## Passaggi chiave per utilizzare AMP per e-mail con  Adobe Campaign {#key-steps-to-use-amp}

Per testare e inviare correttamente un&#39;e-mail AMP con  Adobe Campaign, segui la procedura seguente:
1. Installate il **[!UICONTROL AMP support (Beta)]** pacchetto. Consultate [Installazione di pacchetti](../../installation/using/installing-campaign-standard-packages.md)standard di Campaign.
1. Create un&#39;e-mail e create il contenuto AMP all&#39;interno  Adobe Campaign. Consultate [Creare contenuto e-mail AMP con  Adobe Campaign](#build-amp-email-content).
1. Accertatevi di rispettare tutti i requisiti di consegna dai provider di posta elettronica che supportano il formato AMP. Consultate [AMP per i requisiti](#amp-for-email-delivery-requirements)di distribuzione e-mail.

   >[!NOTE]
   >
   >AMP per e-mail è disponibile come funzionalità beta per il test. Al momento solo alcuni provider di posta elettronica supportano il test di questo formato.

1. Quando definite il target, accertatevi di selezionare i destinatari che saranno in grado di visualizzare il formato AMP. Consultate [Destinazione di un’e-mail](#targeting-amp-email)AMP.

   >[!NOTE]
   >
   >Attualmente è possibile testare la distribuzione di e-mail AMP a indirizzi e-mail specifici configurati in modo appropriato o dopo la registrazione solo con i provider di posta elettronica che partecipano al programma beta di AMP.

1. Invia la tua e-mail come faresti di solito. Consultate [Invio di un’e-mail](#sending-amp-email)AMP.

## Creazione di contenuto e-mail AMP in  Adobe Campaign {#build-amp-email-content}

Per creare un&#39;e-mail utilizzando il formato AMP, segui i passaggi descritti di seguito.

>[!IMPORTANT]
>
>Accertatevi di seguire l&#39;AMP per i requisiti e le specifiche e-mail descritti dettagliatamente nella documentazione [per gli sviluppatori](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)AMP. Potete inoltre consultare l&#39; [AMP per le best practice relative](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)all&#39;e-mail.

1. Quando create la consegna e-mail, selezionate un modello qualsiasi.

   >[!NOTE]
   >
   >Un modello AMP specifico contiene un esempio delle capacità principali che potete utilizzare: elenco prodotti, carosello, doppio consenso, sondaggio e richiesta server avanzata.

1. Fate clic sulla **[!UICONTROL AMP content]** scheda.

   ![](assets/amp_tab.png)

1. Modificate i contenuti AMP in base alle vostre esigenze.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione della prima e-mail AMP, consulta la documentazione [per gli sviluppatori](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)AMP.

   Ad esempio, potete utilizzare il componente elenco prodotti dal modello AMP e mantenere un elenco di prodotti da un sistema di terze parti, o anche all&#39;interno  Adobe Campaign. Ogni volta che regolate un prezzo o un altro elemento, questo verrà riflesso automaticamente quando il destinatario riapre l&#39;e-mail dalla propria cassetta postale.

1. Personalizzate i contenuti AMP in base alle vostre esigenze, come fareste di solito con il formato HTML in  Adobe Campaign, con campi di personalizzazione e blocchi di personalizzazione.

   ![](assets/amp_tab_perso.png)

1. Al termine della modifica, selezionate l’intero contenuto AMP e copiatelo nella funzione di convalida [basata su Web](https://validator.ampproject.org) AMP o in un sito Web simile.

   >[!NOTE]
   >
   >Accertatevi di selezionare **AMP4 EMAIL** dall&#39;elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_validator.png)

   Eventuali errori verranno contrassegnati in linea.

   >[!NOTE]
   >
   >L&#39;editor  Adobe Campaign AMP non è progettato per la convalida del contenuto. Utilizzate un sito Web esterno, ad esempio il validatore [basato su Web](https://validator.ampproject.org) AMP, per verificare che il contenuto sia corretto.

1. Apportate le modifiche necessarie finché il contenuto AMP non supera la convalida.

   ![](assets/amp_validator_pass.png)

1. Copiate e incollate i contenuti convalidati in [AMP Playground](https://playground.amp.dev) o in un sito Web simile per visualizzarne l’anteprima.

   >[!NOTE]
   >
   >Accertatevi di selezionare **AMP per E-mail** dall&#39;elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Non potete visualizzare l&#39;anteprima del contenuto AMP direttamente in  Adobe Campaign. Utilizzate un sito Web esterno, ad esempio [AMP Playground](https://playground.amp.dev).

1. Tornate  Adobe Campaign e incollate i contenuti convalidati nella **[!UICONTROL AMP content]** scheda.

1. Passate alla **[!UICONTROL HTML content]** scheda o **[!UICONTROL Text content]** e definite il contenuto per almeno uno di questi due formati.

   >[!IMPORTANT]
   >
   >Se il messaggio e-mail non contiene una versione HTML o di testo normale oltre al contenuto AMP, non può essere inviato.

## AMP per i requisiti di distribuzione e-mail {#amp-for-email-delivery-requirements}

Quando crei il contenuto AMP in  Adobe Campaign, devi soddisfare le condizioni per la distribuzione di un&#39;e-mail dinamica, specifiche per i provider di posta elettronica dei destinatari.

Attualmente tre provider di posta elettronica supportano il test di questo formato: Gmail, Outlook e Mail.ru.

Tutti i passaggi e le specifiche necessari per testare la consegna con il formato AMP sugli account Gmail sono descritti in dettaglio nelle corrispondenti documentazione per sviluppatori [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/) e [Mail.ru](https://postmaster.mail.ru/amp) .

In particolare, devono essere soddisfatti i seguenti requisiti:
* Seguite i requisiti di sicurezza AMP specifici per [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) e [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* La parte MIME AMP deve contenere un documento [AMP](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)valido.
* La parte MIME AMP deve essere inferiore a 100 KB.

Potete inoltre consultare i [suggerimenti e le limitazioni note per Gmail](https://developers.google.com/gmail/ampemail/tips) e le best practice [AMP per Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## Targeting di un&#39;e-mail AMP {#targeting-amp-email}

AMP per e-mail essendo disponibile come funzionalità beta, al momento è possibile provare a inviare un&#39;e-mail AMP in due passaggi:

1.  Adobe Campaign consente di testare la distribuzione di un&#39;e-mail dinamica basata su AMP a indirizzi e-mail selezionati configurati in modo appropriato, al fine di verificarne il contenuto e il comportamento. Consultate [Verifica della consegna di e-mail AMP per gli indirizzi](#testing-amp-delivery-for-selected-addresses)selezionati.
1. Una volta verificato, è possibile inviare una consegna o una campagna come parte del programma AMP per la versione beta dell&#39;e-mail registrandosi presso i provider di posta elettronica interessati per fare in modo che il dominio del mittente venga aggiunto al elenco consentiti . Consultate [Distribuzione di e-mail AMP tramite registrazione presso un provider](#delivering-amp-emails-by-registering)di posta elettronica.

### Verifica della consegna di e-mail AMP per gli indirizzi selezionati {#testing-amp-delivery-for-selected-addresses}

È possibile verificare l&#39;invio di messaggi dinamici da  Adobe Campaign agli indirizzi e-mail selezionati.

>[!NOTE]
>
>Attualmente solo Gmail, Outlook e Mail.ru supportano il test del formato AMP.

Per Gmail e Outlook, è innanzitutto necessario aggiungere gli indirizzi del mittente che si sta utilizzando al elenco consentiti  per distribuire da  Adobe Campaign per gli account Gmail e Outlook di destinazione.

Per eseguire questa operazione:
1. Verificate che l&#39;opzione che attiva l&#39;e-mail dinamica sia selezionata per i provider e-mail pertinenti.
1. Copiate l&#39;indirizzo del mittente visualizzato nel **[!UICONTROL From]** campo della consegna e incollatelo nella sezione appropriata delle impostazioni dell&#39;account del provider di posta elettronica.

Per ulteriori dettagli, consultate la documentazione per gli sviluppatori [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) e [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) .

![](assets/amp_from_field.png)

Per testare l&#39;invio di un&#39;e-mail AMP a un indirizzo Mail.ru, seguite i passaggi descritti nella documentazione [per gli sviluppatori](https://postmaster.mail.ru/amp/?lang=en#howto) Mail.ru (**Se siete una sezione utente** ).

### Distribuzione di e-mail AMP tramite registrazione presso un provider di posta elettronica {#delivering-amp-emails-by-registering}

È possibile provare a distribuire e-mail dinamiche registrandosi presso i provider di posta elettronica che partecipano al programma beta di AMP per fare in modo che il dominio del mittente venga aggiunto al elenco consentiti .

>[!NOTE]
>
>Attualmente solo Gmail, Outlook e Mail.ru supportano il formato AMP.

Una volta testati con alcuni indirizzi, potete inviare e-mail AMP a qualsiasi indirizzo Gmail o Outlook. Per fare questo, dovete registrarvi rispettosamente con Google o Microsoft, e attendere la loro risposta. Seguite i passaggi descritti nella documentazione per gli sviluppatori [Gmail](https://developers.google.com/gmail/ampemail/register) e [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) . Dopo la registrazione, si diventa un mittente autorizzato.

Per inviare e-mail AMP agli indirizzi Mail.ru, seguite i requisiti e i passaggi elencati nella documentazione [per gli sviluppatori](https://postmaster.mail.ru/amp/?lang=en#howto) Mail.ru (**Se siete un mittente** e-mail).

## Invio di un messaggio e-mail AMP {#sending-amp-email}

Una volta pronti i contenuti e i fallback AMP e una volta definiti una destinazione compatibile, potete inviare l’e-mail come fareste normalmente.

Attualmente solo Gmail, Outlook e Mail.ru supportano il formato AMP, a determinate condizioni. Potete eseguire il targeting degli indirizzi di altri provider di posta elettronica, ma questi riceveranno la versione HTML o in testo normale dell&#39;e-mail.

>[!IMPORTANT]
>
>Se il messaggio e-mail non contiene una versione HTML o di testo normale oltre al contenuto AMP, non può essere inviato.

I destinatari corrispondenti avranno la versione AMP dell’e-mail visualizzata nella propria cassetta postale.

Ad esempio, se hai incluso un elenco di prodotti nel messaggio e-mail, quando modifichi i prezzi in un sistema di terze parti, i prezzi verranno automaticamente modificati ogni volta che i destinatari riaprono il messaggio e-mail nella loro casella di posta.

>[!NOTE]
>
>Potete creare una regola di elaborazione della posta per impedire a domini specifici di ricevere e-mail AMP. Consultate [Gestione dei formati](../../installation/using/email-deliverability.md#managing-email-formats)e-mail.
>
>Per impostazione predefinita, l’ **[!UICONTROL AMP inclusion]** opzione è impostata su **[!UICONTROL No]**.

## Come attivare e utilizzare AMP per le e-mail {#amp-email-video}

Il video seguente spiega come attivare AMP in Adobe Campaign Classic e ne illustra l’utilizzo.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)
