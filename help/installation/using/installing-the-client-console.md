---
title: Installazione della console client
description: Scoprite come installare la console client
page-status-flag: never-activated
uuid: 1279c0d8-bf27-4a58-ae94-796d6147231a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1069b23-e08d-43c5-bbfb-3158ac40dc7e
translation-type: tm+mt
source-git-commit: bdc09e1b6e037e1b21573b8624a947e30f8ad1fc
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 5%

---


# Installazione della console client di Campaign{#installing-the-client-console}

La console Client campagna è un client avanzato che consente di connettersi ai server delle applicazioni Campaign.

Prima di iniziare, è necessario verificare la matrice [di](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)compatibilità delle campagne, ottenere l&#39;URL del server Campaign e le credenziali utente.

>[!CAUTION]
>
>La console Client campagna e il server applicazione Campaign devono essere eseguiti sulla stessa versione del prodotto.  Adobe consiglia inoltre di utilizzare la stessa build di prodotto.

## Scaricare la console{#download-the-client-console}

Per scaricare e installare la console client  Adobe Campaign, effettuate le seguenti operazioni:

1. Aprite un browser Web e scaricate la console dal seguente indirizzo:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://machine/nl/jsp/logon.jsp).

1. Nella finestra di identificazione, immettete il login e la password.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessario, utilizzate le credenziali dell&#39;account interno definito durante la creazione dell&#39;istanza.

1. Fate clic sul **[!UICONTROL Download]** collegamento nella pagina di installazione.
1. Scaricate e salvate il file di installazione client.
1. Eseguire il file scaricato su un computer in Windows: L&#39;installazione viene avviata. Il percorso di installazione predefinito della console client è **$PROGRAMFILES$/ Adobe/Adobe Campaign Classic vX Client**, dove &#39;X&#39; è &#39;6&#39; o &#39;7&#39;, in base alla versione  Adobe Campaign.

>[!NOTE]
>
>In Windows, è possibile avviare il file **nlclient.exe** direttamente dalla `[INSTALL]/bin` directory di un server Windows, dove `[INSTALL]` è il percorso di accesso per la cartella di installazione  Adobe Campaign.

## Creazione della connessione{#create-the-connection}

Una volta installata la console client, effettuate le operazioni seguenti per creare la connessione al server dell’applicazione:

1. Avviate la console dal **[!UICONTROL Start]** menu di Windows, nel gruppo di programmi **Adobe Campaign** .

1. Fare clic sul collegamento nell&#39;angolo superiore destro dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Fate clic su **[!UICONTROL Add > Connection]** e immettete l’etichetta e l’URL del server applicazione Adobe Campaign .

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specificate una connessione al server  applicazione Adobe Campaign tramite un URL. Utilizzate un DNS o un alias del computer o il vostro indirizzo IP.

   Ad esempio, potete utilizzare il [`https://<machine>.<domain>.com`](https://machine) tipo URL.

1. Se  Adobe IMS è configurato per la vostra azienda, selezionate l&#39;opzione **[!UICONTROL Connect with an Adobe ID]**

1. Click **[!UICONTROL Ok]** to save your settings.

Potete aggiungere tutte le connessioni necessarie per collegarvi ai vostri ambienti di prova, di fase e di produzione, ad esempio.

>[!NOTE]
>
>Il **[!UICONTROL Add]** pulsante consente di creare **[!UICONTROL folders]** per organizzare tutte le connessioni. È sufficiente trascinare ogni connessione in una cartella.


## Accedere a  Adobe Campaign

Per accedere a un&#39;istanza esistente, procedere come segue:

1. Avviate la console dal **[!UICONTROL Start]** menu di Windows, nel gruppo di programmi **Adobe Campaign** .

1. Fare clic sul collegamento nell&#39;angolo superiore destro dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

1. Seleziona l&#39;istanza Campaign a cui devi accedere.

1. Fai clic su **[!UICONTROL Ok]**

1. Immettete le credenziali di accesso utente e fate clic su **[!UICONTROL Log in]**

**Argomenti correlati**

* [Creazione di un’istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html)
* [Installazione e configurazione del client](https://docs.adobe.com/content/help/en/campaign-classic-learn/tutorials/getting-started/install-and-setup-the-adobe-campaign-client.html) Adobe Campaign  (video)
