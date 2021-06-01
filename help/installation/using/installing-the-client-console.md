---
product: campaign
title: Installazione della console client
description: Scopri come installare la console client
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '973'
ht-degree: 3%

---

# Installa e aggiorna la console del client Campaign{#installing-the-client-console}

Campaign Client Console è un client avanzato che ti consente di connettersi ai server delle applicazioni Campaign.

Prima di avviare l’installazione della console client, è necessario:

* Verifica la compatibilità di sistema e strumenti con Adobe Campaign nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Ottieni l’URL del server Campaign
* Ottieni le credenziali utente

Il processo di installazione o aggiornamento della console client varia a seconda dell’implementazione di Adobe Campaign Classic.
Controlla i dettagli riportati di seguito per capire cosa è necessario per la tua implementazione.

![](assets/do-not-localize/how-to-video.png) Scopri come installare e configurare il client Adobe Campaign nel  [video](#video)

>[!CAUTION]
>
>La console del client Campaign e il server dell’applicazione Campaign devono essere eseguiti **sulla stessa versione del prodotto**. L&#39;Adobe consiglia inoltre vivamente di utilizzare la **stessa build del prodotto**. Scopri come controllare le versioni Campaign Client e Server in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Adobe Implementazioni in hosting {#hosted-customers}

Aggiungi un cliente ospitato, hai due opzioni per installare o aggiornare le console client:

1. Adobe può distribuire direttamente. Una volta aggiornata la console, agli utenti verrà richiesto di scaricare l’ultima versione della console client in una finestra a comparsa.

1. È possibile scaricare nelle console client da [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)

   **Per completare l’aggiornamento, gli utenti dovranno disporre dell’accesso amministratore. Se gli utenti non dispongono di diritti di amministratore, un amministratore di sistema dovrà distribuire su tutte le console client**

## Implementazioni ibride e on-premise {#hybrid-onprem-customers}

Affinché gli utenti di Adobe Campaign possano accedere all’istanza creata e configurata, devono utilizzare la console client.

### Rendere la console disponibile agli utenti {#make-console-available}

Quando il computer utilizzato per avviare un server applicazioni Adobe Campaign (nlserver web) riceve connessioni utente dalla console client, puoi configurarlo per rendere disponibile il programma di installazione per il client avanzato Adobe Campaign tramite un&#39;interfaccia HTML. Ogni volta che è disponibile una nuova versione della console client, gli utenti vengono invitati a scaricarla all’avvio della console client.

A questo scopo, devi:

1. Selezionare il pacchetto contenente il programma di installazione della console.

   Questo file si chiama setup-client-7.X.XXXX.exe per v7 o setup-client-6.X.XXXX.exe per v6.1, dove X è la sottoversione di Adobe Campaign e XXXX è la build   numero.

1. Copia e incolla questo pacchetto nella cartella di installazione di Adobe Campaign (sul server di marketing per le installazioni ibride), in /datakit/nl/eng/jsp.

1. Avvia il server Adobe Campaign.


### Non chiedere più questa opzione

Adobe consiglia di lasciare l’opzione **[!UICONTROL No longer ask this question]** deselezionata per fare in modo che tutti gli utenti vengano avvisati quando è disponibile una nuova versione della console.  Se questa opzione è selezionata, l’utente non verrà informato delle nuove versioni disponibili.

Se è stato selezionato **[!UICONTROL No longer ask this question]**, è possibile reimpostare questo prompt. Solo gli amministratori di sistema che possono modificare il Registro di sistema di Windows devono apportare le seguenti modifiche:

1. Apri l&#39;Editor del Registro di sistema utilizzando il comando **regedit** dal menu **[!UICONTROL Start > Run]**.

1. Cercare il nodo ed espanderlo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimina la voce **confAdvisorUpgrade** e chiudi l&#39;Editor del Registro di sistema.

>[!NOTE]
>
>Se applichi una console aggiornata a un’implementazione esistente, gli utenti riceveranno automaticamente un messaggio per aggiornare la console client. Se implementi Campaign per la prima volta, gli utenti dovranno scaricare la console. Per maggiori dettagli su entrambe le opzioni, vedere qui sotto

### Aggiorna la console per l&#39;implementazione esistente{#update-the-client-console}

Quando la console è disponibile nella cartella del server Campaign, agli utenti verrà richiesto di scaricare l’ultima versione della console client in una finestra a comparsa.

**Per completare l’aggiornamento, gli utenti avranno bisogno dell’accesso dell’amministratore. Se gli utenti non dispongono di diritti di amministratore, un amministratore di sistema dovrà distribuire su tutte le console client**


### Scarica la console per la nuova implementazione{#download-the-client-console}

Gli utenti ora devono scaricare e installare la console seguendo i passaggi seguenti:

1. Apri un browser web e scarica la console dal seguente indirizzo:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Nella finestra di identificazione, immetti il tuo login e la tua password.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessario, utilizza le credenziali dell’account interno definito durante la creazione dell’istanza.

1. Fai clic sul collegamento **[!UICONTROL Download]** nella pagina di installazione.
1. Scarica e salva il file di installazione client.
1. Esegui il file scaricato su un computer in Windows: L&#39;installazione viene avviata. Il percorso di installazione predefinito della console client è **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, dove &#39;X&#39; è &#39;6&#39; o &#39;7&#39;, in base alla tua versione Adobe Campaign.

### Crea la connessione - solo per gli utenti della prima volta{#create-the-connection}

Una volta installata la console del client, segui i passaggi seguenti per creare la connessione al server dell&#39;applicazione:

1. Avvia la console dal menu Windows **[!UICONTROL Start]**, nel gruppo di programmi **Adobe Campaign**.

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Fai clic su **[!UICONTROL Add > Connection]** e immetti l’etichetta e l’URL del server dell’applicazione Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specifica una connessione al server dell’applicazione Adobe Campaign tramite un URL. Utilizzare un DNS o un alias del computer o l&#39;indirizzo IP.

   Ad esempio, puoi utilizzare l&#39;URL del tipo [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Se Adobe IMS è configurato per la tua organizzazione, seleziona l’opzione **[!UICONTROL Connect with an Adobe ID]**

1. Fai clic su **[!UICONTROL Ok]** per salvare le impostazioni.

Puoi aggiungere tutte le connessioni necessarie per connettersi, ad esempio, agli ambienti di test, stage e produzione.

>[!NOTE]
>
>Il pulsante **[!UICONTROL Add]** consente di creare **[!UICONTROL folders]** per organizzare tutte le connessioni. Trascina e rilascia ciascuna connessione in una cartella.

### Accedere ad Adobe Campaign

Per accedere a un&#39;istanza esistente, segui i passaggi seguenti:

1. Avvia la console dal menu Windows **[!UICONTROL Start]**, nel gruppo di programmi **Adobe Campaign**.

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

1. Seleziona l’istanza Campaign a cui devi accedere.

1. Fai clic su **[!UICONTROL Ok]**

1. Immetti le credenziali di accesso dell&#39;utente e fai clic su **[!UICONTROL Log in]**


**Argomenti correlati**

* [Creazione di un’istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)

## Video tutorial

Questo video mostra come installare e configurare il client Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
