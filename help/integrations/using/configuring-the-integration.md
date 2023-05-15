---
product: campaign
title: Configurare l’integrazione con Adobe Experience Manager
description: Scopri come configurare l’integrazione di Campaign-AEM
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 54ee88b2-e646-4fb9-abec-957f0096f15f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 3%

---

# Configurare l’integrazione di Campaign-AEM{#configuring-the-integration}



## Passaggi di configurazione in Adobe Campaign {#configuring-in-adobe-campaign}

Per utilizzare insieme queste due soluzioni, è necessario configurarle in modo che si connettano tra loro.

Per avviare la configurazione in Adobe Campaign, effettua le seguenti operazioni:

1. [Installare il pacchetto di integrazione AEM in Adobe Campaign](#install-the-aem-integration-package-in-adobe-campaign)
1. [Configurare l’account esterno](#configure-the-external-account)
1. [Configurare il filtro delle risorse AEM](#configure-aem-resources-filtering)

Per configurazioni avanzate, ad esempio gestione di campi e blocchi di personalizzazione. Consulta Adobe Experience Manager [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html).

### Installare il pacchetto di integrazione AEM in Adobe Campaign {#install-the-aem-integration-package-in-adobe-campaign}

È innanzitutto necessario installare il **[!UICONTROL AEM integration]** pacchetto.

1. Dall’istanza Adobe Campaign, seleziona **[!UICONTROL Tools]** dalla barra degli strumenti superiore.
1. Seleziona **[!UICONTROL Tools > Advanced > Import package...]**.

   ![](assets/aem_config_1.png)

1. Seleziona **[!UICONTROL Install a standard package]**.
1. Controlla **[!UICONTROL AEM integration]** quindi fai clic su **[!UICONTROL Next]** pulsante .

   ![](assets/aem_config_2.png)

1. Nella finestra successiva, fai clic sul pulsante **[!UICONTROL Start]** per avviare l&#39;installazione del pacchetto. Al termine dell&#39;installazione, chiudere la finestra.

### Configurare la zona di sicurezza per l’operatore AEM {#configure-the-security-zone-for-aem-operator}

La **[!UICONTROL AEM integration]** imposta il pacchetto **[!UICONTROL aemserver]** in Campaign. Questo operatore verrà utilizzato per collegare il server Adobe Experience Manager ad Adobe Campaign.

Devi configurare una zona di sicurezza per questo operatore per la connessione ad Adobe Campaign tramite Adobe Experience Manager.

>[!CAUTION]
>
>Consigliamo vivamente di creare una zona di sicurezza dedicata a AEM per evitare problemi di sicurezza. Per ulteriori informazioni, consulta Installazione [guida](../../installation/using/security-zones.md).

Se l’istanza Campaign è ospitata per Adobe, contatta [Adobe Customer Care](https://helpx.adobe.com/it/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) squadra. Se utilizzi Campaign on-premise, segui i passaggi seguenti:

1. Apri **serverConf.xml** file di configurazione.
1. Accedere al **allowUserPassword** attributo della zona di sicurezza selezionata e impostarlo su **true**.

   Questo consentirà ad Adobe Experience Manager di collegare Adobe Campaign tramite login/password.

### Configurare l’account esterno {#configure-the-external-account}

La **[!UICONTROL AEM integration]** creato l&#39;account esterno per Adobe Experience Cloud. Ora devi configurarlo per connetterti all’istanza Adobe Experience Manager.

Per configurare l’account esterno AEM, effettua le seguenti operazioni:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.

   ![](assets/aem_config_3.png)

1. Seleziona **[!UICONTROL Administration > Platform > External accounts]**.
1. Da **[!UICONTROL External account]** elenco, selezionare **[!UICONTROL AEM instance]**.
1. Immetti i parametri per la tua istanza di authoring AEM:

   * **[!UICONTROL Server]**
   * **[!UICONTROL Account]**
   * **[!UICONTROL Password]**

   >[!NOTE]
   >
   >Assicurati che il tuo **[!UICONTROL Server]** l&#39;indirizzo non termina con una barra finale.

   ![](assets/aem_config_4.png)

1. Controlla la **[!UICONTROL Enabled]** scatola.
1. Fai clic sul pulsante **[!UICONTROL Save]**.

### Configurare il filtro delle risorse AEM {#configure-aem-resources-filtering}

La **AEMResourceTypeFilter** viene utilizzata per filtrare i tipi di risorse di Experience Manager che possono essere utilizzate in Adobe Campaign. Questo consente ad Adobe Campaign di recuperare contenuti di Experience Manager progettati specificatamente per essere utilizzati solo in Adobe Campaign.

Per verificare se la **[!UICONTROL AEMResourceTypeFilter]** è configurata:

1. Fai clic sul pulsante **[!UICONTROL Explorer]**.
1. Seleziona **[!UICONTROL Administration > Platform > Options]**.
1. Da **[!UICONTROL Options]** elenco, selezionare **[!UICONTROL AEMResourceTypeFilter]**.
1. In **[!UICONTROL Value (text)]** il percorso deve essere il seguente:

   ```
   mcm/campaign/components/newsletter,mcm/campaign/components/campaign_newsletterpage,mcm/neolane/components/newsletter
   ```

   O in qualche caso:

   ```
   mcm/campaign/components/newsletter
   ```

   ![](assets/aem_config_5.png)

## Passaggi di configurazione in Adobe Experience Manager {#configuring-in-adobe-experience-manager}

Per avviare la configurazione in Adobe Experience Manager, effettua le seguenti operazioni:

1. Configura le **replica** per replicare dall’istanza di authoring AEM all’istanza di pubblicazione AEM.

   Per informazioni su come configurare la replica, consulta Adobe Experience Manager [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/replication.html).

1. Installare l’integrazione **FeaturePack** nell’istanza di authoring, replica l’installazione nell’istanza di pubblicazione. (Solo per AEM versioni 5.6.1 e 6.0).

   Per informazioni su come installare FeaturePack, consulta Adobe Experience Manager [documentazione](https://helpx.adobe.com/experience-manager/aem-previous-versions.html).

1. Connetti Adobe Experience Manager ad Adobe Campaign configurando un **Cloud Service**.

   Per informazioni su come collegare entrambe le soluzioni tramite i Cloud Services, consulta Adobe Experience Manager [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/campaignonpremise.html#ConfiguringAdobeExperienceManager) .

1. Configura le **Servizio Externalizer**.

   Per informazioni su come configurarlo, consulta Adobe Experience Manager [documentazione](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/externalizer.html).
