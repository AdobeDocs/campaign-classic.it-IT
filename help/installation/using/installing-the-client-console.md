---
solution: Campaign Classic
product: campaign
title: Installazione della console client
description: Scopri come installare la console client
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: 1b02c3870ddc01705f01ea992e734cf0810e003a
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 6%

---


# Installazione della console del client Campaign{#installing-the-client-console}

La console Client di Campaign è un client avanzato che consente di connettersi ai server delle applicazioni Campaign.

Prima di iniziare, devi controllare l’ [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html) di Campaign, ottenere l’URL del server Campaign e le credenziali utente.

>[!CAUTION]
>
>La console del client Campaign e il server dell’applicazione Campaign devono essere eseguiti sulla stessa versione del prodotto. Adobe consiglia inoltre di utilizzare la stessa build del prodotto.

![](assets/do-not-localize/how-to-video.png) Scopri come installare e configurare il client Adobe Campaign nel  [video](#video)

## Scarica la console{#download-the-client-console}

Per scaricare e installare la console client di Adobe Campaign, segui i passaggi seguenti:

1. Apri un browser web e scarica la console dal seguente indirizzo:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Nella finestra di identificazione, immetti il tuo login e la tua password.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessario, utilizza le credenziali dell’account interno definito durante la creazione dell’istanza.

1. Fai clic sul collegamento **[!UICONTROL Download]** nella pagina di installazione.
1. Scarica e salva il file di installazione client.
1. Esegui il file scaricato su un computer in Windows: L&#39;installazione viene avviata. Il percorso di installazione predefinito della console client è **$PROGRAMFILES$/Adobe/Adobe Campaign Classic vX Client**, dove &quot;X&quot; è &quot;6&quot; o &quot;7&quot;, in base alla versione di Adobe Campaign.

>[!NOTE]
>
>Puoi proporre l’aggiornamento alla versione più recente a tutti gli utenti della console del client Campaign copiando il file eseguibile della console in una cartella specifica del server Campaign Marketing. [Ulteriori informazioni](../../installation/using/client-console-availability-for-windows.md).


## Crea la connessione{#create-the-connection}

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

## Accedi ad Adobe Campaign

Per accedere a un&#39;istanza esistente, segui i passaggi seguenti:

1. Avvia la console dal menu Windows **[!UICONTROL Start]**, nel gruppo di programmi **Adobe Campaign**.

1. Fai clic sul collegamento nell’angolo in alto a destra dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

1. Seleziona l’istanza Campaign a cui devi accedere.

1. Fai clic su **[!UICONTROL Ok]**

1. Immetti le credenziali di accesso dell&#39;utente e fai clic su **[!UICONTROL Log in]**

**Argomenti correlati**

* [Creazione di un’istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matrice di compatibilità](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## Video tutorial

Questo video mostra come installare e configurare il client Adobe Campaign.

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Sono disponibili ulteriori video dimostrativi su Campaign Classic [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
