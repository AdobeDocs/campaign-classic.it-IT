---
title: Configurazione dell'integrazione
seo-title: Configurazione dell'integrazione
description: Configurazione dell'integrazione
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 31f30db6eaf1fee43f9f757124e3fa8ed1d0075f

---


# Configuring the integration{#configuring-the-integration}

## Configurazione in Adobe Campaign {#configuring-in-adobe-campaign}

Per utilizzare insieme queste due soluzioni, è necessario configurarle in modo che si connettano tra loro.

Per avviare la configurazione in Adobe Campaign, procedi come segue:

1. [Installare il pacchetto di integrazione AEM in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configurare l&#39;account esterno](#configure-the-external-account)
1. [Configurare il filtro delle risorse AEM](#configure-aem-resources-filtering)

Per configurazioni avanzate, come la gestione di campi e blocchi di personalizzazione. Fate riferimento alla [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html)di Adobe Experience Manager.

### Installare il pacchetto di integrazione AEM in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

È innanzitutto necessario installare il **[!UICONTROL AEM integration]** pacchetto.

1. Nell&#39;istanza di Adobe Campaign, seleziona **[!UICONTROL Tools]** dalla barra degli strumenti superiore.
1. Selezionare **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Selezionare **[!UICONTROL Install a standard package]**.
1. Selezionare **[!UICONTROL AEM integration]** e fare clic sul **[!UICONTROL Next]** pulsante.

   ![](assets/aem_config_2.png)

1. Nella finestra successiva, fate clic sul **[!UICONTROL Start]** pulsante per avviare l&#39;installazione del pacchetto. Al termine dell&#39;installazione, chiudete la finestra.

### Configurare la zona di protezione per l&#39;operatore AEM {#configure-the-security-zone-for-aem-operator}

Il **[!UICONTROL AEM integration]** pacchetto imposta l&#39; **[!UICONTROL aemserver]** operatore in Campaign. Questo operatore verrà utilizzato per collegare il server Adobe Experience Manager ad Adobe Campaign.

Devi configurare una zona di sicurezza per consentire a questo operatore di connettersi ad Adobe Campaign tramite Adobe Experience Manager.

>[!CAUTION]
>
>È vivamente consigliato creare una zona di sicurezza dedicata ad AEM per evitare problemi di sicurezza. Per ulteriori informazioni, consultare la [guida](../../installation/using/configuring-campaign-server.md#defining-security-zones)all&#39;installazione.

Se l&#39;istanza Campaign è ospitata da Adobe, contatta il team di supporto di Adobe. Se utilizzi Campaign locale, procedi come segue:

1. Aprite il file di configurazione **serverConf.xml** .
1. Accedete all&#39;attributo **allowUserPassword** della zona di protezione selezionata e impostatelo su **true**.

   In questo modo Adobe Experience Manager potrà collegare Adobe Campaign tramite login/password.

### Configurare l&#39;account esterno {#configure-the-external-account}

Il **[!UICONTROL AEM integration]** pacchetto ha creato l&#39;account esterno per Adobe Experience Cloud. È ora necessario configurarlo per connettersi all&#39;istanza Adobe Experience Manager.

Per configurare l&#39;account esterno di AEM, segui i passaggi seguenti:

1. Fate clic sul **[!UICONTROL Explorer]** pulsante.

   ![](assets/aem_config_3.png)

1. Selezionare **[!UICONTROL Administration > Platform > External accounts]**.
1. Dall&#39; **[!UICONTROL External account]** elenco, selezionare **[!UICONTROL AEM instance]**.
1. Immettete i parametri per l’istanza di authoring di AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**
   >[!NOTE]
   >
   >Accertatevi che il vostro **[!UICONTROL Server]** indirizzo non termini con una barra finale.

   ![](assets/aem_config_4.png)

1. Controlla la **[!UICONTROL Enabled]** casella.
1. Fate clic sul **[!UICONTROL Save]** pulsante.

### Configurare il filtro delle risorse AEM {#configure-aem-resources-filtering}

L&#39;opzione **AEMResourceTypeFilter** viene utilizzata per filtrare i tipi di risorse Experience Manager che possono essere utilizzate in Adobe Campaign. Questo consente ad Adobe Campaign di recuperare i contenuti di Experience Manager creati specificamente per essere utilizzati solo in Adobe Campaign.

Per verificare se l&#39; **[!UICONTROL AEMResourceTypeFilter]** opzione è configurata:

1. Fate clic sul **[!UICONTROL Explorer]** pulsante.
1. Selezionare **[!UICONTROL Administration > Platform > Options]**.
1. Dall&#39; **[!UICONTROL Options]** elenco, selezionare **[!UICONTROL AEMResourceTypeFilter]**.
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

Per avviare la configurazione in Adobe Experience Manager, procedi come segue:

1. Configurare la **replica** per la replica dall’istanza di creazione di AEM all’istanza di pubblicazione di AEM.

   Per informazioni su come configurare la replica, consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)di Adobe Experience Manager.

1. Installa l’integrazione **FeaturePack** nell’istanza di creazione, quindi replica l’installazione nell’istanza di pubblicazione. (solo per AEM versioni 5.6.1 e 6.0).

   Per informazioni su come installare FeaturePack, consulta la [documentazione](https://helpx.adobe.com/experience-manager/aem-previous-versions.html)di Adobe Experience Manager.

1. Connetti Adobe Experience Manager ad Adobe Campaign configurando un servizio **** Cloud dedicato.

   Per informazioni su come collegare entrambe le soluzioni tramite Cloud Services, consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) di Adobe Experience Manager.

1. Configurare il servizio **** Externalizer.

   Per informazioni su come configurarlo, consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)di Adobe Experience Manager.

