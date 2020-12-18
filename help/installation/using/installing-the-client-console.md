---
solution: Campaign Classic
product: campaign
title: Installazione della console client
description: Scoprite come installare la console client
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
translation-type: tm+mt
source-git-commit: cea4a26935312b1cb119a3fa671af7bf00788fe9
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 6%

---


# Installazione della console del client Campaign{#installing-the-client-console}

La console Client campagna è un client avanzato che consente di connettersi ai server delle applicazioni Campaign.

Prima di iniziare, è necessario verificare la [Matrice di compatibilità](https://helpx.adobe.com/it/campaign/kb/compatibility-matrix.html) della campagna, ottenere l&#39;URL del server della campagna e le credenziali utente.

>[!CAUTION]
>
>La console Client campagna e il server applicazione Campaign devono essere eseguiti sulla stessa versione del prodotto.  Adobe consiglia inoltre di utilizzare la stessa build di prodotto.

![](assets/do-not-localize/how-to-video.png) Scoprite come installare e configurare il client Adobe Campaign  in  [video](#video)

## Scarica la console{#download-the-client-console}

Per scaricare e installare la console client  Adobe Campaign, effettuate le seguenti operazioni:

1. Aprite un browser Web e scaricate la console dal seguente indirizzo:

   [`https://<your adobe campaign server>:<port number>/nl/jsp/logon.jsp`](https://myserver.adobe.com/nl/jsp/logon.jsp).

1. Nella finestra di identificazione, immettete il login e la password.

   ![](assets/s_ncs_install_setup_download01.png)

   Se necessario, utilizzate le credenziali dell&#39;account interno definito durante la creazione dell&#39;istanza.

1. Fate clic sul collegamento **[!UICONTROL Download]** nella pagina di installazione.
1. Scaricate e salvate il file di installazione client.
1. Eseguire il file scaricato su un computer in Windows: L&#39;installazione viene avviata. Il percorso di installazione predefinito della console client è **$PROGRAMFILES$/ Adobe/Adobe Campaign Classic vX Client**, dove &#39;X&#39; è &#39;6&#39; o &#39;7&#39;, in base alla versione  Adobe Campaign.

>[!NOTE]
>
>In Windows, è possibile avviare il file **nlclient.exe** direttamente dalla directory `[INSTALL]/bin` in un server Windows, dove `[INSTALL]` è il percorso di accesso per la cartella di installazione  Adobe Campaign.

## Creare la connessione{#create-the-connection}

Una volta installata la console client, effettuate le operazioni seguenti per creare la connessione al server dell’applicazione:

1. Avviare la console dal menu Windows **[!UICONTROL Start]**, nel gruppo di programmi **Adobe Campaign**.

1. Fare clic sul collegamento nell&#39;angolo superiore destro dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

   ![](assets/s_ncs_install_define_connection_01.png)

1. Fare clic su **[!UICONTROL Add > Connection]** e immettere l&#39;etichetta e l&#39;URL del server dell&#39;applicazione Adobe Campaign .

   ![](assets/s_ncs_install_define_connection_02.png)

1. Specificate una connessione al server  applicazione Adobe Campaign tramite un URL. Utilizzate un DNS o un alias del computer o il vostro indirizzo IP.

   Ad esempio, potete utilizzare l&#39;URL di tipo [`https://<machine>.<domain>.com`](https://myserver.adobe.com).

1. Se  Adobe IMS è configurato per l&#39;azienda, selezionare l&#39;opzione **[!UICONTROL Connect with an Adobe ID]**

1. Fare clic su **[!UICONTROL Ok]** per salvare le impostazioni.

Potete aggiungere tutte le connessioni necessarie per collegarvi ai vostri ambienti di prova, di fase e di produzione, ad esempio.

>[!NOTE]
>
>Il pulsante **[!UICONTROL Add]** consente di creare **[!UICONTROL folders]** per organizzare tutte le connessioni. È sufficiente trascinare ogni connessione in una cartella.

## Accedere a  Adobe Campaign

Per accedere a un&#39;istanza esistente, procedere come segue:

1. Avviare la console dal menu Windows **[!UICONTROL Start]**, nel gruppo di programmi **Adobe Campaign**.

1. Fare clic sul collegamento nell&#39;angolo superiore destro dei campi delle credenziali per accedere alla finestra di configurazione della connessione.

1. Seleziona l&#39;istanza Campaign a cui devi accedere.

1. Fai clic su **[!UICONTROL Ok]**

1. Immettete le credenziali di accesso utente e fate clic su **[!UICONTROL Log in]**

**Argomenti correlati**

* [Creazione di un’istanza e accesso](../../installation/using/creating-an-instance-and-logging-on.md).
* [Matrice di compatibilità](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

## Video di esercitazione

In questo video viene illustrato come installare e configurare il client Adobe Campaign .

>[!VIDEO](https://video.tv.adobe.com/v/35124?quality=12)

Ulteriori video dimostrativi sui Campaign Classic sono disponibili [qui](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=it).
