---
title: Configurare l'accesso a SAP HANA
description: Scopri come configurare l'accesso a SAP HANA in FDA
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
source-wordcount: '263'
ht-degree: 0%

---


# Configurare l&#39;accesso a SAP HANA {#configure-access-to-sap-hana}

Utilizzate l&#39;opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguire i passaggi indicati di seguito per configurare l&#39;accesso a SAP HANA.

1. Configurare il database [SAP HANA](#sap-config)
1. Configurare l&#39;account [](#sap-external) esterno SAP HANA in Campaign

## Driver SAP HANA {#sap-config}

La connessione a un database esterno SAP HANA in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign :

1. Installare i driver ODBC per SAP HANA, in base al sistema operativo utilizzato:

   * **hdb_client_linux.tgz** per Linux. Una volta decompresso, avviate il comando hdbinst e seguite le istruzioni per completare l&#39;installazione dei driver.
   * **hdb_client_windows.zip** per Windows. Decomprimete il file e avviate il file eseguibile: **hdbinst.exe**. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

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

      &quot;InstallDir&quot; corrisponde alla posizione del file **odbcinst.ini** .

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. Specificate le variabili di ambiente del server Adobe Campaign :

   * **LD_LIBRARY_PATH**: Deve includere il collegamento al client SAP Hana (per impostazione predefinita, /usr/sap/hdbclient/libodbcHDB.so).
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).

## Account esterno SAP HANA{#sap-external}

L&#39;account esterno SAP HANA consente di collegare l&#39;istanza Campaign al database esterno SAP HANA.

1. Da Campaign **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL SAP Hana]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del server SAP Hana

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente
