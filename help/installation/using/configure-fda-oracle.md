---
title: Configurare l'accesso a Oracle
description: Informazioni su come configurare l'accesso a Oracle in FDA
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
source-wordcount: '352'
ht-degree: 0%

---


# Configurare l&#39;accesso a Oracle {#configure-access-to-oracle}

Utilizzate l&#39;opzione Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Seguire i passaggi riportati di seguito per configurare l&#39;accesso a Oracle.

1. Configurare Oracle su [Linux](#oracle-linux) o [Windows](#azure-windows)
1. Configurare l&#39;account [](#oracle-external) esterno Oracle in Campaign

## Oracle su Linux {#oracle-linux}

La connessione a un database Oracle esterno in FDA richiede configurazioni aggiuntive nel server Adobe Campaign .

1. Installare il client completo Oracle corrispondente alla versione di Oracle in uso.
1. Aggiungete le definizioni TNS all&#39;installazione. Per eseguire questa operazione, specificateli in un file **tnsnames.ora** nell&#39;archivio /etc/oracle. Se il repository non esiste, crearlo.

   Quindi create una nuova variabile di ambiente TNS_ADMIN: esportare TNS_ADMIN=/etc/oracle e riavviare il computer.

1. Integrare Oracle nel server Adobe Campaign  (nlserver). A questo scopo, verificate che il file **customer.sh** sia presente nella cartella &quot;nl6&quot; della struttura ad albero del server Adobe Campaign  e che includa i collegamenti alle librerie Oracle.

   Ad esempio, per un client nella versione 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Questi valori (in particolare ORACLE_HOME) dipendono dai repository di installazione. Prima di fare riferimento a tali valori, verificate la struttura ad albero.

1. Installare le librerie necessarie per Oracle:

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

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Oracle] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta [questa sezione](#oracle-external).

## Oracle su Windows {#oracle-windows}

La connessione a un database Oracle esterno in FDA richiede configurazioni aggiuntive nel server Adobe Campaign .

1. Installare il client Oracle.

1. Nella cartella C:Oracle, create un file **tnsnames.ora** contenente la definizione TNS.

1. Aggiungere una variabile di ambiente TNS_ADMIN con C:Oracle come valore e riavviare il computer.

1. In Campaign Classic, potete quindi configurare il vostro account [!DNL Oracle] esterno. Per ulteriori informazioni sulla configurazione dell&#39;account esterno, consulta [questa sezione](#oracle-external).

## Conto esterno Oracle {#oracle-external}

L&#39;account [!DNL Oracle] esterno consente di collegare l&#39;istanza Campaign al database Oracle esterno.

1. Da Campaign **[!UICONTROL Explorer]**, selezionare **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Scegli **[!UICONTROL New]**.

1. Selezionate **[!UICONTROL External database]** come account esterno **[!UICONTROL Type]**.

1. Configurate l&#39;account **[!UICONTROL Oracle]** esterno, dovete specificare:

   * **[!UICONTROL Type]**: Oracle

   * **[!UICONTROL Server]**: Nome del DNS

   * **[!UICONTROL Account]**: Nome dell’utente

   * **[!UICONTROL Password]**: Password account utente

   * **[!UICONTROL Time zone]**: Fuso orario server

   ![](assets/oracle_config.png)

