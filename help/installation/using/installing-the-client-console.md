---
product: campaign
title: Installazione della console client
description: Scopri come installare la console client
feature: Installation, Upgrade
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 1%

---

# Installare e aggiornare la console client di Campaign{#installing-the-client-console}

La console client di Campaign è un client avanzato che consente di connettersi ai server dell’applicazione Campaign.

Prima di iniziare l’installazione della console client, è necessario:

* Verifica la compatibilità del sistema e degli strumenti con Adobe Campaign nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Ottenere l’URL del server Campaign
* Ottieni le credenziali utente
* Installare Microsoft Edge Webview2 Runtime (dalla versione di build Campaign Classic 7.3). [Ulteriori informazioni](#webview)

Il processo di installazione o aggiornamento della console client varia a seconda dell’implementazione di Adobe Campaign Classic.
Rivedi i dettagli riportati di seguito per capire cosa è necessario per l’implementazione.

![](assets/do-not-localize/how-to-video.png) Scopri come installare e configurare il client Adobe Campaign in [video](#video)

>[!CAUTION]
>
>* La console del client di Campaign e il server applicazioni di Campaign devono essere eseguiti **sulla stessa versione del prodotto**. Adobe consiglia inoltre vivamente di utilizzare **stessa build del prodotto**. Scopri come controllare le versioni client e server di Campaign in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).
>
>* L&#39;accesso alla cartella di installazione in cui è installata la console deve essere limitato solo all&#39;utente desiderato, assicurandosi che le autorizzazioni di scrittura siano limitate di conseguenza.



## Installazione runtime di Microsoft Edge Webview2 {#webview}

A partire dalla versione della build Campaign Classic 7.3, l’installazione di Microsoft Edge Webview 2 Runtime è necessaria per qualsiasi installazione della console.

La visualizzazione Web è installata per impostazione predefinita come parte del sistema operativo Windows 11. Se non è già presente nel sistema, Campaign Classic Console Installer ti chiederà di scaricarlo da [Sito Web Microsoft Developer](https://www.adobe.com/go/acc-ms-webview2-runtime-download). Il collegamento di download non funziona nel browser Internet Explorer 11 in quanto Microsoft ne ha dichiarato obsoleto il supporto. Utilizza un browser diverso per accedere al collegamento.

## Adobe di implementazioni in hosting {#hosted-customers}

In qualità di cliente in hosting, hai a disposizione due opzioni per installare o aggiornare le console client:

1. Adobe può distribuire direttamente. Una volta aggiornata la console, agli utenti verrà richiesto di scaricare l’ultima versione della console client in una finestra pop-up.

1. Puoi scaricare nelle console client da [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)

   **Per completare l’aggiornamento, gli utenti dovranno disporre dell’accesso di amministratore. Se gli utenti non dispongono di diritti di amministratore, un amministratore di sistema dovrà distribuire su tutte le console client**

## Implementazioni ibride e on-premise {#hybrid-onprem-customers}

Per poter accedere all’istanza creata e configurata, gli utenti di Adobe Campaign devono utilizzare la console client.

### Rendere la console disponibile agli utenti {#make-console-available}

Quando il computer utilizzato per avviare un server applicazioni di Adobe Campaign (nlserver web) riceve connessioni utente dalla console client, è possibile configurarlo per rendere disponibile il programma di installazione per il client avanzato di Adobe Campaign tramite un&#39;interfaccia HTML. Ogni volta che è disponibile una nuova versione della console client, gli utenti vengono invitati a scaricarla all’avvio della console client.

A questo scopo, devi:

1. Selezionare il pacchetto contenente il programma di installazione della console.

   Questo file è denominato setup-client-7.X.XXXX.exe, dove X è la sottoversione di Adobe Campaign e XXXX è il numero di build.

1. Copia e incolla questo pacchetto nella cartella di installazione di Adobe Campaign (sul server di marketing per le installazioni ibride), in /datakit/nl/eng/jsp.

1. Avvia il server Adobe Campaign.


### Non chiedere più questa opzione

Adobe consiglia di lasciare l’opzione **[!UICONTROL No longer ask this question]** deselezionato per assicurarsi che tutti gli utenti vengano avvisati quando è disponibile una nuova versione della console.  Se questa opzione è selezionata, l’utente non verrà informato delle nuove versioni disponibili.

Se **[!UICONTROL No longer ask this question]**  è stato selezionato, è possibile reimpostare la richiesta. Solo gli amministratori di sistema che hanno familiarità con la modifica del Registro di sistema di Windows possono apportare le seguenti modifiche:

1. Apri l’Editor del Registro di sistema utilizzando **regedit** comando da **[!UICONTROL Start > Run]** menu.

1. Cerca il nodo ed espandilo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimina **confAdvisedUpgrade** e chiudere l&#39;Editor del Registro di sistema.

>[!NOTE]
>
>Se applichi una console aggiornata a un’implementazione esistente, gli utenti riceveranno automaticamente una richiesta di aggiornamento della console client. Se implementi Campaign per la prima volta, gli utenti dovranno scaricare la console. Per informazioni dettagliate su entrambe le opzioni, consulta di seguito

### Aggiorna la console per l&#39;implementazione esistente{#update-the-client-console}

Quando la console sarà disponibile nella cartella del server Campaign, agli utenti verrà richiesto di scaricare l’ultima versione della console client in una finestra pop-up.

**Per completare l’aggiornamento, gli utenti dovranno disporre dell’accesso di amministratore. Se gli utenti non dispongono di diritti di amministratore, un amministratore di sistema dovrà distribuire su tutte le console client**


### Scarica la console per la nuova implementazione{#download-the-client-console}

Ora gli utenti devono scaricare e installare la console seguendo questi passaggi:

1. Apri un browser web e scarica la console dal seguente indirizzo:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. Nella finestra di identificazione, inserire il login e la password.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessario, utilizza le credenziali dell’account interno definite durante la creazione dell’istanza.

1. Fai clic su **[!UICONTROL Download]** nella pagina di installazione.
1. Scaricare e salvare il file di installazione del client.
1. Eseguire il file scaricato su un computer in Windows: l&#39;installazione viene avviata. Il percorso di installazione predefinito della console client è **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, dove &quot;X&quot; è &quot;6&quot; o &quot;7&quot;, in base alla versione di Adobe Campaign in uso.

### Crea la connessione - solo per i nuovi utenti{#create-the-connection}

Dopo aver installato la console client, attenersi alla procedura descritta di seguito per creare la connessione al server applicazioni:

1. Avvia la console da Windows **[!UICONTROL Start]** nel menu **Adobe Campaign** gruppo di programmi.

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Clic **[!UICONTROL Add > Connection]** e immetti l’etichetta e l’URL del server applicazioni Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specifica una connessione al server applicazioni Adobe Campaign tramite un URL. Utilizza un DNS o un alias del computer oppure il tuo indirizzo IP.

   Ad esempio, puoi utilizzare `https://<machine>.<domain>.com` digita URL.

1. Se Adobe IMS è configurato per la tua organizzazione, seleziona l’opzione **[!UICONTROL Connect with an Adobe ID]**

1. Clic **[!UICONTROL Ok]** per salvare le impostazioni.

Puoi aggiungere tutte le connessioni necessarie per connettersi, ad esempio, agli ambienti di test, stage e produzione.

>[!NOTE]
>
>Il **[!UICONTROL Add]** consente di creare **[!UICONTROL folders]** per organizzare tutte le connessioni. È sufficiente trascinare ogni connessione in una cartella.

### Accedere ad Adobe Campaign

Per accedere a un&#39;istanza esistente, effettuare le seguenti operazioni:

1. Avvia la console da Windows **[!UICONTROL Start]** nel menu **Adobe Campaign** gruppo di programmi.

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

1. Seleziona l’istanza di Campaign a cui devi accedere.

1. Clic **[!UICONTROL Ok]**

1. Immetti le credenziali di accesso dell&#39;utente e fai clic su **[!UICONTROL Log in]**

>[!NOTE]
>
>Per le versioni della build Campaign Classic 7.3, la console client di Adobe Campaign può richiedere le credenziali proxy due volte durante l’autenticazione proxy. Ciò è dovuto al fatto che Microsoft Edge Webview2 non salva le credenziali proxy nell&#39;archivio cache/password, a differenza di Internet Explorer.

**Argomenti correlati**

* [Creazione di un’istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

## Video tutorial

Questo video mostra come installare e configurare il client Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Sono disponibili altri video dimostrativi sui Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
