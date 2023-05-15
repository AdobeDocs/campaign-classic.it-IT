---
product: campaign
title: Configurare l’accesso alle Sybasi IQ
description: Scopri come configurare l’accesso alle Sybasi IQ in FDA
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 1%

---

# Configurare l’accesso alle Sybasi IQ {#configure-access-to-sybase-iq}



Utilizzare Campaign **Federated Data Access** (FDA) opzione per elaborare le informazioni memorizzate in database esterni. Segui i passaggi riportati di seguito per configurare l’accesso alle Sybasi IQ.

1. Configura [Database sybase IQ](#configuring-sybase)
1. Configurare la Sybase IQ [account esterno](#sybase-external) in Campaign

## Configurazione sybase IQ {#configuring-sybase}

La connessione a un database esterno di Sybase IQ in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

>[!NOTE]
>
>Prima di iniziare, assicurati che il **unixodbc** il pacchetto è sul server.

1. Installa **iq_odbc**. Alla fine dell&#39;installazione può verificarsi un errore. Questo errore può essere ignorato.

1. Installa **iq_client_common**. Alla fine dell&#39;installazione può verificarsi un errore Java. Questo errore può essere ignorato.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: /etc/odbc.ini per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver:

   * **/etc/odbc.ini** (sostituisci valori come `<server_alias>` caratteri per tuo):

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

1. Aggiungi il percorso della nuova libreria libodbc16.so nella variabile LD_LIBRARY_PATH . Per farlo:

   * Se utilizzi un file customer.sh per dichiarare il percorso: aggiungi il percorso /opt/sybase/IQ-16_0/lib64 per la variabile LD_LIBRARY_PATH .
   * In caso contrario, utilizzare un comando Unix.

## Account esterno sybase IQ {#sybase-external}

L’account esterno Sybase IQ ti consente di collegare l’istanza Campaign al database esterno Sybase IQ.

1. Da campagna **[!UICONTROL Explorer]**, fai clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]** e seleziona **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare le **[!UICONTROL Sybase IQ]** account esterno, devi specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: Corrisponde alla connessione ODBC (`<server_alias>`) definita al punto 5. Non necessariamente il nome del server stesso.

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Database]**: Nome del database

>[!NOTE]
>
>Per Windows, è necessario installare il client Sybase IQ sul server Adobe Campaign e creare una connessione ODBC. Assicurarsi di creare un&#39;origine dati di sistema quando il server Adobe Campaign (nlserver) è in esecuzione come servizio in Windows.
