---
product: campaign
title: Configurare l’accesso a SAP HANA
description: Scopri come configurare l’accesso a SAP HANA in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Configurare l’accesso a SAP HANA {#configure-access-to-sap-hana}

![](../../assets/v7-only.svg)

Utilizza l’opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Per configurare l’accesso a SAP HANA, effettua le seguenti operazioni.

1. Configura [database SAP HANA](#sap-config)
1. Configurare SAP HANA [account esterno](#sap-external) in Campaign

## Driver SAP HANA {#sap-config}

La connessione a un database esterno SAP HANA in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign:

1. Installare i driver ODBC per SAP HANA in base al sistema operativo utilizzato:

   * **hdb_client_linux.** tgzfor Linux. Una volta decompresso, avviare il comando hdbinst e seguire le istruzioni per completare l&#39;installazione dei driver.
   * **hdb_client_windows.** zipfor Windows. Decomprimi il file e avvia l&#39;eseguibile: **hdbinst.exe**. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

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

   * **LD_LIBRARY_PATH**: Deve includere il collegamento al client SAP Hana (/usr/sap/hdbclient/libodbcHDB.so) per impostazione predefinita.
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).

## account esterno SAP HANA{#sap-external}

L’account esterno di SAP HANA ti consente di collegare l’istanza Campaign al database esterno di SAP HANA.

1. Dalla campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fare clic su **[!UICONTROL New]** e selezionare **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l’account esterno **[!UICONTROL SAP Hana]**, devi specificare:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del server SAP Hana

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente
