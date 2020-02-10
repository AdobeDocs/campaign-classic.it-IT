---
title: Installazione del server
seo-title: Installazione del server
description: Installazione del server
seo-description: null
page-status-flag: never-activated
uuid: 02534211-c267-490d-b9c1-78f56f1284e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1510fd9-995b-46c6-8d57-e1fe3999235e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# Installazione del server{#installing-the-server}

## Esecuzione del programma di installazione {#executing-the-installation-program}

Per una piattaforma Windows a 32 bit, installa Adobe Campaign a 32 bit. Per una piattaforma Windows a 64 bit, installa Adobe Campaign a 64 bit.

I passaggi di installazione per il server Adobe Campaign sono i seguenti:

1. Eseguire il file **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Selezionare il tipo di installazione.

   ![](assets/s_ncs_install_installer_01a.png)

   Sono disponibili diversi tipi di installazione:

   * **[!UICONTROL Installation of an application server]** : Installa il server applicazioni Adobe Campaign e la console client.
   * **[!UICONTROL Minimal installation (Network)]** : Installazione del computer client dalla rete. Nel computer verrà installato solo un numero limitato di DLL, se necessario, e tutti gli altri componenti verranno utilizzati da un&#39;unità di rete.
   * **[!UICONTROL Installation of a client]** : Installazione dei componenti richiesti per il client Adobe Campaign.
   * **[!UICONTROL Custom installation]** : L&#39;utente sceglie gli elementi da installare.
   Selezionate **Installazione di un server** applicazione e seguite i diversi passaggi come mostrato di seguito:

   ![](assets/s_ncs_install_installer_02.png)

1. Selezionate la directory di installazione:

   ![](assets/s_ncs_install_installer_03.png)

1. Fate clic **[!UICONTROL Finish]** per avviare l&#39;installazione:

   ![](assets/s_ncs_install_installer_04.png)

   La barra di avanzamento mostra la distanza dell’installazione:

   ![](assets/s_ncs_install_installer_05.png)

   Una volta completata l&#39;installazione, compare un messaggio che vi informa:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Una volta completata l&#39;installazione del server, è necessario riavviare il server per evitare possibili problemi di rete.

   Al termine dell&#39;installazione, avvia Adobe Campaign per creare i file di configurazione. Fare riferimento al [primo avvio del server](#first-start-up-of-the-server).

## Test di installazione di riepilogo {#summary-installation-testing}

Potete verificare l&#39;installazione iniziale utilizzando il seguente comando:

```
nlserver pdump
```

Se Adobe Campaign non viene avviato, la risposta è:

```
No task
```

## Primo avvio del server {#first-start-up-of-the-server}

Al termine del test di installazione, aprite un prompt dei comandi dal **[!UICONTROL Start > Programs > Adobe Campaign]** menu e immettete il comando seguente:

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

I file presenti nella directory di installazione vengono utilizzati per configurare i moduli server di Adobe Campaign.

Vengono visualizzate le informazioni seguenti:

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Premere **Ctrl+C** per interrompere il processo, quindi digitare il comando seguente:

```
nlserver start web
```

Vengono visualizzate le informazioni seguenti:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Per interromperlo, immettere:

```
nlserver stop web
```

Vengono visualizzate le informazioni seguenti:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Password per l’identificatore interno {#password-for-the-internal-identifier}

Il server Adobe Campaign definisce un login tecnico denominato **interno** che dispone di tutti i diritti in tutte le istanze. Subito dopo l&#39;installazione, il login non dispone di una password. È obbligatorio definirne una.

Vedere sezione Identificatore [](../../installation/using/campaign-server-configuration.md#internal-identifier)interno.

## Avvio dei servizi Adobe Campaign {#starting-adobe-campaign-services}

Per avviare i servizi di Adobe Campaign, puoi utilizzare il gestore dei servizi o immettere quanto segue nella riga di comando (con i diritti appropriati):

```
net start nlserver6
```

Se devi interrompere i processi di Adobe Campaign in un secondo momento, usa il comando:

```
net stop nlserver6
```

## Installazione di LibreOffice {#installing-libreoffice}

Scaricate LibreOffice, ad esempio da [https://www.libreoffice.org/download/libreoffice-fresh/](https://www.libreoffice.org/download/libreoffice-fresh/) e seguite i passaggi di installazione regolari.

Aggiungete la seguente variabile di ambiente:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 5\"
```

