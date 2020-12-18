---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso ad SAP HANA
description: Scoprite come configurare l'accesso ad SAP HANA in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---


# Configurare l&#39;accesso ad SAP HANA {#configure-access-to-sap-hana}

Utilizzate l&#39;opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguite i passaggi riportati di seguito per configurare l&#39;accesso ad SAP HANA.

1. Configurare [database SAP HANA](#sap-config)
1. Configurare l&#39;account SAP HANA [esterno](#sap-external) in Campaign

## Driver SAP HANA {#sap-config}

La connessione a un database esterno SAP HANA in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign :

1. Installare i driver ODBC per SAP HANA, in base al sistema operativo utilizzato:

   * **hdb_client_linux.** tgzfor Linux. Una volta decompresso, avviate il comando hdbinst e seguite le istruzioni per completare l&#39;installazione dei driver.
   * **hdb_client_windows.** zip per Windows. Decomprimete il file e avviate il file eseguibile: **hdbinst.exe**. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

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

1. Specificate le variabili di ambiente del server Adobe Campaign :

   * **LD_LIBRARY_PATH**: Deve includere il collegamento al client SAP Hana (per impostazione predefinita, /usr/sap/hdbclient/libodbcHDB.so).
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).

## Account esterno SAP HANA{#sap-external}

L&#39;account esterno di SAP HANA consente di collegare l&#39;istanza Campaign al database esterno di SAP HANA.

1. Da Campaign **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fare clic su **[!UICONTROL New]** e selezionare **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account esterno **[!UICONTROL SAP Hana]**, è necessario specificare:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del server SAP Hana

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente
