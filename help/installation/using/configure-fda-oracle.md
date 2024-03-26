---
product: campaign
title: Configurare l’accesso a Oracle
description: Scopri come configurare l’accesso a Oracle in FDA
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="Applicabile solo a Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 320bfbb4-533b-4c45-a46f-c3c8dd68221f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 1%

---

# Configurare l’accesso a Oracle {#configure-access-to-oracle}



Utilizzare Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA) per elaborare le informazioni memorizzate in un database esterno. Segui i passaggi seguenti per configurare l’accesso a Oracle.

1. Configura Oracle su [Linux](#oracle-linux) o [Windows](#azure-windows)
1. Configurare l’Oracle [account esterno](#oracle-external) in Campaign

## Oracle su Linux {#oracle-linux}

La connessione a un Oracle di database esterno in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

1. Installa il client completo Oracle corrispondente alla versione di Oracle in uso.
1. Aggiungere le definizioni TNS all&#39;installazione. Per eseguire questa operazione, specificali in una **tnsnames.ora** nel repository /etc/oracle. Se l’archivio non esiste, crealo.

   Quindi crea una nuova variabile di ambiente TNS_ADMIN: esporta TNS_ADMIN=/etc/oracle e riavvia il computer.

1. Integra Oracle nel server Adobe Campaign (nlserver). A tale scopo, verificare che **customer.sh** è presente nella cartella &quot;nl6&quot; della struttura ad albero del server Adobe Campaign e include i collegamenti alle librerie Oracle.

   Ad esempio, per un cliente in 11.2:

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >Questi valori (in particolare ORACLE_HOME) dipendono dagli archivi di installazione. Controlla la struttura ad albero prima di fare riferimento a questi valori.

1. Installa le librerie necessarie, ad Oracle:

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

1. In Campaign Classic, puoi quindi configurare i [!DNL Oracle] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#oracle-external).

## Oracle su Windows {#oracle-windows}

La connessione a un Oracle di database esterno in FDA richiede configurazioni aggiuntive di seguito sul server Adobe Campaign.

1. Installa il client Oracle.

1. Nella cartella C:Oracle, crea un **tnsnames.ora** file contenente la definizione TNS.

1. Aggiungi una variabile di ambiente TNS_ADMIN con C:Oracle come valore e riavvia il computer.

1. In Campaign Classic, puoi quindi configurare i [!DNL Oracle] account esterno. Per ulteriori informazioni su come configurare l’account esterno, consulta [questa sezione](#oracle-external).

## Oracle account esterno {#oracle-external}

Il [!DNL Oracle] l’account esterno ti consente di collegare l’istanza Campaign al database esterno Oracle.

1. Da campagna **[!UICONTROL Explorer]**, seleziona **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. Scegli **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come dell’account esterno **[!UICONTROL Type]**.

1. Configurare **[!UICONTROL Oracle]** account esterno, è necessario specificare:

   * **[!UICONTROL Type]**: ORACLE

   * **[!UICONTROL Server]**: nome del DNS

   * **[!UICONTROL Account]**: nome dell’utente

   * **[!UICONTROL Password]**: password dell’account utente

   * **[!UICONTROL Time zone]**: fuso orario del server

   ![](assets/oracle_config.png)
