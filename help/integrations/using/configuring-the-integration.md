---
solution: Campaign Classic
product: campaign
title: Configurazione dell’integrazione con Adobe Experience Manager
description: Scopri come configurare l’integrazione di Campaign-AEM
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d88815e36f7be1b010dcaeee51013a5da769b4a8
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 2%

---


# Configurazione dell’integrazione{#configuring-the-integration}

## Configurazione in Adobe Campaign {#configuring-in-adobe-campaign}

Per utilizzare insieme queste due soluzioni, è necessario configurarle in modo che si connettano tra loro.

Per avviare la configurazione in Adobe Campaign, effettua le seguenti operazioni:

1. [Installare il pacchetto di integrazione AEM in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configurare l’account esterno](#configure-the-external-account)
1. [Configurare il filtro delle risorse AEM](#configure-aem-resources-filtering)

Per configurazioni avanzate, ad esempio gestione di campi e blocchi di personalizzazione. Fare riferimento alla documentazione di Adobe Experience Manager [](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Installa il pacchetto di integrazione AEM in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

Devi prima installare il pacchetto **[!UICONTROL AEM integration]** .

1. Dall’istanza di Adobe Campaign, seleziona **[!UICONTROL Tools]** dalla barra degli strumenti superiore.
1. Seleziona **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Seleziona **[!UICONTROL Install a standard package]**.
1. Selezionare **[!UICONTROL AEM integration]**, quindi fare clic sul pulsante **[!UICONTROL Next]**.

   ![](assets/aem_config_2.png)

1. Nella finestra successiva, fai clic sul pulsante **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto. Al termine dell&#39;installazione, chiudere la finestra.

### Configura la zona di sicurezza per AEM operatore {#configure-the-security-zone-for-aem-operator}

Il pacchetto **[!UICONTROL AEM integration]** imposta l’operatore **[!UICONTROL aemserver]** in Campaign. Questo operatore verrà utilizzato per collegare il server Adobe Experience Manager ad Adobe Campaign.

Devi configurare una zona di sicurezza per questo operatore per la connessione ad Adobe Campaign tramite Adobe Experience Manager.

>[!CAUTION]
>
>Consigliamo vivamente di creare una zona di sicurezza dedicata a AEM per evitare problemi di sicurezza. Per ulteriori informazioni, consulta la Guida all&#39;installazione [a1/>.](../../installation/using/security-zones.md)

Se l’istanza Campaign è ospitata da Adobe, contatta il team [Adobe Customer Care](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) . Se utilizzi Campaign on-premise, segui i passaggi seguenti:

1. Apri il file di configurazione **serverConf.xml** .
1. Accedi all&#39;attributo **allowUserPassword** della zona di sicurezza selezionata e impostalo su **true**.

   Questo consentirà a Adobe Experience Manager di collegare Adobe Campaign tramite login/password.

### Configurare l’account esterno {#configure-the-external-account}

Il pacchetto **[!UICONTROL AEM integration]** ha creato l&#39;account esterno per Adobe Experience Cloud. Ora devi configurarlo per connetterti all’istanza Adobe Experience Manager.

Per configurare l’account esterno AEM, segui i passaggi seguenti:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Seleziona **[!UICONTROL Administration > Platform > External accounts]**.
1. Dall’elenco **[!UICONTROL External account]**, seleziona **[!UICONTROL AEM instance]**.
1. Immetti i parametri per la tua istanza di authoring AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Assicurati che l&#39;indirizzo **[!UICONTROL Server]** non termini con una barra finale.

   ![](assets/aem_config_4.png)

1. Seleziona la casella **[!UICONTROL Enabled]** .
1. Fai clic sul pulsante **[!UICONTROL Save]**.

### Configurare AEM filtro delle risorse {#configure-aem-resources-filtering}

L&#39;opzione **AEMResourceTypeFilter** viene utilizzata per filtrare i tipi di risorse di Experience Manager che possono essere utilizzate in Adobe Campaign. Questo consente ad Adobe Campaign di recuperare contenuti di Experience Manager progettati specificatamente per essere utilizzati solo in Adobe Campaign.

Per verificare se l&#39;opzione **[!UICONTROL AEMResourceTypeFilter]** è configurata:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.
1. Seleziona **[!UICONTROL Administration > Platform > Options]**.
1. Dall’elenco **[!UICONTROL Options]**, seleziona **[!UICONTROL AEMResourceTypeFilter]**.
1. Nel campo **[!UICONTROL Value (text)]** il percorso deve essere il seguente:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   O in qualche caso:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Configurazione in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Per avviare la configurazione in Adobe Experience Manager, effettua le seguenti operazioni:

1. Configura la **replica** per replicare dall&#39;istanza di authoring AEM all&#39;istanza di pubblicazione AEM.

   Per informazioni su come configurare la replica, consulta la documentazione di Adobe Experience Manager [a1/>.](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html)

1. Installa l&#39;integrazione **FeaturePack** nell&#39;istanza di authoring, quindi replica l&#39;installazione nell&#39;istanza di pubblicazione. (Solo per AEM versioni 5.6.1 e 6.0).

   Per informazioni su come installare FeaturePack, consulta la documentazione [Adobe Experience Manager](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. Collega Adobe Experience Manager ad Adobe Campaign configurando un **Cloud Service** dedicato.

   Per informazioni su come collegare entrambe le soluzioni tramite Cloud Services, consulta la documentazione di Adobe Experience Manager [a1/> .](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager)

1. Configura il **servizio Externalizer**.

   Per informazioni su come configurarlo, consulta la documentazione di Adobe Experience Manager [a1/>.](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html)

