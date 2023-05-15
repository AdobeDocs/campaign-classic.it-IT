---
product: campaign
title: Installazione del server
description: Installazione del server
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 3%

---

# Installazione del server{#installing-the-server}



## Esecuzione del programma di installazione {#executing-the-installation-program}

Per una piattaforma Windows a 32 bit, installare Adobe Campaign a 32 bit. Per una piattaforma Windows a 64 bit, installare Adobe Campaign a 64 bit.

I passaggi di installazione per il server Adobe Campaign sono i seguenti:

1. Esegui il file **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. Selezionare il tipo di installazione.

   ![](assets/s_ncs_install_installer_01a.png)

   Sono disponibili diversi tipi di installazione:

   * **[!UICONTROL Installation of an application server]** : Installa il server applicazioni Adobe Campaign e la console client.
   * **[!UICONTROL Minimal installation (Network)]** : Installazione del computer client dalla rete. Se necessario, sul computer verrà installato solo un numero limitato di DLL e tutti gli altri componenti verranno utilizzati da un&#39;unità di rete.
   * **[!UICONTROL Installation of a client]** : Installazione dei componenti richiesti per il client Adobe Campaign.
   * **[!UICONTROL Custom installation]** : L&#39;utente sceglie gli elementi da installare.

   Seleziona **Installazione di un application server** e segui i diversi passaggi come mostrato di seguito:

   ![](assets/s_ncs_install_installer_02.png)

1. Seleziona la directory di installazione:

   ![](assets/s_ncs_install_installer_03.png)

1. Fai clic su **[!UICONTROL Finish]** per avviare l&#39;installazione:

   ![](assets/s_ncs_install_installer_04.png)

   La barra di avanzamento mostra la distanza dell’installazione:

   ![](assets/s_ncs_install_installer_05.png)

   Al termine dell’installazione, viene visualizzato un messaggio per informarti:

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >Una volta completata l&#39;installazione del server, è necessario riavviare il server per evitare possibili problemi di rete.

   Al termine dell’installazione, avvia Adobe Campaign per creare i file di configurazione. Fai riferimento a [Primo avvio del server](#first-start-up-of-the-server).

## Riepilogo del test di installazione {#summary-installation-testing}

Puoi verificare l’installazione iniziale utilizzando il seguente comando:

```
nlserver pdump
```

Se Adobe Campaign non viene avviato, la risposta è:

```
No task
```

## Primo avvio del server {#first-start-up-of-the-server}

Una volta completato il test di installazione, apri un prompt dei comandi tramite il **[!UICONTROL Start > Programs > Adobe Campaign]** e immetti il comando seguente:

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

I file nella directory di installazione vengono utilizzati per configurare i moduli server Adobe Campaign.

Vengono visualizzate le seguenti informazioni:

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

Press **Ctrl+C** per interrompere il processo, immettere il comando seguente:

```
nlserver start web
```

Vengono visualizzate le seguenti informazioni:

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

Per interromperlo, immetti:

```
nlserver stop web
```

Vengono visualizzate le seguenti informazioni:

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## Password per l’identificatore interno {#password-for-the-internal-identifier}

Il server Adobe Campaign definisce un accesso tecnico denominato **interno** che ha tutti i diritti su tutte le istanze. Subito dopo l&#39;installazione, l&#39;accesso non dispone di una password. È obbligatorio definirne uno.

Per ulteriori informazioni, consulta [questa sezione](../../installation/using/configuring-campaign-server.md#internal-identifier).

## Avvio dei servizi Adobe Campaign {#starting-adobe-campaign-services}

Per avviare i servizi Adobe Campaign, puoi utilizzare il gestore dei servizi o immettere quanto segue nella riga di comando (con i diritti appropriati):

```
net start nlserver6
```

Se devi interrompere i processi Adobe Campaign in un secondo momento, utilizza il comando :

```
net stop nlserver6
```

## Installazione di LibreOffice {#installing-libreoffice}

Scarica LibreOffice e segui i passaggi regolari di installazione.

Aggiungi la seguente variabile di ambiente:

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
