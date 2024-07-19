---
product: campaign
title: Configurare l’integrazione di Adobe Experience Manager
description: Scopri come configurare l’integrazione Campaign-AEM
feature: Experience Manager Integration
badge-v8: label="Applicabile anche a v8" type="Positive" tooltip="Applicabile anche a Campaign v8"
audience: integrations
content-type: reference
exl-id: 54ee88b2-e646-4fb9-abec-957f0096f15f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 2%

---

# Configurare l’integrazione Campaign-AEM{#configuring-the-integration}



## Passaggi di configurazione in Adobe Campaign {#configuring-in-adobe-campaign}

Per utilizzare insieme queste due soluzioni, è necessario configurarle per connettersi tra loro.

Per avviare la configurazione in Adobe Campaign, effettua le seguenti operazioni:

1. [Installare il pacchetto di integrazione dell’AEM in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configurare l’account esterno](#configure-the-external-account)
1. [Configurare il filtro delle risorse AEM](#configure-aem-resources-filtering)

Per configurazioni avanzate, ad esempio per gestire campi e blocchi di personalizzazione. Consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html) di Adobe Experience Manager.

### Installare il pacchetto di integrazione dell’AEM in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

È innanzitutto necessario installare il pacchetto **[!UICONTROL AEM integration]**.

1. Dall&#39;istanza di Adobe Campaign, seleziona **[!UICONTROL Tools]** nella barra degli strumenti superiore.
1. Seleziona **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Seleziona **[!UICONTROL Install a standard package]**.
1. Selezionare **[!UICONTROL AEM integration]**, quindi fare clic sul pulsante **[!UICONTROL Next]**.

   ![](assets/aem_config_2.png)

1. Nella finestra successiva fare clic sul pulsante **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto. Chiudere la finestra al termine dell&#39;installazione.

### Configurare l’area di sicurezza per l’operatore AEM {#configure-the-security-zone-for-aem-operator}

Il pacchetto **[!UICONTROL AEM integration]** imposta l&#39;operatore **[!UICONTROL aemserver]** in Campaign. Questo operatore verrà utilizzato per connettere il server Adobe Experience Manager ad Adobe Campaign.

Devi configurare un’area di sicurezza per consentire a questo operatore di connettersi ad Adobe Campaign tramite Adobe Experience Manager.

>[!CAUTION]
>
>Per evitare problemi di sicurezza, si consiglia vivamente di creare un’area di sicurezza dedicata all’AEM. Per ulteriori informazioni, consulta la [guida all&#39;installazione](../../installation/using/security-zones.md).

Se la tua istanza di Campaign è ospitata da Adobe, contatta il team [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). Se utilizzi Campaign on-premise, effettua le seguenti operazioni:

1. Apri il file di configurazione **serverConf.xml**.
1. Accedi all&#39;attributo **allowUserPassword** dell&#39;area di sicurezza selezionata e impostalo su **true**.

   Questo consentirà a Adobe Experience Manager di connettere Adobe Campaign tramite login/password.

### Configurare l’account esterno {#configure-the-external-account}

Il pacchetto **[!UICONTROL AEM integration]** ha creato l&#39;account esterno per Adobe Experience Cloud. Ora devi configurarlo per connettersi all’istanza Adobe Experience Manager.

Per configurare l’account esterno dell’AEM, effettua le seguenti operazioni:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Seleziona **[!UICONTROL Administration > Platform > External accounts]**.
1. Dall&#39;elenco **[!UICONTROL External account]**, selezionare **[!UICONTROL AEM instance]**.
1. Immetti i parametri per l’istanza di authoring AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Verificare che l&#39;indirizzo **[!UICONTROL Server]** non termini con una barra finale.

   ![](assets/aem_config_4.png)

1. Selezionare la casella **[!UICONTROL Enabled]**.
1. Fai clic sul pulsante **[!UICONTROL Save]**.

### Configurare il filtro delle risorse AEM {#configure-aem-resources-filtering}

L&#39;opzione **AEMResourceTypeFilter** viene utilizzata per filtrare i tipi di risorse Experience Manager che possono essere utilizzate in Adobe Campaign. Questo consente ad Adobe Campaign di recuperare contenuti di Experience Manager progettati specificamente per essere utilizzati solo in Adobe Campaign.

Per verificare se l&#39;opzione **[!UICONTROL AEMResourceTypeFilter]** è configurata:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.
1. Seleziona **[!UICONTROL Administration > Platform > Options]**.
1. Dall&#39;elenco **[!UICONTROL Options]**, selezionare **[!UICONTROL AEMResourceTypeFilter]**.
1. Nel campo **[!UICONTROL Value (text)]**, il percorso deve essere il seguente:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   Oppure, in alcuni casi:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Passaggi di configurazione in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Per avviare la configurazione in Adobe Experience Manager, effettua le seguenti operazioni:

1. Configura la **replica** per eseguire la replica dall&#39;istanza di authoring AEM all&#39;istanza di pubblicazione AEM.

   Per informazioni su come configurare la replica, consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html) di Adobe Experience Manager.

1. Connetti Adobe Experience Manager ad Adobe Campaign configurando un **Cloud Service** dedicato.

   Per informazioni su come connettere entrambe le soluzioni tramite Cloud Service, consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) di Adobe Experience Manager.

1. Configura il servizio **Externalizer**.

   Per informazioni su come configurarlo, consulta la [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html) di Adobe Experience Manager.
