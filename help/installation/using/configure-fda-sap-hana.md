---
product: campaign
title: Configurare l’accesso a SAP HANA
description: Scopri come configurare l’accesso a SAP HANA in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Configurare l’accesso a SAP HANA {#configure-access-to-sap-hana}



Utilizza l&#39;opzione [Federated Data Access](../../installation/using/about-fda.md) (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a SAP HANA.

1. Configura [database SAP HANA](#sap-config)
1. Configura l&#39;[account esterno](#sap-external) di SAP HANA in Campaign

## SAP HANA {#sap-config}

La connessione a un database esterno SAP HANA in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign:

1. Installare i driver ODBC per SAP HANA, in base al sistema operativo utilizzato:

   * **hdb_client_linux.tgz** per Linux. Una volta decompresso, avviare il comando hdbinst e seguire le istruzioni per completare l&#39;installazione dei driver.
   * **hdb_client_windows.zip** per Windows. Decomprimere il file e avviare l&#39;eseguibile: **hdbinst.exe**. Seguire le istruzioni dell&#39;assistente per completare l&#39;installazione dei driver.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: /etc/odbc.ini per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver.

   * **/etc/odbc.ini**

     ```
     [ODBC]
     InstallDir=/etc/
     
     [HDB]
     Driver=HDBODBC
     servernode=localhost:39013 (this value depend of your server)
     User:SYSTEM
     ```

     &quot;InstallDir&quot; corrisponde alla posizione del file **odbcinst.ini**.

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. Specifica le variabili di ambiente del server Adobe Campaign:

   * **LD_LIBRARY_PATH**: per impostazione predefinita, deve includere il collegamento al client SAP Hana (/usr/sap/hdbclient/libodbcHDB.so).
   * **ODBCINI**: percorso del file odbc.ini (ad esempio /etc/odbc.ini).

## Account esterno SAP HANA{#sap-external}

L’account esterno SAP HANA ti consente di collegare l’istanza Campaign al database esterno SAP HANA.

1. Dalla campagna **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fare clic su **[!UICONTROL New]** e selezionare **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account esterno **[!UICONTROL SAP Hana]**, è necessario specificare:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del server SAP Hana

   * **[!UICONTROL Account]**: nome dell&#39;utente

   * **[!UICONTROL Password]**: password dell&#39;account utente
