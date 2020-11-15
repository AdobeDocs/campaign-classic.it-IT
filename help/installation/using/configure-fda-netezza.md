---
title: Configurare l'accesso a Netezza
description: Scopri come configurare l'accesso a Netezza in FDA
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 9bbde65aea6735e30e95e75c2b6ae5445d4a2bdd
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---


# Configurare l&#39;accesso a Netezza {#configure-access-to-netezza}

Utilizzate l&#39;opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguite i passaggi riportati di seguito per configurare l&#39;accesso a Netezza.

1. Installare e configurare driver [Netezza](#netezza-config)
1. Configurare l&#39;account [](#netezza-external) esterno Netezza in Campaign

## Configurazione Netezza {#netezza-config}

La connessione a un database esterno Netezza in FDA richiede configurazioni aggiuntive nel server Adobe Campaign :

1. Installare i driver ODBC per Netezza, in base al sistema operativo utilizzato:

   * **nz-linuxclient-v7.2.0.0.tar.gz** per Linux. Selezionate la cartella che corrisponde al sistema operativo in uso (linux o linux64) e avviate il comando di rimozione del pacchetto. È possibile lasciare l&#39;installazione da eseguire nella directory archivio suggerita per impostazione predefinita: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** per Windows. Decomprimete il file e avviate lo script eseguibile corrispondente al sistema operativo in uso: nzodbcsetup.exe o nzodbcsetup64.exe. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: **/etc/odbc.ini** per i parametri generali e **/etc/odbcinst.ini** per la dichiarazione dei driver.

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot; corrisponde alla posizione del file odbcinst.ini.

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. Specificate le variabili di ambiente del server Adobe Campaign :

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib e /usr/local/nz/lib64. &quot;/usr/local/nz&quot; corrisponde al repository di installazione offerto per impostazione predefinita durante l&#39;installazione dei driver. Qui è necessario specificare il repository selezionato per l&#39;installazione.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: posizione del file odbc.ini. Netezza richiede anche questa seconda variabile per utilizzare il file odbc.ini.

## Account esterno Netezza {#netezza-external}

L&#39;account esterno di Netezza consente di collegare l&#39;istanza di Campaign al database esterno di Netezza.

1. Da Campaign **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL Netezza]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL del server Netezza

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

>[!NOTE]
>
>Non vengono prese in considerazione le operazioni sugli schemi contenenti chiavi primarie generate automaticamente.
>
>Nella tabella verrà utilizzata la clausola **Organizza su** sul primo indice definito nello schema. Poiché questa clausola è limitata a 1-4 colonne con Netezza, l&#39;indice non può contenere più di 4 colonne.
