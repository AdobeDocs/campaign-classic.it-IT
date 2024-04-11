---
product: campaign
title: Definire il contenuto interattivo in Adobe Campaign Classic
description: Scopri come definire contenuti e-mail interattivi e dinamici con AMP in Adobe Campaign
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
feature: Email Design
role: User
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1422'
ht-degree: 3%

---

# Definire il contenuto interattivo{#defining-interactive-content}

Adobe Campaign consente di utilizzare il [AMP per e-mail](https://amp.dev/about/email/) che consente di inviare e-mail dinamiche, in determinate condizioni.

Con AMP per e-mail, puoi:
* Verifica la consegna di e-mail AMP a indirizzi specifici configurati in modo appropriato.
* Consegna le e-mail AMP agli indirizzi Gmail o Mail.ru dopo la registrazione ai provider corrispondenti.

Per ulteriori informazioni sul test e sull’invio di e-mail AMP, consulta [questa sezione](#targeting-amp-email).

Questa funzione è disponibile tramite un pacchetto dedicato in Adobe Campaign. A seconda delle autorizzazioni e del modello di distribuzione, puoi installare questo pacchetto o rivolgerti ad Adobe per installarlo al posto tuo.

>[!NOTE]
>
> Per le architetture ibride e in hosting, il pacchetto deve essere installato su tutti i server, incluso [server di mid-sourcing](../../installation/using/mid-sourcing-server.md) e [istanza di esecuzione](../../message-center/using/configuring-instances.md#execution-instance).


## Informazioni su AMP per e-mail {#about-amp-for-email}

Utilizza il **AMP per e-mail** nuovo formato per includere nei messaggi i componenti AMP e migliorare l’esperienza e-mail con contenuti avanzati e fruibili. Integrando direttamente nelle e-mail le funzionalità tipiche delle app, i destinatari possono interagire in modo dinamico con il contenuto stesso del messaggio.

Ad esempio:
* Le e-mail scritte con AMP possono contenere elementi interattivi come caroselli di immagini.
* Il contenuto del messaggio rimane aggiornato.
* I destinatari possono rispondere a un modulo senza uscire dalla casella in entrata.

AMP for Email è compatibile con le e-mail esistenti. La versione AMP del messaggio è incorporata nell’e-mail come nuova parte MIME, oltre al HTML e/o al testo normale, garantendo la compatibilità tra tutti i client e-mail.

Per ulteriori informazioni sul formato, le specifiche e i requisiti dell’AMP per e-mail, consulta la sezione [Documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [Guarda il video su questa funzione](#amp-email-video)

## Passaggi chiave per utilizzare AMP per e-mail con Adobe Campaign {#key-steps-to-use-amp}

Per verificare e inviare correttamente un’e-mail AMP con Adobe Campaign, segui i passaggi seguenti:
1. Installare **[!UICONTROL AMP support]** pacchetto. Consulta [Installazione dei pacchetti incorporati di Campaign](../../installation/using/installing-campaign-standard-packages.md).
1. Crea un messaggio e-mail e crea i contenuti AMP in Adobe Campaign. Consulta [Creare contenuti e-mail AMP con Adobe Campaign](#build-amp-email-content).
1. Assicurati di rispettare tutti i requisiti di consegna dai provider e-mail che supportano il formato AMP. Consulta [AMP per i requisiti di consegna e-mail](#amp-for-email-delivery-requirements).
1. Quando definisci il target, accertati di selezionare i destinatari che saranno in grado di visualizzare il formato AMP. Consulta [Targeting di un’e-mail AMP](#targeting-amp-email).

   >[!NOTE]
   >
   >Attualmente puoi inviare e-mail AMP solo a [indirizzi e-mail specifici](#testing-amp-delivery-for-selected-addresses) (a scopo di test) o dopo [registrazione](#delivering-amp-emails-by-registering) con i client e-mail supportati.

1. Invia la tua e-mail come faresti normalmente. Consulta [Invio di un’e-mail AMP](#sending-amp-email).

## Creare contenuti e-mail AMP in Adobe Campaign {#build-amp-email-content}

Per creare un’e-mail utilizzando il formato AMP, segui i passaggi indicati di seguito.

>[!IMPORTANT]
>
>Assicurati di seguire l’AMP per i requisiti e le specifiche delle e-mail descritti in [Documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). È inoltre possibile consultare [Best practice AMP per le e-mail](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. Durante la creazione della consegna e-mail, seleziona un modello qualsiasi.

   >[!NOTE]
   >
   >Un modello AMP specifico contiene un esempio delle capacità principali che puoi utilizzare: elenco dei prodotti, carosello, doppio consenso, sondaggio e richiesta avanzata di server.

1. Fai clic su **[!UICONTROL AMP content]** scheda.

   ![](assets/amp_tab.png)

1. Modifica il contenuto AMP in base alle tue esigenze.

   >[!NOTE]
   >
   >Per ulteriori informazioni sulla creazione del primo messaggio e-mail AMP, consulta [Documentazione per gli sviluppatori AMP](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   Ad esempio, puoi utilizzare il componente elenco prodotti dal modello AMP e gestire un elenco di prodotti da un sistema di terze parti, o anche all’interno di Adobe Campaign. Ogni volta che regoli un prezzo o un altro elemento, questo viene automaticamente visualizzato quando i destinatari aprono l’e-mail dalla loro cassetta postale.

1. Personalizza il contenuto AMP in base alle esigenze, come faresti solitamente con il formato HTML in Adobe Campaign, con campi di personalizzazione e blocchi di personalizzazione.

   ![](assets/amp_tab_perso.png)

1. Al termine della modifica, seleziona l’intero contenuto AMP e copialo e incollalo nella [Convalida basata su Web AMP](https://validator.ampproject.org) o un sito Web simile.

   >[!NOTE]
   >
   >Assicurati di selezionare **E-MAIL AMP4** dall’elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_validator.png)

   Gli errori vengono contrassegnati in linea.

   >[!NOTE]
   >
   >L’editor AMP di Adobe Campaign non è progettato per la convalida dei contenuti. Utilizza un sito web esterno come [Convalida basata su Web AMP](https://validator.ampproject.org) per verificare che il contenuto sia corretto.

1. Apporta le modifiche necessarie fino a quando il contenuto AMP non supera la convalida.

   ![](assets/amp_validator_pass.png)

1. Per visualizzare l’anteprima del contenuto, copia e incolla il contenuto convalidato in [Playground AMP](https://playground.amp.dev) o un sito Web simile.

   >[!NOTE]
   >
   >Assicurati di selezionare **AMP per e-mail** dall’elenco a discesa nella parte superiore dello schermo.

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >Non puoi visualizzare l’anteprima del contenuto AMP direttamente in Adobe Campaign. Utilizza un sito web esterno come [Playground AMP](https://playground.amp.dev).

1. Torna ad Adobe Campaign e copia e incolla il contenuto convalidato in **[!UICONTROL AMP content]** scheda.

1. Passa a **[!UICONTROL HTML content]** o **[!UICONTROL Text content]** e definiscono il contenuto per almeno uno di questi due formati.

   >[!IMPORTANT]
   >
   >Se l’e-mail non contiene una versione HTML o di testo normale oltre al contenuto AMP, non può essere inviata.

## AMP per i requisiti di consegna e-mail {#amp-for-email-delivery-requirements}

Quando crei il contenuto AMP in Adobe Campaign, devi soddisfare le condizioni per la consegna di un’e-mail dinamica, specifiche per i provider e-mail dei destinatari.

Attualmente due provider di posta elettronica supportano il test di questo formato: Gmail e Mail.ru.

Tutti i passaggi e le specifiche necessari per testare la consegna in formato AMP sugli account Gmail sono descritti nel [Gmail](https://developers.google.com/gmail/ampemail?), e [Mail.ru](https://postmaster.mail.ru/amp) documentazione per gli sviluppatori.

In particolare, devono essere soddisfatti i seguenti requisiti:
* Segui i requisiti di sicurezza AMP specifici per [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), e [Mail.ru](https://postmaster.mail.ru/amp/#howto).
* La parte MIME AMP deve contenere [documento AMP valido](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* La parte MIME AMP deve essere inferiore a 100 KB.

È inoltre possibile consultare [Suggerimenti e limitazioni note per Gmail](https://developers.google.com/gmail/ampemail/tips) documentazione.

## Eseguire il targeting di un’e-mail AMP {#targeting-amp-email}

Al momento puoi sperimentare l’invio di un’e-mail AMP in due passaggi:

1. Adobe Campaign consente di testare la consegna di un’e-mail dinamica basata su AMP a indirizzi e-mail selezionati configurati in modo appropriato, al fine di verificarne il contenuto e il comportamento. Consulta [Verifica della consegna e-mail AMP per gli indirizzi selezionati](#testing-amp-delivery-for-selected-addresses).

1. Una volta testato, puoi inviare una consegna o una campagna come parte del programma AMP per e-mail registrandoti con i provider e-mail pertinenti per far aggiungere il dominio del mittente al inserisco nell&#39;elenco Consentiti di. Consulta [Consegna di e-mail AMP tramite registrazione a un provider e-mail](#delivering-amp-emails-by-registering).

### Verifica della consegna e-mail AMP per gli indirizzi selezionati {#testing-amp-delivery-for-selected-addresses}

Puoi verificare l’invio di messaggi dinamici da Adobe Campaign a indirizzi e-mail selezionati.

>[!NOTE]
>
>Solo Gmail e Mail.ru supportano il test del formato AMP.

Per Gmail, devi innanzitutto aggiungere gli indirizzi del mittente che stai utilizzando al inserisco nell&#39;elenco Consentiti di consegna da Adobe Campaign per gli account Gmail di cui stai eseguendo il targeting.

Per eseguire questa operazione:
1. Assicurati che l’opzione di abilitazione dell’e-mail dinamica sia selezionata per i provider e-mail pertinenti.
1. Copia l’indirizzo del mittente visualizzato nel file **[!UICONTROL From]** e incollarlo nella sezione appropriata delle impostazioni dell’account del provider di posta elettronica.

Per ulteriori dettagli, consultare il [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) documentazione per gli sviluppatori.

![](assets/amp_from_field.png)

Per verificare l’invio di un’e-mail AMP a un indirizzo Mail.ru, segui la procedura descritta nella sezione [Documentazione per gli sviluppatori di Mail.ru](https://postmaster.mail.ru/amp/#howto) (**Se sei un utente** sezione ).

### Consegna di e-mail AMP tramite registrazione a un provider e-mail {#delivering-amp-emails-by-registering}

Puoi sperimentare la distribuzione di e-mail dinamiche registrandoti con i provider di e-mail supportati per aggiungere il dominio del mittente al inserisco nell&#39;elenco Consentiti di.

>[!NOTE]
>
>Solo Gmail e Mail.ru supportano il formato AMP.

Una volta testati con alcuni indirizzi, puoi inviare e-mail AMP a qualsiasi indirizzo Gmail. A questo scopo, è necessario registrarsi a Google e attendere la risposta. Segui i passaggi descritti in [Gmail](https://developers.google.com/gmail/ampemail/register) documentazione per gli sviluppatori. Dopo la registrazione, l&#39;utente diventa un mittente autorizzato.

Per inviare e-mail AMP agli indirizzi Mail.ru, segui i requisiti e i passaggi elencati nella [Documentazione per gli sviluppatori di Mail.ru](https://postmaster.mail.ru/amp/#howto) (**Se sei un mittente e-mail** sezione ).

## Inviare un’e-mail AMP {#sending-amp-email}

Una volta che il contenuto AMP e il fallback sono pronti e una volta definita una destinazione compatibile, puoi inviare l’e-mail come faresti normalmente.

Attualmente solo Gmail e Mail.ru supportano il formato AMP, a determinate condizioni. Puoi eseguire il targeting degli indirizzi di altri provider di posta elettronica, che però riceveranno la versione HTML o in testo normale dell’e-mail.

>[!IMPORTANT]
>
>Se l’e-mail non contiene una versione HTML o di testo normale oltre al contenuto AMP, non può essere inviata.

I destinatari corrispondenti visualizzeranno la versione AMP dell’e-mail nella propria cassetta postale.

Ad esempio, se hai incluso un elenco di prodotti nell’e-mail, quando modifichi i prezzi in un sistema di terze parti, i prezzi verranno automaticamente adeguati ogni volta che i destinatari aprono di nuovo l’e-mail nella loro casella di posta.

>[!NOTE]
>
>Puoi creare una regola di elaborazione della posta per impedire a domini specifici di ricevere e-mail AMP. Consulta [Gestione dei formati e-mail](../../installation/using/email-deliverability.md#managing-email-formats).
>
>Per impostazione predefinita, il **[!UICONTROL AMP inclusion]** è impostata su **[!UICONTROL No]**.

## Video tutorial {#amp-email-video}

Il video seguente spiega come attivare AMP in Adobe Campaign e ne illustra l’utilizzo.

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

Sono disponibili altri video dimostrativi di Campaign [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
