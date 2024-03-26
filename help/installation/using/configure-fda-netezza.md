---
product: campaign
title: Configurare l’accesso a Netezza
description: Scopri come configurare l’accesso a Netezza in FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 1%

---

# Configurare l’accesso a Netezza {#configure-access-to-netezza}



Utilizzare Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a Netezza.

1. Installare e configurare [Netezza driver](#netezza-config)
1. Configurare la Netezza [account esterno](#netezza-external) in Campaign

## Netezza configurazione {#netezza-config}

La connessione a un database esterno Netezza in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign:

1. Installare i driver ODBC per Netezza, in base al sistema operativo utilizzato:

   * **nz-linuxclient-v7.2.0.0.tar.gz** per Linux. Seleziona la cartella corrispondente al sistema operativo in uso (linux o linux64) e avvia il comando unpack. È possibile lasciare che l’installazione venga eseguita nell’archivio suggerito per impostazione predefinita: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** per Windows. Decomprimere il file e avviare lo script eseguibile corrispondente al sistema operativo: nzodbcsetup.exe o nzodbcsetup64.exe. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

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

1. Specifica le variabili di ambiente del server Adobe Campaign:

   * **LD_LIBRARY_PATH**: /usr/local/nz/lib e /usr/local/nz/lib64. &quot;/usr/local/nz&quot; corrisponde all&#39;archivio di installazione offerto per impostazione predefinita durante l&#39;installazione dei driver. Qui è necessario specificare l’archivio selezionato per l’installazione.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: posizione del file odbc.ini. Netezza richiede anche questa seconda variabile per utilizzare il file odbc.ini.

## Netezza account esterno {#netezza-external}

L’account esterno Netezza ti consente di collegare l’istanza Campaign al database esterno Netezza.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clic **[!UICONTROL New]** e seleziona **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Per configurare **[!UICONTROL Netezza]** account esterno, è necessario specificare:

   * **[!UICONTROL Type]**: NETEZZA

   * **[!UICONTROL Server]**: URL del server di Netezza

   * **[!UICONTROL Account]**: nome dell’utente

   * **[!UICONTROL Password]**: password dell’account utente

   * **[!UICONTROL Database]**: nome del database

>[!NOTE]
>
>Le operazioni sugli schemi contenenti chiavi primarie generate automaticamente non vengono prese in considerazione.
>
>La tabella utilizzerà **Organizza su** clausola sul primo indice definito nello schema. Poiché questa clausola è limitata a 1-4 colonne con Netezza, l&#39;indice non può contenere più di 4 colonne.
