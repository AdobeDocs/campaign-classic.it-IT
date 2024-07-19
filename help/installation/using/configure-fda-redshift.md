---
product: campaign
title: Configurare l’accesso ad Amazon Redshift
description: Scopri come configurare l’accesso a Amazon Redshift in FDA
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ef2b98bd-441e-4e59-bb41-4e835e250663
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 1%

---

# Configurare l’accesso ad Amazon Redshift {#configure-access-to-redshift}

Utilizza l&#39;opzione **Federated Data Access** (FDA) di Campaign per elaborare le informazioni archiviate in un database esterno. Segui i passaggi seguenti per configurare l’accesso ad Amazon Redshift.

1. Configura [database Amazon Redshift](#configuring-redshift)
1. Configura l&#39;[account esterno](#redshift-external) di Amazon Redshift in Campaign

## Amazon Redshift su Linux {#redshift-linux}

Per configurare [!DNL Amazon Redshift] su Linux, eseguire la procedura seguente:

1. Prima dell&#39;installazione di ODBC, verificare che i seguenti pacchetti siano installati nella distribuzione Linux:

   * Per Red Hat/CentOS:

     ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
     ```

   * Per Debian:

     ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
     ```

1. Prima di eseguire lo script, è possibile accedere a ulteriori informazioni con l&#39;opzione `--help`:

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./redshift_odbc-setup.sh --help
   ```

1. Accedere alla directory in cui si trova lo script ed eseguire lo script seguente come utente root:

   ```
     cd /usr/local/neolane/nl6/bin/fda-setup-scripts
     ./redshift_odbc-setup.sh
   ```

1. Dopo aver installato i driver ODBC, è necessario riavviare Campaign Classic. A tale scopo, eseguire il comando seguente:

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. In Campaign, puoi quindi configurare l&#39;account esterno [!DNL Amazon Redshift]. Per ulteriori informazioni su come configurare l&#39;account esterno, consulta [questa sezione](#redshift-external).

## Account esterno Amazon Redshift {#redshift-external}

L&#39;account esterno [!DNL Amazon Redshift] ti consente di collegare l&#39;istanza Campaign al database esterno Amazon Redshift.

1. In Campaign Classic, configura l&#39;account esterno [!DNL Amazon Redshift]. Da **[!UICONTROL Explorer]**, fare clic su **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. Fai clic su **[!UICONTROL New]**.

1. Seleziona **[!UICONTROL External database]** come **[!UICONTROL Type]** del tuo account esterno.

1. Configurare l&#39;account esterno **[!UICONTROL Amazon Redshift]**. È necessario specificare:

   * **[!UICONTROL Type]**: Amazon Redshift

   * **[!UICONTROL Server]**: nome del DNS

   * **[!UICONTROL Account]**: nome dell&#39;utente

   * **[!UICONTROL Password]**: password dell&#39;account utente

   * **[!UICONTROL Database]**: nome del database se non specificato nel DSN. Può essere lasciato vuoto se specificato nel DSN

   * **[!UICONTROL Working schema]**: nome dello schema di lavoro. [Ulteriori informazioni](https://docs.aws.amazon.com/redshift/latest/dg/r_Schemas_and_tables.html)

   * **[!UICONTROL Time zone]**: fuso orario del server

   ![](assets/amazon_redshift.png)

1. Fai clic su **[!UICONTROL Save]**.
