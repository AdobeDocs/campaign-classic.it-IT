---
solution: Campaign Classic
product: campaign
title: Configurare l'accesso a  Oracle
description: Scopri come configurare l'accesso a  Oracle in FDA
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Configurare l&#39;accesso  Oracle {#configure-access-to-oracle}

Utilizzate l&#39;opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Per configurare l&#39;accesso a  Oracle, effettuate le operazioni riportate di seguito.

1. Configurare  Oracle su [Linux](#oracle-linux) o [Windows](#azure-windows)
1. Configurare  account Oracle [esterno](#oracle-external) in Campaign

##  Oracle su Linux {#oracle-linux}

La connessione a un database esterno  Oracle in FDA richiede configurazioni aggiuntive nel server Adobe Campaign .

1. Installate il client Oracle  corrispondente alla versione di  Oracle in uso.
1. Aggiungete le definizioni TNS all&#39;installazione. A tal fine, specificateli in un file **tnsnames.ora** nell&#39;archivio di /etc/ oracle. Se il repository non esiste, crearlo.

   Quindi create una nuova variabile di ambiente TNS_ADMIN: esportare TNS_ADMIN=/etc/ oracle e riavviare il computer.

1. Integrare  Oracle nel server Adobe Campaign  (nlserver). A questo scopo, verificate che il file **customer.sh** sia presente nella cartella &quot;nl6&quot; della struttura ad albero del server Adobe Campaign  e che includa i collegamenti alle librerie Oracle .

   Ad esempio, per un client nella versione 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Questi valori (in particolare  ORACLE_HOME) dipendono dai repository di installazione. Prima di fare riferimento a tali valori, verificate la struttura ad albero.

1. Installate le librerie necessarie per  Oracle:

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

1. In Campaign Classic, puoi quindi configurare il tuo account esterno [!DNL Oracle]. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consultare [questa sezione](#oracle-external).

##  Oracle in Windows {#oracle-windows}

La connessione a un database esterno  Oracle in FDA richiede configurazioni aggiuntive nel server Adobe Campaign .

1. Installate il client Oracle .

1. Nella cartella Oracle C:, create un file **tnsnames.ora** contenente la definizione TNS.

1. Aggiungete una variabile di ambiente TNS_ADMIN con C: Oracle come valore e riavviate il computer.

1. In Campaign Classic, puoi quindi configurare il tuo account esterno [!DNL Oracle]. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consultare [questa sezione](#oracle-external).

##  account esterno Oracle {#oracle-external}

L&#39;account esterno [!DNL Oracle] consente di collegare l&#39;istanza Campaign al database esterno  Oracle.

1. Da Campaign **[!UICONTROL Explorer]**, selezionare **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Scegliete **[!UICONTROL New]**.

1. Selezionare **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configurate l&#39;account esterno **[!UICONTROL Oracle]**, dovete specificare:

   * **[!UICONTROL Type]**:  Oracle

   * **[!UICONTROL Server]**: Nome del DNS

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Time zone]**: Fuso orario server

   ![](assets/oracle_config.png)

