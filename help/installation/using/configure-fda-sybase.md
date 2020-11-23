---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso ad Sybase IQ
description: Scoprite come configurare l'accesso ad Sybase IQ in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# Configurare l&#39;accesso ad Sybase IQ {#configure-access-to-sybase-iq}

Utilizzate l&#39;opzione Campaign **Federated Data Access** (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguite i passaggi riportati di seguito per configurare l&#39;accesso ad Sybase IQ.

1. Configurare il database [Sybase IQ](#configuring-sybase)
1. Configurare l&#39;account [](#sybase-external) esterno Sybase IQ in Campaign

## Configurazione sybase IQ {#configuring-sybase}

La connessione a un database esterno Sybase IQ in FDA richiede configurazioni aggiuntive nel server Adobe Campaign .

>[!NOTE]
>
>Prima di iniziare, accertatevi che il pacchetto **unixodbc** sia sul server.

1. Installate **iq_odbc**. Un errore può verificarsi alla fine dell&#39;installazione. Questo errore può essere ignorato.

1. Installate **iq_client_common**. Alla fine dell&#39;installazione può verificarsi un errore Java. Questo errore può essere ignorato.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: /etc/odbc.ini per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver:

   * **/etc/odbc.ini** (sostituite valori come `<server_alias>` caratteri personalizzati):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. Aggiungete il percorso della nuova libreria libodbc16.so nella variabile LD_LIBRARY_PATH. A tale scopo:

   * Se utilizzi un file customer.sh per dichiarare il percorso: aggiungete il percorso /opt/sybase/IQ-16_0/lib64 per la variabile LD_LIBRARY_PATH.
   * In caso contrario, utilizzare un comando Unix.

## Account esterno sybase IQ {#sybase-external}

L&#39;account esterno di Sybase IQ consente di collegare l&#39;istanza Campaign al database esterno di Sybase IQ.

1. Da Campaign **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fate clic **[!UICONTROL New]** e selezionate **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account **[!UICONTROL Sybase IQ]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Corrisponde alla connessione ODBC (`<server_alias>`) definita al punto 5. Non necessariamente il nome del server stesso.

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

>[!NOTE]
>
>Per Windows, è necessario installare il client Sybase IQ sul server Adobe Campaign  e creare una connessione ODBC. Assicurarsi di creare un&#39;origine dati di sistema quando il server Adobe Campaign  (nlserver) è in esecuzione come servizio in Windows.

