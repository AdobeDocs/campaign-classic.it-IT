---
product: campaign
title: Configurare l’accesso a SAP HANA
description: Scopri come configurare l’accesso a SAP HANA in FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 39bfe775-e182-4a0b-ad3c-b7a901297c90
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 2%

---

# Configurare l’accesso a SAP HANA {#configure-access-to-sap-hana}



Utilizzare Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a SAP HANA.

1. Configura [database SAP HANA](#sap-config)
1. Configurare il SAP HANA [account esterno](#sap-external) in Campaign

## SAP HANA {#sap-config}

La connessione a un database esterno SAP HANA in FDA richiede alcune configurazioni aggiuntive sul server Adobe Campaign:

1. Installare i driver ODBC per SAP HANA, in base al sistema operativo utilizzato:

   * **hdb_client_linux.tgz** per Linux. Una volta decompresso, avviare il comando hdbinst e seguire le istruzioni per completare l&#39;installazione dei driver.
   * **hdb_client_windows.zip** per Windows. Decomprimere il file e avviare l&#39;eseguibile: **hdbinst.exe**. Seguire le istruzioni della procedura guidata per completare l&#39;installazione dei driver.

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

     &quot;InstallDir&quot; corrisponde alla posizione del **odbcinst.ini** file.

   * **/etc/odbcinst.ini**

     ```
     [HDBODBC]
     Description = "SmartCloudPT HANA"
     Driver = /usr/sap/hdbclient/libodbcHDB.so
     ```

1. Specifica le variabili di ambiente del server Adobe Campaign:

   * **LD_LIBRARY_PATH**: per impostazione predefinita, deve includere il collegamento al client SAP Hana (/usr/sap/hdbclient/libodbcHDB.so).
   * **ODBCINI**: posizione del file odbc.ini (ad esempio /etc/odbc.ini).

## Account esterno SAP HANA{#sap-external}

L’account esterno SAP HANA ti consente di collegare l’istanza Campaign al database esterno SAP HANA.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Clic **[!UICONTROL New]** e seleziona **[!UICONTROL External database]** as **[!UICONTROL Type]**.

1. Per configurare **[!UICONTROL SAP Hana]** account esterno, è necessario specificare:

   * **[!UICONTROL Type]**: SAP Hana

   * **[!UICONTROL Server]**: URL del server SAP Hana

   * **[!UICONTROL Account]**: nome dell’utente

   * **[!UICONTROL Password]**: password dell’account utente
