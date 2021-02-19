---
solution: Campaign Classic
product: campaign
title: Configurazione dell'integrazione Adobe Experience Manager
description: Scopri come configurare l'integrazione di Campaign-AEM
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
translation-type: tm+mt
source-git-commit: 3139a9bf5036086831e23acef21af937fcfda740
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# Configurazione dell’integrazione{#configuring-the-integration}

## Configurazione in  Adobe Campaign {#configuring-in-adobe-campaign}

Per utilizzare insieme queste due soluzioni, è necessario configurarle in modo che si connettano tra loro.

Per avviare la configurazione in  Adobe Campaign, effettuate le seguenti operazioni:

1. [Installare il pacchetto di integrazione AEM in  Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configurare l&#39;account esterno](#configure-the-external-account)
1. [Configurare AEM filtro risorse](#configure-aem-resources-filtering)

Per configurazioni avanzate, come la gestione di campi e blocchi di personalizzazione. Fare riferimento alla documentazione di Adobe Experience Manager [](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Installare il pacchetto di integrazione AEM in  Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

È innanzitutto necessario installare il pacchetto **[!UICONTROL AEM integration]**.

1. Nell&#39;istanza Adobe Campaign , selezionare **[!UICONTROL Tools]** dalla barra degli strumenti superiore.
1. Seleziona **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Seleziona **[!UICONTROL Install a standard package]**.
1. Selezionare **[!UICONTROL AEM integration]**, quindi fare clic sul pulsante **[!UICONTROL Next]**.

   ![](assets/aem_config_2.png)

1. Nella finestra successiva, fate clic sul pulsante **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto. Al termine dell&#39;installazione, chiudete la finestra.

### Configurare la zona di protezione per l&#39;operatore AEM {#configure-the-security-zone-for-aem-operator}

Il pacchetto **[!UICONTROL AEM integration]** imposta l&#39;operatore **[!UICONTROL aemserver]** in Campaign. Questo operatore verrà utilizzato per collegare il server Adobe Experience Manager a  Adobe Campaign.

È necessario configurare un&#39;area di protezione per consentire a questo operatore di connettersi a  Adobe Campaign tramite Adobe Experience Manager.

>[!CAUTION]
>
>Consigliamo vivamente di creare una zona di sicurezza dedicata a AEM per evitare problemi di sicurezza. Per ulteriori informazioni, fare riferimento alla Guida all&#39;installazione [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Se l&#39;istanza della campagna è ospitata da  Adobe, contatta il team di assistenza clienti [ Adobe](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Se utilizzi Campaign locale, procedi come segue:

1. Aprite il file di configurazione **serverConf.xml**.
1. Accedete all&#39;attributo **allowUserPassword** della zona di protezione selezionata e impostatelo su **true**.

   Questo consentirà ad Adobe Experience Manager di connettersi  Adobe Campaign tramite login/password.

### Configurare l&#39;account esterno {#configure-the-external-account}

Il pacchetto **[!UICONTROL AEM integration]** ha creato l&#39;account esterno per Adobe Experience Cloud. È ora necessario configurarlo per collegarsi all&#39;istanza Adobe Experience Manager.

Per configurare l&#39;account esterno AEM, procedere come segue:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Seleziona **[!UICONTROL Administration > Platform > External accounts]**.
1. Dall&#39;elenco **[!UICONTROL External account]**, selezionare **[!UICONTROL AEM instance]**.
1. Immettete i parametri per l’istanza di authoring AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Assicurarsi che l&#39;indirizzo **[!UICONTROL Server]** non termini con una barra finale.

   ![](assets/aem_config_4.png)

1. Selezionare la casella **[!UICONTROL Enabled]**.
1. Fai clic sul pulsante **[!UICONTROL Save]**.

### Configurare AEM filtro risorse {#configure-aem-resources-filtering}

L&#39;opzione **AEMResourceTypeFilter** viene utilizzata per filtrare i tipi di risorse  Experience Manager che possono essere utilizzate in  Adobe Campaign. Questo consente  Adobe Campaign di recuperare  contenuti di Experience Manager progettati specificamente per essere utilizzati  solo Adobe Campaign.

Per verificare se l&#39;opzione **[!UICONTROL AEMResourceTypeFilter]** è configurata:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.
1. Seleziona **[!UICONTROL Administration > Platform > Options]**.
1. Dall&#39;elenco **[!UICONTROL Options]**, selezionare **[!UICONTROL AEMResourceTypeFilter]**.
1. Nel campo **[!UICONTROL Value (text)]**, il percorso deve essere il seguente:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   O in alcuni casi:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Configurazione in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Per avviare la configurazione in Adobe Experience Manager, effettuate le seguenti operazioni:

1. Configurare la **replica** per replicare dall&#39;istanza di authoring AEM all&#39;istanza di pubblicazione AEM.

   Per informazioni su come configurare la replica, fare riferimento alla documentazione di Adobe Experience Manager [](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. Installate l&#39;integrazione **FeaturePack** nell&#39;istanza di authoring, quindi replicate l&#39;installazione nell&#39;istanza di pubblicazione. (solo per AEM versioni 5.6.1 e 6.0).

   Per informazioni su come installare FeaturePack, consultare la documentazione di Adobe Experience Manager [](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. Connetti Adobe Experience Manager a  Adobe Campaign configurando un **Cloud Service** dedicato.

   Per informazioni su come collegare entrambe le soluzioni tramite Cloud Services, fare riferimento alla documentazione di Adobe Experience Manager [](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) .

1. Configurare il **servizio Externalizer**.

   Per informazioni su come configurarlo, fare riferimento alla documentazione di Adobe Experience Manager [](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html).

