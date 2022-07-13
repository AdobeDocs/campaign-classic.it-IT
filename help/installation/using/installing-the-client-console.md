---
product: campaign
title: Installazione della console client
description: Scopri come installare la console client
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: 7cc78214-92b8-4b1f-a307-96ec6af818d1
source-git-commit: 0f63636e9cc22ac97e634a4f11dc585cb39b05c0
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 3%

---

# Installare e aggiornare la console del client Campaign{#installing-the-client-console}

![](../../assets/v7-only.svg)

Campaign Client Console è un client avanzato che ti consente di connettersi ai server delle applicazioni Campaign.

Prima di avviare l’installazione della console client, è necessario:

* Verifica la compatibilità di sistema e strumenti con Adobe Campaign nella [Matrice di compatibilità](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)
* Ottieni l’URL del server Campaign
* Ottieni le credenziali utente

Il processo di installazione o aggiornamento della console client varia a seconda dell’implementazione di Adobe Campaign Classic.
Controlla i dettagli riportati di seguito per capire cosa è necessario per la tua implementazione.

![](assets/do-not-localize/how-to-video.png) Scopri come installare e configurare il client Adobe Campaign in [video](#video)

>[!CAUTION]
>
>La console del client Campaign e il server dell’applicazione Campaign devono essere eseguiti **sulla stessa versione del prodotto**. L&#39;Adobe consiglia inoltre vivamente di utilizzare il **stessa build di prodotto**. Scopri come controllare le versioni del client e del server Campaign in [questa sezione](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

## Implementazioni in hosting Adobe {#hosted-customers}

In qualità di cliente ospitato, hai due opzioni per installare o aggiornare le console client:

1. Adobe può distribuire direttamente. Una volta aggiornata la console, agli utenti verrà richiesto di scaricare l’ultima versione della console client in una finestra a comparsa.

1. Puoi scaricare i contenuti nelle console client da [Distribuzione di software](https://experience.adobe.com/#/downloads/content/software-distribution/it/campaign.html)

   **Per completare l’aggiornamento, gli utenti dovranno disporre dell’accesso amministratore. Se gli utenti non dispongono di diritti di amministratore, un amministratore di sistema dovrà distribuire tutte le console client**

## Implementazioni ibride e on-premise {#hybrid-onprem-customers}

Affinché gli utenti di Adobe Campaign possano accedere all’istanza creata e configurata, devono utilizzare la console client.

### Rendere la console disponibile agli utenti {#make-console-available}

Quando il computer utilizzato per avviare un server applicazioni Adobe Campaign (nlserver web) riceve connessioni utente dalla console client, è possibile configurarlo per rendere disponibile il programma di installazione per il client avanzato Adobe Campaign tramite un’interfaccia HTML. Ogni volta che è disponibile una nuova versione della console client, gli utenti vengono invitati a scaricarla all’avvio della console client.

A questo scopo, devi:

1. Selezionare il pacchetto contenente il programma di installazione della console.

   Questo file si chiama setup-client-7.X.XXXX.exe per v7 o setup-client-6.X.XXXX.exe per v6.1, dove X è la sottoversione di Adobe Campaign e XXXX è il numero di build.

1. Copia e incolla questo pacchetto nella cartella di installazione di Adobe Campaign (sul server di marketing per le installazioni ibride), in /datakit/nl/eng/jsp.

1. Avvia il server Adobe Campaign.


### Non chiedere più questa opzione

L’Adobe consiglia di lasciare l’opzione **[!UICONTROL No longer ask this question]** deselezionata per informare tutti gli utenti della disponibilità di una nuova versione della console.  Se questa opzione è selezionata, l’utente non verrà informato delle nuove versioni disponibili.

Se **[!UICONTROL No longer ask this question]**  è stato selezionato. È possibile reimpostare il prompt. Solo gli amministratori di sistema che possono modificare il Registro di sistema di Windows devono apportare le seguenti modifiche:

1. Apri l&#39;Editor del Registro di sistema utilizzando **regedit** dal comando **[!UICONTROL Start > Run]** menu.

1. Cercare il nodo ed espanderlo.

   ```
   \HKEY_CURRENT_USER\Software\Neolane\NL_6\nlclient
   ```

1. Elimina **confAdvisorUpgrade** entrare e chiudere l&#39;Editor del Registro di sistema.

>[!NOTE]
>
>Se applichi una console aggiornata a un’implementazione esistente, gli utenti riceveranno automaticamente un messaggio per aggiornare la console client. Se implementi Campaign per la prima volta, gli utenti dovranno scaricare la console. Per maggiori dettagli su entrambe le opzioni, vedere qui sotto

### Aggiorna la console per l’implementazione esistente{#update-the-client-console}

Quando la console è disponibile nella cartella del server Campaign, agli utenti verrà richiesto di scaricare l’ultima versione della console client in una finestra a comparsa.

**Per completare l’aggiornamento, gli utenti avranno bisogno dell’accesso dell’amministratore. Se gli utenti non dispongono di diritti di amministratore, un amministratore di sistema dovrà distribuire tutte le console client**


### Scarica la console per la nuova implementazione{#download-the-client-console}

Gli utenti ora devono scaricare e installare la console seguendo i passaggi seguenti:

1. Apri un browser web e scarica la console dal seguente indirizzo:

   `https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`.

1. Nella finestra di identificazione, immetti il tuo login e la tua password.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessario, utilizza le credenziali dell’account interno definito durante la creazione dell’istanza.

1. Fai clic sul pulsante **[!UICONTROL Download]** nella pagina di installazione.
1. Scarica e salva il file di installazione client.
1. Esegui il file scaricato su un computer in Windows: L&#39;installazione viene avviata. Il percorso di installazione predefinito della console client è **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, dove &quot;X&quot; è &quot;6&quot; o &quot;7&quot;, in base alla tua versione Adobe Campaign.

### Creazione della connessione - solo per i primi utenti{#create-the-connection}

Una volta installata la console del client, segui i passaggi seguenti per creare la connessione al server dell&#39;applicazione:

1. Avvia la console da Windows **[!UICONTROL Start]** nel menu **Adobe Campaign** gruppo di programmi.

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Fai clic su **[!UICONTROL Add > Connection]** e immetti l’etichetta e l’URL dell’application server di Adobe Campaign.

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specifica una connessione al server dell’applicazione Adobe Campaign tramite un URL. Utilizzare un DNS o un alias del computer o l&#39;indirizzo IP.

   Ad esempio, puoi utilizzare il [`https://<machine>.<domain>.com`](https://myserver.adobe.com) digitare URL.

1. Se Adobe IMS è configurato per la tua organizzazione, seleziona l’opzione . **[!UICONTROL Connect with an Adobe ID]**

1. Fai clic su **[!UICONTROL Ok]** per salvare le impostazioni.

Puoi aggiungere tutte le connessioni necessarie per connettersi, ad esempio, agli ambienti di test, stage e produzione.

>[!NOTE]
>
>La **[!UICONTROL Add]** pulsante consente di creare **[!UICONTROL folders]** per organizzare tutte le connessioni. Trascina e rilascia ciascuna connessione in una cartella.

### Accedere ad Adobe Campaign

Per accedere a un&#39;istanza esistente, segui i passaggi seguenti:

1. Avvia la console da Windows **[!UICONTROL Start]** nel menu **Adobe Campaign** gruppo di programmi.

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
