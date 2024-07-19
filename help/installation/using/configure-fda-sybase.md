---
product: campaign
title: Configurare l’accesso alle Sybasi IQ
description: Scopri come configurare l’accesso alle Sybasi IQ in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 0fdf8259-5cab-4a9d-adb3-6c55ec5c8851
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Configurare l’accesso alle Sybasi IQ {#configure-access-to-sybase-iq}



Utilizza l&#39;opzione **Federated Data Access** (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Per configurare l’accesso a Sybase IQ, segui la procedura riportata di seguito.

1. Configura [database Sybasi IQ](#configuring-sybase)
1. Configura l&#39;[account esterno](#sybase-external) della Sybase IQ in Campaign

## Configurazione sybase IQ {#configuring-sybase}

La connessione a un database esterno di Sybase IQ in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

>[!NOTE]
>
>Prima di iniziare, verificare che il pacchetto **unixodbc** si trovi sul server.

1. Installa **iq_odbc**. È possibile che si verifichi un errore al termine dell&#39;installazione. Questo errore può essere ignorato.

1. Installa **iq_client_common**. Al termine dell&#39;installazione può verificarsi un errore Java. Questo errore può essere ignorato.

1. Configurare il driver ODBC. La configurazione può essere eseguita nei file standard: /etc/odbc.ini per i parametri generali e /etc/odbcinst.ini per la dichiarazione dei driver:

   * **/etc/odbc.ini** (sostituisci valori come `<server_alias>` caratteri con il tuo):

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

1. Aggiungi il percorso per la nuova libreria libodbc16.so nella variabile LD_LIBRARY_PATH. Per eseguire questa operazione:

   * Se si utilizza un file customer.sh per dichiarare il percorso: aggiungere il percorso /opt/sybase/IQ-16_0/lib64 per la variabile LD_LIBRARY_PATH.
   * In caso contrario, utilizza un comando Unix.

## Sybase IQ account esterno {#sybase-external}

L’account esterno Sybase IQ ti consente di collegare l’istanza Campaign al database esterno Sybase IQ.

1. Dalla campagna **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Fare clic su **[!UICONTROL New]** e selezionare **[!UICONTROL External database]** come **[!UICONTROL Type]**.

1. Per configurare l&#39;account esterno **[!UICONTROL Sybase IQ]**, è necessario specificare:

   * **[!UICONTROL Type]**: ODBC (Sybase ASE, Sybase IQ)

   * **[!UICONTROL Server]**: corrisponde alla connessione ODBC (`<server_alias>`) definita al passaggio 5. Non necessariamente il nome del server stesso.

   * **[!UICONTROL Account]**: nome dell&#39;utente

   * **[!UICONTROL Password]**: password dell&#39;account utente

   * **[!UICONTROL Database]**: nome del database

>[!NOTE]
>
>Per Windows, è necessario installare il client Sybase IQ sul server Adobe Campaign e creare una connessione ODBC. Assicurarsi di creare un&#39;origine dati di sistema quando il server Adobe Campaign (nlserver) è in esecuzione come servizio in Windows.
