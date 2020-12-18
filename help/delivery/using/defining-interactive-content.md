---
solution: Campaign Classic
product: campaign
title: Definizione di contenuti interattivi in Adobe Campaign Classic
description: Scoprite come definire contenuti e-mail interattivi e dinamici con AMP in Adobe Campaign Classic.
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '1580'
ht-degree: 3%

---


# Definizione del contenuto interattivo{#defining-interactive-content}

 Adobe Campaign consente di utilizzare il nuovo formato interattivo [AMP for Email](https://amp.dev/about/email/), che consente di inviare e-mail dinamiche a determinate condizioni.

Con AMP per e-mail potete:
* Test della distribuzione di e-mail AMP a indirizzi specifici configurati in modo appropriato.
* Dopo la registrazione con i provider corrispondenti, inviate e-mail AMP agli indirizzi Gmail, Outlook o Mail.ru.

Per ulteriori informazioni sul test e l&#39;invio di e-mail AMP, consultate [Targeting an AMP email](#targeting-amp-email) (Impostazione destinazione di un&#39;e-mail AMP).

Questa funzione è disponibile tramite un pacchetto dedicato in  Adobe Campaign. Per utilizzarlo, il pacchetto deve essere installato. Al termine, riavviate il server per prendere in considerazione il pacchetto.

>[!NOTE]
>
> Per le architetture ibride e ospitate, il pacchetto deve essere installato su tutti i server, incluso il [server di mid-sourcing](../../installation/using/mid-sourcing-server.md) e l&#39;istanza di esecuzione [](../../message-center/using/creating-a-shared-connection.md#execution-instance). Contattate il vostro responsabile commerciale.

## Informazioni su AMP per e-mail {#about-amp-for-email}

Il nuovo formato **AMP for Email** consente di includere componenti AMP nei messaggi per migliorare l&#39;esperienza e-mail con contenuti avanzati e fruibili. Grazie alle funzionalità moderne dell’app disponibili direttamente nelle e-mail, i destinatari possono interagire in modo dinamico con il contenuto all’interno del messaggio stesso.

Ad esempio:
* Le e-mail scritte con AMP possono contenere elementi interattivi quali caroselli di immagini.
* Il contenuto rimane aggiornato nel messaggio.
* I destinatari possono intervenire come se rispondessero a un modulo senza uscire dalla casella in entrata.

AMP per e-mail è compatibile con le e-mail esistenti. La versione AMP del messaggio viene incorporata nell&#39;e-mail come nuova parte MIME, oltre all&#39;HTML e/o al testo normale, garantendo la compatibilità tra tutti i client e-mail.

Per ulteriori informazioni su formato, specifiche e requisiti dell&#39;AMP per l&#39;e-mail, consulta la [documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [Scopri questa funzione nel video](#amp-email-video)

## Passaggi chiave per utilizzare AMP per e-mail con  Adobe Campaign {#key-steps-to-use-amp}

Per testare e inviare correttamente un&#39;e-mail AMP con  Adobe Campaign, segui la procedura seguente:
1. Installate il pacchetto **[!UICONTROL AMP support]**. Consultate [Installazione di pacchetti standard di Campaign](../../installation/using/installing-campaign-standard-packages.md).
1. Create un&#39;e-mail e create il contenuto AMP all&#39;interno  Adobe Campaign. Consultate [Creare contenuto e-mail AMP con  Adobe Campaign](#build-amp-email-content).
1. Accertatevi di rispettare tutti i requisiti di consegna dai provider di posta elettronica che supportano il formato AMP. Consulta [AMP per i requisiti di distribuzione e-mail](#amp-for-email-delivery-requirements).
1. Quando definite il target, accertatevi di selezionare i destinatari che saranno in grado di visualizzare il formato AMP. Consultate [Targeting an AMP email](#targeting-amp-email) (Impostazione destinazione di un&#39;e-mail AMP).

   >[!NOTE]
   >
   >Attualmente è possibile inviare e-mail AMP solo a [indirizzi e-mail specifici](#testing-amp-delivery-for-selected-addresses) (a scopo di test) o dopo [la registrazione](#delivering-amp-emails-by-registering) con i client e-mail supportati.

1. Invia la tua e-mail come faresti di solito. Vedere [Invio di un&#39;e-mail AMP](#sending-amp-email).

## Creazione di contenuto e-mail AMP in  Adobe Campaign {#build-amp-email-content}

Per creare un&#39;e-mail utilizzando il formato AMP, segui i passaggi descritti di seguito.

>[!IMPORTANT]
>
>Accertatevi di seguire l&#39;AMP per i requisiti e le specifiche e-mail descritti nella [documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). È inoltre possibile consultare l&#39; [AMP per le best practice relative alle e-mail](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. Quando create la consegna e-mail, selezionate un modello qualsiasi.

   >[!NOTE]
   >
   >Un modello AMP specifico contiene un esempio delle capacità principali che potete utilizzare: elenco prodotti, carosello, doppio consenso, sondaggio e richiesta server avanzata.

1. Fare clic sulla scheda **[!UICONTROL AMP content]**.

   ![](assets/amp_tab.png)

1. Modificate i contenuti AMP in base alle vostre esigenze.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione della prima e-mail AMP, consultate la [documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   Ad esempio, potete utilizzare il componente elenco prodotti dal modello AMP e mantenere un elenco di prodotti da un sistema di terze parti, o anche all&#39;interno  Adobe Campaign. Ogni volta che regolate un prezzo o un altro elemento, questo verrà riflesso automaticamente quando il destinatario riapre l&#39;e-mail dalla propria cassetta postale.

1. Personalizzate i contenuti AMP in base alle vostre esigenze, come fareste di solito con il formato HTML in  Adobe Campaign, con campi di personalizzazione e blocchi di personalizzazione.

   ![](assets/amp_tab_perso.png)

1. Al termine della modifica, selezionate l&#39;intero contenuto AMP e copiatelo nella [convalida basata sul Web AMP](https://validator.ampproject.org) o in un sito Web simile.

   >[!NOTE]
   >
   >Accertatevi di selezionare **AMP4 EMAIL** dall&#39;elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_validator.png)

   Eventuali errori verranno contrassegnati in linea.

   >[!NOTE]
   >
   >L&#39;editor  Adobe Campaign AMP non è progettato per la convalida del contenuto. Utilizzate un sito Web esterno, ad esempio [AMP web-based validator](https://validator.ampproject.org) per verificare che il contenuto sia corretto.

1. Apportate le modifiche necessarie finché il contenuto AMP non supera la convalida.

   ![](assets/amp_validator_pass.png)

1. Copiate e incollate i contenuti convalidati in [AMP Playground](https://playground.amp.dev) o in un sito Web simile per visualizzare l&#39;anteprima dei contenuti.

   >[!NOTE]
   >
   >Accertatevi di selezionare **AMP for Email** dall&#39;elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Non potete visualizzare l&#39;anteprima del contenuto AMP direttamente in  Adobe Campaign. Utilizzate un sito Web esterno, ad esempio [AMP Playground](https://playground.amp.dev).

1. Tornate  Adobe Campaign e incollate i contenuti convalidati nella scheda **[!UICONTROL AMP content]**.

1. Passate alla scheda **[!UICONTROL HTML content]** o **[!UICONTROL Text content]** e definite il contenuto per almeno uno di questi due formati.

   >[!IMPORTANT]
   >
   >Se il messaggio e-mail non contiene una versione HTML o di testo normale oltre al contenuto AMP, non può essere inviato.

## AMP per i requisiti di distribuzione e-mail {#amp-for-email-delivery-requirements}

Quando crei il contenuto AMP in  Adobe Campaign, devi soddisfare le condizioni per la distribuzione di un&#39;e-mail dinamica, specifiche per i provider di posta elettronica dei destinatari.

Attualmente tre provider di posta elettronica supportano il test di questo formato: Gmail, Outlook e Mail.ru.

Tutti i passaggi e le specifiche necessari per testare la consegna con formato AMP sugli account Gmail sono descritti in dettaglio nelle corrispondenti documentazione per gli sviluppatori [Gmail](https://developers.google.com/gmail/ampemail?), [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/) e [Mail.ru](https://postmaster.mail.ru/amp).

In particolare, devono essere soddisfatti i seguenti requisiti:
* Seguire i requisiti di sicurezza AMP specifici per [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) e [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* La parte MIME AMP deve contenere un [documento AMP valido](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* La parte MIME AMP deve essere inferiore a 100 KB.

È inoltre possibile consultare i [Suggerimenti e le limitazioni note per Gmail](https://developers.google.com/gmail/ampemail/tips) e le [Best practice AMP per Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices).

## Targeting di un&#39;e-mail AMP {#targeting-amp-email}

Attualmente puoi provare a inviare un messaggio e-mail AMP in due passaggi:

1.  Adobe Campaign consente di testare la distribuzione di un&#39;e-mail dinamica basata su AMP a indirizzi e-mail selezionati configurati in modo appropriato, al fine di verificarne il contenuto e il comportamento. Vedere [Verifica della consegna di e-mail AMP per gli indirizzi selezionati](#testing-amp-delivery-for-selected-addresses).

1. Una volta verificato, è possibile inviare una consegna o una campagna come parte del programma AMP per e-mail registrandosi presso i provider di posta elettronica pertinenti per fare in modo che il dominio del mittente venga aggiunto al elenco consentiti . Consultate [Invio di e-mail AMP tramite registrazione presso un provider di posta elettronica](#delivering-amp-emails-by-registering).

### Verifica della consegna di e-mail AMP per gli indirizzi selezionati {#testing-amp-delivery-for-selected-addresses}

È possibile verificare l&#39;invio di messaggi dinamici da  Adobe Campaign agli indirizzi e-mail selezionati.

>[!NOTE]
>
>Attualmente solo Gmail, Outlook e Mail.ru supportano il test del formato AMP.

Per Gmail e Outlook, è innanzitutto necessario aggiungere gli indirizzi del mittente che si sta utilizzando al inserire nell&#39;elenco Consentiti di  per distribuire da  Adobe Campaign per gli account Gmail e Outlook di destinazione.

Per eseguire questa operazione:
1. Verificate che l&#39;opzione che attiva l&#39;e-mail dinamica sia selezionata per i provider e-mail pertinenti.
1. Copiate l&#39;indirizzo del mittente visualizzato nel campo **[!UICONTROL From]** della consegna e incollatelo nella sezione appropriata delle impostazioni dell&#39;account del provider di posta elettronica.

Per ulteriori dettagli, consultare la documentazione per gli sviluppatori [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) e [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration).

![](assets/amp_from_field.png)

Per testare l&#39;invio di un&#39;e-mail AMP a un indirizzo Mail.ru, seguire i passaggi descritti nella [Documentazione sviluppatore Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto) (**Se si è un utente**).

### Invio di e-mail AMP tramite registrazione presso un provider di posta elettronica {#delivering-amp-emails-by-registering}

È possibile provare a distribuire e-mail dinamiche registrandosi presso i provider di posta elettronica supportati per fare in modo che il dominio del mittente venga aggiunto al elenco consentiti .

>[!NOTE]
>
>Attualmente solo Gmail, Outlook e Mail.ru supportano il formato AMP.

Una volta testati con alcuni indirizzi, potete inviare e-mail AMP a qualsiasi indirizzo Gmail o Outlook. Per fare questo, dovete registrarvi rispettosamente con Google o Microsoft, e attendere la loro risposta. Seguite i passaggi descritti nella documentazione per gli sviluppatori [Gmail](https://developers.google.com/gmail/ampemail/register) e [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration). Dopo la registrazione, si diventa un mittente autorizzato.

Per inviare e-mail AMP agli indirizzi Mail.ru, segui i requisiti e i passaggi elencati nella [Documentazione sviluppatore Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto) (**Se sei un mittente e-mail**).

## Invio di un&#39;e-mail AMP {#sending-amp-email}

Una volta pronti i contenuti e i fallback AMP e una volta definiti una destinazione compatibile, potete inviare l’e-mail come fareste normalmente.

Attualmente solo Gmail, Outlook e Mail.ru supportano il formato AMP, a determinate condizioni. Potete eseguire il targeting degli indirizzi di altri provider di posta elettronica, ma questi riceveranno la versione HTML o in testo normale dell&#39;e-mail.

>[!IMPORTANT]
>
>Se il messaggio e-mail non contiene una versione HTML o di testo normale oltre al contenuto AMP, non può essere inviato.

I destinatari corrispondenti avranno la versione AMP dell’e-mail visualizzata nella propria cassetta postale.

Ad esempio, se hai incluso un elenco di prodotti nel messaggio e-mail, quando modifichi i prezzi in un sistema di terze parti, i prezzi verranno automaticamente modificati ogni volta che i destinatari riaprono il messaggio e-mail nella loro casella di posta.

>[!NOTE]
>
>Potete creare una regola di elaborazione della posta per impedire a domini specifici di ricevere e-mail AMP. Consultate [Gestione dei formati e-mail](../../installation/using/email-deliverability.md#managing-email-formats).
>
>Per impostazione predefinita, l&#39;opzione **[!UICONTROL AMP inclusion]** è impostata su **[!UICONTROL No]**.

## Video di esercitazione {#amp-email-video}

Il video seguente spiega come attivare AMP in Adobe Campaign Classic e ne illustra l’utilizzo.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
