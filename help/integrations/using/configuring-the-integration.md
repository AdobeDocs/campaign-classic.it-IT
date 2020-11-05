---
title: Configurazione dell'integrazione Adobe Experience Manager
description: Scopri come configurare l'integrazione di Campaign-AEM
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 48acf8cbc52a54a2dd08f0b8f29be57d4e5e006f
workflow-type: tm+mt
source-wordcount: '555'
ht-degree: 2%

---


# Configurazione dell’integrazione{#configuring-the-integration}

## Configuring in Adobe Campaign {#configuring-in-adobe-campaign}

Per utilizzare insieme queste due soluzioni, è necessario configurarle in modo che si connettano tra loro.

Per avviare la configurazione in  Adobe Campaign, effettuate le seguenti operazioni:

1. [Installare il pacchetto di integrazione AEM in  Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configurare l&#39;account esterno](#configure-the-external-account)
1. [Configurare AEM filtro risorse](#configure-aem-resources-filtering)

Per configurazioni avanzate, come la gestione di campi e blocchi di personalizzazione. Consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)Adobe Experience Manager.

### Installare il pacchetto di integrazione AEM in  Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

È innanzitutto necessario installare il **[!UICONTROL AEM integration]** pacchetto.

1. Nell’istanza di Adobe Campaign , selezionate **[!UICONTROL Tools]** dalla barra degli strumenti superiore.
1. Seleziona **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Seleziona **[!UICONTROL Install a standard package]**.
1. Selezionare **[!UICONTROL AEM integration]** e fare clic sul **[!UICONTROL Next]** pulsante.

   ![](assets/aem_config_2.png)

1. Nella finestra successiva, fate clic sul **[!UICONTROL Start]** pulsante per avviare l&#39;installazione del pacchetto. Al termine dell&#39;installazione, chiudete la finestra.

### Configurare la zona di protezione per l&#39;operatore AEM {#configure-the-security-zone-for-aem-operator}

Il **[!UICONTROL AEM integration]** pacchetto imposta l&#39; **[!UICONTROL aemserver]** operatore in Campaign. Questo operatore verrà utilizzato per collegare il server Adobe Experience Manager a  Adobe Campaign.

È necessario configurare un&#39;area di protezione per consentire a questo operatore di connettersi a  Adobe Campaign tramite Adobe Experience Manager.

>[!CAUTION]
>
>Consigliamo vivamente di creare una zona di sicurezza dedicata a AEM per evitare problemi di sicurezza. For more on this, refer to the Installation [guide](../../installation/using/configuring-campaign-server.md#defining-security-zones).

Se l&#39;istanza di Campaign è ospitata da  Adobe, contatta  team di supporto del Adobe. Se utilizzi Campaign locale, procedi come segue:

1. Aprite il file di configurazione **serverConf.xml** .
1. Accedete all&#39;attributo **allowUserPassword** della zona di protezione selezionata e impostatelo su **true**.

   Questo consentirà ad Adobe Experience Manager di connettersi  Adobe Campaign tramite login/password.

### Configurare l&#39;account esterno {#configure-the-external-account}

Il **[!UICONTROL AEM integration]** pacchetto ha creato l&#39;account esterno per Adobe Experience Cloud. È ora necessario configurarlo per collegarsi all&#39;istanza Adobe Experience Manager.

Per configurare l&#39;account esterno AEM, procedere come segue:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Seleziona **[!UICONTROL Administration > Platform > External accounts]**.
1. From the **[!UICONTROL External account]** list, select **[!UICONTROL AEM instance]**.
1. Immettete i parametri per l’istanza di authoring AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Accertatevi che il vostro **[!UICONTROL Server]** indirizzo non termini con una barra finale.

   ![](assets/aem_config_4.png)

1. Controlla la **[!UICONTROL Enabled]** casella.
1. Fai clic sul pulsante **[!UICONTROL Save]**.

### Configurare AEM filtro risorse {#configure-aem-resources-filtering}

L&#39;opzione **AEMResourceTypeFilter** viene utilizzata per filtrare i tipi di risorse di Experience Manager  che possono essere utilizzate in  Adobe Campaign. Questo consente  Adobe Campaign di recuperare  contenuti di Experience Manager progettati specificamente per essere utilizzati  solo Adobe Campaign.

Per verificare se l&#39; **[!UICONTROL AEMResourceTypeFilter]** opzione è configurata:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.
1. Seleziona **[!UICONTROL Administration > Platform > Options]**.
1. From the **[!UICONTROL Options]** list, select **[!UICONTROL AEMResourceTypeFilter]**.
1. Nel **[!UICONTROL Value (text)]** campo, il percorso deve essere il seguente:

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

1. Configurare la **replica** per eseguire la replica dall’istanza di creazione AEM all’istanza di pubblicazione AEM.

   Per informazioni su come configurare la replica, consultare la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)Adobe Experience Manager.

1. Installa l’integrazione **FeaturePack** nell’istanza di creazione, quindi replica l’installazione nell’istanza di pubblicazione. (solo per AEM versioni 5.6.1 e 6.0).

   Per informazioni su come installare FeaturePack, consulta la [documentazione](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)Adobe Experience Manager.

1. Connetti Adobe Experience Manager a  Adobe Campaign configurando un **Cloud Service** dedicato.

   Per informazioni su come collegare entrambe le soluzioni tramite Cloud Services, consultare la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) di Adobe Experience Manager.

1. Configurare il servizio **** Externalizer.

   Per informazioni su come configurarlo, consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)Adobe Experience Manager.

