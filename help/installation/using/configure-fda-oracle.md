---
product: campaign
title: Configurare l’accesso all’Oracle
description: Scopri come configurare l’accesso all’Oracle in FDA
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 1%

---

# Configurare l’accesso all’Oracle {#configure-access-to-oracle}

![](../../assets/v7-only.svg)

Utilizzare Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) opzione per elaborare le informazioni memorizzate in database esterni. Segui i passaggi riportati di seguito per configurare l’accesso ad Oracle.

1. Configura Oracle su [Linux](#oracle-linux) o [Windows](#azure-windows)
1. Configurare l’Oracle [account esterno](#oracle-external) in Campaign

## Oracle su Linux {#oracle-linux}

La connessione a un database esterno di Oracle in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

1. Installa il client completo Oracle corrispondente alla tua versione di Oracle.
1. Aggiungi le definizioni TNS all&#39;installazione. A questo scopo, specificali in un **tnsnames.ora** nel repository /etc/oracle. Se questo archivio non esiste, crealo.

   Quindi crea una nuova variabile di ambiente TNS_ADMIN: esporta TNS_ADMIN=/etc/oracle e riavvia il computer.

1. Integra Oracle nel server Adobe Campaign (nlserver). Per eseguire questa operazione, controlla che la **customer.sh** Il file è presente nella cartella &quot;nl6&quot; della struttura ad albero del server Adobe Campaign e include i collegamenti alle librerie Oracle.

   Ad esempio, per un client nella versione 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Questi valori (in particolare ORACLE_HOME) dipendono dagli archivi di installazione. Prima di fare riferimento a questi valori, controlla la struttura ad albero.

1. Installa le librerie necessarie per Oracle:

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. In Campaign Classic è quindi possibile configurare il [!DNL Oracle] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#oracle-external).

## Oracle su Windows {#oracle-windows}

La connessione a un database esterno di Oracle in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

1. Installa il client Oracle.

1. Nella cartella C:Oracle , crea un **tnsnames.ora** file contenente la definizione TNS.

1. Aggiungi una variabile di ambiente TNS_ADMIN con il valore C:Oracle e riavvia il computer.

1. In Campaign Classic è quindi possibile configurare il [!DNL Oracle] conto esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#oracle-external).

## Oracle account esterno {#oracle-external}

La [!DNL Oracle] l’account esterno ti consente di collegare l’istanza Campaign al database esterno di Oracle.

1. Da campagna **[!UICONTROL Explorer]**, seleziona **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Scegli **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configura le **[!UICONTROL Oracle]** account esterno, devi specificare:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Nome del DNS

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Time zone]**: Fuso orario server
   ![](assets/oracle_config.png)
