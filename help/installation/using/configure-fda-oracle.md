---
product: campaign
title: Configurare l’accesso ad Oracle
description: Scopri come configurare l’accesso a Oracle in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
TQID: https://experienceleague.adobe.com/PbyBdgy6uFZNOmZ2GFrntS4XSJoJj41uFXLWOF4eWyA
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
topic_v2: id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
feature_v2: []
subfeature_v2: []
source-git-commit: bb41e9407ab5853b0194bb325bbf3f17bc3ea232
workflow-type: tm+mt
source-wordcount: 347
ht-degree: 0%

---

# Configurare l’accesso ad Oracle {#configure-access-to-oracle}



Utilizza l&#39;opzione [Federated Data Access](../../installation/using/about-fda.md) (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Segui i passaggi seguenti per configurare l’accesso ad Oracle.

1. Configura Oracle su [Linux](#oracle-linux) o [Windows](#azure-windows)
1. Configura l&#39;[account esterno](#oracle-external) di Oracle in Campaign

## Oracle su Linux {#oracle-linux}

La connessione a un database esterno di Oracle in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

1. Installa il client completo di Oracle corrispondente alla versione di Oracle in uso.
1. Aggiungere le definizioni TNS all&#39;installazione. A tale scopo, specificarli in un file **tnsnames.ora** nell&#39;archivio /etc/oracle. Se l’archivio non esiste, crealo.

   Quindi crea una nuova variabile di ambiente TNS_ADMIN: esporta TNS_ADMIN=/etc/oracle e riavvia il computer.

1. Integra Oracle nel tuo server Adobe Campaign (nlserver). A questo scopo, verifica che il file **customer.sh** sia presente nella cartella &quot;nl6&quot; della struttura ad albero del server Adobe Campaign e che includa i collegamenti alle librerie Oracle.

   Ad esempio, per un cliente in 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Questi valori (in particolare ORACLE_HOME) dipendono dagli archivi di installazione. Controlla la struttura ad albero prima di fare riferimento a questi valori.

1. Installa le librerie necessarie per Oracle:

   * **libclntsh.so**

     ```
     cd /usr/lib/oracle/<version>/client<architecture>/lib
     ln -s libclntsh.so.<version> libclntsh.so
     ```

   * **libaio1**

     ```
     apt install libaio1
     or
     yum install libaio1
     ```

1. In Campaign Classic è quindi possibile configurare l&#39;account esterno [!DNL Oracle]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#oracle-external).

## Oracle su Windows {#oracle-windows}

La connessione a un database esterno di Oracle in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

1. Installa il client Oracle.

1. Nella cartella C:Oracle creare un file **tnsnames.ora** contenente la definizione TNS.

1. Aggiungere una variabile di ambiente TNS_ADMIN con C:Oracle come valore e riavviare il computer.

1. In Campaign Classic è quindi possibile configurare l&#39;account esterno [!DNL Oracle]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#oracle-external).

## Account esterno Oracle {#oracle-external}

L&#39;account esterno [!DNL Oracle] ti consente di collegare l&#39;istanza Campaign al database esterno di Oracle.

1. Dalla campagna **[!UICONTROL Explorer]**, selezionare **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Scegli **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come **[!UICONTROL Type]** del tuo account esterno.

1. Configurare l&#39;account esterno **[!UICONTROL Oracle]**. È necessario specificare:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: nome del DNS

   * **[!UICONTROL Account]**: nome dell&#39;utente

   * **[!UICONTROL Password]**: password dell&#39;account utente

   * **[!UICONTROL Time zone]**: fuso orario del server

   ![](assets/oracle_config.png)
