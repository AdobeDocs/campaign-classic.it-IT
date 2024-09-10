---
product: campaign
title: Configurare l’accesso a Netezza
description: Scopri come configurare l’accesso a Netezza in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: b148d34b-4060-4c54-9cb2-9e712a7c17d7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Configurare l’accesso a Netezza {#configure-access-to-netezza}



Utilizza l&#39;opzione [Federated Data Access](../../installation/using/about-fda.md) (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a Netezza.

1. Installa e configura [driver di Netezza](#netezza-config)
1. Configura l&#39;[account esterno](#netezza-external) di Netezza in Campaign

## Netezza configurazione {#netezza-config}

La connessione a un database esterno Netezza in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign:

1. Installare i driver ODBC per Netezza, in base al sistema operativo utilizzato:

   * **nz-linuxclient-v7.2.0.0.tar.gz** per Linux. Seleziona la cartella corrispondente al sistema operativo in uso (linux o linux64) e avvia il comando unpack. È possibile lasciare che l’installazione venga eseguita nell’archivio suggerito per impostazione predefinita: &quot;/usr/local/nz&quot;.
   * **nz-winclient-v7.2.0.0.zip** per Windows. Decomprimere il file e avviare lo script eseguibile corrispondente al sistema operativo: nzodbcsetup.exe o nzodbcsetup64.exe. Seguire le istruzioni dell&#39;assistente per completare l&#39;installazione dei driver.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: **/etc/odbc.ini** per i parametri generali e **/etc/odbcinst.ini** per i driver dichiaranti.

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
   * **ODBCINI**: percorso del file odbc.ini (ad esempio /etc/odbc.ini).
   * **NZ_ODBC_INI_PATH**: percorso del file odbc.ini. Netezza richiede anche questa seconda variabile per utilizzare il file odbc.ini.

## Netezza account esterno {#netezza-external}

L’account esterno Netezza ti consente di collegare l’istanza Campaign al database esterno Netezza.

1. Dalla campagna **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fare clic su **[!UICONTROL New]** e selezionare **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account esterno **[!UICONTROL Netezza]**, è necessario specificare:

   * **[!UICONTROL Type]**: Netezza

   * **[!UICONTROL Server]**: URL del server Netezza

   * **[!UICONTROL Account]**: nome dell&#39;utente

   * **[!UICONTROL Password]**: password dell&#39;account utente

   * **[!UICONTROL Database]**: nome del database

>[!NOTE]
>
>Le operazioni sugli schemi contenenti chiavi primarie generate automaticamente non vengono prese in considerazione.
>
>La tabella utilizzerà la clausola **Organizza su** sul primo indice definito nello schema. Poiché questa clausola è limitata a 1-4 colonne con Netezza, l&#39;indice non può contenere più di 4 colonne.
